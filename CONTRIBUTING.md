# 为 OpenScience 做贡献

感谢您对贡献的兴趣。以下类型的更改最有可能被合并：

- 错误修复
- 新的 LSP 和格式化程序
- 更好的模型性能
- 对新提供商的支持
- 针对特定环境问题的修复
- 缺失的标准行为
- 文档改进

任何 UI 或核心产品功能在您构建之前，都需要与维护者进行设计讨论。如果您不确定某个更改是否会被接受，请在 Issue 中提问，或查找带有 [`help wanted`](https://github.com/synthetic-sciences/OpenScience/issues?q=is%3Aissue+state%3Aopen+label%3A%22help+wanted%22)、[`good first issue`](https://github.com/synthetic-sciences/OpenScience/issues?q=is%3Aissue+state%3Aopen+label%3A%22good+first+issue%22) 或 [`bug`](https://github.com/synthetic-sciences/OpenScience/issues?q=is%3Aissue+state%3Aopen+label%3Abug) 标签的 Issue。

## 开发

您需要 Bun 1.3 或更高版本。安装依赖并从源码运行 CLI：

```bash
bun install
bun dev
```

`bun dev` 是构建后的 `openscience` 命令的本地等价物。默认情况下，它针对 `backend/cli` 目录运行。要在其他位置运行：

```bash
bun dev <directory>     # 在特定目录中运行
bun dev .               # 在仓库根目录中运行
```

常用命令在开发模式和构建后的二进制文件中工作方式相同：

```bash
bun dev --help          # 列出命令
bun dev serve           # 无头 API 服务器（默认端口 4096）
bun dev web             # 启动服务器并打开工作区
```

### 检查

在推送之前，请运行与 CI 相同的门禁检查——类型检查、测试和格式化：

```bash
bun run typecheck
bun test --cwd backend/cli
bunx prettier --check .
```

有关完整列表（包括工作区构建），请参阅 [docs/notes/verification.md](docs/notes/verification.md)。

### 构建独立二进制文件

```bash
./backend/cli/script/build.ts --single
./backend/cli/dist/@synsci/openscience-<platform>/bin/openscience
```

将 `<platform>` 替换为您的平台，例如 `darwin-arm64` 或 `linux-x64`。

### 代码结构

- `backend/cli`：CLI、服务器和核心逻辑。
- `frontend/workspace`：工作区 UI，使用 SolidJS 编写。
- `frontend/ui`：共享 UI 组件和主题。
- `frontend/docs`：文档源码。
- `frontend/landing`：[openscience.sh](https://openscience.sh) 的营销网站。
- `tooling/plugin`：`@synsci/plugin` 的源码。
- `tooling/sdk/js`：TypeScript SDK。
- `tooling/launcher`：`npx synsci` 安装程序。

### 处理工作区 UI

启动服务器，然后运行 UI 开发服务器：

```bash
bun dev serve
bun run --cwd frontend/workspace dev
```

UI 开发服务器会打印其本地 URL（通常为 http://localhost:3000）。API 服务器必须运行才能实现完整功能。

如果您更改了 API 或 SDK（例如 `backend/cli/src/server/server.ts`），请运行 `./tooling/repo/generate.ts` 以重新生成 SDK 和相关文件。

### 处理文档或落地页

文档站点是 `frontend/docs`，营销站点是 `frontend/landing`。使用其开发服务器运行任一站点：

```bash
bun run --cwd frontend/docs dev
bun run --cwd frontend/landing dev
```

文档页面位于 `frontend/docs/src/content/openscience/` 下，格式为 MDX；请保持它们为纯 Markdown——MDX 解析器已弃用，这些文件已从 Prettier 中排除。

请遵循[样式指南](./AGENTS.md)。

## Pull Requests

### 关联 Issue

在打开 Pull Request 之前，请先打开一个 Issue，并使用 `Fixes #123` 或 `Closes #123` 引用它。对于小型修复，一个简短的 Issue 就足够了。没有关联 Issue 的 Pull Request 可能会被关闭。

### 保持精简

- 保持 Pull Request 小而专注。
- 解释问题以及您的更改为何能修复它。
- 在添加行为之前，检查该行为是否已存在于其他位置。

### 展示您的工作

对于 UI 更改，请包含前后对比截图或短视频。对于逻辑更改，请说明您如何验证更改：您测试了什么，以及审阅者如何复现结果。

### 自己撰写

用您自己的话写简短的描述。Issue 和 Pull Request 中冗长的生成文本可能会被忽略。如果您无法简要解释更改，则可能更改过大。

### Pull Request 标题

遵循约定式提交，可带可选范围：

- `feat:` 新功能
- `fix:` 错误修复
- `docs:` 文档更改
- `chore:` 维护和依赖更新
- `refactor:` 无行为变更的重构
- `test:` 测试
- `ci:` CI 和发布工作流更改

示例：`docs: update contributing guide`、`fix: resolve crash on startup`、`feat(app): add dark mode`。

### 样式

这些是指导原则，而非硬性规则：

- 将逻辑保持在一个函数中，除非拆分能带来真正的复用。
- 避免不必要的解构。
- 避免使用 `else`。
- 在可读性好的情况下，优先使用 `.catch(...)` 而不是 `try`/`catch`。
- 使用精确的类型，避免使用 `any`。
- 优先使用不可变值，避免使用 `let`。
- 选择简洁、描述性的名称。
- 在合适的情况下使用 Bun 辅助函数，如 `Bun.file()`。

## 功能请求

对于新功能，请从设计对话开始。打开一个 Issue，描述问题、可选建议方案，以及为什么它属于 OpenScience。在打开功能 Pull Request 之前，请等待维护者的同意。