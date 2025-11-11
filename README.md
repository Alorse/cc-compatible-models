# Claude Code-Compatible Models

A comprehensive reference guide for developers looking to use Claude Code with cost-effective alternative AI providers. Includes up-to-date pricing, detailed setup instructions, and configuration examples for Anthropic, Alibaba Qwen, DeepSeek, MiniMax, Moonshot AI (Kimi K2), and Zhipu GLM models.


| Provider | Model | Input $/1M tok | Output $/1M tok | Notes |
|----------|-------|----------------|-----------------|-------|
| Anthropic | Haiku 4.5 | $1.00 | $5.00 | Official API pricing. |
| Anthropic | Opus 4.1 | $15.00 | $75.00 | Official API pricing. |
| Anthropic | Sonnet 4.5 | $3.00 | $15.00 | Official API pricing. |
| Alibaba | Qwen3 Coder | $0.22 | $0.95 | Uses Anthropic-compatible endpoint. |
| DeepSeek | deepseek-chat | $0.28 | $0.42 | Context caching enabled by default. |
| MiniMax | MiniMax-M2 | $0.30 | $1.20 | No prompt caching feature available. |
| Moonshot AI | Kimi K2 | $0.14 | $2.49 | Automatic prompt caching (beta). |
| Zhipu (ZAI) | GLM 4.6 | $0.60 | $2.20 | Has **GLM Coding Plan** from $3/mo. |
| Cerebras | Qwen3 Coder | $2.00 | $2.00 | **Cerebras Code** plans: $50-200/mo. |

---

## Provider Setup Guides

### Anthropic (Official)

**Installation:**
```bash
npm install -g @anthropic-ai/claude-code
# or on Unix systems:
curl -fsSL https://claude.ai/install.sh | bash
```

**Authentication:**

There are two main options:

