# Formulas

The Formulas section provides a browsable view of all built-in baking formulas. It is read-only in V1 — formulas are static data, not user-editable.

---

## Purpose

Allow the baker to explore and compare formulas outside of the active bake planning workflow. The Bake tab is for configuring and starting a specific bake; the Formulas section is for browsing and learning.

---

## Formula List

A simple vertical list of all built-in formulas, one per row.

### Each row
- **Formula name** — Noto Serif 16px
- **Difficulty dots** — 1–4 filled dots, color-coded (sage/primary/clay/burned-red)
- **Timing summary** — Manrope 12px, on-surface-variant (e.g., "24–36 hours")
- **Hydration range** — Manrope 12px (e.g., "75–78%")
- Tap → Formula Detail

### V1 formulas (static data, from `docs/formulas-reference.md`)
1. No-Knead PAL
2. Four-Fold PAL
3. Tartine Country Bread
4. 100% Whole Grain
5. 72h Slow Ferment

### Empty state
Not applicable — built-in formulas are always present.

---

## Formula Detail

A full-screen detail view for a single formula.

### Content
- **Formula name** — Noto Serif display size
- **Description** — Manrope body
- **Difficulty** — dots + label (Beginner / Intermediate / Advanced / Expert)
- **Timing** — total time, active hands-on time
- **Hydration range** and **levain range**
- **Ingredients** — baker's percentages table (reference only, not scaled)
- **Timeline** — vertical step overview (reference only)
- **Technique notes** — any special handling
- **"Use this formula" CTA** — primary gradient button → navigates to Bake section with this formula pre-selected

### Not shown
- Interactive hydration/levain controls (those are in the Bake tab)
- Scaled ingredient weights (those require a dough weight, set in Bake tab)

---

## Scope Notes

- **V1**: Static formula list + detail + "Use this formula" deep link to Bake tab.
- **Post-V1**: Formula Builder (create/edit custom formulas) — see `docs/requirements/deferred.md`.
- The "+" card in the Bake tab formula carousel remains visible with a "Coming soon" popover until Formula Builder ships.

---

## Wireframe
`design/wireframes/16-formulas.svg` — Not started
