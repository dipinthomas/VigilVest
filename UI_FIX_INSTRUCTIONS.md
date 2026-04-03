# UI Fix Instructions — vigilVest `index.html`

## Overview

The landing page has two main visual problems:

1. **Hero headline is too large and feels stretched** — it uses `clamp(2.8rem, 7vw, 5.5rem)` which at ~1060px viewport renders at ~74px. The font (Syne 800) is very wide/bold and spans nearly full width, making it look bloated.
2. **Sections have no max-width container** — all content uses `padding: 100px 5%` and stretches edge-to-edge on wide screens, making text lines too long and the layout feel ungrounded.

---

## Fixes

### 1. Reduce Hero H1 Font Size

Find in `<style>`:
```css
/* Before */
font-size: clamp(2.8rem, 7vw, 5.5rem);

/* After */
font-size: clamp(2.2rem, 5vw, 4rem);
```

---

### 2. Reduce Section Heading (`.section-title`) Font Size

Find `.section-title`:
```css
/* Before */
font-size: clamp(2rem, 4.5vw, 3rem);

/* After */
font-size: clamp(1.6rem, 3.5vw, 2.4rem);
```

---

### 3. Add a Max-Width Content Wrapper to All Sections

Currently every `section` stretches the full viewport width with no inner container.

**Add this new CSS rule:**
```css
.section-inner {
  max-width: 1100px;
  margin: 0 auto;
  width: 100%;
}
```

**Then in the HTML**, wrap all child content inside each `<section>` with:
```html
<div class="section-inner">...</div>
```

Sections to update: stats strip, core features, how it works, downturn scanner, personalization engine, comparison table, and CTA.

**Also add a hero inner wrapper:**
```css
.hero-inner {
  max-width: 1100px;
  margin: 0 auto;
  width: 100%;
}
```

And wrap the `.hero` section's content with:
```html
<div class="hero-inner">...</div>
```

---

### 4. Constrain Hero Chart Width

Find `.hero-chart`:
```css
/* Before */
max-width: 880px;

/* After */
max-width: 800px;
```

---

### 5. Tighten Section Vertical Padding

```css
/* Before */
section { padding: 100px 5%; }

/* After */
section { padding: 80px 5%; }
```

Also update the `@media (max-width: 700px)` override:
```css
/* Before */
section { padding: 70px 5%; }

/* After */
section { padding: 60px 5%; }
```

---

### 6. Reduce Stats Strip Number Font Size

Find `.stat-num`:
```css
/* Before */
font-size: clamp(2rem, 4vw, 2.8rem);

/* After */
font-size: clamp(1.8rem, 3.5vw, 2.4rem);
```

---

### 7. Reduce Hero Section Top/Bottom Padding

Find the `.hero` padding:
```css
/* Before */
padding: 120px 5% 80px;

/* After */
padding: 90px 5% 60px;
```

---

## Summary

| Change | Before | After |
|---|---|---|
| Hero H1 font size | `clamp(2.8rem, 7vw, 5.5rem)` | `clamp(2.2rem, 5vw, 4rem)` |
| Section title font size | `clamp(2rem, 4.5vw, 3rem)` | `clamp(1.6rem, 3.5vw, 2.4rem)` |
| Stat number font size | `clamp(2rem, 4vw, 2.8rem)` | `clamp(1.8rem, 3.5vw, 2.4rem)` |
| Section padding | `100px 5%` | `80px 5%` |
| Hero padding | `120px 5% 80px` | `90px 5% 60px` |
| Hero chart max-width | `880px` | `800px` |
| Section content max-width | none | `1100px` (new `.section-inner` wrapper) |

These changes bring the headline down from ~74px to ~48–56px (still bold and impactful), constrain content width so it never stretches edge-to-edge on wide monitors, and tighten vertical rhythm so the page feels more intentional and premium. All changes are backwards-compatible with existing mobile media queries.
