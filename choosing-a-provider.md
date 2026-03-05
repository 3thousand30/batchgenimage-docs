---
layout: default
title: Choosing an AI Provider
nav_order: 3
---

# Choosing an AI Provider

BatchGen Image with AI generates images using **DALL-E 3** via the OpenAI API. Unlike text generation — which works with dozens of compatible providers — image generation requires a provider that supports the DALL-E 3 image endpoint.

---

## Supported providers

| Provider | Notes | Sign up |
|---|---|---|
| **OpenAI** | Default. Full DALL-E 3 support, Standard and HD quality. | [platform.openai.com](https://platform.openai.com) |
| **Fireworks AI** | Faster and cheaper image generation via their endpoint. | [fireworks.ai](https://fireworks.ai) |
| **Custom** | Any OpenAI-compatible image endpoint. | — |

For most users, **OpenAI** is the right choice. It's the most reliable, supports all quality levels, and has the most predictable pricing.

---

## OpenAI pricing

DALL-E 3 charges per image, not per token.

| Quality | Price per image |
|---|---|
| Standard | $0.040 |
| HD | $0.080 |

**Standard** is fine for social media graphics, web images, and drafts. **HD** is better for print, book covers, and hero images where detail matters.

Each template in the app has a quality setting. You can change it in the Templates editor. The app always shows an estimated total cost before you generate.

---

## Getting your OpenAI API key

1. Go to [platform.openai.com](https://platform.openai.com) and create an account
2. Add a payment method under **Billing**
3. Go to **API keys** and click **Create new secret key**
4. Copy the key — you won't be able to see it again
5. Paste it into BatchGen Image via the key icon in the top-right header

> OpenAI gives new accounts some free credits to start with. Once those run out, billing is pay-as-you-go.

---

## Using Fireworks AI

Fireworks AI offers image generation at lower cost with faster response times. To use it:

1. Sign up at [fireworks.ai](https://fireworks.ai) and get an API key
2. In the app, open **AI Provider Settings** (key icon)
3. Select **Fireworks AI** from the provider dropdown
4. Paste your Fireworks API key

---

## Using a custom endpoint

If you have access to another OpenAI-compatible image endpoint, select **Custom** from the provider dropdown and enter the base URL manually. The endpoint must support the `/images/generations` path in OpenAI format.

---

## Switching providers

You can switch providers at any time from the key icon. Each API key is saved separately — switching providers doesn't delete your previous keys.
