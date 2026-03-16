---
layout: default
title: Captions
nav_order: 4
---

# Captions

The caption feature renders visible text directly onto generated images — useful for posters, banners, social media graphics, and book covers where the title or tagline needs to appear in the image itself.

---

## Enabling captions

In Step 3 (Generate), toggle **Include Captions** on. When enabled, any `caption` field in your image list will be composited onto the image after generation.

If an image row has no `caption` value, no overlay is applied — the image is saved as-is.

---

## Adding captions to your image list

Add a `caption` column to your CSV or YAML file:

```csv
title,description,caption
"Summer Festival","Vibrant outdoor music festival at sunset","Summer Beats 2025"
"Product Launch","Clean minimal product shot on white","Now Available"
"Team Photo","Studio portrait of creative team",
```

Rows with an empty `caption` field generate normally without an overlay.

The `caption` field also accepts these aliases: `text`, `overlay`, `label`, `tagline`.

---

## Caption options

When **Include Captions** is on, four additional controls appear:

**Position** — where the caption bar is placed on the image:

| Option | Description |
|---|---|
| Bottom | Bar along the bottom edge (default) |
| Top | Bar along the top edge |
| Middle | Lower-third placement |
| Diagonal | Angled band across the centre |
| Mix (all) | Cycles through all four positions across the batch |

**Font** — the typeface used for the caption text:

| Option | Typeface |
|---|---|
| Serif | Georgia — classic, editorial feel |
| Sans-serif | Arial — clean and modern |
| Impact | Impact — bold, poster-style |

**Size** — font size relative to the image width:

| Option | Approximate size on 1024px image |
|---|---|
| Normal | ~32px |
| Large | ~46px |
| X-Large | ~64px |

**All variants** — saves four copies of each image, one per position (Bottom, Top, Middle, Diagonal). No extra API cost — the image is generated once and composited four times.

**Also save without caption** — saves an additional plain copy of each image alongside the captioned version. Useful when you want both versions.

---

## How it works

After the AI generates each image, the app reads the caption field and composites an SVG text overlay using [sharp](https://sharp.pixelplumbing.com/). The bar colour (dark or light) is chosen automatically by sampling the luminance of the region the bar will cover — so white text appears on dark areas and dark text on light areas.

The original API image is not modified. The captioned version is a new PNG written to your output folder.
