# 假设生成报告 - 格式快速参考

## 概述

本指南为使用假设生成 LaTeX 模板和样式包提供快速参考。完整文档请参阅 `SKILL.md`。

## 快速开始

```latex
% !TEX program = xelatex
\documentclass[11pt,letterpaper]{article}
\usepackage{hypothesis_generation}
\usepackage{natbib}

\title{你的现象名称}
\begin{document}
\maketitle
% 你的内容
\end{document}
```

**编译：** 使用 XeLaTeX 或 LuaLaTeX 以获得最佳效果
```bash
xelatex your_document.tex
bibtex your_document
xelatex your_document.tex
xelatex your_document.tex
```

## 配色方案参考

### 假设颜色
- **假设 1**：深蓝色（RGB：0, 102, 153）- 用于第一个假设
- **假设 2**：森林绿（RGB：0, 128, 96）- 用于第二个假设
- **假设 3**：皇家紫（RGB：102, 51, 153）- 用于第三个假设
- **假设 4**：蓝绿色（RGB：0, 128, 128）- 用于第四个假设（如需要）
- **假设 5**：焦橙色（RGB：204, 85, 0）- 用于第五个假设（如需要）

### 辅助颜色
- **预测**：琥珀色（RGB：255, 191, 0）- 用于可检验的预测
- **证据**：浅蓝色（RGB：102, 178, 204）- 用于支持性证据
- **比较**：钢灰色（RGB：108, 117, 125）- 用于关键比较
- **局限性**：珊瑚红（RGB：220, 53, 69）- 用于局限性/挑战

## 自定义框环境

### 1. 执行摘要框

```latex
\begin{summarybox}[执行摘要]
  此处填写内容
\end{summarybox}
```

**用途：** 文档开头的高层概述

---

### 2. 假设框（5 种变体）

```latex
\begin{hypothesisbox1}[假设 1：标题]
  \textbf{机制解释：}
  [2-3 段解释 HOW 和 WHY]
  
  \textbf{关键支持证据：}
  \begin{itemize}
    \item 证据点 1 \citep{ref1}
    \item 证据点 2 \citep{ref2}
  \end{itemize}
  
  \textbf{核心假设：}
  \begin{enumerate}
    \item 假设 1
    \item 假设 2
  \end{enumerate}
\end{hypothesisbox1}
```

**可用框：** `hypothesisbox1`、`hypothesisbox2`、`hypothesisbox3`、`hypothesisbox4`、`hypothesisbox5`

**用途：** 展示每个竞争性假设及其机制、证据和假设前提

**4 页正文最佳实践：**
- 机制解释仅保留 1-2 个简短段落（最多 6-10 句话）
- 包含 2-3 个最关键的带引用的证据点
- 列出 1-2 个最关键的假设前提
- 确保每个假设具有真正的区分度
- 所有详细解释移至附录 A
- **在每个假设框前使用 `\newpage` 以防止内容溢出**
- 每个完整的假设框应 ≤0.6 页

---

### 3. 预测框

```latex
\begin{predictionbox}[预测：假设 1]
  \textbf{预测 1.1：} [具体预测]
  \begin{itemize}
    \item \textbf{条件：} 此预测适用的时间/地点
    \item \textbf{预期结果：} 具体的可测量结果
    \item \textbf{证伪标准：} 什么会推翻该预测
  \end{itemize}
\end{predictionbox}
```

**用途：** 展示从每个假设推导出的可检验预测

**4 页正文最佳实践：**
- 尽可能使预测具体且定量化
- 明确说明预测成立的条件
- 始终指定证伪标准
- 正文中每个假设仅包含 1-2 个最关键的预测
- 其他预测移至附录

---

### 4. 证据框

```latex
\begin{evidencebox}[支持性证据]
  讨论支持性证据的内容
\end{evidencebox}
```

**用途：** 突出关键支持性证据或文献综述

**最佳实践：**
- 正文中谨慎使用（详细证据移至附录 A）
- 所有证据均需包含引用
- 聚焦最有说服力的证据

