---
name: market-research-reports
description: "生成全面的市场研究报告（50页以上），风格对标顶级咨询公司（麦肯锡、波士顿咨询、高德纳）。具备专业的 LaTeX 排版、通过 scientific-schematics 和 generate-image 生成大量可视化内容、与 research-lookup 深度集成以收集数据，并包含波特五力、PESTLE、SWOT、TAM/SAM/SOM 和 BCG 矩阵等多框架战略分析。"
category: research
allowed-tools: [Read, Write, Edit, Bash]
---

# 市场研究报告

## 概述

市场研究报告是全面的战略性文档，用于分析行业、市场和竞争格局，以支持商业决策、投资策略和战略规划。本技能可生成**50页以上的专业级报告**，包含丰富的可视化内容，对标麦肯锡、波士顿咨询、贝恩、高德纳和福睿斯特等顶级咨询公司的交付成果。

**主要特点：**
- **篇幅全面**：报告设计为50页以上，不受篇幅限制
- **内容丰富视觉化**：开始时生成5-6个关键图表（写作过程中根据需要添加更多）
- **数据驱动分析**：与 research-lookup 深度集成以获取市场数据
- **多框架方法**：波特五力、PESTLE、SWOT、BCG 矩阵、TAM/SAM/SOM
- **专业排版**：咨询公司品质的排版、配色和布局
- **可执行的建议**：注重战略重点并附实施路线图

**输出格式：** 采用专业排版的 LaTeX，编译为 PDF。使用 `market_research.sty` 样式包以确保一致、专业的格式。

## 何时使用本技能

在以下情况下应使用本技能：
- 为投资决策创建全面的市场分析
- 为战略规划编制行业报告
- 分析竞争格局和市场动态
- 进行市场规模测算（TAM/SAM/SOM）
- 评估市场进入机会
- 为并购活动准备尽职调查材料
- 创建行业定位的思想领导力内容
- 制定市场进入战略文档
- 分析法规和政策对市场的影响
- 为新产品的发布构建商业案例

## 可视化增强要求

**关键：市场研究报告应包含关键的可视化内容。**

每份报告应在开始时生成**6个基本可视化**，并在写作过程中根据需要添加更多。从最关键的可视化开始，以建立报告框架。

### 可视化生成工具

**使用 `scientific-schematics` 生成：**
- 市场增长轨迹图
- TAM/SAM/SOM 分解图（同心圆）
- 波特五力图
- 竞争定位矩阵
- 市场细分图
- 价值链图
- 技术路线图
- 风险热力图
- 战略优先级矩阵
- 实施时间表/甘特图
- SWOT 分析图
- BCG 增长-份额矩阵

```bash
# 示例：生成 TAM/SAM/SOM 图
python skills/scientific-schematics/scripts/generate_schematic.py \
  "TAM SAM SOM concentric circle diagram showing Total Addressable Market $50B outer circle, Serviceable Addressable Market $15B middle circle, Serviceable Obtainable Market $3B inner circle, with labels and arrows pointing to each segment" \
  -o figures/tam_sam_som.png --doc-type report

# 示例：生成波特五力图
python skills/scientific-schematics/scripts/generate_schematic.py \
  "Porter's Five Forces diagram with center box 'Competitive Rivalry' connected to four surrounding boxes: 'Threat of New Entrants' (top), 'Bargaining Power of Suppliers' (left), 'Bargaining Power of Buyers' (right), 'Threat of Substitutes' (bottom). Each box should show High/Medium/Low rating" \
  -o figures/porters_five_forces.png --doc-type report
```

**使用 `generate-image` 生成：**
- 执行摘要主视觉信息图
- 行业/领域概念插图
- 抽象技术可视化
- 封面图片

```bash
# 示例：生成执行摘要信息图
python skills/generate-image/scripts/generate_image.py \
  "Professional executive summary infographic for market research report, showing key metrics in modern data visualization style, blue and green color scheme, clean minimalist design with icons representing market size, growth rate, and competitive landscape" \
  --output figures/executive_summary.png
```

### 各章节推荐可视化（按需生成）

