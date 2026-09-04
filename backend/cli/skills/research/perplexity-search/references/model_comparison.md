# Perplexity 模型对比

通过 OpenRouter 可用的不同 Perplexity 模型指南，以及各自的使用场景。

## 可用模型

所有 Perplexity 模型均通过 OpenRouter 访问，格式如下：
`openrouter/perplexity/[model-name]`

### Sonar Pro Search

**模型 ID**：`openrouter/perplexity/sonar-pro-search`

**最适合：**
- 复杂的多步骤研究问题
- 需要深度分析和综合的查询
- 需要全面探索来源的场景
- 跨多个领域的比较分析
- 需要智能体推理流程的研究

**特点：**
- 最先进的智能体搜索系统
- 执行多步骤推理流程
- 使用工具和中间查询
- 提供最全面的答案
- 因处理量大，成本较高

**使用场景：**
- “对竞争性 CAR-T 细胞疗法方案进行全面分析，包括机制差异、临床结果和成本效益”
- “从多个指标维度比较量子计算药物发现方法与传统计算方法”
- 需要综合多个来源的研究问题

**定价**（约）：
- 输入：$3/百万 tokens
- 输出：$15/百万 tokens
- 请求费：每 1000 次请求 $18

**上下文窗口**：200K tokens

### Sonar Pro

**模型 ID**：`openrouter/perplexity/sonar-pro`

**最适合：**
- 通用研究和搜索
- 性能和成本的平衡
- 标准科学查询
- 快速信息收集
- 大多数使用场景

**特点：**
- 比基础 Sonar 有增强能力
- 质量和成本的良好平衡
- 对大多数查询可靠
- 比 Pro Search 更快
- 推荐的默认选择

**使用场景：**
- “CRISPR 碱基编辑的最新进展是什么？”
- “总结近期阿尔茨海默病治疗的临床试验”
- “解释 Transformer 架构在现代 LLM 中如何工作”
- 标准文献检索
- 技术文档查询

**定价**（约）：
- 成本低于 Pro Search
- 性价比良好

**上下文窗口**：200K tokens

### Sonar

**模型 ID**：`openrouter/perplexity/sonar`

**最适合：**
- 基础搜索和查询
- 对成本敏感的应用
- 简单事实查找
- 高容量查询
- 快速查找

**特点：**
- 性能扎实的基础模型
- 最具成本效益的选择
- 更快的响应时间
- 适合直接查询
- 准确度低于 Pro 系列

**使用场景：**
- “阿司匹林的分子量是多少？”
- “CRISPR-Cas9 何时首次用于人类？”
- “列出糖尿病的主要症状”
- 简单事实验证
- 基础信息检索

**定价**（约）：
- 成本最低的选择
- 最适合高容量简单查询

**上下文窗口**：200K tokens

### Sonar Reasoning Pro

**模型 ID**：`openrouter/perplexity/sonar-reasoning-pro`

**最适合：**
- 复杂逻辑推理任务
- 多步骤问题解决
- 需要逐步思考的技术分析
- 数学或计算问题
- 需要显式推理链的查询

**特点：**
- 高级推理能力
- 展示逐步思考过程
- 更适合分析型任务
- 擅长技术问题解决
- 输出结构更清晰

**使用场景：**
- “逐步讲解如何设计一个测试新型癌症疗法的临床试验”
- “分析不同蛋白质折叠算法的计算复杂度”
- “推理多个基因与疾病表型关联的分子机制”
- 多步骤技术故障排查
- 复杂系统的逻辑分析

**定价**（约）：
- 因推理能力成本较高
- 对复杂分析任务物有所值

**上下文窗口**：200K tokens

### Sonar Reasoning

**模型 ID**：`openrouter/perplexity/sonar-reasoning`

**最适合：**
- 基础推理任务
- 成本效益高的分析查询
- 较简单的逻辑问题
- 逐步解释

**特点：**
- 基础推理能力
- 比 Reasoning Pro 更实惠
- 适合中等复杂度任务
- 展示逻辑思考过程

**使用场景：**
- “解释疫苗效力计算背后的逻辑”
- “逐步讲解基本统计分析步骤”
- 简单分析问题
- 教学性解释

**定价**（约）：
- 成本低于 Reasoning Pro
- 基础推理的良好平衡

**上下文窗口**：200K tokens

## 模型选择指南

### 决策树

```
您的查询是否复杂且需要深入的多步骤分析？
├─ 是 → 使用 Sonar Pro Search
└─ 否 → 继续

您的查询是否需要显式的逐步推理？
├─ 是 → 使用 Sonar Reasoning Pro（复杂）或 Sonar Reasoning（简单）
└─ 否 → 继续

这是标准的研究或信息查询吗？
├─ 是 → 使用 Sonar Pro（推荐默认）
└─ 否 → 继续

这是简单的查找事实或基础查询吗？
├─ 是 → 使用 Sonar（成本效益高）
└─ 否 → 使用 Sonar Pro（安全默认）
```

### 按使用场景

| 使用场景 | 推荐模型 | 备选模型 |
|----------|----------|----------|
| 文献综述 | Sonar Pro | Sonar Pro Search |
| 快速事实核查 | Sonar | Sonar Pro |
| 复杂分析 | Sonar Pro Search | Sonar Reasoning Pro |
| 分步教程 | Sonar Reasoning Pro | Sonar Pro |
| 成本敏感的大批量查询 | Sonar | Sonar Pro |
| 一般研究 | Sonar Pro | Sonar |
| 技术调试 | Sonar Reasoning Pro | Sonar Pro |
| 比较分析 | Sonar Pro Search | Sonar Pro |