---

### 5. 比较框

```latex
\begin{comparisonbox}[H1 vs. H2：关键区别]
  \textbf{根本差异：}
  [核心差异的描述]
  
  \textbf{判别性实验：}
  [实验描述]
  
  \textbf{结果解读：}
  \begin{itemize}
    \item \textbf{如果 [结果 A]：} 支持 H1
    \item \textbf{如果 [结果 B]：} 支持 H2
  \end{itemize}
\end{comparisonbox}
```

**用途：** 解释如何区分竞争性假设

**最佳实践：**
- 聚焦根本的机制差异
- 提出清晰、可行的判别性实验
- 明确具体的结果解读
- 为所有主要假设对创建比较

---

### 6. 局限性框

```latex
\begin{limitationbox}[局限性与挑战]
  局限性讨论
\end{limitationbox}
```

**用途：** 突出重要的局限性或挑战

**最佳实践：**
- 当局限性特别重要时使用
- 诚实地面对挑战
- 建议如何应对局限性

---

## 文档结构

### 正文（最多 4 页 - 高度简洁）

1. **执行摘要**（0.5-1 页）
   - 使用 `summarybox`
   - 简要现象概述
   - 用一句话列出每个假设
   - 推荐方法

2. **竞争性假设**（2-2.5 页）
   - 使用 `hypothesisbox1`、`hypothesisbox2` 等
   - 每个假设一个框
   - 简要机制解释（1-2 段）+ 关键证据（2-3 点）+ 核心假设前提（1-2 个）
   - 目标：3-5 个假设
   - 保持高度简洁 - 详细信息移至附录

3. **可检验预测**（0.5-1 页）
   - 为每个假设使用 `predictionbox`
   - 每个假设仅包含 1-2 个最关键的预测
   - 非常简短 - 完整预测移至附录

4. **关键比较**（0.5-1 页）
   - 仅对最高优先级的比较使用 `comparisonbox`
   - 展示如何区分最重要的假设
   - 其他比较移至附录

**正文总计：最多 4 页 - 请极其审慎地选择放入此部分的内容**

### 附录（全面、详细）

**附录 A：综合文献综述**
- 详细背景（广泛引用）
- 当前认知
- 每个假设的证据（详细）
- 矛盾发现
- 知识空白
- **目标：40-60+ 条引用**

**附录 B：详细实验设计**
- 每个假设的完整方案
- 方法、对照、样本量
- 统计方法
- 可行性评估
- 时间线和资源需求

**附录 C：质量评估**
- 详细评估表格
- 优势与劣势分析
- 比较评分
- 建议

**附录 D：补充证据**
- 类似机制
- 初步数据
- 理论框架
- 历史背景

**参考文献**
- **目标：总计 50+ 条参考文献**

## 引用最佳实践

### 正文中
- 引用 15-20 篇关键论文
- 使用 `\citep{author2023}` 进行括号引用
- 使用 `\citet{author2023}` 进行文本内引用
- 聚焦最重要/最新的证据

### 附录中
- 总计引用 40-60+ 篇论文
- 全面覆盖相关文献
- 包含综述、原始研究、理论性论文
- 为每个论断和证据提供引用

### 引用密度指南
- 主要假设框：每框 2-3 条引用（仅最关键的）
- 正文总计：最多 10-15 条引用（保持简洁）
- 附录 A 文献部分：每个小节 8-15 条引用
- 实验设计：方法/先例 2-5 条引用
- 质量评估：根据需要引用评估标准
- 全文总计：50+ 条引用（绝大多数在附录中）

## 表格

### 专业表格格式

```latex
\begin{hypotable}{标题}
\begin{tabular}{|l|l|l|}
\hline
\tableheadercolor
\textcolor{white}{\textbf{表头 1}} & \textcolor{white}{\textbf{表头 2}} \\
\hline
数据行 1 & 数据 \\
\hline
\tablerowcolor  % 交替灰色背景
数据行 2 & 数据 \\
\hline
\end{tabular}
\caption{你的标题}
\end{hypotable}
```

