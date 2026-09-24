# Travel Gallery Section Guide

## How the Gallery Works

1. Photos are listed in `assets/photos.json`
2. JavaScript reads the JSON and creates swiper slides
3. Photos are loaded from `assets/gallery/` folder
4. Gallery auto-scrolls on both mobile and desktop
5. "View All Photos" button opens a lightbox popup with all photos
6. Click any photo in lightbox → full-size viewer with left/right navigation

---

## Current Photos

Listed in `assets/photos.json`:
```json
[
  "chennai-1.jpg",
  "coutralam.jpg",
  "glass-bridge.jpg.webp",
  "Kerala.jpg",
  "kodai-1.avif",
  "kodai-2.avif",
  "mahab.avif",
  "ooty-train.avif",
  "thanjavur-temple.avif",
  "tirupati.jpg"
]
```

---

## Adding New Photos

### Step 1: Upload photo
Upload your photo to `assets/gallery/` folder on GitHub.

### Step 2: Update photos.json
Add the filename to `assets/photos.json`:
```json
[
  "chennai-1.jpg",
  "coutralam.jpg",
  ...existing photos...,
  "new-photo.jpg"
]
```

### Step 3: Push
Push both the image file and `photos.json`.

**Image specs:**
| Setting | Value |
|---------|-------|
| Size | **800 x 600 pixels** or similar (landscape preferred) |
| Format | JPG, PNG, WebP, or AVIF |
| File size | Under 300KB per photo |
| Location | `assets/gallery/` folder |

---

## Removing Photos

1. Remove the filename from `assets/photos.json`
2. Optionally delete the image file from `assets/gallery/`
3. Push

---

## Gallery Display

| View | How it shows |
|------|-------------|
| **Laptop** | 3 photos visible, auto-scrolling carousel |
| **Mobile** | 1 photo visible, auto-scrolling carousel |
| **Both** | Loop infinitely, auto-scroll every 2.2 seconds |

---

## "View All Photos" Button

Opens a popup lightbox with all photos in a grid:
- **Laptop:** 3-column grid
- **Mobile:** 2-column grid
- Click any photo → full-size viewer
- Arrow keys (← →) to navigate in viewer
- Escape key to close

### Button text:
In `index.html`:
```html
<button class="btn btn-outline" id="viewAllGallery" data-i18n="gallery.viewAll">View All Photos</button>
```

Update in `js/i18n.js` for both EN and Tamil.

---

## Section Title and Subtitle

In `index.html`:
```html
<h2 class="section-title" data-i18n="gallery.title">Travel Gallery</h2>
<p class="section-subtitle" data-i18n="gallery.subtitle">Moments from our happy travellers</p>
```

Update in `js/i18n.js` for both EN and Tamil.

---

## Styling

### Gallery image in carousel:
```css
.gallery-item {
    height: 200px;                /* Image height in carousel */
    border-radius: var(--radius-sm);
    overflow: hidden;
}
```

### Lightbox grid:
```css
.lightbox-grid {
    grid-template-columns: repeat(3, 1fr);   /* 3 columns on desktop */
    gap: 12px;
}

.lightbox-grid img {
    height: 180px;               /* Thumbnail height in lightbox */
}
```

---

## Quick Reference

| Action | What to change | File |
|--------|---------------|------|
| Add a photo | Upload to `assets/gallery/` + add to `photos.json` | Both |
| Remove a photo | Remove from `photos.json` | `assets/photos.json` |
| Change section title | `<h2 data-i18n="gallery.title">` + i18n | `index.html` + `js/i18n.js` |
| Change button text | `<button id="viewAllGallery">` + i18n | `index.html` + `js/i18n.js` |
| Carousel image height | `.gallery-item { height: ... }` | `css/style.css` |
| Lightbox columns | `.lightbox-grid { grid-template-columns: ... }` | `css/style.css` |
| No limit on photos | Add as many as you want to `photos.json` | — |
