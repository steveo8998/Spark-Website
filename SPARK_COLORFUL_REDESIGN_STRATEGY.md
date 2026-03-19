# Spark Academy — Colorful Redesign Strategy & Execution Guide

> **Purpose:** This document captures every design decision, color mapping, CSS rule, and execution step for the full-site colorful redesign. It serves as the single source of truth if context is ever lost or compressed.

---

## 1. DESIGN PHILOSOPHY

### Rule #1: Mobile-First
90% of web traffic views this site on smartphones. Every design decision must translate to small screens. Background effects, atmospheric triangles, and decorative elements must be visible and appropriately sized at 375px wide — not just on desktop.

### Rule #2: Triangle Brand Ownership (The "Nike Swoosh" Philosophy)
The triangle is Spark's brand shape. It comes from the five-triangle logo. We do NOT dilute it with circles, squares, rectangles, or other preschool-template shapes. Triangles own the brand/decorative layer. Other shapes may exist only at the content/icon level (e.g., schedule card icons, checkmarks).

### Rule #3: CSS-Only Changes in Block 0
All changes happen in the `<style>` tag (Block 0). HTML structure, content, typography hierarchy, and accessibility features remain unchanged. We are retheming, not rebuilding.

### Rule #4: Accent-Level Theming
Program colors replace accents (buttons, icons, borders, hover states, hero backgrounds, CTA gradients) — NOT the entire page. The base brand palette (teal, sage, white) still anchors navigation, footer, and cross-site elements.

---

## 2. COLOR SYSTEM

### 2A. Base Brand Palette (Shared Across ALL Pages)
```css
:root {
  --sp-teal: #3D6B62;
  --sp-gold: #C49826;
  --sp-gold-hover: #A8821F;
  --sp-sage: #9BB8AD;
  --sp-white: #FBFAF8;
  --sp-whisper: #EFF5F2;
  --sp-text: #2E2E2E;
  --sp-heading: #1A1A1A;
  --sp-gray: #6B7280;
  --sp-max: 1140px;

  /* Logo Triangle Colors (decorative motifs — same on ALL pages) */
  --sp-tri-pink: #FAC1BB;
  --sp-tri-orange: #F9A054;
  --sp-tri-yellow: #FFC716;
  --sp-tri-green: #808E71;
  --sp-tri-blue: #5E8B96;
}
```

### 2B. Program Color Assignments

| Program | Base Hex | Logo Triangle |
|---------|----------|---------------|
| Fresh 3's Fridays | #FAC1BB | Pink |
| 3's Preschool | #F9A054 | Orange |
| 4's Preschool | #FFC716 | Yellow |
| Kindergarten Prep | #808E71 | Green |
| Kindergarten | #5E8B96 | Blue |
| After School | #D4944A | Warm amber (orange-gold blend) |
| Summer Camp | #F5B835 | Sunny yellow-orange |
| Discovery Station | #4D8A8A | Teal-blue tint |

### 2C. Program Variable Template
For each program page, replace the `--sp-program-*` block in `:root`. Here are all 8 computed sets:

#### Fresh 3's Fridays — Pink (#FAC1BB)
```css
--sp-program: #FAC1BB;
--sp-program-dark: #E8A49C;
--sp-program-deep: #D4887E;
--sp-program-light: rgba(250,193,187,0.10);
--sp-program-lighter: rgba(250,193,187,0.06);
--sp-program-wash: #FFF5F4;
--sp-program-whisper: #FEF0EE;
--sp-program-border: rgba(250,193,187,0.30);
```

#### 3's Preschool — Orange (#F9A054) ✅ PROOF OF CONCEPT DONE
```css
--sp-program: #F9A054;
--sp-program-dark: #E0882E;
--sp-program-deep: #C47420;
--sp-program-light: rgba(249,160,84,0.08);
--sp-program-lighter: rgba(249,160,84,0.05);
--sp-program-wash: #FFF8F0;
--sp-program-whisper: #FEF3E8;
--sp-program-border: rgba(249,160,84,0.25);
```