**最佳实践：**
- 使用 `\tableheadercolor` 设置表头行
- 超过 3 行的表格使用 `\tablerowcolor` 交替行色
- 保持表格可读性（不要太宽）
- 用于质量评估、比较

## 常见格式模式

### 假设章节模式

```latex
% 在假设框前使用 \newpage 以防止内容溢出
\newpage
\subsection*{假设 N：[简洁标题]}

\begin{hypothesisboxN}[假设 N：[标题]]

\textbf{机制解释：}

[1-2 个简短解释段落 - 最多 6-10 句话]

\vspace{0.3cm}

\textbf{关键支持证据：}
\begin{itemize}
  \item [证据 1] \citep{ref1}
  \item [证据 2] \citep{ref2}
  \item [证据 3] \citep{ref3}
\end{itemize}

\vspace{0.3cm}

\textbf{核心假设前提：}
\begin{enumerate}
  \item [假设前提 1]
  \item [假设前提 2]
\end{enumerate}

\end{hypothesisboxN}

\vspace{0.5cm}
```

**注意：** 假设框前的 `\newpage` 确保其从新页面开始，防止内容溢出。当框包含大量内容时尤其重要。

### 预测章节模式

```latex
\subsection*{来自假设 N 的预测}

\begin{predictionbox}[预测：假设 N]

\textbf{预测 N.1：} [陈述]
\begin{itemize}
  \item \textbf{条件：} [条件]
  \item \textbf{预期结果：} [结果]
  \item \textbf{证伪标准：} [证伪标准]
\end{itemize}

\vspace{0.2cm}

\textbf{预测 N.2：} [陈述]
[... 继续 ...]

\end{predictionbox}
```

### 比较章节模式

```latex
\subsection*{区分假设 X 与假设 Y}

\begin{comparisonbox}[HX vs. HY：关键区别]

\textbf{根本差异：}

[核心差异的描述]

\vspace{0.3cm}

\textbf{判别性实验：}

[实验描述]

\vspace{0.3cm}

\textbf{结果解读：}
\begin{itemize}
  \item \textbf{如果 [结果 A]：} 支持 HX
  \item \textbf{如果 [结果 B]：} 支持 HY
  \item \textbf{如果 [结果 C]：} 两者均支持/均不支持
\end{itemize}

\end{comparisonbox}
```

## 间距与布局

### 垂直间距
- `\vspace{0.3cm}` - 框内元素之间
- `\vspace{0.5cm}` - 主要章节或框之间
- `\vspace{1cm}` - 标题之后、正文内容之前

### 分页与溢出预防

**关键：防止内容溢出**

LaTeX 框（tcolorbox 环境）不会自动跨页。超出剩余页面空间的内容将导致溢出和格式问题。请遵循以下指南：

1. **在长框前使用策略性分页：**
```latex
\newpage  % 如果框较长，从新页面开始
\begin{hypothesisbox1}[假设 1：标题]
  % 此处为大量内容
\end{hypothesisbox1}
```

2. **监控框内容长度：**
   - 每个假设框最多 ≤0.7 页
   - 如果机制解释 + 证据 + 假设前提超过约 0.6 页，则内容过长
   - 解决方案：将详细内容移至附录，正文框中仅保留核心内容

3. **何时使用 `\newpage`：**
   - 在任何包含超过 3 个子部分或超过 15 行内容的假设框之前
   - 在包含大量实验描述的比较框之前
   - 在主要附录章节之间
   - 如果当前页面剩余空间不足 0.6 页且即将开始新框

4. **正文内容长度指南：**
   - 执行摘要框：最多 0.5-0.8 页
   - 每个假设框：最多 0.4-0.6 页
   - 每个预测框：最多 0.3-0.5 页
   - 每个比较框：最多 0.4-0.6 页

