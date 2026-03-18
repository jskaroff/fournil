# Fournil - Requirements

## App Summary
Fournil ("bakehouse" in French) is an iPad app for managing sourdough bread baking end-to-end.

## Target Platform
- iPad (primary), all orientations
- iOS 17+

## App Navigation

### Tab Order
The app uses a three-tab navigation structure:
1. **Starter** — Manage starters, track feedings
2. **Bake** — Plan and execute bakes
3. **Log** — Browse completed bakes

Settings accessible via ⚙️ gear icon (top-right, available from any tab).

---

## Core Features

### 1. Baker's Math Calculator (Plan Tab)

#### Formula Selector
- Select from built-in formulas via a vertical scroll carousel with full-width cards: No-Knead PAL, Four-Fold PAL, Tartine Basic Country, 100% Whole Grain, 72h Slow Ferment
- Each formula card shows: long name, difficulty badge, timing, technique, 1-sentence description, link to previous bakes
- Difficulty badges: Beginner (1 dot, sage), Intermediate (2 dots, golden), Advanced (3 dots, clay), Expert (4 dots, burned red)
- "+" card at bottom of carousel shows "Coming soon" popover (future: Formula Builder)

#### Starter Selector
- Positioned in the left column between Formula Selector and Dough Weight
- Shows the currently selected starter with name and health indicator dot
- Tap to pick from a list of all starters
- Defaults to the first starter in the list, or the last-used starter if a completed bake exists
- Required: a bake must be associated with a starter

#### Dough Weight
- Input desired dough weight (200–3000g, increments of 50g)
- Doubler toggle (2×) doubles the entire recipe weight and all ingredient quantities

#### Formula Sliders
- Adjustable hydration and levain percentages via sliders with preset snap points
- Interactive for Four-Fold PAL only; read-only ("Fixed") for other formulas

#### DDT Calculator
- Always visible inline (not in a separate tab)
- Three temperature inputs: Flour, Room, Levain
- Large water temperature result display
- Reference row: "DDT of 78°F · Hand mixing [✎]"
- Tapping edit icon opens popover with:
  - "DDT" label clarified as "Desired Dough Temperature"
  - Target DDT field (default 78°F)
  - Mixing method selector: Hand (friction 5), Mixer (25), Processor (30)

#### Ingredients Panel
- All ingredient weights calculated from baker's percentages
- Pills showing hydration %, levain %, and "2× Doubled" badge when active
- Table: ingredient name, baker's %, grams, total

#### Recipe Instructions
- Displayed below the Ingredients panel, above the Timeline
- Scrollable text showing step-by-step instructions for the selected formula
- Part of the Formula data model (each formula includes an `instructions` array)

#### Timeline
- Vertical step-by-step timeline with day boundary markers
- Proof blocks with hatched diagonal fill showing duration ranges

#### Schedule & Actions
- Schedule modes: Start Now, Start At (pick time), Finish By (reverse-calculate start)
- After tapping Start Bake with a future time, prompt to enable a system notification before the scheduled start (lead time configurable in Settings, default 5 min)
- Buttons: Save (snapshot) and Start Bake

---

### 2. Starter Tracker

A user has one or many starters. The Starter tab is the primary interface for managing all starters and their feeding histories.

#### Starter Model
Each starter has:
- **Name** — user-defined name (e.g., "Rye Baby", "Old Faithful")
- **Source** — where the starter came from (e.g., "Friend", "King Arthur", "Cultivated from scratch")
- **Description** — optional free-form notes about the starter
- **Health status** — derived from time since last feed: Thriving (fed < 12h), Needs Feeding (1–7 days), Needs Revival (> 7 days)
- **Feeding history** — ordered list of 0 or more feedings

#### Feeding Model
Each feeding records:
- **Flour(s)**: one or more entries, each with flour type (e.g., AP, Bread, Rye, Whole Wheat) and weight in grams
- **Water**: amount in grams, type selector (tap or filtered)
- **Water temperature**
- **Optional temperatures**: existing starter temp, ambient temp
- **Notes**: free-form text
- **Timestamp**: defaults to now(), user can adjust if logging a past feeding
- **Discard metadata** (optional): whether discard was saved, and how many grams (if known)
- **Previous feeding pointer**: by default, a new feeding chains to the previous feeding. User can break the chain if they missed logging a feeding.
- **Observations on previous cycle**: when chained, user can note how well the growth/maturation went during the previous feed cycle
- **Photos**: one or many

#### Feeding Presets
Ratio presets are available as quick-fill shortcuts when logging a feed:
- **Standard (2:2:1)**: 150g flour, 150g water, 75g starter
- **Overnight (20:20:1)**: 150g flour, 150g water, 8g starter
- **Revival Protocol**: specific feeding schedule for weak starters
Selecting a preset auto-fills flour/water/starter amounts. User can then customize any value.

#### Empty State (No Starters)
Three large onboarding buttons:
1. **"I've got a starter"** — on tap: Create a Starter form → Log your first feed
2. **"Cultivate a new starter"** — on tap: Create a Starter form → full-screen info sheet describing the steps to cultivate a starter (based on wordloaf.org tiny starter guide), with simple text and iconography. A "Log your first feed" button appears when the starter is ready.
3. **"Find a Starter"** — on tap: full-screen view with placeholder links to buy starters online and links to communities (e.g., r/sourdough subreddit). Links to be finalized.

