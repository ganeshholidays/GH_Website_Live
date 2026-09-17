# Contact Section Guide

## Current Contact Details

| Item | Current Value |
|------|--------------|
| Phone | +91 7708109824 |
| WhatsApp | +91 7708109824 |
| Email | ganeshholidays2026@gmail.com |
| Address | Melavasal, Mannargudi - 614001 |
| Facebook | facebook.com/profile.php?id=61592954153497 |
| Instagram | instagram.com/ganeshholidays |
| YouTube | youtube.com/@Ganeshholidays |

---

## Where to Change Contact Details

### In `index.html` (~line 349-395):

**Phone:**
```html
<a href="tel:+917708109824">+91 7708109824</a>
<!-- Change both the href and display text -->
```

**WhatsApp:**
```html
<a href="https://wa.me/917708109824" target="_blank">+91 7708109824</a>
<!-- Change the number in both href (no + or spaces) and display text -->
```

**Email:**
```html
<a href="mailto:ganeshholidays2026@gmail.com">ganeshholidays2026@gmail.com</a>
<!-- Change both href and display text -->
```

**Address:**
```html
<p data-i18n="contact.address.text">Melavasal, Mannargudi - 614001</p>
```
Also update in `js/i18n.js`.

---

## Social Media Links

```html
<a href="https://www.facebook.com/profile.php?id=61592954153497" ...>
<a href="https://www.instagram.com/ganeshholidays..." ...>
<a href="https://www.youtube.com/@Ganeshholidays" ...>
```

### Adding a new social link:
```html
<a href="https://twitter.com/yourhandle" target="_blank" rel="noopener noreferrer" aria-label="Twitter">
    <i class="fab fa-twitter"></i>
</a>
```

Social media icons:
| Platform | Icon Class |
|----------|-----------|
| Facebook | `fab fa-facebook-f` |
| Instagram | `fab fa-instagram` |
| YouTube | `fab fa-youtube` |
| Twitter/X | `fab fa-twitter` |
| LinkedIn | `fab fa-linkedin-in` |
| WhatsApp | `fab fa-whatsapp` |

---

## Enquiry Form

The contact form currently submits via WhatsApp. The form fields:

| Field | Required | Name |
|-------|----------|------|
| Your Name | Yes | `name` |
| Phone Number | Yes | `phone` |
| Destination | No | `destination` |
| Your Message | No | `message` |

### Form action:
Currently uses JavaScript to build a WhatsApp message and open WhatsApp:
```javascript
const whatsappMsg = encodeURIComponent(
    `Hello Ganesh Holidays!\n\nName: ${name}\nPhone: ${phone}\nDestination: ${destination}\nMessage: ${message}`
);
window.open(`https://wa.me/917708109824?text=${whatsappMsg}`, '_blank');
```

### To change the WhatsApp number:
In `js/main.js`, find:
```javascript
window.open(`https://wa.me/917708109824?text=${whatsappMsg}`, '_blank');
```
Change `917708109824` to the new number (country code + number, no + or spaces).

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

Update in `js/i18n.js` for both EN and Tamil.

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
| Change WhatsApp number | `href="https://wa.me/..."` and display text + JS | `index.html` + `js/main.js` |
| Change email | `href="mailto:..."` and display text | `index.html` |
| Change address | `<p data-i18n="contact.address.text">` + i18n | `index.html` + `js/i18n.js` |
| Change social links | `<a href="...">` | `index.html` |
| Add social link | Add new `<a>` with icon | `index.html` |
| Change form labels | `<label data-i18n="...">` + i18n | `index.html` + `js/i18n.js` |
| Change form WhatsApp number | `wa.me/NUMBER` in main.js | `js/main.js` |
