# OpenScience 桌面版

桌面外壳会在随机回环端口启动捆绑的 OpenScience 运行时，并在原生窗口中打开现有工作区。它绝不会向工作区暴露 Node API。

发布版本会生成：

- macOS `.dmg` 安装程序和 `.zip` 自更新负载（Apple Silicon 和 Intel）
- Windows NSIS `.exe`
- Linux `.AppImage`

在运行 `bun run dist` 之前，请将 `OPENSCIENCE_DESKTOP_SIDECAR` 设置为原生运行时。当存在 `CSC_LINK` 和 `CSC_KEY_PASSWORD` 时，Electron Builder 会自动签名。macOS 公证额外使用 `APPLE_ID`、`APPLE_APP_SPECIFIC_PASSWORD` 和 `APPLE_TEAM_ID`。稳定的生产版本需要这些凭据，并对应用包及其外部 DMG 安装程序进行签名、公证和盖章。

只有经过公证的 Developer ID 构建才能参与桌面自更新。它会从已发布的、非预发布版本的 GitHub 发布版本中下载特定架构的 ZIP；验证 GitHub 的 SHA-256 摘要、应用身份、版本、公证和发布者连续性；然后使用捆绑的签名 sidecar 进行原子交接。稳定发布会在发布路径上保留一个打包的更新程序冒烟测试；完整的 Apple Silicon 和 Intel 生命周期/回滚矩阵保留在深度 CI 中。临时签名的开发构建仍可用于本地打包检查，但绝不会作为稳定的更新负载发布，也无法自更新。