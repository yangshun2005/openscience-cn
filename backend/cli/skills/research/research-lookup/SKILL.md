---
name: research-lookup
description: "通过 OpenRouter 使用 Perplexity 的 Sonar Pro Search 或 Sonar Reasoning Pro 模型查找当前研究信息。根据查询复杂度自动选择最佳模型。搜索学术论文、近期研究、技术文档和通用研究信息，并附带引用。"
category: research
allowed-tools: [Read, Write, Edit, Bash]
---

# 研究信息查找

## 概述

此技能支持通过 OpenRouter 使用 Perplexity 的 Sonar 模型进行实时研究信息查找。它能根据查询复杂度智能选择 **Sonar Pro Search**（快速、高效查找）或 **Sonar Reasoning Pro**（深度分析推理）。该技能可访问最新的学术文献、近期研究、技术文档和通用研究信息，并提供正确的引用和来源归属。

## 何时使用此技能

当您需要以下内容时，请使用此技能：

- **当前研究信息**：特定领域的最新研究、论文和发现
- **文献验证**：根据当前研究核实事实、统计数据或论断
- **背景研究**：为科学写作收集背景信息和支持证据
- **引用来源**：查找可在稿件中引用的相关论文和研究
- **技术文档**：查找规格说明、协议或方法论
- **最新进展**：紧跟新兴趋势和突破性进展
- **统计数据**：查找最新统计数据、调查结果或研究发现
- **专家观点**：获取近期访谈、评论或述评中的见解

## 使用科学示意图进行视觉增强

**使用此技能创建文档时，始终考虑添加科学图表和示意图以增强视觉传达效果。**

如果您的文档尚未包含示意图或图表：
- 使用 **scientific-schematics** 技能生成 AI 驱动的出版级图表
- 只需用自然语言描述您想要的图表
- Nano Banana Pro 将自动生成、审查并优化示意图

**对于新文档：** 默认应生成科学示意图，以直观呈现文本中描述的关键概念、工作流程、架构或关系。

**如何生成示意图：**
```bash
python scripts/generate_schematic.py "您的图表描述" -o figures/output.png
```

AI 将自动：
- 创建格式规范的出版级图像
- 通过多次迭代进行审查和优化
- 确保可访问性（色盲友好、高对比度）
- 将输出保存到 figures/ 目录

**何时添加示意图：**
- 研究信息流程图
- 查询处理工作流图示
- 模型选择决策树
- 系统集成架构图
- 信息检索流水线可视化
- 知识综合框架
- 任何受益于可视化的复杂概念

有关创建示意图的详细指导，请参阅 scientific-schematics 技能文档。

---

## 核心能力

### 1. 学术研究查询

**搜索学术文献**：查询特定领域的最新论文、研究和综述：

```
查询示例：
- "Recent advances in CRISPR gene editing 2024"
- "Latest clinical trials for Alzheimer's disease treatment"
- "Machine learning applications in drug discovery systematic review"
- "Climate change impacts on biodiversity meta-analysis"
```

**预期响应格式**：
- 近期文献关键发现摘要
- 引用 3-5 篇最相关的论文，包含作者、标题、期刊和年份
- 突出显示关键统计数据或发现
- 识别研究空白或争议
- 尽可能提供全文链接

### 2. 技术和方法论信息

**协议和方法查询**：查找详细程序、规格和方法论：

```
查询示例：
- "Western blot protocol for protein detection"
- "RNA sequencing library preparation methods"
- "Statistical power analysis for clinical trials"
- "Machine learning model evaluation metrics"
```

**预期响应格式**：
- 分步程序或协议
- 所需材料和设备
- 关键参数和注意事项
- 常见问题排查
- 标准协议或开创性论文的参考文献

### 3. 统计和数据信息

**研究统计**：查找最新统计数据、调查结果和研究数据：

```
查询示例：
- "Prevalence of diabetes in US population 2024"
- "Global renewable energy adoption statistics"
- "COVID-19 vaccination rates by country"
- "AI adoption in healthcare industry survey"
```

**预期响应格式**：
- 带有日期和来源的当前统计数据
- 数据收集方法
- 可用的置信区间或误差范围
- 与往年或基准的比较
- 原始调查或研究的引用

### 4. 引用和参考文献辅助

**查找引用**：定位来自信誉良好的作者和知名出版机构的高影响力、高被引论文：

