# Hero Page — Complete Guide

## Priority Chain (Automatic)

The website checks for files in this order and loads the first one found:

```
1. festival.jpg exists?        → Festival Mode (swaps image)
        ↓ (not found)
2. hero-video.mp4 FILE exists? → Try Video Mode (swaps to video)
        ↓ (video plays)        → Video Mode
        ↓ (slow/blocked)       → Stays on hero-default.jpg (Normal Mode)
        ↓ (file not found)
3. hero-default.jpg            → Already loaded from HTML (instant, no delay)
```

**hero-default.jpg loads instantly** — no blank page. JS checks for festival/video in background and swaps if found.

---

## Files

| File | Size | Required? | Purpose |
|------|------|-----------|---------|
| `assets/hero/hero-default.jpg` | 1920 x 1080 (16:9) | **YES — always keep** | Default hero. Loads instantly. Shows with text overlay |
| `assets/hero/hero-video.mp4` | 1920 x 1080 (16:9), under 5MB, 5-8 sec | Optional | Auto-playing video hero |
| `assets/hero/festival.jpg` | 1920 x 1080 (16:9) | Optional | Festival banner (highest priority) |

---

## What Each Mode Shows

### Festival Mode (`festival.jpg`)

| | Desktop | Mobile |
|---|---------|--------|
| Height | `100vh` (full viewport) | Auto (natural landscape height) |
| Fit | `object-fit: cover` (crops bottom) | `object-fit: contain` (full image) |
| Header | Transparent — image fills behind header | Same |
| Text overlay | Hidden | Hidden |
| Dark overlay | Hidden | Hidden |
| Scroll arrow | Hidden | Hidden |

### Video Mode (`hero-video.mp4`)

| | Desktop | Mobile |
|---|---------|--------|
| Height | `100vh` (full viewport) | Auto (natural video height) |
| Fit | Video fills from top, bottom cropped | Full video visible |
| Header | Transparent — video plays behind header | Same |
| Text overlay | Hidden | Hidden |
| Dark overlay | Hidden | Hidden |
| Scroll arrow | Hidden | Hidden |
| Fallback | After 10 sec timeout or fail → stays on hero-default | Same |
| Retry | Retries 2 times at 1-second intervals | Same |

### Normal Mode (`hero-default.jpg`)

| | Desktop | Mobile |
|---|---------|--------|
| Height | Auto (natural image height, scrollable) | `100vh` (full phone screen) |
| Fit | Natural, starts from top behind transparent header | `object-fit: cover` (fills screen) |
| Header | Transparent — image fills behind header | Same |
| Text overlay | ✅ "Explore All of India With Us" + subtitle + button | ✅ Centered |
| Dark overlay | None (currently disabled) | None |
| Scroll arrow | ✅ Visible (white, bouncing) | Hidden |
| Content position (laptop) | `top: 40%` (centered in visible area) | `top: 50%` (centered) |
| Arrow position (laptop) | `top: calc(40% + 130px)` | Hidden |

---

## Fallback Timeline

```
Page loads
    ↓
hero-default.jpg starts loading immediately (from HTML src)
    ↓
Normal mode applied → user sees temple image instantly
    ↓
Check festival.jpg ──── found? ──→ Swap to festival banner
    ↓ (not found)
Check hero-video.mp4 FILE exists? (HEAD request)
    ↓
    ├── File exists:
    │     ├── Video plays in < 10 sec ──→ Swap to video
    │     ├── Video autoplay blocked ──→ Stay on hero-default
    │     └── 10 seconds pass, no video ──→ Stay on hero-default
    │
    └── File NOT found (404):
          ↓
          Stay on hero-default.jpg (already showing)
```

**No blank hero page.** The default image loads from HTML immediately — JS only upgrades to festival/video if available.

---

## How to Use Each Mode