#### 4's Preschool — Yellow (#FFC716)
```css
--sp-program: #FFC716;
--sp-program-dark: #E0AD00;
--sp-program-deep: #B88E00;
--sp-program-light: rgba(255,199,22,0.10);
--sp-program-lighter: rgba(255,199,22,0.06);
--sp-program-wash: #FFFBEB;
--sp-program-whisper: #FFF8E0;
--sp-program-border: rgba(255,199,22,0.28);
```
> **Special note for Yellow:** Because yellow has low contrast on white, buttons use `--sp-program-deep` for text on light backgrounds, and button text color should be `#5C4700` (dark amber) instead of `#fff` for accessibility.

#### Kindergarten Prep — Green (#808E71)
```css
--sp-program: #808E71;
--sp-program-dark: #6A7A5C;
--sp-program-deep: #556648;
--sp-program-light: rgba(128,142,113,0.10);
--sp-program-lighter: rgba(128,142,113,0.06);
--sp-program-wash: #F5F7F2;
--sp-program-whisper: #EFF2EB;
--sp-program-border: rgba(128,142,113,0.25);
```

#### Kindergarten — Blue (#5E8B96)
```css
--sp-program: #5E8B96;
--sp-program-dark: #4A7580;
--sp-program-deep: #386068;
--sp-program-light: rgba(94,139,150,0.10);
--sp-program-lighter: rgba(94,139,150,0.06);
--sp-program-wash: #F0F6F7;
--sp-program-whisper: #EAF2F4;
--sp-program-border: rgba(94,139,150,0.25);
```

#### After School — Warm Amber (#D4944A)
```css
--sp-program: #D4944A;
--sp-program-dark: #B87E38;
--sp-program-deep: #9C6828;
--sp-program-light: rgba(212,148,74,0.10);
--sp-program-lighter: rgba(212,148,74,0.06);
--sp-program-wash: #FDF6EE;
--sp-program-whisper: #FAF0E4;
--sp-program-border: rgba(212,148,74,0.25);
```

#### Summer Camp — Sunny Yellow-Orange (#F5B835)
```css
--sp-program: #F5B835;
--sp-program-dark: #D9A020;
--sp-program-deep: #B58518;
--sp-program-light: rgba(245,184,53,0.10);
--sp-program-lighter: rgba(245,184,53,0.06);
--sp-program-wash: #FFFAED;
--sp-program-whisper: #FFF6E0;
--sp-program-border: rgba(245,184,53,0.28);
```

#### Discovery Station — Teal-Blue (#4D8A8A)
```css
--sp-program: #4D8A8A;
--sp-program-dark: #3D7474;
--sp-program-deep: #2E5F5F;
--sp-program-light: rgba(77,138,138,0.10);
--sp-program-lighter: rgba(77,138,138,0.06);
--sp-program-wash: #EFF7F7;
--sp-program-whisper: #E8F3F3;
--sp-program-border: rgba(77,138,138,0.25);
```

### 2D. Hub / Utility Pages Color Treatment
Hub pages (Homepage, Programs, Why Spark, Purposeful Play, Founder Hub, Blog Hub, FAQ, Answer Hub, Consulting) do NOT have a single program color. They use:
- The base brand palette (teal accents for buttons and links)
- Triangle dividers and color bars (universal brand motifs)
- Atmospheric triangles using `--sp-teal` instead of `--sp-program`
- Hero backgrounds stay `--sp-whisper` (sage tint) rather than a program wash

For hub pages, set:
```css
--sp-program: var(--sp-teal);
--sp-program-dark: #2F5A52;
--sp-program-deep: #234840;
--sp-program-light: rgba(61,107,98,0.08);
--sp-program-lighter: rgba(61,107,98,0.05);
--sp-program-wash: #EFF5F2;
--sp-program-whisper: #E8F0EC;
--sp-program-border: rgba(61,107,98,0.20);
```
This keeps them feeling "brand neutral" while still benefiting from the atmospheric triangles and divider system.

### 2E. Small Pages (Tour, Thank You, Consulting Thank You)
These are short confirmation/form pages. They get:
- Triangle divider after hero (if hero exists)
- Color bar before footer
- Footer triangles
- Use the hub/teal color scheme (same as 2D)
- No atmospheric triangles (pages are too short for them to register)

---

## 3. THREE-TIER DIVIDER SYSTEM

### Tier 1: Triangle Row — After Hero (Brand Opening Signature)
```html
<div class="sp-triangle-divider">
  <span class="sp-tri sp-tri-1"></span>
  <span class="sp-tri sp-tri-2"></span>
  <span class="sp-tri sp-tri-3"></span>
  <span class="sp-tri sp-tri-4"></span>
  <span class="sp-tri sp-tri-5"></span>
</div>
```
Placed immediately after the `</section>` closing the hero block.

