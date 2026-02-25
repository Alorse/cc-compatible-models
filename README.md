# Claude Code: Compatible Models & Providers (2025-2026 Edition)

A comprehensive reference guide for developers using **Claude Code** with official and alternative AI providers. This guide covers the latest flagship models, pricing (Input/Output per 1M tokens), and configuration for Anthropic, Alibaba Qwen, DeepSeek, MiniMax, Moonshot AI (Kimi), Zhipu GLM, and **OpenRouter**.

## 💰 Model Pricing Overview (Latest Models)

| Provider | Flagship Model | Input ($/1M) | Output ($/1M) | Notes |
| :--- | :--- | :--- | :--- | :--- |
| **Anthropic** | Claude 4.6 Sonnet | $3.00 | $15.00 | Best-in-class performance & agentic tasks. |
| **Alibaba** | Qwen 3.5 | $0.55 | $3.50 | Next-gen native multimodal, 1M context. |
| **DeepSeek** | DeepSeek V3.2 | $0.27 | $0.42 | Extremely efficient, caching enabled. |
| **MiniMax** | MiniMax-M2.5 | $0.15 | $1.20 | "Intelligence too cheap to meter", MoE. |
| **Moonshot** | Kimi K2.5 | $0.60 | $3.00 | 1T parameters MoE, native multimodal. |
| **Zhipu (Z.ai)** | GLM-5 | $1.00 | $3.20 | New flagship with strong reasoning. |
| **OpenRouter** | Multi-Provider | Varies | Varies | Unified access to all the above. |

---

## 🚀 Provider Setup Guides

### Anthropic (Official)

Claude Code officially supports Claude 4.6 Sonnet, which excels at coding tasks and tool use.

**Installation:**
```bash
npm install -g @anthropic-ai/claude-code
```

**Authentication:**
- **OAuth:** Run `claude` and follow the browser login.
- **API Key:** Set `ANTHROPIC_API_KEY` in your environment.

[Official Documentation](https://docs.claude.com/en/docs/claude-code/setup)

---

### Alibaba Cloud - DashScope (Qwen)

Qwen 3.5 is the latest flagship, supporting massive context windows.

**Configuration:**
Edit `~/.claude/settings.json`:
```json
{
  "env": {
    "ANTHROPIC_BASE_URL": "https://dashscope-intl.aliyuncs.com/apps/anthropic",
    "ANTHROPIC_AUTH_TOKEN": "YOUR_DASHSCOPE_API_KEY",
    "ANTHROPIC_MODEL": "qwen3.5-plus",
    "ANTHROPIC_SMALL_FAST_MODEL": "qwen3.5-coder"
  }
}
```

---

### DeepSeek

DeepSeek V3.2 incredibly cost-effective alternatives.

**Configuration:**
```json
{
  "env": {
    "ANTHROPIC_BASE_URL": "https://api.deepseek.com/anthropic",
    "ANTHROPIC_AUTH_TOKEN": "YOUR_DEEPSEEK_API_KEY",
    "ANTHROPIC_MODEL": "deepseek-reasoner",
    "ANTHROPIC_SMALL_FAST_MODEL": "deepseek-chat"
  }
}
```
*Note: `deepseek-reasoner` maps to DeepSeek V3.2 (with thinking processes).*

---

### MiniMax

The new MiniMax-M2.5 series offers the lowest output pricing in its class.

**Configuration:**
```json
{
  "env": {
    "ANTHROPIC_BASE_URL": "https://api.minimax.io/anthropic",
    "ANTHROPIC_AUTH_TOKEN": "YOUR_MINIMAX_API_KEY",
    "ANTHROPIC_MODEL": "minimax-m2.5",
    "ANTHROPIC_SMALL_FAST_MODEL": "minimax-m2.5-lightning"
  }
}
```

---

### Moonshot AI - Kimi

Kimi K2.5 is a massive 1T-parameter model optimized for long context (256K).

**Configuration:**
```json
{
  "env": {
    "ANTHROPIC_BASE_URL": "https://api.moonshot.ai/anthropic",
    "ANTHROPIC_AUTH_TOKEN": "YOUR_MOONSHOT_API_KEY",
    "ANTHROPIC_MODEL": "kimi-k2.5",
    "ANTHROPIC_SMALL_FAST_MODEL": "kimi-k2"
  }
}
```

---

### Zhipu (Z.ai) - GLM

GLM-5 is Zhipu's latest flagship model

**Configuration:**
```json
{
  "env": {
    "ANTHROPIC_BASE_URL": "https://api.z.ai/api/anthropic",
    "ANTHROPIC_AUTH_TOKEN": "YOUR_ZAI_API_KEY",
    "ANTHROPIC_MODEL": "glm-5",
    "ANTHROPIC_SMALL_FAST_MODEL": "glm-4-flash"
  }
}
```

---

### OpenRouter (Multi-Provider)

Best for comparing models or failover. Supports all the above via one token.

**Basic Setup:**
```bash
export ANTHROPIC_BASE_URL="https://openrouter.ai/api"
export ANTHROPIC_AUTH_TOKEN="YOUR_OPENROUTER_KEY"
```

---

## ⭐ Special Coding Plans

### MiniMax M2.5 Coding Plan
- **Max Plan:** $50/mo for 1000 prompts/5h window.
- **Lightning Edge:** Extremely fast generation for repo-wide scans.

### GLM Subscription Plans
- **Pro:** $15/mo, includes Vision and Web Search capabilities.
- **Lite:** $3/mo, perfect for hobbyists.

---

## 💡 Quick Tips
1.  **Thinking Mode:** For complex refactors, use models like `deepseek-reasoner` or `kimi-k2-thinking`.
2.  **Context Caching:** DeepSeek and Anthropic support caching, which can reduce input costs by up to 90%.
3.  **Regional Endpoints:** If you are in China, use `open.bigmodel.cn` for GLM or `dashscope.aliyuncs.com` for Qwen for lower latency.
