# Wireframe: Starter Empty State

Shown when the user has no starters. Three large onboarding buttons guide the
user to get started with their first starter.

## iPad Landscape Layout

```
┌──────────────────────────────────────────────────────────────────────────────┐
│  Starters                                                          [⚙️]     │
│                                                                              │
│                                                                              │
│                          🫙                                                   │
│                                                                              │
│                   Every great loaf starts                                    │
│                   with a great starter.                                      │
│                                                                              │
│                                                                              │
│  ┌──────────────────────────────────────────────────────────────────────┐    │
│  │                                                                      │    │
│  │  🍞  I've got a starter                                              │    │
│  │                                                                      │    │
│  │  Already have an active starter? Add it here and start               │    │
│  │  tracking your feedings.                                             │    │
│  │                                                                      │    │
│  └──────────────────────────────────────────────────────────────────────┘    │
│                                                                              │
│  ┌──────────────────────────────────────────────────────────────────────┐    │
│  │                                                                      │    │
│  │  🌱  Cultivate a new starter                                         │    │
│  │                                                                      │    │
│  │  Create a starter from scratch. We'll walk you through               │    │
│  │  the process step by step.                                           │    │
│  │                                                                      │    │
│  └──────────────────────────────────────────────────────────────────────┘    │
│                                                                              │
│  ┌──────────────────────────────────────────────────────────────────────┐    │
│  │                                                                      │    │
│  │  🔍  Find a starter                                                  │    │
│  │                                                                      │    │
│  │  Get a starter from a friend, bakery, or online source.              │    │
│  │  We'll help you find one.                                            │    │
│  │                                                                      │    │
│  └──────────────────────────────────────────────────────────────────────┘    │
│                                                                              │
├────────────────┬────────────────┬──────────────────────────────────────────┤
│  Starter (●)   │      Bake      │     Log                                  │
└────────────────┴────────────────┴──────────────────────────────────────────┘
```

---

## Button Details

### "I've got a starter"
- Icon: 🍞
- Subtitle: "Already have an active starter? Add it here and start tracking your feedings."
- On tap: navigates to **Create a Starter** form (13-create-starter.md)
- After creating: navigates to **Log your first feed** (12-log-a-feed.md)

### "Cultivate a new starter"
- Icon: 🌱
- Subtitle: "Create a starter from scratch. We'll walk you through the process step by step."
- On tap: navigates to **Create a Starter** form (13-create-starter.md)
- After creating: navigates to **Cultivate Info Sheet** (14-cultivate-info-sheet.md)
- The info sheet has a "Log your first feed" button for when the starter is ready

### "Find a starter"
- Icon: 🔍
- Subtitle: "Get a starter from a friend, bakery, or online source. We'll help you find one."
- On tap: navigates to **Find a Starter** screen (15-find-a-starter.md)
- This is informational only — user returns to empty state and uses "I've got a starter" once they have one

---

## Component Details

### Button Style
- Large tappable cards, full-width
- `flourDust` background with subtle border
- Icon + title in Fraunces serif, bold
- Subtitle in body sans font, `wheatField` color
- Hover/press state: `goldenCrust` border, slight scale-up (1.01x)
- Generous padding: 20pt vertical, 24pt horizontal
- Rounded corners matching the app's card style

### Header
- Jar emoji (🫙) centered, large
- Tagline: "Every great loaf starts with a great starter."
- Fraunces serif, `crustBrown` color

### Layout
- Centered column, max-width ~600px on landscape iPad
- Buttons stacked vertically with 16pt spacing
- Equal visual weight for all 3 options

---

## Interactions
- Tapping any button navigates to the appropriate flow
- No back button needed — this is the tab root
- Once a starter is created, this screen is replaced by the non-empty state (02-starter-tab.md)
