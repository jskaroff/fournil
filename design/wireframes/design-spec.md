# Fournil — Design Spec

Consolidated reference for all screen designs. SVG wireframes are the visual source of truth.
This document captures interaction behavior, states, and component details that SVGs cannot show.

---

## Navigation

### Tab Bar (bottom, all screens)
- 3 tabs: **Starter**, **Bake** (active by default), **Log**
- Active tab: `goldenCrust` (#C07A2E), inactive: `wheatField` (#8B7355)
- Tab bar background: `flourDust` (#F2EBE0)
- Settings ⚙️ gear icon: top-right nav bar, available from every tab

### Navigation Flows
```
Starter Tab
├── [Empty] → 3 onboarding buttons
│   ├── "I've got a starter" → Create Starter → Log First Feed
│   ├── "Cultivate" → Create Starter → Cultivate Info Sheet → Log First Feed
│   └── "Find" → Find a Starter (informational)
├── [Non-empty] → Starter card grid
│   ├── Tap card → Starter Details → Log a Feed
│   └── + New Starter → Create Starter
└── Log a Feed → returns to Starter Details

Bake Tab
├── Configure formula, starter, weight, DDT (inline)
├── View ingredients + timeline (side-by-side sub-panels)
└── Start Bake → Bake Tracker (full-screen)
    └── Complete → Log Entry (sheet)

Log Tab
├── Filter bar (by Starter, by Formula)
├── Bake grid → Bake Detail
│   ├── Edit, Share, Bake this Again → Bake tab
│   └── Share Your Bread (coming soon)
└── + New Entry (sheet)

Settings ⚙️ → Inspiration, Preferences, Equipment Guide, About Fournil
```

---

## Screen Index

| SVG File | Screen | Notes |
|----------|--------|-------|
| `01-plan-tab.svg` | Bake tab | Formula carousel, starter selector, ingredients + timeline side-by-side |
| `02-starter-tab.svg` | Starter list (non-empty) | Multi-starter card grid with health dots |
| `03-bread-log-tab.svg` | Bread Log | Photo grid with filter bar |
| `04-bake-tracker.svg` | Bake Tracker | Full-screen during active bake |
| `05-settings-screen.svg` | Settings | Split-view sidebar + detail |
| `06-log-a-feed.svg` | Log a Feed | Modal sheet with chain UX, progressive disclosure |
| `06a/b/c-log-feed-*.svg` | Log a Feed variants | Exploration: no extras / one / all expanded |
| `07-bake-detail.svg` | Bake Detail | Photo carousel, ratings, "Bake this Again" CTA |
| `08-bake-entry-form.svg` | Bake Entry Form | Log a completed bake |
| `09-starter-empty-state.svg` | Starter empty state | 3 onboarding buttons |
| `11-starter-details.svg` | Starter Details | Feeding history, bake history, health |
| `13-create-starter.svg` | Create a Starter | Name, source, description |
| `15-find-a-starter.svg` | Find a Starter | Buy online, community links |

---

## Bake Tab (01-plan-tab.svg)

### Layout
- **Left column** (380px, fixed, scrollable, parchment-warm bg):
  Formula carousel → Starter selector → Dough weight + 2× → Hydration/Levain controls → DDT calculator
- **Right area** splits into two side-by-side sub-panels:
  - **Ingredients** (left): pills, table, recipe instructions below
  - **Timeline** (right): vertical steps with proof blocks
- **Bottom bar**: When (Start Now / Start At / Finish By) + Save + Start Bake

### Formula Carousel
- Vertical scroll, snap-to-card, ~230px max height (shows ~2 cards)
- Selected card: white bg, goldenCrust border, shadow
- Unselected: flourDust bg
- Each card: thumbnail icon, name (Fraunces), difficulty dots + label, timing, description (2-line clamp), "View previous bakes →"
- "+" New Formula: dashed border, "Coming soon" popover on tap

### Starter Selector
- Compact card with health dot (🟢/🟡/🔴), name, "Fed X hours ago", ▼ dropdown
- Defaults to first starter or last-used if a completed bake exists

### Formula Controls (Hydration / Levain)
Three interchangeable styles (toggle: Arc / Slider / Steps):
- **Arc**: circular knob with goldenCrust fill arc, value in center
- **Slider**: horizontal with thumb, tick marks at presets
- **Stepper**: preset buttons + fine-tune ±
- Interactive only for Four-Fold PAL; read-only (dimmed) for others

### DDT Calculator
- White card with 3 temp inputs (Flour, Room, Levain)
- Large result: "Use water at 127°F" (Fraunces, 28px, slate color)
- Reference row: "DDT of 78°F · Hand mixing [✎]"
- Popover: "Desired Dough Temperature" label, target DDT, mixing method selector (Hand/Mixer/Processor)

### Ingredients Panel
- Pills row: hydration %, levain %, "2× Doubled" (red, when active)
- Table: ingredient / baker's % / grams. Flour rows get sage-bg highlight
- Total row with hydration summary
- Recipe Instructions below table (scrollable, numbered steps from formula)

### Timeline Panel
- Vertical line: gradient (goldenCrust → flourDust → sage)
- Step dots: golden (first), open (upcoming), sage (bake)
- Duration badges: short=sage, long=golden, overnight=clay
- Proof blocks (4 styles, toggle: Gradient/Thick/Hatched/Bracket):
  - Bulk: golden-glow gradient, goldenCrust left border
  - Cold: night-bg gradient, night-blue left border
- Day boundary markers: "🌙 tomorrow"

### Schedule
- Radio: Start Now (default) / Start At / Finish By
- Hint: "Starting now, bread ready ~4:40 AM tomorrow"
- Notification prompt on future Start At/Finish By (configurable lead time in Settings)

---

## Bake Tracker (04-bake-tracker.svg)

### Layout
- Full-screen modal from Bake tab
- **Top bar**: "Baking: [formula name]" + "Step N of M" + [✕ End Bake]
- **Left panel (55%)**: step name, timer ring, instructions, TIP card, controls
- **Right panel (45%)**: Progress, Ingredients (check-off), Tools, Notes

### Timer Ring
- 260×260px circular countdown
- Ring colors: goldenCrust (counting), overProofAmber (paused), sage (complete)
- 60 tick marks, Fira Mono digits (38px)
- Long steps: "Done around 7:00 PM" hint

### Controls
- Skip (⏭): outlined, confirm dialog
- Pause (⏸) / Resume (▶): toggles, amber styling when paused
- Done (✓): filled goldenCrust, primary CTA

### Step Complete Celebration
- Semi-transparent overlay with backdrop blur
- Sage checkmark circle, pop-bounce animation
- "[Step name] — done!" + "Moving to [next]…"
- Auto-dismisses ~1.4s

### Right Panel Sections
1. **Progress**: vertical list, completed=✓ struck-through, current=golden highlight, upcoming=dimmed
2. **Ingredients**: compact list with check-off (flour/water at Mix, salt at Add Salt, levain at Mix). Checked items struck through.
3. **Tools**: pill chips for current step tools + "Next: ..." hint
4. **Notes**: [📷 Add Photo] [📝 Add Note] buttons

### Persistence
- Active bake saved to SwiftData, survives app termination
- On relaunch: resume with corrected times

---

## Starter Tab — Empty State (09-starter-empty-state.svg)

- Centered jar emoji + tagline "Every great loaf starts with a great starter."
- 3 large stacked cards:
  1. 🍞 "I've got a starter" → Create Starter → Log First Feed
  2. 🌱 "Cultivate a new starter" → Create Starter → Cultivate Info Sheet
  3. 🔍 "Find a starter" → Find a Starter screen

---

## Starter Tab — Non-Empty (02-starter-tab.svg)

- Card grid (3 cols landscape, 2 portrait)
- Each card: health dot, name, time since last feed, flour summary, peak time, thumbnail photo
- Health states: 🟢 Thriving (< 12h), 🟡 Needs Feeding (1-7 days), 🔴 Needs Revival (> 7 days)
- "+ New Starter" button top-right
- Long-press: context menu with "Delete Starter"

---

## Starter Details (11-starter-details.svg)

### Layout
- **Left (40%)**: last feed photo, health status + timer, about section, bakes with this starter
- **Right (60%)**: feeding history list

### Feeding History
- Cards with: timestamp, preset badge (Standard/Overnight/Custom), flour(s) + water + temp, peak time, discard info, photo count, notes
- Chain connector lines between feedings (solid = chained, dashed = missed feed gap)
- "Log a Feed" button top-right

---

## Log a Feed (06-log-a-feed.svg)

### Presentation
- Modal sheet over Starter Details (not full-screen)
- Drag handle at top, dimmed backdrop

### Section Order (top to bottom)
1. **Previous Feed** — chain toggle + observations (comes first)
2. **Presets** — ratio shortcut cards (Standard / Overnight / Revival)
3. **Flour(s)** — autocomplete with previously entered flours, defaults from last feed
4. **Water** — amount, type (tap/filtered), temp
5. **Add Details** — progressive disclosure toggle tray: Discard, Photos, Temps, Notes (TODO: refine toggle design)
6. **When** — Now (default) / Earlier
7. **Footer** — Cancel (text only, left) / Save Feed (large primary, bottom-right)

### Chain UX (Previous Feed Connection)
Horizontal flow diagram with two pills side by side and a break/reconnect control between them:

**Layout**: `[Prev feed pill] ——— (✕) ——— [This feed pill]`
- Left pill: previous feed timestamp + green health dot
- Center: connector lines on both sides of a circular break/reconnect button
- Right pill: "This feed · Now" with amber dot and golden border
- "from previous feed" label centered below the connector

**Connected (default)**: amber connector lines, ✕ in center circle. Tap ✕ to disconnect.
**Disconnected**: lines removed, ✕ swaps to reconnect icon, label changes to "missed a feed". Tap to reconnect.

Observations on previous cycle are **always visible** regardless of chain state.

### Flour Selector
- Autocompletes any previously entered flour types
- Prepopulated with 5 common: All-Purpose, Bread Flour, Whole Wheat, Rye, Spelt
- Defaults to flours from the last feed of this starter

### Timestamp
- Radio: "Now" (default, shows current time) / "Earlier…" (reveals date picker)

---

## Create a Starter (13-create-starter.svg)

- Centered form: Name (required), Source (optional), Description (optional)
- Save navigates based on entry path

---

## Cultivate Info Sheet (14)

- Full-screen scrollable guide for growing a starter from scratch
- Day-by-day steps with icons: Day 1 mix, Days 2-3 watch, Days 3-5 first feedings, Days 5-7 activity, Days 7-14 ready
- Tips section, link to wordloaf.org guide
- "Log Your First Feed" CTA at bottom
- (SVG not yet created — content page, lower priority)

---

## Find a Starter (15-find-a-starter.svg)

- Sections: Buy Online (3 vendor cards), Ask the Community (Reddit links), Other Ideas (bulleted)
- Footer: "Once you have a starter, tap 'I've got a starter' to start tracking."
- Links may include affiliate parameters (respects Settings toggle)

---

## Bread Log (03-bread-log-tab.svg)

- **Filter bar**: Starter dropdown + Formula dropdown (above grid)
- **Photo grid**: 4 cols landscape, 3 portrait. Each card: photo, date, formula, rating
- Reverse chronological, newest first

---

## Bake Detail (07-bake-detail.svg)

- **Left (50%)**: Photo carousel with ◀▶ arrows, dot indicators, thumbnail strip, "+ Add Photo"
- **Right (50%)**: Title + date + starter, ratings (5 dimensions), formula details, notes, bake details
- **CTAs**: "Bake this Again" (→ Bake tab with presets), "Share Your Bread" (coming soon popover)
- System Share button in top bar

---

## Settings (05-settings-screen.svg)

- Split-view: sidebar menu + detail pane
- Sections: Inspiration, Formula Builder (Coming Soon), Preferences, Equipment Guide, About Fournil

### Preferences
- Temperature unit (°F/°C), default dough weight, default formula
- Affiliate links toggle (on by default). When off, emphasize Tip section.

### About Fournil
- "Fournil is made with love (and Claude) by Josh Skaroff"
- Tip: "Leave a tip to help the developer buy their next bag of flour" — $1, $5, $10
- StoreKit 2 for in-app purchases

---

## Shared Components

### Color System
| Token | Hex | Usage |
|-------|-----|-------|
| parchment | #FEFBF5 | Main background |
| parchment-warm | #FAF5EC | Left column bg |
| flour-dust | #F2EBE0 | Cards, tab bar, surfaces |
| flour-dust-deep | #E4D9C8 | Borders, dividers |
| crust-brown | #4A3228 | Primary text |
| crust-medium | #6B4D3E | Secondary text |
| wheat-field | #8B7355 | Tertiary text, labels |
| wheat-light | #A89478 | Hints, disabled |
| golden-crust | #C07A2E | Primary accent, active states |
| sage | #7A9178 | Success, thriving, beginner |
| night-blue | #3D4F6A | Cold proof |
| clay | #B86B4A | Advanced difficulty |
| burned-red | #A04030 | Expert difficulty, destructive |

### Typography
- **Titles**: Fraunces (serif, 600-700 weight)
- **Body**: Source Serif 4 (serif, 400-500)
- **Mono**: Fira Mono (weights, percentages, times)
- **Section labels**: Fraunces, 11px, 600, uppercase, 0.13em letter-spacing

### Reusable Components
- **Starter Card**: health dot + name + feed info + photo thumbnail
- **Starter Selector**: compact card (Bake tab) or dropdown (forms)
- **Filter Bar**: horizontal dropdown row
- **Photo Carousel**: main + thumbnails + "Add Photo"
- **Flour Entry Row**: type dropdown + grams + remove button
- **Star Rating**: interactive (forms) or display-only (detail)
- **Difficulty Dots**: 1-4 filled, color-coded
- **Expandable Card**: chevron toggle, spring animation
- **Progress Dot**: ✓ completed / ● current / ○ upcoming
- **Empty State**: centered icon + message + CTA
