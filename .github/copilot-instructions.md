# Copilot Instructions for Just So Yummy

This is a Hugo-based recipe website using the Etch theme. The site is written in German and deployed to GitHub Pages.

## Project Structure

- **Content**: All recipes are in `content/posts` as Markdown files
- **Categories**: Category definitions are in `content/categories`
- **Theme**: Custom fork of Etch theme in `themes/etch`
- **Static assets**: Images and favicons in `static`
- **Configuration**: Site config in `config.toml`

## Recipe File Format

When creating new recipes, follow this frontmatter structure:

```md
---
title: "Recipe Name"
draft: false
image: /images/recipe_name.webp
categories: ["category-slug"]
---
```

### Available Categories

- `hauptgerichte` - Main dishes
- `pasta-pizza-risotto` - Italian dishes
- `salate-beilagen` - Salads and sides
- `snacks-brot-herzhaftes-gebaeck` - Snacks and bread
- `suesses-gebaeck` - Desserts and pastries
- `vegetarisch-vegan` - Vegetarian/Vegan

### Recipe Content Structure

1. Brief intro about serving size
2. `# Zutaten` (Ingredients) section with bullet list
3. `# Zubereitung` (Preparation) section with numbered steps
4. End with "Guten Appetit!"

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
- German translations
- Custom fonts (Dayrom)
- Background image support per recipe

## Deployment

The site deploys automatically via GitHub Actions when pushing to `main` branch.

## Code Style

- Use German for all user-facing content
- Image files should be `.webp` format
- Category slugs use lowercase with hyphens
- Keep recipes consistent with existing format
