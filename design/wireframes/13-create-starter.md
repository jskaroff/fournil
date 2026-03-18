# Wireframe: Create a Starter

Simple form to register a new starter. Presented as a sheet from the empty state
onboarding or the "+ New Starter" button.

## iPad Layout

```
┌────────────────────────────────────────────────────────────────┐
│  Create a Starter                             [Save]  [Cancel] │
│                                                                │
│                                                                │
│         🫙                                                      │
│    Give your starter a name                                    │
│                                                                │
│                                                                │
│  NAME *                                                        │
│  ┌──────────────────────────────────────────────────────┐      │
│  │  Rye Baby                                            │      │
│  └──────────────────────────────────────────────────────┘      │
│                                                                │
│  SOURCE                                                        │
│  ┌──────────────────────────────────────────────────────┐      │
│  │  Friend (Sarah, 2024)                                │      │
│  └──────────────────────────────────────────────────────┘      │
│  Where did your starter come from?                             │
│  e.g., "Friend", "King Arthur", "Cultivated from scratch"     │
│                                                                │
│  DESCRIPTION                                                   │
│  ┌──────────────────────────────────────────────────────┐      │
│  │  My original rye starter, maintained since 2024.     │      │
│  │  Robust and reliable.                                │      │
│  └──────────────────────────────────────────────────────┘      │
│  Tell us about your starter — anything that makes it special.  │
│                                                                │
└────────────────────────────────────────────────────────────────┘
```

---

## Fields

| Field | Required | Placeholder / Help Text |
|-------|----------|------------------------|
| **Name** | Yes | "Rye Baby" — must be unique among user's starters |
| **Source** | No | "Friend", "King Arthur", "Cultivated from scratch" |
| **Description** | No | "Tell us about your starter — anything that makes it special." |

## Interactions

- **Name** is the only required field. Save is disabled until name is non-empty.
- **Source** and **Description** are optional free-text fields with helpful placeholder text.
- **Save** creates the starter and navigates to the next step based on the entry path:
  - From "I've got a starter" → **Log your first feed** (12-log-a-feed.md)
  - From "Cultivate a new starter" → **Cultivate Info Sheet** (14-cultivate-info-sheet.md)
  - From "+ New Starter" button → **Starter Details** (11-starter-details.md)
- **Cancel** dismisses with confirmation if name has been entered.

## Component Details

- Centered layout, max-width ~500px
- Jar emoji header, friendly prompt
- Text fields use standard iOS styling
- Helper text below fields in `wheatField` color, smaller font
- Save button uses `goldenCrust` accent when enabled, dimmed when disabled
