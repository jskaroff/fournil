# Overview

## App Summary
Fournil ("bakehouse" in French) is an iPad app for managing sourdough bread baking end-to-end.

## Target Platform
- iPad (primary), all orientations
- iOS 17+

## Navigation Architecture

**Landscape (regular width):** `NavigationSplitView` sidebar (always visible) + detail column.
**Portrait (compact width):** Sidebar collapses; tab bar appears at bottom.

Home is always the default landing screen on launch.

### Sections

| # | Section | Purpose |
|---|---------|---------|
| 1 | **Home** | Control center — monthly overview, starter status, recent bakes, quick nav |
| 2 | **Starter** | Manage starters, track feedings |
| 3 | **Bake** | Plan and execute bakes |
| 4 | **Log** | Browse completed bakes |
| 5 | **Formulas** | Browse and select built-in formulas (read-only in V1) |

Settings accessible via ⚙️ gear icon in the sidebar footer (available from any screen).

### Navigation Flows

```
Home  [default landing]
├── → Starter section
├── → Bake section
├── → Log section
└── → Formulas section

Starter
├── [Empty] → Create Starter → Log First Feed
│   ├── "I've got a starter"
│   ├── "Cultivate" → Cultivate Info Sheet → Log First Feed
│   └── "Find" → Find a Starter (informational)
└── [Non-empty] → Starter card grid
    ├── Tap → Starter Details → Log a Feed (sheet)
    └── + New Starter → Create Starter

Bake
├── Formula selector → Starter → Weight/DDT controls
├── Ingredients + Timeline (sub-panels)
└── Start Bake → Bake Tracker (full-screen modal)
    └── Complete → Bake Entry Form → Bake Detail

Log
├── Filter bar (Starter, Formula)
├── Photo grid → Bake Detail
│   ├── Bake this Again → Bake (with presets)
│   └── Share (coming soon)
└── + New Entry (sheet) → Bake Entry Form

Formulas
└── Formula list (static) → Formula Detail → "Use this formula" → Bake

Settings ⚙️ → Inspiration · Preferences · Equipment Guide · About Fournil
```
