# 文献检索策略

## 寻找科学证据的有效技巧

全面的文献检索对于将假设建立在现有证据基础上至关重要。本参考资料提供了 PubMed（生物医学文献）和通用科学检索的策略。

## 检索策略框架

### 三阶段方法

1. **广泛探索：** 了解领域全貌并识别关键概念
2. **聚焦检索：** 针对特定机制、理论或发现进行检索
3. **引文挖掘：** 追踪关键论文的参考文献和相关文章

### 检索前准备

**明确检索目标：**
- 该现象的哪些方面需要证据支持？
- 哪些类型的研究最相关（综述、原始研究、方法学）？
- 什么时间范围是相关的（仅近期，还是包含历史背景）？
- 需要什么级别的证据（机制性、相关性、因果性）？

## PubMed 检索策略

### 何时使用 PubMed

将 WebFetch 与 PubMed URL 结合使用，适用于：
- 生物医学和生命科学研究
- 临床研究和医学文献
- 分子、细胞和生理机制
- 疾病病因学和病理学
- 药物和治疗研究

### 有效的 PubMed 检索技巧

#### 1. 从综述文章开始

**原因：** 综述综合了文献、识别关键概念，并提供全面的参考文献列表。

**检索策略：**
- 在检索词中添加“review”
- 使用 PubMed 筛选器：文章类型 → Review、Systematic Review、Meta-Analysis
- 查找近期综述（过去 2-5 年）

**检索示例：**
- `https://pubmed.ncbi.nlm.nih.gov/?term=wound+healing+diabetes+review`
- `https://pubmed.ncbi.nlm.nih.gov/?term=gut+microbiome+cognition+systematic+review`

#### 2. 使用 MeSH 词表（医学主题词表）

**原因：** MeSH 词是标准化的词汇，能够涵盖概念的各种变体。

**策略：**
- PubMed 自动推荐 MeSH 词
- 有助于找到使用不同术语描述同一概念的论文
- 比仅使用关键词检索更全面

**示例：**
- 不要仅使用“heart attack”，而应使用 MeSH 词“Myocardial Infarction”
- 这样可以涵盖使用“MI”、“heart attack”、“cardiac infarction”等术语的论文

#### 3. 布尔运算符和高级语法

**AND：** 缩小检索范围（所有词必须同时出现）
- `diabetes AND wound healing AND inflammation`

**OR：** 扩大检索范围（任一词语出现即可）
- `(Alzheimer OR dementia) AND gut microbiome`

**NOT：** 排除特定词语
- `cancer treatment NOT surgery`

**引号：** 精确短语匹配
- `"oxidative stress"`

**通配符：** 词形变化
- `gene*` 可检索到 gene、genes、genetic、genetics

#### 4. 按出版物类型和日期筛选

**出版物类型：**
- Clinical Trial（临床试验）
- Meta-Analysis（荟萃分析）
- Systematic Review（系统综述）
- Research Support, NIH（NIH 研究资助）
- Randomized Controlled Trial（随机对照试验）

**日期筛选：**
- 近期研究（过去 2-5 年）：前沿发现
- 历史研究：奠基性研究
- 特定时间段：追踪认识发展历程

#### 5. 使用“Similar Articles”和“Cited By”

**策略：**
- 找到一篇高度相关的论文
- 点击“Similar articles”查找相关研究
- 使用引文追踪工具查找基于该研究的更新成果

### 按假设目标分类的 PubMed 检索示例

**机制理解：**
```
https://pubmed.ncbi.nlm.nih.gov/?term=(mechanism+OR+pathway)+AND+[phenomenon]+AND+(molecular+OR+cellular)
```

**因果关系：**
```
https://pubmed.ncbi.nlm.nih.gov/?term=[exposure]+AND+[outcome]+AND+(randomized+controlled+trial+OR+cohort+study)
```

**生物标志物与关联性：**
```
https://pubmed.ncbi.nlm.nih.gov/?term=[biomarker]+AND+[disease]+AND+(association+OR+correlation+OR+prediction)
```

**治疗效果：**
```
https://pubmed.ncbi.nlm.nih.gov/?term=[intervention]+AND+[condition]+AND+(efficacy+OR+effectiveness+OR+clinical+trial)
```

## 通用科学网络检索策略

### 何时使用网络检索

