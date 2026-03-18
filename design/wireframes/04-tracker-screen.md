# Wireframe: Bake Tracker (Full-Screen)

The Bake Tracker is presented as a full-screen experience from the Plan tab.
It is the primary screen during an active bake (potentially 16–22 hours).

## iPad Landscape Layout

```
┌──────────────────────────────────────────────────────────────────────────────┐
│  Baking: No-Knead PAL                                    [✕ End Bake]       │
│  Step 3 of 7                                                                 │
│                                                                              │
│  ┌─ LEFT: CURRENT STEP (55%) ───────────┐  ┌─ RIGHT: OVERVIEW (45%) ──────┐ │
│  │                                      │  │  bg: parchment-warm           │ │
│  │     Coil Fold + Bulk Proof           │  │                               │ │
│  │                                      │  │  PROGRESS                     │ │
│  │        ┌─────────────┐               │  │                               │ │
│  │        │  ╭───────╮  │               │  │  ✓ Mix (autolyse)    6:00 AM │ │
│  │        │  │12:42:15│  │               │  │  ✓ Add Salt         6:30 AM │ │
│  │        │  │remain. │  │               │  │  ● Coil Fold ◄      7:00 AM │ │
│  │        │  ╰───────╯  │               │  │  ○ Preshape          7:00 PM │ │
│  │        │  [progress]  │               │  │  ○ Final Shape       7:30 PM │ │
│  │        └─────────────┘               │  │  ○ Cold Proof        8:00 PM │ │
│  │     Done around 7:00 PM              │  │  ○ Bake!             4:00 AM │ │
│  │                                      │  │                               │ │
│  │  One set of coil folds, then cover   │  │  ─────────────────────────── │ │
│  │  and let proof at room temperature   │  │                               │ │
│  │  (75-78°F) until about doubled.      │  │  INGREDIENTS                  │ │
│  │                                      │  │  ✓ AP Flour          472g    │ │
│  │  ┌─ TIP ─────────────────────────┐   │  │  ✓ Rye Flour          25g    │ │
│  │  │ Look for 60-100% volume       │   │  │  ✓ Water             368g    │ │
│  │  │ expansion. The dough should be │   │  │    Salt               11g    │ │
│  │  │ jiggly and domed on top.       │   │  │  ✓ Levain             25g    │ │
│  │  └────────────────────────────────┘   │  │                               │ │
│  │                                      │  │  ─────────────────────────── │ │
│  │  [⏭ Skip]  [⏸ Pause]  [Done ✓]     │  │                               │ │
│  │                                      │  │  TOOLS                        │ │
│  │                                      │  │  [Straight-sided container]   │ │
│  │                                      │  │  [Cover or shower cap]        │ │
│  │                                      │  │  [Instant-read thermometer]   │ │
│  │                                      │  │  Next: bench scraper,         │ │
│  │                                      │  │  unfloured surface            │ │
│  │                                      │  │                               │ │
│  │                                      │  │  ─────────────────────────── │ │
│  │                                      │  │                               │ │
│  │                                      │  │  NOTES                        │ │
│  │                                      │  │  [📷 Add Photo] [📝 Add Note] │ │
│  └──────────────────────────────────────┘  └───────────────────────────────┘ │
│                                                                              │
└──────────────────────────────────────────────────────────────────────────────┘
```

---

## Top Bar

```
  Baking: No-Knead PAL                                    [✕ End Bake]
  Step 3 of 7
```

- Left: title ("Baking: _formula name_") + subtitle ("Step N of M")
- Title uses Fraunces serif for formula name, regular weight for "Baking:"
- Subtitle in Source Serif, small, wheat-light color
- Right: "End Bake" button — outlined, subtle (border only, not filled)
- End Bake hover state: border and text turn burned-red
- Bottom border: flour-dust-deep

---

## Left Panel (55%) — Current Step

### Step Name
- Fraunces serif, ~26px, centered
- Shows the combined step name (e.g., "Coil Fold + Bulk Proof")

### Timer Ring
- Large circular countdown timer (260×260px)
- **Background ring**: flour-dust color, thin stroke
- **Progress ring**: fills clockwise as time elapses
  - `goldenCrust` when counting (with golden glow drop shadow)
  - `overProofAmber` when paused
  - `risingGreen` when complete
- **Tick marks**: 60 subtle tick marks around the ring (every 5 = bolder)
- **Inner display**:
  - Time in Fira Mono, ~38px: `12:42:15`
  - Label below: "remaining" (or "PAUSED" in overProofAmber when paused)
- For long steps (12h+), hint below ring: "Done around 7:00 PM"

### Step Instructions
- Centered below timer, max-width ~440px
- Source Serif body text, wheat-field color
- Describes what the baker should do

