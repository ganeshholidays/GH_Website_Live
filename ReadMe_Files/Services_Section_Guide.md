# Services Section Guide

## Current Services (6 cards)

| # | Icon | Title | i18n Key |
|---|------|-------|----------|
| 1 | `fa-car` | Rental Car Service | `services.rental` |
| 2 | `fa-user-tie` | Acting Driver Service | `services.driver` |
| 3 | `fa-umbrella-beach` | Customized Holidays | `services.holiday` |
| 4 | `fa-om` | Pilgrimage Tours | `services.pilgrimage` |
| 5 | `fa-users` | Family & Group Tours | `services.family` |
| 6 | `fa-briefcase` | Corporate Travel | `services.corporate` |

---

## Where to Change Text

### In `index.html` (~line 102-140):
Each service card looks like:
```html
<div class="swiper-slide service-card">
    <div class="service-icon"><i class="fas fa-car"></i></div>
    <h3 data-i18n="services.rental.title">Rental Car Service</h3>
    <p data-i18n="services.rental.desc">Well-maintained cars available for rent...</p>
</div>
```

### Tamil translations in `js/i18n.js`:
```javascript
"services.rental.title": "Rental Car Service",
"services.rental.desc": "Well-maintained cars available for rent...",
```

---

## Changing the Icon

Icons use Font Awesome. Find icons at: https://fontawesome.com/icons (free icons only)

Replace the icon class:
```html
<div class="service-icon"><i class="fas fa-car"></i></div>
<!--                              ^^^^^^^^^^^ change this -->
```

Common travel icons:
| Icon | Class |
|------|-------|
| Car | `fa-car` |
| Plane | `fa-plane` |
| Bus | `fa-bus` |
| Train | `fa-train` |
| Hotel | `fa-hotel` |
| Map | `fa-map` |
| Compass | `fa-compass` |
| Camera | `fa-camera` |
| Mountain | `fa-mountain` |
| Temple | `fa-om` |

---

## Adding a New Service

Add this block inside `<div class="swiper-wrapper">`:
```html
<div class="swiper-slide service-card">
    <div class="service-icon"><i class="fas fa-plane"></i></div>
    <h3 data-i18n="services.newservice.title">New Service Name</h3>
    <p data-i18n="services.newservice.desc">Description of the new service.</p>
</div>
```

Also add translations in `js/i18n.js` for both EN and Tamil.

---

## Removing a Service

Delete the entire `<div class="swiper-slide service-card">...</div>` block.

---

## Display Behavior

| View | How it shows |
|------|-------------|
| **Laptop** | 3-column grid (all 6 visible) |
| **Tablet** | 2-column grid |
| **Mobile** | Swiper carousel (1 at a time, auto-scroll) |

---

## Styling

### Card styling in `css/style.css`:
```css
.service-card {
    background: white;
    padding: 35px 25px;
    border-radius: var(--radius-md);
    box-shadow: var(--shadow-sm);
    text-align: center;
}

.service-icon {
    font-size: 2.5rem;           /* Icon size */
    color: var(--gold);           /* Icon color — gold */
    margin-bottom: 20px;
}

.service-card h3 {
    font-size: 16px;              /* Title size */
    color: var(--blue-dark);      /* Title color */
}

.service-card p {
    font-size: 13px;              /* Description size */
    color: var(--gray-500);       /* Description color */
}
```

---

## Quick Reference

| Action | What to change | File |
|--------|---------------|------|
| Change service title | `<h3 data-i18n="...">` + i18n | `index.html` + `js/i18n.js` |
| Change service description | `<p data-i18n="...">` + i18n | `index.html` + `js/i18n.js` |
| Change icon | `<i class="fas fa-xxx">` | `index.html` |
| Add a service | Add `service-card` div | `index.html` + `js/i18n.js` |
| Remove a service | Delete `service-card` div | `index.html` |
| Icon color | `.service-icon { color: ... }` | `css/style.css` |
| Icon size | `.service-icon { font-size: ... }` | `css/style.css` |
| Card background | `.service-card { background: ... }` | `css/style.css` |