### 按领域

**生物医学研究：**
- 默认：Sonar Pro
- 复杂机制：Sonar Reasoning Pro
- 文献综合：Sonar Pro Search
- 快速查找：Sonar

**计算科学：**
- 默认：Sonar Pro
- 算法分析：Sonar Reasoning Pro
- 技术文档：Sonar Pro
- 基础语法：Sonar

**药物发现：**
- 默认：Sonar Pro
- 多靶点分析：Sonar Pro Search
- 机制推理：Sonar Reasoning Pro
- 化合物性质：Sonar

**临床研究：**
- 默认：Sonar Pro
- 试验设计：Sonar Reasoning Pro
- 证据综合：Sonar Pro Search
- 基础指南：Sonar

## 性能特征

### 响应时间

**从最快到最慢：**
1. Sonar（最快）
2. Sonar Pro
3. Sonar Reasoning
4. Sonar Reasoning Pro
5. Sonar Pro Search（最慢，因多步骤处理）

**注意事项：**
- 对时间敏感的查询，使用 Sonar 或 Sonar Pro
- 对全面分析，接受较慢的 Sonar Pro Search
- 推理模型因显式思考步骤而较慢

### 质量与成本的权衡

**质量层级**（从高到低）：
1. Sonar Pro Search
2. Sonar Reasoning Pro
3. Sonar Pro
4. Sonar Reasoning
5. Sonar

**成本层级**（从高到低）：
1. Sonar Pro Search
2. Sonar Reasoning Pro
3. Sonar Pro
4. Sonar Reasoning
5. Sonar

**建议**：以 Sonar Pro 为默认起点。复杂查询升级到 Pro Search，简单查找降级到 Sonar。

### 准确性和全面性

**最全面：**
- Sonar Pro Search：探索多个来源，深度综合
- Sonar Reasoning Pro：彻底的逐步分析

**最准确：**
- Sonar Pro Search：最佳来源验证和交叉检查
- Sonar Pro：对大多数查询可靠

**足够用：**
- Sonar：对简单事实和基础查询足够

## 特殊注意事项

### 上下文窗口

所有模型支持 200K token 上下文窗口：
- 足以满足大多数查询
- 可处理长文档或多个来源
- 对非常大的分析考虑分块处理

### 温度设置

不同模型受益于不同的温度设置：

**Sonar Pro Search：**
- 默认：0.2（更聚焦、分析性更强）
- 事实性查询使用更低值（0.0-0.1）
- 创造性综合使用更高值（0.3-0.5）

**Sonar Reasoning Pro：**
- 默认：0.2
- 保持低值（0.0-0.2）以确保逻辑一致性
- 高温下推理质量会下降

**Sonar Pro / Sonar：**
- 默认：0.2
- 根据查询类型调整（事实性 vs 探索性）

### 速率限制和配额

OpenRouter 强制执行速率限制：
- 查看 OpenRouter 控制面板了解当前限制
- 高容量使用考虑请求批处理
- 使用 OpenRouter 的跟踪工具监控成本

### API 密钥安全

**最佳实践：**
- 切勿将 API 密钥提交到版本控制
- 使用环境变量或 .env 文件
- 定期轮换密钥
- 监控使用情况以发现异常活动
- 为不同项目使用不同密钥

## 示例对比

### 查询：“解释 CRISPR-Cas9 基因编辑”

**Sonar：**
- 快速概述
- 基础机制解释
- 约 200-300 tokens
- 引用 1-2 个来源
- 成本：$0.001

**Sonar Pro：**
- 详细解释
- 涵盖多种机制
- 约 500-800 tokens
- 引用 3-5 个来源
- 成本：$0.003

**Sonar Reasoning Pro：**
- 逐步机制分解
- 编辑过程的逻辑流程
- 约 800-1200 tokens
- 展示推理步骤
- 成本：$0.005

**Sonar Pro Search：**
- 全面分析
- 综合多个来源
- 包含历史背景
- 涵盖最新进展
- 约 1500-2000 tokens
- 探索 10+ 个来源
- 成本：$0.020+

### 查询：“2+2 等于多少？”

所有模型均返回准确答案。对简单查询使用 Sonar 以最小化成本。

### 查询：“设计新型免疫疗法的临床试验”

**Sonar：**
- 提供基本模板
- 可能遗漏重要细节
- 成本效益高但不完整

**Sonar Pro：**
- 扎实的试验设计框架
- 涵盖主要组成部分
- 良好的起点

**Sonar Reasoning Pro：**
- 详细的逐步设计
- 考虑多种因素
- 展示每个选择的推理
- **推荐用于此类查询**

**Sonar Pro Search：**
- 最全面的设计
- 整合多个来源的最佳实践
- 比较不同方法
- 对初步设计可能过于全面

## 总结

**默认建议**：对大多数科学查询，从 **Sonar Pro** 开始。

**何时升级：**
- 复杂的多步骤分析 → Sonar Pro Search
- 需要显式推理 → Sonar Reasoning Pro

**何时降级：**
- 简单事实或查找 → Sonar
- 成本敏感的大批量查询 → Sonar

**请记住**：最佳模型取决于您的具体使用场景、预算和质量要求。监控您的使用情况，并根据结果调整模型选择。