| 章节 | 优先可视化 | 可选可视化 |
|---------|-----------------|------------------|
| 执行摘要 | 执行摘要信息图（开始） | - |
| 市场规模与增长 | 增长轨迹（开始）、TAM/SAM/SOM（开始） | 区域细分、细分市场增长 |
| 竞争格局 | 波特五力（开始）、定位矩阵（开始） | 市场份额图、战略群组 |
| 风险分析 | 风险热力图（开始） | 缓解矩阵 |
| 战略建议 | 机会矩阵 | 优先级框架 |
| 实施路线图 | 时间表/甘特图 | 里程碑跟踪器 |
| 投资论点 | 财务预测 | 情景分析 |

**从6个优先可视化开始**（如上标记为“开始”），然后在撰写特定章节并需要视觉支持时生成额外的可视化。

---

## 报告结构（50页以上）

### 前置部分（约5页）

#### 封面页（1页）
- 报告标题和副标题
- 主视觉图（已生成）
- 日期和密级
- 编制单位 / 编制人

#### 目录（1-2页）
- 由 LaTeX 自动生成
- 图表目录
- 表格目录

#### 执行摘要（2-3页）
- **市场概览框**：关键指标一览
- **投资论点**：3-5条要点总结
- **主要发现**：重大发现和洞察
- **战略建议**：前3-5条可操作建议
- **执行摘要信息图**：报告亮点的视觉综合

---

### 核心分析（约35页）

#### 第1章：市场概述与定义（4-5页）

**内容要求：**
- 市场定义和范围
- 行业生态系统映射
- 关键利益相关者及其角色
- 市场边界和相邻领域
- 历史背景和演变

**必备可视化（2个）：**
1. 市场生态系统/价值链图
2. 行业结构图

**关键数据点：**
- 市场定义标准
- 包含/排除的细分市场
- 地理范围
- 分析的时间跨度

---

#### 第2章：市场规模与增长分析（6-8页）

**内容要求：**
- 总体可寻址市场（TAM）计算
- 可服务可寻址市场（SAM）定义
- 可获得服务市场（SOM）估算
- 历史增长分析（5-10年）
- 增长预测（未来5-10年）
- 增长驱动因素和抑制因素
- 区域市场细分
- 细分市场层面分析

**必备可视化（4个）：**
1. 市场增长轨迹图（历史+预测）
2. TAM/SAM/SOM 同心圆图
3. 区域市场细分（饼图或矩形树图）
4. 细分市场增长对比（柱状图）

**关键数据点：**
- 当前市场规模（注明来源）
- CAGR（历史和预测）
- 各区域市场规模
- 各细分市场规模
- 预测的关键假设

**数据来源：**
使用 `research-lookup` 查找：
- 市场研究报告（Gartner、Forrester、IDC 等）
- 行业协会数据
- 政府统计数据
- 公司财务报告
- 学术研究

---

#### 第3章：行业驱动因素与趋势（5-6页）

**内容要求：**
- 宏观经济因素
- 技术趋势
- 监管驱动因素
- 社会和人口结构变化
- 环境因素
- 行业特定趋势

**分析框架：**
- **PESTLE 分析**：政治、经济、社会、技术、法律、环境
- **趋势影响评估**：可能性 vs 影响矩阵

**必备可视化（3个）：**
1. 行业趋势时间线或雷达图
2. 驱动因素影响矩阵
3. PESTLE 分析图

**关键数据点：**
- 前5-10个增长驱动因素及其量化影响
- 新兴趋势及时间线
- 颠覆性因素

---

#### 第4章：竞争格局（6-8页）

**内容要求：**
- 市场结构分析
- 主要参与者概况
- 市场份额分析
- 竞争定位
- 进入壁垒
- 竞争动态

**分析框架：**
- **波特五力**：全面的行业分析
- **竞争定位矩阵**：关键维度的2x2矩阵
- **战略群组映射**：按战略对竞争对手进行聚类

**必备可视化（4个）：**
1. 波特五力图
2. 市场份额饼图或柱状图
3. 竞争定位矩阵（2x2）
4. 战略群组图

