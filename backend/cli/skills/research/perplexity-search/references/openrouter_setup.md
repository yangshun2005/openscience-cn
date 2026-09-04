# OpenRouter 设置指南

使用 OpenRouter 访问 Perplexity 模型的完整设置与使用指南。

## 什么是 OpenRouter？

OpenRouter 是一个统一的 API 网关，通过单一 API 接口提供对来自不同提供商的 100+ AI 模型的访问。它提供：

- **单一 API 密钥**：使用一个密钥访问多个模型
- **统一格式**：兼容 OpenAI 的 API 格式
- **成本追踪**：内置使用监控和计费功能
- **模型路由**：智能回退和负载均衡
- **按量付费**：无需订阅，仅按使用量付费

具体到 Perplexity 模型，OpenRouter 提供对某些模型（如 Sonar Pro Search）的独家访问权限。

## 快速开始

### 第 1 步：创建 OpenRouter 账户

1. 访问 https://openrouter.ai/
2. 点击右上角的“注册”
3. 使用 Google、GitHub 或邮箱注册
4. 如果使用邮箱注册，请验证您的邮箱

### 第 2 步：添加支付方式

OpenRouter 使用按量付费模式：

1. 导航至 https://openrouter.ai/account
2. 点击“积分”选项卡
3. 添加支付方式（信用卡）
4. 充值初始积分（建议最低 $5）
5. 可选：设置自动充值

**定价说明：**
- 不同模型的每 token 成本不同
- 查看 Perplexity 定价请访问 https://openrouter.ai/perplexity
- 在 https://openrouter.ai/activity 监控使用情况

### 第 3 步：生成 API 密钥

1. 前往 https://openrouter.ai/keys
2. 点击“创建密钥”
3. 为您的密钥命名（例如：“perplexity-search-skill”）
4. 可选：设置使用限制以确保安全
5. 复制密钥（以 `sk-or-v1-...` 开头）
6. **重要**：请安全保存此密钥——您将无法再次查看它！

**安全提示：**
- 切勿公开分享您的 API 密钥
- 不要将密钥提交到版本控制
- 为不同项目使用不同的密钥
- 设置使用限制以防止意外费用
- 定期轮换密钥

### 第 4 步：配置环境

您有两种设置 API 密钥的方式：

#### 方式 A：环境变量（推荐）

**Linux/macOS：**
```bash
export OPENROUTER_API_KEY='sk-or-v1-your-key-here'
```

要使其永久生效，请添加到您的 shell 配置文件中：
```bash
# 对于 bash：添加到 ~/.bashrc 或 ~/.bash_profile
echo 'export OPENROUTER_API_KEY="sk-or-v1-your-key-here"' >> ~/.bashrc
source ~/.bashrc

# 对于 zsh：添加到 ~/.zshrc
echo 'export OPENROUTER_API_KEY="sk-or-v1-your-key-here"' >> ~/.zshrc
source ~/.zshrc
```

**Windows（PowerShell）：**
```powershell
$env:OPENROUTER_API_KEY = "sk-or-v1-your-key-here"
```

要使其永久生效：
```powershell
[System.Environment]::SetEnvironmentVariable('OPENROUTER_API_KEY', 'sk-or-v1-your-key-here', 'User')
```

#### 方式 B：.env 文件

在您的项目目录中创建 `.env` 文件：

```bash
# 创建 .env 文件
cat > .env << EOF
OPENROUTER_API_KEY=sk-or-v1-your-key-here
EOF
```

或使用设置脚本：
```bash
python scripts/setup_env.py --api-key sk-or-v1-your-key-here
```

然后在运行脚本前加载它：
```bash
# 从 .env 加载环境变量
source .env

# 或使用 python-dotenv
pip install python-dotenv
```

**在脚本中使用 python-dotenv：**
```python
from dotenv import load_dotenv
load_dotenv()  # 自动加载 .env 文件

import os
api_key = os.environ.get("OPENROUTER_API_KEY")
```

### 第 5 步：安装依赖

使用 uv 安装 LiteLLM：

```bash
uv pip install litellm
```

或使用常规 pip：
```bash
pip install litellm
```

**可选依赖：**
```bash
# 支持 .env 文件
uv pip install python-dotenv

# 额外功能
uv pip install litellm[proxy]  # 如果使用 LiteLLM 代理服务器
```