```
查询示例：
- "Foundational papers on transformer architecture"（预期：Vaswani 等人 2017 年发表于 NeurIPS，被引 90,000+ 次）
- "Seminal works in quantum computing"（预期：Nature、Science 上领先研究者的论文）
- "Key studies on climate change mitigation"（预期：IPCC 引用论文、Nature Climate Change）
- "Landmark trials in cancer immunotherapy"（预期：NEJM、Lancet 试验，被引 1000+ 次）
```

**预期响应格式**：
- 5-10 篇最具影响力的论文，**按影响力和相关性排序**
- 完整的引用信息（作者、标题、期刊、年份、DOI）
- 每篇论文的**被引次数**（如无法精确获取，提供近似值）
- **期刊层级**指示（Nature、Science、Cell = 第一梯队等）
- 每篇论文贡献的简要描述
- 知名作者的**资质信息**（例如，“来自 Hinton 实验室”、“诺贝尔奖得主”）
- 相关期刊的影响因子

**引用选择的质量标准**：
- 优先选择**被引 100+ 次**的论文（针对发表 3 年以上的论文）
- 优先选择**第一梯队期刊**（Nature、Science、Cell、NEJM、Lancet）
- 包含该领域**公认领军人物**的工作
- 平衡**基础性论文**（高被引、较早期）与**近期进展**（新兴、高影响力期刊）

## 自动模型选择

此技能具备基于查询复杂度的**智能模型选择**功能：

### 模型类型

**1. Sonar Pro Search** (`perplexity/sonar-pro-search`)
- **适用场景**：直接的信息查找
- **最适合**：
  - 简单的事实查询
  - 近期出版物搜索
  - 基本协议查询
  - 统计数据检索
- **速度**：响应快速
- **成本**：每次查询成本较低

**2. Sonar Reasoning Pro** (`perplexity/sonar-reasoning-pro`)
- **适用场景**：需要深度推理的复杂分析查询
- **最适合**：
  - 比较分析（“比较 X 与 Y”）
  - 多项研究的综合
  - 评估权衡或争议
  - 解释机制或关系
  - 批判性分析和解读
- **速度**：较慢但更全面
- **成本**：每次查询成本较高，但提供更深入的见解

### 复杂度评估

此技能使用以下指标自动检测查询复杂度：

**推理关键词**（触发 Sonar Reasoning Pro）：
- 分析类：`compare`、`contrast`、`analyze`、`analysis`、`evaluate`、`critique`
- 比较类：`versus`、`vs`、`vs.`、`compared to`、`differences between`、`similarities`
- 综合类：`meta-analysis`、`systematic review`、`synthesis`、`integrate`
- 因果类：`mechanism`、`why`、`how does`、`how do`、`explain`、`relationship`、`causal relationship`、`underlying mechanism`
- 理论类：`theoretical framework`、`implications`、`interpret`、`reasoning`
- 争议类：`controversy`、`conflicting`、`paradox`、`debate`、`reconcile`
- 权衡类：`pros and cons`、`advantages and disadvantages`、`trade-off`、`tradeoff`、`trade offs`
- 复杂类：`multifaceted`、`complex interaction`、`critical analysis`

**复杂度评分**：
- 推理关键词：每个 3 分（权重较高）
- 多个问题：每个问号 2 分
- 复杂句式：每个从句指示词（and、or、but、however、whereas、although）1.5 分
- 超长查询：超过 150 个字符加 1 分
- **阈值**：评分 ≥3 分的查询触发 Sonar Reasoning Pro

**实际效果**：即使只有一个强推理关键词（compare、explain、analyze 等）也会触发更强大的 Sonar Reasoning Pro 模型，确保在需要时获得深度分析。

**查询分类示例**：

✅ **Sonar Pro Search**（直接查找）：
- "Recent advances in CRISPR gene editing 2024"
- "Prevalence of diabetes in US population"
- "Western blot protocol for protein detection"

✅ **Sonar Reasoning Pro**（复杂分析）：
- "Compare and contrast mRNA vaccines vs traditional vaccines for cancer treatment"
- "Explain the mechanism underlying the relationship between gut microbiome and depression"
- "Analyze the controversy surrounding AI in medical diagnosis and evaluate trade-offs"

### 手动覆盖

