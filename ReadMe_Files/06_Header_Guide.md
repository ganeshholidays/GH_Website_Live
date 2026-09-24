# Header (Navbar) Guide

## Current Header Setup

| Property | Value |
|----------|-------|
| Background (at top) | **Transparent** — hero image visible behind |
| Background (on scroll) | Dark navy `rgba(15, 23, 42, 0.95)` with blur |
| Position | Fixed at top (stays visible while scrolling) |
| Height | ~70px (logo 50px + padding) |
| Border | None |
| Text color | Bright white `#ffffff` with text shadow |
| Tagline color | Gold `#f6ad55` with text shadow |
| Transition | Smooth 0.4s fade between transparent and solid |

---

## How the Header Behaves

```
At top of page (hero visible):
┌─────────────────────────────────────────────────┐
│ 🔆 GANESH HOLIDAYS  Home About Services ... EN  │  ← transparent, white text
│                                                  │
│         (hero image visible behind header)       │
└─────────────────────────────────────────────────┘

After scrolling down:
┌─────────────────────────────────────────────────┐
│ 🔆 GANESH HOLIDAYS  Home About Services ... EN  │  ← solid dark navy + blur
├─────────────────────────────────────────────────┤
│         About Ganesh Holidays                    │
└─────────────────────────────────────────────────┘
```

---

## What the Header Contains

| Element | Details | Color |
|---------|---------|-------|
| Logo | 50x50 image (see Logo_Guide.md) | — |
| Brand name | "GANESH HOLIDAYS" | White `#ffffff` + text shadow |
| Tagline | "YOUR JOURNEY, OUR COMMITMENT" | Gold `#f6ad55` + text shadow |
| Nav links | Home, About, Services, Packages, Gallery, Reviews, Contact | White `#ffffff` + text shadow |
| Language toggle | EN / தமிழ் | White border, white text, active = white fill dark text |
| Hamburger menu | Mobile only (☰) | White lines |

---

## Current CSS (in `css/style.css`)

### Navbar:
```css
.navbar {
    position: fixed;
    top: 0;
    left: 0;
    right: 0;
    z-index: 1000;
    background: transparent;
    backdrop-filter: none;
    -webkit-backdrop-filter: none;
    border-bottom: none;
    transition: background 0.4s ease, box-shadow 0.4s ease, backdrop-filter 0.4s ease;
}

.navbar.scrolled {
    background: rgba(15, 23, 42, 0.95);
    backdrop-filter: blur(12px);
    -webkit-backdrop-filter: blur(12px);
    box-shadow: 0 2px 20px rgba(0,0,0,0.3);
}
```

### Nav links:
```css
.nav-link {
    font-size: 14px;
    font-weight: 600;
    color: #ffffff;
    text-shadow: 0 1px 4px rgba(0, 0, 0, 0.4);
}
```

### Language toggle:
```css
.lang-toggle {
    background: transparent;
    border: 1px solid #ffffff;
    border-radius: 20px;
    padding: 0px;
}

.lang-btn {
    color: #ffffff;
}

.lang-btn.active {
    background: #ffffff;
    color: #0f172a;
    border-radius: 18px;
}
```

---

## Changing the Header Background Color

### To make it solid (not transparent):
```css
.navbar {
    background: rgba(15, 23, 42, 0.95);  /* solid dark navy */
    backdrop-filter: blur(12px);
    border-bottom: 1px solid rgba(246, 173, 85, 0.15);  /* optional gold border */
}
```

### Color options:

| Style | CSS |
|-------|-----|
| **Transparent (current)** | `background: transparent;` |
| **Solid dark navy** | `background: rgba(15, 23, 42, 0.95);` |
| **Pure black** | `background: rgba(0, 0, 0, 0.9);` |
| **Glass dark** | `background: rgba(0, 0, 0, 0.3); backdrop-filter: blur(10px);` |
| **Glass white** | `background: rgba(255, 255, 255, 0.2); backdrop-filter: blur(10px);` |

### If switching to a light/white header:
Text colors need to change from white to dark:
```css
.logo-brand { color: #0f172a; text-shadow: none; }
.logo-tagline { color: #b8860b; text-shadow: none; }
.nav-link { color: rgba(15, 23, 42, 0.7); text-shadow: none; }
.nav-link:hover { color: #0f172a; }
.nav-hamburger span { background: #0f172a; }
.lang-toggle { border-color: #0f172a; }
.lang-btn { color: #0f172a; }
.lang-btn.active { background: #0f172a; color: #ffffff; }
```

---

## Hero Image and Transparent Header

Since the header is transparent, the hero image fills from the **very top** of the page (behind the header). Key CSS:
```css
.hero {
    padding-top: 0;   /* no gap — image starts from top */
    margin-top: 0;
}
```

