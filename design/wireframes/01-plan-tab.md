# Wireframe: Plan Tab (Bake Screen)

This is the primary baking tab. It combines formula selection, starter selection, baker's math
calculation, DDT calculator, recipe instructions, timeline generation, and the entry point to
start a bake.

The right column is split into two side-by-side sub-panels: Ingredients and Timeline.
This matches the HTML prototype layout.

## iPad Landscape Layout

```
┌──────────────────────────────────────────────────────────────────────────────────────┐
│  Bake                                                                    [⚙️]       │
│                                                                                      │
│  ┌─ LEFT COL (380px) ─────────┐  ┌─ RIGHT: INGREDIENTS ──┐ ┌─ RIGHT: TIMELINE ────┐│
│  │  bg: parchment-warm        │  │                        │ │                       ││
│  │  border-right: flour-dust  │  │  Ingredients    ~870g  │ │  Timeline     ~23h    ││
│  │                            │  │                        │ │                       ││
│  │  FORMULA                   │  │  [74% hyd] [5% lev]   │ │  ● 6:00 AM  Mix      ││
│  │  ┌──────────────────────┐  │  │                        │ │  │          30 min    ││
│  │  │ 🍞 No-Knead PAL     │  │  │  INGREDIENT  %   GRAMS│ │  ○ 6:30 AM  Add Salt ││
│  │  │   ●○○○ Beginner      │  │  │  AP Flour   95%  456g │ │  │                    ││
│  │  │   22h · minimal      │  │  │  Rye Flour   5%   24g │ │  ○ 7:00 AM  Coil Fold││
│  │  │   View prev bakes →  │  │  │  Water      74%  355g │ │  │                    ││
│  │  └──────────────────────┘  │  │  Salt      2.2%   11g │ │  │  ┌── Bulk Proof ─┐││
│  │  ┌──────────────────────┐  │  │  Levain      5%   24g │ │  │  │ 12-16 hours   │││
│  │  │ 🌾 Four-Fold PAL    │  │  │  ─────────────────────│ │  │  └────────────────┘││
│  │  │   ●●○○ Intermediate  │  │  │  Total          ~870g │ │  │                    ││
│  │  │   16.5h · 4 folds    │  │  │                        │ │  🌙 tomorrow         ││
│  │  └──────────────────────┘  │  │                        │ │  ...                  ││
│  │  ┌ - + New Formula - - ┐  │  │                        │ │  ○ 7:00 PM  Preshape ││
│  │  └ - - - - - - - - - - ┘  │  │                        │ │  ○ 7:30 PM  Shape    ││
│  │                            │  │                        │ │  │                    ││
│  │  STARTER                   │  │                        │ │  │  ┌── Cold Proof ──┐││
│  │  ┌──────────────────────┐  │  │                        │ │  │  │ 8-24 hours    │││
│  │  │ 🟢 Rye Baby      ▼  │  │  │                        │ │  │  └────────────────┘││
│  │  │    Fed 6h ago        │  │  │                        │ │  │                    ││
│  │  └──────────────────────┘  │  │                        │ │  ● 4:00 AM  Bake!   ││
│  │                            │  │                        │ │                       ││
│  │  DOUGH WEIGHT              │  └────────────────────────┘ └───────────────────────┘│
│  │  [ − ]   900g   [ + ] [2×]│                                                      │
│  │                            │  ┌─ SCHEDULE + ACTIONS ─────────────────────────────┐│
│  │  HYDRATION / LEVAIN        │  │                                                   ││
│  │  ○──●──── ○──●────         │  │  WHEN  [● Start Now]  [Start At]  [Finish By]    ││
│  │  74% Fixed  5% Fixed       │  │                                                   ││
│  │                            │  │  Starting now, bread ready ~4:40 AM tomorrow      ││
│  │  WATER TEMPERATURE         │  │                                                   ││
│  │  Flour   Room    Levain    │  │  [ 📌 Save ]                  [ Start Bake ▶ ]   ││
│  │  [68°F] [72°F]  [40°F]    │  └───────────────────────────────────────────────────┘│
│  │                            │                                                      │
│  │     Use water at 127°F     │                                                      │
│  │  DDT of 78°F · Hand [✎]    │                                                      │
│  └────────────────────────────┘                                                      │
│                                                                                      │
├────────────────┬────────────────┬────────────────────────────────────────────────────┤
│    Starter     │   Bake (●)     │     Log                                            │
└────────────────┴────────────────┴────────────────────────────────────────────────────┘
```

### Key Layout Notes (from prototype)
- Left column is a fixed 380px scrollable sidebar with parchment-warm background
- Right area splits into **two sub-panels** side by side: Ingredients (left) and Timeline (right)
  - Each sub-panel scrolls independently
  - Separated by a thin flour-dust border
- Schedule/actions bar sits below the two sub-panels at the bottom

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

---

### Starter Selector

Positioned between Formula Selector and Dough Weight. Compact card/dropdown:

```
┌────────────────────────────────────────────────────────┐
│  🟢 Rye Baby                                     ▼    │
│     Fed 6 hours ago                                    │
└────────────────────────────────────────────────────────┘
```

- Shows selected starter name with health indicator dot (🟢/🟡/🔴)
- Shows time since last feeding
- Dropdown chevron (▼) — tap to pick from list of all starters
- Defaults to first starter in list, or last-used starter if a completed bake exists
- If no starters exist, shows "No starter — add one in the Starter tab" with link

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

### Formula Controls (Hydration / Levain)

