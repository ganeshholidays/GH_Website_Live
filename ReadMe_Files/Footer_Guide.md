# Footer Guide

## Current Footer Content

| Section | Content |
|---------|---------|
| Brand | Logo + "GANESH HOLIDAYS" |
| Description | Your trusted All-India tour and travel partner... |
| Quick Links | Home, About, Services, Packages, Contact |
| Popular Destinations | Ooty, Kerala, Rameshwaram, Pondicherry, Madurai & Coorg |
| Copyright | © 2025 Ganesh Holidays. All rights reserved. |

---

## Where to Change Text

### In `index.html` (~line 415-460):

**Brand description:**
```html
<p data-i18n="footer.desc">Your trusted All-India tour and travel partner. Making every journey memorable since 2020.</p>
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
Change `2025` to current year.

---

## Adding a New Quick Link

Add inside the Quick Links `footer-links` div:
```html
<a href="#gallery" data-i18n="nav.gallery">Gallery</a>
```

---

## Adding a New Destination

Add inside the Popular Destinations `footer-links` div:
```html
<a href="#packages">New Destination Name</a>
```

---

## Changing or Removing the Footer Logo

The footer has the same logo as the header. To remove:
```html
<!-- DELETE this block -->
<div class="logo-icon">
    <img src="assets/logo.jpg" alt="Ganesh Holidays Logo" class="logo-img logo-img-footer">
</div>
```

See `Logo_Guide.md` for more details.

---

## Footer Styling

### Background color:
```css
.footer {
    background: var(--blue-dark);    /* Dark navy — change color here */
    color: rgba(255,255,255,0.7);
    padding: 60px 0 0;
}
```

### Footer link color:
```css
.footer-links a {
    color: rgba(255,255,255,0.6);    /* Link color */
}

.footer-links a:hover {
    color: var(--gold);               /* Hover color — gold */
}
```

### Footer heading color:
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
| Footer background color | `.footer { background: ... }` | `css/style.css` |
| Link color | `.footer-links a { color: ... }` | `css/style.css` |
| Link hover color | `.footer-links a:hover { color: ... }` | `css/style.css` |
