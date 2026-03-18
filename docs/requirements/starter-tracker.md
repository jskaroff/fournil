# Starter Tracker

## Starter Model
A user has one or many starters. Each starter has:
- **Name** — user-defined (e.g., "Rye Baby", "Old Faithful")
- **Source** — where it came from (e.g., "Friend", "King Arthur", "Cultivated from scratch")
- **Description** — optional free-form notes
- **Health status** — derived from time since last feed:
  - Thriving: fed < 12h
  - Needs Feeding: 1–7 days
  - Needs Revival: > 7 days
- **Feeding history** — ordered list of 0 or more feedings

---

## Feeding Model
Each feeding records:
- **Flour(s)**: one or more entries, each with flour type and weight in grams
  - Flour selector **autocompletes** any previously entered flour types
  - Prepopulated with 5 common flours: All-Purpose, Bread Flour, Whole Wheat, Rye, Spelt
  - **Defaults to the flours from the last feed of this starter** (user can modify)
- **Water**: amount in grams, type selector (tap or filtered)
- **Water temperature**
- **Optional temperatures**: existing starter temp, ambient temp
- **Notes**: free-form text
- **Timestamp**: defaults to now(), user can adjust if logging a past feeding
- **Discard metadata** (optional): whether discard was saved, and how many grams (if known)
- **Previous feeding pointer**: chain/break mechanism (see Chain UX below)
- **Observations on previous cycle**: notes on how the starter grew/matured during the previous feed cycle. **Always available regardless of chain state.**
- **Photos**: one or many

### Chain UX (Previous Feed Connection)
The chain is a **toggle with two visual states**:

**Layout**: Two pills side by side with a break/reconnect control between them:
`[Previous feed pill] ——— (✕) ——— [This feed pill]`
- Left pill: previous feed timestamp + health dot
- Center: circular break/reconnect button with connector lines on both sides
- Right pill: "This feed · Now" with active styling
- "from previous feed" label centered below the connector

**Connected (default)**: amber connector lines visible, ✕ in center circle. Tap ✕ to disconnect.

**Disconnected**: connector lines removed, ✕ swaps to reconnect icon, label changes to "missed a feed". Tap to reconnect.

In both states, the observations field for the previous cycle remains visible.

### Feeding Presets
Quick-fill ratio shortcuts:
- **Standard (2:2:1)**: 150g flour, 150g water, 75g starter
- **Overnight (20:20:1)**: 150g flour, 150g water, 8g starter
- **Revival Protocol**: specific schedule for weak starters

Selecting a preset auto-fills amounts. User can then customize any value.

---

## Starter Tab — Empty State
Three large onboarding buttons:
1. **"I've got a starter"** → Create a Starter → Log your first feed
2. **"Cultivate a new starter"** → Create a Starter → full-screen info sheet (based on wordloaf.org tiny starter guide) with simple text and iconography. "Log your first feed" button when ready.
3. **"Find a Starter"** → Full-screen view with links to buy starters online and community links (e.g., r/sourdough). Placeholder links for now.

## Starter Tab — Non-Empty State
- All starters displayed as cards: name, health indicator dot, last feeding summary
- Tap card → Starter Details
- Button to create a new starter
- Affordance to select a starter and log a feed

---

## Starter Details
- All starter metadata (name, source, description)
- Health indicator with color-coded status
- Time since last feed (live countdown timer)
- Photo from the most recent feeding
- Prominent affordance to log a new feeding
- **History**:
  - Bakes completed with this starter (links to Bake Detail)
  - Chronological feeding history (most recent first)
  - Time graph visualization of feeding history *(deferred — V1 ships with list only)*

---

## Log a Feed (Modal Sheet)
Modal presented over Starter Details.

### Section Order (top to bottom)
1. **Previous Feed** — chain toggle + observations (comes first)
2. **Presets** — ratio shortcut cards
3. **Flour(s)** — with autocomplete, defaults from last feed
4. **Water** — amount, type, temp
5. **Add Details** — progressive disclosure toggles (Discard, Photos, Temps, Notes)
6. **When** — now or earlier
7. **Footer** — Cancel (text) / Save Feed (large primary button, bottom-right)

### Save Behavior
- On save, return to Starter Details
- Timestamp defaults to now(); user can adjust for past feedings

### TODO
- Refine the progressive disclosure toggle design (current tray approach is acceptable placeholder)

---

## Create a Starter
- Form: Name (required), Source (optional), Description (optional)
- On save, navigates based on entry path (Log First Feed or Cultivate Info Sheet)
