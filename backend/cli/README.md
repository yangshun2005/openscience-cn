# @synsci/openscience

OpenScience 是一个与模型无关的开源 AI 研究代理，适用于科学和机器学习工程工作。它在您的浏览器中运行一个工作区，代理可以在其中规划任务、编写和运行代码、驱动实验、查询科学数据库并撰写结果。您可以自带 API 密钥，使用符合条件的 ChatGPT/Codex 访问权限，或运行本地模型。

属于 [OpenScience](https://github.com/synthetic-sciences/OpenScience) 仓库的一部分。

## 安装

```bash
npm install -g @synsci/openscience
```

命令为 `openscience`。

在 Linux 上，捆绑的运行时需要内核 5.1 或更高版本。Glibc 二进制文件需要 glibc 2.17 或更高版本；系统会自动选择单独的 musl 包。CentOS 7 自带的 3.10 内核不受支持。在 Linux ARM64 上，Bun 编译的可执行文件目前需要 4 KB 内核页大小；16 KB 和 64 KB 页大小的内核会提前失败并显示清晰的诊断信息，同时 [上游支持](https://github.com/oven-sh/bun/issues/17627) 仍在进行中。

## 快速开始

```bash
openscience                     # 在浏览器中打开工作区
openscience ~/code/project      # 在特定目录中打开
openscience connect             # 在本地连接 ChatGPT / Codex 订阅
openscience run "..."           # 运行一次性任务
```

配置存放在 `~/.config/openscience/openscience.json` 中。提供商密钥可以在工作区中设置，并保留在此设备上。默认技能、学习技能、已安装技能和项目技能均为本地存储。

## 文档

请参阅 [仓库 README](https://github.com/synthetic-sciences/OpenScience#readme) 了解完整的布局、提供商设置、代理和技能架构以及贡献指南。

## 许可证

Apache License 2.0。请参阅 [LICENSE](https://github.com/synthetic-sciences/OpenScience/blob/main/LICENSE)。与 Anthropic 无关联。