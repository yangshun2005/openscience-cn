# OpenScience 文档

OpenScience 的文档站点，这是一个面向科学研究的开源 AI 工作台。站点地址为 [openscience.sh/docs](https://openscience.sh/docs)。

这是一个轻量级的 Vite + React 应用，用于渲染一个 MDX 页面文件夹——无需文档框架、无需 CMS、无需服务器。页面以 `.mdx` 文件形式存放在 `src/content/openscience/` 中，并附带一个驱动侧边栏的 `docs.json`。路由基于哈希（`#/openscience/<page>`），因此整个应用是一个静态单页应用。

## 开发

```bash
bun install                       # 在仓库根目录执行
bun run --cwd frontend/docs dev   # 热重载 .mdx 编辑
```

## 构建

```bash
bun run --cwd frontend/docs build      # 生成 dist/，资源位于 /docs/ 下
bun run --cwd frontend/docs typecheck  # tsc --noEmit
```

## 添加页面

1. 创建 `src/content/openscience/<page>.mdx`，并包含 `title` 和 `description` frontmatter。
2. 将页面添加到 `src/content/openscience/docs.json` 中对应的分组下。
3. 内部链接使用 `/openscience/<page>`；构建时会解析为哈希路由。

## 部署

Vite 的 `base` 设置为 `/docs/`，因此资源 URL 会在 `/docs` 路径下解析。构建命令为 `bun run build`，输出目录为 `dist`，`/docs` 下的深层链接会回退到 `index.html`（参见 `vercel.json`）。合并到 `main` 分支后会自动部署。