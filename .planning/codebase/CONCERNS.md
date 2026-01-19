# Codebase Concerns

**Analysis Date:** 2026-01-19

## Tech Debt

**Massive Inline Styles (737+ occurrences):**
- Issue: Heavy reliance on inline `style=""` attributes instead of CSS classes
- File: `index.html` (throughout lines 1272-4152)
- Why: Rapid prototyping, quick visual iterations
- Impact: Difficult to maintain consistency, no CSS caching, violates separation of concerns
- Fix approach: Extract common inline styles to CSS classes, use component-based styling

**Single-File Architecture:**
- Issue: All 4152 lines in one HTML file
- File: `index.html`
- Why: Simple prototype without build system
- Impact: Hard to navigate, no code reuse, merge conflicts likely
- Fix approach: When converting to production, split into components/modules

**Mixed Local and External Images:**
- Issue: 27 local images in `images/` but HTML also references external CDN
- Files: `index.html` (lines referencing `orpatgroup.com`), `images/` directory
- Why: Inconsistent asset sourcing during development
- Impact: External URLs may break, inconsistent loading behavior
- Fix approach: Standardize on local images or document CDN strategy

## Known Bugs

**No known runtime bugs** (static HTML prototype)

## Security Considerations

**Hardcoded Test Credentials in Version Control:**
- Risk: CRITICAL - Login credentials exposed in repository
- File: `Distributor APP.postman_collection.json` (lines 29-35)
- Exposed: `azamgarhdistributor@orpatgroup.com` / `06051979`
- Current mitigation: None
- Recommendations:
  1. Immediately rotate this account password
  2. Remove credentials from git history using `git filter-branch`
  3. Add Postman collections to `.gitignore`
  4. Create `.postman_environment.example.json` template instead

**No .env.example Template:**
- Risk: Future developers may commit actual credentials
- Current mitigation: None (no sensitive config currently needed)
- Recommendations: Create environment template when adding backend integration

## Performance Bottlenecks

**External Image Loading:**
- Problem: Some images load from `orpatgroup.com` CDN
- File: `index.html` (multiple image src attributes)
- Measurement: Dependent on external server response time
- Cause: External URL dependencies instead of local assets
- Improvement path: Use local images from `images/` directory consistently

**Large Single-File Load:**
- Problem: 4152-line HTML file loaded at once
- File: `index.html` (214KB uncompressed)
- Measurement: ~200KB+ initial load
- Cause: All 21 screens in single file for prototype viewing
- Improvement path: Acceptable for prototype; split for production app

## Fragile Areas

**CSS Custom Properties:**
- File: `index.html` (lines 80-85)
- Why fragile: All brand styling depends on 4 CSS variables
- Common failures: Typos in variable names, missing fallbacks
- Safe modification: Always test in browser after color changes
- Test coverage: Manual visual inspection only

**Phone Frame Styling:**
- File: `index.html` (lines 16-78)
- Why fragile: Complex CSS for phone mockup appearance (notch, borders)
- Common failures: Border-radius changes break notch simulation
- Safe modification: Test on multiple screen sizes
- Test coverage: Manual visual inspection only

## Scaling Limits

**Browser Rendering:**
- Current capacity: Handles all 21 screens reasonably
- Limit: Adding many more screens may slow rendering
- Symptoms at limit: Sluggish scrolling, high memory usage
- Scaling path: Split into separate files or lazy-load sections

**Image Assets:**
- Current capacity: 27 images (~1.7MB total)
- Limit: Browser caching handles current volume
- Scaling path: Image optimization (WebP), lazy loading for production

## Dependencies at Risk

**Google Fonts External Dependency:**
- Risk: External service dependency for typography
- Impact: Fallback to system fonts if Google Fonts unavailable
- Migration plan: Consider self-hosting Inter font files

**External Product Images:**
- Risk: `orpatgroup.com` CDN availability
- Impact: Broken images if CDN changes or goes down
- Migration plan: Use local `images/` directory exclusively

## Missing Critical Features

**No JavaScript Interactivity:**
- Problem: Static HTML cannot demonstrate real interactions
- Current workaround: Separate screens show different states
- Blocks: Cannot demonstrate user flows, animations, data updates
- Implementation complexity: Medium - needs framework adoption

**No Accessibility Attributes:**
- Problem: Missing ARIA labels, semantic HTML improvements
- Files: Throughout `index.html`
- Current workaround: None
- Blocks: Screen reader support, keyboard navigation
- Implementation complexity: Low - add aria-* attributes, semantic elements

**No README Documentation:**
- Problem: No project documentation file
- Current workaround: None
- Blocks: New developer onboarding
- Implementation complexity: Low - create README.md with setup instructions

## Test Coverage Gaps

**No Automated Tests:**
- What's not tested: All functionality (100% manual)
- Risk: Visual regressions undetected
- Priority: Low for prototype, High for production
- Difficulty to test: Would need visual regression tooling

**No Accessibility Testing:**
- What's not tested: Screen reader compatibility, keyboard navigation
- Risk: Inaccessible to users with disabilities
- Priority: Medium
- Difficulty to test: Run WAVE or axe-core browser extensions

**No HTML/CSS Validation:**
- What's not tested: Standards compliance
- Risk: Browser compatibility issues
- Priority: Low
- Difficulty to test: Use W3C validators

---

*Concerns audit: 2026-01-19*
*Update as issues are fixed or new ones discovered*
