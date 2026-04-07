# Fournil — Project Plan

A high-level plan governing the design, review, and build of Fournil, an iPad sourdough baking app. Inspired by the workflow used to build [PourCraft](https://github.com/vscarpenter/PourCraft).

---

## How This Project Works

Fournil is built through a conversation between a human (Josh) and an AI agent (Claude). The project moves through distinct phases, each with a clear deliverable and an explicit **approval gate** before advancing. Nothing ships without review. Nothing gets coded without approved designs.

### Roles

| Role | Who | Responsibilities |
|------|-----|-----------------|
| **Product Owner** | Josh | Requirements, priorities, taste, approval at every gate |
| **Architect / Designer** | Claude (Opus) | Planning, architecture, wireframes, prototypes, project plan |
| **Implementer** | Claude (Sonnet) | SwiftUI code, tests, build fixes |
| **Utility** | Claude (Haiku) | Structured data tasks, formatting, simple lookups |

### Key Principles

1. **Design before code.** Every screen is wireframed, reviewed, and prototyped before a line of SwiftUI is written.
2. **Gates, not waterfalls.** Each phase ends with an explicit approval. Rejected work loops back — it never leaks forward.
3. **Agent-readable artifacts.** Designs and specs are structured so the implementing agent can work from them autonomously, with minimal back-and-forth.
4. **Small surface area.** No external dependencies. SwiftUI + SwiftData + iOS 17 APIs only.
5. **Ship the simplest thing.** Deferred features stay deferred. V1 scope is locked.

---

## Project Phases

### Phase 0 — Foundation
**Status: Complete**

Establish the project's requirements, architecture, and tooling.

| Deliverable | Location | Status |
|-------------|----------|--------|
| App requirements (decomposed by feature) | `docs/requirements/` | Done |
| Architecture document | `docs/architecture.md` | Done |
| Data models (Starter, Feeding, Formula, BakeRecord) | `docs/architecture.md` | Done |
| Persistence strategy (AppStorage → SwiftData) | `docs/architecture.md` | Done |
| Navigation map | `design/wireframes/design-spec.md` | Done |
| Reference material (formulas, glossary) | `docs/formulas-reference.md` | Done |
| Design system (colors, typography, components) | `design/wireframes/design-spec.md` | Done |

**Gate: Requirements Review** — Josh reviewed and approved requirements and architecture.

---

### Phase 1 — Design
**Status: In Progress**

Every screen gets a wireframe (SVG) and, for complex screens, an interactive HTML prototype. Designs are iterated until approved.

#### 1a. Wireframes

Low-fidelity SVG layouts at 1194x834 (iPad landscape). Created with the `/wireframe` skill.

| Screen | SVG | Status |
|--------|-----|--------|
| Home (control center) | `00-home.svg` | Not started |
| Bake tab (Plan) | `01-plan-tab.svg` | Done |
| Starter tab (non-empty) | `02-starter-tab.svg` | Done |
| Bread Log tab | `03-bread-log-tab.svg` | Done |
| Bake Tracker | `04-bake-tracker.svg` | Done |
| Settings | `05-settings-screen.svg` | Done |
| Log a Feed (+ variants) | `06-log-a-feed.svg`, `06a/b/c` | Done |
| Bake Detail | `07-bake-detail.svg` | Done |
| Bake Entry Form | `08-bake-entry-form.svg` | Done |
| Starter empty state | `09-starter-empty-state.svg` | Done |
| Starter Details | `11-starter-details.svg` | Done |
| Create a Starter | `13-create-starter.svg` | Done |
| Cultivate Info Sheet | `14-cultivate-info.svg` | Not started |
| Find a Starter | `15-find-a-starter.svg` | Done |
| Formulas | `16-formulas.svg` | Not started |

#### 1b. Interactive Prototypes

High-fidelity HTML prototypes for screens with complex interaction (calculations, timers, progressive disclosure). These validate behavior before SwiftUI implementation.

| Screen | Prototype | Status |
|--------|-----------|--------|
| Bake tab (Plan) | `design/prototypes/plan-tab.html` | Done |
| Bake Tracker | `design/prototypes/bake-tracker.html` | Done |
| Log a Feed | `design/prototypes/log-a-feed.html` | Done |
| Cultivate Info Sheet | — | Not started |

**Gate: Design Review** — Every wireframe and prototype must be reviewed and approved by Josh before coding begins. The design spec (`design/wireframes/design-spec.md`) captures interaction details that SVGs can't show. This document, combined with the SVGs and prototypes, forms the complete design package.

---

### Phase 2 — Architecture Review
**Status: Not Started**

Before writing any Swift code, conduct a focused review of the architecture decisions and their rationale. This is a conversation, not a document — but the outcome is a confirmed (or revised) architecture.

#### What Gets Reviewed

| Decision | Current Choice | Rationale to Confirm |
|----------|---------------|---------------------|
| MVVM with `@Observable` | iOS 17 native, no Combine boilerplate | Follows PourCraft pattern; simpler than older approaches |
| SwiftData for persistence | Apple-native, CloudKit-ready | No Core Data migration overhead; UUID keys ready for sync |
| No external dependencies | Stability, App Review simplicity | Everything needed is in the SDK |
| XcodeGen for project file | Avoids Xcode merge conflicts | Proven in PourCraft; `project.yml` is the source of truth |
| Static formulas (not DB) | Formulas are read-only in V1 | Simpler; Formula Builder deferred to post-V1 |
| Compressed JPEG for photos | SwiftData-compatible, small footprint | Acceptable quality for bread photos; no external image pipeline |
| StoreKit 2 for tips | Modern API, no server needed | Simple consumable IAP |
| `UNUserNotificationCenter` | Standard local notifications | Sufficient for bake step reminders; no push server needed |

#### Review Process
1. Walk through each decision with Josh
2. For any decision Josh questions: present alternatives, trade-offs, and recommendation
3. Confirm or revise. Update `docs/architecture.md` with any changes.
4. Lock architecture for V1 — further changes require a new review

**Gate: Architecture Approval** — Josh confirms the technical approach. Architecture doc updated if needed.

---

### Phase 3 — Scaffolding
**Status: Not Started**

Set up the Xcode project, folder structure, and build pipeline. No feature code — just the skeleton.

#### Deliverables
- [ ] `project.yml` (XcodeGen) with targets, iOS 17 deployment, iPad-only
- [ ] Folder structure matching architecture (Models, Views, Theme, Extensions)
- [ ] `AppColors` and `AppTypography` theme enums from design spec
- [ ] `Color+Hex` extension
- [ ] `NavigationSplitView` shell with 5 sidebar sections (Home, Starter, Bake, Log, Formulas) + Settings footer
- [ ] SwiftData model container setup
- [ ] Test target with one passing placeholder test
- [ ] Project generates and builds clean (`xcodegen generate && xcodebuild`)

**Gate: Clean Build** — Project generates, compiles, and runs on iPad simulator with an empty tab shell.

---

### Phase 4 — Implementation
**Status: Not Started**

Build features in vertical slices. Each slice delivers one working feature area end-to-end (model + views + tests). Order follows dependency chain and user value.

#### How Designs Drive Implementation

Each implementation slice follows this workflow:

```
┌─────────────────────────────────────────────────────┐
│  DESIGN PACKAGE (input to implementing agent)       │
│                                                     │
│  1. Requirements doc    → docs/requirements/{x}.md  │
│  2. Wireframe SVG(s)    → design/wireframes/{x}.svg │
│  3. HTML prototype      → design/prototypes/{x}.html│
│  4. Design spec section → design-spec.md § {x}      │
│  5. Architecture ref    → docs/architecture.md      │
│  6. Formulas ref        → docs/formulas-reference.md│
└─────────────────┬───────────────────────────────────┘
                  │
                  ▼
┌─────────────────────────────────────────────────────┐
│  BUILD PROMPT (generated per slice)                 │
│                                                     │
│  Opus drafts a focused build prompt that:           │
│  - Names the exact files to create/modify           │
│  - References the design package above              │
│  - Specifies models, views, and interactions        │
│  - Includes acceptance criteria                     │
│  - Gets reviewed by Josh before execution           │
│                                                     │
└─────────────────┬───────────────────────────────────┘
                  │
                  ▼
┌─────────────────────────────────────────────────────┐
│  AGENT EXECUTION (Sonnet)                           │
│                                                     │
│  - Reads the build prompt + referenced artifacts    │
│  - Implements the slice                             │
│  - Writes tests                                     │
│  - Builds and runs tests                            │
│                                                     │
└─────────────────┬───────────────────────────────────┘
                  │
                  ▼
┌─────────────────────────────────────────────────────┐
│  REVIEW (Josh)                                      │
│                                                     │
│  - Visual check against wireframe/prototype         │
│  - Functional check against requirements            │
│  - Approve, request changes, or reject              │
│                                                     │
└─────────────────────────────────────────────────────┘
```

#### Implementation Order

| Slice | Feature | Dependencies | Key Screens |
|-------|---------|-------------|-------------|
| **4a** | Theme + shared components | Phase 3 scaffold | Colors, typography, reusable components |
| **4b** | Static formulas + calculator | 4a | Bake tab (01) — formula data, baker's math, DDT |
| **4c** | Starter CRUD + empty state | 4a | Starter empty (09), Create (13), Starter list (02) |
| **4d** | Feeding system | 4c | Log a Feed (06), Starter Details (11) |
| **4e** | Bake planning (full tab) | 4b, 4c | Bake tab (01) — starter selector, timeline, schedule |
| **4f** | Bake Tracker | 4e | Tracker (04) — timers, notifications, persistence |
| **4g** | Bake Log + Detail | 4f | Log tab (03), Detail (07), Entry Form (08) |
| **4h** | Settings + Inspiration | 4a | Settings (05), glossary, tips, about |
| **4i** | Find/Cultivate a Starter | 4c | Find (15), Cultivate info (14) |
| **4j** | Home screen | 4c, 4g | Home (00) — starter overview, monthly stats, recent bakes tail, nav hub |

Each slice has its own gate: **Josh reviews the running feature against the approved designs.**

---

### Phase 5 — Integration & Polish
**Status: Not Started**

After all slices land, focus shifts to cross-cutting concerns and fit-and-finish.

#### Deliverables
- [ ] End-to-end flow testing (create starter → feed → plan bake → track → log)
- [ ] Dark mode audit (not V1 priority, but ensure nothing breaks)
- [ ] Accessibility pass (VoiceOver labels, Dynamic Type)
- [ ] iPad multitasking / rotation behavior
- [ ] Performance check (SwiftData queries, photo loading)
- [ ] StoreKit 2 tip jar integration (code — products configured in Phase 7)
- [ ] Affiliate link infrastructure (accounts set up in Phase 7)
- [ ] App icon and launch screen (final assets from Phase 6)

**Gate: V1 Feature Complete** — All features work, all slices approved, no known blockers.

---

### Phase 6 — Branding & Identity
**Status: Not Started**

Finalize the app's public identity before any store or marketing assets are created.

- [ ] Finalize app name (confirm "Fournil" or choose alternative; check App Store availability and domain availability together)
- [ ] Purchase domain name
- [ ] App icon design (multiple concepts → pick one; export all required sizes)
- [ ] Launch screen design

**Gate: Name & Icon Locked** — Josh approves the final name and icon. Domain is secured.

---

### Phase 7 — Financial & Legal Setup
**Status: Not Started**

The tip jar (StoreKit 2 consumable IAP) and affiliate links require accounts and agreements to be in place before they can be tested or go live.

- [ ] Apple Developer Program membership (if not already active)
- [ ] App Store Connect: create app record, configure bundle ID
- [ ] Paid Apps Agreement signed in App Store Connect (required for IAP)
- [ ] StoreKit 2 tip jar products created in App Store Connect ($1, $5, $10 consumables)
- [ ] Test tips in sandbox environment
- [ ] Affiliate program sign-ups for any outbound product links (equipment, starter vendors)
- [ ] Bank account / tax info configured in App Store Connect for payouts
- [ ] Privacy policy published (hosted on app website or a simple page — no tracking, no analytics in V1)

**Gate: Money Plumbing Works** — Sandbox tip purchases complete successfully. Affiliate links configured. Legal pages live.

---

### Phase 8 — Release Prep
**Status: Not Started**

- [ ] TestFlight beta build (Josh's devices)
- [ ] Real-world bake test (use the app through a full bake cycle)
- [ ] Bug fixes from testing
- [ ] App Store screenshots (iPad, all required sizes; designed to showcase key flows)
- [ ] App Store metadata (subtitle, description, keywords, category)
- [ ] App preview video (optional — short screen recording of a bake flow)
- [ ] Submit to App Store Review

**Gate: Submitted** — App is in App Store review queue.

---

### Phase 9 — Marketing & Web Presence
**Status: Not Started**

A simple marketing website and social presence to support the launch.

- [ ] Design and build a single-page marketing site (app name, tagline, screenshots, App Store badge, brief feature overview)
- [ ] Deploy website to purchased domain (Vercel or similar)
- [ ] Open Graph / social meta tags (so link shares look good)
- [ ] Social media assets (Bluesky post card, share images)
- [ ] Launch announcement (Bluesky, relevant communities)
- [ ] App Store link added to website once live

**Gate: Live** — App is on the App Store. Website is deployed. Launch announced.

---

## What's NOT in V1

These features are intentionally deferred. The architecture supports them, but they will not be built until after V1 ships.

- Formula Builder (creating/editing custom formulas — browsing static formulas is V1)
- Feeding history time graph
- "Share Your Bread" social feature
- Voice notes on Bake Tracker
- Badges & Streaks
- Analytics
- iCloud Sync
- Dark mode (design, not just "doesn't break")

---

## Reference Documents

| Document | Purpose |
|----------|---------|
| `docs/requirements/` | Feature requirements (source of truth) |
| `docs/architecture.md` | Technical architecture and data models |
| `docs/formulas-reference.md` | Baker's math formulas and reference data |
| `design/wireframes/*.svg` | Visual layouts for every screen |
| `design/wireframes/design-spec.md` | Interaction behavior, states, component details |
| `design/prototypes/*.html` | Interactive prototypes for complex screens |
| `CLAUDE.md` | Agent instructions for working in this repo |

---

## Revision History

| Date | Change |
|------|--------|
| 2026-03-19 | Initial project plan created |
| 2026-03-19 | Added phases 6-9: branding, financial/legal setup, release prep, marketing |
| 2026-03-23 | Adopted Stitch "Living Ferment" design system; added Home screen requirement; rethought navigation to Home-centered NavigationSplitView (hybrid); promoted Formulas from deferred to V1 (read-only); added 00-home.svg, 16-formulas.svg wireframe rows; added Phase 4j (Home impl) |
