# Claude Code: Compatible Models & Providers (2025-2026 Edition)

A comprehensive reference guide for developers using **Claude Code** with official and alternative AI providers. This guide covers the latest flagship models, pricing (Input/Output per 1M tokens), configuration for Anthropic, Alibaba Qwen, DeepSeek, MiniMax, Moonshot AI (Kimi), Zhipu GLM, Xiaomi MiMo, StepFun, and multi-provider gateways.

## Model Pricing Overview (Latest Models)

| Provider | Flagship Model | Input ($/1M) | Output ($/1M) | Context | Notes |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **Anthropic** | Claude Opus 4.7 | $5.00 | $25.00 | 200K | Most capable; agentic coding & reasoning. |
| **Anthropic** | Claude Sonnet 4.6 | $3.00 | $15.00 | 200K | Best price/performance for coding tasks. |
| **Alibaba** | Qwen 3.6-Plus | $0.28 | $1.65 | 1M | Agentic coding, deep reasoning, 1M context. |
| **DeepSeek** | DeepSeek V3.2 | $0.27 | $1.10 | 128K | Extremely efficient, caching enabled. |
| **DeepSeek** | DeepSeek-R2 | $0.55 | $2.19 | 128K | Reasoning model, strong benchmarks. |
| **MiniMax** | MiniMax-M2.7 | $0.30 | $1.20 | 205K | Open-source MoE, SWE-Pro 56.22%. |
| **Moonshot** | Kimi K2.5 | $0.60 | $3.00 | 262K | 1T params MoE, native multimodal. |
| **Moonshot** | Kimi K2.6 | TBD | TBD | 262K | Beta; coding-agent-first model. |
| **Zhipu (Z.ai)** | GLM-5.1 | $0.95 | $3.15 | 203K | 8+ hr autonomous tasks, MIT license. |
| **Xiaomi** | MiMo-V2-Pro | $1.00 | $3.00 | 1M | Top-5 global on OpenRouter Arena. |
| **StepFun** | Step-3.5-Flash | $0.10 | $0.30 | 256K | Best value reasoning model. |
| **OpenRouter** | Multi-Provider | Varies | Varies | Varies | Unified access to all the above. |
| **SiliconFlow** | Multi-Provider | Varies | Varies | Varies | Hosted models, Anthropic-compatible. |
| **Ollama** | Local/Cloud | Free | Free | 32K+ | Local models or cloud via ollama.com. |

---

## Provider Setup Guides

### Anthropic (Official)

Claude Code officially supports Claude Opus 4.7 and Sonnet 4.6, excelling at agentic coding tasks and tool use.

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

Qwen 3.6-Plus is the latest flagship (April 2026), with 1M context window and strong agentic coding capabilities.

**Configuration:**
Edit `~/.claude/settings.json`:
```json
{
  "env": {
    "ANTHROPIC_BASE_URL": "https://dashscope-intl.aliyuncs.com/apps/anthropic",
    "ANTHROPIC_AUTH_TOKEN": "YOUR_DASHSCOPE_API_KEY",
    "ANTHROPIC_MODEL": "qwen3.6-plus",
    "ANTHROPIC_SMALL_FAST_MODEL": "qwen3.5-coder"
  }
}
```

**Pricing tiers (per 1M tokens):**
| Context Band | Input | Output |
| :--- | :--- | :--- |
| 0 - 256K | $0.28 | $1.65 |
| 256K - 1M | $1.10 | $6.60 |

---

### DeepSeek

DeepSeek V3.2 and R2 offer incredibly cost-effective coding and reasoning.

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

**Pricing (per 1M tokens):**
| Model | Input | Cache Hit | Output |
| :--- | :--- | :--- | :--- |
| DeepSeek V3.2 | $0.27 | $0.07 | $1.10 |
| DeepSeek-R2 | $0.55 | $0.14 | $2.19 |

*Note: `deepseek-reasoner` maps to the reasoning model with thinking processes.*

---

### MiniMax

MiniMax-M2.7 (March 2026) is open-source, 230B params MoE, with SOTA on real-world software engineering benchmarks.

**Configuration:**
```json
{
  "env": {
    "ANTHROPIC_BASE_URL": "https://api.minimax.io/anthropic",
    "ANTHROPIC_AUTH_TOKEN": "YOUR_MINIMAX_API_KEY",
    "ANTHROPIC_MODEL": "minimax-m2.7",
    "ANTHROPIC_SMALL_FAST_MODEL": "minimax-m2.7-highspeed"
  }
}
```

**China endpoint:** `https://api.minimaxi.com/anthropic`

**Pricing (per 1M tokens):**
| Model | Input | Cache Read | Output |
| :--- | :--- | :--- | :--- |
| MiniMax-M2.7 | $0.30 | $0.059 | $1.20 |
| M2.7-Highspeed | $0.60 | — | $2.40 |

