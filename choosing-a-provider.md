---
layout: default
title: Choosing an AI Provider
nav_order: 3
---

# Choosing an AI Provider

Batch Generate Image with any AI connects directly to your own provider. You bring the API key, choose the model, and the app sends requests straight to that provider.

---

## Quick recommendation

| Goal | Best choice |
|---|---|
| Easiest first run | OpenAI |
| One key for many model families | OpenRouter |
| Lower-cost open-source image models | Fireworks AI or Together AI |
| Reference analysis and sample analysis | OpenAI or OpenRouter |
| Custom or self-hosted endpoint | Custom (OpenAI-compatible) |

---

## Supported provider presets

The current app ships with these built-in provider presets:

| Provider | Typical use | Sign up |
|---|---|---|
| **OpenAI** | Straightforward first-run image generation | [platform.openai.com](https://platform.openai.com) |
| **OpenRouter** | One key for multiple model families | [openrouter.ai](https://openrouter.ai) |
| **Together AI** | Open-source image models such as FLUX and SDXL variants | [api.together.xyz](https://api.together.xyz) |
| **Fireworks AI** | Fast FLUX and SDXL-style image workflows | [fireworks.ai](https://fireworks.ai) |
| **Custom (OpenAI-compatible)** | Your own compatible endpoint | — |

You can save up to 10 named connections and switch the active one at any time.

---

## OpenAI

OpenAI is the smoothest place to start if you want the fewest moving parts.

Typical use:

- DALL-E 3 or `gpt-image-1` for final image generation
- automatic fallback to `gpt-4o-mini` for reference analysis or sample analysis when your image model is image-only

OpenAI works well when you want:

- reliable first-run setup
- strong portrait and landscape support
- Step 2 reference analysis
- persona sample analysis

---

## OpenRouter

OpenRouter is useful when you want one key across multiple providers or model families.

Typical use:

- image generation with model IDs such as FLUX or Gemini image models
- reference analysis or sample analysis using a vision-capable chat model

Important behavior:

- if your active OpenRouter generation model looks image-only, the app can use `openai/gpt-4o-mini` for reference analysis and sample analysis
- AI CSV generation does **not** use that fallback automatically

That means OpenRouter can be a strong all-around option, but for the **Generate CSV** dialog you should still switch to a chat-capable model if you want AI-written rows and captions.

---

## Together AI

Together AI is a good option for open-source image models and lower-cost experimentation.

Use full Together model IDs, for example:

```text
black-forest-labs/FLUX.1-schnell-Free
```

Together AI is mainly useful here for **final image generation**. If your configured model is image-only, Step 2 reference analysis and persona sample analysis will not be available from that setup.

---

## Fireworks AI

Fireworks AI is useful for fast FLUX-style generation and SDXL-style workflows.

Typical patterns:

- FLUX models for fast square generations
- SDXL-style models when you need other aspect ratios

Important current limitation:

- in the current app, Fireworks connections do **not** support Step 2 reference analysis
- Fireworks connections also do **not** support persona sample analysis

Use Fireworks when you mainly want final image output and do not need the analysis features on that connection.

---

## Custom (OpenAI-compatible)

Choose **Custom (OpenAI-compatible)** if you want to point the app at your own compatible endpoint.

Examples:

- a self-hosted image generation service
- a local wrapper around another image backend
- a compatible enterprise endpoint

For final image generation, the endpoint needs to support an OpenAI-style image generation route.

For analysis or AI CSV writing, the endpoint also needs compatible chat or vision capability. If it only exposes image generation, those helper features will not work.

---

## Image generation vs analysis vs AI CSV writing

These are three separate capabilities in the app:

1. **Image generation** — creates the final images
2. **Reference or sample analysis** — inspects folders of images and summarizes visual cues
3. **AI CSV generation** — writes image-list rows using a chat completion call

This matters because some models only do the first job well.

Example:

- FLUX is often great for final image generation
- but FLUX by itself cannot inspect reference folders
- and FLUX by itself cannot write AI CSV rows through the chat-based CSV helper

So if you want **all** features in one workflow:

- use OpenAI or OpenRouter for reference analysis and sample analysis
- use a chat-capable model for AI CSV generation
- use an image model for the final batch generation

Many users keep multiple saved connections for exactly this reason.

---

## Switching connections

Each saved connection stores its own provider, model, base URL, and API key.

You can:

- create separate connections for different jobs
- test them independently
- switch the active connection without re-entering old keys

This is the easiest way to keep one setup for high-quality image generation, another for cheaper bulk runs, and another for chat-based helper tasks such as AI CSV writing.
