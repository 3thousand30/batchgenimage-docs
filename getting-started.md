---
layout: default
title: Getting Started
nav_order: 2
---

# Getting Started

This guide walks you through setting up Batch Generate Image with any AI and running your first batch.

---

## 1. Install the app

Install **Batch Generate Image with any AI** from the Microsoft Store, then launch it from the Start menu.

The first launch opens a **Getting Started** dialog automatically. You can reopen it any time with the **?** button in the header.

---

## 2. Set up your AI connection

Before generating anything, you need an API key from your chosen provider.

1. Click the **key icon** in the top-right header
2. Select a provider from the dropdown
3. Click **Get API key** if you need to open the provider page
4. Paste your API key
5. Click **Test connection**
6. Click **Done**

Your API key is encrypted and stored on your device using Windows DPAPI. It is sent directly to your provider.

> **Multiple connections:** You can save up to 10 named connections. This is useful when you want one setup for OpenAI, another for OpenRouter, another for a cheaper FLUX batch model, and another for a custom endpoint. Use **Set as active connection** to switch.

> **Practical tip:** OpenAI is the simplest first-run option. OpenRouter is a good second choice if you want one key for multiple model families. Fireworks AI and Together AI are useful for cheaper open-source image models, but some analysis features may be unavailable depending on the model.

---

## 3. Configure your persona (Step 1)

The persona is your reusable visual brief. It shapes the overall style of the batch before the row-specific description is added.

The app includes three starter personas:

- **Vivid Vera** — bold colours, stronger contrast, dramatic energy
- **Minimalist Max** — cleaner layouts, restraint, negative space
- **Fantasy Flora** — painterly, atmospheric, richer storytelling mood

You can also create your own personas and edit:

- artist type
- visual mediums
- lighting styles
- color palettes
- moods
- composition rules
- do / avoid guidance
- quality requirements
- 10 visual datapoints

To edit a persona, click **Edit** on the persona card.

### Analyze sample images for persona suggestions

Inside the persona editor, use **Analyse samples** to pick a folder of your own images. The app will inspect that folder and suggest persona values that better match the style of those images.

This is separate from Step 2 style-reference analysis:

- **Sample analysis** helps you improve the persona itself
- **Style-reference analysis** guides a specific generation run

### Global style controls in Step 1

**Content Style** — choose from 24 styles including Photorealistic, Cinematic, Watercolor, Storybook, Editorial Illustration, Coloring Book Line Art, Invitation / Stationery, and more.

**Black & White** — convert all outputs to greyscale.

**Include Captions** — when on, any `caption` field in your image list is rendered as visible text in the image. See [Captions](captions) for layout and preview options.

---

## 4. Load style reference images (Step 2, optional)

Style-reference images help the app understand the look you want from a specific folder of inspiration images.

1. Choose a folder containing `.png`, `.jpg`, `.jpeg`, `.webp`, or `.gif` files
2. Click **Analyze**

Important behavior:

- The app does **not** auto-analyze the folder
- Until you click **Analyze**, prompt preview and generation ignore the reference folder
- Your prompt, persona, template, and content style stay primary
- The reference folder acts as soft secondary guidance only

After analysis, the app can show:

- a short summary of the folder
- whether the folder looks consistent or mixed
- cue matches and gaps compared with the active persona
- a 10-point visual comparison between reference traits and persona traits

> **Provider note:** Style-reference analysis needs a vision-capable chat model. Image-only generation models such as FLUX can still generate final images, but they cannot inspect a folder by themselves. Some providers can temporarily fall back to a separate vision model for analysis; others cannot.

> **Re-run when needed:** If you change the folder, change the active provider, or change the model, click **Analyze again**. Balanced and Sample generation focus require a current analysis.

---

## 5. Prepare your image list (Step 3)

The image list is a CSV or YAML file with one row per image you want to generate. Each row becomes one image request.

### Generate a list with AI