### Tier 2: Color Bar — Between Middle Sections (Content Separators)
```html
<div class="sp-color-bar"></div>
```
Placed between major content sections in the body. Typically 2-4 per page depending on section count.

### Tier 3: Triangle Row — Footer (Brand Closing Signature)
Located inside `.sp-positioning-footer`:
```html
<div class="sp-footer-triangles">
  <span class="sp-ft" style="border-bottom-color: var(--sp-tri-pink);"></span>
  <span class="sp-ft" style="border-bottom-color: var(--sp-tri-orange);"></span>
  <span class="sp-ft" style="border-bottom-color: var(--sp-tri-yellow);"></span>
  <span class="sp-ft" style="border-bottom-color: var(--sp-tri-green);"></span>
  <span class="sp-ft" style="border-bottom-color: var(--sp-tri-blue);"></span>
</div>
```
Placed inside the positioning footer div, above the `<p>` tagline.

---

## 4. ATMOSPHERIC BACKGROUND TRIANGLES

### CSS Classes
Add `sp-atmos sp-atmos-[A/B/C/D]` to alternating white-background content sections:

| Variant | Position | Description |
|---------|----------|-------------|
| A | Bottom-right corner | Large triangle, 500×500px desktop |
| B | Top-left corner | Large triangle, 420×420px desktop |
| C | Two corners (top-right + bottom-left) | Dual smaller triangles |
| D | Centered-right | Single large offset triangle |

### Assignment Pattern
Rotate variants across white/light sections to avoid repetition:
- Block 2 (first content): `sp-atmos sp-atmos-a`
- Block 3: `sp-atmos sp-atmos-c`
- Block 4: `sp-atmos sp-atmos-b`
- Block 5: `sp-atmos sp-atmos-d`
- Block 6+: restart cycle or skip if section is short

Only apply to sections with `sp-bg-white` or `sp-bg-sage` backgrounds. Do NOT apply to hero, CTA, or positioning footer (those have their own triangle decorations).

### Responsive Behavior
Desktop opacity: 0.025–0.035 (felt, not seen)
Mobile (under 768px): Sizes shrink to 140–240px, offsets tighten to -10 to -20px, opacity bumps to 0.035–0.045
Small phones (under 360px): Sizes shrink to 110–180px, offsets tighten to -5 to -15px, opacity bumps to 0.04–0.05

---

## 5. RESPONSIVE BREAKPOINTS

### Desktop (768px+)
- Full-size atmospheric triangles
- Two-column grids where applicable
- Full padding (80px 24px)

### Tablet / Mobile (max-width: 767px)
- Single-column grids
- Reduced padding (48px 20px)
- Smaller font sizes (H1: 32px, H2: 28px, H3: 21px)
- Hero triangles: 100×180px and 80×140px
- Atmospheric triangles: 140–240px with 0.035–0.045 opacity
- CTA triangles: 90×160px and 70×120px
- Divider triangles: `transform: scale(0.8)`
- Touch-friendly links get underline treatment

### Small Phones (max-width: 360px)
- Tightest padding (36px 16px)
- Smallest fonts (H1: 28px, H2: 24px, H3: 19px)
- Hero triangles: 70×130px and 55×100px
- Atmospheric triangles: 110–180px with 0.04–0.05 opacity
- Divider triangles: `transform: scale(0.65)`

---

## 6. CSS COMPONENTS THAT ARE UNIVERSAL (Same on ALL Pages)

These CSS blocks are identical across every page — copy as-is:

1. **Triangle divider** (`.sp-triangle-divider`, `.sp-tri`, `.sp-tri-1` through `.sp-tri-5`)
2. **Color bar** (`.sp-color-bar`)
3. **Footer triangles** (`.sp-footer-triangles`, `.sp-ft`)
4. **Atmospheric system** (`.sp-atmos`, `.sp-atmos-a/b/c/d` + responsive overrides)
5. **Logo triangle CSS variables** (`--sp-tri-pink` through `--sp-tri-blue`)
6. **Base brand palette variables** (`--sp-teal` through `--sp-max`)
7. **All responsive media queries** (structure is the same, only rgba values in box-shadows/borders change per program color)