将 WebSearch 用于：
- 非生物医学科学（物理、化学、材料、地球科学）
- 跨学科主题
- 近期预印本和未发表研究
- 灰色文献（技术报告、会议论文集）
- 更广泛的背景和跨领域类比

### 有效的网络检索技巧

#### 1. 使用领域特定检索词

**包含领域专业术语：**
- 化学：“mechanism”、“reaction pathway”、“synthesis”
- 物理学：“model”、“theory”、“experimental validation”
- 材料科学：“properties”、“characterization”、“synthesis”
- 生态学：“population dynamics”、“community structure”

#### 2. 定向检索学术来源

**检索运算符：**
- `site:arxiv.org` - 预印本（物理、计算机科学、数学、定量生物学）
- `site:biorxiv.org` - 生物学预印本
- `site:edu` - 学术机构
- `filetype:pdf` - 学术论文（通常）

**检索示例：**
- `superconductivity high temperature mechanism site:arxiv.org`
- `CRISPR off-target effects site:biorxiv.org`

#### 3. 检索作者和实验室

**当找到相关论文时：**
- 检索该作者的其他研究
- 访问其实验室网站查找未发表研究
- 识别该领域的主要研究团队

#### 4. 使用 Google Scholar 方法

**策略：**
- 使用“Cited by”查找更新的相关研究
- 使用“Related articles”扩展检索范围
- 设置日期范围以聚焦近期研究
- 使用 author: 运算符查找特定研究者

#### 5. 结合通用和特定术语

**结构：**
- 特定现象 + 通用概念
- “tomato plant growth” + “bacterial promotion”
- “cognitive decline” + “gut microbiome”

**布尔逻辑：**
- 使用引号进行精确短语匹配：`"spike protein mutation"`
- 使用 OR 表示替代选项：`(transmissibility OR transmission rate)`
- 组合使用：`"spike protein" AND (transmissibility OR virulence) AND mutation`

## 跨数据库检索策略

### 综合文献检索工作流程

1. **从综述开始（PubMed 或网络检索）：**
   - 识别关键概念和术语
   - 记录有影响力的论文和研究者
   - 了解领域现状

2. **聚焦原始研究（PubMed）：**
   - 检索特定机制
   - 查找实验证据
   - 识别研究方法

3. **通过网络检索扩展范围：**
   - 查找其他领域的相关研究
   - 定位近期预印本
   - 识别类似系统

4. **引文挖掘：**
   - 追踪关键论文的参考文献
   - 使用“cited by”查找近期研究
   - 追踪有影响力的研究

5. **迭代优化：**
   - 添加论文中发现的新术语
   - 结果过多时缩小范围
   - 相关结果过少时扩大范围

## 主题特定检索策略

### 机制与通路

**目标：** 理解某事物如何运作

**检索要素：**
- 现象 + “mechanism”
- 现象 + “pathway”
- 现象 + 疑似涉及的特定分子/通路

**示例：**
- `diabetic wound healing mechanism inflammation`
- `autophagy pathway cancer`

### 关联与相关性

**目标：** 找出哪些因素相互关联

**检索要素：**
- 变量 A + 变量 B + “association”
- 变量 A + 变量 B + “correlation”
- 变量 A + “predicts” + 变量 B

**示例：**
- `vitamin D cardiovascular disease association`
- `gut microbiome diversity predicts cognitive function`

### 干预与治疗

**目标：** 寻找有效性的证据

**检索要素：**
- 干预措施 + 疾病状况 + “efficacy”
- 干预措施 + 疾病状况 + “randomized controlled trial”
- 干预措施 + 疾病状况 + “treatment outcome”

**示例：**
- `probiotic intervention depression randomized controlled trial`
- `exercise intervention cognitive decline efficacy`

### 方法与技术

**目标：** 如何检验假设

**检索要素：**
- 方法名称 + 应用领域
- “How to measure” + 现象
- 技术 + 验证

**示例：**
- `CRISPR screen cancer drug resistance`
- `measure protein-protein interaction methods`

### 类似系统

**目标：** 从相关现象中获取洞见

**检索要素：**
- 机制 + 不同系统
- 类似现象 + 不同生物体/条件

**示例：**
- 如果研究植物-微生物共生：检索 `nitrogen fixation rhizobia legumes`
- 如果研究药物耐药性：检索 `antibiotic resistance evolution mechanisms`

