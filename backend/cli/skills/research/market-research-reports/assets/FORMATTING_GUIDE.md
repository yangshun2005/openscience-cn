# 市场研究报告格式指南

使用 `market_research.sty` 样式包的快速参考。

## 调色板

### 主色
| 颜色名称 | RGB | 十六进制 | 用途 |
|------------|-----|-----|-------|
| `primaryblue` | (0, 51, 102) | `#003366` | 标题、页眉、链接 |
| `secondaryblue` | (51, 102, 153) | `#336699` | 小节标题、次要元素 |
| `lightblue` | (173, 216, 230) | `#ADD8E6` | 关键洞察框背景 |
| `accentblue` | (0, 120, 215) | `#0078D7` | 强调高亮、机会框 |

### 辅助色
| 颜色名称 | RGB | 十六进制 | 用途 |
|------------|-----|-----|-------|
| `accentgreen` | (0, 128, 96) | `#008060` | 市场数据框、积极指标 |
| `lightgreen` | (200, 230, 201) | `#C8E6C9` | 市场数据框背景 |
| `warningorange` | (255, 140, 0) | `#FF8C00` | 风险框、警告 |
| `alertred` | (198, 40, 40) | `#C62828` | 严重风险 |
| `recommendpurple` | (103, 58, 183) | `#673AB7` | 建议框 |

### 中性色
| 颜色名称 | RGB | 十六进制 | 用途 |
|------------|-----|-----|-------|
| `darkgray` | (66, 66, 66) | `#424242` | 正文文本 |
| `mediumgray` | (117, 117, 117) | `#757575` | 次要文本 |
| `lightgray` | (240, 240, 240) | `#F0F0F0` | 背景、标注框 |
| `tablealt` | (245, 247, 250) | `#F5F7FA` | 表格交替行 |

---

## 框环境

### 关键洞察框（蓝色）
用于主要发现、洞察和重要发现。

```latex
\begin{keyinsightbox}[自定义标题]
在日益增长的企业采用率和有利的监管环境推动下，
预计到2030年市场将以15.3%的复合年增长率增长。
\end{keyinsightbox}
```

### 市场数据框（绿色）
用于市场统计、指标和数据亮点。

```latex
\begin{marketdatabox}[市场概览]
\begin{itemize}
    \item \textbf{市场规模（2024年）：} \marketsize{452亿}
    \item \textbf{预计规模（2030年）：} \marketsize{987亿}
    \item \textbf{复合年增长率：} \growthrate{15.3}
\end{itemize}
\end{marketdatabox}
```

### 风险框（橙色/警告）
用于风险因素、警告和注意事项。

```latex
\begin{riskbox}[市场风险]
欧盟的监管变化可能在未来18个月内影响40%的
市场参与者。
\end{riskbox}
```

### 严重风险框（红色）
用于高严重性或关键风险。

```latex
\begin{criticalriskbox}[严重：供应链中断]
重大供应链中断可能导致6-12个月的延迟
和30%的成本增加。
\end{criticalriskbox}
```

### 建议框（紫色）
用于战略建议和行动项目。

```latex
\begin{recommendationbox}[战略建议]
\begin{enumerate}
    \item 优先进入亚太地区市场
    \item 与本地分销商建立战略合作伙伴关系
    \item 投资于产品本地化
\end{enumerate}
\end{recommendationbox}
```

### 标注框（灰色）
用于定义、注释和补充信息。

```latex
\begin{calloutbox}[定义：TAM]
可寻址市场总量（TAM）代表在实现100%市场份额的情况下
可获得的全部收入机会。
\end{calloutbox}
```

### 执行摘要框
用于执行摘要亮点的特殊样式。

```latex
\begin{executivesummarybox}[执行摘要]
报告的主要发现和亮点...
\end{executivesummarybox}
```

### 机会框（青色/强调蓝）
用于机会和积极发现。