---

### Moonshot AI - Kimi

Kimi K2.5 is a 1T-parameter MoE model optimized for long context. K2.6 is in beta (April 2026).

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

*Note: K2.6 is currently beta-only via Kimi CLI/IDE integrations. Public API expected May 2026.*

---

### Zhipu (Z.ai) - GLM

GLM-5.1 (April 2026) is a 744B MoE model capable of 8+ hour autonomous tasks, MIT-licensed.

**Configuration:**
```json
{
  "env": {
    "ANTHROPIC_BASE_URL": "https://api.z.ai/api/anthropic",
    "ANTHROPIC_AUTH_TOKEN": "YOUR_ZAI_API_KEY",
    "ANTHROPIC_MODEL": "glm-5.1",
    "ANTHROPIC_SMALL_FAST_MODEL": "glm-4-flash"
  }
}
```

**Pricing (per 1M tokens):**
| Model | Input | Output |
| :--- | :--- | :--- |
| GLM-5.1 | $0.95 - $1.40 | $3.15 - $4.40 |
| GLM-5 | $1.00 | $3.20 |
| GLM-4.7 | $0.60 | $2.20 |

*Note: GLM-5.1 consumes 3x quota during peak hours, 2x off-peak on Coding Plan.*

---

### Xiaomi - MiMo

MiMo-V2-Pro ranks top-5 globally on OpenRouter Arena. 1M context, MoE architecture.

**Configuration:**
```json
{
  "env": {
    "ANTHROPIC_BASE_URL": "https://api.xiaomimimo.com",
    "ANTHROPIC_AUTH_TOKEN": "YOUR_MIMO_API_KEY",
    "ANTHROPIC_MODEL": "mimo-v2-pro",
    "ANTHROPIC_SMALL_FAST_MODEL": "mimo-v2-flash"
  }
}
```

**Pricing (per 1M tokens):**
| Model | Context | Input | Output | Cache Read |
| :--- | :--- | :--- | :--- | :--- |
| MiMo-V2-Pro | ≤256K | $1.00 | $3.00 | $0.20 |
| MiMo-V2-Pro | 256K-1M | $2.00 | $6.00 | $0.40 |
| MiMo-V2-Omni | 256K | $0.40 | $2.00 | $0.08 |
| MiMo-V2-Flash | 256K | $0.09 | $0.29 | $0.01 |

**Supported integrations:** Claude Code, OpenCode, OpenClaw, Cline, Kilo Code, Roo Code, Codex, Cherry Studio, Zed.

---

### StepFun (Step / 阶跃星辰)

Step-3.5-Flash is a powerful reasoning model at the lowest price point among major providers.

**Configuration (Pay-as-you-go):**
```json
{
  "env": {
    "ANTHROPIC_AUTH_TOKEN": "YOUR_STEPFUN_API_KEY",
    "ANTHROPIC_BASE_URL": "https://api.stepfun.ai/",
    "ANTHROPIC_MODEL": "step-3.5-flash"
  }
}
```

**Configuration (Step Plan subscription):**
```json
{
  "env": {
    "ANTHROPIC_API_KEY": "YOUR_STEPFUN_API_KEY",
    "ANTHROPIC_BASE_URL": "https://api.stepfun.ai/step_plan",
    "ANTHROPIC_MODEL": "step-3.5-flash"
  }
}
```

**China endpoints:** Replace `.ai` with `.com` (e.g., `https://api.stepfun.com/`).

**Pricing (per 1M tokens):**
| Model | Input | Output | Cache Read |
| :--- | :--- | :--- | :--- |
| Step-3.5-Flash | $0.10 | $0.30 | $0.02 |
| Step-3 | ~$0.21 | ~$0.55 - $1.10 | ~$0.04 |
| Step-2-Mini | ~$0.14 | ~$0.28 | ~$0.03 |

**Supported integrations:** Claude Code, OpenCode, OpenClaw, Cline, Kilo Code, Roo Code, Trae, Cursor, Zed, Cherry Studio, Goose.

---

### SiliconFlow (Multi-Provider)

Hosted access to DeepSeek, GLM, Qwen, Kimi, and more via Anthropic-compatible API.

**Configuration:**
```json
{
  "env": {
    "ANTHROPIC_BASE_URL": "https://api.siliconflow.com/",
    "ANTHROPIC_API_KEY": "YOUR_SILICONFLOW_KEY",
    "ANTHROPIC_MODEL": "deepseek-ai/DeepSeek-V3"
  }
}
```

*Note: Currently does not support "thinking" model variants — only non-thinking.*

---

### Ollama (Local / Cloud)

Run models locally for free since January 2026 (v0.14.0+). Also supports cloud models via ollama.com.

