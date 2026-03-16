# Wireframe: Bread Log Tab

## iPad Landscape Layout - Grid View

```
┌──────────────────────────────────────────────────────────────────────────────┐
│  Bread Log                                              [+ New Entry] [⚙️]  │
│  12 bakes                                                                    │
│                                                                              │
│  ┌────────────┐  ┌────────────┐  ┌────────────┐  ┌────────────┐            │
│  │            │  │            │  │            │  │            │            │
│  │   [photo]  │  │   [photo]  │  │   [photo]  │  │   [photo]  │            │
│  │            │  │            │  │            │            │            │
│  │────────────│  │────────────│  │────────────│  │────────────│            │
│  │ Mar 15     │  │ Mar 10     │  │ Mar 5      │  │ Feb 28     │            │
│  │ No-Knead   │  │ 4-Fold     │  │ No-Knead   │  │ Tartine    │            │
│  │ ★★★★☆      │  │ 80/25      │  │ ★★★☆☆      │  │ ★★★★☆      │            │
│  │            │  │ ★★★★★      │  │            │  │            │            │
│  └────────────┘  └────────────┘  └────────────┘  └────────────┘            │
│                                                                              │
│  ┌────────────┐  ┌────────────┐  ┌────────────┐  ┌────────────┐            │
│  │            │  │            │  │            │  │            │            │
│  │   [photo]  │  │   [photo]  │  │   [photo]  │  │   [photo]  │            │
│  │            │  │            │  │            │  │            │            │
│  │────────────│  │────────────│  │────────────│  │────────────│            │
│  │ Feb 22     │  │ Feb 15     │  │ Feb 10     │  │ Feb 5      │            │
│  │ 4-Fold     │  │ No-Knead   │  │ 4-Fold     │  │ No-Knead   │            │
│  │ 75/25      │  │            │  │ 75/35      │  │            │            │
│  │ ★★★★★      │  │ ★★☆☆☆      │  │ ★★★★☆      │  │ ★★★☆☆      │            │
│  └────────────┘  └────────────┘  └────────────┘  └────────────┘            │
│                                                                              │
├────────────────┬────────────────┬────────────────────────────────────────────┤
│     Plan       │   Starter      │     Log                                    │
└────────────────┴────────────────┴────────────────────────────────────────────┘
```

## Bake Detail View (Tap on a bake card)

```
┌──────────────────────────────────────────────────────────────────────────────┐
│  [← Back]  March 15 Bake                             [Share ↗]  [Edit ✏️]   │
│                                                                              │
│  ┌─ LEFT: PHOTOS (50%) ────────────────┐  ┌─ RIGHT: DETAILS (50%) ────────┐ │
│  │                                      │  │                               │ │
│  │  ┌──────────────────────────────┐    │  │  No-Knead Pain au Levain     │ │
│  │  │                              │    │  │  March 15, 2026              │ │
│  │  │                              │    │  │                               │ │
│  │  │        [Main Photo]          │    │  │  RATING                      │ │
│  │  │                              │    │  │  Overall  ★★★★☆              │ │
│  │  │                              │    │  │  Crumb    ★★★★★              │ │
│  │  └──────────────────────────────┘    │  │  Crust    ★★★☆☆              │ │
│  │                                      │  │  Flavor   ★★★★☆              │ │
│  │  ┌──────┐ ┌──────┐ ┌──────┐         │  │  Rise     ★★★★☆              │ │
│  │  │thumb │ │thumb │ │thumb │         │  │                               │ │
│  │  │  1   │ │  2   │ │  3   │         │  │  FORMULA                     │ │
│  │  └──────┘ └──────┘ └──────┘         │  │  95% AP · 5% rye             │ │
│  │                                      │  │  74% hydration · 5% levain   │ │
│  │                                      │  │  Target: 900g                │ │
│  │                                      │  │                               │ │
│  │                                      │  │  NOTES                       │ │
│  │                                      │  │  "Best crumb yet! The long   │ │
│  │                                      │  │  cold proof really helped    │ │
│  │                                      │  │  with the open crumb         │ │
│  │                                      │  │  structure. Scored a bit     │ │
│  │                                      │  │  too shallow though."        │ │
│  │                                      │  │                               │ │
│  │                                      │  │  BAKE DETAILS                │ │
│  │                                      │  │  Oven: 475°F → 425°F        │ │
│  │                                      │  │  Covered: 20 min             │ │
│  │                                      │  │  Uncovered: 25 min           │ │
│  └──────────────────────────────────────┘  └───────────────────────────────┘ │
│                                                                              │
└──────────────────────────────────────────────────────────────────────────────┘
```

