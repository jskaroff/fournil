# Bake Tracker

Full-screen guided walkthrough during an active bake.

## Layout
- **Top bar**: "Baking: [formula name]" + "Step N of M" + [✕ End Bake]
- **Left panel (55%)**: step name, timer ring, instructions, TIP card, controls
- **Right panel (45%)**: progress list, ingredients check-off, tools, notes

## Timer
- 260×260px circular countdown ring
- Ring colors: goldenCrust (counting), overProofAmber (paused), sage (complete)
- 60 tick marks, Fira Mono digits (38px)
- Long steps: "Done around 7:00 PM" hint

## Controls
- Skip (⏭): outlined, confirm dialog
- Pause (⏸) / Resume (▶): toggles, amber styling when paused
- Done (✓): filled goldenCrust, primary CTA

## Step Complete Celebration
- Semi-transparent overlay with backdrop blur
- Sage checkmark circle, pop-bounce animation
- "[Step name] — done!" + "Moving to [next]…"
- Auto-dismisses ~1.4s

## Right Panel
1. **Progress**: vertical list — ✓ struck-through (completed), golden highlight (current), dimmed (upcoming)
2. **Ingredients**: check-off as used during mixing steps. Checked items struck through.
3. **Tools**: pill chips for current step + "Next: ..." hint
4. **Notes**: [📷 Add Photo] [📝 Add Note] buttons

## Persistence
- Active bake saved to SwiftData, survives app termination
- On relaunch: resume with corrected times
