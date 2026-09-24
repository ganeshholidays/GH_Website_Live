# Services Section Guide

## Current Services (6 cards)

| # | Icon | Title | Color | i18n Key |
|---|------|-------|-------|----------|
| 1 | `fa-car` | Rental Car Service | Blue `#3B82F6` | `services.rental` |
| 2 | `fa-user-tie` | Acting Driver Service | Purple `#8B5CF6` | `services.driver` |
| 3 | `fa-umbrella-beach` | Customized Holidays | Amber `#F59E0B` | `services.holiday` |
| 4 | `fa-om` | Pilgrimage Tours | Red `#EF4444` | `services.pilgrimage` |
| 5 | `fa-users` | Family & Group Tours | Green `#10B981` | `services.family` |
| 6 | `fa-briefcase` | Corporate Travel | Indigo `#6366F1` | `services.corporate` |

---

## Icon Style (Modern — Pastel Background + Colored Icon)

Each icon has a rounded square with a light pastel background and matching colored icon:

```css
.service-icon {
    width: 60px;
    height: 60px;
    border-radius: 16px;       /* Rounded square */
    font-size: 24px;
}

.service-icon.icon-rental {
    background: rgba(59, 130, 246, 0.1);   /* Light blue bg */
    color: #3B82F6;                         /* Blue icon */
}
```

---

## Where to Change Text

### In `index.html` (~line 102-140):
Each service card:
```html
<div class="swiper-slide service-card">
    <div class="service-icon icon-rental"><i class="fas fa-car"></i></div>
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

### Step 1: Change icon class in `index.html`:
```html
<div class="service-icon icon-rental"><i class="fas fa-car"></i></div>
<!--                                          ^^^^^^^^^^^ change this -->
```

Find icons at: https://fontawesome.com/icons (free icons only)

### Step 2: The color class (`icon-rental`, `icon-driver`, etc.) controls the color. Reuse an existing class or add a new one in `css/style.css`.

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

### Step 1: Add HTML in `index.html` inside `<div class="swiper-wrapper">`:
```html
<div class="swiper-slide service-card">
    <div class="service-icon icon-newservice"><i class="fas fa-plane"></i></div>
    <h3 data-i18n="services.newservice.title">New Service Name</h3>
    <p data-i18n="services.newservice.desc">Description of the new service.</p>
</div>
```

### Step 2: Add color class in `css/style.css`:
```css
.service-icon.icon-newservice {
    background: rgba(236, 72, 153, 0.1);   /* Light pink */
    color: #EC4899;                         /* Pink */
}
```

### Step 3: Add translations in `js/i18n.js` (both EN and Tamil).

---

## Removing a Service

Delete the entire `<div class="swiper-slide service-card">...</div>` block from `index.html`.

---

## Changing Icon Colors

In `css/style.css`, find the icon class and change colors:
```css
.service-icon.icon-rental {
    background: rgba(59, 130, 246, 0.1);   /* Background — use rgba with 0.1 opacity */
    color: #3B82F6;                         /* Icon color */
}
```

### To revert to old style (blue circle, white icon):
Replace all `.service-icon` styles with:
```css
.service-icon {
    width: 60px;
    height: 60px;
    background: linear-gradient(135deg, var(--blue-dark), var(--blue-mid));
    border-radius: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
    margin: 0 auto 18px;
    color: white;
    font-size: 22px;
}
```
And remove the individual `icon-rental`, `icon-driver`, etc. classes.

---

## Display Behavior

| View | How it shows |
|------|-------------|
| **Laptop** | 3-column grid (all 6 visible) |
| **Tablet** | 2-column grid |
| **Mobile** | Swiper carousel (1 at a time, auto-scroll) |

---

## Card Styling

```css
.service-card {
    background: white;
    padding: 35px 25px;
    border-radius: var(--radius-md);
    box-shadow: var(--shadow-sm);
    text-align: center;
}

.service-card h3 {
    font-size: 16px;
    color: var(--blue-dark);
}

.service-card p {
    font-size: 13px;
    color: var(--gray-500);
}
```

---

## Quick Reference

| Action | What to change | File |
|--------|---------------|------|
| Change service title | `<h3 data-i18n="...">` + i18n | `index.html` + `js/i18n.js` |
| Change service description | `<p data-i18n="...">` + i18n | `index.html` + `js/i18n.js` |
| Change icon | `<i class="fas fa-xxx">` | `index.html` |
| Change icon color | `.service-icon.icon-xxx { color: ...; background: ... }` | `css/style.css` |
| Add a service | Add `service-card` div + CSS color class | `index.html` + `css/style.css` + `js/i18n.js` |
| Remove a service | Delete `service-card` div | `index.html` |
| Revert to blue circle icons | Replace `.service-icon` CSS (see above) | `css/style.css` |