## 评估论文影响力和质量

### 引用次数的重要性

引用次数反映论文在领域内的影响力和重要性。解读引用次数时应考虑论文年龄和领域规范：

| 论文年龄 | 引用次数 | 解读 |
|-----------|-----------|----------------|
| 0-3 年 | 20+ | 值得关注——正在获得关注 |
| 0-3 年 | 100+ | 高度影响——已产生显著影响 |
| 3-7 年 | 100+ | 重要——已确立的贡献 |
| 3-7 年 | 500+ | 里程碑——对领域有重大贡献 |
| 7 年以上 | 500+ | 开创性——被广泛认可的重要研究 |
| 7 年以上 | 1000+ | 奠基性——定义领域的论文 |

**领域特定考量：**
- 生物医学/临床：引用规范较高（NEJM 论文通常 1000+）
- 计算机科学：会议引用比期刊引用更重要
- 数学/物理学：引用规范较低，引用半衰期较长
- 社会科学：引用规范中等，书籍引用率较高

### 期刊影响因子指南

**第一梯队 - 顶级期刊（始终优先）：**
- **综合科学：** Nature（IF ~65）、Science（IF ~55）、Cell（IF ~65）、PNAS（IF ~12）
- **医学：** NEJM（IF ~175）、Lancet（IF ~170）、JAMA（IF ~120）、BMJ（IF ~93）
- **领域旗舰期刊：** Nature Medicine、Nature Biotechnology、Nature Methods、Nature Genetics

**第二梯队 - 高影响力专业期刊（强烈优先）：**
- 影响因子 >10
- 示例：JAMA Internal Medicine、Annals of Internal Medicine、Circulation、Blood
- 顶级 ML/AI 会议：NeurIPS、ICML、ICLR（相当于 IF 15-25）

**第三梯队 - 受尊重的专业期刊（相关时纳入）：**
- 影响因子 5-10
- 成熟的学会期刊
- 收录良好的专业期刊

**第四梯队 - 其他同行评审期刊（谨慎使用）：**
- 影响因子 <5
- 仅在直接相关且无更优来源时引用

### 作者履历评估

优先引用资深研究者的论文：

**强作者指标：**
- **高 h-index：** 成熟领域 >40，早期职业学者 >20
- **多篇第一梯队出版物：** 在 Nature/Science/Cell 系列中有发表记录
- **机构隶属关系：** 顶尖研究型大学和研究所
- **学术认可：** 奖项、学会会员、编辑职位
- **第一/通讯作者：** 在多篇高被引论文中担任

**如何核查作者声誉：**
1. Google Scholar 个人主页：查看 h-index、i10-index、总引用次数
2. PubMed：检索作者姓名，查看发表期刊
3. 机构主页：查看职位、奖项、资助情况
4. ORCID 个人主页：完整的发表历史

### 会议级别认知（计算机科学/人工智能）

对于 ML/AI 和计算机科学主题，会议级别很重要：

**A*（旗舰级）- 相当于 Nature/Science：**
- NeurIPS（神经信息处理系统大会）
- ICML（国际机器学习大会）
- ICLR（国际学习表征大会）
- CVPR（计算机视觉与模式识别大会）
- ACL（计算语言学协会年会）

**A（优秀）- 相当于第二梯队期刊：**
- AAAI、IJCAI（通用人工智能）
- EMNLP、NAACL（自然语言处理）
- ECCV、ICCV（计算机视觉）
- SIGKDD、WWW（数据挖掘）

**B（良好）- 相当于第三梯队期刊：**
- COLING、CoNLL（自然语言处理）
- WACV、BMVC（计算机视觉）
- 大多数 ACM/IEEE 专业会议

## 评估来源质量

### 原始研究质量指标

**强质量信号：**
- 发表于第一或第二梯队期刊
- 相对于论文年龄的引用次数较高
- 由具有良好履历的资深研究者撰写
- 样本量较大（统计功效更高）
- 预注册研究（减少偏倚）
- 适当的对照和方法
- 与其他研究结果一致
- 数据和方法透明

**警示信号：**
- 发表于掠夺性期刊或低影响力期刊
- 作者无既定学术履历
- 未经同行评审（谨慎使用）
- 未披露利益冲突
- 方法描述不清
- 非凡主张缺乏非凡证据
- 与大量证据矛盾且无合理解释

