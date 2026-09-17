# Logo Management Guide

## Current Logo Details

| Property | Value |
|----------|-------|
| File | `assets/logo.jpg` |
| Display size | 50 x 50 px (set in CSS) |
| Fit | `object-fit: contain` (scales to fit, no cropping) |
| Background | Transparent / none |

---

## Where the Logo Appears

| Location | File | Size | Notes |
|----------|------|------|-------|
| **Header (navbar)** | `index.html` line ~20 | 50x50 px | Main logo next to "GANESH HOLIDAYS" text |
| **Footer** | `index.html` line ~421 | 50x50 px | Same logo with slight brightness boost |
| **Review page** | `review.html` line ~144 | 50x50 px (inline style) | Shown above "Thank You for Traveling with Us" |

All three point to the same file: `assets/logo.jpg`

---

## Recommended Logo Size

| Setting | Value |
|---------|-------|
| **Image size** | **200 x 200 pixels** (square) |
| **Format** | JPG (solid background) or PNG (transparent background) |
| **File size** | Under 100KB |
| **Background** | Transparent PNG preferred (blends with any header color) |

**Why 200x200?** The logo displays at 50x50 on screen. A 200x200 source image gives 4x resolution — looks sharp on high-DPI (Retina) screens without being too large in file size.

**Why square?** The container is 50x50 square. A square logo fits perfectly. Non-square logos will be scaled down to fit within the square (with `object-fit: contain`), leaving empty space on the sides.

---

## How to Update the Logo

### Simple replace (same filename):
1. Save your new logo as `logo.jpg` (overwrite the file)
2. Upload to `assets/` folder on GitHub
3. Done — all 3 locations (header, footer, review page) update automatically

### If switching from JPG to PNG (for transparency):
1. Save as `logo.png`
2. Update 3 references in the code:

**index.html** (2 places):
```html
<!-- Header — line ~20 -->
<img src="assets/logo.png" alt="Ganesh Holidays Logo" class="logo-img">

<!-- Footer — line ~421 -->
<img src="assets/logo.png" alt="Ganesh Holidays Logo" class="logo-img logo-img-footer">
```

**review.html** (1 place):
```html
<!-- Line ~144 -->
<img src="assets/logo.png" alt="Ganesh Holidays" ...>
```

3. Push all 3 files

---

## If the Logo Looks Too Small or Too Big

The display size is controlled in `css/style.css`. Find this section:

```css
.logo-icon {
    position: relative;
    flex-shrink: 0;
    width: 50px;      /* ← Change this for logo width */
    height: 50px;     /* ← Change this for logo height */
    overflow: visible;
    border-radius: 0;
    background: none;
}
```

| Want | Change to |
|------|-----------|
| **Smaller logo** | `width: 40px; height: 40px;` |
| **Current size** | `width: 50px; height: 50px;` |
| **Bigger logo** | `width: 60px; height: 60px;` |
| **Much bigger** | `width: 70px; height: 70px;` |

**Note:** Making the logo bigger than 70px may push the header to be too tall. Keep it between 40-70px.

### For the review page logo only:
The review page uses inline styles. Find this in `review.html`:
```html
<div class="icon" style="width:50px; height:50px; margin:0 auto;">
```
Change `50px` to your desired size.

---

## If the Logo Looks Cropped or Stretched

The current CSS uses `object-fit: contain` which **never crops or stretches** — it scales the logo to fit inside the 50x50 box while maintaining the aspect ratio.

If you see issues:
- **Logo has extra whitespace around it** → Crop the whitespace from the image file before uploading
- **Logo appears with a colored background box** → Save as PNG with transparent background
- **Logo looks blurry** → Upload a higher resolution version (at least 200x200)

---

## Generating a New Logo with Gemini / ChatGPT

### Prompt for Gemini:
```
Generate a professional logo for "Ganesh Holidays" — an All India tour and travel company based in South India.
Size: 200x200 pixels, square.
Background: Transparent.
Style: Include Lord Ganesha icon, car/road element, gold and blue color scheme.
The letters "GH" should be prominent.
Modern, premium travel brand feel.
Output as PNG with transparent background.
```

### After generating:
1. Download the image
2. If file is large, compress at https://tinyjpg.com
3. Rename to `logo.jpg` (or `logo.png` if transparent)
4. Upload to `assets/` folder on GitHub
5. If it looks too big/small, adjust the CSS width/height as described above

---

## Logo Color Considerations

| Header color | Logo background recommendation |
|-------------|-------------------------------|
| Dark navy (current) | Transparent PNG or dark background |
| Light/cream | Transparent PNG or white background |
| Any color | Transparent PNG works with everything |

**Best practice:** Always use transparent PNG — it works regardless of header color changes.

---

## Removing the Logo

### Remove from header only (keep in footer and review page):
In `index.html`, find the header logo section (~line 20) and delete or comment it out:

```html
<!-- DELETE or comment this block -->
<div class="logo-icon">
    <img src="assets/logo.jpg" alt="Ganesh Holidays Logo" class="logo-img">
</div>
```

The "GANESH HOLIDAYS" text will remain — just the image is removed.

### Remove from everywhere:
Delete the same block from 3 places:
1. `index.html` — header (~line 20)
2. `index.html` — footer (~line 421)
3. `review.html` — review page header (~line 144)

---

## Quick Reference

| Action | What to do |
|--------|-----------|
| Replace logo (same format) | Overwrite `assets/logo.jpg`, push |
| Replace logo (different format) | Update `index.html` (2 places) + `review.html` (1 place) |
| Make logo bigger/smaller | Change `width` and `height` in `.logo-icon` in `css/style.css` |
| Logo looks blurry | Upload higher resolution (200x200 minimum) |
| Logo has white box | Save as PNG with transparent background |
| Remove from header only | Delete `logo-icon` div in header section of `index.html` |
| Remove from everywhere | Delete from `index.html` (2 places) + `review.html` (1 place) |
