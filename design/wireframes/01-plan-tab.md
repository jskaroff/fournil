# Wireframe: Plan Tab (Calculator + Planner Merged)

This is the primary tab. It combines formula selection, baker's math calculation,
DDT calculator, timeline generation, and the entry point to start a bake.

## iPad Landscape Layout

```
┌──────────────────────────────────────────────────────────────────────────────┐
│  Plan                                                          [⚙️]         │
│                                                                              │
│  ┌─ LEFT COLUMN (40%) ──────────────────┐  ┌─ RIGHT COLUMN (60%) ─────────┐ │
│  │                                      │  │                               │ │
│  │  FORMULA                             │  │  ┌─ SEGMENT: Ingredients | Timeline | DDT ─┐ │
│  │  ┌──────────┐ ┌──────────┐           │  │                               │ │
│  │  │ No-Knead │ │Four-Fold │           │  │  ═══ INGREDIENTS VIEW ═══     │ │
│  │  │  PAL     │ │  PAL     │           │  │                               │ │
│  │  │  ●       │ │          │           │  │  ┌───────────────────────────┐│ │
│  │  └──────────┘ └──────────┘           │  │  │ AP Flour      95%   456g ││ │
│  │  ┌──────────┐                        │  │  ├───────────────────────────┤│ │
│  │  │ Tartine  │                        │  │  │ Rye Flour      5%    24g ││ │
│  │  │ Country  │                        │  │  ├───────────────────────────┤│ │
│  │  └──────────┘                        │  │  │ Water         74%   355g ││ │
│  │                                      │  │  ├───────────────────────────┤│ │
│  │  ─── FOUR-FOLD VARIANT ──────        │  │  │ Salt          2.2%   11g ││ │
│  │  (only visible when Four-Fold        │  │  ├───────────────────────────┤│ │
│  │   is selected)                       │  │  │ Levain         5%    24g ││ │
│  │                                      │  │  └───────────────────────────┘│ │
│  │  Hydration       Levain              │  │                               │ │
│  │  ┌──────┐        ┌──────┐            │  │  Hydration: 74%              │ │
│  │  │ 75%  │        │ 25%  │            │  │  Total: ~870g                │ │
│  │  │      │        │      │            │  │                               │ │
│  │  └──────┘        └──────┘            │  │  ═══ TIMELINE VIEW ═══       │ │
│  │  ┌──────┐        ┌──────┐            │  │  (shown when Timeline        │ │
│  │  │ 80%  │        │ 35%  │            │  │   segment selected)          │ │
│  │  │      │        │      │            │  │                               │ │
│  │  └──────┘        └──────┘            │  │  ═══ DDT VIEW ═══            │ │
│  │  ⚠️ Difficulty: ●●●○ Advanced       │  │  (shown when DDT             │ │
│  │  "80% hydration is stickier and     │  │   segment selected)          │ │
│  │   harder to shape"                   │  │                               │ │
│  │                                      │  │                               │ │
│  │  DOUGH WEIGHT                        │  │  ─────────────────────────── │ │
│  │  [ - ]    900g     [ + ]             │  │                               │ │
│  │                                      │  │  WHEN                         │ │
│  │  LEVAIN % (No-Knead only)            │  │  ◉ Start now (6:00 AM)       │ │
│  │  ○ 1% ────●──────────── 10%         │  │  ○ Bake by: [picker]         │ │
│  │                                      │  │                               │ │
│  │                                      │  │  ┌──────────────────────────┐│ │
│  │  ┌────────────────────────────────┐  │  │  │  [ Save for Later 📌 ]  ││ │
│  │  │                                │  │  │  │  [ Start Bake ▶ ]       ││ │
│  │  │                                │  │  │  └──────────────────────────┘│ │
│  │  └────────────────────────────────┘  │  │                               │ │
│  └──────────────────────────────────────┘  └───────────────────────────────┘ │
│                                                                              │
├────────────────┬────────────────┬────────────────────────────────────────────┤
│     Plan       │   Starter      │     Log                                    │
└────────────────┴────────────────┴────────────────────────────────────────────┘
```

## Four-Fold Variant Picker (Detail)

When "Four-Fold PAL" is selected, a variant grid appears with hydration × levain combinations:

```
  FOUR-FOLD VARIANT

  Select hydration and levain:

  ┌─────────────────────────────────────────────┐
  │           │  25% levain  │  35% levain      │
  │───────────┼──────────────┼─────────────────│
  │  75%      │  ● 75/25    │    75/35         │
  │  hydration│  Beginner    │    Intermediate  │
  │           │  ●○○○        │    ●●○○          │
  │───────────┼──────────────┼─────────────────│
  │  80%      │    80/25     │    80/35         │
  │  hydration│  Intermediate│    Advanced      │
  │           │  ●●○○        │    ●●●○          │
  └─────────────────────────────────────────────┘

  DIFFICULTY: ●○○○ Beginner
  "75% hydration with 25% levain. A great starting
  point — forgiving dough, easy to shape."

  ─────────────────────────────────────────────

  Lower levain (12.5%) → warm kitchen
  Higher levain (35%) → cold kitchen
  Lower hydration (75%) → easier to shape
  Higher hydration (80%) → more open crumb, stickier
```

### Four-Fold Pre-Calculated Variants (from Janjigian pp. 12-13)

| Variant | Hydration | Levain | Water | AP Flour | Rye | Levain (g) | Salt | Difficulty |
|---------|-----------|--------|-------|----------|-----|------------|------|------------|
| 75/25 | 75% | 25% | 315g | 420g | 25g | 130g | 11g | Beginner |
| 75/35 | 75% | 35% | 290g | 395g | 25g | 180g | 11g | Intermediate |
| 80/25 | 80% | 25% | 330g | 405g | 25g | 125g | 11g | Intermediate |
| 80/35 | 80% | 35% | 310g | 380g | 25g | 175g | 11g | Advanced |

