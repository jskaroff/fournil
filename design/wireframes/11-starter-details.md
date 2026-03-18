# Wireframe: Starter Details

Full details view for a single starter. Accessed by tapping a starter card
from the Starter List.

## iPad Landscape Layout

```
┌──────────────────────────────────────────────────────────────────────────────┐
│  [← Starters]   Rye Baby                              [Log a Feed ▶]       │
│                                                                              │
│  ┌─ LEFT COLUMN (40%) ──────────────────┐  ┌─ RIGHT COLUMN (60%) ──────────┐│
│  │                                      │  │                                ││
│  │       ┌───────────────────┐          │  │  FEEDING HISTORY               ││
│  │       │                   │          │  │                                ││
│  │       │    [Last feed     │          │  │  ┌────────────────────────────┐││
│  │       │     photo]        │          │  │  │ Mar 18, 8:30 AM           │││
│  │       │                   │          │  │  │ Standard (2:2:1)          │││
│  │       └───────────────────┘          │  │  │ AP 125g + Rye 25g        │││
│  │                                      │  │  │ Water: 150g (filtered)    │││
│  │       🟢 THRIVING                    │  │  │ Water temp: 80°F          │││
│  │       Fed 6 hours ago                │  │  │ Peaked at 4.5h            │││
│  │                                      │  │  │ Discard: saved, ~75g      │││
│  │  ──────────────────────              │  │  │ 📷 2 photos               │││
│  │                                      │  │  │ "Doubled nicely, good     │││
│  │  ABOUT                               │  │  │  aroma, slight tang"      │││
│  │  Source: Friend (Sarah, 2024)        │  │  └────────────────────────────┘││
│  │  "My original rye starter,           │  │  ┌────────────────────────────┐││
│  │   maintained since 2024.             │  │  │ Mar 17, 7:00 AM           │││
│  │   Robust and reliable."             │  │  │ Standard (2:2:1)          │││
│  │                                      │  │  │ AP 125g + Rye 25g        │││
│  │  ──────────────────────              │  │  │ Water: 150g (tap)         │││
│  │                                      │  │  │ Peaked at 5h              │││
│  │  BAKES WITH THIS STARTER             │  │  │ Observations: "Grew well, │││
│  │  ┌──────────────────────────┐        │  │  │  ready by 12:00 PM"       │││
│  │  │ Mar 15 · No-Knead · ★★★★☆│        │  │  └────────────────────────────┘││
│  │  │ Mar 10 · 4-Fold   · ★★★★★│        │  │  ┌────────────────────────────┐││
│  │  │ Mar 5  · No-Knead · ★★★☆☆│        │  │  │ Mar 16, 9:00 PM           │││
│  │  └──────────────────────────┘        │  │  │ Overnight (20:20:1)       │││
│  │                                      │  │  │ AP 150g                   │││
│  │                                      │  │  │ Water: 150g (filtered)    │││
│  │                                      │  │  └────────────────────────────┘││
│  │                                      │  │                                ││
│  │                                      │  │  ...more entries...            ││
│  │                                      │  │                                ││
│  └──────────────────────────────────────┘  └────────────────────────────────┘│
│                                                                              │
├────────────────┬────────────────┬──────────────────────────────────────────┤
│  Starter (●)   │      Bake      │     Log                                  │
└────────────────┴────────────────┴──────────────────────────────────────────┘
```

---

## Left Column

### Last Feed Photo
- Large photo from the most recent feeding
- Placeholder image if no photos have been taken
- Tappable to view full-screen

### Health Status
- Color-coded status: 🟢 THRIVING / 🟡 NEEDS FEEDING / 🔴 NEEDS REVIVAL
- Time since last feed as live countdown: "Fed 6 hours ago"
- Updates in real time while the view is open

### About Section
- **Source**: where the starter came from
- **Description**: user's free-form notes about the starter
- Edit button to modify these fields

### Bakes with This Starter
- Compact list of completed bakes that used this starter
- Each row: date, formula name, rating
- Tap a row → navigates to Bake Detail (in Log tab)
- Empty state: "No bakes yet with this starter"

---

## Right Column

### Feeding History
- Scrollable list of all feedings, most recent first
- Each feeding card shows:
  - **Timestamp**: date and time
  - **Preset used** (if any): "Standard (2:2:1)", "Overnight (20:20:1)", or "Custom"
  - **Flour(s)**: type and amount for each flour (e.g., "AP 125g + Rye 25g")
  - **Water**: amount, type (tap/filtered)
  - **Water temperature** (if recorded)
  - **Peak time** (if recorded)
  - **Discard info** (if recorded): "saved, ~75g" or "discarded"
  - **Photo count**: "📷 2 photos" (tappable to view)
  - **Notes** (if any): truncated to 2 lines
  - **Observations on previous cycle** (if chained and recorded)
- **Chain indicator**: a thin connecting line between chained feedings. A break in
  the line indicates a missed/unchained feeding.

### Feeding History — Future Enhancement
Time graph visualization of feeding history (deferred to fast follow).
V1 ships with the list view only.

---

## Top Bar

### Back Button
- "← Starters" returns to the Starter List

### "Log a Feed" Button
- Prominent button, top-right
- Opens the **Log a Feed** form (12-log-a-feed.md)
- Pre-selects this starter

---

## Interactions

- **"Log a Feed"** → opens feeding form for this starter
- **Tap a feeding card** → expands to show full details (or push to detail view)
- **Tap photo count** → opens photo gallery for that feeding
- **Tap a bake row** → navigates to Bake Detail
- **Long-press a feeding** → context menu: "Delete Feeding" (with confirmation)
- **Edit (About section)** → inline edit for source and description
- **Pull to refresh** → updates health indicator and time-since-feed

---

## iPad Portrait Layout

Single-column stack:
1. Last feed photo (full-width, shorter height)
2. Health status + time since last feed
3. About section
4. "Log a Feed" button (full-width)
5. Bakes with this starter
6. Feeding history list
