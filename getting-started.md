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

Before generating anything, you need an API key from your chosen AI provider.

1. Click the **key icon** (top right of the app)
2. Select a provider from the dropdown (start with **OpenAI** or **Fireworks AI**)
3. Click **Get your API key →** to open the provider's API key page
4. Create an account, add billing, and copy your API key
5. Paste the key into the field — it saves automatically
6. Click **Test** to confirm everything is working

Your API key is encrypted and stored on your device only. It is sent directly to your provider — nowhere else.

> **Cost note:** Image generation is charged per image. OpenAI DALL-E 3 Standard is $0.040/image, HD is $0.080/image. Fireworks AI FLUX models are significantly cheaper. The app always shows an estimated total before you generate. See [Choosing an AI Provider](choosing-a-provider) for full details.

---

## 3. Configure your persona (Step 1)

The persona defines the visual style and artistic direction applied to every image in a batch. Think of it as your AI art director's brief.

The app includes three starter personas:

- **Vivid Vera** — bold colours, high contrast, dramatic lighting. Great for posters and social media.
- **Minimalist Max** — clean lines, restrained palette, generous negative space. Great for product shots and banners.
- **Fantasy Flora** — ethereal, painterly, rich textures. Great for book covers and album art.

Select a persona by clicking its card. You can customise any persona or add your own (up to 5 total) by clicking the edit button on the card.

**Content Style** — choose from 18 styles including Photorealistic, Cinematic, Watercolor, Oil Painting, Anime, Pixel Art, Noir, and more. Applied to all images in the batch.

**Black & White** — toggle to convert all outputs to monochrome.

**Include Captions** — when on, any `caption` field in your image list is rendered as visible text in the image. See [Captions](captions) for styling options.

---

## 4. Load sample prompts (Step 2, optional)

Sample prompts give the AI examples of visual styles you like — golden hour photography, minimalist compositions, cinematic colour grading. They help ground the AI's interpretation and keep a batch visually consistent.

A default sample file is loaded automatically. You can replace it with your own `.yaml`, `.yml`, or `.csv` file.

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
| `description` | `desc`, `prompt`, `content` | Yes |
| `subject` | `main_subject`, `focal`, `focus` | No |
| `mood` | `tone`, `feeling`, `atmosphere`, `vibe` | No |
| `tags` | `keywords`, `styles`, `style`, `keyword` | No |
| `notes` | `note`, `guidance`, `context`, `instructions` | No |
| `caption` | `text`, `overlay`, `label`, `tagline` | No |

### CSV format

```csv
title,description,subject,mood,tags,notes,caption
"Summer Festival Poster","Vibrant outdoor music festival at sunset with crowd and stage lights","Concert stage","Energetic and festive","music,festival,summer","Warm golden hour lighting","Summer Beats 2025"
"Tech Conference","Sleek modern conference poster with geometric shapes and neon accents","Abstract tech shapes","Professional and futuristic","technology,minimal,neon",,
```

### YAML format

```yaml
- title: "Summer Festival Poster"
  description: "Vibrant outdoor music festival at sunset with crowd and stage lights"
  subject: "Concert stage"
  mood: "Energetic and festive"
  tags: "music, festival, summer"
  notes: "Warm golden hour lighting"
  caption: "Summer Beats 2025"

- title: "Tech Conference"
  description: "Sleek modern conference poster with geometric shapes and neon accents"
  subject: "Abstract tech shapes"
  mood: "Professional and futuristic"
  tags: "technology, minimal, neon"
```

Only `title` and `description` are required.

---

## 6. Run your first generation

1. Choose your **template** from the dropdown — each template has a preset size, aspect ratio, and quality level
2. Confirm your **output folder** (defaults to `Documents\BatchGenImage`)
3. Click **Preview Prompt** to review the assembled AI prompt for the first few items
4. Click **Generate**

If your batch has more than 15 images, a confirmation dialog shows the estimated total cost before proceeding.

Output images are saved in a timestamped subfolder (e.g. `2026-03-01_14-30-00`) so each run is kept separate. A success banner at the end links directly to the output folder.

---

## Next steps

- Try different personas on the same image list to see how artistic direction changes results
- Use **Prompt Preview** to tune your descriptions before a large run
- Explore the **Templates editor** (book icon in the header) to customise dimensions, quality, and prompt guidance
- Add a `caption` column to render visible text in images — see [Captions](captions) for font and position options
