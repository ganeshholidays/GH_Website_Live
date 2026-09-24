# Logo Editing Guide — Source Files & Tools

## File Formats You'll Receive

| Format | What it is | Editable? | Use for |
|--------|-----------|-----------|---------|
| **.ai** | Adobe Illustrator file | ✅ Full editing (vector) | **Master source file — keep this safe** |
| **.eps** | Encapsulated PostScript (vector) | ✅ Full editing (vector) | Alternative to .ai — works in most design tools |
| **.psd** | Adobe Photoshop file | ✅ Full editing (layers) | Pixel-based editing — colors, effects, text |
| **.pdf** | Portable Document Format | ⚠️ Limited editing | Viewing, printing, some editing possible |
| **.png** | PNG image | ❌ Not editable (flat image) | **Use this for website** (supports transparency) |
| **.jpg** | JPEG image | ❌ Not editable (flat image) | **Use this for website** (smaller file size, no transparency) |
| **.doc** | Word document | ❌ Not for editing logo | Documentation/reference only |

### Which files to keep:
- **Keep `.ai` and `.eps` files safe** — these are the editable source files. Back them up to Google Drive or OneDrive.
- **Use `.png` or `.jpg` for the website** — these are the final output files.
- The 300 DPI files are for **printing** (business cards, banners). For website, you need 72 DPI (see conversion below).

---

## Free Tools to Edit Logo Files

### 1. Canva (Easiest — Browser/Mobile)

| | Detail |
|---|--------|
| **URL** | https://www.canva.com |
| **Cost** | Free (Pro features paid) |
| **Supports** | PNG, JPG, PDF, SVG |
| **Cannot open** | .ai, .eps, .psd |
| **Best for** | Adding text, changing colors on PNG/JPG, resizing |

**How to use:**
1. Go to Canva → Create a design → Custom size (200x200 for logo)
2. Upload your PNG logo
3. Change colors, add text, resize
4. Download as PNG (transparent) or JPG

**Limitation:** Can't edit vector files (.ai, .eps) or layered files (.psd). Only works with flat images.

---

### 2. Photopea (Best Free Tool — Browser)

| | Detail |
|---|--------|
| **URL** | https://www.photopea.com |
| **Cost** | Completely free |
| **Supports** | ✅ .ai, .eps, .psd, .pdf, .png, .jpg, .svg — **opens everything** |
| **Best for** | Full logo editing — change colors, fonts, shapes, export for web |

**This is the tool you should use for editing the source files.**

**How to edit your logo:**

#### Open the file:
1. Go to https://www.photopea.com
2. Click **File → Open** → select your `.ai`, `.eps`, or `.psd` file
3. The logo opens with all layers/elements editable

#### Change colors:
1. In the **Layers panel** (right side), click on the layer you want to change
2. Go to **Image → Adjustments → Hue/Saturation**
3. Move the **Hue** slider to change color
4. Or: **Edit → Fill** → pick a new color

#### Change text/fonts:
1. Click the **Text tool** (T) in the left toolbar
2. Click on the text in the logo
3. Change the font, size, or text content in the top toolbar
4. Free fonts available at https://fonts.google.com — download and upload to Photopea

#### Resize for website:
1. Go to **Image → Image Size**
2. Change to **200 x 200 pixels** (or your desired size)
3. Resolution: **72 DPI** (for web — not 300 DPI which is for print)

#### Export for website:
1. **File → Export As → PNG** (if you need transparency)
2. Or **File → Export As → JPG** (smaller file size, no transparency)
3. Save and upload to GitHub

---

### 3. Inkscape (Free Desktop App — For Vector Files)

| | Detail |
|---|--------|
| **Download** | https://inkscape.org |
| **Cost** | Completely free |
| **Supports** | ✅ .ai, .eps, .svg, .pdf, .png |
| **Cannot open** | .psd |
| **Best for** | Vector editing — scale logo to any size without quality loss |

**How to use:**
1. Download and install Inkscape
2. File → Open → select `.ai` or `.eps` file
3. Edit shapes, colors, text
4. File → Export PNG Image → set size → Export

---

### 4. GIMP (Free Desktop App — For PSD Files)