您可以使用 `force_model` 参数强制指定特定模型：

```python
# 强制使用 Sonar Pro Search 进行快速查找
research = ResearchLookup(force_model='pro')

# 强制使用 Sonar Reasoning Pro 进行深度分析
research = ResearchLookup(force_model='reasoning')

# 自动选择（默认）
research = ResearchLookup()
```

命令行用法：
```bash
# 强制使用 Sonar Pro Search
python research_lookup.py "您的查询" --force-model pro

# 强制使用 Sonar Reasoning Pro
python research_lookup.py "您的查询" --force-model reasoning

# 自动选择（无标志）
python research_lookup.py "您的查询"

# 将输出保存到文件
python research_lookup.py "您的查询" -o results.txt

# 以 JSON 格式输出（适用于编程访问）
python research_lookup.py "您的查询" --json

# 组合：JSON 输出保存到文件
python research_lookup.py "您的查询" --json -o results.json
```

## 技术集成

### OpenRouter API 配置

此技能与 OpenRouter (openrouter.ai) 集成，以访问 Perplexity 的 Sonar 模型：

**模型规格**：
- **模型**：
  - `perplexity/sonar-pro-search`（快速查找）
  - `perplexity/sonar-reasoning-pro-online`（深度分析）
- **搜索模式**：学术/学术模式（优先考虑同行评审来源）
- **搜索上下文**：始终使用 `high` 搜索上下文，以获得更深入、更全面的研究结果
- **上下文窗口**：200K+ tokens，支持全面研究
- **能力**：学术论文搜索、引用生成、学术分析
- **输出**：包含来自学术数据库的引用和来源链接的丰富响应

**API 要求**：
- OpenRouter API 密钥（设置为 `OPENROUTER_API_KEY` 环境变量）
- 账户有足够的研究查询额度
- 正确归属和引用来源

**学术模式配置**：
- 系统消息配置为优先考虑学术来源
- 搜索聚焦于同行评审期刊和学术出版物
- 增强学术参考文献的引用提取
- 偏好近期学术文献（2020-2024）
- 直接访问学术数据库和知识库

### 响应质量和可靠性

**来源验证**：此技能优先考虑：
- 同行评审的学术论文和期刊
- 信誉良好的机构来源（大学、政府机构、非政府组织）
- 近期出版物（优先选择过去 2-3 年内）
- 高影响力期刊和会议
- 一手研究优先于二手来源

**引用标准**：所有响应均包含：
- 完整的书目信息
- 可用的 DOI 或稳定 URL
- 网络来源的访问日期
- 直接引用或数据的明确归属

## 论文质量和影响力优先级

**关键**：搜索论文时，始终优先选择高质量、有影响力的论文，而非冷门或低影响力的出版物。质量比数量更重要。

### 基于引用的排名

根据论文的引用次数与其发表年限的对应关系进行优先排序：

| 论文年限 | 引用阈值 | 分类 |
|-----------|-------------------|----------------|
| 0-3 年 | 20+ 次引用 | 值得关注 |
| 0-3 年 | 100+ 次引用 | 高影响力 |
| 3-7 年 | 100+ 次引用 | 重要 |
| 3-7 年 | 500+ 次引用 | 里程碑式论文 |
| 7 年以上 | 500+ 次引用 | 开创性工作 |
| 7 年以上 | 1000+ 次引用 | 基础性工作 |

**报告引用时**：如已知，始终注明近似引用次数（例如，“被引 500+ 次”或“高被引”）。

### 出版机构质量层级

优先选择来自更高层级出版机构的论文：

**第一梯队 - 顶级出版机构**（始终优先）：
- **综合科学**：Nature、Science、Cell、PNAS
- **医学**：NEJM、Lancet、JAMA、BMJ
- **领域旗舰期刊**：Nature Medicine、Nature Biotechnology、Nature Methods、Nature Genetics、Cell Stem Cell、Immunity
- **顶级 CS/AI**：NeurIPS、ICML、ICLR、ACL、CVPR（适用于 ML/AI 主题）

**第二梯队 - 高影响力专业期刊**（强烈优先）：
- 影响因子 > 10 的期刊
- 子领域的顶级会议（如 EMNLP、NAACL、ECCV、MICCAI）
- 学会旗舰期刊（如 Blood、Circulation、Gastroenterology）