---

## 7. CSS COMPONENTS THAT CHANGE PER PAGE

### 7A. Program Color Variables (change on every page)
The `:root` program color variables change:
1. `--sp-program` — the base hex
2. `--sp-program-dark` — hover/emphasis shade
3. `--sp-program-deep` — deepest shade (CTA gradient, dark text)
4. `--sp-program-light` — rgba at ~0.08 for icon backgrounds
5. `--sp-program-lighter` — rgba at ~0.05 for note backgrounds
6. `--sp-program-wash` — hero/light section background
7. `--sp-program-whisper` — lighter variant for alternating sections
8. `--sp-program-border` — rgba at ~0.25 for borders

Additionally, hardcoded rgba values in these spots must match the program color:
- `box-shadow` on `.sp-btn-gold` and `.sp-btn-gold:hover`
- `text-decoration-color` in the 1024px media query
- `border-bottom-color` on `.sp-hero-secondary`
- Gradient stops in `.sp-tuition-header` and `.sp-cta-section`

**Tip:** Search for `rgba(249,160,84` in the 3's Preschool proof of concept — those are all the hardcoded orange values that need to change per program.

### 7B. Page-Specific CSS Rules (CRITICAL — Do NOT Drop These)

> **LESSON LEARNED (Phase 1):** The 3's Preschool proof of concept was used as the CSS template for all pages. During the initial Phase 1 build, the entire `<style>` block from each original file was replaced wholesale with the POC's CSS. This broke every page except the 3's Preschool because each page has unique HTML components with their own CSS rules that do not exist in the 3's Preschool. Without those rules, elements like SVG icons rendered at full container width (no `width`/`height` constraints), grids collapsed, and card layouts disappeared entirely.

**Each page has unique CSS classes that MUST be preserved during the redesign.** The POC only covers the shared/common components. Here is what each page adds beyond the 3's Preschool baseline:

| Page | Unique CSS Components | Key Classes |
|------|----------------------|-------------|
| Fresh 3's Fridays | Tuition detail rows with icons, testimonial quotes | `.sp-tuition-detail-row`, `.sp-tuition-detail-icon`, `.sp-testimonial-quote` |
| 4's Preschool | "How Many Days?" scheduling decision cards, enrichment detail rows, link arrows | `.sp-days-grid`, `.sp-days-card`, `.sp-days-card-featured`, `.sp-enrich-details`, `.sp-link-arrow` |
| Kindergarten Prep | Readiness checklist grid, progression path cards | `.sp-ready-grid`, `.sp-ready-item`, `.sp-ready-icon`, `.sp-paths-grid`, `.sp-path-card` |
| Kindergarten | Academic skill domain cards (6-card grid with SVG icons), tuition detail checkmarks | `.sp-skill-grid`, `.sp-skill-card`, `.sp-skill-icon`, `.sp-tuition-detail-check`, `.sp-tuition-detail-line` |
| After School | Featured performance cards, activity pills, tuition detail rows, register CTAs | `.sp-featured-card`, `.sp-featured-header`, `.sp-activity-pills`, `.sp-activity-pill`, `.sp-tuition-detail-row`, `.sp-register-ctas`, `.sp-btn-outline-dark` |
| Summer Camp | Age group cards, pricing cards/table, deadline callout, differentiator cards, value reframe | `.sp-age-grid`, `.sp-age-card`, `.sp-pricing-cards`, `.sp-pricing-card`, `.sp-pricing-table`, `.sp-deadline-callout`, `.sp-diff-grid`, `.sp-diff-card`, `.sp-value-reframe`, `.sp-detail-card` |
| Discovery Station | Class cards grid, schedule cards, pricing cards/table, register block, drop-off declaration | `.sp-class-grid`, `.sp-class-card`, `.sp-schedule-cards`, `.sp-schedule-card-item`, `.sp-pricing-cards`, `.sp-pricing-card`, `.sp-pricing-table`, `.sp-register-block`, `.sp-dropoff-declaration` |
| Homepage | Program cards, feature grid, testimonial slider, stats counter, hero CTA layout | 598 lines page-specific CSS |
| Programs | Program overview cards, age range badges, comparison grid | 183 lines page-specific CSS |
| Why Spark | Philosophy cards, differentiator sections, value props | 143 lines page-specific CSS |
| Purposeful Play | Play methodology cards, activity examples, learning outcomes grid | 323 lines page-specific CSS |
| Founder Hub | Bio layout, timeline, mission cards, leadership grid | 425 lines page-specific CSS |
| Blog Hub | Post cards, category filters, featured post layout, pagination | 251 lines page-specific CSS |
| FAQ | Accordion items, category sections, search bar, expandable groups | 243 lines page-specific CSS |
| Answer Hub | Answer cards, topic grid, search functionality, related links | 385 lines page-specific CSS |
| Consulting | Service tiers, process steps, testimonial cards, booking CTA | 306 lines page-specific CSS |

