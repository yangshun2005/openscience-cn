---
name: perplexity-search
description: 使用 Perplexity 模型（通过 LiteLLM 和 OpenRouter）执行基于 AI 的网页搜索，获取实时信息。当需要搜索当前信息、查找最新科学文献、获取带有来源引用的可靠答案，或访问超出模型知识截止日期之外的信息时，应使用此技能。通过单个 OpenRouter API 密钥即可访问多种 Perplexity 模型，包括 Sonar Pro、Sonar Pro Search（高级代理搜索）和 Sonar Reasoning Pro。
category: research
license: MIT license
compatibility: 使用 Perplexity 搜索需要 OpenRouter API 密钥
metadata:
    skill-author: Synthetic Sciences
---

# Perplexity 搜索

## 概述

通过 LiteLLM 和 OpenRouter 使用 Perplexity 模型执行基于 AI 的网页搜索。Perplexity 提供带有来源引用的实时、基于网络的答案，非常适合查找超出模型训练数据截止日期之外的当前信息、最新科学文献和事实。

此技能通过 OpenRouter 提供对所有 Perplexity 模型的访问，仅需一个 API 密钥（无需单独的 Perplexity 账户）。

## 何时使用此技能

在以下情况下使用此技能：
- 搜索当前信息或最新进展（2024 年及以后）
- 查找最新的科学出版物和研究
- 获取基于网络来源的实时答案
- 使用来源引用验证事实
- 跨多个领域进行文献检索
- 访问超出模型知识截止日期之外的信息
- 进行特定领域的研究（生物医学、技术、临床）
- 比较当前的方法或技术

**不要用于**：
- 简单的计算或逻辑问题（直接使用）
- 需要代码执行的任务（使用标准工具）
- 模型训练数据中已充分涵盖的问题（除非需要验证）

## 快速开始

### 设置（一次性）

1. **获取 OpenRouter API 密钥**：
   - 访问 https://openrouter.ai/keys
   - 创建账户并生成 API 密钥
   - 向账户添加积分（建议最低 $5）

2. **配置环境**：
   ```bash
   # 设置 API 密钥
   export OPENROUTER_API_KEY='sk-or-v1-your-key-here'

   # 或使用设置脚本
   python scripts/setup_env.py --api-key sk-or-v1-your-key-here
   ```

3. **安装依赖**：
   ```bash
   uv pip install litellm
   ```

4. **验证设置**：
   ```bash
   python scripts/perplexity_search.py --check-setup
   ```

有关详细的设置说明、故障排除和安全最佳实践，请参阅 `references/openrouter_setup.md`。

### 基本用法

**简单搜索：**
```bash
python scripts/perplexity_search.py "CRISPR 基因编辑的最新进展有哪些？"
```

**保存结果：**
```bash
python scripts/perplexity_search.py "近期 CAR-T 疗法临床试验" --output results.json
```

**使用特定模型：**
```bash
python scripts/perplexity_search.py "比较 mRNA 和病毒载体疫苗" --model sonar-pro-search
```

**详细输出：**
```bash
python scripts/perplexity_search.py "量子计算用于药物发现" --verbose
```

## 可用模型

通过 `--model` 参数访问模型：

- **sonar-pro**（默认）：通用搜索，成本和质量的平衡最佳
- **sonar-pro-search**：最先进的代理搜索，支持多步推理
- **sonar**：基础模型，对于简单查询最具成本效益
- **sonar-reasoning-pro**：高级推理，支持逐步分析
- **sonar-reasoning**：基础推理能力

**模型选择指南：**
- 默认查询 → `sonar-pro`
- 复杂的多步分析 → `sonar-pro-search`
- 需要显式推理 → `sonar-reasoning-pro`
- 简单事实查询 → `sonar`
- 成本敏感型批量查询 → `sonar`

有关详细比较、用例、定价和性能特征，请参阅 `references/model_comparison.md`。

## 构建有效的查询

### 具体且详细

**好的示例：**
- "2024 年发表的 CAR-T 细胞疗法治疗 B 细胞淋巴瘤的最新临床试验结果有哪些？"
- "比较 mRNA 疫苗与病毒载体疫苗针对 COVID-19 的有效性和安全性特征"
- "解释 AlphaFold3 相对于 AlphaFold2 的改进，包括 2023-2024 年研究的具体准确性指标"

**不好的示例：**
- "告诉我关于癌症治疗的信息"（过于宽泛）
- "CRISPR"（过于模糊）
- "疫苗"（缺乏特异性）

### 包含时间限制

Perplexity 搜索实时网络数据：
- "2024 年《自然医学》上发表了哪些关于长新冠的论文？"
- "过去 6 个月大语言模型效率方面有哪些最新进展？"
- "NeurIPS 2023 上关于 AI 安全发布了哪些公告？"

