# Wireframe: Plan Tab (Bake Screen)

This is the primary tab. It combines formula selection, baker's math calculation,
DDT calculator, timeline generation, and the entry point to start a bake.

## iPad Landscape Layout

```
┌──────────────────────────────────────────────────────────────────────────────┐
│  Bake                                                          [⚙️]         │
│                                                                              │
│  ┌─ LEFT COLUMN (40%) ──────────────────┐  ┌─ RIGHT COLUMN (60%) ──────────┐ │
│  │                                      │  │                                │ │
│  │  FORMULA                             │  │  ┌─ Ingredients ──────────────┐│ │
│  │  ┌────────────────────────────────┐  │  │  │ 74% hydration  5% levain  ││ │
│  │  │ 🍞 No-Knead Pain au Levain  ●○○○│  │  │                            ││ │
│  │  │ Beginner · 22h · minimal handling│  │  │ INGREDIENT   BAKER'S%  GRAMS││ │
│  │  │ A hands-off loaf with a crispy  │  │  │ AP Flour        95%    456g ││ │
│  │  │ crust and mild, tangy crumb.    │  │  │ Rye Flour        5%     24g ││ │
│  │  │ View previous bakes →           │  │  │ Water           74%    355g ││ │
│  │  └────────────────────────────────┘  │  │ Salt            2.2%    11g ││ │
│  │  ┌────────────────────────────────┐  │  │ Levain           5%     24g ││ │
│  │  │ 🌾 Four-Fold Pain au Levain ●●○○│  │  │ ─────────────────────────  ││ │
│  │  │ Intermediate · 16.5h · structure │  │  │ Total                 ~870g ││ │
│  │  │ ...                             │  │  └────────────────────────────┘│ │
│  │  └────────────────────────────────┘  │  │                                │ │
│  │  ┌ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ┐  │  │  ┌─ Timeline ─────────────────┐│ │
│  │    + New Formula                    │  │  │                            ││ │
│  │  └ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ┘  │  │  │  ● 6:00 AM  Mix (autolyse)││ │
│  │                                      │  │  │  │          30 min        ││ │
│  │  DOUGH WEIGHT                        │  │  │  ○ 6:30 AM  Add Salt      ││ │
│  │  [ − ]    900g    [ + ]       [2×]   │  │  │  │                        ││ │
│  │                                      │  │  │  ○ 7:00 AM  Bulk Proof    ││ │
│  │  FORMULA (Hydration / Levain)        │  │  │  │  ╔════════════════════╗ ││ │
│  │  Hydration              Levain       │  │  │  │  ║ ▓▓▓▓▓ Bulk ▓▓▓▓▓  ║ ││ │
│  │  74%                    5%           │  │  │  │  ║ 12-16 hours        ║ ││ │
│  │  ○────●──────────────── ○────●────── │  │  │  ╚════════════════════╝ ││ │
│  │  Fixed        Fixed                  │  │  │  ...                      ││ │
│  │                                      │  │  └────────────────────────────┘│ │
│  │  WATER TEMPERATURE                   │  │                                │ │
│  │  Flour    Room     Levain            │  │  ─────────────────────────────  │ │
│  │  [ 68°F ] [ 72°F ] [ 40°F ]         │  │                                │ │
│  │                                      │  │  WHEN                          │ │
│  │       Use water at                   │  │  [● Start Now] [Start At] [Finish By]│ │
│  │           127°F                      │  │                                │ │
│  │                                      │  │  Starting now, bread ready ~   │ │
│  │  DDT of 78°F · Hand mixing  [✎]      │  │  4:40 AM tomorrow              │ │
│  │                                      │  │                                │ │
│  └──────────────────────────────────────┘  │  [ 📌 Save ]  [ Start Bake ▶ ]│ │
│                                            └────────────────────────────────┘ │
│                                                                              │
├────────────────┬────────────────┬──────────────────────────────────────────┤
│    Starter     │   Bake (●)     │     Log                                  │
└────────────────┴────────────────┴──────────────────────────────────────────┘
```

---

## Left Column Detail

### Formula Selector (Vertical Carousel)

A scrollable vertical carousel with `scroll-snap-type: y mandatory`. Max height ~230px
(shows ~2 cards at a time). Cards are full-width with:

```
┌────────────────────────────────────────────────────────┐
│  [🍞]  No-Knead Pain au Levain           ●○○○ Beginner │
│        22h · minimal handling                          │
│        A hands-off loaf with a crispy crust and mild,  │
│        tangy crumb.                                    │
│        View previous bakes →                           │
└────────────────────────────────────────────────────────┘
```

Card fields:
- Emoji icon (48×48px thumbnail)
- Long formula name (Fraunces serif)
- Difficulty dots (●○○○ = Beginner, ●●○○ = Intermediate, ●●●○ = Advanced, ●●●● = Expert)
- Timing + technique (one-liner meta)
- 1-sentence description (clamped to 2 lines)
- "View previous bakes →" log link

**"+" Add Formula button** — dashed-border card at bottom of carousel:
```
┌ - - - - - - - - - - - - - - - - - - - - ┐
   + New Formula
└ - - - - - - - - - - - - - - - - - - - - ┘
```
Tapping shows a "Coming soon" popover. Future: launches Formula Builder/Editor.
TODO: Wire to Formula Builder when implemented.

---

### Dough Weight

```
   [ − ]     900g     [ + ]                         [2×]
```

- `−` and `+` are rounded square buttons (38×38px)
- Weight display is large Fraunces number
- **2× Doubler** is a rectangular pill badge at the far right — visually distinct from
  the square +/− controls. Inactive: outlined. Active: filled golden, all quantities doubled.

---

### Formula Sliders (Hydration / Levain)

