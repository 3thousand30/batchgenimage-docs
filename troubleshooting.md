---
layout: default
title: Troubleshooting
nav_order: 5
---

# Troubleshooting

---

## "API Key Required" warning

This appears when the **active connection** does not have a saved API key yet.

1. Click the **key icon** in the header
2. Select the connection you want to use
3. Paste the API key
4. Click **Test connection**

If you already entered a key and still see the warning, confirm that the correct connection is set as active.

---

## Generation fails with an error

Open the **Logs panel** from the clipboard icon in the header to see the exact error for each image.

Common causes:

| Error | Fix |
|---|---|
| `401 Unauthorized` | API key is invalid, missing, or tied to a different connection than the active one. |
| `403 Forbidden` | Your account or endpoint does not have access to that model. |
| `429 Too Many Requests` | You hit a rate limit. Try a smaller batch or wait and retry. |
| `402 Payment Required` | Your provider account has no credits or billing is not enabled. |
| `500 / 503 Server Error` | Provider-side issue. Retry later. |
| `content_policy_violation` | The provider rejected the prompt. Rephrase the description. |
| `invalid_size` | The template dimensions do not match what that model supports. |

---

## The reference folder seems to do nothing

Most often this is because the folder was selected but never analyzed.

Check this:

- load the folder in Step 2
- click **Analyze**
- wait for the analysis summary to appear

Important:

- the app does **not** auto-analyze the folder
- until analysis is current, prompt preview and generation ignore that folder
- if you change the folder, provider, or model, click **Analyze again**

If Balanced and Sample are unavailable, the app is telling you there is no current Step 2 analysis yet.

---

## "Style-reference folder analysis unavailable" warning

This means your current setup can still generate images, but it cannot inspect a reference folder.

Common reasons:

- the active model is image-only, such as FLUX
- the provider does not expose a usable vision-capable chat model for analysis
- you are on a Fireworks connection, which does not support this analysis path in the current app

Fix:

- switch to OpenAI or OpenRouter for Step 2 analysis
- or skip Step 2 and rely on persona, content style, and row descriptions only

---

## Sample analysis is unavailable in the persona editor

Persona sample analysis has similar requirements to Step 2 reference analysis.

It can fail when:

- the active connection is image-only
- the provider does not provide a vision-capable chat path
- the connection is Fireworks AI, which does not support sample analysis in the current app

Fix:

- switch to OpenAI or OpenRouter
- then reopen the persona editor and use **Analyse samples** again

---

## Fireworks AI images look wrong or use the wrong size

FLUX models are often square-only. If you are using a portrait or landscape template, choose a model that supports that shape instead of assuming every image model supports every template.

If a provider returns `invalid_size`, switch either:

- to a different template
- or to a different model on that connection

---

## Some images generated, others failed

Partial failures are normal. Successfully generated images are kept, and failures are logged row by row.

You can:

- fix the failed rows
- run the batch again
- keep **Skip already generated files** on so existing outputs are not regenerated

---

## The Generate button is disabled

The button stays disabled until:

- an image list file is selected
- an output folder is set

Check both fields in Step 3.

---

## Images look nothing like what I described

Try these in order:

- improve the `description` field with clearer subject, lighting, and composition detail
- use `subject`, `mood`, `tags`, and `notes` instead of packing everything into one line
- switch persona or edit the current persona
- use **Prompt Preview** to inspect the assembled prompt
- try a different content style
- if you loaded a reference folder, check whether Generation Focus is set to Persona, Balanced, or Sample

If the output is drifting too much toward the reference folder, switch focus back to **Persona**.

---

## Captions are not appearing on images

Check all of these:

- **Include Captions** is turned on in Step 3
- the row has a non-empty `caption` value
- the header is one of: `caption`, `text`, `overlay`, `label`, or `tagline`
- the file is actually the latest CSV or YAML you intended to load

Good test:

- load one of the example files
- confirm captions appear there
- then compare its headers with your own file

Remember that captions are added locally after generation. If the row has no caption value, the image is saved without text.

---

## The AI CSV generator created a simple starter CSV instead of AI-written rows

This usually means the active connection could not complete the chat-based CSV writing step.

Common reasons:

- the active model is image-only, such as FLUX
- the endpoint supports image generation but not chat completions
- the provider returned an error during CSV generation

Fix:

- switch to a chat-capable connection
- use **Generate CSV** again

The app can still save a local starter CSV so you are not blocked.

---

## The app won't start or crashes on launch

- Ensure you are running Windows 10 or later
- Reinstall from the Microsoft Store
- Check for pending Windows updates

If it still fails, [open an issue](https://github.com/3thousand30/batchgenimage-docs/issues) with a description of what happens.

---

## Output folder not opening

The **Open output folder** action uses Windows Explorer.

If it does not open:

- open the configured output folder manually
- look for the newest timestamped subfolder from your last run