### 指定领域和来源

为获得高质量结果，请提及来源偏好：
- "根据高影响力期刊中同行评审的出版物..."
- "基于 FDA 批准的治疗方法..."
- "来自 clinicaltrials.gov 等临床试验注册库..."

### 构建复杂查询

将复杂问题分解为清晰的组成部分：
1. **主题**：主要研究对象
2. **范围**：感兴趣的特定方面
3. **上下文**：时间范围、领域、约束条件
4. **输出**：期望的答案格式或类型

**示例：**
"根据 2023 年至 2024 年间发表的研究，AlphaFold3 在蛋白质结构预测方面相对于 AlphaFold2 提供了哪些改进？请包含具体的准确性指标和基准测试。"

有关查询设计、特定领域模式和高级技术的全面指导，请参阅 `references/search_strategies.md`。

## 常见用例

### 科学文献检索

```bash
python scripts/perplexity_search.py \
  "近期研究（2023-2024）关于肠道微生物组在帕金森病中的作用有何发现？重点关注同行评审研究，并包含已识别的特定细菌种类。" \
  --model sonar-pro
```

### 技术文档

```bash
python scripts/perplexity_search.py \
  "如何使用 Python 实现从 Kafka 到 PostgreSQL 的实时数据流？包括处理背压和确保精确一次语义的注意事项。" \
  --model sonar-reasoning-pro
```

### 比较分析

```bash
python scripts/perplexity_search.py \
  "在易用性、性能和生态系统支持方面，比较 PyTorch 与 TensorFlow 用于实现 Transformer 模型。包含近期研究的基准测试结果。" \
  --model sonar-pro-search
```

### 临床研究

```bash
python scripts/perplexity_search.py \
  "间歇性禁食在管理成人 2 型糖尿病方面的证据是什么？重点关注随机对照试验，并报告 HbA1c 变化和体重减轻结果。" \
  --model sonar-pro
```

### 趋势分析

```bash
python scripts/perplexity_search.py \
  "过去 5 年单细胞 RNA 测序技术的主要趋势是什么？突出通量、成本和分辨率的改进，并提供具体示例。" \
  --model sonar-pro
```

## 处理结果

### 编程访问

将 `perplexity_search.py` 作为模块使用：

```python
from scripts.perplexity_search import search_with_perplexity

result = search_with_perplexity(
    query="CRISPR 的最新进展有哪些？",
    model="openrouter/perplexity/sonar-pro",
    max_tokens=4000,
    temperature=0.2,
    verbose=False
)

if result["success"]:
    print(result["answer"])
    print(f"使用的令牌数: {result['usage']['total_tokens']}")
else:
    print(f"错误: {result['error']}")
```

### 保存和处理结果

```bash
# 保存为 JSON
python scripts/perplexity_search.py "查询" --output results.json

# 使用 jq 处理
cat results.json | jq '.answer'
cat results.json | jq '.usage'
```

### 批处理

为多个查询创建脚本：

```bash
#!/bin/bash
queries=(
  "CRISPR 2024 年进展"
  "mRNA 疫苗技术进展"
  "AlphaFold3 准确性改进"
)

for query in "${queries[@]}"; do
  echo "正在搜索: $query"
  python scripts/perplexity_search.py "$query" --output "results_$(echo $query | tr ' ' '_').json"
  sleep 2  # 速率限制
done
```

## 成本管理

Perplexity 模型有不同的定价层级：

**每次查询的近似成本：**
- Sonar：$0.001-0.002（最具成本效益）
- Sonar Pro：$0.002-0.005（推荐的默认选项）
- Sonar Reasoning Pro：$0.005-0.010
- Sonar Pro Search：$0.020-0.050+（最全面）

**成本优化策略：**
1. 对于简单事实查询使用 `sonar`
2. 大多数查询默认使用 `sonar-pro`
3. 将 `sonar-pro-search` 保留用于复杂分析
4. 设置 `--max-tokens` 以限制响应长度
5. 在 https://openrouter.ai/activity 监控使用情况
6. 在 OpenRouter 仪表板中设置消费限额

## 故障排除

### API 密钥未设置

**错误**："OpenRouter API 密钥未配置"

**解决方案**：
```bash
export OPENROUTER_API_KEY='sk-or-v1-your-key-here'
# 或运行设置脚本
python scripts/setup_env.py --api-key sk-or-v1-your-key-here
```

### LiteLLM 未安装

**错误**："LiteLLM 未安装"

**解决方案**：
```bash
uv pip install litellm
```

### 速率限制

**错误**："超出速率限制"

**解决方案**：
- 等待几秒钟后重试
- 在 https://openrouter.ai/keys 提高速率限制
- 在批处理请求之间添加延迟

### 积分不足

**错误**："积分不足"

