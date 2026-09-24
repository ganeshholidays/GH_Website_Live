# Ganesh Holidays - Complete Project Plan

## Overview

| Item | Detail |
|------|--------|
| **Website** | https://ganeshholidays.in |
| **GitHub URL** | https://ganeshholidays.github.io/GH_Website_Live |
| **Business** | Tours & Travels (South India based, All India coverage) |
| **Languages** | Tamil (தமிழ்) and English — toggle in header |
| **Access** | Public — anyone with the URL can access |
| **Devices** | Auto-detects mobile/tablet/laptop and loads appropriate view |
| **Maintenance** | Minimal — review approval via Google Sheet, hero/gallery updates via file upload |
| **Design Theme** | Modern — transparent header, glass buttons, brand-colored icons |
| **Hosting** | GitHub Pages (free) |
| **Repository** | https://github.com/ganeshholidays/GH_Website_Live |
| **Domain** | ganeshholidays.in (BigRock) |

---

## Current Status

| Feature | Status |
|---------|--------|
| Main website (index.html) | ✅ Live |
| Review form (review.html) | ✅ Live |
| Bilingual (EN/Tamil) | ✅ Working |
| Mobile responsive | ✅ Working |
| Desktop grid layout | ✅ Working |
| Swiper carousels (mobile) | ✅ Working |
| Gallery auto-scroll + View All lightbox | ✅ Working |
| Touch pause on swipe | ✅ Working |
| Custom logo | ✅ Done |
| Custom domain (ganeshholidays.in) | ✅ Live |
| Google Sheets review system | ✅ Live (all reviews from Google Sheet) |
| Transparent header | ✅ Live |
| Modern icons (brand-colored) | ✅ Live |
| Glass/frosted buttons | ✅ Live |
| Hero auto-detection (festival/video/default) | ✅ Working |
| Google Business Profile | ✅ Set up |

---

## Hosting

| Detail | Value |
|--------|-------|
| Platform | GitHub Pages (free forever) |
| Repository | GH_Website_Live |
| Deploy method | Upload files to GitHub → auto-deploys in ~1 minute |
| SSL/HTTPS | Auto (free) |
| Custom domain | ganeshholidays.in (BigRock, ~₹500-700/year) |
| Uptime | 99.99% |

---

## Design Theme (Modern)

| Element | Current Style |
|---------|--------------|
| Header | Transparent at top → solid dark navy on scroll |
| Nav text | Bright white with text shadow |
| Language toggle | Transparent with white border, active = white fill |
| Buttons | Glass/frosted — semi-transparent with blur |
| Service icons | Pastel background + colored icon (rounded square) |
| Why Choose Us icons | Flat colored (no background) |
| Contact icons | Brand colors on grey circle |
| Social icons | Brand colors on grey circle |
| Review arrows | White circle, dark arrow |
| Back to top | White circle, dark navy arrow |
| Hero | Starts from top (behind transparent header) |

---

## Contact Details

| Item | Value |
|------|-------|
| Phone (primary) | +91 9443943153 |
| Phone (secondary) | +91 7708109824 |
| WhatsApp | +91 9443943153 |
| Email | ganeshholidays2026@gmail.com |
| Address | Melavasal, Mannargudi - 614001 |
| Facebook | facebook.com/profile.php?id=61592954153497 |
| Instagram | instagram.com/ganeshholidays |
| YouTube | youtube.com/@Ganeshholidays |

---

## Bilingual Support (Tamil + English)

- All text content stored in `js/i18n.js` with translations
- Language toggle in header switches instantly (no page reload)
- User's language preference saved in browser
- Default language: English

---

## Responsive Design

| Device | Screen Width | Layout |
|--------|-------------|--------|
| Mobile | < 768px | Single column, hamburger menu, swiper carousels |
| Tablet | 768px – 1024px | Two columns, compact nav |
| Desktop | > 1024px | Full 3-column grid, side-by-side content, hover effects |

---

## Website Sections

### Header / Navigation Bar (Fixed, Transparent)
- Logo (50x50, `assets/logo.jpg`)
- Brand name: "GANESH HOLIDAYS" — white with text shadow
- Tagline: "YOUR JOURNEY, OUR COMMITMENT" — gold with text shadow
- Language toggle: EN / தமிழ் — white border, modern pill style
- Menu: Home | About | Services | Packages | Gallery | Reviews | Contact
- Transparent at top → solid dark navy on scroll
- Mobile: hamburger menu with slide-in panel