Note: Janjigian also mentions 12.5% levain for very warm kitchens. We can support this via the levain slider as a manual override beyond the grid presets.

### Difficulty Indicator

```
●○○○  Beginner       "Forgiving dough, easy to shape"
●●○○  Intermediate   "Some experience with wet doughs helpful"
●●●○  Advanced       "Sticky dough, requires confident shaping"
●●●●  Expert         "Very wet, challenging — for experienced bakers"
```

- Displayed below the variant grid when Four-Fold is selected
- Color: `risingGreen` for beginner, `goldenCrust` for intermediate, `overProofAmber` for advanced, `burnedRed` for expert
- Includes a one-line description of what makes it harder/easier
- Also relevant if user overrides hydration beyond 80% via a future formula builder

---

## Right Column: Segmented Content

The right column has a segmented control at the top to switch between three views:

### Segment 1: Ingredients (default)

```
  Ingredients                                  900g
  ┌────────────────────────────────────────────────┐
  │ AP Flour              95%              456g    │
  │ Rye Flour              5%               24g    │
  │ Water                 74%              355g    │
  │ Salt                  2.2%              11g    │
  │ Levain                 5%               24g    │
  ├────────────────────────────────────────────────┤
  │ Hydration: 74%         Total: ~870g            │
  └────────────────────────────────────────────────┘
```

### Segment 2: Timeline

```
  Timeline                              Est. 22h

  ● 6:00 AM   Mix (autolyse)
  │            Combine water, levain, flours. Rest 30 min.
  │
  ○ 6:30 AM   Add salt
  │            Add reserved water + salt. Knead. Rest 30 min.
  │
  ○ 7:00 AM   Coil fold
  │            One set of coil folds. Bulk proof 12-16h.
  │
  ○ 7:00 PM   Preshape
  │            Preshape into round. Rest 30 min.
  │
  ○ 7:30 PM   Final shape
  │            Shape, transfer to proofing basket. Rest 30 min.
  │
  ○ 8:00 PM   Fridge
  │            Cold proof 8-24h.
  │
  ○ 4:00 AM   Bake!
               Preheat 475°F, Dutch oven. ~40 min total.
```

### Segment 3: DDT Calculator

```
  Water Temperature (DDT)

  Target DDT: 78°F

  ┌────────────────────────────────────────────────┐
  │ Flour temperature      [  68  ] °F             │
  │ Room temperature       [  72  ] °F             │
  │ Levain temperature     [  40  ] °F             │
  │                                                │
  │ Mixing method:                                 │
  │ [● Hand]  [○ Stand Mixer]  [○ Food Processor]  │
  │                                                │
  │ ─────────────────────────────────────────────  │
  │                                                │
  │         Use water at: 104.5°F                  │
  │                                                │
  │ ⓘ Friction factor: 5 (hand mixing)            │
  └────────────────────────────────────────────────┘
```

---

## Bottom Actions

```
┌─────────────────────────────────┐  ┌─────────────────────────────────┐
│  📌  Save for Later             │  │  ▶  Start This Bake             │
│  Save this plan to revisit      │  │  Begin guided bake tracker      │
└─────────────────────────────────┘  └─────────────────────────────────┘
```

- **Save for Later:** Stores the current formula + configuration for quick access
- **Start This Bake:** Launches full-screen Bake Tracker with this plan
- Both buttons anchored at bottom of right column

---

## iPad Portrait Layout

```
┌────────────────────────────────────────────┐
│  Plan                              [⚙️]    │
│                                            │
│  FORMULA                                   │
│  ┌──────────┐ ┌──────────┐ ┌──────────┐   │
│  │ No-Knead │ │Four-Fold │ │ Tartine  │   │
│  │  PAL  ●  │ │  PAL     │ │ Country  │   │
│  └──────────┘ └──────────┘ └──────────┘   │
│                                            │
│  DOUGH WEIGHT                              │
│  [ - ]    900g     [ + ]                   │
│                                            │
│  LEVAIN %:  5%                             │
│                                            │
│  [Ingredients] [Timeline] [DDT]            │
│  ┌────────────────────────────────────┐    │
│  │ AP Flour      95%          456g    │    │
│  │ Rye Flour      5%           24g    │    │
│  │ Water         74%          355g    │    │
│  │ Salt          2.2%          11g    │    │
│  │ Levain         5%           24g    │    │
│  │                                    │    │
│  │ Hydration: 74%  Total: ~870g       │    │
│  └────────────────────────────────────┘    │
│                                            │
│  WHEN: ◉ Start now  ○ Bake by             │
│                                            │
│  [📌 Save]          [▶ Start Bake]        │
│                                            │
├────────────┬──────────┬───────────────────┤
│   Plan     │ Starter  │    Log            │
└────────────┴──────────┴───────────────────┘
```

---

## Interactions

- Selecting a formula updates ingredients, timeline, and DDT defaults instantly
- Selecting a Four-Fold variant updates ingredient list to match pre-calculated values
- Changing dough weight rescales all ingredients (timeline unchanged)
- No-Knead: levain % slider (1-10%) with free adjustment
- Four-Fold: variant grid for preset combos, OR manual slider for fine-tuning (12.5-35%)
- Tartine: fixed percentages (no sliders)
- Difficulty indicator updates dynamically based on hydration selection
- "Start now" auto-updates time; "Bake by" reverse-calculates start
- Segment control remembers last selection
- `@AppStorage`: last formula, variant, weight, temp unit
- "Save for Later" stores named plan snapshots (future: list of saved plans)
