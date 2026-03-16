# Wireframe: Starter Tab

## iPad Landscape Layout

```
┌──────────────────────────────────────────────────────────────────────────────┐
│  Starter                                                      [Feed ▶]      │
│                                                                              │
│  ┌─ LEFT COLUMN (35%) ──────────────────┐  ┌─ RIGHT COLUMN (65%) ─────────┐ │
│  │                                      │  │                               │ │
│  │       ┌─────────────┐                │  │  FEEDING HISTORY              │ │
│  │       │             │                │  │                               │ │
│  │       │   ╭─────╮   │                │  │  ┌───────────────────────────┐│ │
│  │       │   │ 🟢  │   │                │  │  │ Mar 15, 8:30 AM          ││ │
│  │       │   │     │   │                │  │  │ 2:2:1 standard           ││ │
│  │       │   ╰─────╯   │                │  │  │ 150g flour · 150g water  ││ │
│  │       │  THRIVING    │                │  │  │ · 75g starter            ││ │
│  │       └─────────────┘                │  │  │ Peaked at 4.5h           ││ │
│  │                                      │  │  └───────────────────────────┘│ │
│  │  Last fed: 8 hours ago               │  │  ┌───────────────────────────┐│ │
│  │  Next feeding: ~4 hours              │  │  │ Mar 14, 7:00 AM          ││ │
│  │                                      │  │  │ 2:2:1 standard           ││ │
│  │  ┌──────────────────────────┐        │  │  │ 150g flour · 150g water  ││ │
│  │  │  STARTER NOTES           │        │  │  │ · 75g starter            ││ │
│  │  │                          │        │  │  │ Peaked at 5h             ││ │
│  │  │  "Fed with KA bread      │        │  │  └───────────────────────────┘│ │
│  │  │   flour, room at 72°F"   │        │  │  ┌───────────────────────────┐│ │
│  │  │                          │        │  │  │ Mar 13, 9:00 PM          ││ │
│  │  └──────────────────────────┘        │  │  │ 20:20:1 overnight        ││ │
│  │                                      │  │  │ 150g flour · 150g water  ││ │
│  │  QUICK STATS                         │  │  │ · 8g starter             ││ │
│  │  Avg peak time: 4.8h                 │  │  └───────────────────────────┘│ │
│  │  Feedings this week: 5               │  │                               │ │
│  │  Days since revival: 42              │  │  │  ...more entries...  │      │ │
│  │                                      │  │                               │ │
│  └──────────────────────────────────────┘  └───────────────────────────────┘ │
│                                                                              │
├──────────┬──────────┬──────────┬──────────┬──────────────────────────────────┤
│ Calculate│ Starter  │  Plan    │   Log    │  Inspire                         │
└──────────┴──────────┴──────────┴──────────┴──────────────────────────────────┘
```

## Health Indicator States

```
THRIVING (green ring)          NEEDS FEEDING (amber ring)       NEEDS REVIVAL (red ring)
   ╭─────╮                       ╭─────╮                          ╭─────╮
   │ 🟢  │                       │ 🟡  │                          │ 🔴  │
   │     │                       │     │                          │     │
   ╰─────╯                       ╰─────╯                          ╰─────╯
  THRIVING                      FEED SOON                        REVIVE ME
  Fed < 12h ago                 Fed 1-7 days ago                 Fed > 7 days ago
  "Ready to bake"               "Refresh before using"           "Needs revival protocol"
```

## Feed Sheet (Presented as Modal)

```
┌────────────────────────────────────────────┐
│  Record Feeding                    [Save]  │
│                                    [Cancel]│
│                                            │
│  RATIO                                     │
│  ┌──────────┐ ┌──────────┐ ┌──────────┐   │
│  │ Standard │ │Overnight │ │ Revival  │   │
│  │  2:2:1 ● │ │ 20:20:1  │ │ Protocol │   │
│  └──────────┘ └──────────┘ └──────────┘   │
│                                            │
│  AMOUNTS                                   │
│  Flour     [  150  ] g                     │
│  Water     [  150  ] g                     │
│  Starter   [   75  ] g                     │
│                                            │
│  TEMPERATURES (optional)                   │
│  Flour temp    [  68  ] °F                 │
│  Room temp     [  72  ] °F                 │
│  Water temp    [  80  ] °F                 │
│                                            │
│  NOTES                                     │
│  ┌────────────────────────────────────┐    │
│  │ Used KA bread flour + rye...      │    │
│  └────────────────────────────────────┘    │
│                                            │
│  ☐ Set reminder for peak check (4h)       │
│                                            │
└────────────────────────────────────────────┘
```

## Component Details

### Health Indicator Ring
- Circular ring/badge, prominent at top of left column
- Color maps to health status: `risingGreen`, `overProofAmber`, `burnedRed`
- Animated fill or pulse when thriving
- Text label below ring states status + guidance

### Last Feeding Summary
- Time since last feeding (relative: "8 hours ago")
- Estimated next feeding time
- Based on ratio used: standard = 12h, overnight = next morning

### Feeding History List
- Scrollable list of all past feedings
- Each row: date/time, ratio type, amounts, peak time (if logged)
- Tapping a row could expand to show full details + notes
- Most recent at top

### Feed Button
- Prominent button top-right: "Feed"
- Opens the Feed Sheet as a modal/sheet
- Pre-fills amounts based on selected ratio

### Feed Sheet
- Ratio picker: tappable cards (standard, overnight, revival)
- Selecting a ratio pre-fills the gram amounts
- Temperature fields are optional (collapse if not needed)
- Notes field for free-form text
- Optional reminder checkbox to check on starter later

### Quick Stats
- Derived from feeding history
- Average peak time across recent feedings
- Feeding frequency this week
- Days since last revival (if applicable)

### Interactions
- Selecting a ratio in the feed sheet auto-fills amounts
- After saving a feeding, history list updates immediately
- Health indicator recalculates on every app foreground
- Long-press on a history entry to delete
