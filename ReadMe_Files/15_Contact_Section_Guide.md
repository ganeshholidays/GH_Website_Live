# Contact Section Guide

## Current Contact Details

| Item | Current Value |
|------|--------------|
| Phone (primary) | +91 9443943153 |
| Phone (secondary) | +91 7708109824 |
| WhatsApp | +91 9443943153 |
| Email | ganeshholidays2026@gmail.com |
| Address | Melavasal, Mannargudi - 614001 (links to Google Maps) |
| Facebook | facebook.com/profile.php?id=61592954153497 |
| Instagram | instagram.com/ganeshholidays |
| YouTube | youtube.com/@Ganeshholidays |

---

## Icon Colors (Modern / Brand-Colored)

### Contact icons (grey circle, brand-colored icon):

| Icon | Color | CSS Class |
|------|-------|-----------|
| 📞 Phone | Blue `#0078d4` | `.fa-phone` |
| WhatsApp | Green `#25D366` | `.fa-whatsapp` |
| ✉️ Email | Red `#EA4335` (Gmail) | `.fa-envelope` |
| 📍 Address | Orange `#FF6D00` (Maps) | `.fa-map-marker-alt` |

### Social icons (grey circle, brand-colored icon):

| Icon | Color | CSS Selector |
|------|-------|-------------|
| Facebook | Blue `#1877F2` | `a[aria-label="Facebook"]` |
| Instagram | Pink `#E4405F` | `a[aria-label="Instagram"]` |
| YouTube | Red `#FF0000` | `a[aria-label="YouTube"]` |
| WhatsApp | Green `#25D366` | `a[aria-label="WhatsApp"]` (if added) |

---

## Where to Change Contact Details

### In `index.html` (~line 320-355):

**Phone (both numbers):**
```html
<a href="tel:+919443943153">+91 9443943153</a>
<br>
<a href="tel:+917708109824">+91 7708109824</a>
```

**WhatsApp:**
```html
<a href="https://wa.me/919443943153" target="_blank">+91 9443943153</a>
```

**Email:**
```html
<a href="mailto:ganeshholidays2026@gmail.com">ganeshholidays2026@gmail.com</a>
```

**Address (links to Google Maps):**
```html
<a href="https://www.google.com/maps/search/Melavasal,+Mannargudi+614001" target="_blank" rel="noopener noreferrer" data-i18n="contact.address.text">Melavasal, Mannargudi - 614001</a>
```

### WhatsApp number in enquiry form:
In `js/main.js`:
```javascript
window.open(`https://wa.me/919443943153?text=${whatsappMsg}`, '_blank');
```

---

## Changing Icon Colors

### Contact item icons:
In `css/style.css`:
```css
.contact-item .fa-phone { color: #0078d4; }
.contact-item .fa-whatsapp { color: #25D366; }
.contact-item .fa-envelope { color: #EA4335; }
.contact-item .fa-map-marker-alt { color: #FF6D00; }
```

### Social media icons:
```css
.contact-social a[aria-label="Facebook"] { color: #1877F2; }
.contact-social a[aria-label="Instagram"] { color: #E4405F; }
.contact-social a[aria-label="YouTube"] { color: #FF0000; }
```

### To revert all icons to blue:
```css
.contact-item i {
    background: var(--blue-dark);
    color: white;
}
.contact-social a {
    color: var(--blue-dark);
}
```

---

## Social Media Links

```html
<a href="https://www.facebook.com/..." aria-label="Facebook"><i class="fab fa-facebook-f"></i></a>
<a href="https://www.instagram.com/..." aria-label="Instagram"><i class="fab fa-instagram"></i></a>
<a href="https://www.youtube.com/..." aria-label="YouTube"><i class="fab fa-youtube"></i></a>
```

### Adding a new social link:
```html
<a href="https://twitter.com/yourhandle" target="_blank" rel="noopener noreferrer" aria-label="Twitter">
    <i class="fab fa-twitter"></i>
</a>
```

Also add color in CSS:
```css
.contact-social a[aria-label="Twitter"] { color: #1DA1F2; }
```

Social media icon classes:
| Platform | Class |
|----------|-------|
| Facebook | `fab fa-facebook-f` |
| Instagram | `fab fa-instagram` |
| YouTube | `fab fa-youtube` |
| Twitter/X | `fab fa-twitter` |
| LinkedIn | `fab fa-linkedin-in` |
| WhatsApp | `fab fa-whatsapp` |

---

## Enquiry Form

### Current behavior:
Form submits via WhatsApp — builds a message and opens WhatsApp with pre-filled text.

### Form fields:

| Field | Required | Name |
|-------|----------|------|
| Your Name | Yes | `name` |
| Phone Number | Yes | `phone` |
| Destination | No | `destination` |
| Your Message | No | `message` |

### Button style:
Currently uses glass/frosted style (same as all buttons):
```css
.btn-primary {
    background: rgba(255, 255, 255, 0.15);
    color: var(--blue-dark);
    border: 2px solid rgba(15, 23, 42, 0.2);
    backdrop-filter: blur(10px);
}
```

### To change the WhatsApp number for enquiry:
In `js/main.js`:
```javascript
window.open(`https://wa.me/919443943153?text=${whatsappMsg}`, '_blank');
//                    ^^^^^^^^^^^^^ change this number
```

### Form field labels:
Update in both `index.html` and `js/i18n.js`:
```javascript
"contact.form.name": "Your Name",
"contact.form.phone": "Phone Number",
"contact.form.destination": "Destination",
"contact.form.message": "Your Message",
"contact.form.submit": "Send Enquiry",
```

---

## Section Title and Subtitle

```html
<h2 class="section-title" data-i18n="contact.title">Contact Us</h2>
<p class="section-subtitle" data-i18n="contact.subtitle">Get in touch for bookings and enquiries</p>
```

---

## Display Behavior

| View | Layout |
|------|--------|
| **Laptop** | 2 columns — contact info left, form right |
| **Mobile** | Stacked — contact info on top, form below |

---

## Quick Reference

| Action | What to change | File |
|--------|---------------|------|
| Change phone number | `href="tel:..."` and display text | `index.html` |
| Change WhatsApp number | `href="https://wa.me/..."` + display text + JS | `index.html` + `js/main.js` |
| Change email | `href="mailto:..."` and display text | `index.html` |
| Change address | `<a href="https://www.google.com/maps/search/..."` + text | `index.html` + `js/i18n.js` |
| Change social links | `<a href="...">` | `index.html` |
| Add social link | Add new `<a>` with icon + CSS color | `index.html` + `css/style.css` |
| Change icon color | `.contact-item .fa-xxx { color: ... }` | `css/style.css` |
| Change social icon color | `.contact-social a[aria-label="..."] { color: ... }` | `css/style.css` |
| Change form labels | `<label data-i18n="...">` + i18n | `index.html` + `js/i18n.js` |
| Change enquiry WhatsApp number | `wa.me/NUMBER` in main.js | `js/main.js` |
