# CLAUDE.md — AI Assistant Guide for tsurutaikegolf

## Project Overview

This repository contains the website for **Tsurutaike Golf Center** (鶴田池ゴルフセンター), a golf practice facility located in Sakai, Osaka, Japan. The site is currently a holding/landing page communicating temporary closure and a 2027 renovation reopening, while also promoting an operational sub-facility called Garage Golf Kurotsu (ガレージゴルフ黒鶴).

**Repository:** `yoshi28j-crypto/tsurutaikegolf`
**Live content:** Single-page static HTML website

---

## Repository Structure

```
tsurutaikegolf/
├── README.md                  # Minimal project title only
├── CLAUDE.md                  # This file
└── tsurutaike_home.html       # Entire website (HTML + embedded CSS)
```

This is a **flat, single-file project** — the entire website lives in `tsurutaike_home.html`.

---

## Technology Stack

| Layer       | Technology                          |
|-------------|-------------------------------------|
| Markup      | HTML5 (semantic)                    |
| Styling     | CSS3 (vanilla, embedded in `<style>`) |
| Fonts       | Google Fonts (Noto Serif JP, Noto Sans JP, Cinzel) |
| JavaScript  | None                                |
| Backend     | None (fully static)                 |
| Build tools | None                                |
| Dependencies| None                                |

There are no package managers, build steps, transpilers, or server-side components.

---

## Design System

### Color Palette (CSS Variables)

```css
--green-dark:    #0d2b1a   /* Primary dark green (backgrounds) */
--green-mid:     #1a4d2e   /* Mid-tone green */
--green-light:   #2d6a4f   /* Lighter green accent */
--gold:          #c9a84c   /* Primary gold / accent */
--gold-light:    #e8c97a   /* Lighter gold for highlights */
--white:         #f5f5f0   /* Off-white body text */
--cream:         #faf8f0   /* Cream for cards/backgrounds */
--text-dark:     #1a1a1a   /* Near-black body text on light bg */
--border-color:  #c9a84c33 /* Translucent gold for borders */
```

### Typography

- **Headings (display):** `'Cinzel'` (serif, Latin/number characters)
- **Japanese headings:** `'Noto Serif JP'` (serif, elegant)
- **Body text:** `'Noto Sans JP'` (sans-serif, readable)
- Language attribute: `lang="ja"` on `<html>`

### Layout Patterns

- **CSS Grid** for multi-column sections (e.g., pages preview cards)
- **Flexbox** for header, nav, and component-level alignment
- **Mobile-first** responsive design with media query breakpoints
- Consistent spacing in multiples of 8px

### Naming Conventions

- Class names follow a **descriptive-hyphenated** pattern:
  - Section containers: `.hero-section`, `.kurotsu-section`, `.renewal-section`
  - Header parts: `.header-logo`, `.header-contact`
  - Component elements: `.hero-badge`, `.kurotsu-pricing`, `.page-card`
- No BEM strict methodology, but structure is component-like

---

## Page Structure (`tsurutaike_home.html`)

The HTML is organized into distinct sections in this order:

1. **`<head>`** — Meta charset (UTF-8), viewport, title, Google Fonts imports, all `<style>` CSS
2. **`<header>`** — Logo (dual-language), phone number contact
3. **`<nav>`** — Navigation bar (most links disabled, pending 2027 renovation)
4. **Hero section** — Large banner with "2027 AUTUMN" renewal announcement
5. **Grand Renewal section** — Detailed announcement with Instagram/LINE social links
6. **Garage Golf Kurotsu section** — Currently open indoor facility info, pricing table, hours
7. **Closure Notice section** — Official notice (dated Sept 9, 2024) about closure for seismic work
8. **Pages Preview Grid** — 4 cards (Facilities, Hours & Rates, School, Access) — all "Coming in 2027"
9. **`<footer>`** — Nav links, address, phone, copyright

---

## Key Content Details

