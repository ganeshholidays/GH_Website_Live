# Header (Navbar) Guide

## Current Header Setup

| Property | Value |
|----------|-------|
| Background | Dark navy `rgba(15, 23, 42, 0.95)` |
| Position | Fixed at top (stays visible while scrolling) |
| Height | ~70px (logo 50px + padding) |
| Border | Subtle gold line at bottom |
| Blur | `backdrop-filter: blur(12px)` |
| Text color | White |
| Tagline color | Gold `#f6ad55` |

---

## What the Header Contains

| Element | Details |
|---------|---------|
| Logo | 50x50 image (see Logo_Guide.md) |
| Brand name | "GANESH HOLIDAYS" — white, bold |
| Tagline | "YOUR JOURNEY, OUR COMMITMENT" — gold, small |
| Nav links | Home, About, Services, Packages, Gallery, Reviews, Contact — white, bold |
| Language toggle | EN / தமிழ் — pill buttons |
| Hamburger menu | Mobile only (☰) — white lines |

---

## Changing the Header Background Color

### In `css/style.css`, find:
```css
.navbar {
    position: fixed;
    top: 0;
    left: 0;
    right: 0;
    z-index: 1000;
    background: rgba(15, 23, 42, 0.95);
    backdrop-filter: blur(12px);
    -webkit-backdrop-filter: blur(12px);
    border-bottom: 1px solid rgba(246, 173, 85, 0.15);
    transition: var(--transition);
}
```

### Color options:

| Style | CSS | Look |
|-------|-----|------|
| **Dark navy (current)** | `background: rgba(15, 23, 42, 0.95);` | Professional, dark |
| **Pure black** | `background: rgba(0, 0, 0, 0.9);` | Sleek, modern |
| **Dark charcoal** | `background: rgba(45, 45, 45, 0.95);` | Subtle, warm dark |
| **White/cream** | `background: rgba(255, 252, 245, 0.95);` | Light, clean |
| **Light grey** | `background: rgba(240, 242, 245, 0.95);` | Neutral |
| **Light blue** | `background: rgba(215, 225, 240, 0.95);` | Soft blue |
| **Fully transparent** | `background: transparent;` | Hero image visible through header |
| **Glass (semi-transparent)** | `background: rgba(0, 0, 0, 0.2);` | Modern glass effect |

### If switching to a light color:
All text is currently white — you need to change text colors too:

```css
/* Change these for light header */
.logo-brand { color: #0f172a; }           /* Dark navy */
.logo-tagline { color: #b8860b; }         /* Dark gold */
.nav-link { color: rgba(15, 23, 42, 0.7); }
.nav-link:hover { color: #0f172a; }
.nav-hamburger span { background: #0f172a; }
.lang-toggle { background: rgba(15, 23, 42, 0.08); }
.lang-btn { color: rgba(15, 23, 42, 0.6); }
```

### If switching to dark color:
Keep current text colors (white) — they already work.

---

## Making the Header Transparent

### Step 1: Change navbar background
```css
.navbar {
    background: rgba(0, 0, 0, 0.2);        /* semi-transparent */
    backdrop-filter: blur(10px);
    -webkit-backdrop-filter: blur(10px);
    border-bottom: none;                     /* remove border */
}
```

### Step 2: Add text shadow for readability
When the header is transparent, text may be hard to read against light images:
```css
.nav-link,
.logo-brand,
.logo-tagline {
    text-shadow: 0 1px 3px rgba(0, 0, 0, 0.5);
}
```

### Step 3: Adjust hero image
The hero image should start from the very top (behind the transparent header):

In `.hero.normal-mode .hero-img`:
```css
padding-top: 0;     /* was 70px */
margin-top: 0;
```

In `.hero.normal-mode .hero-content` (for laptop):
```css
top: calc(50% + 35px);  /* shift down to avoid overlap with header */
```

### Step 4: Consider the logo
Logo may not be visible against some hero images. Options:
- Use a white/outlined version of the logo
- Remove the logo from header (see Logo_Guide.md)
- Keep it if your logo has enough contrast