```latex
\begin{opportunitybox}[增长机会]
亚太市场代表着一个150亿美元的机会，
以22%的复合年增长率增长。
\end{opportunitybox}
```

### 框架框
用于战略分析框架。

```latex
% SWOT分析
\begin{swotbox}[SWOT分析摘要]
内容...
\end{swotbox}

% 波特五力模型
\begin{porterbox}[波特五力分析]
内容...
\end{porterbox}
```

---

## 引用块

用于突出重要统计数据或引文。

```latex
\begin{pullquote}
“人工智能与医疗保健的融合代表着到2034年
1990亿美元的机会。”
\end{pullquote}
```

---

## 统计框

用于突出关键统计数据（以3个为一排使用）。

```latex
\begin{center}
\statbox{\$452亿}{2024年市场规模}
\statbox{15.3\%}{2024-2030年复合年增长率}
\statbox{23\%}{市场领导者份额}
\end{center}
```

---

## 自定义命令

### 高亮文本
```latex
\highlight{重要文本}  % 蓝色粗体
```

### 市场规模格式化
```latex
\marketsize{452亿}   % 输出：绿色 $452亿
```

### 增长率格式化
```latex
\growthrate{15.3}           % 输出：绿色 15.3%
```

### 风险指标
```latex
\riskhigh{}     % 输出：红色 高
\riskmedium{}   % 输出：橙色 中
\risklow{}      % 输出：绿色 低
```

### 评级星级（1-5）
```latex
\rating{4}      % 输出：★★★★☆
```

### 趋势指标
```latex
\trendup{}      % 绿色向上三角形
\trenddown{}    % 红色向下三角形
\trendflat{}    % 灰色向右箭头
```

---

## 表格格式化

### 带交替行的标准表格
```latex
\begin{table}[htbp]
\centering
\caption{各地区市场规模}
\begin{tabular}{@{}lrrr@{}}
\toprule
\textbf{地区} & \textbf{规模} & \textbf{份额} & \textbf{复合年增长率} \\
\midrule
北美 & \$182亿 & 40.3\% & 12.5\% \\
\rowcolor{tablealt} 欧洲 & \$121亿 & 26.8\% & 14.2\% \\
亚太 & \$105亿 & 23.2\% & 18.7\% \\
\rowcolor{tablealt} 世界其他地区 & \$44亿 & 9.7\% & 11.3\% \\
\midrule
\textbf{总计} & \textbf{\$452亿} & \textbf{100\%} & \textbf{15.3\%} \\
\bottomrule
\end{tabular}
\label{tab:regional}
\end{table}
```

### 带趋势指标的表格
```latex
\begin{tabular}{@{}lrrl@{}}
\toprule
\textbf{公司} & \textbf{收入} & \textbf{份额} & \textbf{趋势} \\
\midrule
公司A & \$52亿 & 15.3\% & \trendup{} +12\% \\
公司B & \$48亿 & 14.1\% & \trenddown{} -3\% \\
公司C & \$42亿 & 12.4\% & \trendflat{} +1\% \\
\bottomrule
\end{tabular}
```

---

## 图片格式化

### 标准图片
```latex
\begin{figure}[htbp]
\centering
\includegraphics[width=0.9\textwidth]{../figures/market_growth.png}
\caption{市场增长轨迹（2020-2030年）}
\label{fig:growth}
\end{figure}
```

### 带来源标注的图片
```latex
\begin{figure}[htbp]
\centering
\includegraphics[width=0.85\textwidth]{../figures/market_share.png}
\caption{市场份额分布（2024年）}
\figuresource{公司年报、行业分析}
\label{fig:market_share}
\end{figure}
```

---

## 列表格式化

### 项目符号列表
```latex
\begin{itemize}
    \item 第一项（自动蓝色项目符号）
    \item 第二项
    \item 第三项
\end{itemize}
```

### 编号列表
```latex
\begin{enumerate}
    \item 第一项（蓝色编号）
    \item 第二项
    \item 第三项
\end{enumerate}
```