### Hero Section (Auto-Detection)
- Priority: `festival.jpg` → `hero-video.mp4` → `hero-default.jpg`
- hero-default.jpg loads instantly (from HTML src)
- Text overlay: "Explore All of India With Us" + subtitle + button
- Starts from top of page (behind transparent header)
- Down arrow on desktop (bouncing, clickable)

### About Section
- Company story (Vignesh Ganesan, Mannargudi)
- Animated counters: 5 Years, 200 Customers, 30 Destinations, 100% On-Time

### Services (6 cards, modern icons)
- Rental Car (blue), Acting Driver (purple), Customized Holidays (amber)
- Pilgrimage Tours (red), Family Tours (green), Corporate Travel (indigo)
- Desktop: 3-column grid | Mobile: swiper carousel

### Packages (6 cards with images)
- Ooty, Kerala, Rameshwaram, Pondicherry, Coorg, Thiruchendur
- Badges: Popular, Trending
- "Enquire Now" → scrolls to contact form
- Desktop: 3-column grid | Mobile: swiper carousel

### Why Choose Us (6 items, flat colored icons)
- Safe (green), Transparent Pricing (blue), 24/7 Support (amber)
- South India Experts (red), Customizable (purple), We Care (pink)
- Desktop: 3-column grid | Mobile: swiper carousel

### Travel Gallery
- Photos loaded from `assets/photos.json`
- Auto-scrolling carousel (both mobile and desktop)
- "View All Photos" → lightbox popup with grid + full-size viewer
- Keyboard navigation (arrows, escape)

### Customer Experiences (Reviews)
- All reviews from Google Sheet (no hardcoded reviews)
- Star ratings, feedback text, customer name, trip destination
- "Read More" for long reviews (opens popup)
- Desktop: 3 visible, auto-scroll, white circle arrows
- Mobile: 1 visible, auto-scroll
- "Loading reviews..." spinner while fetching
- Auto-retry (2 retries at 1-second intervals)

### Contact Section
- Phone: two numbers (primary + secondary)
- WhatsApp (opens chat with primary number)
- Email (clickable)
- Address (links to Google Maps)
- Social links: Facebook, Instagram, YouTube (brand-colored)
- Enquiry form → submits via WhatsApp

### Footer
- Logo + brand name
- Description: "Your trusted tour and travel partner..."
- Quick links, Popular destinations
- Copyright: © 2025 Ganesh Holidays

### Review Page (review.html)
- Separate page for customer feedback
- Language toggle (modern style matching header)
- Fields: Name, Phone, Destination, Rating, Feedback, Photo upload
- Submits to Google Apps Script → Google Sheet
- Success: green checkmark + thank you message (translatable)
- Back to Home link

---

## Project File Structure

```
GH_tile_scroll/
├── index.html              ← Main website
├── review.html             ← Customer feedback form
├── css/
│   ├── style.css           ← Active stylesheet (modern theme)
│   └── style-modern.css    ← Backup of modern theme
├── js/
│   ├── main.js             ← Navigation, hero detection, reviews, gallery, animations
│   └── i18n.js             ← Tamil/English translations
├── assets/
│   ├── logo.jpg            ← Logo file
│   ├── favicon.svg         ← Browser tab icon
│   ├── photos.json         ← Gallery photo filenames
│   ├── hero/               ← Hero images/video
│   │   ├── hero-default.jpg    ← Default hero (always present)
│   │   ├── hero-video.mp4     ← Optional video
│   │   └── festival.jpg       ← Optional festival banner
│   ├── gallery/            ← Gallery photos
│   └── packages/           ← Package destination images
├── Documents/              ← All guides and documentation
│   ├── Project_Plan.md
│   ├── Deployment_Guide.md
│   ├── Domain_Setup_Guide.md
│   ├── Hero_Page_Guide.md
│   ├── Hero_Content_Guide.md
│   ├── Header_Guide.md
│   ├── Logo_Guide.md
│   ├── About_Section_Guide.md
│   ├── Services_Section_Guide.md
│   ├── Packages_Section_Guide.md
│   ├── WhyChooseUs_Section_Guide.md
│   ├── Gallery_Section_Guide.md
│   ├── User_Review_Guide.md
│   ├── Contact_Section_Guide.md
│   ├── Footer_Guide.md
│   └── Google_Business_Profile_Guide.md
├── CNAME                   ← Custom domain config
└── (backup files)
    ├── index-original_bkp.html
    └── style-bkp-original.css
```

