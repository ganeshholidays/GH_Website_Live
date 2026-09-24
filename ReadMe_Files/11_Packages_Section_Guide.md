# Packages Section Guide

## Current Packages (6 cards)

| # | Destination | Image File | Badge | i18n Key |
|---|-------------|-----------|-------|----------|
| 1 | Ooty & Kodaikanal | `assets/packages/kodai.jpg` | Popular | `packages.ooty` |
| 2 | Kerala Backwaters | `assets/packages/kerala.jpg` | Trending | `packages.kerala` |
| 3 | Rameshwaram Pilgrimage | `assets/packages/rameshwaram.jpg` | — | `packages.rameshwaram` |
| 4 | Pondicherry & Mahabalipuram | `assets/packages/pondi.jpg` | — | `packages.pondy` |
| 5 | Coorg (Karnataka) | `assets/packages/coorg.jpg` | — | `packages.coorg` |
| 6 | Thiruchendur & Kanyakumari | `assets/packages/thiruchendur.jpg` | — | `packages.thiruchendur` |

---

## Where to Change Text

### In `index.html` (~line 148-215):
Each package card looks like:
```html
<div class="swiper-slide package-card">
    <div class="package-img">
        <img src="assets/packages/kodai.jpg" alt="Ooty" loading="lazy">
        <div class="package-badge" data-i18n="packages.popular">Popular</div>
    </div>
    <div class="package-info">
        <h3 data-i18n="packages.ooty.title">Ooty & Kodaikanal</h3>
        <p class="package-price"><i class="fas fa-map-pin"></i> <span data-i18n="packages.ooty.highlights">Nilgiris, Botanical Garden, Doddabetta, Coaker's Walk</span></p>
        <a href="#enquiryForm" class="btn btn-outline" data-i18n="packages.enquire">Enquire Now</a>
    </div>
</div>
```

### Tamil translations in `js/i18n.js`:
```javascript
"packages.ooty.title": "Ooty & Kodaikanal",
"packages.ooty.highlights": "Nilgiris, Botanical Garden, Doddabetta, Coaker's Walk",
```

---

## Changing the Package Image

### Image specs:
| Setting | Value |
|---------|-------|
| Size | **600 x 400 pixels** (landscape) |
| Format | JPG |
| File size | Under 200KB |
| Location | `assets/packages/` folder |

### Steps:
1. Save your new image to `assets/packages/` folder
2. Update the `src` in `index.html`:
```html
<img src="assets/packages/your-new-image.jpg" alt="Destination" loading="lazy">
```
3. Push both the image and `index.html`

---

## Badges (Popular / Trending)

### Current badges:
| Package | Badge |
|---------|-------|
| Ooty & Kodaikanal | Popular (gold) |
| Kerala Backwaters | Trending (red) |
| All others | No badge |

### Change badge text:
Edit the text inside the badge div:
```html
<div class="package-badge" data-i18n="packages.popular">Popular</div>
<!-- Change "Popular" to anything: "New", "Best Seller", "Hot Deal" etc. -->
```
Also update in `js/i18n.js` for Tamil.

### Remove a badge:
Delete the entire badge line from inside the `package-img` div:
```html
<!-- DELETE this line -->
<div class="package-badge" data-i18n="packages.popular">Popular</div>
```

### Add a badge to a package that doesn't have one:
Add this line right after the `<img>` inside `package-img`:
```html
<div class="package-badge">New</div>
```
For red style:
```html
<div class="package-badge package-badge-hot">Hot Deal</div>
```

### Badge styles:
| Type | Class | Color |
|------|-------|-------|
| Gold (default) | `package-badge` | Gold background |
| Red (hot) | `package-badge package-badge-hot` | Red background |

### Change badge color in `css/style.css`:
```css
.package-badge {
    background: var(--gold);     /* Gold — change to any color */
    color: white;
}

.package-badge-hot {
    background: #e53e3e;         /* Red — change to any color */
}
```

---

## Adding a New Package

Add this block inside `<div class="swiper-wrapper">`:
```html
<div class="swiper-slide package-card">
    <div class="package-img">
        <img src="assets/packages/newdest.jpg" alt="New Destination" loading="lazy">
    </div>
    <div class="package-info">
        <h3 data-i18n="packages.newdest.title">New Destination Name</h3>
        <p class="package-price"><i class="fas fa-map-pin"></i> <span data-i18n="packages.newdest.highlights">Highlight 1, Highlight 2, Highlight 3</span></p>
        <a href="#enquiryForm" class="btn btn-outline" data-i18n="packages.enquire">Enquire Now</a>
    </div>
</div>
```

Also:
1. Upload the image to `assets/packages/`
2. Add translations in `js/i18n.js` for both EN and Tamil

---

## Removing a Package

Delete the entire `<div class="swiper-slide package-card">...</div>` block.

---

## "Enquire Now" Button

All "Enquire Now" buttons link to `#enquiryForm` which scrolls to the Contact form. To change:
- `#enquiryForm` — scroll to contact form
- `https://wa.me/917708109824` — open WhatsApp directly
- `tel:+917708109824` — dial phone

---

## Pricing Note

Below the packages there's a note:
```html
<p class="packages-note" data-i18n="packages.note">
    <i class="fas fa-info-circle"></i> Pricing is based on kilometers travelled...
</p>
```
Update text in `index.html` and `js/i18n.js`.

---

## Display Behavior

| View | How it shows |
|------|-------------|
| **Laptop** | 3-column grid (all 6 visible) |
| **Tablet** | 2-column grid |
| **Mobile** | Swiper carousel (1 at a time, auto-scroll) |

---

## Quick Reference

| Action | What to change | File |
|--------|---------------|------|
| Change destination name | `<h3 data-i18n="...">` + i18n | `index.html` + `js/i18n.js` |
| Change highlights | `<span data-i18n="...">` + i18n | `index.html` + `js/i18n.js` |
| Change image | `<img src="assets/packages/xxx.jpg">` | `index.html` + upload image |
| Add badge | Add `package-badge` div | `index.html` |
| Add a package | Add `package-card` div | `index.html` + `js/i18n.js` |
| Remove a package | Delete `package-card` div | `index.html` |
| Change button link | `<a href="...">` | `index.html` |
| Image size/format | 600x400 JPG, under 200KB | `assets/packages/` |