If you switch back to a solid header, you'll need to add padding so the image starts below:
```css
.hero {
    padding-top: 70px;  /* push content below solid header */
}
```

---

## Scrolled Header Behavior

When the user scrolls down, JavaScript adds the `.scrolled` class to `.navbar`. This is handled in `js/main.js`:
```javascript
window.addEventListener('scroll', () => {
    if (window.scrollY > 50) {
        navbar.classList.add('scrolled');
    } else {
        navbar.classList.remove('scrolled');
    }
});
```

To change when it kicks in, change `50` to a higher/lower number.

---

## Changing Nav Link Style

### Font weight:
```css
.nav-link {
    font-weight: 600;    /* Current: bold. 400 for normal */
}
```

### Font size:
```css
.nav-link {
    font-size: 14px;     /* Current. 16px for larger */
}
```

### Text shadow (for readability on transparent header):
```css
.nav-link {
    text-shadow: 0 1px 4px rgba(0, 0, 0, 0.4);  /* Current */
}
```
Remove `text-shadow` if using a solid header.

---

## Changing Brand Name and Tagline

### Text content:
In `index.html` (~line 23-28):
```html
<div class="logo-text">
    <span class="logo-brand" data-i18n="nav.brand">GANESH HOLIDAYS</span>
    <span class="logo-tagline" data-i18n="nav.tagline">YOUR JOURNEY, OUR COMMITMENT</span>
</div>
```
Also update Tamil translations in `js/i18n.js`.

### Brand name style:
```css
.logo-brand {
    font-family: 'Sora', sans-serif;
    font-weight: 700;
    font-size: 16px;
    color: #ffffff;
    letter-spacing: 1.5px;
    text-shadow: 0 1px 4px rgba(0, 0, 0, 0.4);
}
```

### Tagline style:
```css
.logo-tagline {
    font-family: 'Josefin Sans', sans-serif;
    font-weight: 400;
    font-size: 9px;
    color: #f6ad55;
    letter-spacing: 2px;
    text-transform: uppercase;
    text-shadow: 0 1px 4px rgba(0, 0, 0, 0.4);
}
```

---

## Website Title (Browser Tab / Google Search)

### Current titles:

| Page | Title | File |
|------|-------|------|
| Main website | Ganesh Holidays - Tours & Travels | `index.html` line 6 |
| Review page | Share Your Experience - Ganesh Holidays | `review.html` line 5 |

### To change:
```html
<title>Ganesh Holidays - Tours & Travels</title>
```

### Meta description (shows below title in Google search):
```html
<meta name="description" content="Ganesh Holidays - Your trusted All India tour and travel partner. Your Journey, Our Commitment.">
```

---

## Mobile Menu (Hamburger)

### Current setup:
- Hamburger icon (☰) shows on screens < 768px
- White lines (matching transparent header)
- Slide-in menu from right side — white background, dark text

### Hamburger line color:
```css
.nav-hamburger span {
    background: #ffffff;  /* White for transparent header */
}
```

### Mobile menu background:
```css
.nav-menu {
    background: white;
}

.nav-menu .nav-link {
    color: #1a365d;
}
```

### Mobile language toggle:
```css
.lang-toggle {
    padding: 0px;  /* No gap between border and active button */
}
```

---

## Quick Reference

| Action | What to change | File |
|--------|---------------|------|
| Header background | `.navbar { background: ... }` | `css/style.css` |
| Scrolled header background | `.navbar.scrolled { background: ... }` | `css/style.css` |
| Remove transparency | Set solid `background`, add `border-bottom` | `css/style.css` |
| Nav link color | `.nav-link { color: ... }` | `css/style.css` |
| Nav link font size | `.nav-link { font-size: ... }` | `css/style.css` |
| Text shadow | `.nav-link, .logo-brand, .logo-tagline { text-shadow: ... }` | `css/style.css` |
| Brand name text | `<span class="logo-brand">` | `index.html` |
| Tagline text | `<span class="logo-tagline">` | `index.html` |
| Brand name color | `.logo-brand { color: ... }` | `css/style.css` |
| Tagline color | `.logo-tagline { color: ... }` | `css/style.css` |
| Lang toggle border | `.lang-toggle { border: ... }` | `css/style.css` |
| Lang active style | `.lang-btn.active { background: ...; color: ... }` | `css/style.css` |
| Mobile menu color | `.nav-menu { background: ... }` (inside 768px media query) | `css/style.css` |
| Hamburger line color | `.nav-hamburger span { background: ... }` | `css/style.css` |
| Website title | `<title>` tag | `index.html` / `review.html` |
| Meta description | `<meta name="description">` | `index.html` / `review.html` |
| Hero padding (if switching to solid header) | `.hero { padding-top: 70px; }` | `css/style.css` |
