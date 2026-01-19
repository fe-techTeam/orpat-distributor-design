# Coding Conventions

**Analysis Date:** 2026-01-19

## Naming Patterns

**Files:**
- `index.html` - Main application file (lowercase)
- `kebab-case.ext` - Image files (e.g., `clock-2397-blue.jpg`)
- Title case with spaces - Postman collections

**CSS Classes:**
- kebab-case for all classes: `.product-card`, `.checkout-item`
- Component-element pattern: `.header-back`, `.cart-text`, `.nav-icon`
- State classes: `.active`, `.pending`, `.approved`, `.dispatched`
- Prefix patterns:
  - `.btn-*` - Buttons (`.btn-add`, `.btn-update`)
  - `.product-*` - Product components
  - `.checkout-*` - Checkout components
  - `.order-*` - Order components
  - `.scheme-*` - Scheme components
  - `.nav-*` - Navigation elements

**Screen Labels:**
- Format: `{Letter} - {Description}`
- Examples: `A - Home`, `E - Checkout`, `K - Orders`

## Code Style

**HTML Formatting:**
- 4-space indentation throughout
- Attributes on same line for short elements
- Multi-line for complex elements
- Self-closing tags for void elements

**CSS Formatting:**
- 4-space indentation within `<style>` block
- One property per line
- Space after colon: `property: value;`
- Blank lines between rule blocks

**Comments:**
- HTML: `<!-- Section description -->`
- CSS: `/* Section Name */`
- Section headers for logical grouping

## Import Organization

**External Resources:**
1. Google Fonts (preconnect, stylesheet)
2. No other external dependencies

**Resource Loading:**
```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&display=swap" rel="stylesheet">
```

## CSS Patterns

**Color Variables:**
```css
:root {
    --orpat-red: #c41e3a;
    --orpat-dark: #1a1a2e;
    --orpat-blue: #0066cc;
    --orpat-gold: #d4a056;
}
```

**Usage:** Always use `var(--orpat-red)` for brand colors

**Gradient Pattern:**
```css
background: linear-gradient(135deg, var(--orpat-red) 0%, #a01830 100%);
```

**Hover Effects:**
```css
.element:hover {
    transform: translateY(-2px);
    box-shadow: 0 4px 12px rgba(196, 30, 58, 0.4);
}
```

**Transition Pattern:**
```css
transition: all 0.2s;
```

## Spacing Conventions

**Base Unit:** 4px

**Common Values:**
- Tight: `4px`, `6px`
- Normal: `8px`, `10px`, `12px`
- Medium: `16px`, `20px`
- Large: `24px`, `32px`

**Border Radius:**
- Small: `6px` (buttons, badges)
- Medium: `10px`, `12px`, `16px` (cards)
- Large: `20px`, `30px` (pills, floats)
- Circle: `50%` (icons)

## Typography

**Font Family:**
```css
font-family: 'Inter', sans-serif;
```

**Font Weights:**
- Regular: 400
- Medium: 500
- Semi-bold: 600
- Bold: 700
- Extra-bold: 800

**Font Sizes:**
- Extra small: `8px`, `9px` (badges, details)
- Small: `10px`, `11px` (captions)
- Body: `12px`, `13px`, `14px`
- Heading: `16px`, `18px`, `20px`, `22px`

## Inline Style Usage

**Current Pattern:** Heavy reliance on inline styles (737+ occurrences)

**When Used:**
- Component-specific positioning
- Unique styling variations
- Dynamic-like variations in static prototype

**Example:**
```html
<div style="padding: 16px; background: #fff; border-radius: 12px;">
```

**Note:** Consider extracting to CSS classes when converting to production

## Comment Patterns

**CSS Section Headers:**
```css
/* ORPAT Brand Colors */
/* Header Styles */
/* Home Screen Styles */
/* Product Detail Screen */
/* Checkout Screen */
```

**HTML Section Markers:**
```html
<!-- Screen A: Home/Dashboard -->
<!-- Category Tabs -->
<!-- Products Grid -->
<!-- First Row -->
<!-- Promotional Banner -->
```

## Component Patterns

**Card Component:**
```css
.card {
    background: #fff;
    border-radius: 12px;
    border: 1px solid #e9ecef;
    overflow: hidden;
    transition: all 0.2s;
}
.card:hover {
    box-shadow: 0 4px 16px rgba(0,0,0,0.1);
    transform: translateY(-2px);
}
```

**Button Component:**
```css
.btn {
    padding: 6px 14px;
    border: none;
    border-radius: 6px;
    font-size: 10px;
    font-weight: 700;
    cursor: pointer;
    text-transform: uppercase;
}
```

**Badge Component:**
```css
.badge {
    padding: 3px 8px;
    border-radius: 6px;
    font-size: 8px;
    font-weight: 700;
    text-transform: uppercase;
}
```

---

*Convention analysis: 2026-01-19*
*Update when patterns change*
