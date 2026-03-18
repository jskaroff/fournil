# Wireframe: Find a Starter

Full-screen informational view with links to buy or find a sourdough starter.
Accessed from the "Find a Starter" button on the empty state.

## iPad Landscape Layout

```
┌──────────────────────────────────────────────────────────────────────────────┐
│  [← Back]   Find a Starter                                                  │
│                                                                              │
│                                                                              │
│                          🔍                                                   │
│                                                                              │
│                   There are lots of ways to                                  │
│                   get your hands on a starter.                               │
│                                                                              │
│                                                                              │
│  ┌─────────────────────────────────────────────────────────────────────────┐ │
│  │                                                                         │ │
│  │  🏪  BUY A STARTER ONLINE                                               │ │
│  │                                                                         │ │
│  │  ┌─────────────────────────────────────────────────────┐                │ │
│  │  │  King Arthur Baking — Fresh Sourdough Starter   →   │                │ │
│  │  │  A reliable, active starter shipped to your door.   │                │ │
│  │  └─────────────────────────────────────────────────────┘                │ │
│  │                                                                         │ │
│  │  ┌─────────────────────────────────────────────────────┐                │ │
│  │  │  Cultures for Health — Sourdough Starter       →   │                │ │
│  │  │  Dehydrated starter cultures in several varieties.  │                │ │
│  │  └─────────────────────────────────────────────────────┘                │ │
│  │                                                                         │ │
│  │  ┌─────────────────────────────────────────────────────┐                │ │
│  │  │  Breadtopia — Sourdough Starter                →   │                │ │
│  │  │  Organic, well-established starter culture.         │                │ │
│  │  └─────────────────────────────────────────────────────┘                │ │
│  │                                                                         │ │
│  └─────────────────────────────────────────────────────────────────────────┘ │
│                                                                              │
│  ┌─────────────────────────────────────────────────────────────────────────┐ │
│  │                                                                         │ │
│  │  🤝  ASK THE COMMUNITY                                                  │ │
│  │                                                                         │ │
│  │  ┌─────────────────────────────────────────────────────┐                │ │
│  │  │  r/Sourdough — Reddit Community               →   │                │ │
│  │  │  Ask for a starter share in your area.              │                │ │
│  │  └─────────────────────────────────────────────────────┘                │ │
│  │                                                                         │ │
│  │  ┌─────────────────────────────────────────────────────┐                │ │
│  │  │  r/Breadit — Reddit Bread Community            →   │                │ │
│  │  │  General bread baking community, many share starters.│               │ │
│  │  └─────────────────────────────────────────────────────┘                │ │
│  │                                                                         │ │
│  └─────────────────────────────────────────────────────────────────────────┘ │
│                                                                              │
│  ┌─────────────────────────────────────────────────────────────────────────┐ │
│  │                                                                         │ │
│  │  💡  OTHER IDEAS                                                         │ │
│  │                                                                         │ │
│  │  • Ask a friend who bakes sourdough — most are happy to share!         │ │
│  │  • Check your local bakery — many will sell or give away starter       │ │
│  │  • Visit a local farmers market — artisan bakers often share           │ │
│  │                                                                         │ │
│  └─────────────────────────────────────────────────────────────────────────┘ │
│                                                                              │
│  ──────────────────────────────────────────────────                          │
│                                                                              │
│  Once you have a starter, head back and tap                                  │
│  "I've got a starter" to start tracking.                                    │
│                                                                              │
└──────────────────────────────────────────────────────────────────────────────┘
```

---

## Content Sections

### Buy a Starter Online
- Placeholder links to online starter retailers
- Each link card shows: vendor name, brief description, → arrow
- Links open in Safari
- **Links may include affiliate links** (respects affiliate toggle in Settings)
- TODO: Finalize vendor list and affiliate partnerships

### Ask the Community
- Links to Reddit communities (r/Sourdough, r/Breadit)
- Encouraging text about asking for starter shares
- Links open in Safari

### Other Ideas
- Simple bulleted list of offline options
- Friends, local bakeries, farmers markets

### Footer Note
- Gentle nudge: "Once you have a starter, head back and tap 'I've got a starter' to start tracking."
- No CTA button — user navigates back manually

---

## Component Details

### Link Cards
- Tappable cards with `flourDust` background
- Vendor/community name in bold
- Brief description below in `wheatField` color
- → arrow indicating external link
- Opens in Safari on tap

### Layout
- Scrollable single column
- Max content width ~700px, centered on landscape iPad
- Sections separated by section headers with emoji icons

### Affiliate Links
- Product links in "Buy a Starter Online" section may include affiliate parameters
- Respects the affiliate link toggle in Settings/Preferences
- When affiliate links are off, same links are used without tracking parameters

---

## Interactions

- **Tap a link card** → opens URL in Safari
- **Back button** → returns to Starter empty state
- All links are outbound — no in-app purchasing
