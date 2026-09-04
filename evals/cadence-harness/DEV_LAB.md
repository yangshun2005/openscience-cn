# 精简研究开发实验室

本实验室直接运行源代码，并将其项目、配置、凭据、缓存、状态和轨迹保存在发布安装之外。它从不从常规的 OpenScience 配置文件中复制凭据，并且 `bun --no-env-file` 可防止仓库中的 `.env` 文件成为隐藏的凭据来源。

## 首次启动

在此工作树中，通过交互式提供商流程保存实验室的模型凭据。以交互方式粘贴可使其不进入 shell 历史记录，并且仅将其写入实验室数据根目录：

```bash
bun evals/cadence-harness/dev-lab.ts auth
```

然后在单独的终端中运行后端和工作区：

```bash
bun evals/cadence-harness/dev-lab.ts server
bun evals/cadence-harness/dev-lab.ts workspace
```

后端默认监听 `127.0.0.1:4196`；工作区默认监听 `127.0.0.1:4444`。`OPENSCIENCE_DEV_PORT`、`OPENSCIENCE_DEV_ROOT` 和 `OPENSCIENCE_DEV_MODEL` 可覆盖这些默认值，而无需在此仓库中存储机密值。

## 一次一条轨迹

```bash
bun evals/cadence-harness/dev-lab.ts run P11
bun evals/cadence-harness/dev-lab.ts run P15
bun evals/cadence-harness/dev-lab.ts run P21
bun evals/cadence-harness/dev-lab.ts run P23
bun evals/cadence-harness/dev-lab.ts run P24
```

每次调用都会在 `~/.openscience-dev/researchagent-test/campaigns` 下创建一个独立的 campaign。如果监听后端的源代码 SHA 或工作树指纹与当前检出不一致，它将拒绝运行。健康标识还会记录确切的后端进程运行 ID，因此同一端口上的过期服务器会在每条轨迹中可见。

新的 harness 项目会立即归档，因此即使运行被中断，评估工作也不会填充 Home 的活动项目列表。它们的文件和会话仍可在“已归档”和 campaign 证据中获取。现有项目绝不会按名称被识别、归档或删除。

运行器具有传输超时和范围限定的权限策略。它不会施加任意的模型调用、工具调用、子代理或成本预算。可选的诊断上限可通过 `--max-events`、`--max-tool-calls` 和 `--max-child-agents` 使用；除非显式提供，否则它们默认关闭。提示中写入的资源约束仍然具有权威性。直接 MCP、原始 Modal、外部目录和环境变更权限仍被拒绝；Modal 工作必须通过受信任的 `compute_job` 能力进行。

使用 `bun evals/cadence-harness/dev-lab.ts paths` 检查活动的非机密路径和 URL。