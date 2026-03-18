# Plan Tab (Baker's Math Calculator)

## Layout
- **Left column** (380px, fixed, parchment-warm bg):
  Formula carousel → Starter selector → Dough weight + 2× → Hydration/Levain controls → DDT calculator
- **Right area** (two side-by-side sub-panels):
  - Ingredients panel (with recipe instructions below)
  - Timeline panel

## Formula Selector
- Vertical scroll carousel with full-width cards
- Built-in formulas: No-Knead PAL, Four-Fold PAL, Tartine Basic Country, 100% Whole Grain, 72h Slow Ferment
- Each card: name, difficulty badge, timing, technique, 1-sentence description, link to previous bakes
- Difficulty: Beginner (1 dot, sage), Intermediate (2, golden), Advanced (3, clay), Expert (4, burned red)
- "+" card at bottom: "Coming soon" popover (future Formula Builder)

## Starter Selector
- Between Formula Selector and Dough Weight in left column
- Shows selected starter with name and health indicator dot
- Tap to pick from all starters
- Defaults to first starter or last-used (if a completed bake exists)
- Required: every bake must be associated with a starter

## Dough Weight
- Input: 200–3000g, increments of 50g
- Doubler toggle (2×): doubles recipe weight and all ingredient quantities

## Formula Sliders (Hydration / Levain)
- Interactive for Four-Fold PAL only; read-only ("Fixed") for other formulas
- Three control styles (toggle: Arc / Slider / Steps)

## DDT Calculator
- Always visible inline (not a separate tab)
- Three temperature inputs: Flour, Room, Levain
- Large water temperature result display
- Reference row: "DDT of 78°F · Hand mixing [✎]"
- Popover on edit icon:
  - "DDT" label clarified as **"Desired Dough Temperature"**
  - Target DDT field (default 78°F)
  - Mixing method selector: Hand (friction 5), Mixer (25), Processor (30)

## Ingredients Panel
- Pills: hydration %, levain %, "2× Doubled" badge
- Table: ingredient / baker's % / grams / total
- Flour rows get sage-bg highlight
- Total row with hydration summary

## Recipe Instructions
- Displayed below the Ingredients panel
- Scrollable text showing step-by-step instructions for the selected formula
- Part of the Formula data model (each formula includes an `instructions` array)

## Timeline Panel
- Vertical step-by-step timeline with day boundary markers
- Proof blocks with hatched diagonal fill (default style)
- Duration badges: short=sage, long=golden, overnight=clay

## Schedule & Actions
- Modes: Start Now (default), Start At (pick time), Finish By (reverse-calculate)
- After tapping Start Bake with a future time: prompt to enable notification (configurable lead time in Settings, default 5 min)
- Buttons: Save (snapshot) and Start Bake