### Step 5: Test all hero modes
Test with:
- hero-default.jpg (static image)
- hero-video.mp4 (video)
- festival.jpg (festival banner)
- Mobile view
- Desktop view

---

## Changing the Scrolled Header

When the user scrolls down, the header gets a shadow. Find:
```css
.navbar.scrolled {
    box-shadow: 0 2px 15px rgba(0,0,0,0.3);
}
```

You can also change the background on scroll for transparent headers:
```css
.navbar.scrolled {
    background: rgba(15, 23, 42, 0.95);    /* solid on scroll */
    box-shadow: 0 2px 15px rgba(0,0,0,0.3);
}
```

This makes the header transparent at top → solid when scrolled. Very modern look.

---

## Changing Nav Link Style

### Font weight:
```css
.nav-link {
    font-weight: 600;    /* Current: bold. Change to 400 for normal */
}
```

### Font size:
```css
.nav-link {
    font-size: 14px;     /* Current. Change to 15px or 16px for larger */
}
```

### Hover effect:
Currently a gold underline appears on hover. Find:
```css
.nav-link::after {
    ...
    background: var(--gold);   /* Change color of underline */
    ...
}
```

---

## Changing Brand Name and Tagline

### Text content:
In `index.html`, find (~line 23-28):
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
    font-size: 16px;         /* Change size */
    color: #ffffff;           /* Change color */
    letter-spacing: 1.5px;
}
```

### Tagline style:
```css
.logo-tagline {
    font-family: 'Josefin Sans', sans-serif;
    font-weight: 400;
    font-size: 9px;           /* Change size */
    color: #f6ad55;           /* Change color — gold */
    letter-spacing: 2px;
    text-transform: uppercase;
}
```

---

## Mobile Menu (Hamburger)

### Current setup:
- Hamburger icon (☰) shows on screens < 768px
- Slide-in menu from right side
- White background, dark text

### Menu background:
In `css/style.css` under `@media (max-width: 768px)`:
```css
.nav-menu {
    background: white;    /* Change for different mobile menu color */
}

.nav-menu .nav-link {
    color: #1a365d;       /* Dark text for white menu */
}
```

---

## Quick Reference

| Action | What to change | File |
|--------|---------------|------|
| Header background color | `.navbar { background: ... }` | `css/style.css` |
| Make transparent | `.navbar { background: transparent; }` | `css/style.css` |
| Border at bottom | `.navbar { border-bottom: ... }` | `css/style.css` |
| Nav link color | `.nav-link { color: ... }` | `css/style.css` |
| Nav link font size | `.nav-link { font-size: ... }` | `css/style.css` |
| Brand name text | `<span class="logo-brand">` | `index.html` |
| Tagline text | `<span class="logo-tagline">` | `index.html` |
| Brand name color | `.logo-brand { color: ... }` | `css/style.css` |
| Tagline color | `.logo-tagline { color: ... }` | `css/style.css` |
| Mobile menu color | `.nav-menu { background: ... }` (inside 768px media query) | `css/style.css` |
| Hamburger line color | `.nav-hamburger span { background: ... }` | `css/style.css` |


---

## Website Title (Browser Tab / Google Search)

The page title shows in the browser tab, Chrome history, Google search results, and when shared on WhatsApp/social media.

### Current titles:

| Page | Title | File |
|------|-------|------|
| Main website | Ganesh Holidays - Tour & Travel | `index.html` line 6 |
| Review page | Share Your Experience - Ganesh Holidays | `review.html` line 5 |

### To change:
In `index.html`:
```html
<title>Ganesh Holidays - Tour & Travel</title>
<!-- Change the text between <title> and </title> -->
```

In `review.html`:
```html
<title>Share Your Experience - Ganesh Holidays</title>
```

### Meta description (shows below title in Google search):
```html
<meta name="description" content="Ganesh Holidays - Your trusted All India tour and travel partner. Your Journey, Our Commitment.">
```
Change the `content` text to update what Google shows below your website link in search results.