**The correct approach for building each page's CSS:**
1. Start with the POC CSS as the base (it covers all shared components)
2. Swap the `--sp-program-*` variables and hardcoded rgba values for the target program color
3. Extract all CSS rules from the original page's `<style>` block that are NOT present in the 3's Preschool baseline
4. Apply color swaps to those page-specific rules (replace `var(--sp-teal)` with `var(--sp-program)`, replace `rgba(61,107,98,...)` and `rgba(155,184,173,...)` with the program color rgba equivalents)
5. Append those page-specific rules (including their responsive media query overrides) after the POC CSS
6. Verify SVGs, grids, and card layouts render correctly at desktop and mobile widths

---

## 8. HTML CHANGES PER PAGE

For each page, add these HTML elements (Block 0 CSS handles the styling):

### 8A. After Hero Section
Insert triangle divider HTML immediately after `</section>` of hero block.

### 8B. Between Content Sections
Insert `<div class="sp-color-bar"></div>` between major `<section>` blocks. Typically after every 2nd or 3rd section, not between every single one.

### 8C. Atmospheric Classes on Sections
Add `sp-atmos sp-atmos-[variant]` to the `class` attribute of content sections that have white or program-whisper backgrounds.

### 8D. Positioning Footer
Add the five-triangle markup inside `.sp-positioning-footer`, before the `<p>` tagline.

---

## 9. EXECUTION ORDER

### Phase 1: Core Program Pages (highest impact) ✅ COMPLETE
These are the pages prospective parents visit. Each gets full treatment.

