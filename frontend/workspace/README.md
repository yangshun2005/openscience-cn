## 使用方法

这些模板的依赖通过 [pnpm](https://pnpm.io) 管理，使用 `pnpm up -Lri` 命令更新。

这就是你会看到 `pnpm-lock.yaml` 文件的原因。不过，任何包管理器都可以使用。克隆模板后，此文件可以安全删除。

```bash
$ npm install # 或 pnpm install 或 yarn install
```

### 在 [Solid 官网](https://solidjs.com) 了解更多信息，并加入我们的 [Discord](https://discord.com/invite/solidjs) 与我们交流。

## 可用脚本

在项目目录中，你可以运行：

### `npm run dev` 或 `npm start`

以开发模式运行应用。<br>
在浏览器中打开 [http://localhost:3000](http://localhost:3000) 查看。

如果你编辑代码，页面将自动重新加载。<br>

### `npm run build`

构建生产版本的应用到 `dist` 文件夹。<br>
它会以生产模式正确打包 Solid，并优化构建以获得最佳性能。

构建后的文件会被压缩，文件名包含哈希值。<br>
你的应用已准备好部署！

## 端到端测试

`bun run test:e2e` 是安全默认选项：它会分配全新的后端、Vite 和模型端口，创建临时沙箱，填充种子数据，并且绝不重用现有的 3000 端口监听器。`test:e2e:local` 是等效的兼容别名。它还会启动一个仅限回环的确定性模型，因此提示/回复的覆盖测试绝不会使用开发者凭据或外部推理服务。直接运行 `playwright test` 会被有意拒绝，因为它无法确定现有监听器归属于哪个后端或检出。

```bash
bunx playwright install
bun run test:e2e
bun run test:e2e -- --grep "settings"
```

要测试已运行或已打包的 OpenScience 服务器，请显式选择加入。外部命令需要 `PLAYWRIGHT_BASE_URL`，不会启动 Vite，并且会从该 URL 推导 SDK 后端主机/端口，除非单独覆盖：

```bash
PLAYWRIGHT_BASE_URL=http://127.0.0.1:4112 bun run test:e2e:external
PLAYWRIGHT_BASE_URL=http://127.0.0.1:4112 bun run test:e2e:packaged
```

显式外部运行的环境选项：

- `PLAYWRIGHT_BASE_URL`（必需的服务器 URL）
- `PLAYWRIGHT_SERVER_HOST` / `PLAYWRIGHT_SERVER_PORT`（可选的 SDK 后端覆盖）

如果无法在主机上安装捆绑的浏览器，请将 `PLAYWRIGHT_CHROMIUM_EXECUTABLE_PATH` 设置为兼容的 Chromium 可执行文件。

## 部署

你可以将 `dist` 文件夹部署到任何静态主机提供商（netlify、surge、now 等）。