# Footer Guide

## Current Footer Content

| Section | Content |
|---------|---------|
| Brand | Logo + "GANESH HOLIDAYS" |
| Description | Your trusted tour and travel partner. Making every journey memorable since 2020. |
| Quick Links | Home, About, Services, Packages, Contact |
| Popular Destinations | Ooty, Kerala, Rameshwaram, Pondicherry, Madurai & Coorg |
| Copyright | © 2025 Ganesh Holidays. All rights reserved. |

---

## Where to Change Text

### In `index.html` (~line 415-460):

**Brand description:**
```html
<p data-i18n="footer.desc">Your trusted tour and travel partner. Making every journey memorable since 2020.</p>
```

**Quick Links:**
```html
<div class="footer-links">
    <h4 data-i18n="footer.quicklinks">Quick Links</h4>
    <a href="#home" data-i18n="nav.home">Home</a>
    <a href="#about" data-i18n="nav.about">About</a>
    <a href="#services" data-i18n="nav.services">Services</a>
    <a href="#packages" data-i18n="nav.packages">Packages</a>
    <a href="#contact" data-i18n="nav.contact">Contact</a>
</div>
```

**Popular Destinations:**
```html
<div class="footer-links">
    <h4 data-i18n="footer.popular">Popular Destinations</h4>
    <a href="#packages">Ooty & Kodaikanal</a>
    <a href="#packages">Kerala Backwaters</a>
    <a href="#packages">Rameshwaram</a>
    <a href="#packages">Pondicherry</a>
    <a href="#packages">Madurai & Coorg</a>
</div>
```

**Copyright year:**
```html
<p>&copy; 2025 Ganesh Holidays. <span data-i18n="footer.rights">All rights reserved.</span></p>
```

---

## Adding/Removing Links

### Add a quick link:
```html
<a href="#gallery" data-i18n="nav.gallery">Gallery</a>
```

### Add a destination:
```html
<a href="#packages">New Destination Name</a>
```

---

## Footer Logo

Same logo as header. To remove:
```html
<!-- DELETE this block -->
<div class="logo-icon">
    <img src="assets/logo.jpg" alt="Ganesh Holidays Logo" class="logo-img logo-img-footer">
</div>
```

See `Logo_Guide.md` for more.

---

## Footer Styling

### Background:
```css
.footer {
    background: var(--blue-dark);
    color: rgba(255,255,255,0.7);
    padding: 60px 0 20px;
}
```

### Link colors:
```css
.footer-links a {
    color: rgba(255,255,255,0.6);
}

.footer-links a:hover {
    color: var(--gold);
}
```

### Heading color:
```css
.footer-links h4 {
    color: white;
    font-size: 16px;
}
```

### Copyright bar:
```css
.footer-bottom {
    border-top: 1px solid rgba(255,255,255,0.1);
    padding: 20px 0;
    margin-top: 40px;
    text-align: center;
}
```

---

## Display Behavior

| View | Layout |
|------|--------|
| **Laptop** | 3 columns — brand, quick links, destinations |
| **Tablet** | 2 columns |
| **Mobile** | Stacked single column |

---

## Quick Reference

| Action | What to change | File |
|--------|---------------|------|
| Change description | `<p data-i18n="footer.desc">` + i18n | `index.html` + `js/i18n.js` |
| Change copyright year | `&copy; 2025` | `index.html` |
| Add quick link | Add `<a href="#section">` | `index.html` |
| Add destination | Add `<a href="#packages">` | `index.html` |
| Remove footer logo | Delete `logo-icon` div | `index.html` |
| Footer background | `.footer { background: ... }` | `css/style.css` |
| Link color | `.footer-links a { color: ... }` | `css/style.css` |
| Link hover color | `.footer-links a:hover { color: ... }` | `css/style.css` |
