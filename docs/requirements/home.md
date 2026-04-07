# Home Screen

The Home screen is the default landing screen and control center for a baking session. It answers: "Where am I in my baking right now?" and "What do I need to do next?"

---

## Layout

Two-column iPad landscape layout within the NavigationSplitView detail column.

- **Left column (36%)**: Starter Overview — full column height
- **Right column (64%)**: Three stacked zones (no dividers between them)
  - Zone 1: Navigation Hub
  - Zone 2: Monthly Overview
  - Zone 3: Recent Bakes

---

## Left Column — Starter Overview

A tall card (surface-container-low background, 16px rounded corners, ambient shadow) occupying the full left column height.

### Content (non-empty state)
- **Starter name** — Noto Serif 22px (e.g., "Goldie")
- **Health indicator** — large filled dot (sage/amber/red) + status text: "Thriving", "Needs Feeding", or "Needs Revival"
  - Thriving: fed < 12 hours ago
  - Needs Feeding: fed 12h–7 days ago
  - Needs Revival: fed > 7 days ago
- **Last fed** — relative time + absolute (e.g., "Fed 4 hours ago · Today at 9:30 AM")
- **Flour summary** — compact representation of last feed (e.g., "AP Flour + Rye · 1:1:1")
- **Peak estimate** — (e.g., "Peaks around 2:00 PM") — derived from last feed time + starter type; displayed only when relevant (within ~12 hours)
- **Generous whitespace**
- **"Log a Feed" CTA** — full-width primary gradient button (primary → primary-container) at the bottom of the card

### If multiple starters
- Displays the most-recently-fed starter by default
- Starter name is a tappable dropdown to switch to another starter

### Empty state (no starters yet)
- Large centered icon (e.g., jar illustration or 🫙)
- "Add your first starter to get started"
- "Add Starter" CTA → Create Starter flow

### Behavior
- "Log a Feed" sheet-presents the Log a Feed form (same as from Starter Details)
- On save, Home refreshes immediately
- Health status recalculates on every `.onAppear`

---

## Right Column — Zone 1: Navigation Hub

A 2×2 grid of navigation tap targets near the top of the right column.

### Each tap target
- Background: surface-container-low, 12px rounded corners
- Icon (small, left-aligned or centered above text)
- **Section name** — Manrope medium
- **One-line context hint** — Manrope 12px, on-surface-variant color
- Tap → navigates to that sidebar section

### Content per target

| Target | Icon | Context hint |
|--------|------|-------------|
| Starter | wheat sprout | "{Starter name} · fed {X}h ago" |
| Bake | bread loaf | "Ready to bake" or "Bake in progress" |
| Log | photo grid | "{N} bakes logged" |
| Formulas | document | "{N} formulas" |

### Empty states per target
- Starter (no starters): "Add your first starter"
- Log (no bakes): "No bakes yet"

---

## Right Column — Zone 2: Monthly Overview

A lightweight stats strip showing the current calendar month at a glance.

### Content
- **Month label** — "March 2026" in Noto Serif 18px, left-aligned
- **Four stat chips** in a horizontal row, each with:
  - Large number — Manrope 24px bold
  - Label below — Manrope 12px, on-surface-variant

| Stat | Value | Label |
|------|-------|-------|
| Loaves this month | integer count | "Loaves" |
| Avg hydration | percentage (no decimal) | "Hydration" |
| Avg rating | one decimal (e.g., 4.2) | "Rating" |
| Active starters | count fed in last 48h | "Active" |

### Empty state
"No bakes logged this month — start a bake to see stats"

### Behavior
- Stats are read-only, derived from SwiftData aggregates
- Recalculates on `.onAppear`

---

## Right Column — Zone 3: Recent Bakes

A compact tail of the bread log showing the 2–3 most recent bake entries.

### Header row
- "Recent Bakes" — Manrope 13px, left-aligned
- "See all →" — Manrope 13px, primary color, right-aligned → navigates to Log section

### Bake cards
- 2 cards side by side (3 if screen space allows)
- Background: surface-container-low, 12px rounded corners, ambient shadow
- Each card:
  - **Photo thumbnail** — 80×80px square, 8px rounded corners (placeholder if no photo)
  - **Formula name** — Noto Serif 16px
  - **Date** — Manrope 12px, on-surface-variant (e.g., "Mar 12")
  - **Star rating** — row of 5 small stars, primary fill
  - **Starter name** — Manrope 12px, on-surface-variant
- Tap → Bake Detail

### Empty state
- "Your bakes will appear here"
- "Log a Bake" CTA (secondary button) → Bake Entry Form sheet

---

## Behavior

- Home refreshes on every `.onAppear` — not just on launch
- Monthly stats update when returning from Log or Bake
- "Log a Feed" sheets over the current screen without navigating away
- "Bake this Again" on a recent bake card navigates to the Bake section with that formula + starter preloaded
- Home does not hold persistent state — it reads live from SwiftData on each appearance

---

## Wireframe
`design/wireframes/00-home.svg` — Not started
