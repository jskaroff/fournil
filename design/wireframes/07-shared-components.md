# Wireframe: Shared Components

## Weight Input Field

Used in: Plan tab, Bake Entry Form, Preferences

```
STEPPER VARIANT (primary)
┌─────────────────────────────────────┐
│  [ - ]      900g        [ + ]      │
│                                     │
│  ○──────────────●──────────────○    │
│  200g                      3000g    │
└─────────────────────────────────────┘

SIMPLE VARIANT (forms)
┌─────────────────────────────────────┐
│  Weight    [  900  ] g              │
└─────────────────────────────────────┘
```

- Stepper increments: 50g
- Slider for quick adjustment
- Clamped: 200g minimum, 3000g maximum
- Large numeric display with `numericText()` content transition
- Accessible: stepper labels, VoiceOver announces grams

---

## Temperature Input Field

Used in: Plan tab (DDT), Starter (feeding form)

```
WITH UNIT TOGGLE
┌─────────────────────────────────────┐
│  Flour temp    [  68  ]  °F  °C    │
└─────────────────────────────────────┘

SIMPLE
┌─────────────────────────────────────┐
│  Room temp     [  72  ] °F         │
└─────────────────────────────────────┘
```

- Numeric keyboard input
- °F/°C toggle (global setting via `@AppStorage` in Preferences)
- Conversion happens in the model, display adapts
- Valid range: 32°F - 212°F (0°C - 100°C)

---

## Section Header

Used in: All screens

```
┌─────────────────────────────────────┐
│  FORMULA                            │  ← Serif, small caps, wheatField color
│─────────────────────────────────────│     with thin separator line
```

- Serif font, small caps style
- `wheatField` secondary text color
- Optional thin separator line below
- Consistent spacing: 24pt above, 12pt below

---

## Formula Selection Card

Used in: Plan tab

```
UNSELECTED                           SELECTED
┌──────────────┐                    ┌──────────────┐
│              │                    │ ┌──────────┐ │
│  No-Knead    │                    │ │ No-Knead │ │
│  PAL         │                    │ │ PAL      │ │
│              │                    │ │    ●     │ │
│  ~22h        │                    │ │ ~22h     │ │
│  minimal     │                    │ └──────────┘ │
│  handling    │                    │  goldenCrust  │
│              │                    │  border       │
└──────────────┘                    └──────────────┘
  flourDust bg                        slight scale-up
  wheatField text                     spring animation
```

- Tappable card
- Shows: formula name, brief descriptor, estimated time
- Selected: `goldenCrust` border, slight scale-up (1.02x), spring animation
- Unselected: `flourDust` background, `wheatField` text
- Selection indicator dot

---

## Starter Card

Used in: Starter tab (non-empty state)

```
┌─────────────────────────────────────┐
│  🟢 Rye Baby                       │
│                                     │
│  Fed 6 hours ago                    │
│  AP + Rye · 150g each              │
│  Peaked at 4.5h                     │
│                                     │
│  ┌──────────┐                       │
│  │  [photo] │                       │
│  └──────────┘                       │
└─────────────────────────────────────┘
```

- Health indicator dot (🟢/🟡/🔴) next to starter name
- Name in Fraunces serif
- Time since last feeding (relative)
- Last feeding summary (flour types, amounts)
- Last peak time (if recorded)
- Thumbnail photo from most recent feeding (if available, otherwise placeholder)
- Tap navigates to Starter Details
- Long-press for context menu (Delete)
- Card background: `flourDust` surface

---

## Starter Selector

Used in: Plan tab, Bake Entry Form

```
COMPACT (Plan tab left column)
┌─────────────────────────────────────┐
│  🟢 Rye Baby                   ▼   │
│     Fed 6 hours ago                 │
└─────────────────────────────────────┘

DROPDOWN (Bake Entry Form)
┌─────────────────────────────────────┐
│  Starter    [Rye Baby ▼]           │
└─────────────────────────────────────┘
```

- Compact variant: shows health dot, name, and time since last feed
- Dropdown variant: simple picker for forms
- Tap opens a list of all starters to pick from
- "No starters yet" state shows link to Starter tab

---

## Filter Bar

Used in: Bread Log tab

```
┌─────────────────────────────────────────────────┐
│  Starter: [All Starters ▼]  Formula: [All ▼]   │
└─────────────────────────────────────────────────┘
```

- Horizontal row of dropdown filters
- Each filter defaults to "All" (no filter active)
- Active filter uses `goldenCrust` accent
- Filters apply immediately to the content below
- Content count updates to reflect filtered results

---

## Photo Carousel

Used in: Bake Detail, Starter Details

```
┌──────────────────────────────────────────────┐
│                                              │
│         ◀  [Current Photo]  ▶                │
│                                              │
└──────────────────────────────────────────────┘
● ○ ○ ○

┌──────┐ ┌──────┐ ┌──────┐ ┌──────────┐
│thumb │ │thumb │ │thumb │ │  + Add   │
│  1   │ │  2   │ │  3   │ │  Photo   │
└──────┘ └──────┘ └──────┘ └──────────┘
```