**Configuration:**
```json
{
  "env": {
    "ANTHROPIC_AUTH_TOKEN": "ollama",
    "ANTHROPIC_BASE_URL": "http://localhost:11434",
    "ANTHROPIC_API_KEY": ""
  }
}
```

**Quick start:** `ollama launch claude --config` provides guided setup. Requires models with 32K+ context.

**Local models:** `qwen3-coder`, `glm-4.7`, `minimax-m2.1`, and more.
**Cloud models:** `glm-5.1:cloud`, `kimi-k2.5:cloud`, `qwen3.5:cloud` via ollama.com.

---

### OpenRouter (Multi-Provider)

Best for comparing models or failover. Supports all providers via one token, including Fast Mode (2.5x faster output at premium pricing).

**Basic Setup:**
```bash
export ANTHROPIC_BASE_URL="https://openrouter.ai/api"
export ANTHROPIC_AUTH_TOKEN="YOUR_OPENROUTER_KEY"
```

**Model environment variables:**
```bash
export ANTHROPIC_DEFAULT_OPUS_MODEL="anthropic/claude-opus-4.7"
export ANTHROPIC_DEFAULT_SONNET_MODEL="anthropic/claude-sonnet-4.6"
```

---

## Special Coding Plans & Subscriptions

| Provider | Plan | Price | Allowance | Key Features |
| :--- | :--- | :--- | :--- | :--- |
| **MiniMax** | Token Plan Starter | $10/mo | 1,500 req / 5hrs | All M2.7 models |
| **MiniMax** | Token Plan Plus | $20/mo | 4,500 req / 5hrs | + Highspeed access |
| **MiniMax** | Token Plan Max | $50/mo | 15,000 req / 5hrs | + Speech 2.8 |
| **MiniMax** | Token Plan Max-Highspeed | $80/mo | 15,000 req / 5hrs | Fastest generation |
| **MiniMax** | Token Plan Ultra-Highspeed | $150/mo | 30,000 req / 5hrs | Maximum throughput |
| **Zhipu GLM** | Coding Plan Lite | $10/mo | Usage-based | GLM-5.1 (3x peak / 2x off-peak quota) |
| **Zhipu GLM** | Coding Plan Pro | $30/mo | Usage-based | + Vision & Web Search |
| **Zhipu GLM** | Coding Plan Max | $80/mo | Usage-based | Maximum quota |
| **Xiaomi MiMo** | Token Plan Lite | ~$6/mo | 60M credits | All MiMo models |
| **Xiaomi MiMo** | Token Plan Standard | ~$16/mo | 200M credits | ~400 complex tasks |
| **Xiaomi MiMo** | Token Plan Pro | ~$50/mo | 700M credits | + Priority beta access |
| **Xiaomi MiMo** | Token Plan Max | ~$100/mo | 1.6B credits | ~3,200 complex tasks |
| **StepFun** | Flash Mini | $6.99/mo | 100 prompts / 5hrs | ~1,500 model calls |
| **StepFun** | Flash Plus | $9.99/mo | 400 prompts / 5hrs | ~6,000 model calls |
| **StepFun** | Flash Pro | $29/mo | 1,500 prompts / 5hrs | ~22,500 model calls |
| **StepFun** | Flash Max | $99/mo | 5,000 prompts / 5hrs | ~75,000 model calls |

### MiMo Token Plan Credit Multipliers
- MiMo-V2-Omni (≤256K): **1x** (1 token = 1 credit)
- MiMo-V2-Pro (≤256K): **2x**
- MiMo-V2-Pro (256K-1M): **4x**

### StepFun Rate Limits (Pay-as-you-go)
| Tier | Top-up | Concurrency | RPM | TPM |
| :--- | :--- | :--- | :--- | :--- |
| V0 | $0 | 5 | 10 | 5M |
| V1 | $15 | 100 | 1,000 | 20M |
| V2 | $70 | 200 | 5,000 | 30M |
| V3 | $300 | 400 | 10,000 | 40M |

---

## Quick Tips

1. **Thinking Mode:** For complex refactors, use models like `deepseek-reasoner`, `kimi-k2-thinking`, or `mimo-v2-flash-thinking`.
2. **Context Caching:** DeepSeek, Anthropic, and MiMo support caching — reduces input costs by up to 90%.
3. **Regional Endpoints:** In China, use `open.bigmodel.cn` for GLM, `dashscope.aliyuncs.com` for Qwen, `api.stepfun.com` for StepFun, or `api.minimaxi.com` for MiniMax for lower latency.
4. **Step Plan API:** Use `https://api.stepfun.ai/step_plan` (not the standard endpoint) for Step Plan subscriptions.
5. **Ollama Local:** Run `ollama launch claude --config` for guided zero-cost local setup with open-source models.
6. **Free Tiers:** Step-3.5-Flash and MiMo-V2-Flash are available free (rate-limited) via OpenRouter.
