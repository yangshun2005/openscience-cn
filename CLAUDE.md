# CLAUDE.md: OpenScience

## 项目概述

**OpenScience (`openscience`)** 是一个开源、模型无关的 AI 研究代理，用于机器学习工程和科学工作。基于 Bun 和 TypeScript 构建，以原生二进制形式发布，支持 Linux、macOS 和 Windows。

- **npm 包**：`@synsci/openscience`
- **二进制名称**：`openscience`
- **配置目录**：`~/.config/openscience/`（可通过 `OPENSCIENCE_CONFIG_DIR` 覆盖）
- **数据根目录**：默认为 `~/.openscience/`（可重新定位；旧版 `synsc` 数据会自动导入）
- **配置文件**：`openscience.json`
- **提供商 ID**：`synsci`（Atlas 线路合约，请勿重命名）

## 仓库结构

按运行时边界组织的单一 Git 仓库。

```text
frontend/          workspace（浏览器 UI）、文档站点和共享 UI
backend/           CLI/服务器、技能、会话和提供商集成
tooling/           SDK、插件运行时、仓库自动化、启动器、工具和补丁
```

## 开发

```bash
# 以开发模式运行 CLI
bun run dev

# 构建所有平台二进制文件
cd backend/cli && bun run build

# 类型检查
bun run typecheck

# 运行测试
cd backend/cli && bun test
```

## 提示架构（双层）

CLI 使用**双层提示系统**：提供商级系统提示 + 代理级工作流提示。

```
带有代理名称的用户请求（例如“research”）
  │
  ├─ 第 1 层：SYSTEM 角色 ← 提供商中立的产物合约
  │   src/session/system.ts 向每个模型提供同一合约
  │
  └─ 第 2 层：USER 角色注入 ← 代理提示（任务特定）
      src/session/prompt.ts 根据代理名称和层级选择
```

### 会话提示（`src/session/prompt/`）

| 文件                                | 用途                                  |
| ----------------------------------- | ---------------------------------------- |
| `core.txt`                          | 提供商中立操作合约      |
| `plan.txt`                          | 只读 Plan 模式合约             |
| `build-switch.txt`、`max-steps.txt` | 模式转换和步骤限制工具 |

路由逻辑：`src/session/system.ts` 向每个模型提供相同的产物合约。

### 代理提示（`src/agent/prompt/`）

| 文件                    | 活动角色                                    |
| ----------------------- | ---------------------------------------------- |
| `research.txt`          | `research`，唯一的用户面向入口     |
| `explore.txt`           | 隐藏的 Explore 配置文件和兼容性别名 |
| `biology.txt`           | 隐藏的领域兼容性配置文件            |
| `physics.txt`           | 隐藏的领域兼容性配置文件            |
| `ml.txt`                | 隐藏的领域兼容性配置文件            |
| `write.txt`             | 隐藏的写作兼容性配置文件           |
| `literature-review.txt` | 隐藏的文献综述兼容性配置文件 |
| `critique.txt`          | 隐藏的评论兼容性配置文件          |
| `physics-critique.txt`  | 隐藏的物理评论兼容性配置文件  |
| `compaction.txt`        | 隐藏的系统代理                            |
| `title.txt`             | 隐藏的系统代理                            |

`execute` 使用共享的执行合约，而非单独的提示文件。Plan 模式位于 `src/session/prompt/plan.txt`。`src/session/prompt.ts` 中的路由逻辑注入 Research 努力合约并保留隐藏的兼容性提示。

### 代理注册表（`src/agent/agent.ts`）

使用 `Agent.Info` Schema 定义内置代理：`name`、`mode`（primary/subagent/all）、`hidden`、`model`、`prompt`、`permission`、`temperature`、`steps`。

**默认入口**：`research`（唯一的用户面向默认值；也是 plan 退出目标）
**内部任务配置文件**：`explore`、`execute`（隐藏；按工作类型而非领域品牌选择）
**模式**：`plan`（只读）
**兼容性配置文件**（隐藏）：`task`、`biology`、`physics`、`ml`、`write`、`literature-review`、`critique`、`physics-critique`
**系统代理**：`compaction`、`title`

可通过配置文件（`openscience.json` → `agent` 键）添加自定义代理。参见 `src/cli/cmd/agent.ts` 了解创建 CLI。

## RCA 与调试指南

### 代理行为异常？追踪提示链：

1. **哪个代理处于活动状态？** → `src/agent/agent.ts`，按名称查找代理，检查其 `mode`、`model`、`prompt` 字段
2. **注入了哪个提示？** → `src/session/prompt.ts`，跟踪 `input.agent.name` 开关
3. **哪个系统提示？** → `src/session/system.ts`，`SystemPrompt.provider(model)` 返回共享的产物合约

### 常见故障模式：

| 症状                               | 可能原因                                                        | 查看位置                                              |
| ------------------------------------- | ------------------------------------------------------------------- | ---------------------------------------------------------- |
| 代理过度处理简单请求 | 工作流提示过于程序化                                   | `src/agent/prompt/{agent}.txt`，保留自适应行为 |
| 使用了错误的模型                      | 代理/模型配置不正确                                        | `src/agent/agent.ts` + `openscience.json` `agent` 配置   |
| 代理过度委派           | 委派姿态或独立工作指导回退           | `src/tool/task.txt` + `src/session/prompt.ts`              |
| 委派循环或停滞            | 任务配置文件、容量队列或持久尝试合约回退 | `src/tool/task.ts` + `src/session/loop-state.ts`           |
| 子代理返回空内容               | 上下文耗尽、提供商故障或自定义代理步骤限制  | `src/agent/agent.ts` + 子会话跟踪                 |
| 自定义代理未出现            | 配置不在 `openscience.json` 中或 `mode` 错误                    | 配置文件 `agent` 键 → `src/agent/agent.ts`             |

### 提示调试的关键文件（请先阅读这些）：

```
src/agent/agent.ts          # 代理定义，存在哪些代理及其配置
src/agent/prompt/*.txt      # 代理行为，代理被告知要做什么
src/session/prompt.ts       # 路由，哪个提示被注入到哪个代理
src/session/system.ts       # 提供商路由，哪个系统提示用于哪个模型
```

## 风格指南

完整风格指南请参见 `AGENTS.md`。要点：

- 优先使用 `const` 而非 `let`，避免使用 `else`，使用单词级变量名
- 使用 Bun API（`Bun.file()` 等）
- 依赖类型推断，避免显式注解
- 测试中不使用 mock，测试真实实现
- 不使用 `any` 类型