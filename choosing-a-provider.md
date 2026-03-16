---
layout: default
title: Choosing an AI Provider
nav_order: 3
---

# Choosing an AI Provider

BatchGen Image supports multiple AI image providers. You connect with your own API key — the app sends requests directly to your chosen provider.

---

## Quick recommendation

| Goal | Best choice |
|---|---|
| Best quality | OpenAI DALL-E 3 (HD) |
| Cheapest | Fireworks AI (FLUX Schnell) |
| Free tier available | Fireworks AI |
| Portrait / landscape sizes | OpenAI or Fireworks SDXL |
| Custom / local endpoint | OpenAI-Compatible |

---

## Supported providers

| Provider | Image models | Sign up |
|---|---|---|
| **OpenAI** | DALL-E 3 | [platform.openai.com](https://platform.openai.com) |
| **Fireworks AI** | FLUX.1 Schnell FP8, FLUX.1 Dev FP8, SDXL | [fireworks.ai](https://fireworks.ai) |
| **OpenRouter** | Various (model-dependent) | [openrouter.ai](https://openrouter.ai) |
| **Together AI** | Stable Diffusion XL and others | [api.together.xyz](https://api.together.xyz) |
| **Custom** | Any OpenAI-compatible image endpoint | — |

---

## OpenAI

The default provider. Supports full DALL-E 3 quality with Standard and HD tiers.

**Pricing:**

| Quality | Price per image |
|---|---|
| Standard | $0.040 |
| HD | $0.080 |

**Standard** is fine for social media graphics, web images, and drafts. **HD** is better for print, book covers, and hero images where detail matters.

**Getting your API key:**

1. Go to [platform.openai.com](https://platform.openai.com) and create an account
2. Add a payment method under **Billing**
3. Go to **API keys** and click **Create new secret key**
4. Copy the key and paste it into the app via the key icon

> OpenAI gives new accounts some free credits to start with. Once those run out, billing is pay-as-you-go.

**Supported sizes:** 1024×1024, 1024×1792 (portrait), 1792×1024 (landscape)

---

## Fireworks AI

Faster and cheaper than OpenAI for most use cases. Offers FLUX and SDXL models.

**Models:**

| Model | Notes |
|---|---|
| `flux-1-schnell-fp8` | Fastest and cheapest. Good for drafts and large batches. |
| `flux-1-dev-fp8` | Higher quality than Schnell, slower. |
| SDXL models | Supports portrait and landscape orientations (768×1344). |

> **Note:** FLUX models only generate at 1024×1024 (square). For portrait or landscape outputs, use an SDXL model with Fireworks.

**Getting started with Fireworks:**

1. Sign up at [fireworks.ai](https://fireworks.ai) and get an API key
2. In the app, click the key icon and select **Fireworks AI**
3. Paste your API key and click **Test**

---

## OpenRouter

OpenRouter routes to 100+ models from a single API key. Image model availability depends on which models OpenRouter carries at a given time.

Set the model field to the full OpenRouter model ID, e.g. `openai/dall-e-3`.

---

## Together AI

Together AI hosts Stable Diffusion XL and other open-source image models. Pricing is per-image and generally lower than OpenAI.

Use model IDs from their documentation, e.g. `stabilityai/stable-diffusion-xl-base-1.0`.

---

## Custom (OpenAI-compatible)

Select **Custom (OpenAI-Compatible)** to connect to any endpoint that supports the OpenAI `/images/generations` API format.

Examples:
- A locally hosted model via [ComfyUI](https://github.com/comfyanonymous/ComfyUI) with an OpenAI-compatible wrapper
- A self-hosted image generation server
- Azure OpenAI with DALL-E deployment

Enter the base URL (e.g. `http://localhost:7860/v1`) in the Base URL field.

---

## Switching providers

You can switch providers at any time from the key icon. Each API key is saved separately per provider — switching does not delete previously saved keys.
