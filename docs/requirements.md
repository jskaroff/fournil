# Fournil - Requirements

## App Summary
Fournil ("bakehouse" in French) is an iPad app for managing sourdough bread baking end-to-end.

## Core Features

### 1. Baker's Math Calculator
- Select from built-in formulas via a vertical scroll carousel with full-width cards: No-Knead PAL, Four-Fold PAL, Tartine Basic Country, 100% Whole Grain, 72h Slow Ferment
- Each formula card shows: long name, difficulty badge, timing, technique, 1-sentence description, link to previous bakes
- Input desired dough weight (200-3000g)
- Doubler toggle (2×) doubles the entire recipe weight and all ingredient quantities
- See all ingredient weights calculated from baker's percentages
- DDT (Desired Dough Temperature) calculator — always visible inline, not in a separate tab
- Adjustable hydration and levain percentages via sliders with preset snap points (interactive for Four-Fold PAL; read-only for other formulas)
- Difficulty badge shown for every formula: Beginner (1 dot, sage), Intermediate (2 dots, golden), Advanced (3 dots, clay), Expert (4 dots, burned red)

### 2. Starter Tracker
- Track starter health with visual indicator
- Record feedings (ratio, grams, temperatures, notes)
- Feeding history log
- Standard ratios: 2:2:1 (standard), 20:20:1 (overnight), revival protocol
- Health status: thriving / needs feeding / needs revival

### 3. Bake Planner
- Choose formula and method
- Generate timestamped schedule from start time or desired bake time
- Scaled ingredient list
- Schedule modes: Start Now (use current time), Start At (pick a start time), Finish By (pick a desired finish time, reverse-calculates start)
- After tapping Start Bake with a future Start At or Finish By time, prompt user to enable a system notification 5 minutes before the scheduled start time. Notification lead time is configurable in Settings (default: 5 min).

### 4. Bake Tracker
- Step-by-step guided walkthrough
- Countdown timers for each step
- Local notifications with snooze/delay
- Pause/resume/skip controls
- Proofing guide (under/over proofing tips)
- Survives app termination
- Ingredient check-off: ingredients are checked off as they are used during mixing steps (flour and water during Mix, salt during Add Salt, levain during Mix)
- Tools guidance: each step shows required tools and previews tools needed for the next step (e.g., bench scraper, cambro/bowl, banneton, lame, Dutch oven, parchment)

### 5. Bread Log
- Record completed bakes with photos, notes, ratings
- Rating dimensions: overall, crumb, crust, flavor, rise (1-5)
- Photo gallery per bake
- Browse and compare past bakes

### 6. Inspiration
- Credits: Andrew Janjigian (Wordloaf), Chad Robertson (Tartine)
- Sourdough glossary (autolyse, bulk proof, DDT, hydration, levain, etc.)
- Links to further reading
- Equipment recommendations

### 7. Formula Builder (Future)
- Accessed via the "+" button in the formula carousel
- Create custom formulas with name, description, difficulty, ingredient percentages, and timeline steps
- Saved formulas appear in the carousel alongside built-in formulas
- Entry point: tapping "+" in the formula selector launches the Formula Builder/Editor

## Target Platform
- iPad (primary), all orientations
- iOS 17+

## App Navigation

### Tab Order
The app uses a three-tab navigation structure:
1. **Starter** - Tracker for starter health and feedings
2. **Bake** - Planner and execution
3. **Log** - Bread log for recording completed bakes

## Sources
- Andrew Janjigian, *The Sourdough Lifestyle Workshop Handout* (2022)
- Chad Robertson, *Tartine Bread* (2010)
