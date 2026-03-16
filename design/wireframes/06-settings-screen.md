# Wireframe: Settings Screen

Accessed via ⚙️ gear icon in the navigation bar (top-right, available from any tab).
Presented as a navigation push or sheet.

## iPad Layout

```
┌──────────────────────────────────────────────────────────────────────────────┐
│  [← Back]  Settings                                                          │
│                                                                              │
│  ┌─ LEFT: MENU (35%) ──────────────────┐  ┌─ RIGHT: DETAIL (65%) ─────────┐ │
│  │                                      │  │                               │ │
│  │  ┌──────────────────────────────┐    │  │  (Selected section content    │ │
│  │  │ ✨ Inspiration               │    │  │   appears here)               │ │
│  │  └──────────────────────────────┘    │  │                               │ │
│  │  ┌──────────────────────────────┐    │  │                               │ │
│  │  │ 🧪 Formula Builder          │    │  │                               │ │
│  │  │    Coming Soon               │    │  │                               │ │
│  │  └──────────────────────────────┘    │  │                               │ │
│  │  ┌──────────────────────────────┐    │  │                               │ │
│  │  │ 🔧 Preferences              │    │  │                               │ │
│  │  └──────────────────────────────┘    │  │                               │ │
│  │  ┌──────────────────────────────┐    │  │                               │ │
│  │  │ 🍳 Equipment Guide          │    │  │                               │ │
│  │  └──────────────────────────────┘    │  │                               │ │
│  │  ┌──────────────────────────────┐    │  │                               │ │
│  │  │ ℹ️ About Fournil             │    │  │                               │ │
│  │  └──────────────────────────────┘    │  │                               │ │
│  │                                      │  │                               │ │
│  └──────────────────────────────────────┘  └───────────────────────────────┘ │
│                                                                              │
└──────────────────────────────────────────────────────────────────────────────┘
```

---

## Section: Inspiration

```
  ┌─ INSPIRATION ────────────────────────────────────────────────┐
  │                                                              │
  │  SOURCES                                                     │
  │                                                              │
  │  ┌────────────────────────────────────────────────────┐      │
  │  │  Andrew Janjigian                                  │      │
  │  │  The Sourdough Lifestyle                           │      │
  │  │  wordloaf.substack.com · @wordloaf                 │      │
  │  └────────────────────────────────────────────────────┘      │
  │  ┌────────────────────────────────────────────────────┐      │
  │  │  Chad Robertson                                    │      │
  │  │  Tartine Bread                                     │      │
  │  │  tartinebakery.com                                 │      │
  │  └────────────────────────────────────────────────────┘      │
  │                                                              │
  │  FURTHER READING                                             │
  │  • On desired dough temperatures (DDT)                       │
  │  • Care and feeding of a sourdough starter                   │
  │  • More on care and feeding of a sourdough starter           │
  │  • That Levain Feeling                                       │
  │  • On Dutch oven baking                                      │
  │  • No-knead PAL recipe template                              │
  │  • Quarantinystarter 2.0                                     │
  │                                                              │
  │  SOURDOUGH GLOSSARY                                          │
  │  ┌────────────────────────────────────────────────────┐      │
  │  │ ▶ Autolyse                                        │      │
  │  ├────────────────────────────────────────────────────┤      │
  │  │ ▶ Bulk Proof                                      │      │
  │  ├────────────────────────────────────────────────────┤      │
  │  │ ▶ Cold-Proofing                                   │      │
  │  ├────────────────────────────────────────────────────┤      │
  │  │ ▶ DDT                                             │      │
  │  ├────────────────────────────────────────────────────┤      │
  │  │ ...                                               │      │
  │  └────────────────────────────────────────────────────┘      │
  └──────────────────────────────────────────────────────────────┘
```

---

## Section: Formula Builder (Future Phase)