### I want a VIDEO hero
1. Create/download video (1920x1080, under 5MB, 5-8 sec, no audio)
2. Save as `assets/hero/hero-video.mp4`
3. Push to GitHub
4. Website auto-plays video. If video is slow, stays on hero-default.

### I want a FESTIVAL banner
1. Generate banner from Gemini/ChatGPT (1920x1080, landscape)
2. Save as `assets/hero/festival.jpg`
3. Push to GitHub
4. Website shows festival banner (overrides video and everything else)

### Festival is over — remove banner
1. Delete `assets/hero/festival.jpg` from GitHub
2. Website auto-falls back to video → hero-default.jpg

### I want just a STATIC IMAGE (no video)
1. Delete `assets/hero/hero-video.mp4` from GitHub (if exists)
2. Website shows hero-default.jpg with text overlay

### I want to change the DEFAULT hero image
1. Replace `assets/hero/hero-default.jpg` with your new photo
2. This is the final fallback — always present, always works

---

## Transparent Header Integration

Since the header is transparent, all hero modes start from the **very top of the page** — the image/video fills behind the transparent header.

Key CSS (applies to all modes):
```css
.hero {
    padding-top: 0;
    margin-top: 0;
}
```

**If the header is changed back to solid**, you'll need:
```css
.hero {
    padding-top: 70px;  /* push hero below solid header */
}
```
And update video/festival height from `100vh` to `calc(100vh - 70px)`.

---

## Image Specifications