| | Detail |
|---|--------|
| **Download** | https://www.gimp.org |
| **Cost** | Completely free |
| **Supports** | ✅ .psd, .png, .jpg, .pdf |
| **Cannot open** | .ai, .eps (limited) |
| **Best for** | Pixel editing — like Photoshop but free |

---

### Tool Recommendation Summary

| I want to... | Use this tool |
|--------------|---------------|
| Quick color/text change on PNG | **Canva** (browser) |
| Edit .ai / .eps / .psd files (full editing) | **Photopea** (browser, free) |
| Edit vector files on desktop | **Inkscape** (free download) |
| Edit PSD files on desktop | **GIMP** (free download) |
| Just resize/compress for web | **Photopea** or https://tinyjpg.com |

**My recommendation: Photopea** — it opens everything (.ai, .eps, .psd, .pdf), runs in browser (no install), and is completely free.

---

## Converting 300 DPI to Web-Ready (72 DPI)

The designer will share files at **300 DPI** (for print). For web, you need **72 DPI** and smaller dimensions.

### Using Photopea:
1. Open the file at https://www.photopea.com
2. Go to **Image → Image Size**
3. Change:
   - Width: **200 pixels** (for logo) or **1920 pixels** (for hero image)
   - Resolution: **72** pixels/inch
4. Click OK
5. **File → Export As → PNG** (for logo) or **JPG** (for hero)

### Using online tools:
1. Go to https://www.iloveimg.com/resize-image
2. Upload your image
3. Set width to 200px (logo) or 1920px (hero)
4. Download

---

## Logo Versions to Ask the Designer For

Ask your designer to provide these versions:

| Version | Background | Format | Size | Use for |
|---------|-----------|--------|------|---------|
| **Icon only** (square) | Transparent | PNG | 200x200 px | Website header/footer (current setup) |
| **Icon + Text** (wide) | Transparent | PNG | 500x120 px | Website header if you want text in logo |
| **Icon + Text** (white) | Transparent | PNG | 500x120 px | Dark/transparent header |
| **Icon + Text** (dark) | Transparent | PNG | 500x120 px | Light header (if you change later) |
| **Full color** | White background | JPG | 1000x1000 px | Social media, Google Business |
| **Source files** | — | .ai + .eps + .psd | Original | Keep safe for future edits |

---

## Where to Store Source Files

**Do NOT upload source files (.ai, .eps, .psd) to GitHub** — they're large and not needed for the website.

Store them safely in:
- **Google Drive** — free 15GB, access from anywhere
- **OneDrive** — if you have Microsoft account
- **External hard drive/USB** — physical backup

Only upload the web-ready `.png` or `.jpg` files to GitHub `assets/` folder.

---

## Common Editing Tasks

### Change logo background from white to transparent:
1. Open in Photopea (https://www.photopea.com)
2. Use **Magic Wand tool** (W) → click on the white background
3. Press **Delete** → background becomes transparent (checkered pattern)
4. File → Export As → **PNG** (must be PNG for transparency)

### Change logo text color:
1. Open `.ai` or `.psd` in Photopea
2. Click the **Text tool** (T)
3. Select the text
4. Change color in the top toolbar
5. Export as PNG

### Change logo icon color:
1. Open `.ai` or `.psd` in Photopea
2. Click on the icon layer in Layers panel
3. **Image → Adjustments → Hue/Saturation** → shift the Hue slider
4. Export as PNG

### Make logo smaller for web:
1. Open in Photopea
2. **Image → Image Size** → set to 200x200 pixels, 72 DPI
3. Export as PNG or JPG
4. If still large, compress at https://tinyjpg.com

---

## Quick Reference

| Task | Tool | Steps |
|------|------|-------|
| Edit .ai/.eps/.psd | Photopea (browser) | photopea.com → File → Open → edit → Export |
| Quick resize/color on PNG | Canva (browser) | canva.com → upload → edit → download |
| Remove white background | Photopea | Magic Wand → select white → Delete → Export PNG |
| Convert 300 DPI to 72 DPI | Photopea | Image → Image Size → 72 DPI → Export |
| Compress file size | TinyJPG | tinyjpg.com → upload → download |
| Edit vectors on desktop | Inkscape | inkscape.org → install → open .ai/.eps → edit |
| Edit PSD on desktop | GIMP | gimp.org → install → open .psd → edit |
