# About Section Guide

## Current Content

| Element | Current Text |
|---------|-------------|
| Title | About Ganesh Holidays |
| Subtitle | Named with love. Driven with passion. |
| Description | Ganesh Holidays was founded in 2026 by Vignesh Ganesan... |
| Stat 1 | 5 — Years Experience |
| Stat 2 | 200 — Happy Customers |
| Stat 3 | 30 — Destinations |
| Stat 4 | 100 — On-Time Record % |

---

## Where to Change Text

### Title and subtitle:
In `index.html` (~line 70-71):
```html
<h2 class="section-title" data-i18n="about.title">About Ganesh Holidays</h2>
<p class="section-subtitle" data-i18n="about.subtitle">Named with love. Driven with passion.</p>
```

### Description paragraph:
In `index.html` (~line 75):
```html
<p data-i18n="about.desc">Ganesh Holidays was founded in 2026...</p>
```

### Stats numbers:
In `index.html` (~line 78-93). Change the `data-count` value:
```html
<div class="stat-number" data-count="5">0</div>     <!-- Years -->
<div class="stat-number" data-count="200">0</div>    <!-- Customers -->
<div class="stat-number" data-count="30">0</div>     <!-- Destinations -->
<div class="stat-number" data-count="100">0</div>    <!-- On-Time % -->
```

### Stats labels:
```html
<div class="stat-label" data-i18n="about.stats.years">Years Experience</div>
<div class="stat-label" data-i18n="about.stats.customers">Happy Customers</div>
<div class="stat-label" data-i18n="about.stats.destinations">Destinations</div>
<div class="stat-label" data-i18n="about.stats.ontime">On-Time Record %</div>
```

### Tamil translations in `js/i18n.js`:
Update both English and Tamil sections:
```javascript
// English
"about.title": "About Ganesh Holidays",
"about.subtitle": "Named with love. Driven with passion.",
"about.desc": "Ganesh Holidays was founded in 2026...",
"about.stats.years": "Years Experience",
"about.stats.customers": "Happy Customers",
"about.stats.destinations": "Destinations",
"about.stats.ontime": "On-Time Record %",

// Tamil
"about.title": "கணேஷ் ஹாலிடேஸ் பற்றி",
// ... update corresponding Tamil text
```

---

## How to Update Stats Numbers

The stats use an animated counter that counts from 0 to the target number when the section scrolls into view.

To change a stat value, update the `data-count` attribute:

| Stat | Current | To change to 300 customers |
|------|---------|--------------------------|
| Customers | `data-count="200"` | `data-count="300"` |

The counter animation works automatically — no JS changes needed.

---

## Adding or Removing Stats

### To add a 5th stat:
Add this block inside `<div class="stats-grid">`:
```html
<div class="stat-card">
    <div class="stat-number" data-count="50">0</div>
    <div class="stat-label" data-i18n="about.stats.newstat">New Stat Label</div>
</div>
```

### To remove a stat:
Delete the entire `<div class="stat-card">...</div>` block for that stat.

---

## Styling

### Section background:
The About section has a white background by default. To change:
```css
.about {
    background: #f7fafc;    /* Light grey */
}
```

### Stats card styling in `css/style.css`:
```css
.stat-card {
    text-align: center;
    padding: 20px;
}

.stat-number {
    font-size: 2.5rem;       /* Number size */
    font-weight: 800;
    color: var(--blue-dark);  /* Number color */
}

.stat-label {
    font-size: 13px;          /* Label size */
    color: var(--gray-500);   /* Label color */
}
```

---

## Quick Reference

| Action | What to change | File |
|--------|---------------|------|
| Change title | `<h2 class="section-title">` + i18n | `index.html` + `js/i18n.js` |
| Change subtitle | `<p class="section-subtitle">` + i18n | `index.html` + `js/i18n.js` |
| Change description | `<p data-i18n="about.desc">` + i18n | `index.html` + `js/i18n.js` |
| Change stat number | `data-count="X"` | `index.html` |
| Change stat label | `<div class="stat-label">` + i18n | `index.html` + `js/i18n.js` |
| Add a stat | Add `stat-card` div | `index.html` |
| Remove a stat | Delete `stat-card` div | `index.html` |
| Stat number color | `.stat-number { color: ... }` | `css/style.css` |
