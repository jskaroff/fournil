# Wireframe: Bread Log Tab

## iPad Landscape Layout - Grid View

```
┌──────────────────────────────────────────────────────────────────────────────┐
│  Bread Log                                              [+ New Entry] [⚙️]  │
│  12 bakes                                                                    │
│                                                                              │
│  ┌─ FILTER BAR ────────────────────────────────────────────────────────────┐ │
│  │  Starter: [All Starters ▼]    Formula: [All Formulas ▼]                │ │
│  └─────────────────────────────────────────────────────────────────────────┘ │
│                                                                              │
│  ┌────────────┐  ┌────────────┐  ┌────────────┐  ┌────────────┐            │
│  │            │  │            │  │            │  │            │            │
│  │   [photo]  │  │   [photo]  │  │   [photo]  │  │   [photo]  │            │
│  │            │  │            │  │            │  │            │            │
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
│   Starter      │     Bake       │     Log (●)                                │
└────────────────┴────────────────┴────────────────────────────────────────────┘
```

## Filter Bar

```
┌─────────────────────────────────────────────────────────────┐
│  Starter: [All Starters ▼]    Formula: [All Formulas ▼]    │
└─────────────────────────────────────────────────────────────┘
```

- Two dropdown filters at top of the grid
- **Starter filter**: "All Starters" or pick a specific starter by name
- **Formula filter**: "All Formulas" or pick a specific formula (No-Knead, Four-Fold, etc.)
- Filters apply immediately; grid updates to show only matching bakes
- Active filter shows with `goldenCrust` accent; "All" is default/neutral
- Count updates to reflect filtered results (e.g., "4 bakes" when filtered)

---

## Bake Detail View (Tap on a bake card)

```
┌──────────────────────────────────────────────────────────────────────────────┐
│  [← Back]  March 15 Bake                    [Share ↗]  [Edit ✏️]            │
│                                                                              │
│  ┌─ LEFT: PHOTOS (50%) ────────────────┐  ┌─ RIGHT: DETAILS (50%) ────────┐ │
│  │                                      │  │                               │ │
│  │  ┌──────────────────────────────┐    │  │  No-Knead Pain au Levain     │ │
│  │  │                              │    │  │  March 15, 2026              │ │
│  │  │                              │    │  │  Starter: Rye Baby           │ │
│  │  │    ◀  [Main Photo]  ▶        │    │  │                               │ │
│  │  │                              │    │  │  RATING                      │ │
│  │  │                              │    │  │  Overall  ★★★★☆              │ │
│  │  └──────────────────────────────┘    │  │  Crumb    ★★★★★              │ │
│  │  ● ○ ○                               │  │  Crust    ★★★☆☆              │ │
│  │                                      │  │  Flavor   ★★★★☆              │ │
│  │  ┌──────┐ ┌──────┐ ┌──────┐ ┌─────┐ │  │  Rise     ★★★★☆              │ │
│  │  │thumb │ │thumb │ │thumb │ │ +📷 │ │  │                               │ │
│  │  │  1   │ │  2   │ │  3   │ │ Add │ │  │  FORMULA                     │ │
│  │  └──────┘ └──────┘ └──────┘ └─────┘ │  │  95% AP · 5% rye             │ │
│  │                                      │  │  74% hydration · 5% levain   │ │
│  │                                      │  │  Target: 900g                │ │
│  │                                      │  │                               │ │
│  │                                      │  │  NOTES                       │ │
│  │                                      │  │  "Best crumb yet! The long   │ │
│  │                                      │  │  cold proof really helped    │ │
│  │                                      │  │  with the open crumb."       │ │
│  │                                      │  │                               │ │
│  │                                      │  │  BAKE DETAILS                │ │
│  │                                      │  │  Oven: 475°F → 425°F        │ │
│  │                                      │  │  Covered: 20 min             │ │
│  │                                      │  │  Uncovered: 25 min           │ │
│  │                                      │  │                               │ │
│  │                                      │  │  ──────────────────────────  │ │
│  │                                      │  │                               │ │
│  │                                      │  │  [ 🔄 Bake this Again ]     │ │
│  │                                      │  │  [ 🍞 Share Your Bread ]    │ │
│  └──────────────────────────────────────┘  └───────────────────────────────┘ │
│                                                                              │
└──────────────────────────────────────────────────────────────────────────────┘
```

### Photo Carousel
- Horizontal scrollable carousel of all bake photos
- ◀ ▶ arrows for navigation, dot indicators below
- Thumbnail strip below the main photo
- **"+ Add Photo"** button at end of thumbnail strip to add more photos after the fact
- Uses `PhotosPicker` for adding photos

### Share Affordance
The Share button (↗) in the top-right opens the iOS share sheet with:
- A composed summary: photo + formula name + rating + notes
- Shareable as image, text, or both
- Example share text:
  ```
  🍞 No-Knead Pain au Levain — ★★★★☆
  74% hydration · 5% levain · 900g
  "Best crumb yet! The long cold proof really helped."
  Baked with Fournil
  ```

### Bake this Again
- Button at bottom of details pane
- On tap: navigates to the Bake tab with all values preset:
  - Formula pre-selected
  - Starter pre-selected (same starter used for this bake)
  - Dough weight preset
  - Variant preset (if Four-Fold)

### Share Your Bread
- CTA button below "Bake this Again"
- On tap: shows a "Coming soon" popover
- TODO: concept how to encourage bakers to share bread with friends, family, and community

### Edit Capabilities
- Edit button (✏️) in top bar enables inline editing of all metadata fields
- Ratings are tappable to change
- Notes and crumb description are editable text fields
- Bake details (temp, time) are editable

---

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
│  STARTER                                                       │
│  [Rye Baby ▼]                                                  │
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

---

## Component Details

### Bake Grid
- Scrollable grid of bake cards
- Each card: hero photo (or placeholder), date, formula name, variant (if 4-fold), star rating
- 4 columns in landscape, 3 in portrait
- Newest first (reverse chronological)
- Card background: `flourDust` surface
- Filter bar above grid narrows results

### Bake Detail
- Two-column in landscape
- Left: photo carousel (main + thumbnails + add photo)
- Right: metadata, rating, formula, starter, notes, bake details, action buttons
- Back button returns to grid

### Entry Form
- Pre-populated from completed bake tracker (if coming from that flow)
- Includes: Starter selector dropdown (which starter was used)
- Formula dropdown includes variant (75/25, 80/35, etc.) for Four-Fold
- Required: date (auto-filled), overall rating
- Optional: everything else

### Interactions
- Coming from Bake Tracker completion: form auto-populates with formula, starter, weight, captured media
- "+ New Entry" for manual logging
- Swipe to delete on grid cards (with confirmation)
- Edit button on detail view to modify entry
- Share button on detail view to share externally
- "Bake this Again" navigates to Bake tab with preset values
- Filter dropdowns update grid immediately
