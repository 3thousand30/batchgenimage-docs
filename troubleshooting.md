---
layout: default
title: Troubleshooting
nav_order: 4
---

# Troubleshooting

---

## "API Key Required" warning

The app shows this when no API key has been saved yet.

1. Click the **key icon** in the top-right header
2. Paste your OpenAI API key into the field
3. Click **Test** to verify the connection

If you've already entered a key and still see this, try re-entering it. The key is stored in Windows secure storage — if that's unavailable on your machine, the app will prompt you each session.

---

## Generation fails with an error

Open the **Logs panel** (clipboard icon in the header) to see the exact error message per image.

**Common causes:**

| Error | Fix |
|---|---|
| `401 Unauthorized` | API key is invalid or expired. Re-enter it in settings. |
| `429 Too Many Requests` | Rate limit hit. The app retries automatically with backoff, but very large batches may exceed your account's rate limit. |
| `402 Payment Required` | Your OpenAI account has run out of credits. Add billing at platform.openai.com. |
| `content_policy_violation` | DALL-E 3 rejected the prompt. Review the description for the failed image and rephrase. |
| `invalid_size` | The template dimensions don't map to a supported DALL-E 3 size. Edit the template to use 1024×1024, 1792×1024, or 1024×1792. |

---

## Some images generated, others failed

Partial failures are normal — DALL-E 3 occasionally rejects prompts for content policy reasons. Successfully generated images are saved; failed ones are logged with the reason.

Check the Logs panel for details on which items failed and why.

---

## The Generate button is disabled

The button stays disabled until:

- An image list file is selected
- An output folder is set

Check both fields in Step 3. The image list field shows a drop zone if no file is loaded.

---

## Images look nothing like what I described

A few things to try:

- **Improve the description** — be specific about subject, lighting, mood, and composition. Vague descriptions give vague results.
- **Use the subject and mood fields** — these are injected separately from the description and give DALL-E 3 stronger signals.
- **Check your persona** — the visual style in the active persona shapes every image. If the persona has strong stylistic overrides (e.g. "oil painting") it may override realistic descriptions. Edit or switch the persona.
- **Use Prompt Preview** — click Preview Prompt in Step 3 to see exactly what's being sent to the API before spending money.
- **Switch to HD quality** — for complex scenes, HD often follows the prompt more faithfully.

---

## The app won't start / crashes on launch

- Ensure you're running Windows 10 or later
- Try reinstalling from the Microsoft Store
- Check for a pending Windows update

If the issue persists, [open an issue](https://github.com/3thousand30/batchgenimage-docs/issues) with a description of what happens.

---

## Output folder not opening

The **Open output folder** button after generation uses Windows Explorer. If it doesn't open, navigate manually to `Documents\BatchGenImage` and look for the most recent timestamped subfolder.
