---
layout: default
title: Getting Started
nav_order: 2
---

# Getting Started

This guide walks you through setting up BatchGen Image with AI and generating your first batch of images.

---

## 1. Install the app

Download and install **BatchGen Image with AI** from the Microsoft Store. Once installed, launch it from the Start menu.

---

## 2. Set up your API key

Before generating anything, you need an OpenAI API key.

1. Click the **key icon** (top right of the app)
2. Select **OpenAI** from the provider dropdown
3. Click **Get your API key →** to open platform.openai.com
4. Create an account, add billing, and copy your API key
5. Paste the key into the field — it saves automatically on blur
6. Click **Test** to confirm everything is working

Your API key is encrypted and stored on your device only. It is sent directly to OpenAI — nowhere else.

> **Cost note:** DALL-E 3 charges per image — Standard quality is $0.040/image, HD quality is $0.080/image. The app always shows an estimated total before you generate. See [Choosing an AI Provider](choosing-a-provider) for full pricing details.

---

## 3. Configure your persona (Step 1)

The persona defines the visual style and artistic direction applied to every image in a batch. Think of it as your AI art director's brief.

The app includes three starter personas:

- **Vivid Vera** — bold colours, high contrast, dramatic lighting
- **Minimalist Max** — clean lines, restrained palette, generous negative space
- **Fantasy Flora** — ethereal, painterly, rich textures

Select a persona by clicking its card. The detail panel shows the full visual style and quality bar currently applied.

You can customise any persona or add your own (up to 5 total). Click the **edit** button or use the persona menu in the header.

**Content Style** and **Black & White** toggles let you adjust the aesthetic further without editing the persona.

**Include Captions** — when on, any `caption` field in your image list is rendered as visible text in the image.

---

## 4. Load sample prompts (Step 2, optional)

Sample prompts show the AI examples of visual styles you like — golden hour photography, minimalist compositions, cinematic colour grading. They help ground the AI's interpretation and keep a batch visually consistent.

A default sample file is loaded automatically. You can replace it with your own `.yaml`, `.yml`, `.json`, or `.csv` file.

**YAML format:**

```yaml
- title: "Cinematic Wide"
  prompt: "Wide angle landscape, dramatic golden hour lighting, cinematic colour grading, shallow depth of field"

- title: "Clean Studio"
  prompt: "White studio background, soft diffused lighting, minimal composition, product photography"
```

This step is optional. Skip it to let the persona and template alone guide the style.

---

## 5. Prepare your image list (Step 3)

The image list is a CSV or YAML file with one row per image you want to generate. Each row becomes one API call.

### Try an example first

Click **Load Example** in Step 3 to load a pre-built example for the active template. It's the fastest way to see the format and run a test generation.

### Field reference

| Field | Aliases accepted | Required |
|---|---|---|
| `title` | `name`, `topic`, `subject` | Yes |
| `description` | `desc`, `prompt`, `content`, `caption_text` | Yes |
| `subject` | `main_subject`, `focal`, `focus` | No |
| `mood` | `tone`, `feeling`, `atmosphere`, `vibe` | No |
| `tags` | `keywords`, `styles`, `style`, `keyword` | No |
| `notes` | `note`, `guidance`, `context`, `instructions` | No |
| `caption` | `text`, `overlay`, `label`, `tagline` | No |

### CSV format

```csv
title,description,subject,mood,tags,notes,caption
"Summer Sale Poster","Bold promotional poster for a summer clothing sale","Bright beach lifestyle imagery","Energetic and fun","vibrant,summer,fashion","Bright yellows and blues. Plenty of white space for text overlay.","SUMMER SALE — UP TO 50% OFF"
"Autumn Collection","Warm editorial poster for an autumn fashion line","Model in autumn foliage","Warm and nostalgic","warm tones,editorial,fashion",,
```

### YAML format

```yaml
- title: "Summer Sale Poster"
  description: "Bold promotional poster for a summer clothing sale"
  subject: "Bright beach lifestyle imagery"
  mood: "Energetic and fun"
  tags: "vibrant, summer, fashion"
  notes: "Bright yellows and blues. Plenty of white space for text overlay."
  caption: "SUMMER SALE — UP TO 50% OFF"

- title: "Autumn Collection"
  description: "Warm editorial poster for an autumn fashion line"
  subject: "Model in autumn foliage"
  mood: "Warm and nostalgic"
  tags: "warm tones, editorial, fashion"
```

Only `title` and `description` are required. All other fields are optional.

---

## 6. Run your first generation

1. In Step 3, choose your **template** from the dropdown — each template has a preset size, aspect ratio, and quality level
2. Confirm your **output folder** (defaults to `Documents\BatchGenImage`)
3. Click **Preview Prompt** to review the assembled AI prompt for the first few items before spending anything
4. Click **Generate**

If your batch has more than 15 images, a confirmation dialog shows the estimated total cost before proceeding.

Output images are saved in a timestamped subfolder (e.g. `2026-03-01_14-30-00`) so each run is kept separate. A success banner at the end links directly to the output folder.

---

## Next steps

- Try different personas on the same image list to see how the artistic direction changes
- Use the **Prompt Preview** to tune your descriptions before a large run
- Explore the **Templates editor** (book icon in header) to customise dimensions, quality, and prompt guidance
- Add a `caption` column to your CSV to render visible text in images (useful for posters and banners)
