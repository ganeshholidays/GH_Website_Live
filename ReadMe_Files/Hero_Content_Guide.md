# Hero Content Guide (Title, Subtitle, Button, Arrow)

## Current Content

The hero section (for hero-default.jpg / normal-mode) shows 3 elements:

```
        Explore All of India With Us              ← Title (hero-title)
South India's trusted road travel partner...      ← Subtitle (hero-subtitle)
        [ View Tour Packages ]                    ← Button (btn-primary)

                  ⌄                               ← Down arrow (hero-scroll)
```

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
"hero.subtitle": "தென் இந்தியாவின் நம்பகமான பயணத் தோழன் — இந்தியா முழுவதும் வசதியான கார் பயணங்கள்",
"hero.cta": "டூர் பேக்கேஜ்களைப் பார்க்க",
```

**Important:** Update both English AND Tamil translations when changing text.

---

## Title Styling

### Current CSS (in `css/style.css`):
```css
.hero-title {
    font-size: clamp(2rem, 5vw, 3.5rem);
    font-weight: 800;
    color: white;
    margin-bottom: 16px;
    line-height: 1.2;
}
```

### What you can change:

| Property | Current | Options |
|----------|---------|---------|
| **Font size** | `clamp(2rem, 5vw, 3.5rem)` | `clamp(1.5rem, 4vw, 3rem)` for smaller, `clamp(2.5rem, 6vw, 4rem)` for bigger |
| **Font weight** | `800` (extra bold) | `400` normal, `600` semi-bold, `700` bold, `800` extra bold |
| **Color** | `white` | Any color — `#f6ad55` for gold, `#ffffff` for white |
| **Space below title** | `margin-bottom: 16px` | Increase to `24px` or `30px` for more gap before subtitle |

### Mobile override (in 768px media query):
```css
.hero-title {
    font-size: 2rem;    /* Smaller on mobile */
}
```

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

### What you can change:

| Property | Current | Options |
|----------|---------|---------|
| **Font size** | `clamp(1rem, 2vw, 1.2rem)` | Make bigger/smaller |
| **Color** | `#ffffff` (white) | `rgba(255,255,255,0.85)` for slight transparency, `#f6ad55` for gold |
| **Font weight** | `300` (light) | `400` normal, `600` semi-bold |
| **Max width** | `600px` | `500px` for narrower, `800px` for wider |
| **Space below subtitle** | `margin: 0 auto 30px` | Change `30px` — gap before the button |

### Extra space before button (laptop only):
```css
.hero.normal-mode .hero-content .hero-subtitle {
    margin-bottom: 40px;    /* Current — change for more/less space */
}
```

---

## Button Styling

### Current CSS:
```css
.btn {
    display: inline-block;
    padding: 12px 28px;
    border-radius: 25px;
    font-size: 14px;
    font-weight: 600;
    cursor: pointer;
    transition: var(--transition);
    border: 2px solid transparent;
    text-align: center;
}

.btn-primary {
    background: var(--gold);         /* Gold #f6ad55 */
    color: var(--gray-900);          /* Dark text */
    border-color: var(--gold);
}

.btn-primary:hover {
    background: var(--gold-dark);
    border-color: var(--gold-dark);
    transform: translateY(-2px);
    box-shadow: 0 8px 25px rgba(246, 173, 85, 0.3);
}
```

### What you can change:

| Property | Current | Options |
|----------|---------|---------|
| **Background color** | Gold (`var(--gold)`) | `#ffffff` white, `#0f172a` dark navy, any color |
| **Text color** | Dark (`var(--gray-900)`) | `#ffffff` white (if dark background button) |
| **Border radius** | `25px` (pill shape) | `8px` for rounded rectangle, `0` for square |
| **Padding** | `12px 28px` | `15px 35px` for bigger, `10px 20px` for smaller |
| **Font size** | `14px` | `16px` for bigger text |
| **Border** | Transparent | `2px solid #ffffff` for outline button |

### Button text:
Change in `index.html`:
```html
<a href="#packages" class="btn btn-primary" data-i18n="hero.cta">View Tour Packages</a>
```
And update `js/i18n.js` for both EN and Tamil.