1. **Claude Console (OAuth)**: Requires active billing at [console.anthropic.com](https://console.anthropic.com). A "Claude Code" workspace is automatically created for usage tracking.

2. **Claude.ai Subscription**: Subscribe to Claude Pro or Max plan and log in with your Claude.ai account.

**Enterprise Options:**
- Configure Claude Code to use Amazon Bedrock or Google Vertex AI with your existing cloud infrastructure.

**Documentation:** [https://docs.claude.com/en/docs/claude-code/setup](https://docs.claude.com/en/docs/claude-code/setup)

---

### Alibaba - Qwen

**Getting API Key:**
1. Visit [Alibaba Cloud Model Studio](https://www.alibabacloud.com/help/en/model-studio)
2. Create an account and generate a DashScope API key

**Configuration:**

Edit `~/.claude/settings.json`:

```json
{
  "env": {
    "ANTHROPIC_BASE_URL": "https://dashscope-intl.aliyuncs.com/apps/anthropic",
    "ANTHROPIC_AUTH_TOKEN": "YOUR_DASHSCOPE_API_KEY",
    "ANTHROPIC_MODEL": "qwen-plus",
    "ANTHROPIC_SMALL_FAST_MODEL": "qwen-flash"
  }
}
```

**Recommended Model Combinations:**
- **Main Model** (`ANTHROPIC_MODEL`): `qwen-max`, `qwen-plus`, or Qwen-Coder series for complex tasks
- **Fast Model** (`ANTHROPIC_SMALL_FAST_MODEL`): `qwen-flash` or `qwen-turbo` for simple jobs

**Launch:**
```bash
cd your-project-directory
claude
```

**Documentation:** [https://www.alibabacloud.com/help/en/model-studio/claude-code](https://www.alibabacloud.com/help/en/model-studio/claude-code)

---

### DeepSeek

**Getting API Key:**
Visit [DeepSeek Platform](https://platform.deepseek.com) to obtain your API key.

**Configuration:**

Edit `~/.claude/settings.json`:

```json
{
  "env": {
    "ANTHROPIC_BASE_URL": "https://api.deepseek.com/anthropic",
    "ANTHROPIC_AUTH_TOKEN": "YOUR_DEEPSEEK_API_KEY",
    "API_TIMEOUT_MS": "600000",
    "ANTHROPIC_MODEL": "deepseek-chat",
    "ANTHROPIC_SMALL_FAST_MODEL": "deepseek-chat",
    "CLAUDE_CODE_DISABLE_NONESSENTIAL_TRAFFIC": "1"
  }
}
```

**Using DeepSeek Reasoner (R1):**
Replace `deepseek-chat` with `deepseek-reasoner` in the configuration above.

**Launch:**
```bash
cd your-project-directory
claude
```

**Troubleshooting:**
- Invalid token error: Verify `ANTHROPIC_AUTH_TOKEN` is set to your real DeepSeek API key
- No response: Confirm `ANTHROPIC_BASE_URL` is correct: `https://api.deepseek.com/anthropic`

**Documentation:** [https://api-docs.deepseek.com/guides/anthropic_api](https://api-docs.deepseek.com/guides/anthropic_api)

---

### MiniMax

**Getting API Key:**
1. Visit [MiniMax Developer Platform](https://platform.minimax.io)
2. Navigate to the interface key section
3. Create a new secret key with a project name
4. Copy and save the key securely (shown only once)

**Configuration:**

Edit `~/.claude/settings.json`:

```json
{
  "env": {
    "ANTHROPIC_BASE_URL": "https://api.minimax.io/anthropic",
    "ANTHROPIC_AUTH_TOKEN": "YOUR_MINIMAX_API_KEY",
    "API_TIMEOUT_MS": "3000000",
    "ANTHROPIC_MODEL": "MiniMax-M2",
    "ANTHROPIC_SMALL_FAST_MODEL": "MiniMax-M2",
    "ANTHROPIC_DEFAULT_SONNET_MODEL": "MiniMax-M2",
    "ANTHROPIC_DEFAULT_OPUS_MODEL": "MiniMax-M2",
    "ANTHROPIC_DEFAULT_HAIKU_MODEL": "MiniMax-M2",
    "CLAUDE_CODE_DISABLE_NONESSENTIAL_TRAFFIC": "1"
  }
}
```

**Launch:**
```bash
cd your-project-directory
claude
```

**Documentation:** [https://platform.minimax.io/docs/guides/text-ai-coding-tools](https://platform.minimax.io/docs/guides/text-ai-coding-tools)

---

### Moonshot AI - Kimi K2

**Getting API Key:**
1. Visit [Moonshot Platform](https://platform.moonshot.ai/)
2. Create an account and generate an API key

**Configuration:**

Edit `~/.claude/settings.json`:

```json
{
  "env": {
    "ANTHROPIC_BASE_URL": "https://api.moonshot.ai/anthropic",
    "ANTHROPIC_AUTH_TOKEN": "YOUR_MOONSHOT_API_KEY",
    "ANTHROPIC_MODEL": "kimi-k2-turbo-preview",
    "ANTHROPIC_SMALL_FAST_MODEL": "kimi-k2-turbo-preview"
  }
}
```

**Launch:**
```bash
cd your-project-directory
claude
```

**Features:**
- 256K context length for handling complex codebases
- Seamless Claude Code compatibility with agentic tool use
- Automatic prompt caching (currently in 3-month public beta)

**Documentation:** [https://platform.moonshot.ai/docs/guide/agent-support](https://platform.moonshot.ai/docs/guide/agent-support)

---

### Zhipu (ZAI) - GLM 4.6

**Getting API Key:**
1. Visit [Z.AI Platform](https://open.bigmodel.cn/) (Mainland China) or [api.z.ai](https://api.z.ai) (International)
2. Create an account and generate an API key

**Configuration:**

Edit `~/.claude/settings.json`:

```json
{
  "env": {
    "ANTHROPIC_BASE_URL": "https://api.z.ai/api/anthropic",
    "ANTHROPIC_AUTH_TOKEN": "YOUR_ZAI_API_KEY",
    "ANTHROPIC_DEFAULT_HAIKU_MODEL": "glm-4.5-air",
    "ANTHROPIC_DEFAULT_SONNET_MODEL": "glm-4.6",
    "ANTHROPIC_DEFAULT_OPUS_MODEL": "glm-4.6"
  }
}
```

**For Mainland China:**
Replace base URL with: `https://open.bigmodel.cn/api/anthropic`

**Launch:**
```bash
cd your-project-directory
claude
```

**Documentation:** [https://docs.z.ai/scenario-example/develop-tools/claude](https://docs.z.ai/scenario-example/develop-tools/claude)

---

## 💰 Coding Plans Overview

Several providers offer **subscription-based coding plans** that provide generous limits for development work, often at 3-10x better value than pay-per-token pricing. These are perfect for intensive coding sessions or professional development work.

### **MiniMax M2 - Coding Plan** ⭐

**Plans:**
- **Starter**: $10/mo (100 prompts/5h) | $100/yr
- **Plus**: $20/mo (300 prompts/5h) | $200/yr
- **Max**: $50/mo (1000 prompts/5h) | $500/yr

**Benefits:**
- 1 prompt ≈ 15 model requests
- **1/10th the cost** of comparable plans (Claude, etc.)
- No unpredictable bills - fixed subscription
- Powered by MiniMax-M2 (230B MoE, 10B active)
- 204K context window

**Subscribe:** https://platform.minimax.io/subscribe/coding-plan

---

### **GLM 4.6 - GLM Coding Plan** ⭐

**Plans:**
- **Lite**: $3/mo (~120 prompts/5h)
- **Pro**: $15/mo (~600 prompts/5h)
- **Max**: Price varies (~2400 prompts/5h)

**Benefits:**
- **3x more usage** than comparable plans
- 1 prompt = ~15-20 model calls
- Over **55 tokens/second** generation speed
- No network restrictions or account bans
- Vision & Web Search (Pro+)
- Compatible with Claude Code, Cline, Cursor, etc.

**Features:**
- Text generation, Vision, Video generation
- Model mapping: Opus/Sonnet/Haiku all default to GLM models
- Singapore-based services with privacy protection

**Subscribe:** https://z.ai/subscribe

---

### **Qwen3 Coder - Cerebras Code** (Third-party)

**Plans:**
- **Cerebras Code Pro**: $50/mo
- **Cerebras Code Max**: $200/mo

**Benefits:**
- **20x faster coding** than competitors
- Equal or higher rate limits than Cursor/Anthropic
- Powered by Qwen3 Coder 480B (MoE architecture)
- Access via Cerebras Inference Cloud, OpenRouter, or HuggingFace

**Performance:**
- 2,000 tokens/second on Cerebras Wafer Scale Engine
- Problems that take 20s on Sonnet 4 finish in 1s

**Learn More:** https://www.cerebras.ai/blog/qwen3-coder-480b-is-live-on-cerebras

---

## General Tips

1. **Version Check**: Ensure Claude Code is up to date with `claude --version` and update with `claude update`

2. **Timeout Settings**: Some providers require higher timeout values (especially for complex reasoning tasks). The `API_TIMEOUT_MS` setting helps prevent premature timeouts.

3. **Model Selection**: Most providers support automatic model selection based on task complexity using `ANTHROPIC_MODEL` (main) and `ANTHROPIC_SMALL_FAST_MODEL` (quick tasks).

4. **Regional Considerations**: China-based providers often have separate endpoints for mainland China vs. international users.

5. **Testing Configuration**: After setup, run `claude` in a test directory and verify the model responds correctly.

6. **Cost Optimization**:
   - Use cache-enabled providers (Anthropic, DeepSeek, Kimi) for repetitive tasks
   - Select appropriate model sizes for the task complexity
   - Consider batch processing for non-urgent workloads
