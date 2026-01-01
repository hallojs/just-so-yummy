# Copilot Instructions for Just So Yummy

This is a Hugo-based recipe website using the Etch theme. The site is **multilingual** (German and English) and deployed to GitHub Pages at https://just-so-yummy.de/.

## Project Structure

- **Content**: All recipes are in `content/posts` as Markdown files
- **Categories**: Category definitions are in `content/categories`
- **Theme**: Custom fork of Etch theme in `themes/etch`
- **Static assets**: Images and favicons in `static`
- **Configuration**: Site config in `config.toml`
- **Layouts**: Custom layout overrides in `layouts` (including SEO partials)
- **Workflows**: GitHub Actions workflow in `.github/workflows/gh-pages.yml`

## Multilingual Support

The site supports German (default) and English. Language-specific content uses file naming convention:

- German (default): `recipe_name.md`
- English: `recipe_name.en.md`

A language switcher in the header allows visitors to switch between languages.

### Creating Multilingual Recipes

When creating a new recipe, create both language versions:

1. German version: `content/posts/recipe_name.md`
2. English version: `content/posts/recipe_name.en.md`

Both files should have the same base filename and share the same image.

## Recipe File Format

When creating new recipes, follow this frontmatter structure:

**German (default):**
```md
---
title: "Rezeptname"
draft: false
image: /images/recipe_name.webp
categories: ["category-slug"]
description: ""
date: ""
prepTime: ""
cookTime: ""
servings: ""
---
```

**English:**
```md
---
title: "Recipe Name"
draft: false
image: /images/recipe_name.webp
categories: ["category-slug"]
description: ""
date: ""
prepTime: ""
cookTime: ""
servings: ""
---
```

Recipes can belong to multiple categories, e.g., `categories: ["hauptgerichte", "pasta-pizza-risotto"]`.

### Available Categories

- `hauptgerichte` - Main dishes
- `pasta-pizza-risotto` - Italian dishes
- `salate-beilagen` - Salads and sides
- `snacks-brot-herzhaftes-gebaeck` - Snacks and bread
- `suesses-gebaeck` - Desserts and pastries
- `vegetarisch-vegan` - Vegetarian/Vegan

### Recipe Content Structure

**German recipes:**
1. Brief intro about serving size (e.g., "Die Menge reicht für 2 Portionen.")
2. `# Zutaten` (Ingredients) section(s) with bullet list
   - For complex recipes, use multiple ingredient sections (e.g., `# Zutaten für die Tomatensauce`)
3. `# Zubereitung` (Preparation) section with numbered steps or paragraphs
   - For complex recipes, use multiple preparation sections
4. End with "Guten Appetit!"

**English recipes:**
1. Brief intro about serving size (e.g., "This serves 2 people.")
2. `# Ingredients` section(s) with bullet list
   - For complex recipes, use multiple ingredient sections (e.g., `# Ingredients for the Tomato Sauce`)
3. `# Instructions` section with numbered steps or paragraphs
   - For complex recipes, use multiple preparation sections
4. End with "Enjoy your meal!"

## Hugo Commands

```sh
# Run local development server
hugo server

# Build site
hugo --minify
```

## Theme Customizations

The Etch theme has been customized with:

- Category grid display on homepage
- Recipe search functionality
- Language switcher in header (German/English)
- Custom fonts (Dayrom)
- Background image support per recipe
- SEO and structured data partials (`layouts/partials/seo.html`, `layouts/partials/structured-data.html`)

## Deployment

The site deploys automatically via GitHub Actions (`.github/workflows/gh-pages.yml`) when pushing to `main` branch.

## Recipe Image Generation

When creating images for new recipes, follow these guidelines to match the existing style:

### Image Specifications

- **Format**: WebP
- **Dimensions**: 1792 × 1024 pixels (16:9 aspect ratio)
- **Location**: `static/images/`
- **Naming**: `recipe_name.webp` (matching the recipe markdown filename)

### Style Requirements

The recipe images use a **soft watercolor illustration style** with these characteristics:

- Warm, inviting watercolor painting technique
- Soft background wash that fades to the edges (NO decorative borders or corner ornaments)
- Full bleed illustration extending to all edges
- Cozy, hand-painted artistic look
- Food presented appetizingly with relevant ingredients/garnishes visible

### Image Generation Prompt Template

When generating images with AI tools, use this prompt structure with 3 existing images as style references:

```
Create a new illustration matching EXACTLY the same style as these three reference images. 
The subject is: [DETAILED FOOD DESCRIPTION WITH GARNISHES AND PRESENTATION]. 
Copy the EXACT same: watercolor illustration technique, color warmth, soft background 
wash style, and overall artistic feel from the reference images. NO decorative borders 
or corner ornaments - the image should extend to the edges like a full bleed illustration. 
The new image must look like it belongs to the same series.
```

**Important settings:**
- Use 3 existing recipe images as style references (e.g., `lasagne.webp`, `waffeln.webp`, `pizza.webp`)
- Apply negative prompt: `decorative border, corner ornaments, frame, border decorations, ornamental frame`
- Aspect ratio: 16:9
- Resolution: high

### Image Conversion

After generating the image, convert to WebP format at the correct dimensions:

```sh
# Resize to 1792x1024
sips -z 1024 1792 /path/to/generated_image.png --out /tmp/resized.png

# Convert to WebP
cwebp -q 85 /tmp/resized.png -o static/images/recipe_name.webp
```

## Code Style

- Use German for German content files, English for English content files
- Image files should be `.webp` format
- Category slugs use lowercase with hyphens
- Keep recipes consistent with existing format
- Recipes can have multiple categories when applicable