Two horizontal sliders showing current Hydration % and Levain %:

```
  Hydration              Levain
  74%                    5%
  ───────●───────────    ────●──────────────
  Fixed                  Fixed
```

- **Interactive** (with snap points to presets) only for Four-Fold PAL
- **Read-only** ("Fixed" label) for all other formulas
- Preset snap points for Four-Fold: Hydration 75%/80%, Levain 25%/35%

TODO: Improve visual richness — custom thumb style, gradient fill, better tick marks.

---

### Water Temperature (DDT Calculator — always visible)

```
  Flour      Room       Levain
  [ 68 °F ]  [ 72 °F ]  [ 40 °F ]

       Use water at
           127°F

  DDT of 78°F · Hand mixing  [✎]
```

- Three inline inputs with °F suffix inside each field
- Large result display (Fira Mono, 32px)
- Reference row: "DDT of 78°F · [method]" with pencil/edit icon
  → Tapping opens an iPad-style fixed-position popover:
    ```
    ┌───────────────────────────────┐
    │  DDT Settings                 │
    │  Target DDT        78°F       │
    │                               │
    │  Mixing Method                │
    │  [● Hand] [Mixer] [Processor] │
    └───────────────────────────────┘
    ```
- Friction factors: Hand = 5, Mixer = 25, Processor = 30
- DDT formula: waterTemp = 4×78 − flour − room − levain − frictionFactor

---

## Right Column Detail

### Ingredients Panel

```
  Ingredients
  ┌──────────────────────────────────────────────────────┐
  │  [74% hydration]  [5% levain]  [2× Doubled]         │
  │                                                      │
  │  INGREDIENT        BAKER'S %        GRAMS            │
  │  AP Flour             95%            456g            │
  │  Rye Flour             5%             24g            │
  │  Water                74%            355g            │
  │  Salt                2.2%             11g            │
  │  Levain                5%             24g            │
  │  ────────────────────────────────────────────        │
  │  Total                                ~870g          │
  └──────────────────────────────────────────────────────┘
```

- Pills row: hydration %, levain %, and "2× Doubled" badge (red) when doubler is on
- Total row is inside the same `<table>` as ingredients (via `<tfoot>`) so it
  aligns perfectly with the Grams column

### Timeline Panel

Vertical step-by-step timeline with day boundary markers and proof blocks:

```
  Timeline                                    ~23 hours

  ● 6:00 AM   Mix
  │            Combine water, levain, flours.
  ○ 6:30 AM   Add Salt
  │            Add reserved water + salt.
  ○ 7:00 AM   Coil Fold
  │
  │  ╔══════════════════════════════╗
  │  ║ ▓▓▓▓ Bulk Proof ▓▓▓▓▓▓▓▓▓  ║  12-16 hours
  │  ╚══════════════════════════════╝
  │  until ~7:25 PM today
  │
  🌙 tomorrow
  ...
  ● 4:40 AM   Bake
               Bread ready ~4:40 AM tomorrow
```

Proof block style: **hatched** (diagonal fill, default). TODO: refine visual treatment.

---

## Bottom Bar

```
  WHEN  [ Start Now ]  [ Start At ]  [ Finish By ]

  Starting now, bread ready ~4:40 AM tomorrow

  [ 📌 Save ]                    [ Start Bake ▶ ]
```

- **Start Now**: uses current time, updates hint in real-time
- **Start At**: reveals time picker, calculates finish
- **Finish By**: reveals time picker, reverse-calculates start time

**Notification prompt (future):** After tapping "Start Bake" with a future Start At or
Finish By time, prompt user to enable a system notification 5 minutes before the
scheduled start time. Lead time is configurable in Settings.

---

## iPad Portrait Layout

Same content, single-column stack:
1. Formula Selector
2. Dough Weight + Doubler
3. Formula Sliders
4. Water Temperature
5. Ingredients Table
6. Timeline
7. When + Action Buttons

---

## Interactions

- Selecting a formula updates ingredients, timeline, and DDT defaults instantly
- Selecting Four-Fold unlocks hydration and levain sliders with preset snap points
- Changing dough weight rescales all ingredient quantities (timeline unchanged)
- Toggling 2× doubles all ingredient quantities; pill badge appears in Ingredients
- "Start now" auto-updates time hint; "Start At" / "Finish By" show time inputs
- DDT reference row tap opens popover; click-outside closes
- "+" New Formula tap shows "Coming soon" popover; click-outside closes
- `@AppStorage`: last formula, weight, temp unit
- "Save" stores named plan snapshots

---

## Difficulty Indicator

```
●○○○  Beginner       "Forgiving dough, easy to shape"
●●○○  Intermediate   "Some experience with wet doughs helpful"
●●●○  Advanced       "Sticky dough, requires confident shaping"
●●●●  Expert         "Very wet, challenging — for experienced bakers"
```

Colors: `risingGreen` (beginner), `goldenCrust` (intermediate), `overProofAmber` (advanced), `burnedRed` (expert)

---

## Four-Fold Preset Values (from Janjigian pp. 12-13)

| Variant | Hydration | Levain | Water | AP Flour | Rye | Levain (g) | Salt | Difficulty |
|---------|-----------|--------|-------|----------|-----|------------|------|------------|
| 75/25 | 75% | 25% | 315g | 420g | 25g | 130g | 11g | Beginner |
| 75/35 | 75% | 35% | 290g | 395g | 25g | 180g | 11g | Intermediate |
| 80/25 | 80% | 25% | 330g | 405g | 25g | 125g | 11g | Intermediate |
| 80/35 | 80% | 35% | 310g | 380g | 25g | 175g | 11g | Advanced |

Sliders snap to these preset values. Fine-tuning between presets is allowed.