### Share Affordance

The Share button (↗) in the top-right of Bake Detail opens the iOS share sheet with:
- A composed summary: photo + formula name + rating + notes
- Shareable as image, text, or both
- Example share text:
  ```
  🍞 No-Knead Pain au Levain — ★★★★☆
  74% hydration · 5% levain · 900g
  "Best crumb yet! The long cold proof really helped."
  Baked with Fournil
  ```

## New Bake Entry Form (Sheet)

```
┌────────────────────────────────────────────────────────────────┐
│  Log a Bake                                   [Save]  [Cancel] │
│                                                                │
│  PHOTOS                                                        │
│  ┌──────┐ ┌──────┐ ┌──────┐ ┌──────────┐                      │
│  │      │ │      │ │      │ │  + Add   │                      │
│  │ 📷   │ │ 📷   │ │ 📷   │ │  Photo   │                      │
│  │      │ │      │ │      │ │          │                      │
│  └──────┘ └──────┘ └──────┘ └──────────┘                      │
│                                                                │
│  FORMULA                                                       │
│  [No-Knead PAL ▼]    Weight: [900] g                          │
│  Variant: [75/25 ▼]  (if Four-Fold)                           │
│                                                                │
│  RATING                                                        │
│  Overall:  ☆ ☆ ☆ ☆ ☆                                          │
│  Crumb:    ☆ ☆ ☆ ☆ ☆   (optional)                             │
│  Crust:    ☆ ☆ ☆ ☆ ☆   (optional)                             │
│  Flavor:   ☆ ☆ ☆ ☆ ☆   (optional)                             │
│  Rise:     ☆ ☆ ☆ ☆ ☆   (optional)                             │
│                                                                │
│  BAKE DETAILS                                                  │
│  Oven temp: [475] °F     Bake time: [45] min                  │
│                                                                │
│  NOTES                                                         │
│  ┌──────────────────────────────────────────────────────┐      │
│  │                                                      │      │
│  └──────────────────────────────────────────────────────┘      │
│                                                                │
│  CRUMB DESCRIPTION                                             │
│  ┌──────────────────────────────────────────────────────┐      │
│  │ Open, irregular holes with thin walls...             │      │
│  └──────────────────────────────────────────────────────┘      │
│                                                                │
└────────────────────────────────────────────────────────────────┘
```

## Component Details

### Bake Grid
- Scrollable grid of bake cards
- Each card: hero photo (or placeholder), date, formula name, variant (if 4-fold), star rating
- 4 columns in landscape, 3 in portrait
- Newest first
- Card background: `flourDust` surface

### Share Button
- Top-right of Bake Detail, alongside Edit
- Uses `ShareLink` (SwiftUI native)
- Composes: best photo + formula summary + rating + notes excerpt
- Standard iOS share sheet (Messages, Mail, Instagram, etc.)

### Bake Detail
- Two-column in landscape
- Left: photo gallery (main + thumbnails)
- Right: metadata, rating, formula, notes, bake details
- Back button returns to grid

### Entry Form
- Pre-populated from completed bake tracker (if coming from that flow)
- Formula dropdown includes variant (75/25, 80/35, etc.) for Four-Fold
- Required: date (auto-filled), overall rating
- Optional: everything else

### Interactions
- Coming from Bake Tracker completion: form auto-populates with formula, weight, captured media
- "+ New Entry" for manual logging
- Swipe to delete on grid cards (with confirmation)
- Edit button on detail view to modify entry
- Share button on detail view to share externally
