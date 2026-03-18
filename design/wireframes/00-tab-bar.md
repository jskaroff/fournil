# Wireframe: Tab Bar & Navigation

## Tab Bar Layout (Bottom) + Settings (Top)

```
┌──────────────────────────────────────────────────────────────────┐
│  Fournil                                              [⚙️]      │
│                                                     Settings     │
│                        [Active Screen]                           │
│                                                                  │
├────────────────┬────────────────┬────────────────────────────────┤
│     🫙         │     📋         │     📖                         │
│   Starter      │    Bake        │     Log                        │
└────────────────┴────────────────┴────────────────────────────────┘
```

## Tabs (3)

| Tab | Icon (SF Symbol) | Label | Purpose |
|-----|-----------------|-------|---------|
| 1 | `flask` | Starter | Manage starters & feedings |
| 2 | `list.clipboard` | Bake | Baker's math calculator + planner + timeline |
| 3 | `book.closed` | Log | Bread log / bake journal |

## Settings (⚙️ gear icon, top-right navigation)

Accessible from any tab via gear icon in the navigation bar. Opens as a full-screen push or sheet.

Settings contains:
- **Inspiration** — credits, sources, glossary, further reading
- **Formula Builder** — custom formula creation (future phase, "Coming Soon")
- **Preferences** — temperature unit (°F/°C), default dough weight, affiliate link toggle
- **Equipment Guide** — recommended tools from Janjigian's list
- **About Fournil** — attribution, tip bucket, affiliate link toggle

## Navigation Flows

```
Starter (Tab 1)
├── [Empty State] ──┬── "I've got a starter" ──► Create Starter ──► Log First Feed
│                   ├── "Cultivate a new starter" ──► Create Starter ──► Cultivate Info Sheet ──► Log First Feed
│                   └── "Find a Starter" ──► Find a Starter (full screen)
├── [Non-Empty State] ── Starter Cards
│   ├── Tap card ──► Starter Details
│   │                   ├── Log a Feed (sheet/push)
│   │                   ├── Bake history ──► Bake Detail (in Log tab)
│   │                   └── Feeding history (inline list)
│   └── Create New Starter ──► Create Starter form
└── Log a Feed (quick action)

Bake (Tab 2)
├── Configure formula (inline carousel)
├── Select starter (inline selector)
├── View ingredients + recipe instructions + DDT (inline)
├── View timeline (inline)
├── Save for later
└── Start Bake ──► [Tracker - full screen]
                       │
                       └── Complete ──► Log Entry (sheet)

Log (Tab 3)
├── Filter bar (by Starter, by Formula)
├── Bake Detail ──┬── Share (system share sheet)
│                 ├── Edit
│                 ├── Bake this Again ──► Bake tab (preset values)
│                 └── Share Your Bread (coming soon popover)
└── New Entry (sheet)

Settings ⚙️
├── Inspiration (credits, glossary, reading, equipment)
├── Formula Builder (future — "Coming Soon")
├── Preferences (temp unit, default weight, affiliate toggle)
├── Equipment Guide
└── About Fournil (attribution, tip bucket)
```

## iPad Considerations
- Tab bar remains at bottom in all orientations
- Settings gear icon in navigation bar, top-right
- Active tab uses `goldenCrust` accent color
- Inactive tabs use `wheatField` secondary text color
- Tab bar background: `flourDust` surface color
