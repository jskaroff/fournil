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
| Preferences (temp unit, default formula, affiliate toggle) | `@AppStorage` | Phase 0 |
| Built-in formulas, glossary terms | Static Swift arrays | Phase 1 |
| Starters | SwiftData `@Model` | Phase 2 |
| Feedings (with photos) | SwiftData `@Model` | Phase 2 |
| Active bake state | SwiftData `@Model` | Phase 4 |
| Bake records + photos | SwiftData `@Model` | Phase 5 |

### Data Models

#### Starter
```swift
@Model class Starter {
    var id: UUID
    var name: String
    var source: String?
    var starterDescription: String?
    var createdAt: Date

    @Relationship(deleteRule: .cascade, inverse: \Feeding.starter)
    var feedings: [Feeding]

    @Relationship(inverse: \BakeRecord.starter)
    var bakes: [BakeRecord]

    // Derived: health status based on time since last feeding
    // Thriving (< 12h), Needs Feeding (1-7 days), Needs Revival (> 7 days)
}
```

#### Feeding
```swift
@Model class Feeding {
    var id: UUID
    var timestamp: Date
    var flours: [FlourEntry]       // Codable array
    var waterGrams: Double
    var waterType: WaterType       // .tap, .filtered
    var waterTemp: Double?
    var existingStarterTemp: Double?
    var ambientTemp: Double?
    var notes: String?
    var discardSaved: Bool
    var discardGrams: Double?
    var previousFeeding: Feeding?  // Optional pointer (chain)
    var chainBroken: Bool          // true = user missed a feed
    var observations: String?      // Notes about previous cycle outcome
    var photos: [Data]             // Compressed JPEG

    var starter: Starter
}
```

#### FlourEntry (Codable, embedded in Feeding)
```swift
struct FlourEntry: Codable, Identifiable {
    var id: UUID
    var type: String    // "AP", "Bread", "Rye", "Whole Wheat", etc.
    var grams: Double
}
```

#### WaterType
```swift
enum WaterType: String, Codable {
    case tap
    case filtered
}
```

#### Formula (Static)
```swift
struct Formula: Identifiable {
    let id: String
    let name: String
    let difficulty: Difficulty        // .beginner, .intermediate, .advanced, .expert
    let timingDescription: String
    let technique: String
    let description: String
    let ingredients: [Ingredient]
    let timelineSteps: [TimelineStep]
    let instructions: [String]        // Step-by-step recipe instructions
    let hydrationRange: ClosedRange<Double>?  // Interactive for Four-Fold only
    let levainRange: ClosedRange<Double>?     // Interactive for Four-Fold only
    let isBuiltIn: Bool
}
```

#### BakeRecord
```swift
@Model class BakeRecord {
    var id: UUID
    var date: Date
    var formulaID: String
    var variant: String?              // e.g., "75/25" for Four-Fold
    var doughWeightGrams: Double
    var photos: [Data]                // Compressed JPEG
    var notes: String?
    var crumbDescription: String?
    var ovenTemp: Double?
    var bakeTimeMinutes: Int?

    // Ratings (1-5)
    var ratingOverall: Int?
    var ratingCrumb: Int?
    var ratingCrust: Int?
    var ratingFlavor: Int?
    var ratingRise: Int?

    var starter: Starter?             // Which starter was used
}
```

### Theme System
- `AppColors` enum with adaptive helpers: `background(for:)`, `surface(for:)`, etc.
- `AppTypography` enum: serif for titles, sans for body
- `Color+Hex` extension for hex color parsing

### Navigation
- TabView with 3 tabs: Starter, Bake, Log
- Settings accessible via ⚙️ gear icon (top-right, any tab)
- Starter tab: conditional empty/non-empty state → Starter Details, Log a Feed, Create a Starter (navigation stack)
- Bake Tracker: full-screen flow from Plan tab
- Bake Detail: push from Log grid

### Notifications
- `UNUserNotificationCenter` for bake step reminders (Phase 4)
- Request permission on first bake start
- Support snooze via notification actions

### Photos
- SwiftUI `PhotosPicker` (Phase 5)
- Store as compressed JPEG Data in SwiftData
- Used in: Feedings, Bake Records

### iCloud Sync (Future)
- All SwiftData models use UUID primary keys
- Avoid non-syncable types
- CloudKit-compatible schema design
- Implementation deferred post-V1

### Analytics (TODO)
- Privacy-focused, aggregate only
- No individual user tracking
- Solution TBD

## Model Assignments
- **Opus:** Planning, design, architecture
- **Sonnet:** Implementation (writing code)
- **Haiku:** Simple structured tasks