**关键数据点：**
- 各公司市场份额（前10名）
- 竞争强度评级
- 进入壁垒评估
- 供应商/买方议价能力评估

---

#### 第5章：客户分析与细分（4-5页）

**内容要求：**
- 客户细分定义
- 细分市场规模和增长
- 购买行为分析
- 客户需求和痛点
- 决策过程
- 各细分市场的价值驱动因素

**分析框架：**
- **客户细分矩阵**：规模 vs 增长
- **价值主张画布**：任务、痛点、收益
- **客户旅程映射**：从认知到推荐

**必备可视化（3个）：**
1. 客户细分分解（饼图/矩形树图）
2. 细分市场吸引力矩阵
3. 客户旅程或价值主张图

**关键数据点：**
- 细分市场规模和百分比
- 各细分市场增长率
- 平均交易规模/每客户收入
- 各细分市场客户获取成本

---

#### 第6章：技术与创新格局（4-5页）

**内容要求：**
- 当前技术栈
- 新兴技术
- 创新趋势
- 技术采用曲线
- 研发投入分析
- 专利格局

**分析框架：**
- **技术就绪度评估**：TRL 等级
- **炒作周期定位**：技术所处阶段
- **技术路线图**：随时间演变

**必备可视化（2个）：**
1. 技术路线图
2. 创新/采用曲线或炒作周期

**关键数据点：**
- 行业研发支出
- 关键技术里程碑
- 专利申请趋势
- 技术采用率

---

#### 第7章：法规与政策环境（3-4页）

**内容要求：**
- 当前监管框架
- 主要监管机构
- 合规要求
- 即将出台的监管变化
- 政策趋势
- 影响评估

**必备可视化（1个）：**
1. 监管时间线或框架图

**关键数据点：**
- 关键法规及生效日期
- 合规成本
- 监管风险
- 政策变化可能性

---

#### 第8章：风险分析（3-4页）

**内容要求：**
- 市场风险
- 竞争风险
- 监管风险
- 技术风险
- 运营风险
- 财务风险
- 风险缓解策略

**分析框架：**
- **风险热力图**：概率 vs 影响
- **风险登记册**：全面的风险清单
- **缓解矩阵**：风险 vs 缓解策略

**必备可视化（2个）：**
1. 风险热力图（概率 vs 影响）
2. 风险缓解矩阵

**关键数据点：**
- 前10大风险及评级
- 风险概率评分
- 影响严重程度评分
- 缓解成本估算

---

### 战略建议（约10页）

#### 第9章：战略机会与建议（4-5页）

**内容要求：**
- 机会识别
- 机会规模测算
- 战略选项分析
- 优先级框架
- 详细建议
- 成功因素

**分析框架：**
- **机会吸引力矩阵**：吸引力 vs 获胜能力
- **战略选项框架**：构建、购买、合作、忽略
- **优先级矩阵**：影响 vs 投入

**必备可视化（3个）：**
1. 机会矩阵
2. 战略选项框架
3. 优先级/建议矩阵

**关键数据点：**
- 机会规模
- 投资要求
- 预期回报
- 实现价值的时间线

---

#### 第10章：实施路线图（3-4页）

**内容要求：**
- 分阶段实施计划
- 关键里程碑和交付成果
- 资源需求
- 时间线和排序
- 依赖关系和关键路径
- 治理结构

**必备可视化（2个）：**
1. 实施时间表/甘特图
2. 里程碑跟踪器或阶段图

**关键数据点：**
- 各阶段持续时间
- 资源需求
- 关键里程碑及日期
- 各阶段预算分配

---

#### 第11章：投资论点与财务预测（3-4页）

**内容要求：**
- 投资摘要
- 财务预测
- 情景分析
- 回报预期
- 关键假设
- 敏感性分析

**必备可视化（2个）：**
1. 财务预测图（收入、增长）
2. 情景分析对比

**关键数据点：**
- 收入预测（3-5年）
- CAGR 预测
- ROI/IRR 预期
- 关键财务假设

---

### 后置部分（约5页）

#### 附录A：方法论与数据来源（1-2页）
- 研究方法
- 数据收集方法
- 数据来源和引用
- 局限性和假设