#### Non-Empty State (Has Starters)
- All starters displayed as cards, each showing: name, health indicator, last feeding summary
- Tap a starter card → opens Starter Details
- Button to create a new starter
- Button/affordance to select a starter and log a feed

#### Starter Details
- All starter metadata (name, source, description)
- Health indicator with color-coded status
- Time since last feed (live countdown timer)
- Photo from the most recent feeding
- Prominent affordance to log a new feeding
- **History section**:
  - Bakes completed with this starter (links to Bake Detail)
  - Chronological feeding history list (most recent first)
  - Time graph visualization of feeding history (deferred to fast follow — V1 ships with list only)

#### Log a Feed
- Full form to configure all feeding values
- Ratio preset shortcuts at the top for quick-fill
- By default, the new feeding chains to the previous feed:
  - When chained, user can log observations about the previous feed cycle (how well the starter grew/matured)
- User can break the chain by indicating they missed a feed
- Timestamp defaults to now(); user can adjust if the feeding occurred in the past
- On save, return to Starter Details

#### Create a Starter
- Form with fields: Name, Source, Description
- On save, navigates to Log first feed (or Cultivate info sheet if that path was chosen)

---

### 3. Bake Planner
- Choose formula and method
- Generate timestamped schedule from start time or desired bake time
- Scaled ingredient list with recipe instructions
- Schedule modes: Start Now, Start At, Finish By
- Notification prompt for future scheduled bakes

### 4. Bake Tracker
- Step-by-step guided walkthrough
- Countdown timers for each step
- Local notifications with snooze/delay
- Pause/resume/skip controls
- Proofing guide (under/over proofing tips)
- Survives app termination
- Ingredient check-off: ingredients checked off as used during mixing steps
- Tools guidance: each step shows required tools and previews tools needed for the next step

---

### 5. Bake Log

#### Grid View
- Reverse chronological photo grid of all completed bakes (newest first)
- **Filter bar** at top: filter by Starter, filter by Formula
- Each card shows: date, formula name, photo, overall rating
- 4 columns in landscape, 3 in portrait
- "+ New Entry" for manual logging

#### Bake Detail
- **Photo carousel** with horizontal scroll and affordance to add more photos
- All metadata displayed with inline edit capabilities
- **Rating dimensions**: overall, crumb, crust, flavor, rise (1–5 stars each)
- Formula details, dough weight, bake details (oven temp, time)
- Notes and crumb description
- **"Bake this Again"** button → navigates to Plan tab with all values preset (formula, starter, weight, variant)
- **System Share button** (↗) — opens iOS share sheet with photo + formula + rating + notes
- **"Share Your Bread"** CTA — on tap, shows "Coming soon" popover. (TODO: concept how to encourage bakers to share their bread with friends, family, and community)

#### Bake Entry Form
- Pre-populated from completed bake tracker (if coming from that flow)
- Includes: photos, formula selector, starter selector, weight, variant (if Four-Fold), ratings, bake details, notes, crumb description
- Required: date (auto-filled), overall rating
- Optional: everything else

---

### 6. Inspiration & Reference (in Settings)
- Credits: Andrew Janjigian (Wordloaf), Chad Robertson (Tartine)
- Sourdough glossary (autolyse, bulk proof, DDT, hydration, levain, etc.)
- Links to further reading
- Equipment recommendations

### 7. Formula Builder (Future — Not V1)
- Accessed via "+" button in the formula carousel
- Create custom formulas with name, description, difficulty, ingredient percentages, timeline steps, and instructions
- Saved formulas appear alongside built-in formulas
- V1: "+" card shows "Coming soon" popover

---

## General Requirements

### Affiliate Links
- All outbound product links (equipment, further reading, buy starters) can include affiliate links
- Affiliate links are **on by default**
- On the About Fournil page, there is an option to turn off affiliate links
- When affiliate links are disabled, slightly increased emphasis is placed on the Tip section

### About Fournil
- "Fournil is made with love (and Claude) by Josh Skaroff"
- Tip section: "Leave a tip to help the developer buy their next bag of flour"
  - Tip options: $1, $5, $10
- Affiliate link toggle (see above)

### Analytics (TODO)
- Privacy-focused analytics solution required
- No individual user tracking — aggregate usage patterns and dropoff only
- Must value privacy and anonymity
- Solution TBD

### Data Architecture
- All data structures should follow the architecture plan and be built to support future iCloud Sync
- Use UUID primary keys, avoid non-syncable types

---

## NOT V1 (Deferred Features)

### Badges & Streaks
Earn badges for baking streaks and accomplishments:
- **Starter badges**: create first starter; fed starter 5, 10, 25, 50, 100, 500, 1000 days in a row
- **Baking badges**: first bake; first bake of each formula; baked a loaf every day for a week; baked X days/weeks in a row; baked 5, 10, 25, 50, 100, 500, 1000 total loaves
- **Badge gallery**: prominent placement in UI (TBD) to see all earned badges and progress toward future badges
- **Badge detail**: tapping a badge shows large badge with info from the feed/starter/bake that earned it, plus a share button

### Other Deferred
- Formula Builder (custom formulas)
- Feeding history time graph (Starter Details — fast follow)
- "Share Your Bread" social feature (CTA visible with "Coming Soon" popover)
- Voice notes on Bake Tracker
- Analytics implementation (solution TBD)
- iCloud Sync (design for it, implement post-V1)

---

## Sources
- Andrew Janjigian, *The Sourdough Lifestyle Workshop Handout* (2022)
- Chad Robertson, *Tartine Bread* (2010)
