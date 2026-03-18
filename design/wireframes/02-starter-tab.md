# Wireframe: Starter Tab

The Starter tab manages all starters and their feedings. It conditionally renders an
empty state (onboarding) or a non-empty state (starter cards). Detailed screens are
in separate wireframe files.

## Conditional Rendering

```
Starter Tab
├── [No starters] → Empty State (see 09-starter-empty-state.md)
└── [Has starters] → Starter List (see below + 10-starter-list.md)
    └── Tap card → Starter Details (see 11-starter-details.md)
        └── Log a Feed (see 12-log-a-feed.md)
```

---

## Empty State (No Starters)

See **09-starter-empty-state.md** for full wireframe.

Three large onboarding buttons:
1. "I've got a starter" → Create Starter → Log first feed
2. "Cultivate a new starter" → Create Starter → Cultivate info sheet → Log first feed
3. "Find a Starter" → Links to buy/find starters

---

## Non-Empty State (Has Starters)

### iPad Landscape Layout

```
┌──────────────────────────────────────────────────────────────────────────────┐
│  Starters                                              [+ New Starter]      │
│                                                                              │
│  ┌─────────────────────┐  ┌─────────────────────┐  ┌─────────────────────┐  │
│  │  🟢 Rye Baby        │  │  🟡 Old Faithful    │  │  🟢 Pumpernickel   │  │
│  │                      │  │                      │  │                      │
│  │  Fed 6 hours ago     │  │  Fed 3 days ago      │  │  Fed 10 hours ago   │  │
│  │  AP + Rye · 150g ea  │  │  Bread flour · 150g  │  │  Dark rye · 100g    │  │
│  │  Peaked at 4.5h      │  │  Last peak: 5.2h     │  │  Peaked at 6h       │  │
│  │                      │  │                      │  │                      │
│  │  ┌──────┐            │  │  ┌──────┐            │  │  ┌──────┐            │
│  │  │photo │            │  │  │photo │            │  │  │photo │            │
│  │  └──────┘            │  │  └──────┘            │  │  └──────┘            │
│  └─────────────────────┘  └─────────────────────┘  └─────────────────────┘  │
│                                                                              │
├────────────────┬────────────────┬──────────────────────────────────────────┤
│  Starter (●)   │      Bake      │     Log                                  │
└────────────────┴────────────────┴──────────────────────────────────────────┘
```

### Starter Card

Each starter is shown as a card with:
- **Health indicator dot** (🟢 Thriving, 🟡 Needs Feeding, 🔴 Needs Revival)
- **Starter name** (Fraunces serif, prominent)
- **Time since last feed** (relative: "Fed 6 hours ago")
- **Last feeding summary** (flour types + amounts)
- **Last peak time** (if recorded)
- **Thumbnail photo** from most recent feeding (if available)

Cards are arranged in a responsive grid (3 columns landscape, 2 portrait).

### Health Indicator States

```
🟢 THRIVING           🟡 NEEDS FEEDING        🔴 NEEDS REVIVAL
Fed < 12 hours ago    Fed 1-7 days ago        Fed > 7 days ago
"Ready to bake"       "Time for a refresh"    "Needs revival protocol"
```

Health is derived from time since last feeding. Color dot appears on both the
starter card and in Starter Details.

### Interactions
- **Tap a starter card** → navigates to Starter Details (see 11-starter-details.md)
- **"+ New Starter" button** → opens Create a Starter form (see 13-create-starter.md)
- **Long-press on a card** → context menu with "Delete Starter" (with confirmation)

---

## Related Wireframes

| File | Screen |
|------|--------|
| 09-starter-empty-state.md | Empty state with 3 onboarding buttons |
| 10-starter-list.md | Extended starter list details |
| 11-starter-details.md | Full starter details + history |
| 12-log-a-feed.md | Log a feeding form |
| 13-create-starter.md | Create a new starter form |
| 14-cultivate-info-sheet.md | Guide to cultivating a starter from scratch |
| 15-find-a-starter.md | Links to buy/find starters |
