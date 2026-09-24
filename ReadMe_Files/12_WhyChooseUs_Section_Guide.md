# Why Choose Us Section Guide

## Current Items (6 cards)

| # | Icon | Title | Color | i18n Key |
|---|------|-------|-------|----------|
| 1 | `fa-shield-alt` | Safe & Secure | Green `#10B981` | `whyus.safe` |
| 2 | `fa-hand-holding-usd` | Transparent Pricing | Blue `#3B82F6` | `whyus.price` |
| 3 | `fa-headset` | 24/7 Support | Amber `#F59E0B` | `whyus.support` |
| 4 | `fa-map-marked-alt` | South India Experts | Red `#EF4444` | `whyus.coverage` |
| 5 | `fa-cogs` | Customizable Plans | Purple `#8B5CF6` | `whyus.custom` |
| 6 | `fa-heart` | We Care | Pink `#EC4899` | `whyus.care` |

---

## Icon Style (Flat Colored — No Background)

Each icon is a flat colored icon without background box:

```css
.whyus-item i {
    font-size: 32px;
    margin-bottom: 15px;
}

.whyus-item .fa-shield-alt { color: #10B981; }
.whyus-item .fa-hand-holding-usd { color: #3B82F6; }
/* etc. */
```

---

## Where to Change Text

### In `index.html` (~line 218-260):
Each item:
```html
<div class="swiper-slide whyus-item">
    <i class="fas fa-shield-alt"></i>
    <h4 data-i18n="whyus.safe.title">Safe & Secure</h4>
    <p data-i18n="whyus.safe.desc">Well-maintained vehicles with experienced, verified drivers for your safety.</p>
</div>
```

### Tamil translations in `js/i18n.js`:
```javascript
"whyus.safe.title": "Safe & Secure",
"whyus.safe.desc": "Well-maintained vehicles with experienced...",
```

---

## Changing the Icon

Replace the icon class in `index.html`:
```html
<i class="fas fa-shield-alt"></i>
<!--           ^^^^^^^^^^^^^^ change this -->
```

Find icons at: https://fontawesome.com/icons

Then add color in `css/style.css`:
```css
.whyus-item .fa-new-icon { color: #yourcolor; }
```

---

## Changing Icon Colors

In `css/style.css`:
```css
.whyus-item .fa-shield-alt { color: #10B981; }      /* Green */
.whyus-item .fa-hand-holding-usd { color: #3B82F6; } /* Blue */
.whyus-item .fa-headset { color: #F59E0B; }          /* Amber */
.whyus-item .fa-map-marked-alt { color: #EF4444; }   /* Red */
.whyus-item .fa-cogs { color: #8B5CF6; }             /* Purple */
.whyus-item .fa-heart { color: #EC4899; }            /* Pink */
```

### To revert all to gold (original):
Replace all individual colors with:
```css
.whyus-item i {
    font-size: 32px;
    color: var(--gold);
    margin-bottom: 15px;
}
```
And remove the individual `.whyus-item .fa-xxx` color rules.

---

## Adding a New Item

Add inside `<div class="swiper-wrapper">` in `index.html`:
```html
<div class="swiper-slide whyus-item">
    <i class="fas fa-award"></i>
    <h4 data-i18n="whyus.newthing.title">New Feature</h4>
    <p data-i18n="whyus.newthing.desc">Description of the feature.</p>
</div>
```

Add color in CSS:
```css
.whyus-item .fa-award { color: #F59E0B; }
```

Add translations in `js/i18n.js`.

---

## Removing an Item

Delete the entire `<div class="swiper-slide whyus-item">...</div>` block.

---

## Display Behavior

| View | How it shows |
|------|-------------|
| **Laptop** | 3-column grid (all 6 visible) |
| **Tablet** | 2-column grid |
| **Mobile** | Swiper carousel (1 at a time, auto-scroll) |

---

## Styling

```css
.whyus-item {
    text-align: center;
    padding: 30px 20px;
}

.whyus-item h4 {
    font-size: 16px;
    color: var(--blue-dark);
}

.whyus-item p {
    font-size: 13px;
    color: var(--gray-500);
}
```

---

## Quick Reference

| Action | What to change | File |
|--------|---------------|------|
| Change item title | `<h4 data-i18n="...">` + i18n | `index.html` + `js/i18n.js` |
| Change item description | `<p data-i18n="...">` + i18n | `index.html` + `js/i18n.js` |
| Change icon | `<i class="fas fa-xxx">` | `index.html` |
| Change icon color | `.whyus-item .fa-xxx { color: ... }` | `css/style.css` |
| Add an item | Add `whyus-item` div + CSS color | `index.html` + `css/style.css` + `js/i18n.js` |
| Remove an item | Delete `whyus-item` div | `index.html` |
| Revert to all gold | Replace with `.whyus-item i { color: var(--gold); }` | `css/style.css` |