```
  ┌─ FORMULA BUILDER ────────────────────────────────────────────┐
  │                                                              │
  │       🧪                                                     │
  │                                                              │
  │    Formula Builder                                           │
  │    Coming in a future update                                 │
  │                                                              │
  │    Create your own custom formulas with:                     │
  │    • Custom flour blends and ratios                          │
  │    • Adjustable hydration and levain                         │
  │    • Baker's percentage calculations                         │
  │    • Save and reuse your recipes                             │
  │                                                              │
  └──────────────────────────────────────────────────────────────┘
```

When built (later phase), the Formula Builder will allow:
- Add custom ingredients (name + baker's %)
- Set whether each ingredient is a flour (contributes to 100% base)
- Set hydration range
- Set levain range and type
- Preview calculated weights at a given dough weight
- Save as a named custom formula that appears alongside built-in formulas in Plan tab

---

## Section: Preferences

```
  ┌─ PREFERENCES ────────────────────────────────────────────────┐
  │                                                              │
  │  Temperature Unit                                            │
  │  [● Fahrenheit]  [○ Celsius]                                 │
  │                                                              │
  │  Default Dough Weight                                        │
  │  [ - ]    900g     [ + ]                                     │
  │                                                              │
  │  Default Formula                                             │
  │  [No-Knead PAL ▼]                                            │
  │                                                              │
  └──────────────────────────────────────────────────────────────┘
```

---

## Section: Equipment Guide

```
  ┌─ EQUIPMENT GUIDE ────────────────────────────────────────────┐
  │                                                              │
  │  Recommended equipment for sourdough baking at home.         │
  │  Based on Andrew Janjigian's recommendations.                │
  │                                                              │
  │  ESSENTIAL                                                   │
  │  • Kitchen scale (to 0.1g precision)                         │
  │  • Dutch oven or Challenger bread pan (7qt+)                 │
  │  • Instant-read thermometer                                  │
  │  • Bench scraper                                             │
  │  • Lame or razor blade (for scoring)                         │
  │  • Banneton / proofing basket (round or oval)                │
  │  • Parchment paper                                           │
  │                                                              │
  │  HELPFUL                                                     │
  │  • Straight-sided container (for bulk proof)                 │
  │  • Dough whisk                                               │
  │  • Baking stone or steel                                     │
  │  • Cooling rack                                              │
  │                                                              │
  └──────────────────────────────────────────────────────────────┘
```

---

## Section: About Fournil

```
  ┌─ ABOUT FOURNIL ──────────────────────────────────────────────┐
  │                                                              │
  │           🍞                                                  │
  │         Fournil                                              │
  │        Version 1.0                                           │
  │                                                              │
  │  "Fournil" is French for bakehouse — the room                │
  │  where bread is made.                                        │
  │                                                              │
  │  Built with love by a home baker.                            │
  │                                                              │
  │  ─────────────────────────────────────────                   │
  │                                                              │
  │  ┌────────────────────────────────────────────────────┐      │
  │  │  ☕  Support the Developer                          │      │
  │  │                                                    │      │
  │  │  If Fournil helps your baking, consider buying     │      │
  │  │  the developer a coffee (or a bag of flour).       │      │
  │  │                                                    │      │
  │  │  [ Tip $3 ]  [ Tip $5 ]  [ Tip $10 ]             │      │
  │  └────────────────────────────────────────────────────┘      │
  │                                                              │
  └──────────────────────────────────────────────────────────────┘
```

---

## Component Details

### Navigation Pattern
- iPad: split-view (sidebar + detail) within the Settings screen
- List items in sidebar, selected item's content in detail pane
- "Formula Builder" row shows "Coming Soon" badge, dimmed

### Tip Bucket
- Three tier options ($3, $5, $10)
- Uses StoreKit 2 for in-app purchases (or tip jar via App Store)
- Thank-you animation on successful tip

### Glossary
- Same expandable card component from shared components
- Alphabetically sorted
- All 15 terms from Janjigian's glossary

### Interactions
- Sidebar list items are tappable, detail pane updates
- External links open in Safari
- Preferences changes take effect immediately via `@AppStorage`
- Tip buttons trigger StoreKit purchase flow
