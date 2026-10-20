# Claude Code: Compatible Models & Providers

A comprehensive reference guide for developers using **Claude Code** with official and alternative AI providers. This guide covers the latest flagship models, pricing (Input/Output per 1M tokens), configuration for Anthropic, Alibaba Qwen, DeepSeek, MiniMax, Moonshot AI (Kimi), Zhipu GLM, Xiaomi MiMo, StepFun, and multi-provider gateways.

## Compatible Providers

| Provider | Type | Notable Models | Coding Plan |
| :--- | :--- | :--- | :--- |
| **Anthropic** | Official | Claude Opus 4.7, Sonnet 4.6 | Max subscription |
| **Alibaba (DashScope)** | Direct | Qwen 3.6-Plus, Qwen 3.5-Coder | — |
| **DeepSeek** | Direct | DeepSeek V3.2, DeepSeek-R2 | — |
| **MiniMax** | Direct | MiniMax-M2.7, M2.7-Highspeed | Token Plan (from $10/mo) |
| **Moonshot (Kimi)** | Direct | Kimi K2.5, K2.6 (beta) | — |
| **Zhipu (Z.ai)** | Direct | GLM-5.1, GLM-5, GLM-4.7 | Coding Plan (from $18/mo) |
| **Xiaomi (MiMo)** | Direct | MiMo-V2-Pro, V2-Omni, V2-Flash | Token Plan (from ~$6/mo) |
| **StepFun** | Direct | Step-3.5-Flash, Step-3 | Step Plan (from $6.99/mo) |
| **SiliconFlow** | Gateway | Hosted DeepSeek, GLM, Qwen, Kimi | — |
| **OpenRouter** | Gateway | 200+ models from all providers | — |
| **RouterPlex** | Gateway | DeepSeek V4, Kimi K3, GLM-5.3, Qwen 3.8, MiniMax-M3 and Claude, GPT, Gemini (64 models) | — (prepaid, per token) |
| **Ollama** | Local / Cloud | Open-source models, free | Free (local) |

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
    "ANTHROPIC_MODEL": "qwen3.6-plus"
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
    "ANTHROPIC_MODEL": "deepseek-reasoner"
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
    "ANTHROPIC_MODEL": "minimax-m2.7"
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
    "ANTHROPIC_MODEL": "kimi-k2.5"
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
    "ANTHROPIC_MODEL": "glm-5.1"
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
    "ANTHROPIC_MODEL": "mimo-v2-pro"
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

### StepFun

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

### RouterPlex (Multi-Provider)

