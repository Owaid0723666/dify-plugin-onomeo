# onomeo

Model provider plugin for [onomeo](https://onomeo.com): one OpenAI-compatible API key for Claude, GPT, Gemini, DeepSeek, Kimi and GLM models.

Source repository: https://github.com/Owaid0723666/dify-plugin-onomeo

onomeo is in public beta: not every feature is guaranteed to work, and feedback is being collected.

## What onomeo adds beyond forwarding requests

- **Per-key spending caps and expiry.** Each API key can carry its own spending cap and expiry date, set in the onomeo dashboard, so a Dify workspace can get a key with a fixed budget.
- **Cost confirmation.** The first request on an account whose reservation exceeds 1 US dollar, and again the first one past each tenfold step (10, 100 US dollars), returns the estimate as the answer instead of running, and nothing is charged; sending the same request again runs it.
- **Failover across free upstreams.** Free models are served from several upstream providers; when one is rate-limited or down, the request moves to the next. The `auto` model picks an available free model.
- **Usage records.** Every call is metered and listed in the dashboard with model, calling tool and amount.
- **Content filtering.** The last message of each request and each reply are checked against a blocklist for child sexual abuse material.

## Setup

1. Create an onomeo account at https://onomeo.com and create an API key on the dashboard: https://onomeo.com/dashboard
2. In Dify, open **Settings → Model Provider**, find **onomeo** and paste the API key.
3. Pick one of the predefined models, or add any other model ID listed by `GET https://onomeo.com/v1/models` (with your key) through **Add Model**.

## Models

Predefined: `deepseek-v4.1-flash`, `claude-sonnet-5.5`, `claude-opus-5.5`, `claude-haiku-5.5`, `gpt-6.2-sol`, `gemini-4-argon` and `kimi-k3`.

- New accounts can call `deepseek-v4.1-flash` for free within daily limits.
- Claude, GPT, Gemini and Kimi models need a topped-up balance, which is bought on the onomeo website; the plugin itself handles no payments. Paid models are billed per token; prices are listed at https://onomeo.com/models
- Free models such as `glm-5.3` can be added through **Add Model**. A single free request is limited to about 32,000 characters, so set a small context size for them.

## Connection requirements

The Dify instance must be able to reach `https://onomeo.com` over HTTPS. The plugin calls only `https://onomeo.com/v1/chat/completions`.

## Privacy

See [PRIVACY.md](PRIVACY.md) and https://onomeo.com/privacy.
