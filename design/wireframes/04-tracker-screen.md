# Wireframe: Bake Tracker (Full-Screen)

The Bake Tracker is presented as a full-screen experience from the Planner.
It is the primary screen during an active bake (potentially 16-22 hours).

## iPad Landscape Layout

```
┌──────────────────────────────────────────────────────────────────────────────┐
│  Baking: No-Knead PAL                               [✕ End Bake]            │
│  Step 3 of 7                                                                 │
│                                                                              │
│  ┌─ LEFT: CURRENT STEP (55%) ───────────┐  ┌─ RIGHT: OVERVIEW (45%) ──────┐ │
│  │                                      │  │                               │ │
│  │           COIL FOLD                  │  │  STEP PROGRESS                │ │
│  │                                      │  │                               │ │
│  │        ┌─────────────┐               │  │  ✓ Mix (autolyse)    6:00 AM │ │
│  │        │             │               │  │  ✓ Add salt          6:30 AM │ │
│  │        │   12:42:15  │               │  │  ● Coil fold ◄──    7:00 AM │ │
│  │        │  remaining  │               │  │  ○ Preshape          7:00 PM │ │
│  │        │             │               │  │  ○ Final shape       7:30 PM │ │
│  │        │    ╭────╮   │               │  │  ○ Fridge            8:00 PM │ │
│  │        │    │    │   │               │  │  ○ Bake!             4:00 AM │ │
│  │        │    ╰────╯   │               │  │                               │ │
│  │        │  ▓▓▓▓▓░░░░  │               │  │  ─────────────────────────── │ │
│  │        └─────────────┘               │  │                               │ │
│  │                                      │  │  INGREDIENTS                  │ │
│  │  Do one set of coil folds.           │  │  AP Flour           456g     │ │
│  │  Transfer to a straight-sided        │  │  Rye Flour           24g     │ │
│  │  container. Cover and let sit        │  │  Water              355g     │ │
│  │  at room temperature (75-78°F)       │  │  Salt                11g     │ │
│  │  until about doubled, 12-14h.        │  │  Levain              24g     │ │
│  │                                      │  │                               │ │
│  │  TIP: Look for 60-100% volume       │  │  ─────────────────────────── │ │
│  │  expansion. The dough should be      │  │                               │ │
│  │  jiggly and domed on top.            │  │  📷 [Add Photo]              │ │
│  │                                      │  │  🎤 [Voice Note]             │ │
│  │  ┌──────┐  ┌──────┐  ┌──────┐       │  │  📝 [Add Note]               │ │
│  │  │ Skip │  │Pause │  │ Done │       │  │                               │ │
│  │  │  ▶▶  │  │  ⏸   │  │  ✓   │       │  │                               │ │
│  │  └──────┘  └──────┘  └──────┘       │  │                               │ │
│  │                                      │  │                               │ │
│  └──────────────────────────────────────┘  └───────────────────────────────┘ │
│                                                                              │
└──────────────────────────────────────────────────────────────────────────────┘
```

## Timer States

```
COUNTING DOWN                    PAUSED                         STEP COMPLETE
┌─────────────┐                 ┌─────────────┐                ┌─────────────┐
│   12:42:15  │                 │   PAUSED    │                │    DONE!    │
│  remaining  │                 │   12:42:15  │                │             │
│    ╭────╮   │                 │    ╭────╮   │                │    ╭────╮   │
│    │ ▓▓ │   │                 │    │ ░░ │   │                │    │ ✓  │   │
│    ╰────╯   │                 │    ╰────╯   │                │    ╰────╯   │
│  ▓▓▓▓░░░░░  │                 │  ▓▓▓▓░░░░░  │                │  ▓▓▓▓▓▓▓▓▓  │
└─────────────┘                 └─────────────┘                └─────────────┘
  goldenCrust fill                overProofAmber                  risingGreen
```

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

## Proofing Guide (Accessible via "TIP" area or button)

```
┌────────────────────────────────────────────┐
│  Proofing Guide                   [Close]  │
│                                            │
│  UNDER-PROOFED                             │
│  • Dough hasn't doubled                    │
│  • Dense, tight crumb                      │
│  • Less oven spring                        │
│  → Wait longer. Be patient.                │
│                                            │
│  JUST RIGHT                                │
│  • Dough has doubled (or close)            │
│  • Jiggly, domed on top                    │
│  • Passes the poke test                    │
│  → Proceed to next step.                   │
│                                            │
│  OVER-PROOFED                              │
│  • Dough has more than doubled             │
│  • Flat or collapsing top                  │
│  • Sticky, hard to shape                   │
│  → Shape quickly. Reduce levain % or       │
│    proof time next bake.                   │
│                                            │
└────────────────────────────────────────────┘
```

## Component Details

### Timer Ring
- Large circular countdown timer (center of current step area)
- Ring fills clockwise as time elapses
- Color: `goldenCrust` when counting, `overProofAmber` when paused, `risingGreen` when complete
- Digital time display inside ring (HH:MM:SS)
- For long steps (12h+), also show end time: "Done around 7:00 PM"

### Step Instructions
- Below the timer
- Step name in serif headline
- Instructions in sans body text
- Optional "TIP" callout box for proofing/technique guidance

### Control Buttons
- **Skip (▶▶):** Advance to next step immediately (confirm dialog)
- **Pause (⏸):** Freeze timer, snooze notifications
- **Done (✓):** Mark current step complete, advance to next

### Step Progress Sidebar
- Vertical list of all steps
- ✓ = completed (greyed, struck through)
- ● = current (highlighted, `goldenCrust`)
- ○ = upcoming (dimmed)
- Each shows scheduled time
- Tapping a completed step could show its details/photos

### Media Capture
- Photo: opens camera or photo picker, attaches to current step
- Voice Note: records audio memo, attaches to current step
- Note: text input, attaches to current step
- All captured media persists to the eventual Bread Log entry

### Interactions
- Timer updates every second
- Notifications scheduled for each upcoming step
- "End Bake" button (top right) with confirmation dialog
- On completion of last step: celebration moment, prompt to log the bake
- Active bake persists to SwiftData -- survives app kill
- On app relaunch with active bake: resume tracker with corrected times
