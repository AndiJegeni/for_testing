# Test Plan — AndiJegeni/for_testing & AndiJegeni/vanilla-html

**Version:** 1.0  
**Date:** 2026-07-11  
**Tester:** QA Agent  
**Scope:** Static front-end repos — `for_testing` (portfolio site) and `vanilla-html` (Kilo design-studio site)

---

## 1. Scope & Objectives

### In Scope
- HTML structure and semantic correctness
- CSS validity, layout integrity, and responsive behaviour
- JavaScript functionality (interactive buttons, clock widget, poof animation)
- Accessibility (ARIA, alt text, keyboard navigation, colour contrast)
- Navigation link targets and anchor correctness
- Performance indicators (external resource loading, unused code)
- Cross-repo consistency where both sites share the same deployment origin

### Out of Scope
- Backend / API endpoints (none exist — static sites)
- Browser automation / visual regression screenshots
- SEO ranking or Core Web Vitals measured in a real browser

### Objectives
1. Identify structural or semantic HTML issues.
2. Identify CSS rules that are broken, missing, or cause layout regressions.
3. Verify all interactive JavaScript behaves as intended.
4. Surface accessibility defects.
5. Document debug/placeholder content left in production files.
6. Produce an issue list for the maintainer to act on.

---

## 2. Test Environment

| Item | Detail |
|------|--------|
| Repos under test | `AndiJegeni/for_testing`, `AndiJegeni/vanilla-html` |
| Branch | `main` |
| Analysis method | Static code review of HTML, CSS, JS source |
| Tools | Manual inspection, WCAG 2.1 AA checklist, HTML5 spec reference |
| Date of snapshot | 2026-07-11 |

---

## 3. Test Cases

### Group A — HTML Structure

| ID | Description | File(s) |
|----|-------------|---------|
| A-01 | DOCTYPE and lang attribute present | both |
| A-02 | Meta charset and viewport declared | both |
| A-03 | All nav anchor hrefs resolve to real IDs or pages | both |
| A-04 | No duplicate `id` attributes on the same page | both |
| A-05 | Images have `alt` attributes | both |
| A-06 | No raw debug/placeholder text visible to users | for_testing/index.html |
| A-07 | Footer copyright year is current | both |
| A-08 | All external links use `rel="noopener noreferrer"` | both |
| A-09 | `<button>` elements without `type` attribute default to `type="submit"` inside forms | for_testing/index.html |
| A-10 | `<title>` is meaningful and unique per page | both |

### Group B — CSS

| ID | Description | File(s) |
|----|-------------|---------|
| B-01 | `.about-me-btn` class referenced in HTML is defined in stylesheet | for_testing |
| B-02 | `.poof-button` and `.poof-wrapper` classes exist in stylesheet | for_testing |
| B-03 | `.poof-pop` animation class exists in stylesheet | for_testing |
| B-04 | Mobile breakpoints tested at 375 px and 768 px | both |
| B-05 | CSS custom properties (`--*`) are all declared in `:root` before use | both |
| B-06 | No `!important` overuse | both |
| B-07 | Colour contrast meets WCAG AA (4.5:1 for normal text) | both |

### Group C — JavaScript

| ID | Description | File(s) |
|----|-------------|---------|
| C-01 | `poofWorks()` function triggers animation and alert | for_testing/index.html |
| C-02 | `document.getElementById('poofBtn')` resolves to an existing element | for_testing/index.html |
| C-03 | `poof-pop` class is added then removed without error | for_testing/index.html |
| C-04 | Clock `tick()` function initialises on load | vanilla-html/index.html |
| C-05 | Clock `setInterval` uses a correct interval (30 s) | vanilla-html/index.html |
| C-06 | No inline `onclick` attribute conflicts with JS function scope | for_testing/index.html |

### Group D — Accessibility

| ID | Description | File(s) |
|----|-------------|---------|
| D-01 | Navbar landmark `<nav>` present with accessible label | both |
| D-02 | Headings follow correct hierarchy (h1 > h2 > h3) | both |
| D-03 | Interactive elements focusable via keyboard | both |
| D-04 | Colour-only information not used as sole differentiator | both |
| D-05 | Fixed overlay buttons do not obstruct main content on mobile | for_testing/index.html |
| D-06 | Contact icon uses HTML entity with no accessible text | for_testing/index.html |

### Group E — Content Quality

| ID | Description | File(s) |
|----|-------------|---------|
| E-01 | No lorem-ipsum or placeholder copy visible | both |
| E-02 | Debug labels ("testing vercel deployment", "wassuppp hello") removed before production | for_testing/index.html |
| E-03 | Email addresses and social links are real and functional | for_testing/index.html |
| E-04 | Project descriptions are plausible and complete | for_testing/index.html |
| E-05 | Stats (50+ projects, 5+ years, 100% satisfaction) are accurate | for_testing/index.html |

---

## 4. Pass / Fail Criteria

- **Pass:** The code meets the stated requirement with no observable defect.
- **Fail:** A defect exists that would cause incorrect rendering, broken functionality, accessibility barrier, or misleading content.
- **Warning:** The code works but represents a quality or maintainability risk.
