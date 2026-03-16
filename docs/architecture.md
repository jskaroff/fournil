# Fournil - Architecture

## Reference: PourCraft
Architecture follows PourCraft (github.com/vscarpenter/PourCraft) exactly where applicable.

## Stack
- SwiftUI + iOS 17+ (`@Observable` macro)
- XcodeGen for project generation
- No external dependencies
- Swift Testing framework
- OSLog for logging

## Patterns

### MVVM with @Observable
- Models are `@Observable` classes holding data + business logic
- Views are SwiftUI structs that read from models
- Views never do math -- they display what the model tells them
- `@Bindable` in views to create bindings from `@Observable` properties

### Persistence
| Data | Storage | When Introduced |
|------|---------|----------------|
| Preferences (temp unit, default formula) | `@AppStorage` | Phase 0 |
| Built-in formulas, glossary terms | Static Swift arrays | Phase 1 |
| Starter feeding log | SwiftData `@Model` | Phase 2 |
| Active bake state | SwiftData `@Model` | Phase 4 |
| Bake records + photos | SwiftData `@Model` | Phase 5 |

### Theme System
- `AppColors` enum with adaptive helpers: `background(for:)`, `surface(for:)`, etc.
- `AppTypography` enum: serif for titles, sans for body
- `Color+Hex` extension for hex color parsing

### Navigation
- TabView with 5 tabs (Calculator, Starter, Planner, Bread Log, Inspiration)
- Bake Tracker is presented as a full-screen flow from the Planner

### Notifications
- `UNUserNotificationCenter` for bake step reminders (Phase 4)
- Request permission on first bake start
- Support snooze via notification actions

### Photos
- SwiftUI `PhotosPicker` (Phase 5)
- Store as compressed JPEG Data in SwiftData

## Model Assignments
- **Opus:** Planning, design, architecture
- **Sonnet:** Implementation (writing code)
- **Haiku:** Simple structured tasks