Click **Generate CSV** in Step 3 to open the built-in list generator. Enter the category, subject, style, mood, and notes, then generate a ready-to-use CSV.

The generated file is saved to:

```text
Documents\BatchGenImage\generated-lists\
```

It is also loaded into the app automatically.

You can optionally turn on **Add AI captions column** in the CSV dialog. This adds a `caption` field for each row so caption overlays are ready to use.

> **Model note:** AI CSV writing uses a chat-capable model. If your active connection is an image-only model like FLUX, switch to a chat-capable connection for AI-written CSV rows and captions. If not, the app can still save a simpler local starter CSV.

### Try an example first

Click **Load Example** in Step 3 to load an example file for the active template.

### Field reference

| Field | Aliases accepted | Required |
|---|---|---|
| `title` | `name`, `topic` | Yes |
| `description` | `desc`, `prompt`, `content` | Yes |
| `subject` | `main_subject`, `focal`, `focus` | No |
| `mood` | `tone`, `feeling`, `atmosphere`, `vibe` | No |
| `tags` | `keywords`, `styles`, `style`, `keyword` | No |
| `notes` | `note`, `guidance`, `context`, `instructions` | No |
| `caption` | `text`, `overlay`, `label`, `tagline` | No |

### CSV format

Use semicolons inside the `tags` field if you want multiple tags:

```csv
title,description,subject,mood,tags,notes,caption
"Summer Festival Poster","Vibrant outdoor music festival at sunset with crowd and stage lights","Concert stage","Energetic and festive","music;festival;summer","Warm golden hour lighting","Summer Beats 2025"
"Tech Conference","Sleek modern conference poster with geometric shapes and neon accents","Abstract tech shapes","Professional and futuristic","technology;minimal;neon",,
```

Quoted headers are supported too:

```csv
"title","description","caption"
"Summer Festival Poster","Vibrant outdoor music festival at sunset","Summer Beats 2025"
```

### YAML format

For YAML, use arrays for `tags`:

```yaml
- title: "Summer Festival Poster"
  description: "Vibrant outdoor music festival at sunset with crowd and stage lights"
  subject: "Concert stage"
  mood: "Energetic and festive"
  tags:
    - "music"
    - "festival"
    - "summer"
  notes: "Warm golden hour lighting"
  caption: "Summer Beats 2025"

- title: "Tech Conference"
  description: "Sleek modern conference poster with geometric shapes and neon accents"
  subject: "Abstract tech shapes"
  mood: "Professional and futuristic"
  tags:
    - "technology"
    - "minimal"
    - "neon"
```

Only `title` and `description` are required.

---

## 6. Run your first generation

1. Choose your **template**
2. Confirm your **output folder**
3. If you analyzed a reference folder, choose the **Generation Focus**
4. Click **Preview Prompt**
5. Click **Generate**

Large batches show a cost confirmation before the app starts.

### Templates

The app includes 12 built-in templates plus a custom template. Current built-in options include:

- Poster
- Social Media Post
- Banner / Cover
- Book Cover
- Book Illustration Page
- Children's Book Illustration
- Storybook Spread
- Coloring Book Page
- Invitation / Save the Date
- Product Mockup
- Album Art

### Generation Focus

When a current Step 2 analysis exists, you can choose:

| Option | Effect |
|---|---|
| **Persona** | Follow the persona only. Reference guidance is ignored. |
| **Balanced** | Share influence between persona and reference folder. |
| **Sample** | Lean more strongly toward the reference folder while still respecting persona rules. |

If no current analysis exists, only **Persona** is available.

---

## Next steps

- Try different personas on the same image list to see how artistic direction changes results
- Use **Analyse samples** inside the persona editor if you want the persona to better match your existing image library
- Use **Prompt Preview** before large batches
- Explore the **Templates** editor in the header to customize dimensions, quality, and prompt guidance
- Add a `caption` column or use **Add AI captions column** in the CSV generator if you want visible text on the final images