### Button link:
Currently links to `#packages` (scrolls to Packages section). Change `href` to:
- `#contact` — scroll to Contact
- `#services` — scroll to Services
- `review.html` — open review page
- `https://wa.me/917708109824` — open WhatsApp

---

## Down Arrow Styling

### Current CSS:
```css
.hero.normal-mode .hero-scroll i {
    color: rgba(255, 255, 255, 0.8);    /* White, 80% opacity */
    font-size: 24px;
}
```

### What you can change:

| Property | Current | Options |
|----------|---------|---------|
| **Color** | White 80% | `#ffffff` pure white, `#f6ad55` gold, `rgba(0,0,0,0.5)` dark |
| **Size** | `24px` | `20px` smaller, `30px` bigger |
| **Animation** | Bouncing (`bounceDown 2s infinite`) | Remove animation: delete `animation` line |

### Arrow icon:
In `index.html`:
```html
<div class="hero-scroll" onclick="document.getElementById('about').scrollIntoView({behavior:'smooth'})">
    <i class="fas fa-chevron-down"></i>
</div>
```

Change the icon class to:
- `fa-chevron-down` — current (⌄)
- `fa-arrow-down` — solid arrow (↓)
- `fa-angle-down` — wider angle
- `fa-angles-down` — double angle (⏬)

### Arrow click behavior:
Currently scrolls to About section. Change `'about'` to scroll elsewhere:
```javascript
document.getElementById('about')    // scrolls to About
document.getElementById('services') // scrolls to Services
document.getElementById('packages') // scrolls to Packages
```

### Arrow visibility:

| View | Currently |
|------|-----------|
| Laptop | ✅ Visible (bouncing) |
| Mobile | ❌ Hidden |

To show on mobile too, find in `@media (max-width: 768px)`:
```css
.hero.normal-mode .hero-scroll {
    display: none;    /* Change to: display: block; */
}
```

---

## Positioning — Move Content Up or Down

### All 3 (title + subtitle + button) together:

**For laptop** (in `@media (min-width: 769px)`):
```css
.hero.normal-mode .hero-content {
    top: 40%;    /* Current. Lower number = higher position */
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
    top: calc(40% + 130px);    /* 130px below the content position */
}
```
If you move content to `35%`, change arrow to `calc(35% + 130px)`.

**Rule:** Arrow `top` = Content `top` + `130px` (keeps consistent gap).

**For mobile:**
Arrow is hidden — no adjustment needed.

### Gap between title and subtitle:
```css
.hero-title {
    margin-bottom: 16px;    /* Space between title and subtitle */
}
```

### Gap between subtitle and button:
```css
.hero-subtitle {
    margin: 0 auto 30px;    /* 30px = space before button */
}
```

Laptop-specific override:
```css
.hero.normal-mode .hero-content .hero-subtitle {
    margin-bottom: 40px;    /* More space on laptop */
}
```

### Gap between button and arrow:
Controlled by the difference between content `top` and arrow `top`.
Currently: content at `40%`, arrow at `40% + 130px` = 130px gap.
- Want less gap: change `130px` to `100px`
- Want more gap: change `130px` to `160px`

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
| Button color | `.btn-primary { background: ... }` | `css/style.css` |
| Button text color | `.btn-primary { color: ... }` | `css/style.css` |
| Arrow color | `.hero.normal-mode .hero-scroll i { color: ... }` | `css/style.css` |
| Arrow icon | `<i class="fas fa-chevron-down">` | `index.html` |
| Move content up/down (laptop) | `.hero.normal-mode .hero-content { top: ... }` in min-width:769px | `css/style.css` |
| Move content up/down (mobile) | `.hero.normal-mode .hero-content { top: ... }` in max-width:768px | `css/style.css` |
| Move arrow up/down (laptop) | `.hero.normal-mode .hero-scroll { top: ... }` in min-width:769px | `css/style.css` |
| Gap: title → subtitle | `.hero-title { margin-bottom: ... }` | `css/style.css` |
| Gap: subtitle → button | `.hero-subtitle { margin: 0 auto Xpx }` | `css/style.css` |
| Gap: button → arrow | Difference between content top and arrow top values | `css/style.css` |
