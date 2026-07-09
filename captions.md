---
layout: default
title: Captions
nav_order: 4
---

# Captions

Captions render visible text directly onto generated images. This is useful for posters, banners, social media graphics, invitations, book covers, and other layouts where the headline or tagline should appear in the final image.

---

## Enabling captions

In Step 3, turn **Include Captions** on.

When enabled, any row in your image list with a non-empty `caption` field will receive a text overlay after the image is generated.

If a row has no caption value, that image is saved without an overlay.

---

## Adding captions to your image list

Add a `caption` column to your CSV or YAML file:

```csv
title,description,caption
"Summer Festival","Vibrant outdoor music festival at sunset","Summer Beats 2025"
"Product Launch","Clean minimal product shot on white","Now Available"
"Team Photo","Studio portrait of creative team",
```

Aliases also work:

- `text`
- `overlay`
- `label`
- `tagline`

Rows with an empty caption field generate normally without any text overlay.

### Generate captions with the built-in CSV tool

The **Generate CSV** dialog includes an **Add AI captions column** switch.

When that is on, the app asks the AI to create a short `caption` value for each row so the file is ready for caption overlays.

> **Model note:** AI CSV writing uses a chat-capable model. If your active connection is an image-only model like FLUX, switch to a chat-capable connection if you want AI-written caption fields. You can always type captions manually either way.

---

## Caption options

When **Include Captions** is on, these controls appear:

**Font** — choose from the fonts installed on your Windows machine.

**Size** — numeric font size in pixels.

**Color** — caption text color.

**Background** — choose `None`, `Dark`, or `Light` to place a rounded block behind the caption for readability.

**Position** — where the caption is placed:

| Option | Description |
|---|---|
| Bottom | Along the bottom edge |
| Top | Along the top edge |
| Middle | Centered placement |
| Diagonal | Angled treatment across the image |

**Text Align** — choose `Center` or `Left`.

**Margin** — controls distance from the top or bottom edge.

Important:

- Margin applies to `Top` and `Bottom`
- `Middle` and `Diagonal` ignore margin by design

**All variants** — save four captioned copies of each image, one per position. The image is generated once and composited locally four times, so there is no extra image-generation API cost.

**Save without caption** — save an additional plain version of the image alongside the captioned one.

---

## Caption preview

The app includes a caption preview card in Step 3 so you can check how the current font, size, background, and position look before running the full batch.

If your image list already has captions, the preview uses the first non-empty one it finds. Otherwise it falls back to sample text.

---

## How it works

Captions are added **after** the AI image is returned.

That means:

- the image model still generates the base artwork
- the app then composites the caption locally on your PC
- the original API response is not modified on the provider side

This is why caption overlays can still work even when your image model is image-only. The only part that needs a chat-capable model is **AI-writing** the caption text for the CSV generator.