---

## Technology Stack

| Layer | Technology | Purpose |
|-------|-----------|---------|
| Structure | HTML5 | Page layout |
| Styling | CSS3 (custom) | Responsive design, animations, modern theme |
| Interactivity | Vanilla JavaScript | Language toggle, hero detection, counters, reviews |
| Carousels | Swiper.js (CDN) | Mobile/desktop scrolling, gallery |
| Fonts | Google Fonts (Sora, Josefin Sans, Noto Sans Tamil) | Typography |
| Icons | Font Awesome 6.5 (CDN) | UI icons (brand-colored) |
| Hosting | GitHub Pages | Free static hosting |
| Domain | BigRock (ganeshholidays.in) | Custom domain |
| Reviews | Google Sheets + Apps Script | Review storage, approval, display |
| Images | JPG/PNG, lazy-loaded | Fast loading |
| SSL | Auto (GitHub) | HTTPS security |

---

## Review System

- Customers submit via `ganeshholidays.in/review.html`
- Data stored in Google Sheet (`GH_Reviews`)
- You get email notification on new review
- Approve by typing `YES` in Approved column
- Website fetches approved reviews on page load
- No hardcoded reviews — all from Google Sheet
- Auto-retry if fetch fails (2 retries, 1-second intervals)
- "Read More" popup for long reviews
- See `User_Review_Guide.md` for full details

---

## Hero System

- Auto-detects: `festival.jpg` → `hero-video.mp4` → `hero-default.jpg`
- hero-default.jpg loads instantly (no blank page)
- Festival/video checked in background, swapped if found
- All modes work with transparent header (image fills from top)
- See `Hero_Page_Guide.md` for full details

---

## Gallery Management

- Photos listed in `assets/photos.json`
- Upload photo to `assets/gallery/` + add filename to JSON
- No limit on photos
- "View All Photos" → lightbox popup
- See `Gallery_Section_Guide.md` for full details

---

## Cost Summary

| Item | Cost |
|------|------|
| GitHub Pages hosting | ₹0 (free forever) |
| Google Sheets (reviews) | ₹0 (free) |
| Domain (ganeshholidays.in) | ₹500-700/year |
| SSL certificate | ₹0 (auto, free) |
| **Total** | **~₹500-700/year** |

---

## Day-to-Day Operations

| Task | How | Frequency |
|------|-----|-----------|
| Approve reviews | Open Google Sheet → type YES | As reviews come in |
| Add gallery photos | Upload to `assets/gallery/` + update `photos.json` | As needed |
| Festival banner | Upload `festival.jpg` to `assets/hero/` | Before festivals |
| Remove festival banner | Delete `festival.jpg` | After festivals |
| Update hero video | Upload `hero-video.mp4` to `assets/hero/` | As needed |
| Update contact details | Edit `index.html` | Rarely |
| Domain renewal | BigRock dashboard | Yearly |

---

## Documentation Index

| Document | Purpose |
|----------|---------|
| `Project_Plan.md` | This file — full project overview |
| `Deployment_Guide.md` | How to push updates to GitHub |
| `Domain_Setup_Guide.md` | Connect/manage ganeshholidays.in |
| `Hero_Page_Guide.md` | Hero modes — video, festival, default |
| `Hero_Content_Guide.md` | Title, subtitle, button, arrow styling |
| `Header_Guide.md` | Navbar — transparency, colors, styling |
| `Logo_Guide.md` | Logo update, sizing, removal |
| `About_Section_Guide.md` | About text, stats numbers |
| `Services_Section_Guide.md` | Service cards, modern icons |
| `Packages_Section_Guide.md` | Package cards, images, badges |
| `WhyChooseUs_Section_Guide.md` | Why us items, colored icons |
| `Gallery_Section_Guide.md` | Photos, lightbox, photos.json |
| `User_Review_Guide.md` | Google Sheets reviews, approval, troubleshooting |
| `Contact_Section_Guide.md` | Phone, WhatsApp, email, social links |
| `Footer_Guide.md` | Footer links, destinations, copyright |
| `Google_Business_Profile_Guide.md` | Google Business setup, SEO tips |
