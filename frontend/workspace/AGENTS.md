## 调试

- 切勿尝试重启应用或服务器进程。

## 本地开发

- 如需进行本地 UI 更改，请分别运行后端和应用开发服务器。
- 后端（在 `backend/cli` 目录下）：`bun run --conditions=browser ./src/index.ts serve --port 4096`
- 应用（在 `frontend/workspace` 目录下）：`bun dev -- --port 4444`
- 打开 `http://localhost:4444` 验证 UI 更改（该地址会指向位于 `http://localhost:4096` 的后端服务）。

## SolidJS

- 始终优先使用 `createStore`，而非多个 `createSignal` 调用

## 工具调用

- 适用情况下，务必使用并行工具。

## 浏览器自动化

使用 `agent-browser` 进行 Web 自动化。运行 `agent-browser --help` 查看所有命令。

核心工作流程：

1. `agent-browser open <url>` - 导航至页面
2. `agent-browser snapshot -i` - 获取带引用（@e1、@e2）的交互元素
3. `agent-browser click @e1` / `fill @e2 "text"` - 使用引用进行交互
4. 页面更改后重新获取快照