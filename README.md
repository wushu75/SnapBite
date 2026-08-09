<div align="center">

<img src="icons/icon128.png" width="96" height="96" alt="SnapBite logo" />

# SnapBite

**Snap. Bite. Done.**

Snap a photo, paste an image, or describe your meal. Your own API key. Your data stays yours.

A free, open-source, privacy-first calorie tracker that runs as a Chrome / Edge extension (Manifest V3). No account, no backend, no telemetry — you bring your own AI API key and everything is stored locally on your machine.

</div>

---

## Why SnapBite

- **Free & open source** — MIT licensed. No subscription, no upsell.
- **BYOK (bring your own key)** — you paste your own provider key; SnapBite talks *directly* to the provider you choose and nothing routes through a server we control.
- **Chinese models first** — defaults favor low-cost, high-quality Chinese vision/text models (Qwen-VL, DeepSeek), with everything else supported too.
- **Local-first** — settings live in `chrome.storage.local`; your meal log lives in IndexedDB on your device. Export/import is a plain JSON file you own.
- **Private by design** — no analytics, no tracking, minimal permissions. The only network request is the API call *you* trigger to *your* provider.
- **Lightweight** — vanilla JS, no framework, no build step.

## Features

- Three ways to log a meal:
  - **Image** — upload a file or paste an image straight from your clipboard.
  - **Camera** — snap a photo in the popup (or open in a tab for a bigger, more reliable camera).
  - **Describe** — just type what you ate.
- Editable results — the AI fills in calories, protein, carbs, fat, and a confidence score; you can correct anything before saving.
- Daily energy ring, per-day macros, and a browsable meal history.
- Units your way — kcal or kJ; grams for macros.
- Dark mode (follows your system, or force light/dark).

## Install (load unpacked)

1. Download or clone this repo.
2. Open `chrome://extensions` (or `edge://extensions`).
3. Turn on **Developer mode** (top-right).
4. Click **Load unpacked** and select the project folder.
5. Pin SnapBite, open it, and hit **Settings** to paste an API key.

> Works in any Chromium browser that supports Manifest V3 (Chrome, Edge, Brave, Arc, etc.).

## Getting an API key

SnapBite needs a key for one AI provider. You only need **one**. Cheapest/free-friendly picks are at the top.

| Provider | Best for | Vision? | Get a key |
| --- | --- | --- | --- |
| **Qwen-VL** (Alibaba) ⭐ | Chinese-first vision, free trial quota | ✅ | [bailian.console.alibabacloud.com](https://bailian.console.alibabacloud.com/) |
| **DeepSeek** | Extremely cheap **text** (Describe tab) | ❌ text-only | [platform.deepseek.com](https://platform.deepseek.com/) |
| **SiliconFlow** | Hosts DeepSeek-VL & Qwen-VL, some free models | ✅ | [cloud.siliconflow.cn](https://cloud.siliconflow.cn/) |
| **OpenRouter** | One key, hundreds of models | ✅ | [openrouter.ai/keys](https://openrouter.ai/keys) |
| **Google Gemini** | Generous free tier, fast flash models | ✅ | [aistudio.google.com/apikey](https://aistudio.google.com/apikey) |
| **OpenAI** | Reliable GPT-4o vision | ✅ | [platform.openai.com/api-keys](https://platform.openai.com/api-keys) |
| **Claude** (Anthropic) | Careful estimation | ✅ | [console.anthropic.com](https://console.anthropic.com/settings/keys) |
| **Grok** (xAI) | xAI vision | ✅ | [console.x.ai](https://console.x.ai/) |
| **Ollama** (local) | 100% offline & free | ✅ | [ollama.com](https://ollama.com/) |
| **Custom** | Any OpenAI-compatible endpoint | ✅ | — |

### ⚠️ Note on DeepSeek + photos

DeepSeek's official hosted API (`deepseek-v4-*`) is **text-only** and will reject an image. So in SnapBite:

- **DeepSeek** powers the **Describe** tab (cheap, fast, Chinese-first).
- For **photos**, pick a vision model — the default is **Qwen-VL**, and **SiliconFlow** / **OpenRouter** also host DeepSeek-VL and Qwen-VL.
- If you point a text-only model at a photo, SnapBite tells you and suggests a fix instead of failing silently.

Every model ID and base URL is editable in **Settings**, so if a provider renames a model you can update it yourself without waiting for a release.

## Privacy

- No backend. No account. No analytics or telemetry of any kind.
- Your API key is stored locally in `chrome.storage.local` and is sent **only** to the provider you selected, on the request you initiate.
- Your meal history stays in IndexedDB on your device. **Export never includes your API keys**, and **import never restores keys** — you always re-enter those yourself.
- Base permissions are just `storage` plus the specific provider domains. Custom endpoints ask for domain access at the moment you use them.

## How it works

```
popup / options  →  js/api.js  →  your chosen provider's API
      │                              (OpenAI-compatible or Anthropic native)
      ▼
chrome.storage.local (settings)  +  IndexedDB (meals)
```

The model is prompted to return strict JSON (`{ title, items[], totals, confidence, assumptions }`), which SnapBite parses, normalizes, and shows in an editable card before you save.

## Project structure

```
manifest.json          MV3 manifest (minimal permissions)
popup.html             Main UI (Image / Camera / Describe + Today)
options.html           Settings (keys, models, units, goal, theme, export/import)
css/                   theme.css, popup.css, options.css
js/
  background.js        Tiny service worker — first-run setup only
  popup.js             Popup controller
  options.js           Settings controller
  api.js               Provider calls + JSON normalization
  config.js            Provider registry & defaults
  storage.js           Settings + IndexedDB meal store
  utils.js             Helpers (image compression, JSON extraction, etc.)
icons/                 App icons (16–512)
```

## Tech

Vanilla JavaScript (ES modules), no framework, no build step. Manifest V3.

## Contributing

Issues and PRs welcome — bug reports, provider updates (model IDs drift!), and UI polish especially. Keep it dependency-free and privacy-first.

## License

[MIT](LICENSE) © wushu75
