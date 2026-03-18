# Wireframe: Starter List (Non-Empty State Details)

This extends the non-empty state described in 02-starter-tab.md with additional
layout and interaction details.

## iPad Landscape Layout

```
┌──────────────────────────────────────────────────────────────────────────────┐
│  Starters                                              [+ New Starter]      │
│  3 starters                                                                  │
│                                                                              │
│  ┌─────────────────────┐  ┌─────────────────────┐  ┌─────────────────────┐  │
│  │  🟢 Rye Baby        │  │  🟡 Old Faithful    │  │  🟢 Pumpernickel   │  │
│  │                      │  │                      │  │                      │
│  │  Fed 6 hours ago     │  │  Fed 3 days ago      │  │  Fed 10 hours ago   │  │
│  │  AP + Rye · 150g ea  │  │  Bread flour · 150g  │  │  Dark rye · 100g    │  │
│  │  Peaked at 4.5h      │  │  Last peak: 5.2h     │  │  Peaked at 6h       │  │
│  │                      │  │                      │  │                      │
│  │  ┌──────┐            │  │  ┌──────┐            │  │  ┌──────┐            │
│  │  │photo │            │  │  │photo │            │  │  │photo │            │
│  │  └──────┘            │  │  └──────┘            │  │  └──────┘            │
│  └─────────────────────┘  └─────────────────────┘  └─────────────────────┘  │
│                                                                              │
│  (scrolls if more starters)                                                  │
│                                                                              │
├────────────────┬────────────────┬──────────────────────────────────────────┤
│  Starter (●)   │      Bake      │     Log                                  │
└────────────────┴────────────────┴──────────────────────────────────────────┘
```

## Card Grid Layout

- **Landscape**: 3 columns
- **Portrait**: 2 columns
- Cards use the **Starter Card** shared component (see 07-shared-components.md)
- Grid scrolls vertically if more starters than fit on screen
- Cards are equal height within each row

## Card Content

Each card displays (via the Starter Card component):
1. **Health dot** — 🟢 Thriving (< 12h), 🟡 Needs Feeding (1-7 days), 🔴 Needs Revival (> 7 days)
2. **Starter name** — Fraunces serif, prominent
3. **Time since last feed** — "Fed 6 hours ago" or "Never fed" for new starters
4. **Last feeding flour summary** — "AP + Rye · 150g each"
5. **Last peak time** — "Peaked at 4.5h" (if recorded)
6. **Thumbnail photo** — from most recent feeding (placeholder if none)

## "+ New Starter" Button

- Top-right of the screen
- Navigates to **Create a Starter** form (13-create-starter.md)
- After creation, the new starter card appears in the grid

## Interactions

- **Tap a card** → push navigation to **Starter Details** (11-starter-details.md)
- **Long-press a card** → context menu:
  - "Delete Starter" (with confirmation alert: "Delete [name]? This will also delete all feeding history.")
- **Pull to refresh** — updates health indicators and time-since-feed
- **"+ New Starter"** → Create a Starter form

## Single Starter Optimization

When there's only one starter, the card takes full width (centered, max ~400px)
and the layout feels less like a grid and more like a focused detail preview.
