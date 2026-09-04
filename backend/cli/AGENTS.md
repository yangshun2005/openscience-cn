# OpenScience - ML 工作流默认配置

本文件为 OpenScience 在 ML/AI 研究项目中工作时提供默认指令。

## 技能加载指南

根据当前任务主动加载相应技能：

### 训练与后训练

- **RLHF/GRPO/DPO** → `grpo-rl-training`、`trl-fine-tuning`、`openrlhf`、`simpo`
- **微调** → `axolotl`、`unsloth`、`llama-factory`、`torchtune`
- **分布式** → `deepspeed-training`、`fsdp`、`megatron-core`、`accelerate`

### 推理与服务

- **高吞吐量** → `vllm-inference`、`sglang`、`tensorrt-llm`
- **本地/边缘** → `llama-cpp`、`gguf-quantization`
- **优化** → `flash-attention`、`gptq`、`awq`、`bitsandbytes`

### 评估与分析

- **基准测试** → `lm-eval-harness`、`bigcode-eval`、`nemo-evaluator`
- **可解释性** → `transformer-lens`、`saelens`、`nnsight`、`pyvene`

### RAG 与检索

- **向量存储** → `chroma`、`faiss`、`pinecone`、`qdrant`
- **嵌入** → `sentence-transformers`
- **编排** → `langchain`、`llamaindex`

### 智能体与结构化输出

- **智能体框架** → `langchain`、`llamaindex`、`crewai`
- **结构化输出** → `dspy`、`instructor`、`guidance`、`outlines`

### 多模态

- **视觉** → `clip`、`llava`、`segment-anything`、`stable-diffusion`
- **音频** → `whisper`、`audiocraft`
- **文档** → `blip-2`

### 数据与基础设施

- **数据处理** → `ray-data`、`nemo-curator`
- **云计算** → `modal`、`skypilot`、`lambda-labs`
- **实验跟踪** → `weights-and-biases`、`mlflow`、`tensorboard`

### 新兴技术

- **扩展** → `moe-training`、`speculative-decoding`、`long-context`
- **压缩** → `knowledge-distillation`、`model-pruning`、`model-merging`

## ML 工作流标准

### 训练前

- [ ] 检查 GPU 可用性：`nvidia-smi` 或 `torch.cuda.is_available()`
- [ ] 验证 CUDA 版本与框架的兼容性
- [ ] 估算模型 + 优化器 + 梯度的内存需求
- [ ] 设置实验跟踪（W&B 或 MLflow）
- [ ] 验证数据集格式和分词

### 训练最佳实践

- 在 Ampere+ GPU（A100、H100、RTX 30xx+）上使用 bf16，其他情况使用 fp16
- 在内存受限的环境中启用梯度检查点
- 每 N 步保存一次检查点（N = 训练时间小时数 \* 2）
- 记录学习率、损失和梯度范数
- 设置随机种子以确保可复现性：`torch.manual_seed(42)`

### 内存优化优先级

1. 梯度检查点（免费，约减少 30% 内存）
2. 混合精度训练（免费，约减少 50% 内存）
3. 梯度累积（免费，支持更大的有效批次）
4. DeepSpeed ZeRO 阶段 2（开销极小）
5. 模型分片 / FSDP（适用于多 GPU）

### OOM 错误处理

遇到 CUDA 内存不足时：

1. 将批次大小减少 50%
2. 启用梯度检查点
3. 切换到 8 位优化器（bitsandbytes）
4. 尝试 DeepSpeed ZeRO 卸载
5. 对于超大型模型，考虑模型并行

## 代码风格指南

### 推荐模式

- 使用 HuggingFace Transformers 加载模型
- 使用 `accelerate` 进行设备管理
- 使用 `datasets` 库加载数据
- 使用 `peft` 进行参数高效微调

### 示例配置

```python
import torch
from accelerate import Accelerator
from transformers import AutoModelForCausalLM, AutoTokenizer

accelerator = Accelerator(mixed_precision="bf16")
model = AutoModelForCausalLM.from_pretrained(
    "model-name",
    torch_dtype=torch.bfloat16,
    device_map="auto",
)
```

## 环境变量

ML 工作流的关键环境变量：

- `CUDA_VISIBLE_DEVICES` - GPU 选择
- `WANDB_PROJECT` - W&B 项目名称
- `HF_TOKEN` - HuggingFace API 令牌
- `TRANSFORMERS_CACHE` - 模型缓存目录