### 嵌套列表
```latex
\begin{itemize}
    \item 主要观点
    \begin{itemize}
        \item 子观点A
        \item 子观点B
    \end{itemize}
    \item 另一个主要观点
\end{itemize}
```

---

## 标题页

### 使用自定义标题命令
```latex
\makemarketreporttitle
    {市场标题}              % 报告标题
    {此处为副标题}             % 副标题
    {../figures/cover.png}      % 主图（留空则不显示图片）
    {2025年1月}              % 日期
    {市场情报团队}  % 作者/编制方
```

### 手动标题页
有关完整的手动标题页代码，请参阅模板。

---

## 附录部分

```latex
\appendix

\chapter{方法论}

\appendixsection{数据来源}
显示在目录中的内容...
```

---

## 常见模式

### 市场概览部分
```latex
\begin{marketdatabox}[市场概览]
\begin{itemize}
    \item \textbf{当前市场规模：} \marketsize{452亿}
    \item \textbf{预计规模（2030年）：} \marketsize{987亿}
    \item \textbf{复合年增长率：} \growthrate{15.3}
    \item \textbf{最大细分市场：} 企业级（42\% 份额）
    \item \textbf{增长最快地区：} 亚太（\growthrate{22.1} 复合年增长率）
\end{itemize}
\end{marketdatabox}
```

### 风险登记摘要
```latex
\begin{table}[htbp]
\centering
\caption{风险评估摘要}
\begin{tabular}{@{}llccl@{}}
\toprule
\textbf{风险} & \textbf{类别} & \textbf{概率} & \textbf{影响} & \textbf{评级} \\
\midrule
市场颠覆 & 市场 & 高 & 高 & \riskhigh{} \\
\rowcolor{tablealt} 监管变化 & 监管 & 中 & 高 & \riskhigh{} \\
新进入者 & 竞争 & 中 & 中 & \riskmedium{} \\
\rowcolor{tablealt} 技术过时 & 技术 & 低 & 高 & \riskmedium{} \\
货币波动 & 财务 & 中 & 低 & \risklow{} \\
\bottomrule
\end{tabular}
\end{table}
```

### 竞争对比表
```latex
\begin{table}[htbp]
\centering
\caption{竞争对比}
\begin{tabular}{@{}lccccc@{}}
\toprule
\textbf{因素} & \textbf{公司A} & \textbf{公司B} & \textbf{公司C} & \textbf{公司D} \\
\midrule
市场份额 & \rating{5} & \rating{4} & \rating{3} & \rating{2} \\
\rowcolor{tablealt} 产品质量 & \rating{4} & \rating{5} & \rating{3} & \rating{4} \\
价格竞争力 & \rating{3} & \rating{3} & \rating{5} & \rating{4} \\
\rowcolor{tablealt} 创新能力 & \rating{5} & \rating{4} & \rating{2} & \rating{3} \\
客户服务 & \rating{4} & \rating{4} & \rating{4} & \rating{5} \\
\bottomrule
\end{tabular}
\end{table}
```

---

## 故障排除

### 框内容溢出
如果框内容溢出页面，请拆分为多个框或使用分页符：
```latex
\newpage
\begin{keyinsightbox}[续...]
```

### 图片位置
使用 `[htbp]` 进行灵活定位，或使用 `[H]`（需要 `float` 包）进行精确定位：
```latex
\begin{figure}[H]  % 需要 \usepackage{float}
```

### 表格过宽
使用 `\resizebox` 或 `adjustbox`：
```latex
\resizebox{\textwidth}{!}{
\begin{tabular}{...}
...
\end{tabular}
}
```

### 颜色不显示
确保 `xcolor` 包已加载并带有 `[table]` 选项（样式文件中已包含）。

---

## 编译

使用 XeLaTeX 编译以获得最佳效果：
```bash
xelatex report.tex
bibtex report
xelatex report.tex
xelatex report.tex
```

或使用 latexmk：
```bash
latexmk -xelatex report.tex
```