- Horizontal scrollable main photo with swipe/arrow navigation
- Dot indicator for current position
- Thumbnail strip below (scrollable if many photos)
- "+ Add Photo" button at end of thumbnail strip
- Uses `PhotosPicker` for adding photos
- Empty state: single placeholder with "+ Add Photo"

---

## Flour Entry Row

Used in: Log a Feed form

```
SINGLE ROW
┌─────────────────────────────────────────────────┐
│  [AP Flour ▼]    [  150  ] g          [✕]       │
└─────────────────────────────────────────────────┘

MULTIPLE ROWS
┌─────────────────────────────────────────────────┐
│  [AP Flour ▼]    [  125  ] g          [✕]       │
│  [Rye ▼]         [   25  ] g          [✕]       │
│  [ + Add Flour ]                                │
└─────────────────────────────────────────────────┘
```

- Flour type dropdown: AP, Bread, Rye, Whole Wheat, Other (free-text)
- Weight in grams input
- ✕ button to remove a flour row (disabled if only one row)
- "+ Add Flour" button to add another row
- Used in the feeding form for multi-flour feeds

---

## Difficulty Indicator

Used in: Plan tab (formula cards, Four-Fold variant picker)

```
●○○○  Beginner       risingGreen
●●○○  Intermediate   goldenCrust
●●●○  Advanced       overProofAmber
●●●●  Expert         burnedRed
```

Full component:
```
┌─────────────────────────────────────────────┐
│  Difficulty: ●●○○  Intermediate             │
│  "Some experience with wet doughs helpful"  │
└─────────────────────────────────────────────┘
```

- 4 dots, filled to indicate level
- Color matches difficulty: green → gold → amber → red
- One-line description below
- Animated transition when difficulty changes

---

## Variant Grid (Four-Fold Specific)

Used in: Plan tab (when Four-Fold PAL selected)

```
┌─────────────────────────────────────────────┐
│           │  25% levain  │  35% levain      │
│───────────┼──────────────┼─────────────────│
│  75%      │  [● 75/25]  │  [  75/35  ]    │
│  hydration│   Beginner   │  Intermediate   │
│───────────┼──────────────┼─────────────────│
│  80%      │  [  80/25]  │  [  80/35  ]    │
│  hydration│ Intermediate │    Advanced     │
└─────────────────────────────────────────────┘
```

- 2×2 grid of tappable cells
- Selected cell: `goldenCrust` border + filled background
- Each cell shows: ratio shorthand, difficulty label
- Selecting a cell updates ingredients to pre-calculated values
- Temperature guidance below: "25% levain for normal temps, 35% for cold kitchen, 12.5% for warm"

---

## Star Rating

Used in: Bread Log (entry form, detail view, grid card)

```
INTERACTIVE (entry form)
★ ★ ★ ★ ☆    ← tap to set rating
  goldenCrust filled, flourDust empty

DISPLAY (detail/card)
★★★★☆  4/5
```

- 1-5 stars
- Tappable in forms, display-only in detail views
- Filled star: `goldenCrust`
- Empty star: `flourDust` with `wheatField` border
- Tap a star to set that rating; tap same star to clear

---

## Expandable Card (Glossary / Tips)

Used in: Settings > Inspiration (glossary), Tracker (proofing tips)

```
COLLAPSED
┌─────────────────────────────────────┐
│  ▶  Autolyse                        │
└─────────────────────────────────────┘

EXPANDED
┌─────────────────────────────────────┐
│  ▼  Autolyse                        │
│                                     │
│  A 15-60 minute rest at the start   │
│  of mixing prior to the addition    │
│  of salt and sometimes the yeast    │
│  or levain...                       │
└─────────────────────────────────────┘
```

- Chevron rotates 90° on expand (spring animation)
- Card background: `flourDust`
- Title: serif font, `crustBrown`
- Body: sans font, `wheatField`
- Smooth height animation on expand/collapse

---

## Progress Indicator (Timeline Dot)

Used in: Plan tab (timeline), Tracker (step progress)

```
COMPLETED    CURRENT      UPCOMING
   ✓            ●            ○
 risingGreen  goldenCrust   wheatField
   │            │            │
   │            │            │
   (thin line connects dots vertically)
```

- Dots connected by thin vertical line
- Completed: checkmark, `risingGreen`
- Current: filled circle, `goldenCrust`, slightly larger
- Upcoming: open circle, `wheatField` border only

---

## Empty State

Used in: Bread Log (no bakes yet), Starter (simple variant)

```
┌─────────────────────────────────────┐
│                                     │
│         🍞                          │
│                                     │
│    No bakes yet                     │
│                                     │
│    Start your first bake from       │
│    the Plan tab, or log a           │
│    past bake here.                  │
│                                     │
│    [+ Log a Bake]                   │
│                                     │
└─────────────────────────────────────┘
```

- Centered content
- SF Symbol icon
- Brief helpful message
- CTA button to get started

Note: The Starter tab has its own specialized empty state with 3 onboarding buttons
(see 09-starter-empty-state.md), not this generic component.
