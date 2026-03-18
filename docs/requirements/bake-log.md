# Bake Log

## Grid View
- Reverse chronological photo grid of all completed bakes (newest first)
- **Filter bar** at top: filter by Starter, filter by Formula
- Each card: date, formula name, photo, overall rating
- Layout: 4 columns landscape, 3 portrait
- "+ New Entry" for manual logging

## Bake Detail
- **Photo carousel**: horizontal scroll with affordance to add more photos
- All metadata displayed with inline edit capabilities
- **Ratings**: overall, crumb, crust, flavor, rise (1–5 stars each)
- Formula details, dough weight, bake details (oven temp, time)
- Notes and crumb description
- **"Bake this Again"** button → navigates to Plan tab with all values preset (formula, starter, weight, variant)
- **System Share button** (↗) — iOS share sheet with photo + formula + rating + notes
- **"Share Your Bread" CTA** — on tap, shows "Coming soon" popover
  - TODO: Concept how to encourage bakers to share with friends, family, and community

## Bake Entry Form
- Pre-populated from completed bake tracker (if coming from that flow)
- Fields: photos, formula, starter, weight, variant (if Four-Fold), ratings, bake details, notes, crumb description
- Required: date (auto-filled), overall rating
- Optional: everything else