### Business Information
- **Facility Name:** 鶴田池ゴルフセンター (Tsurutaike Golf Center)
- **Address:** 〒593-8312 堺市西区草部1630
- **Phone:** 072-273-6600
- **Status:** Closed for seismic reinforcement work (since Sept 15, 2024)
- **Planned Reopening:** Autumn 2027

### Garage Golf Kurotsu (Sub-facility — Currently Open)
- **Name:** ガレージゴルフ黒鶴
- **Location:** Within the Tsurutaike Golf Center parking lot
- **Hours:** 9:00–21:00
- **Pricing:** ¥1,210–¥1,430 per 50-minute session (tax included)
- **Instagram:** `@garage_golf_kurotsu`
- **LINE:** Official account available

---

## Development Workflow

### There is no build process. To make changes:

1. Edit `tsurutaike_home.html` directly
2. Open in a browser to preview (file:// is sufficient for static HTML)
3. Commit and push changes

### Recommended Preview

```bash
# Any of these work to preview locally:
open tsurutaike_home.html          # macOS
xdg-open tsurutaike_home.html      # Linux
python3 -m http.server 8080        # Serve locally at http://localhost:8080
```

### Git Workflow

```bash
git add tsurutaike_home.html
git commit -m "descriptive message"
git push -u origin <branch-name>
```

Branches should use clear naming. Claude branches follow:
`claude/<task-id>-<session-id>` pattern.

---

## Conventions for AI Assistants

### Editing HTML

- **CSS lives inside `<style>` in the `<head>`.** Do not move it to an external file unless the project structure is specifically being refactored.
- **All JavaScript additions** should go in a `<script>` tag before `</body>`. The site currently has no JS — keep additions minimal.
- **Preserve bilingual content** — the site uses both Japanese (日本語) and English. Both languages matter and should be maintained when editing text.
- **Do not break the CSS variable system** — always use `var(--variable-name)` instead of hardcoded colors.

### Content Edits

- Business info (phone, address, hours, pricing) should only be changed if explicitly requested with new values.
- The closure/renovation timeline (2027 Autumn reopening) is intentional — do not alter dates without explicit instruction.
- Navigation items are intentionally disabled (using `.disabled` class) for pages not yet built.

### Adding New Sections

- Follow the existing section pattern: `<section class="<name>-section">` with an inner `.container` div.
- Use the established color variables and typography classes.
- Add a corresponding navigation link in both `<nav>` and `<footer>` when creating new page sections.

### Responsive Design

- Test both mobile (<768px) and desktop (≥768px) layouts.
- The primary breakpoint is `@media (max-width: 768px)`.
- Mobile layout uses single-column stacking; desktop uses multi-column grids.

### Image and Asset Handling

- The site currently references external images via URLs. If adding local assets, place them in an `/assets/` or `/images/` directory and update paths.
- Prefer using CSS gradients and backgrounds already established rather than adding external image dependencies.

---

## No Testing Framework

There are no automated tests. Validation can be done manually:
- **HTML validation:** https://validator.w3.org/
- **CSS validation:** https://jigsaw.w3.org/css-validator/
- **Visual regression:** Manual browser testing

---

## Internationalization Notes

- The site uses `lang="ja"` and `charset="UTF-8"` — both are essential.
- Japanese text uses full-width characters where appropriate.
- Prices use the yen sign (¥) directly in HTML.
- Dates follow the Japanese format (令和X年X月X日) for official notices, alongside the Gregorian calendar equivalent where provided.
- Era references: 令和6年 = 2024, 令和9年 = 2027.

---

## Future Development Scope (as of site content)

Pages planned for 2027:
- **施設** (Facilities) — Golf center features and equipment
- **営業時間・料金** (Hours & Rates) — Pricing and schedule
- **スクール** (School) — Golf lessons and instruction
- **アクセス** (Access) — Directions and map

When these pages are built, the `.disabled` class and `pointer-events: none` CSS should be removed from their respective nav links.
