# landing

OpenScience 的营销网站——[openscience.sh](https://openscience.sh) 背后的源码。

独立的 Vite + React + Tailwind 项目（不属于 monorepo bun workspace 的一部分，因此其依赖保持隔离）。整个页面是一个文件：`src/pages/Landing.tsx`，样式由 `src/index.css` 定义（暖暗色调、自托管 CMU Concrete、抖动/颗粒/氛围工具类、滚动显现效果）。

```bash
bun install
bun run dev              # 本地预览
bun run build            # 生产构建 → dist/
```

`public/install` 在 `openscience.sh/install` 路径下提供服务，因此 `curl -fsSL https://openscience.sh/install | bash` 可以正常工作。`src/assets/` 中的截图来自真实的工作区 UI。

`public/install-desktop` 是无证书的 macOS 引导程序。它会验证发布版本的校验和和应用身份，将应用安装到 Applications 文件夹，移除下载的 quarantine 属性，并启动经过验证的副本。

合并到 `main` 分支后，会通过关联的 Vercel 项目自动部署。如需手动进行生产部署，请运行 `vercel deploy --prod`。