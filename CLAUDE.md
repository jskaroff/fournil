# Fournil — Claude Instructions

## Project Overview
iPad app for managing sourdough bread baking. Currently in design phase.
- `index.html` — design prototype landing page (the source of truth for what's ready/wired)
- `design/prototypes/` — interactive HTML prototypes
- `design/wireframes/` — SVG wireframes (1194×834 landscape iPad format)

## Keeping the Landing Page Current

**Whenever new wireframes or HTML prototypes are added**, update `index.html` to reflect them:

### New SVG wireframe added
Add a wireframe card to the "Wireframes" section in `index.html`. Each card needs:
- `class="proto-card wireframe-card"` with `data-svg` and `data-title` attributes
- A logical eyebrow (e.g., `Tab 01 · Starter`, `Sheet · Bake`, `Screen · Settings`)
- A short description of what the screen does
- `badge-wireframe` badge

If it's a variant of an existing screen (e.g., `06b-...`), add it to the existing card's `data-svg` and `data-title` comma-separated lists and update the variant count in the badge.

### New HTML prototype added
Move the corresponding wireframe card from "Wireframes" to "Ready to preview" — change it from a `div.wireframe-card` to an `<a href="...">` link with `badge-ready` badge. Keep the same eyebrow/title/description.

### Wireframe naming conventions
- `01-` through `15-` = main screens
- Suffix letters `a`, `b`, `c` = layout variants of the same screen
- Prefix maps to tabs: `01`=Starter, `02`=Bake, `03`=Log; sheets/modals use descriptive names

## Deploying
Push to `main` on GitHub. Vercel auto-deploys from `main`.

```
git add -A
git commit -m "..."
git push
```

## Design System
Fonts: Fraunces (headings), Source Serif 4 (body), Fira Mono (labels)
Colors: `--parchment`, `--flour-dust`, `--crust-brown`, `--wheat-field`, `--golden-crust`, `--sage`