Controls for Hydration % and Levain %. Three interchangeable display styles
(toggle in top-right: Arc / Slider / Steps):

**Arc Style (default):**
```
     Hydration              Levain
      ╭─────╮               ╭─────╮
     │  74% │              │   5% │
      ╰─────╯               ╰─────╯
       Fixed                  Fixed
```
- Circular arc knob with golden-crust fill
- Value displayed in center (Fira Mono, 20px)
- Read-only formulas show at 50% opacity

**Slider Style:**
```
  Hydration              Levain
  74%                    5%
  ───────●───────────    ────●──────────────
  Fixed                  Fixed
```
- Horizontal slider with golden-crust fill and thumb
- Tick marks at preset snap points

**Stepper Style:**
```
  Hydration              Levain
  74%                    5%
  [75%] [80%]           [25%] [35%]
    [ − ] [ + ]           [ − ] [ + ]
```
- Preset buttons with golden-crust active state
- Fine-tune +/− round buttons below

- **Interactive** (with snap points to presets) only for Four-Fold PAL
- **Read-only** (dimmed, no interaction) for all other formulas
- Preset snap points for Four-Fold: Hydration 75%/80%, Levain 25%/35%

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
    │                               │
    │  Desired Dough Temperature    │
    │  Target DDT        78°F       │
    │                               │
    │  Mixing Method                │
    │  [● Hand] [Mixer] [Processor] │
    └───────────────────────────────┘
    ```
- "Desired Dough Temperature" label clarifies the DDT acronym
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

### Recipe Instructions

Displayed below the ingredients table within the Ingredients sub-panel:

```
  Recipe Instructions
  ┌──────────────────────────────────────────────────────┐
  │  1. Combine water and levain in a large mixing       │
  │     bowl. Stir to dissolve the levain.               │
  │                                                      │
  │  2. Add the AP flour and rye flour. Mix until        │
  │     no dry flour remains. Cover and rest             │
  │     (autolyse) for 30 minutes.                       │
  │                                                      │
  │  3. Sprinkle salt over dough. Dimple in and          │
  │     fold to incorporate. ...                         │
  └──────────────────────────────────────────────────────┘
```

- Positioned within the Ingredients sub-panel (scrolls with it)
- Shows numbered step-by-step instructions from the Formula's `instructions` field
- Read-only display (instructions are part of the formula, not user-editable for built-ins)

### Timeline Panel

Vertical step-by-step timeline with day boundary markers and proof blocks.
The timeline line uses a gradient: golden-crust at top → flour-dust-deep middle → sage at bottom (bake step).

```
  Timeline                                    ~23 hours

  ● 6:00 AM   Mix              30 min
  │
  ○ 6:30 AM   Add Salt         30 min
  │
  ○ 7:00 AM   Coil Fold
  │
  │  ┌── Bulk Proof ──────────────────┐
  │  │ 12-16 hours                     │
  │  └────────────────────────────────┘
  │  until ~7:25 PM today
  │
  🌙 tomorrow
  ○ 7:00 PM   Preshape         30 min
  ○ 7:30 PM   Final Shape      30 min
  │
  │  ┌── Cold Proof ──────────────────┐
  │  │ 8-24 hours                      │
  │  └────────────────────────────────┘
  │
  ● 4:00 AM   Bake!            40 min
```

#### Step Dots
- **First step**: golden-crust filled, golden glow
- **Regular steps**: open circle, flour-dust-deep border
- **Bake step** (final): sage filled, sage glow

#### Step Duration Badges
- Short durations (≤30 min): sage-bg background, sage text
- Long durations (hours): golden-glow background, golden-crust text
- Overnight: clay-bg background, clay text

#### Proof Blocks
Interchangeable display styles (toggle: Gradient / Thick / Hatched / Bracket):

- **Gradient (default)**: Rounded card with gradient background and left border
  - Bulk: golden-glow gradient, golden-crust-light left border
  - Cold: night-bg gradient, night-blue left border
- **Thick**: Thick vertical line alongside label text
- **Hatched**: Diagonal repeating lines (45°), same card shape
  - Bulk: golden-crust hatching
  - Cold: night-blue hatching
- **Bracket**: Top/bottom horizontal bracket lines with label between

Each proof block shows: label ("Bulk Proof" / "Cold Proof") + duration badge.
Finish hint in italic below: "until ~7:25 PM today".

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

**Notification prompt:** After tapping "Start Bake" with a future Start At or
Finish By time, prompt user to enable a system notification before the
scheduled start time. Lead time is configurable in Settings (default 5 min).

---

## iPad Portrait Layout

Same content, single-column stack (sub-panels collapse to stacked):
1. Formula Selector (horizontal scroll)
2. Starter Selector
3. Dough Weight + Doubler
4. Formula Controls (Hydration / Levain)
5. Water Temperature (DDT)
6. Ingredients Table + Recipe Instructions
7. Timeline
8. When + Action Buttons

---

## Interactions

- Selecting a formula updates ingredients, instructions, timeline, and DDT defaults instantly
- Selecting Four-Fold unlocks hydration and levain sliders with preset snap points
- Changing dough weight rescales all ingredient quantities (timeline unchanged)
- Toggling 2× doubles all ingredient quantities; pill badge appears in Ingredients
- Changing starter updates the association for the planned bake
- "Start now" auto-updates time hint; "Start At" / "Finish By" show time inputs
- DDT reference row tap opens popover; click-outside closes
- "+" New Formula tap shows "Coming soon" popover; click-outside closes
- `@AppStorage`: last formula, last starter, weight, temp unit
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