### For hero-default.jpg
- **Resolution:** 1920 x 1080 pixels
- **Aspect ratio:** 16:9 landscape
- **Format:** JPG
- **File size:** Under 500KB (compress at https://tinyjpg.com)

### For hero-video.mp4
- **Resolution:** 1920 x 1080 pixels
- **Duration:** 5-8 seconds (loops automatically)
- **Audio:** No audio (muted)
- **File size:** Under 5MB (compress at https://www.freeconvert.com/video-compressor)

### For festival.jpg
- **Resolution:** 1920 x 1080 pixels
- **Format:** JPG
- **File size:** Under 500KB
- **Text placement:** Keep important text centered (edges may be cropped on desktop)

---

## Quick Reference

| Action | What to do |
|--------|-----------|
| Show video | Upload `hero-video.mp4` to `assets/hero/` |
| Show festival banner | Upload `festival.jpg` to `assets/hero/` |
| Remove festival | Delete `festival.jpg` from `assets/hero/` |
| Remove video | Delete `hero-video.mp4` from `assets/hero/` |
| Change default image | Replace `hero-default.jpg` in `assets/hero/` |

---

## How to Create a Poster in Canva

### Step 1: Open Canva
1. Go to https://www.canva.com (login or create free account)
2. Click **Create a design** → **Custom size**
3. Enter: **1920** width x **1080** height (pixels)
4. Click **Create new design**

### Step 2: Design Your Poster

**For festival.jpg:**
1. Left panel → **Elements** → search `diwali` or `pongal` etc.
2. Pick festive backgrounds/elements
3. Add text: `Ganesh Holidays Wishes You a Happy Diwali`
4. Add your logo

### Step 3: Keep Text Centered
**Important:** Keep all text and important elements in the **center area** of the design. On desktop, the edges/bottom may get cropped.

```
┌──────────────────────────────────────────┐
│  edge    │  ★ SAFE ZONE ★  │    edge    │
│ (may     │  Keep all text   │  (may      │
│  crop)   │  and logos here  │   crop)    │
│──────────│──────────────────│────────────│
│          │  bottom may crop on desktop   │
└──────────────────────────────────────────┘
```

### Step 4: Export
1. Click **Share** → **Download**
2. File type: **PNG** or **JPG**
3. If file is over 500KB, compress at https://tinyjpg.com

---

## Sample Gemini/ChatGPT Prompts

### Festival Banners

**Diwali:**
```
Generate a professional travel brand banner, 1920x1080 pixels, 16:9 landscape.
Theme: Happy Diwali.
Include: Diwali diyas/lamps, Indian travel landmarks, fireworks, car on scenic road.
Text on image: "Ganesh Holidays Wishes You a Happy Diwali"
Style: Warm golden light, festive, premium travel brand.
Keep all text centered.
```

**Pongal:**
```
Generate a professional travel brand banner, 1920x1080 pixels, 16:9 landscape.
Theme: Happy Pongal.
Include: Pongal pot with sugarcane, sunrise, South Indian landscape, temple, car.
Text on image: "Ganesh Holidays Wishes You a Happy Pongal"
Style: Warm sunrise tones, festive, traditional South Indian feel.
Keep all text centered.
```

**Onam:**
```
Generate a professional travel brand banner, 1920x1080 pixels, 16:9 landscape.
Theme: Happy Onam.
Include: Kerala backwaters, Onam pookalam, boat, scenic nature.
Text on image: "Ganesh Holidays Wishes You a Happy Onam"
Style: Lush green, vibrant flowers, tropical feel.
Keep all text centered.
```

**New Year:**
```
Generate a professional travel brand banner, 1920x1080 pixels, 16:9 landscape.
Theme: Happy New Year 2027.
Include: Indian travel landmarks, fireworks, celebration, car on highway.
Text on image: "Ganesh Holidays Wishes You a Happy New Year 2027"
Style: Night scene, fireworks, celebratory.
Keep all text centered.
```

---

## Upcoming Festivals Calendar

| Festival | Approx Date | Banner Theme |
|----------|-------------|-------------|
| Ganesh Chaturthi | Aug/Sep | Lord Ganesha, temple, blessings |
| Onam | Aug/Sep | Kerala, flowers, boat |
| Navratri | Sep/Oct | Durga, vibrant colors, dance |
| Diwali | Oct/Nov | Diyas, fireworks, golden light |
| Christmas | Dec 25 | Winter, celebration, landmarks |
| New Year | Jan 1 | Fireworks, new beginnings |
| Pongal / Sankranti | Jan 14-15 | Pongal pot, sunrise, harvest |
| Republic Day | Jan 26 | India Gate, tricolor, patriotic |
| Tamil New Year | Apr 14 | Traditional, kolam, fresh start |
| Independence Day | Aug 15 | Tricolor, landmarks, patriotic |

**Tip:** Generate banners 2-3 days before the festival.

---

## Important Notes

- **File format:** The code expects `.jpg` for images. If you want to use `.png` instead, update these locations:

### For hero-default.png:
**File 1: `index.html`** (~line 54):
```html
<!-- Change this -->
<img src="assets/hero/hero-default.jpg" alt="India Travel" class="hero-img">
<!-- To this -->
<img src="assets/hero/hero-default.png" alt="India Travel" class="hero-img">
```

**File 2: `js/main.js`** (in the hero detection code):
```javascript
// Change this
heroImg.src = 'assets/hero/hero-default.jpg';
// To this (appears twice in the file — update both)
heroImg.src = 'assets/hero/hero-default.png';
```

### For festival.png:
**File: `js/main.js`**:
```javascript
// Change this
var festivalFile = 'assets/hero/festival.jpg';
// To this
var festivalFile = 'assets/hero/festival.png';
```

### Simplest approach:
Save your PNG file but rename it to `.jpg` before uploading. Browsers handle this fine — no code changes needed. For example, save as `hero-default.jpg` even if it's a PNG file.

- **File size:** Keep images under **500KB** and videos under **5MB**
- **Compress images:** https://tinyjpg.com (free)
- **Compress videos:** https://www.freeconvert.com/video-compressor (free)
- **File names are case-sensitive** — use exactly `festival.jpg`, `hero-video.mp4`, `hero-default.jpg` (all lowercase)
- **Browser cache:** After uploading/deleting, clear cache (Ctrl+Shift+R) or open in incognito