### 第 6 步：验证设置

测试您的配置：

```bash
# 使用设置脚本
python scripts/setup_env.py --validate

# 或使用搜索脚本
python scripts/perplexity_search.py --check-setup
```

您应该看到：
```
✓ OPENROUTER_API_KEY 已设置 (sk-or-v1-...xxxx)
✓ LiteLLM 已安装 (版本 X.X.X)
✓ 设置完成！您已准备好使用 Perplexity 搜索。
```

### 第 7 步：测试您的第一次搜索

运行一个简单的测试查询：

```bash
python scripts/perplexity_search.py "什么是 CRISPR 基因编辑？"
```

预期输出：
```
================================================================================
答案
================================================================================
CRISPR（成簇规律间隔短回文重复序列）是一种革命性的基因编辑技术，可以对 DNA 进行精确修改...
[详细答案继续]
================================================================================
```

## 使用监控

### 查看您的使用情况

监控您的 OpenRouter 使用情况和成本：

1. 访问 https://openrouter.ai/activity
2. 查看请求、token 和成本
3. 按日期范围、模型或密钥筛选
4. 导出使用数据进行分析

### 设置使用限制

防止意外费用：

1. 前往 https://openrouter.ai/keys
2. 点击您的密钥
3. 设置“速率限制”（每分钟请求数）
4. 设置“消费限制”（最大总消费额）
5. 可选：启用带限额的“自动充值”

**开发环境的建议限制：**
- 速率限制：每分钟 10-20 个请求
- 消费限制：$10-50，视使用情况而定

### 成本优化

降低成本的技巧：

1. **选择合适的模型**：简单查询使用 Sonar，而非 Sonar Pro Search
2. **设置 max_tokens**：使用 `--max-tokens` 参数限制响应长度
3. **批量查询**：尽可能合并多个简单问题
4. **监控使用情况**：密集开发期间每日检查成本
5. **使用缓存**：为重复查询存储结果

## 故障排除

### 错误：“OpenRouter API 密钥未配置”

**原因**：环境变量未设置

**解决方案**：
```bash
# 检查变量是否已设置
echo $OPENROUTER_API_KEY

# 如果为空，请设置
export OPENROUTER_API_KEY='sk-or-v1-your-key-here'

# 或使用设置脚本
python scripts/setup_env.py --api-key sk-or-v1-your-key-here
```

### 错误：“无效的 API 密钥”

**可能原因**：
- 密钥已被删除或撤销
- 密钥已过期
- 密钥中存在拼写错误
- 密钥格式错误

**解决方案**：
1. 在 https://openrouter.ai/keys 验证密钥
2. 检查是否有多余的空格或引号
3. 如有需要，生成新密钥
4. 确保密钥以 `sk-or-v1-` 开头

### 错误：“积分不足”

**原因**：OpenRouter 账户积分已用完

**解决方案**：
1. 前往 https://openrouter.ai/account
2. 点击“积分”选项卡
3. 添加更多积分
4. 考虑启用自动充值

### 错误：“超出速率限制”

**原因**：短时间内请求过多

**解决方案**：
1. 等待几秒后重试
2. 在 https://openrouter.ai/keys 提高速率限制
3. 在代码中实现指数退避
4. 批量请求或降低频率

### 错误：“未找到模型”

**原因**：模型名称错误或模型不再可用

**解决方案**：
1. 在 https://openrouter.ai/models 查看可用模型
2. 使用正确的格式：`openrouter/perplexity/sonar-pro`
3. 确认模型仍受支持

### 错误：“LiteLLM 未安装”

**原因**：LiteLLM 包未安装

**解决方案**：
```bash
uv pip install litellm
```

### LiteLLM 导入错误

**原因**：Python 路径问题或版本冲突

**解决方案**：
1. 验证安装：`pip list | grep litellm`
2. 重新安装：`uv pip install --force-reinstall litellm`
3. 检查 Python 版本：`python --version`（需要 3.8+）
4. 使用虚拟环境以避免冲突

## 高级配置

### 使用多个密钥

适用于不同项目或团队成员：

```bash
# 项目 1
export OPENROUTER_API_KEY='sk-or-v1-project1-key'

# 项目 2
export OPENROUTER_API_KEY='sk-or-v1-project2-key'
```

或在不同的目录中使用 .env 文件。