### 综述质量指标

**系统综述（最高质量）：**
- 发表于第一/二梯队期刊（Cochrane、Nature Reviews、Annual Reviews）
- 预定义的检索策略
- 明确的纳入/排除标准
- 对纳入研究进行质量评估
- 定量综合（荟萃分析）

**叙述性综述（质量参差不齐）：**
- 领域专家综合
- 可能存在选择偏倚
- 有助于了解背景和框架
- 核查作者专业水平和引用情况
- 优先选择领域领军人物在第一/二梯队期刊发表的综述

## 文献检索时间管理

### 合理分配检索时间

**对于直接明了的假设（30-60 分钟）：**
- 1-2 篇广泛综述文章
- 3-5 篇定向原始研究论文
- 快速网络检索近期进展

**对于复杂假设（1-3 小时）：**
- 针对不同方面的多篇综述
- 10-15 篇原始研究论文
- 跨数据库系统检索
- 从关键论文进行引文挖掘

**对于有争议的主题（3 小时以上）：**
- 采用系统综述方法
- 识别竞争性观点
- 追踪历史发展
- 交叉验证研究结果

### 边际效益递减

**检索已充分的标志：**
- 反复找到相同的论文
- 新检索大多返回无关论文
- 已有足够证据支持/构建假设背景
- 多条独立的证据链趋于一致

**需要继续检索的情况：**
- 理解上仍存在重大空白
- 矛盾证据需要解决
- 假设与文献似乎不一致
- 需要特定的方法学信息

## 记录检索结果

### 需要捕获的信息

**对每篇相关论文：**
- 完整引文（作者、年份、期刊、标题）
- 与假设相关的关键发现
- 研究设计和方法
- 作者指出的局限性
- 与假设的关联

### 组织研究发现

**按以下方式分组：**
- 支持假设 A、B、C 的证据
- 方法学途径
- 需要解释的矛盾发现
- 当前知识的空白

**综合笔记：**
- 哪些已被充分证实？
- 哪些存在争议或不确定性？
- 其他系统中存在哪些类比？
- 常用方法有哪些？

### 假设报告的引文组织

**报告结构：** 为两类读者组织引文：

**正文（15-20 篇关键引文）：**
- 最具影响力的论文（高被引、开创性研究）
- 近期决定性证据（过去 2-3 年）
- 直接支持每个假设的关键论文（每个假设 3-5 篇）
- 综合领域的主要综述

**附录 A：综合文献综述（40-60+ 篇引文）：**
- **历史背景：** 奠定领域基础的奠基性论文
- **当前认识：** 近期综述和荟萃分析
- **假设特定证据：** 每个假设 8-15 篇论文，涵盖：
  - 直接支持证据
  - 相关系统中的类似机制
  - 方法学先例
  - 理论框架论文
- **矛盾发现：** 代表不同观点的论文
- **知识空白：** 指出局限性或未解决问题的论文

**目标引文密度：** 目标总参考文献数 50+ 篇，为所有主张提供全面支持，并展示充分的文献基础。

**附录 A 的分组策略：**
1. 背景和背景论文
2. 当前认识和已确立的机制
3. 支持每个假设的证据（单独小节）
4. 矛盾或替代性发现
5. 方法学和技术论文

## 实用检索工作流程

### 分步流程

1. **定义检索目标（5 分钟）：**
   - 现象的哪些方面需要证据？
   - 什么可以支持或反驳假设？

2. **广泛综述检索（15-20 分钟）：**
   - 找到 1-3 篇综述文章
   - 浏览摘要评估相关性
   - 记录关键概念和术语

3. **定向原始研究（30-45 分钟）：**
   - 检索特定机制/证据
   - 阅读摘要，浏览图表和结论
   - 追踪最有前景的参考文献

4. **跨领域检索（15-30 分钟）：**
   - 在其他系统中寻找类比
   - 查找近期预印本
   - 识别新兴趋势

5. **引文挖掘（15-30 分钟）：**
   - 追踪关键论文的参考文献
   - 使用“cited by”查找近期研究
   - 识别开创性研究

6. **综合发现（20-30 分钟）：**
   - 总结每个假设的证据
   - 记录模式和矛盾
   - 识别知识空白

### 迭代与优化

**当初始检索不足时：**
- 结果过少时扩大检索词
- 结果过多时添加特定机制/通路
-