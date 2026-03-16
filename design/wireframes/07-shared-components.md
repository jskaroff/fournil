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

## Difficulty Indicator

Used in: Plan tab (Four-Fold variant picker)

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
- Maps to hydration level:
  - 75% = Beginner (●○○○)
  - 75% + high levain = Intermediate (●●○○)
  - 80% = Intermediate (●●○○)
  - 80% + high levain = Advanced (●●●○)
  - >80% (future custom formulas) = Expert (●●●●)

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
│  or levain. It serves two           │
│  purposes: easy mixing of flour     │
│  and liquids, and passive           │
│  development of gluten.             │
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

Used in: Bread Log (no bakes yet), Starter (no feedings yet)

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
