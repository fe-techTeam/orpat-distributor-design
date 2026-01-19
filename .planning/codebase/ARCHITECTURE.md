# Architecture

**Analysis Date:** 2026-01-19

## Pattern Overview

**Overall:** Static Frontend Prototype (Monolithic Single-File Design)

**Key Characteristics:**
- Single HTML file containing all 21 screen designs
- Embedded CSS styling (no external stylesheets)
- Mobile-first design (375x812px iPhone frame mockup)
- No JavaScript logic (presentation-only)
- API contract defined separately in Postman collection

## Layers

**Presentation Layer:**
- Purpose: Display all UI screens for the distributor mobile app
- Contains: HTML structure, embedded CSS, inline styles
- Location: `index.html` (4152 lines)
- Depends on: External images from `orpatgroup.com` and local `images/`
- Used by: Direct browser viewing

**Design System Layer:**
- Purpose: Brand consistency via CSS custom properties
- Contains: Color variables, typography, spacing patterns
- Location: `index.html` (lines 80-85 for CSS variables)
- Variables: `--orpat-red: #c41e3a`, `--orpat-dark: #1a1a2e`, `--orpat-blue: #0066cc`, `--orpat-gold: #d4a056`
- Used by: All UI components

**Asset Layer:**
- Purpose: Product images for UI mockups
- Contains: 27 product images (clocks, calculators, fans, appliances)
- Location: `images/` directory
- Used by: HTML image tags throughout screens

**API Contract Layer:**
- Purpose: Define backend integration points
- Contains: 21+ REST endpoints with authentication patterns
- Location: `Distributor APP.postman_collection.json`
- Pattern: Bearer token authentication, RESTful structure

## Data Flow

**Current State (Static Prototype):**

1. User opens `index.html` in browser
2. Browser renders all 21 screens in phone frame mockups
3. CSS styling applied from embedded `<style>` block
4. Images loaded from local `images/` and external CDN
5. No interactivity (visual prototype only)

**Planned Backend Integration (per Postman specs):**

1. Mobile app sends HTTP request with Bearer token
2. API validates authentication
3. Backend processes request (products, orders, schemes)
4. JSON response returned
5. Mobile app updates UI with data

**State Management:**
- None currently (static HTML)
- Planned: Backend-driven via REST API

## Key Abstractions

**Screen Containers:**
- Purpose: Represent distinct app screens/pages
- Examples: Screen A (Home), Screen E (Checkout), Screen K (Orders)
- Pattern: `.phone-frame > .screen` structure
- Location: 21 instances throughout `index.html`

**Component Classes:**
- Purpose: Reusable UI patterns via CSS classes
- Examples: `.product-card`, `.checkout-item`, `.order-card`, `.scheme-card`
- Pattern: BEM-inspired kebab-case naming
- Location: CSS definitions in `index.html` (lines 10-1269)

**Navigation Elements:**
- Purpose: App navigation structure
- Examples: `.header`, `.bottom-nav`, `.sidebar`
- Pattern: Fixed positioning with z-index layering
- Used across: All screen designs

## Entry Points

**Browser Entry:**
- Location: `index.html`
- Triggers: File open in browser or HTTP request
- Responsibilities: Render all 21 screen mockups in phone frames

**API Testing Entry:**
- Location: `Distributor APP.postman_collection.json`
- Triggers: Postman import and execution
- Responsibilities: Test backend API endpoints

## Error Handling

**Strategy:** Not applicable (static HTML)

**Planned (per API contract):**
- HTTP status codes for API responses
- No client-side error handling defined yet

## Cross-Cutting Concerns

**Styling:**
- Embedded CSS in `<style>` block
- CSS custom properties for brand colors
- 737+ inline styles for component variations

**Typography:**
- Google Fonts Inter (400, 500, 600, 700, 800 weights)
- Loaded via `fonts.googleapis.com`

**Responsive Design:**
- Media query at 800px breakpoint
- Phone frame adapts to smaller screens

---

*Architecture analysis: 2026-01-19*
*Update when major patterns change*