#### 附录B：详细市场数据表（2-3页）
- 全面的市场数据表
- 区域细分
- 细分市场详情
- 历史数据序列

#### 附录C：公司概况（1-2页）
- 主要竞争对手的简要概况
- 财务亮点
- 战略重点领域

#### 参考文献/参考书目
- 所有引用来源
- BibTeX 格式（用于 LaTeX）

---

## 工作流程

### 阶段1：研究与数据收集

**步骤1：定义范围**
- 明确市场定义
- 设定地理边界
- 确定时间跨度
- 确定需要回答的关键问题

**步骤2：进行深度研究**

广泛使用 `research-lookup` 收集市场数据：

```bash
# 市场规模和增长数据
python skills/research-lookup/scripts/research_lookup.py \
  "What is the current market size and projected growth rate for [MARKET] industry? Include TAM, SAM, SOM estimates and CAGR projections"

# 竞争格局
python skills/research-lookup/scripts/research_lookup.py \
  "Who are the top 10 competitors in the [MARKET] market? What is their market share and competitive positioning?"

# 行业趋势
python skills/research-lookup/scripts/research_lookup.py \
  "What are the major trends and growth drivers in the [MARKET] industry for 2024-2030?"

# 监管环境
python skills/research-lookup/scripts/research_lookup.py \
  "What are the key regulations and policy changes affecting the [MARKET] industry?"
```

**步骤3：数据整理**
- 创建 `sources/` 文件夹存放研究笔记
- 按章节组织数据
- 识别数据缺口
- 根据需要开展后续研究

### 阶段2：分析与框架应用

**步骤4：应用分析框架**

对每个框架进行结构化分析：

- **市场规模测算**：TAM → SAM → SOM，附明确假设
- **波特五力**：对每种力量进行高/中/低评级并说明理由
- **PESTLE**：分析每个维度及其趋势和影响
- **SWOT**：内部优势/劣势，外部机会/威胁
- **竞争定位**：定义坐标轴，绘制竞争对手位置

**步骤5：形成洞察**
- 将发现综合为关键洞察
- 识别战略影响
- 制定建议
- 对机会进行优先级排序

### 阶段3：可视化生成

**步骤6：生成所有可视化**

在撰写报告**之前**生成可视化。使用批量生成脚本：

```bash
# 生成所有标准市场报告可视化
python skills/market-research-reports/scripts/generate_market_visuals.py \
  --topic "[MARKET NAME]" \
  --output-dir figures/
```

或单独生成：

```bash
# 1. 市场增长轨迹
python skills/scientific-schematics/scripts/generate_schematic.py \
  "Bar chart showing market growth from 2020 to 2034, with historical bars in dark blue (2020-2024) and projected bars in light blue (2025-2034). Y-axis shows market size in billions USD. Include CAGR annotation" \
  -o figures/01_market_growth.png --doc-type report

# 2. TAM/SAM/SOM 分解
python skills/scientific-schematics/scripts/generate_schematic.py \
  "TAM SAM SOM concentric circles diagram. Outer circle TAM Total Addressable Market, middle circle SAM Serviceable Addressable Market, inner circle SOM Serviceable Obtainable Market. Each labeled with acronym and description. Blue gradient" \
  -o figures/02_tam_sam_som.png --doc-type report

# 3. 波特五力
python skills/scientific-schematics/scripts/generate_schematic.py \
  "Porter's Five Forces diagram with center box 'Competitive Rivalry' connected to four surrounding boxes: Threat of New Entrants (top), Bargaining Power of Suppliers (left), Bargaining Power of Buyers (right), Threat of Substitutes (bottom). Color code by rating: High=red, Medium=yellow, Low=green" \
  -o figures/03_porters_five_forces.png --doc-type report

# 4. 竞争定位矩阵
python skills/scientific-schematics/scripts/generate_schematic.py \
  "2x2 competitive positioning matrix with X-axis 'Market Focus (Niche to Broad)' and Y-axis 'Solution Approach (Product to Platform)'. Plot 8-10 competitors as labeled circles of varying sizes. Include quadrant labels" \
  -o figures/04_competitive_positioning.png --doc-type report
```