# Wireframe: Tab Bar & Navigation

## Tab Bar Layout (Bottom) + Settings (Top)

```
┌──────────────────────────────────────────────────────────────────┐
│  Fournil                                              [⚙️]      │
│                                                     Settings     │
│                        [Active Screen]                           │
│                                                                  │
├────────────────┬────────────────┬────────────────┬───────────────┤
│     📋         │     🫙         │     📖         │               │
│    Plan        │   Starter      │     Log        │               │
└────────────────┴────────────────┴────────────────┘               │
```

## Tabs (3)

| Tab | Icon (SF Symbol) | Label | Purpose |
|-----|-----------------|-------|---------|
| 1 | `list.clipboard` | Plan | Baker's math calculator + bake planner + timeline |
| 2 | `flask` | Starter | Starter health & feeding log |
| 3 | `book.closed` | Log | Bread log / bake journal |

## Settings (⚙️ gear icon, top-right navigation)

Accessible from any tab via gear icon in the navigation bar. Opens as a full-screen push or sheet.

Settings contains:
- **Inspiration** -- credits, sources, glossary, further reading
- **Formula Builder** -- custom formula creation (future phase)
- **Preferences** -- temperature unit (°F/°C), default dough weight
- **About Fournil** -- version, tip bucket for the developer
- **Equipment Guide** -- recommended tools from Janjigian's list

## Navigation Flows

```
Plan ──┬── Configure formula (inline)
       ├── View ingredients + DDT (inline)
       ├── View timeline (inline)
       ├── Save for later
       └── Start Bake ──► [Tracker - full screen]
                              │
                              └── Complete ──► Log Entry (sheet)

Starter ──┬── Feed (sheet)
           └── History (inline list)

Log ──┬── Bake Detail ──┬── Share
      │                  └── Edit
      └── New Entry (sheet)

Settings ⚙️ ──┬── Inspiration
               ├── Formula Builder (future)
               ├── Preferences
               ├── Equipment Guide
               └── About / Tip Bucket
```

## iPad Considerations
- Tab bar remains at bottom in all orientations
- Settings gear icon in navigation bar, top-right
- Active tab uses `goldenCrust` accent color
- Inactive tabs use `wheatField` secondary text color
- Tab bar background: `flourDust` surface color
