# Wireframe: Planner Tab

## iPad Landscape Layout

```
┌──────────────────────────────────────────────────────────────────────────────┐
│  Plan a Bake                                                                 │
│                                                                              │
│  ┌─ LEFT COLUMN (40%) ──────────────────┐  ┌─ RIGHT COLUMN (60%) ─────────┐ │
│  │                                      │  │                               │ │
│  │  FORMULA                             │  │  TIMELINE           Est. 22h  │ │
│  │  ┌──────────┐ ┌──────────┐           │  │                               │ │
│  │  │ No-Knead │ │Four-Fold │           │  │  ● 6:00 AM  Mix (autolyse)   │ │
│  │  │  PAL  ●  │ │  PAL     │           │  │  │          30 min            │ │
│  │  └──────────┘ └──────────┘           │  │  ○ 6:30 AM  Add salt         │ │
│  │  ┌──────────┐                        │  │  │          30 min            │ │
│  │  │ Tartine  │                        │  │  ○ 7:00 AM  Coil fold        │ │
│  │  │ Country  │                        │  │  │          12-16h            │ │
│  │  └──────────┘                        │  │  ○ 7:00 PM  Preshape         │ │
│  │                                      │  │  │          30 min            │ │
│  │  DOUGH WEIGHT                        │  │  ○ 7:30 PM  Final shape      │ │
│  │  [ - ]    900g     [ + ]             │  │  │          30 min            │ │
│  │                                      │  │  ○ 8:00 PM  Fridge           │ │
│  │  WHEN                                │  │  │          8-24h             │ │
│  │  ◉ Start now (6:00 AM)              │  │  ○ 4:00 AM  Bake!            │ │
│  │  ○ Bake by: [date/time picker]       │  │             ~40 min           │ │
│  │                                      │  │                               │ │
│  │  ADJUSTMENTS                         │  │  ─────────────────────────── │ │
│  │  Levain %:  5%   [slider]            │  │                               │ │
│  │  Hydration: 74%  [slider]            │  │  INGREDIENTS                  │ │
│  │                                      │  │  ┌───────────────────────────┐│ │
│  │                                      │  │  │ AP Flour           456g  ││ │
│  │  ┌────────────────────────────────┐  │  │  │ Rye Flour           24g  ││ │
│  │  │                                │  │  │  │ Water              355g  ││ │
│  │  │    [ Start This Bake ▶ ]       │  │  │  │ Salt                11g  ││ │
│  │  │                                │  │  │  │ Levain              24g  ││ │
│  │  └────────────────────────────────┘  │  │  └───────────────────────────┘│ │
│  │                                      │  │                               │ │
│  └──────────────────────────────────────┘  └───────────────────────────────┘ │
│                                                                              │
├──────────┬──────────┬──────────┬──────────┬──────────────────────────────────┤
│ Calculate│ Starter  │  Plan    │   Log    │  Inspire                         │
└──────────┴──────────┴──────────┴──────────┴──────────────────────────────────┘
```

## Timeline Detail (Vertical Timeline Component)

```
    ● 6:00 AM ─── Mix (autolyse) ──────────────────────────────
    │             Combine water, levain, and flours.
    │             Stir until no dry flour remains.
    │             Cover and rest 30 min.
    │             ░░░░░░░░░░░░░░░░░░░░░  30 min
    │
    ○ 6:30 AM ─── Add salt ────────────────────────────────────
    │             Add reserved water and salt.
    │             Knead until uniform. Cover and rest 30 min.
    │             ░░░░░░░░░░░░░░░░░░░░░  30 min
    │
    ○ 7:00 AM ─── Coil fold ──────────────────────────────────
    │             One set of coil folds. Cover.
    │             Bulk proof at 75-78°F until doubled.
    │             ░░░░░░░░░░░░░░░░░░░░░  12-16h
    │
    ...
```

## Planning Mode: "Bake By" (Reverse Planning)

```
  WHEN
  ○ Start now
  ◉ Bake by: [ Sat Mar 15, 6:00 PM ▼ ]

  Calculated start: Fri Mar 14, 8:00 PM
  ⚠️ You should start tonight!
```

When "Bake by" is selected, the timeline is generated in reverse from the desired bake time, and the required start time is prominently displayed. If the start time is in the past, show a warning.

## Component Details

### Formula Cards
- Same component as Calculator tab (reusable `FormulaCard`)
- Selected card highlighted with `goldenCrust` accent

### Dough Weight Input
- Same component as Calculator tab (reusable `DoughWeightInput`)
- Shares the `@AppStorage` value with Calculator tab

### Planning Mode Toggle
- "Start now" uses current time
- "Bake by" opens a date/time picker
- Reverse planning computes start time from bake time

### Timeline View
- Vertical timeline with connected dots and lines
- Filled dot (●) = first step / current focus
- Open dots (○) = future steps
- Each step: time, name, brief instructions, duration bar
- Tapping a step expands to show full instructions
- Total estimated duration shown at top

### Ingredient List
- Compact version below timeline
- Same calculation engine as Calculator tab
- Shows final gram amounts for the configured formula

### "Start This Bake" Button
- Large, prominent CTA
- Transitions to the Bake Tracker (full-screen presentation)
- Passes the configured timeline and ingredients to the tracker
- Disabled until a formula is selected

### Interactions
- Changing formula updates both timeline and ingredients
- Changing weight updates ingredients (timeline steps don't change)
- Changing levain/hydration updates both
- "Start now" auto-updates the start time every minute
- All configuration persists via `@AppStorage`
