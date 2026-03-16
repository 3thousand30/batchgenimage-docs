---
layout: default
title: Troubleshooting
nav_order: 5
---

# Troubleshooting

---

## "API Key Required" warning

The app shows this when no API key has been saved yet.

1. Click the **key icon** in the top-right header
2. Select your provider and paste your API key
3. Click **Test** to verify the connection

If you've already entered a key and still see this, try re-entering it. The key is stored in Windows secure storage — if that's unavailable on your machine, the app will prompt you each session.

---

## Generation fails with an error

Open the **Logs panel** (clipboard icon in the header) to see the exact error message per image.

**Common causes:**

| Error | Fix |
|---|---|
| `401 Unauthorized` | API key is invalid or expired. Re-enter it in settings. |
| `403 Forbidden` | Your account doesn't have access to this model or endpoint. |
| `429 Too Many Requests` | Rate limit hit. The app retries automatically with backoff, but very large batches may exceed your account's tier. Slow down or upgrade your plan. |
| `402 Payment Required` | Your account has run out of credits. Add billing at your provider's dashboard. |
| `500 / 503 Server Error` | Provider-side error. The app retries automatically. If it persists, try again later. |
| `content_policy_violation` | The AI rejected the prompt. Review the description for the failed image and rephrase. Avoid references to real people, violence, or explicit content. |
| `invalid_size` | The template dimensions don't map to a supported size for this model. For OpenAI: use 1024×1024, 1024×1792, or 1792×1024. For Fireworks FLUX: only 1024×1024 is supported. |

---

## Fireworks AI — image looks wrong or wrong size

FLUX models on Fireworks only support **1024×1024** (square). If you're using a portrait or landscape template, switch to an SDXL model on Fireworks, which supports 768×1344 portrait and 1344×768 landscape.

---

## Some images generated, others failed

Partial failures are normal — AI providers occasionally reject prompts for content policy reasons or experience transient errors. Successfully generated images are saved; failed ones are logged with the reason.

Check the Logs panel for details on which items failed and why. You can fix the offending rows and re-run — skip existing files is on by default so previously generated images won't be regenerated.

---

## The Generate button is disabled

The button stays disabled until:

- An image list file is selected
- An output folder is set

Check both fields in Step 3.

---

## Images look nothing like what I described

A few things to try:

- **Improve the description** — be specific about subject, lighting, mood, and composition. Vague descriptions give vague results.
- **Use the subject and mood fields** — these are injected separately and give the model stronger signals.
- **Check your persona** — the visual style in the active persona shapes every image. If the persona has strong stylistic overrides it may override your description. Edit or switch the persona.
- **Use Prompt Preview** — click **Preview Prompt** in Step 3 to see exactly what's being sent to the API before spending money.
- **Switch to HD quality** (OpenAI) — for complex scenes, HD often follows the prompt more faithfully.
- **Try a different content style** — if Photorealistic isn't working, try Cinematic or Digital Art.

---

## Captions not appearing on images

- Check that **Include Captions** is toggled on in Output Settings
- Confirm the relevant rows in your image list have a non-empty `caption` (or `text` / `tagline`) column
- Use **Prompt Preview** to verify the caption field is being picked up — the preview shows which fields were parsed

---

## The app won't start / crashes on launch

- Ensure you're running Windows 10 or later
- Try reinstalling from the Microsoft Store
- Check for a pending Windows update

If the issue persists, [open an issue](https://github.com/3thousand30/batchgenimage-docs/issues) with a description of what happens.

---

## Output folder not opening

The **Open output folder** button after generation uses Windows Explorer. If it doesn't open, navigate manually to your configured output folder and look for the most recent timestamped subfolder (e.g. `2026-03-01_14-30-00`).
