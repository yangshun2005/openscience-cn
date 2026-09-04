# 架构

本文档解释 OpenScience 的构成方式，以便您了解代码库结构，并知晓某项更改应归属于何处。

## 系统形态

当您运行 `openscience` 时，CLI 会启动一个本地服务器，并在浏览器中打开一个工作区。工作区、持久化状态、权限以及计算控制平面均在您的机器上运行。模型调用、科学连接器以及经明确批准的远程计算任务可以使用您配置的提供商。

```
  浏览器工作区  (frontend/workspace, SolidJS)
        |  HTTP + SSE，仅限 localhost
        v
  本地服务器       (backend/cli/src/server)
        |
        +--  代理运行时      会话、消息循环、模型路由
        +--  工具层         shell、编辑、LSP、MCP、科学连接器
        +--  技能             内置和用户安装的技能包
        +--  提供商          Anthropic、OpenAI、Google 以及 75+ 更多
        +--  计算任务       本地、SSH、调度器以及用户拥有的 Modal 运行
```

服务器绑定到 `127.0.0.1`，并强制执行 Host 和 Origin 白名单。不存在远程模式。

## 仓库布局

```
backend/cli          CLI、服务器、代理运行时、工具和技能
frontend/workspace   工作区 UI (SolidJS)，由 CLI 提供服务
frontend/ui          共享 UI 组件、主题和字体
frontend/docs        文档站点 (Vite + React)
frontend/landing     营销站点 (openscience.sh)
tooling/sdk/js       TypeScript SDK，根据服务器契约生成
tooling/plugin       插件运行时 (@synsci/plugin)
tooling/launcher     `npx synsci` 安装器
tooling/repo         发布自动化
tooling/script       跨包使用的构建辅助工具
tooling/util         共享 TypeScript 工具 (@synsci/util)
tooling/patches      安装时应用的依赖补丁
```

## 后端 (`backend/cli`)

后端是一个 Bun 和 TypeScript 应用程序，为每个平台编译为单个原生二进制文件。

- `src/index.ts` 注册 CLI 命令并启动进程。运行不带子命令的 `openscience` 会打开工作区 (`src/cli/cmd/web.ts`)。
- `src/server` 是一个 Hono 服务器。它提供嵌入式工作区 UI，公开会话和工具 API，并通过 SSE 将事件流式传输回浏览器。
- `src/session` 是代理运行时：消息循环、工具分发、压缩、来源追踪、持久化运行时事件，以及针对会话或不可变工件版本的显式只读审查流程。
- `src/agent` 保存代理注册表和提示词。`research` 是唯一的面向用户的代理；它通过技能加载领域知识，并可能在内部委派独立的 Explore 或 Execute 工作。委派姿态改变其并行化的容易程度，而运行时容量提供实际的并发边界。领域和旧版辅助配置文件仍然是隐藏的兼容性别名；`plan` 是只读模式。
- `src/provider` 将每个请求路由到模型。模型定义来自 [models.dev](https://models.dev)，本地缓存并附带捆绑快照作为后备。原生直接密钥路由与中继保持不同：DeepSeek 直接 BYOK 使用官方适配器，而选择显式的 OpenRouter 模型则将该请求保留在 OpenRouter 上。
- `src/tool` 和 `src/science` 实现代理可以调用的工具，包括 shell、编辑器、LSP 桥接、MCP 客户端以及科学数据库连接器。版本化的科学能力注册表包含一份真实的 54 项清单。五个实验性 Python 能力拥有完整的 doctor/setup/plan/start/status/wait/logs/artifacts/verify/cancel/retry/release 生命周期，基于精确的本地或 Modal 运行时锁；十个实验性 BioNeMo 能力使用严格的进程内 BYOK NVIDIA NIM 适配器。两项被明确阻止，且没有一项在没有匹配的发布证据的情况下被标记为已验证。单一的 `scientific_capability` 工具拥有这些生命周期，因此模型永远不需要第二个单独选择的计算工具来完成已批准的运行。
- `src/compute` 拥有持久的本地和远程作业生命周期。Modal 分发绑定到已批准的摘要、显式文件和密钥、持久所有权以及可恢复的输出交付。其并发设置是一个准入限制：超出限制的启动会明显失败，而不是进入自主等待队列。
- `src/openscience` 包含本地凭据编辑和子进程环境边界。

### 提示词架构

提示词由两层组成：由模型选择的提供商级系统提示词 (`src/session/system.ts`)，以及由代理名称注入的代理级工作流提示词 (`src/session/prompt.ts`)。有关路由详情，请参阅 [CLAUDE.md](CLAUDE.md)。

### 技能

技能是代理按需加载的指令包 (`src/skill`)。规范的默认库是 `backend/cli/skills`；发布版本会嵌入完整树的压缩、哈希副本，并将其物化到版本化的本地缓存中。学习到的技能、用户编写的技能、通过 Git 安装的技能以及项目技能也是本地的。技能发现、加载、安全审查、安装和移除永远不需要 Gateway。经过身份验证的升级可以执行一次性的只读导入，导入由旧版本创建的技能记录。

## 前端

- `frontend/workspace` 是工作区 UI。它通过 SDK 公开的相同 API 与本地服务器通信，并渲染会话、文件、终端以及内联科学视图（分子、结构、基因组、图表）。CLI 构建将编译后的 UI 嵌入到二进制文件中。
- `frontend/ui` 是应用程序和文档站点使用的共享组件和主题库。
- `frontend/docs` 是 Vite + React 文档站点。

## SDK 和插件

- `tooling/sdk/js` 根据服务器的 OpenAPI 契约生成。更改服务器 API 后，运行 `./tooling/repo/generate.ts` 以重新生成。
- `tooling/plugin` 是插件运行时。插件接收类型化客户端，并可以添加工具、提供商和钩子。

## 配置和状态

全局配置位于 `~/.config/openscience/openscience.json`；项目配置位于 `openscience.json` 或仓库根目录下的 `.openscience/` 目录中。持久化应用程序数据（会话、认证、凭据、二进制文件和日志）默认存储在稳定的 `~/.openscience` 数据根目录下，并且可以重新定位；配置、缓存和状态使用其解析后的 XDG 目录。`src/global/index.ts` 拥有这些路径。在 OpenScience 重命名之前进行的安装会在首次运行时导入或迁移旧的 `synsc` 目录。

## 构建和发布

`backend/cli/script/build.ts` 获取模型目录，构建工作区 UI，并将 CLI 编译为适用于 Linux、macOS 和 Windows 的原生二进制文件。每个平台的二进制文件都作为独立的 npm 包 (`@synsci/openscience-<platform>`) 发布，一个小型元包 (`@synsci/openscience`) 在安装时选择正确的包。`npx synsci` 启动器安装该元包。发布通过 `.github/workflows/publish.yml` 进行。稳定的 macOS 发布版本需要 Developer ID 签名和公证；临时签名的开发包仅限本地使用，绝不会进入稳定更新渠道。Windows 签名仍然是可选的，未签名的 Windows 安装程序会在发布说明中披露。