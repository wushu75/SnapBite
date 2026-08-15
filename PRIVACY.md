# SnapBite — Privacy Policy

_Last updated: 15 August 2026_

**The short version:** SnapBite has no servers, no accounts, and no analytics. It does not collect, transmit, or sell your data to us or anyone else. Everything you log stays on your device. The only time anything leaves your machine is when **you** ask SnapBite to analyze a meal — and then it goes straight to the AI provider whose key you entered, and nowhere else.

## Who this covers

This policy applies to the SnapBite browser extension ("SnapBite", "the extension"). SnapBite is free, open-source software. There is no company, backend service, or hosted account behind it.

## What SnapBite stores, and where

All of the following is stored **locally on your device** using your browser's built-in storage (`chrome.storage.local` and IndexedDB). None of it is transmitted to the developer or any third party except as described below.

- **Your meal log** — titles, calories, macros, notes, timestamps, and optional small image thumbnails you save.
- **Your settings** — chosen provider, model, units, daily goal, and theme.
- **Your API key(s)** — the key you paste for your chosen AI provider is stored locally so you don't have to re-enter it.

## What is sent off your device, and to whom

SnapBite only makes a network request when you actively trigger a meal analysis. At that moment, and only then, it sends the following **directly to the AI provider you selected and configured** (for example DeepSeek, Alibaba Qwen, Kimi/Moonshot, SiliconFlow, OpenRouter, Google, OpenAI, Anthropic, xAI, or a custom/local endpoint you entered):

- The meal **photo or text** you are analyzing.
- Your **API key** for that provider, used to authenticate the request.

This request goes straight from your browser to that provider's API. It does **not** pass through any server operated by the SnapBite developer, because none exists. SnapBite never sends your data to any destination you did not configure.

> **Third-party providers have their own policies.** Once your meal data reaches the AI provider you chose, that provider's privacy policy and terms govern how they handle it. Please review the policy of whichever provider you use. If you prefer that _nothing_ leaves your device at all, you can run a fully local model (for example via Ollama) and configure SnapBite to use it.

## What SnapBite does NOT do

- No analytics, tracking, telemetry, or usage reporting of any kind.
- No advertising and no ad networks.
- No selling, renting, or sharing of your data with data brokers or any third party.
- No developer-operated servers, and no account or sign-in.
- No use of your data for anything beyond the single purpose of estimating and logging the meals you ask it to.

## Permissions

- **Storage** — to save your log, settings, and key locally on your device.
- **Access to specific AI provider domains** — so SnapBite can send your analysis request to the provider you chose.
- **Optional access to a custom endpoint** — only requested if you add your own OpenAI-compatible or self-hosted endpoint, and only granted when you approve the browser's permission prompt.

## Data retention and deletion

Because your data lives only on your device, you are always in control of it. You can edit or delete individual meals at any time, or clear everything from the extension's settings. Removing your keys or uninstalling the extension deletes SnapBite's locally stored data from your browser. SnapBite keeps no copy anywhere else.

## Children

SnapBite is a general-purpose utility and is not directed at children. It collects no personal information for the developer from anyone.

## Limited Use

SnapBite's use and handling of any user data complies with the Chrome Web Store User Data Policy, including the Limited Use requirements. User data is used solely to provide and improve the single user-facing purpose of the extension — estimating and logging the meals you choose to analyze — and is never transferred except as needed to fulfill that purpose at your direction.

## Changes to this policy

If this policy changes in a way that affects how your data is handled, the updated version will be posted here with a new "last updated" date, and — where the change is material — surfaced in the extension.

## Contact & support

Questions, concerns, or bug reports? Open an issue at **https://github.com/wushu75/SnapBite/issues**.

---

_SnapBite · MIT licensed · your data stays yours · not affiliated with any model provider._