5. **拆分长内容：**
   ```latex
   % 良好：简洁的正文加分页符
   \newpage
   \begin{hypothesisbox1}[假设 1：简短标题]
   \textbf{机制解释：}
   用 1-2 段简要概述（6-10 句话）。
   
   \textbf{关键支持证据：}
   \begin{itemize}
     \item 证据 1 \citep{ref1}
     \item 证据 2 \citep{ref2}
   \end{itemize}
   
   \textbf{核心假设前提：}
   \begin{enumerate}
     \item 假设前提 1
   \end{enumerate}
   
   详细机制和全面证据请参阅附录 A。
   \end{hypothesisbox1}
   ```

   ```latex
   % 不佳：过长内容将导致溢出
   \begin{hypothesisbox1}[假设 1]
   \subsection{很长的章节}
   多个段落...
   \subsection{另一个长章节}
   更多段落...
   \subsection{更多内容}
   [内容超出页面边界 → 溢出！]
   \end{hypothesisbox1}
   ```

6. **分页命令：**
   - `\newpage` - 强制新页（推荐在长框之前使用）
   - `\clearpage` - 强制新页并刷新浮动体（在附录前使用）

### 章节间距
样式包已处理，但你可以调整：
```latex
\vspace{0.5cm}  % 如需额外空间
```

## 故障排除

### 常见问题

**问题："File hypothesis_generation.sty not found"**
- 解决方案：确保 .sty 文件与 .tex 文件在同一目录中，或位于 LaTeX 搜索路径中

**问题：框没有颜色**
- 解决方案：使用 XeLaTeX 或 LuaLaTeX 编译，而非 pdfLaTeX
- 命令：`xelatex yourfile.tex`

**问题：引用显示为 [?]**
- 解决方案：在第一次 xelatex 编译后运行 bibtex
```bash
xelatex yourfile.tex
bibtex yourfile
xelatex yourfile.tex
xelatex yourfile.tex
```

**问题：找不到字体**
- 解决方案：如果未安装自定义字体，请注释掉 .sty 文件中的字体行
- 需要注释的行：`\setmainfont{...}` 和 `\setsansfont{...}`

**问题：框标题与内容重叠**
- 解决方案：在标题后使用 `\vspace{0.3cm}` 增加更多垂直空间

**问题：表格过宽**
- 解决方案：在 tabular 前使用 `\small` 或 `\footnotesize`，或使用 `p{width}` 列规格

**问题：内容溢出页面**
- **原因：** 框（tcolorbox 环境）过长，无法适应当前剩余页面空间
- **解决方案 1：** 在框前添加 `\newpage` 使其从新页面开始
- **解决方案 2：** 减少框内容 - 将详细信息移至附录
- **解决方案 3：** 将内容拆分为多个较小的框
- **预防：** 保持每个假设框最多 0.4-0.6 页；在包含大量内容的框前充分使用 `\newpage`

**问题：正文超过 4 页**
- **原因：** 框中包含过多详细信息
- **解决方案：** 积极将内容移至附录 - 正文框应仅包含：
  - 简要机制概述（1-2 段）
  - 2-3 条关键证据要点
  - 1-2 个核心假设前提
- 所有详细解释、额外证据和全面讨论应放入附录 A

### 包要求

确保已安装以下包：
- `tcolorbox`（使用 `most` 选项）
- `xcolor`
- `fontspec`（用于 XeLaTeX/LuaLaTeX）
- `fancyhdr`
- `titlesec`
- `enumitem`
- `booktabs`
- `natbib`

安装缺失的包：
```bash
# 对于 TeX Live
tlmgr install tcolorbox xcolor fontspec fancyhdr titlesec enumitem booktabs natbib

# 对于 MiKTeX（Windows）
# 使用 MiKTeX 包管理器 GUI
```

## 样式一致性提示

1. **颜色使用**
   - 在整个文档中始终为每个假设使用相同颜色
   - H1 = 蓝色，H2 = 绿色，H3 = 紫色，以此