### 自定义基础 URL

如果使用 OpenRouter 代理或自定义端点：

```python
from litellm import completion

response = completion(
    model="openrouter/perplexity/sonar-pro",
    messages=[{"role": "user", "content": "query"}],
    api_base="https://custom-endpoint.com/v1"  # 自定义 URL
)
```

### 请求头

添加自定义请求头以进行跟踪：

```python
from litellm import completion

response = completion(
    model="openrouter/perplexity/sonar-pro",
    messages=[{"role": "user", "content": "query"}],
    extra_headers={
        "HTTP-Referer": "https://your-app.com",
        "X-Title": "您的应用名称"
    }
)
```

### 超时配置

为长时间运行的查询设置自定义超时：

```python
from litellm import completion

response = completion(
    model="openrouter/perplexity/sonar-pro-search",
    messages=[{"role": "user", "content": "复杂查询"}],
    timeout=120  # 120 秒超时
)
```

## 安全最佳实践

### API 密钥管理

1. **切勿提交密钥**：将 `.env` 添加到 `.gitignore`
2. **使用密钥轮换**：每 3-6 个月轮换一次密钥
3. **分离密钥**：为开发/预发布/生产环境使用不同密钥
4. **监控使用情况**：检查是否有未授权访问
5. **设置限制**：配置消费和速率限制

### .gitignore 模板

添加到您的 `.gitignore`：
```
# 环境变量
.env
.env.local
.env.*.local

# API 密钥
*api_key*
*apikey*
*.key

# 敏感配置
config/secrets.yaml
```

### 密钥撤销

如果密钥泄露：

1. 立即前往 https://openrouter.ai/keys
2. 点击泄露密钥的“删除”
3. 生成新密钥
4. 更新所有使用旧密钥的应用程序
5. 检查使用日志是否有未授权访问
6. 如有需要，联系 OpenRouter 支持

## 常见问题解答

**问：通过 OpenRouter 使用 Perplexity 的费用是多少？**

答：定价因模型而异。Sonar 最便宜（每次查询约 $0.001-0.002），Sonar Pro 适中（约 $0.002-0.005），Sonar Pro Search 最贵（每次查询约 $0.02-0.05+）。请访问 https://openrouter.ai/perplexity 查看确切定价。

**问：我需要单独的 Perplexity API 密钥吗？**

答：不需要！OpenRouter 仅使用您的 OpenRouter 密钥即可提供对 Perplexity 模型的访问。

**问：除了 Perplexity，我还可以将 OpenRouter 用于其他模型吗？**

答：可以！OpenRouter 通过同一个 API 密钥提供对来自 OpenAI、Anthropic、Google、Meta 等提供商的 100+ 模型的访问。

**问：有免费套餐吗？**

答：OpenRouter 需要付费，但提供非常有竞争力的定价。初始 $5 积分应足以进行大量测试。

**问：如何取消我的 OpenRouter 账户？**

答：请联系 OpenRouter 支持。请注意，未使用的积分可能无法退款。

**问：我可以在生产应用中使用 OpenRouter 吗？**

答：可以，OpenRouter 专为生产环境设计，提供强大的基础设施、SLA 和企业支持。

## 资源

**官方文档：**
- OpenRouter：https://openrouter.ai/docs
- Perplexity 模型：https://openrouter.ai/perplexity
- LiteLLM：https://docs.litellm.ai/

**账户管理：**
- 仪表盘：https://openrouter.ai/account
- API 密钥：https://openrouter.ai/keys
- 使用情况：https://openrouter.ai/activity
- 计费：https://openrouter.ai/credits

**社区：**
- OpenRouter Discord：https://discord.gg/openrouter
- GitHub Issues：https://github.com/OpenRouter
- LiteLLM GitHub：https://github.com/BerriAI/litellm

## 总结

为访问 Perplexity 设置 OpenRouter 的步骤：

1. 在 https://openrouter.ai 创建账户
2. 添加支付方式和积分
3. 在 https://openrouter.ai/keys 生成 API 密钥
4. 设置 `OPENROUTER_API_KEY` 环境变量
5. 安装 LiteLLM：`uv pip install litellm`
6. 验证设置：`python scripts/setup_env.py --validate`
7. 开始搜索：`python scripts/perplexity_search.py "您的查询"`

定期监控使用情况和成本，以优化支出并确保安全。