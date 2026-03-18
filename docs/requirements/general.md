# General Requirements

## Affiliate Links
- All outbound product links (equipment, reading, buy starters) can include affiliate links
- On by default; toggle in Settings → About Fournil
- When disabled, slightly increased emphasis on Tip section

## Analytics (TODO)
- Privacy-focused solution required
- No individual user tracking — aggregate usage patterns and dropoff only
- Must value privacy and anonymity
- Solution TBD — need to evaluate options

## Data Architecture
- All data structures follow the architecture plan
- Built to support future iCloud Sync
- Use UUID primary keys, avoid non-syncable types
- SwiftData `@Model` for Starters, Feedings, Active Bakes, Bake Records
- `@AppStorage` for preferences
- Static arrays for formulas/glossary

## Save/Cancel Pattern (Global)
- Save button is always the large primary affordance (bottom-right)
- Cancel is a smaller secondary control (text only, left side)
- Design to prevent accidental cancellation (baker's hands may be dirty or occupied)