**第三梯队 - 受尊重的专业期刊**（相关时包含）：
- 影响因子 5-10 的期刊
- 该领域成熟会议
- 索引良好的专业期刊

**第四梯队 - 其他同行评审**（谨慎使用）：
- 较低影响力期刊，仅在与主题直接相关且无更好来源时使用

### 作者声誉指标

优先选择来自成熟、信誉良好研究者的论文：

- **资深作者具有较高的 h 指数**（在成熟领域 >40）
- **在第一梯队出版机构发表多篇论文**
- **在公认研究机构担任领导职务**
- **公认的专业知识**：奖项、编辑职位、学会会士
- **领域内里程碑式论文的第一/通讯作者**

### 直接相关性评分

始终优先选择直接回答研究问题的论文：

1. **首要优先级**：直接回答确切研究问题的论文
2. **次要优先级**：具有适用方法、数据或概念框架的论文
3. **第三优先级**：间接相关的论文（仅当来自第一梯队出版机构或高被引时包含）

### 实际应用

进行研究查找时：

1. **从最具影响力的论文开始** - 首先寻找高被引、基础性的工作
2. **优先选择第一梯队出版机构** - Nature、Science、Cell 系列期刊、NEJM、Lancet（医学主题）
3. **检查作者资质** - 优先选择成熟研究团队的工作
4. **平衡新颖性与影响力** - 近期高被引论文 > 早期冷门论文 > 近期未被引论文
5. **报告质量指标** - 在响应中包含引用次数、期刊名称和作者所属机构

**高质量查询响应示例**：
```
高影响力文献的关键发现：

1. Smith 等人 (2023)，Nature Medicine (IF: 82.9，被引 450+ 次)
   - 通讯作者：John Smith 教授，哈佛医学院
   - 关键发现：[发现]

2. Johnson & Lee (2024)，Cell (IF: 64.5，被引 120+ 次)
   - 来自斯坦福大学著名的 Lee 实验室
   - 关键发现：[发现]

3. Chen 等人 (2022)，NEJM (IF: 158.5，被引 890+ 次)
   - 里程碑式临床试验 (N=5,000)
   - 关键发现：[发现]
```

## 查询最佳实践

### 1. 模型选择策略

**对于简单查询（Sonar Pro Search）**：
- 特定主题的近期论文
- 统计数据或患病率
- 标准协议或方法论
- 特定论文的引用查找
- 事实信息检索

**对于复杂分析（Sonar Reasoning Pro）**：
- 比较研究和综合
- 机制解释
- 争议评估
- 权衡分析
- 理论框架
- 多方面关系

**专业提示**：自动选择已针对大多数用例进行优化。仅当您有特定要求或知道查询需要比检测到的更深层推理时，才使用 `force_model`。

### 2. 具体且聚焦的查询

**良好查询**（将触发相应模型）：
- "Randomized controlled trials of mRNA vaccines for cancer treatment 2023-2024" → Sonar Pro Search
- "Compare the efficacy and safety of mRNA vaccines vs traditional vaccines for cancer treatment" → Sonar Reasoning Pro
- "Explain the mechanism by which CRISPR off-target effects occur and strategies to minimize them" → Sonar Reasoning Pro

**不佳查询**：
- "Tell me about AI"（过于宽泛）
- "Cancer research"（缺乏具体性）
- "Latest news"（过于模糊）

### 3. 结构化查询格式

**推荐结构**：
```
[主题] + [具体方面] + [时间范围] + [信息类型]
```

**示例**：
- "CRISPR gene editing + off-target effects + 2024 + clinical trials"
- "Quantum computing + error correction + recent advances + review papers"
- "Renewable energy + solar efficiency + 2023-2024 + statistical data"

### 4. 后续查询

**有效的后续查询**：
- "Show me the full citation for the Smith et al. 2024 paper"
- "What are the limitations of this methodology?"
- "Find similar studies using different approaches"
- "What controversies exist in this research area?"

## 与科学写作的集成

此技能通过以下方式增强科学写作：

1. **文献综述支持**：为引言和讨论部分收集当前研究
2. **方法验证**：根据当前标准验证协议和程序
3. **结果情境化**：将发现与近期类似研究进行比较
4. **讨论增强**：用最新证据支持论点
5. **引用管理**：以多种格式提供格式规范的引用

## 错误处理和局限性

**