**解决方案**：
- 在 https://openrouter.ai/account 添加积分
- 启用自动充值以防止中断

有关全面的故障排除指南，请参阅 `references/openrouter_setup.md`。

## 与其他技能的集成

此技能可补充其他科学技能：

### 文献综述

与 `literature-review` 技能配合使用：
1. 使用 Perplexity 查找近期论文和预印本
2. 使用实时网络结果补充 PubMed 搜索
3. 验证引用并查找相关工作
4. 发现数据库索引之后的最新进展

### 科学写作

与 `scientific-writing` 技能配合使用：
1. 为引言/讨论部分查找近期参考文献
2. 验证当前技术发展水平
3. 检查最新术语和惯例
4. 识别近期竞争方法

### 假设生成

与 `hypothesis-generation` 技能配合使用：
1. 搜索最新研究发现
2. 识别当前知识空白
3. 查找近期方法论进展
4. 发现新兴研究方向

### 批判性思维

与 `scientific-critical-thinking` 技能配合使用：
1. 查找支持和反对假设的证据
2. 定位方法论批评
3. 识别领域内的争议
4. 使用当前证据验证主张

## 最佳实践

### 查询设计

1. **具体明确**：包含领域、时间范围和约束条件
2. **使用术语**：使用领域适当的关键词和短语
3. **指定来源**：提及偏好的出版物类型或期刊
4. **结构化问题**：清晰的组成部分，带有明确的上下文
5. **迭代优化**：根据初步结果进行改进

### 模型选择

1. **从 sonar-pro 开始**：大多数查询的良好默认选项
2. **针对复杂性升级**：对于多步分析使用 sonar-pro-search
3. **针对简单性降级**：对于基本事实使用 sonar
4. **使用推理模型**：当需要逐步分析时

### 成本优化

1. **选择适当的模型**：将模型与查询复杂性匹配
2. **设置令牌限制**：使用 `--max-tokens` 控制成本
3. **监控使用情况**：定期检查 OpenRouter 仪表板
4. **高效批处理**：尽可能合并相关的简单查询
5. **缓存结果**：保存并重用重复查询的结果

### 安全性

1. **保护 API 密钥**：切勿提交到版本控制
2. **使用环境变量**：将密钥与代码分离
3. **设置消费限额**：在 OpenRouter 仪表板中配置
4. **监控使用情况**：留意意外活动
5. **轮换密钥**：定期更换密钥

## 资源

### 捆绑资源

**脚本：**
- `scripts/perplexity_search.py`：带有 CLI 界面的主搜索脚本
- `scripts/setup_env.py`：环境设置和验证辅助工具

**参考：**
- `references/search_strategies.md`：全面的查询设计指南
- `references/model_comparison.md`：详细的模型比较和选择指南
- `references/openrouter_setup.md`：完整的设置、故障排除和安全指南

**资产：**
- `assets/.env.example`：示例环境文件模板

### 外部资源

**OpenRouter：**
- 仪表板：https://openrouter.ai/account
- API 密钥：https://openrouter.ai/keys
- Perplexity 模型：https://openrouter.ai/perplexity
- 使用监控：https://openrouter.ai/activity
- 文档：https://openrouter.ai/docs

**LiteLLM：**
- 文档：https://docs.litellm.ai/
- OpenRouter 提供商：https://docs.litellm.ai/docs/providers/openrouter
- GitHub：https://github.com/BerriAI/litellm

**Perplexity：**
- 官方文档：https://docs.perplexity.ai/

## 依赖项

### 必需

```bash
# LiteLLM 用于 API 访问
uv pip install litellm
```

### 可选

```bash
# 支持 .env 文件
uv pip install python-dotenv

# 用于 JSON 处理（通常已预装）
uv pip install jq
```

### 环境变量

必需：
- `OPENROUTER_API_KEY`：您的 OpenRouter API 密钥

可选：
- `DEFAULT_MODEL`：要使用的默认模型（默认：sonar-pro）
- `DEFAULT_MAX_TOKENS`：默认最大令牌数（默认：4000）
- `DEFAULT_TEMPERATURE`：默认温度（默认：0.2）

## 总结

此技能提供：

1. **实时网页搜索**：访问超出训练数据截止日期之外的当前信息
2. **多种模型**：从高性价比的 Sonar 到先进的 Sonar Pro Search
3. **简单设置**：单个 OpenRouter API 密钥，无需单独的 Perplexity 账户
4. **全面指导**：详细的查询设计和模型选择参考
5. **成本效益**：按使用量付费的定价，支持使用监控
6. **科学聚焦**：针对研究、文献检索和技术查询进行了优化
7. **易于集成**：与其他科学技能无缝协作

执行基于 AI 的网页搜索，查找当前信息、近期研究以及带有来源引用的可靠答案。