1. **Spark_3s_Preschool_WordPress_Blocks.html** — Orange ✅
2. **Fresh_3s_Fridays_WordPress_Blocks.html** — Pink ✅
3. **Spark_4s_Preschool_WordPress_Blocks.html** — Yellow ✅ (dark button text #5C4700 applied)
4. **Spark_Kindergarten_Prep_WordPress_Blocks.html** — Green ✅
5. **Spark_Kindergarten_WordPress_Blocks.html** — Blue ✅

Output files saved to `New Designs/` folder with `_Colorful_Redesign` suffix.

### Phase 2: Supplemental Program Pages ✅ COMPLETE
6. **Spark_AfterSchool_WordPress_Blocks.html** — Warm Amber ✅
7. **Spark_Summer_Camp_WordPress_Blocks.html** — Sunny Yellow-Orange ✅
8. **Spark_Discovery_Station_WordPress_Blocks.html** — Teal-Blue ✅

Output files saved to `New Designs/` folder with `_Colorful_Redesign` suffix.

### Phase 3: Hub / Utility Pages ✅ COMPLETE
9. **Spark_Homepage_WordPress_Blocks.html** — Teal (brand neutral) ✅
10. **Spark_Programs_WordPress_Blocks.html** — Teal ✅
11. **Spark_Why_Spark_WordPress_Blocks.html** — Teal ✅
12. **Spark_Purposeful_Play_WordPress_Blocks.html** — Teal ✅
13. **Spark_Founder_Hub_WordPress_Blocks.html** — Teal ✅
14. **Spark_Blog_Hub_WordPress_Blocks.html** — Teal ✅
15. **Spark_FAQ_WordPress_Blocks.html** — Teal ✅
16. **Spark_Answer_Hub_WordPress_Blocks.html** — Teal ✅
17. **Spark_Consulting_WordPress_Blocks.html** — Teal ✅

Output files saved to `New Designs/` folder with `_Colorful_Redesign` suffix.

### Phase 4: Small / Confirmation Pages (light touch) ✅ COMPLETE
18. **Spark_Schedule_Tour_WordPress_Blocks.html** — Teal ✅
19. **Spark_Consulting_Thank_You_WordPress_Blocks.html** — Teal ✅
20. **Spark_Tour_Confirmed_WordPress_Blocks.html** — Teal ✅

Output files saved to `New Designs/` folder with `_Colorful_Redesign` suffix.
Light-touch treatment: triangle divider after hero, color bar before footer, footer triangles, no atmospheric triangles.

---

## 10. PER-PAGE EXECUTION CHECKLIST

For each file, follow this exact sequence:

- [ ] Read the original HTML file
- [ ] Identify all sections/blocks and their current classes
- [ ] **Extract page-specific CSS** from the original `<style>` block — any rules for classes NOT present in the 3's Preschool baseline (see Section 7B for the known list per page)
- [ ] Build the redesigned CSS: start with the POC base CSS, swap `--sp-program-*` variables for the correct program color
- [ ] Update hardcoded rgba values in box-shadows, gradients, and decoration-colors to match the new program color
- [ ] **Apply color swaps to the page-specific CSS** (teal/sage references become program color references) and append it to the redesigned CSS
- [ ] Insert triangle divider HTML after hero section
- [ ] Insert color bar HTML between middle content sections (2-4 placements)
- [ ] Add `sp-atmos sp-atmos-[variant]` classes to appropriate content sections
- [ ] Add footer triangle HTML inside positioning footer
- [ ] Verify the page comment block at the top reflects the correct program name and color
- [ ] **Verify page-specific components render correctly** — check SVG sizing, grid layouts, and card components at desktop and mobile widths
- [ ] Save the updated file

---

## 11. SPECIAL CONSIDERATIONS

### Yellow Accessibility
Yellow (#FFC716) has poor contrast on white. For the 4's Preschool page:
- Primary button text should be dark (`#5C4700`) instead of white
- The `.sp-btn-gold` override: `color: #5C4700;`
- Hero secondary link and trust line text should use `--sp-program-deep` for readability

### CTA Gradient Customization
Each program's CTA section uses a three-stop gradient:
```css
background: linear-gradient(135deg, [deep] 0%, [program] 60%, [light-tint] 100%);
```
The light-tint stop should be approximately 30% lighter than the program color. For each:
- Pink: `#D4887E → #FAC1BB → #FDDEDA`
- Orange: `#C47420 → #F9A054 → #FBBC78`
- Yellow: `#B88E00 → #FFC716 → #FFD966`
- Green: `#556648 → #808E71 → #A8B89C`
- Blue: `#386068 → #5E8B96 → #8AB4BF`
- Amber: `#9C6828 → #D4944A → #E8BA82`
- Summer: `#B58518 → #F5B835 → #F9D06A`
- Teal-Blue: `#2E5F5F → #4D8A8A → #7AB0B0`

### Tuition Header Gradient
Same pattern:
```css
background: linear-gradient(135deg, [dark] 0%, [program] 50%, [light-tint] 100%);
```

---

## 12. FILES REFERENCE

- **Proof of concept:** `3s_preschool_colorful_preview.html` (in workspace root — this is the gold standard)
- **Original pages:** All `*_WordPress_Blocks.html` files in workspace folder
- **Logo PDF:** `Spark_icon_full color.pdf`
- **Brand assets:** `Image Asset Examples/` folder (logos + document line)
- **Divider comparison:** `divider_comparison.html` (reference only, no longer needed)
- **This document:** `SPARK_COLORFUL_REDESIGN_STRATEGY.md`

---

## 13. BUILD AUTOMATION

Phase 1 was built using a Python script (`build_redesign_v2.py`) that automates the redesign process. The script:

1. Reads the POC CSS as the base template
2. Reads each original file's CSS to extract page-specific rules (by comparing class selectors against the 3's Preschool baseline)
3. Applies program color swaps to both the base CSS and the page-specific CSS
4. Preserves the original HTML content unchanged
5. Adds triangle dividers, color bars, atmospheric classes, and footer triangles
6. Outputs standalone HTML preview files to `New Designs/`

The same script can be extended for Phases 2-4 by adding program color configurations for the remaining pages.

---

*Last updated: March 12, 2026*
*ALL 4 PHASES COMPLETE. All 20 pages redesigned and saved to New Designs/ folder.*
*Phase 1: 5 core program pages | Phase 2: 3 supplemental program pages | Phase 3: 9 hub/utility pages | Phase 4: 3 small/confirmation pages*