Hosted OpenAI- and Anthropic-compatible gateway with Claude, GPT, Gemini, DeepSeek, Kimi, GLM, Qwen, MiniMax and more behind one key. Prepaid balance, billed per token at vendor list prices (0% markup, $0 top-up fee). Balance stops at $0 and each key can carry a hard USD budget. Full guide: [docs.routerplex.com/claude-code](https://docs.routerplex.com/claude-code).

**Configuration** (`~/.claude/settings.json`):
```json
{
  "env": {
    "ANTHROPIC_BASE_URL": "https://api.routerplex.com",
    "ANTHROPIC_AUTH_TOKEN": "YOUR_ROUTERPLEX_KEY",
    "ANTHROPIC_API_KEY": "",
    "ANTHROPIC_MODEL": "deepseek-v4-pro",
    "ANTHROPIC_DEFAULT_HAIKU_MODEL": "deepseek-v4-pro",
    "ANTHROPIC_DEFAULT_SONNET_MODEL": "deepseek-v4-pro",
    "ANTHROPIC_DEFAULT_OPUS_MODEL": "deepseek-v4-pro",
    "CLAUDE_CODE_MAX_CONTEXT_TOKENS": "616000"
  }
}
```

The base URL has no `/v1`; Claude Code adds `/v1/messages`. Set all four model variables to the same ID to use one non-Claude model. For IDs that do not start with `claude-`, set `CLAUDE_CODE_MAX_CONTEXT_TOKENS` to the model's context window minus its max output (otherwise Claude Code assumes 200K and compacts early). One-command setup: `npx routerplex`.

**Model IDs (USD per 1M tokens, input / output; source: [routerplex.com/api/models](https://routerplex.com/api/models)):**

| Family | Model ID | Price | `CLAUDE_CODE_MAX_CONTEXT_TOKENS` |
| :--- | :--- | :--- | :--- |
| DeepSeek | `deepseek-v4-pro` | $0.435 / $0.87 | 616000 |
| DeepSeek | `deepseek-v4-flash` | $0.09 / $0.18 | 616000 |
| Kimi | `kimi-k3` | $3 / $15 | 917504 |
| GLM | `glm-5.3` | $1.40 / $4.40 | 868928 |
| GLM | `glm-5.3-flash` | $0.15 / $0.50 | 868928 |
| Qwen | `qwen3.8-max` | $2 / $6 | 868928 |
| Qwen | `qwen3.7-plus` | $0.32 / $1.28 | 936000 |
| MiniMax | `MiniMax-M3` | $0.30 / $1.20 | 488000 |

*Note: Tool support varies by model; run a short tool round trip before real work. Top-ups start at $5 (card) or $15 (crypto). Prices change; check the live catalog.*

---

## Coding Plans & Subscriptions

Several providers offer subscription plans with flat-rate usage for Claude Code, typically measured in requests within a 5-hour rolling window.

### StepFun — Step Plan

| Plan | Price | Prompts / 5 hrs | Est. Model Calls |
| :--- | :--- | :--- | :--- |
| Flash Mini | $6.99/mo | 100 | ~1,500 |
| Flash Plus | $9.99/mo | 400 | ~6,000 |
| Flash Pro | $29/mo | 1,500 | ~22,500 |
| Flash Max | $99/mo | 5,000 | ~75,000 |

All plans include step-3.5-flash, multi-device login, and concurrent agent execution. Plus and above get priority API access and support.

[Step Plan pricing &rarr;](https://platform.stepfun.ai/step-plan)

---

### Xiaomi MiMo — Token Plan

| Plan | Price | Credits | Est. Complex Tasks |
| :--- | :--- | :--- | :--- |
| Lite | ~$6/mo (39 RMB) | 60M | ~120 |
| Standard | ~$16/mo (99 RMB) | 200M | ~400 |
| Pro | ~$50/mo (329 RMB) | 700M | ~1,400 |
| Max | ~$100/mo (659 RMB) | 1.6B | ~3,200 |

Credit multipliers: MiMo-V2-Omni **1x**, MiMo-V2-Pro (≤256K) **2x**, MiMo-V2-Pro (256K-1M) **4x**. First purchase gets 12% off. No 5-hour limit.

[Token Plan pricing &rarr;](https://platform.xiaomimimo.com/#/token-plan)

---

### MiniMax — Token Plan

| Plan | Price | Requests / 5 hrs |
| :--- | :--- | :--- |
| Starter | $10/mo | 1,500 |
| Plus | $20/mo | 4,500 |
| Max | $50/mo | 15,000 |
| Max-Highspeed | $80/mo | 15,000 |
| Ultra-Highspeed | $150/mo | 30,000 |

All tiers include MiniMax-M2.7. Highspeed plans use the faster M2.7-Highspeed variant. Yearly plans available: Starter $100/yr, Plus $200/yr, Max $500/yr.

[Token Plan pricing &rarr;](https://platform.minimax.io/subscribe/token-plan)

---

### Zhipu (Z.ai) — Coding Plan

| Plan | Price | Quota |
| :--- | :--- | :--- |
| Lite | $18/mo | 3x Claude Pro usage |
| Pro | $72/mo | 5x Lite Plan usage |
| Max | $160/mo | 4x Pro Plan usage |

GLM-5.1 consumes **3x** quota during peak hours, **2x** off-peak. Pro and above include Vision and Web Search.

[Coding Plan pricing &rarr;](https://z.ai/subscribe)

---

### Alibaba Cloud — Model Studio Coding Plan

| Plan | Price | Quota | Status |
| :--- | :--- | :--- | :--- |
| Lite | ~$10/mo | Lower quotas | **Discontinued for new purchases** (Mar 2026) |
| Pro | $50/mo | 6,000 req/5hrs, 90K req/mo | Available |

Pro plan includes Qwen 3.5-Plus, Kimi K2.5, GLM-5, MiniMax-M2.5, and Qwen 3-Coder variants. Each query costs 5-30+ requests depending on complexity.

[Coding Plan pricing &rarr;](https://www.alibabacloud.com/en/campaign/ai-scene-coding)

---

### Moonshot (Kimi) — Kimi Code

| Plan | Price | Quota |
| :--- | :--- | :--- |
| Free | $0 | Basic chat, daily/weekly quotas |
| Moderato | ~$19/mo | 2,048 Kimi Code requests/week |
| Allegretto | ~$49/mo | Higher quotas |
| Vivace | ~$129/mo | Highest quotas, premium features |

Plans include CLI and developer tools, priority compute, and 5-hour rolling token quotas.

[Kimi Code &rarr;](https://www.kimi.com/code)

---

### Ollama — Cloud Plans

| Plan | Price | Cloud Usage | Concurrent Cloud Models |
| :--- | :--- | :--- | :--- |
| Free | $0 | Light | 1 |
| Pro | $20/mo ($200/yr) | 50x Free | 3 |
| Max | $100/mo | 5x Pro | 10 |

Local model execution is always unlimited and free on all plans. Cloud usage resets every 5 hours (session) and weekly.

[Ollama Cloud pricing &rarr;](https://ollama.com/pricing)

---

## Quick Tips

1. **Thinking Mode:** For complex refactors, use models like `deepseek-reasoner`, `kimi-k2-thinking`, or `mimo-v2-flash-thinking`.
2. **Context Caching:** DeepSeek, Anthropic, and MiMo support caching — reduces input costs by up to 90%.
3. **Regional Endpoints:** In China, use `open.bigmodel.cn` for GLM, `dashscope.aliyuncs.com` for Qwen, `api.stepfun.com` for StepFun, or `api.minimaxi.com` for MiniMax for lower latency.
4. **Step Plan API:** Use `https://api.stepfun.ai/step_plan` (not the standard endpoint) for Step Plan subscriptions.
5. **Ollama Local:** Run `ollama launch claude --config` for guided zero-cost local setup with open-source models.
6. **Free Tiers:** Step-3.5-Flash and MiMo-V2-Flash are available free (rate-limited) via OpenRouter.