### TIP Card
- Rounded card with sage-bg background, sage border
- "TIP" badge (Fraunces, tiny, bold) + text
- Shows proofing guidance, technique tips
- Only shown when the step has a tip (not all steps do)

### Control Buttons
- Row of 3 buttons, centered:
  - **Skip** (⏭): outlined, wheat-field text. Hover: wheat-light border
  - **Pause** (⏸): outlined. Toggles to "Resume" (▶) with overProofAmber styling when paused
  - **Done** (✓): filled goldenCrust, white text, golden shadow. Primary CTA.

---

## Right Panel (45%) — Overview

Background: parchment-warm. Scrollable. Separated into sections by thin dividers.

### Progress
- Vertical list with connecting line (flour-dust-deep)
- **Completed steps**: sage green dot with ✓, name struck through, wheat-light text
- **Current step**: goldenCrust dot (larger, with glow), bold name, golden-glow background row
- **Upcoming steps**: open circle (flour-dust-deep border), wheat-field text
- Each row shows: step name (left) + scheduled time (right, Fira Mono)

### Ingredients
- Compact list of all ingredients with check-off state
- Each row: name (left) + grams (right, Fira Mono)
- **Checked off**: ✓ prefix, struck through, wheat-light text
  - Flour and water checked off during Mix step
  - Salt checked off during Add Salt step
  - Levain checked off during Mix step
- **Flour rows**: sage-bg highlight when unchecked, transparent when checked
- Check state advances automatically as steps are completed

### Tools
- Section showing tools needed for the **current step**
- Displayed as pill/tag chips with tool icon + name
  - Rounded, flour-dust background, crust-medium text
- Below: italic hint for next step's tools (e.g., "Next: bench scraper, unfloured surface")
- Tools update when the step advances

### Notes
- Quick action buttons: [📷 Add Photo] [📝 Add Note]
- Buttons: outlined, flour-dust-deep border, wheat-field text
- Photo: opens camera or PhotosPicker
- Note: opens text input
- Captured media persists to the eventual Bread Log entry

---

## Timer States

```
COUNTING DOWN               PAUSED                      STEP COMPLETE
┌─────────────┐            ┌─────────────┐             ┌─────────────┐
│   12:42:15  │            │   12:42:15  │             │    00:00    │
│  remaining  │            │   PAUSED    │             │    done     │
│    ╭────╮   │            │    ╭────╮   │             │    ╭────╮   │
│    │    │   │            │    │    │   │             │    │ ✓  │   │
│    ╰────╯   │            │    ╰────╯   │             │    ╰────╯   │
│  ▓▓▓▓░░░░░  │            │  ▓▓▓▓░░░░░  │             │  ▓▓▓▓▓▓▓▓▓  │
└─────────────┘            └─────────────┘             └─────────────┘
  goldenCrust               overProofAmber               risingGreen
  + golden glow             + amber glow                 + sage glow
```

---

## Step Complete Celebration

When the "Done" button is tapped, a brief celebration overlay appears:

```
┌──────────────────────────────────────────────────────────────────────┐
│                                                                      │
│                      ┌───────┐                                       │
│                      │   ✓   │   ← sage green circle, pop animation │
│                      └───────┘                                       │
│                                                                      │
│                  Coil Fold — done!                                    │
│                  Moving to Preshape…                                  │
│                                                                      │
└──────────────────────────────────────────────────────────────────────┘
```

- Semi-transparent parchment overlay with backdrop blur
- Green checkmark circle with pop-bounce animation
- Step name + "done!" in Fraunces
- "Moving to [next step]…" in Source Serif
- Auto-dismisses after ~1.4 seconds, advances to next step

---

## Notification Preview

```
┌──────────────────────────────────────┐
│ 🍞 Fournil                    now   │
│ Time for: Preshape                   │
│ Your dough has bulk proofed.         │
│ Preshape into a round.              │
│                                      │
│  [Snooze 5m]  [Open]  [Done]       │
└──────────────────────────────────────┘
```

---

## Component Details

### Interactions
- Timer updates every second with smooth ring animation
- Notifications scheduled for each upcoming step
- Pause freezes timer and changes ring color to amber
- Skip advances immediately (with confirmation dialog)
- Done triggers celebration overlay, then advances
- "End Bake" top-right with confirmation dialog ("End this bake? Your progress will be saved.")
- On completion of last step: celebration, then prompt to log the bake
- Active bake persists to SwiftData — survives app termination
- On app relaunch with active bake: resume tracker with corrected times

### Entry Animations
- Left panel content fades in with staggered slide-up
- Progress items animate in with stagger
- Smooth transitions when advancing steps
