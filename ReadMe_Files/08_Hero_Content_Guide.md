# Hero Content Guide (Title, Subtitle, Button, Arrow)

## Current Content

The hero section (for hero-default.jpg / normal-mode) shows these elements:

```
        Explore All of India With Us              ← Title (hero-title)
South India's trusted road travel partner...      ← Subtitle (hero-subtitle)
        [ View Tour Packages ]                    ← Button (glass/frosted, white border)

                  ⌄                               ← Down arrow (white, bouncing)
```

**Note:** These are only visible in normal-mode (hero-default.jpg). In video-mode and festival-mode, all text is hidden.

---

## Where to Change the Text

### In `index.html` (~line 58-62):
```html
<div class="hero-content">
    <h1 class="hero-title" data-i18n="hero.title">Explore All of India With Us</h1>
    <p class="hero-subtitle" data-i18n="hero.subtitle">South India's trusted road travel partner — comfortable car journeys across India</p>
    <a href="#packages" class="btn btn-primary" data-i18n="hero.cta">View Tour Packages</a>
</div>
```

### Also update translations in `js/i18n.js`:

**English section:**
```javascript
"hero.title": "Explore All of India With Us",
"hero.subtitle": "South India's trusted road travel partner — comfortable car journeys across India",
"hero.cta": "View Tour Packages",
```

**Tamil section:**
```javascript
"hero.title": "எங்களுடன் இந்தியா முழுவதும் பயணியுங்கள்",
"hero.subtitle": "...",
"hero.cta": "டூர் பேக்கேஜ்களைப் பார்க்க",
```

**Important:** Update both English AND Tamil.

---

## Title Styling

### Current CSS:
```css
.hero-title {
    font-size: clamp(2rem, 5vw, 3.5rem);
    font-weight: 800;
    color: white;
    margin-bottom: 16px;
    line-height: 1.2;
}
```

| Property | Current | Options |
|----------|---------|---------|
| **Font size** | `clamp(2rem, 5vw, 3.5rem)` | Smaller: `clamp(1.5rem, 4vw, 3rem)`, Bigger: `clamp(2.5rem, 6vw, 4rem)` |
| **Font weight** | `800` (extra bold) | `400` normal, `600` semi-bold, `700` bold |
| **Color** | `white` | `#f6ad55` for gold, any color |
| **Space below** | `margin-bottom: 16px` | Increase to `24px` or `30px` for more gap |

---

## Subtitle Styling

### Current CSS:
```css
.hero-subtitle {
    font-size: clamp(1rem, 2vw, 1.2rem);
    color: #ffffff;
    max-width: 600px;
    margin: 0 auto 30px;
    font-weight: 300;
}
```

| Property | Current | Options |
|----------|---------|---------|
| **Color** | `#ffffff` (pure white) | `rgba(255,255,255,0.85)` for slight transparency |
| **Font weight** | `300` (light) | `400` normal, `600` semi-bold |
| **Space below** | `30px` | Gap before the button |

---

## Button Styling

### Current CSS (glass/frosted):
```css
.btn-primary {
    background: rgba(255, 255, 255, 0.15);
    color: var(--blue-dark);
    border: 2px solid rgba(15, 23, 42, 0.2);
    backdrop-filter: blur(10px);
}
```

### On hero image (white version):
```css
.hero.normal-mode .hero-content .btn-primary {
    background: rgba(255, 255, 255, 0.2);
    color: #ffffff;
    border: 2px solid #ffffff;
}
```

| Property | Current | Options |
|----------|---------|---------|
| **Background** | Frosted glass | `var(--gold)` for gold, `#ffffff` for solid white |
| **Text color** | White (on hero) | `var(--gray-900)` for dark |
| **Border** | White `#ffffff` | `transparent`, any color |

### Button link:
Currently links to `#packages`. Change `href` to:
- `#contact` — scroll to Contact
- `#services` — scroll to Services
- `https://wa.me/919443943153` — open WhatsApp

---

## Down Arrow Styling

### Current CSS:
```css
.hero.normal-mode .hero-scroll i {
    color: rgba(255, 255, 255, 0.8);
    font-size: 24px;
}
```

| Property | Current | Options |
|----------|---------|---------|
| **Color** | White 80% | `#ffffff` pure white, `#f6ad55` gold |
| **Size** | `24px` | `20px` smaller, `30px` bigger |
| **Animation** | Bouncing | Remove: delete `animation` line |

### Arrow icon:
```html
<i class="fas fa-chevron-down"></i>
```
Other options: `fa-arrow-down`, `fa-angle-down`, `fa-angles-down`

### Arrow click:
Currently scrolls to About section. Change target:
```javascript
document.getElementById('about')    // → About
document.getElementById('services') // → Services
document.getElementById('packages') // → Packages
```

### Arrow visibility:

| View | Status |
|------|--------|
| Laptop | ✅ Visible (bouncing) |
| Mobile | ❌ Hidden |

---

## Positioning — Move Content Up or Down

### All 3 (title + subtitle + button) together:

**For laptop** (in `@media (min-width: 769px)`):
```css
.hero.normal-mode .hero-content {
    top: 40%;    /* Current — lower number = higher */
}
```
| Want | Change to |
|------|-----------|
| Move up | `top: 30%;` or `top: 35%;` |
| Center | `top: 50%;` |
| Move down | `top: 55%;` or `top: 60%;` |

**For mobile** (in `@media (max-width: 768px)`):
```css
.hero.normal-mode .hero-content {
    top: 50%;    /* Current — centered */
}
```

### Down arrow position:

**For laptop** (in `@media (min-width: 769px)`):
```css
.hero.normal-mode .hero-scroll {
    top: calc(40% + 130px);    /* 130px below content */
}
```
**Rule:** Arrow `top` = Content `top` + `130px`

**For mobile:** Arrow is hidden.

### Gaps between elements:

| Gap | CSS | Current |
|-----|-----|---------|
| Title → Subtitle | `.hero-title { margin-bottom: 16px; }` | 16px |
| Subtitle → Button | `.hero-subtitle { margin: 0 auto 30px; }` | 30px |
| Button → Arrow | Difference between content and arrow `top` values | 130px |

---

## Quick Reference

| Action | What to change | File |
|--------|---------------|------|
| Change title text | `<h1 class="hero-title">` + i18n | `index.html` + `js/i18n.js` |
| Change subtitle text | `<p class="hero-subtitle">` + i18n | `index.html` + `js/i18n.js` |
| Change button text | `<a class="btn btn-primary">` + i18n | `index.html` + `js/i18n.js` |
| Title font size | `.hero-title { font-size: ... }` | `css/style.css` |
| Title color | `.hero-title { color: ... }` | `css/style.css` |
| Subtitle color | `.hero-subtitle { color: ... }` | `css/style.css` |
| Button background | `.hero.normal-mode .hero-content .btn-primary { background: ... }` | `css/style.css` |
| Button border | `.hero.normal-mode .hero-content .btn-primary { border: ... }` | `css/style.css` |
| Arrow color | `.hero.normal-mode .hero-scroll i { color: ... }` | `css/style.css` |
| Arrow icon | `<i class="fas fa-chevron-down">` | `index.html` |
| Move content up/down (laptop) | `.hero.normal-mode .hero-content { top: ... }` in min-width:769px | `css/style.css` |
| Move content up/down (mobile) | `.hero.normal-mode .hero-content { top: ... }` in max-width:768px | `css/style.css` |
| Move arrow (laptop) | `.hero.normal-mode .hero-scroll { top: ... }` in min-width:769px | `css/style.css` |
