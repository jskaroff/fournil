# Wireframe: Log a Feed

Full form for recording a starter feeding. Presented as a sheet or push navigation
from Starter Details.

## iPad Layout

```
┌────────────────────────────────────────────────────────────────────────┐
│  Log a Feed — Rye Baby                                [Save] [Cancel] │
│                                                                        │
│  ┌─ LEFT (50%) ──────────────────────┐  ┌─ RIGHT (50%) ──────────────┐│
│  │                                    │  │                            ││
│  │  PRESET SHORTCUTS                  │  │  TEMPERATURES              ││
│  │  ┌──────────┐ ┌──────────┐ ┌────┐ │  │                            ││
│  │  │ Standard │ │Overnight │ │Rev.│ │  │  Water temp                ││
│  │  │  2:2:1 ● │ │ 20:20:1  │ │    │ │  │  [  80  ] °F              ││
│  │  └──────────┘ └──────────┘ └────┘ │  │                            ││
│  │                                    │  │  Starter temp (optional)   ││
│  │  FLOUR(S)                          │  │  [  72  ] °F              ││
│  │  ┌──────────────────────────────┐  │  │                            ││
│  │  │ [AP Flour ▼]   [  125  ] g  │  │  │  Ambient temp (optional)  ││
│  │  │ [Rye ▼]        [   25  ] g  │  │  │  [  70  ] °F              ││
│  │  │ [ + Add Flour ]             │  │  │                            ││
│  │  └──────────────────────────────┘  │  │  ──────────────────────   ││
│  │                                    │  │                            ││
│  │  WATER                             │  │  DISCARD                   ││
│  │  Amount:  [  150  ] g              │  │  ☐ Discard was saved       ││
│  │  Type:    [● Tap] [○ Filtered]     │  │  Amount: [  75  ] g       ││
│  │                                    │  │  (optional)               ││
│  │  ──────────────────────            │  │                            ││
│  │                                    │  │  ──────────────────────   ││
│  │  PREVIOUS FEED                     │  │                            ││
│  │  ┌──────────────────────────────┐  │  │  PHOTOS                   ││
│  │  │ [● Chained to last feed]    │  │  │  ┌──────┐ ┌──────┐ ┌───┐ ││
│  │  │    Mar 17, 7:00 AM          │  │  │  │      │ │      │ │ + │ ││
│  │  │                              │  │  │  │ 📷   │ │ 📷   │ │Add│ ││
│  │  │ [○ Missed a feed]           │  │  │  │      │ │      │ │   │ ││
│  │  │    (breaks the chain)       │  │  │  └──────┘ └──────┘ └───┘ ││
│  │  └──────────────────────────────┘  │  │                            ││
│  │                                    │  │  ──────────────────────   ││
│  │  OBSERVATIONS ON LAST FEED         │  │                            ││
│  │  (How did the previous cycle go?)  │  │  TIMESTAMP                 ││
│  │  ┌──────────────────────────────┐  │  │  [● Now]                  ││
│  │  │ Doubled nicely in about 5h, │  │  │  [○ Earlier today]        ││
│  │  │ good aroma, slight tang...  │  │  │     [date/time picker]    ││
│  │  └──────────────────────────────┘  │  │                            ││
│  │                                    │  │                            ││
│  │  NOTES                             │  │                            ││
│  │  ┌──────────────────────────────┐  │  │                            ││
│  │  │ Used KA bread flour + rye...│  │  │                            ││
│  │  └──────────────────────────────┘  │  │                            ││
│  │                                    │  │                            ││
│  └────────────────────────────────────┘  └────────────────────────────┘│
│                                                                        │
└────────────────────────────────────────────────────────────────────────┘
```

---

## Section Details

### Preset Shortcuts
- Three tappable cards: Standard (2:2:1), Overnight (20:20:1), Revival Protocol
- Selecting a preset **auto-fills** flour, water, and starter amounts:
  - Standard: 150g flour, 150g water, 75g starter
  - Overnight: 150g flour, 150g water, 8g starter
  - Revival: follows revival protocol amounts
- User can customize any value after selecting a preset
- Selected preset is highlighted with `goldenCrust` border
- If user modifies values, preset deselects and shows "Custom"

### Flour(s)
- Uses the **Flour Entry Row** shared component (07-shared-components.md)
- Default: one row (type + grams)
- "+ Add Flour" to add additional flour types
- Flour type dropdown: AP, Bread, Rye, Whole Wheat, Other (free-text entry)
- ✕ to remove a row (disabled if only one)
- When a preset is selected, flour type defaults to "AP Flour"

### Water
- Amount in grams
- Type selector: Tap or Filtered (radio buttons)
- Defaults: amount from preset (if selected), type from last feeding

### Previous Feed (Chain)
- Radio selection:
  - **"Chained to last feed"** (default) — shows the date/time of the previous feeding
  - **"Missed a feed"** — breaks the chain, indicating a gap in the feeding log
- When chained, the **Observations** field appears below

### Observations on Last Feed
- Only shown when chained to previous feed
- Free-form text field
- Prompt: "How did the previous cycle go?"
- For noting: growth quality, timing, aroma, activity level
- These observations are stored on the *current* feeding but describe the *previous* cycle

### Temperatures
- **Water temp** — always shown (numeric input with °F/°C)
- **Starter temp** — optional, labeled "(optional)"
- **Ambient temp** — optional, labeled "(optional)"
- All use the Temperature Input shared component

### Discard
- Checkbox: "Discard was saved"
- When checked, shows optional "Amount" field in grams
- Helps track discard for recipes, composting, etc.

### Photos
- Horizontal row of photo thumbnails
- "+ Add" button to take or select photos
- Uses `PhotosPicker` / camera
- Photos are stored with the feeding record

### Timestamp
- Radio selection:
  - **"Now"** (default) — saves with current date/time
  - **"Earlier today"** / custom — reveals date/time picker for past timestamps
- Useful for logging a feeding that happened earlier

### Notes
- Free-form text field for any additional notes
- Examples: flour brand, water source, room conditions

---

## Interactions

- **Selecting a preset** auto-fills flour/water amounts, animates fill
- **Modifying a preset value** deselects the preset badge
- **Toggling chain/break** shows/hides observations field with animation
- **"+ Add Flour"** inserts a new flour row with animation
- **Save** validates required fields (at minimum: one flour with grams, water amount), saves the feeding, and returns to Starter Details
- **Cancel** dismisses with confirmation if form has unsaved changes

---

## Required vs Optional Fields

| Field | Required | Default |
|-------|----------|---------|
| Flour(s) — at least one with type + grams | Yes | From preset or empty |
| Water — amount | Yes | From preset or empty |
| Water — type (tap/filtered) | Yes | Last used or Tap |
| Water temp | No | — |
| Starter temp | No | — |
| Ambient temp | No | — |
| Previous feed chain | Yes | Chained |
| Observations | No | — |
| Discard saved | No | Unchecked |
| Discard grams | No | — |
| Photos | No | — |
| Timestamp | Yes | Now |
| Notes | No | — |
