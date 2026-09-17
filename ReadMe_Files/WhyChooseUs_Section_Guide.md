# Why Choose Us Section Guide

## Current Items (6 cards)

| # | Icon | Title | i18n Key |
|---|------|-------|----------|
| 1 | `fa-shield-alt` | Safe & Secure | `whyus.safe` |
| 2 | `fa-hand-holding-usd` | Transparent Pricing | `whyus.price` |
| 3 | `fa-headset` | 24/7 Support | `whyus.support` |
| 4 | `fa-map-marked-alt` | South India Experts | `whyus.coverage` |
| 5 | `fa-cogs` | Customizable Plans | `whyus.custom` |
| 6 | `fa-heart` | We Care | `whyus.care` |

---

## Where to Change Text

### In `index.html` (~line 218-260):
Each item looks like:
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

Replace the icon class. Find icons at: https://fontawesome.com/icons

```html
<i class="fas fa-shield-alt"></i>
<!--           ^^^^^^^^^^^^^^ change this -->
```

Useful icons:
| Icon | Class |
|------|-------|
| Shield | `fa-shield-alt` |
| Money | `fa-hand-holding-usd` |
| Headset | `fa-headset` |
| Map | `fa-map-marked-alt` |
| Gear | `fa-cogs` |
| Heart | `fa-heart` |
| Star | `fa-star` |
| Clock | `fa-clock` |
| Thumbs up | `fa-thumbs-up` |
| Award | `fa-award` |

---

## Adding a New Item

Add inside `<div class="swiper-wrapper">`:
```html
<div class="swiper-slide whyus-item">
    <i class="fas fa-award"></i>
    <h4 data-i18n="whyus.newthing.title">New Feature</h4>
    <p data-i18n="whyus.newthing.desc">Description of the feature.</p>
</div>
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

In `css/style.css`:
```css
.whyus-item {
    text-align: center;
    padding: 30px 20px;
}

.whyus-item i {
    font-size: 2.2rem;           /* Icon size */
    color: var(--gold);           /* Icon color */
    margin-bottom: 15px;
}

.whyus-item h4 {
    font-size: 16px;              /* Title size */
    color: var(--blue-dark);      /* Title color */
}

.whyus-item p {
    font-size: 13px;              /* Description size */
    color: var(--gray-500);       /* Description color */
}
```

---

## Quick Reference

| Action | What to change | File |
|--------|---------------|------|
| Change item title | `<h4 data-i18n="...">` + i18n | `index.html` + `js/i18n.js` |
| Change item description | `<p data-i18n="...">` + i18n | `index.html` + `js/i18n.js` |
| Change icon | `<i class="fas fa-xxx">` | `index.html` |
| Add an item | Add `whyus-item` div | `index.html` + `js/i18n.js` |
| Remove an item | Delete `whyus-item` div | `index.html` |
| Icon color | `.whyus-item i { color: ... }` | `css/style.css` |
| Icon size | `.whyus-item i { font-size: ... }` | `css/style.css` |
