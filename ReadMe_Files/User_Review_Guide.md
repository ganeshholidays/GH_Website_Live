# Ganesh Holidays - Review System Guide

## Overview

The review system allows customers to submit feedback about their travel experience. Reviews are stored in a Google Sheet and displayed on the website automatically after your approval.

**Key URLs:**
| What | URL |
|------|-----|
| Website | https://ganeshholidays.in (or https://ganeshholidays.github.io) |
| Review form (send to customers) | https://ganeshholidays.in/review.html |
| Google Sheet (manage reviews) | _(Your Google Sheet URL — bookmark this)_ |

---

## How the System Works

```
Customer fills review form (review.html)
        |
        v
Data is sent to Google Apps Script (Web App URL)
        |
        v
Google Apps Script writes data to your Google Sheet (new row)
        |
        v
You get email notification (new review received)
        |
        v
You open Google Sheet → type "YES" in Approved column
        |
        v
Website fetches approved reviews from Google Sheet on page load
        |
        v
Review appears on the website in "Customer Experiences" section
```

---

## Setting Up Google Sheets (One-Time Setup)

### Step 1: Create the Google Sheet

1. Go to https://sheets.google.com
2. Click **+ Blank** to create a new spreadsheet
3. Rename it: `GH_Reviews`
4. In **Row 1**, add these column headers exactly:

| A | B | C | D | E | F | G |
|---|---|---|---|---|---|---|
| Timestamp | Name | Phone | Destination | Rating | Feedback | Approved |

5. Bookmark this sheet — you'll open it to approve reviews

---

### Step 2: Create Google Apps Script

1. In the Google Sheet, click **Extensions → Apps Script**
2. Delete all existing code in the editor
3. Paste this code:

```javascript
function doPost(e) {
  try {
    var sheet = SpreadsheetApp.getActiveSpreadsheet().getActiveSheet();
    var data = JSON.parse(e.postData.contents);

    // Validate required fields
    if (!data.name || !data.destination || !data.feedback) {
      return ContentService
        .createTextOutput(JSON.stringify({status: 'error', message: 'Missing required fields'}))
        .setMimeType(ContentService.MimeType.JSON);
    }

    // Sanitize inputs - strip HTML tags
    var sanitize = function(str) {
      return String(str).replace(/<[^>]*>/g, '').trim();
    };

    sheet.appendRow([
      new Date().toLocaleString('en-IN', {timeZone: 'Asia/Kolkata'}),
      sanitize(data.name),
      sanitize(data.phone || ''),
      sanitize(data.destination),
      Number(data.rating) || 5,
      sanitize(data.feedback),
      ''  // Approved column - left empty for you to fill
    ]);

    // Send email notification — REPLACE with your actual email
    MailApp.sendEmail({
      to: 'YOUR_EMAIL@gmail.com',
      subject: '⭐ New Review - Ganesh Holidays',
      body: 'New review received!\n\n' +
            'Name: ' + sanitize(data.name) + '\n' +
            'Phone: ' + sanitize(data.phone || 'Not provided') + '\n' +
            'Destination: ' + sanitize(data.destination) + '\n' +
            'Rating: ' + data.rating + '/5\n' +
            'Feedback: ' + sanitize(data.feedback) + '\n\n' +
            '➡️ Open Google Sheet to approve:\n' +
            'YOUR_SHEET_URL'
    });

    return ContentService
      .createTextOutput(JSON.stringify({status: 'success'}))
      .setMimeType(ContentService.MimeType.JSON);

  } catch (err) {
    return ContentService
      .createTextOutput(JSON.stringify({status: 'error', message: err.toString()}))
      .setMimeType(ContentService.MimeType.JSON);
  }
}

function doGet(e) {
  try {
    var sheet = SpreadsheetApp.getActiveSpreadsheet().getActiveSheet();
    var data = sheet.getDataRange().getValues();
    var headers = data[0];
    var approvedIndex = headers.indexOf('Approved');

    var reviews = [];
    for (var i = 1; i < data.length; i++) {
      if (data[i][approvedIndex] &&
          data[i][approvedIndex].toString().toUpperCase() === 'YES') {
        reviews.push({
          timestamp: data[i][0],
          name: data[i][1],
          destination: data[i][3],
          rating: data[i][4],
          feedback: data[i][5]
        });
      }
    }

    return ContentService
      .createTextOutput(JSON.stringify(reviews))
      .setMimeType(ContentService.MimeType.JSON);

  } catch (err) {
    return ContentService
      .createTextOutput(JSON.stringify([]))
      .setMimeType(ContentService.MimeType.JSON);
  }
}
```

4. **IMPORTANT — Replace these two values in the code:**
   - `YOUR_EMAIL@gmail.com` → your actual email address
   - `YOUR_SHEET_URL` → the URL of your Google Sheet (copy from browser address bar)

5. Click **Save** (Ctrl+S)
6. Name the project: `GH Reviews API`

---

### Step 3: Deploy the Apps Script

1. Click **Deploy → New deployment**
2. Click the gear icon (⚙️) next to "Select type" → choose **Web app**
3. Fill in:
   - Description: `GH Reviews API`
   - Execute as: **Me**
   - Who has access: **Anyone**
4. Click **Deploy**
5. Click **Authorize access** when prompted
6. Select your Google account
7. If you see "Google hasn't verified this app" warning:
   - Click **Advanced** (bottom left)
   - Click **Go to GH Reviews API (unsafe)** — this is safe, it's YOUR script
   - Click **Allow**
8. **Copy the Web App URL** that appears
   - It looks like: `https://script.google.com/macros/s/AKfycb.../exec`
   - **Save this URL — you need it for the next step**

---

### Step 4: Update the Website Code

You need to paste the Web App URL in **two files**:

#### File 1: `review.html`
Open the file and find this line near the top of the script section:
```javascript
const APPS_SCRIPT_URL = 'YOUR_APPS_SCRIPT_URL';
```
Replace `YOUR_APPS_SCRIPT_URL` with your actual Web App URL:
```javascript
const APPS_SCRIPT_URL = 'https://script.google.com/macros/s/AKfycb.../exec';
```

#### File 2: `js/main.js`
Open the file and find this line near the bottom:
```javascript
const REVIEWS_SCRIPT_URL = 'YOUR_APPS_SCRIPT_URL';
```
Replace `YOUR_APPS_SCRIPT_URL` with the same Web App URL:
```javascript
const REVIEWS_SCRIPT_URL = 'https://script.google.com/macros/s/AKfycb.../exec';
```

#### Push to GitHub:
```cmd
cd "D:\Users\q68373\OneDrive - Delta Air Lines\KIRO\Kanna_Projects\Website_GH\GH_tile_scroll"
git add review.html js/main.js
git commit -m "Connected Google Sheets review system"
git push
```

---

## How to Share the Review Link with Customers

### Option 1: WhatsApp Message (Recommended)
After a customer's trip, send this message via WhatsApp:

**English:**
```
Hi [Customer Name]! Thank you for choosing Ganesh Holidays for your [Destination] trip! 🙏

We'd love to hear your feedback. Please share your experience here:
https://ganeshholidays.in/review.html

Your review helps other travelers and means a lot to us! ⭐
```

**Tamil:**
```
வணக்கம் [Customer Name]! கணேஷ் ஹாலிடேஸுடன் [Destination] பயணம் செய்ததற்கு நன்றி! 🙏

உங்கள் அனுபவத்தை எங்களிடம் பகிருங்கள்:
https://ganeshholidays.in/review.html

உங்கள் கருத்து மற்ற பயணிகளுக்கு உதவும்! ⭐
```

### Option 2: Create a Short Link
1. Go to https://bit.ly (or https://tinyurl.com)
2. Paste: `https://ganeshholidays.in/review.html`
3. Create short link like: `bit.ly/gh-review`
4. Use this short link in WhatsApp/SMS

### Option 3: QR Code (for business card / vehicle sticker)
1. Go to https://www.qr-code-generator.com
2. Enter: `https://ganeshholidays.in/review.html`
3. Download the QR code image
4. Print it on your business card or vehicle sticker
5. Customers scan with phone camera → opens review form

---

## What the Customer Sees

When a customer opens the review link:

1. **Language toggle** (EN / தமிழ்)
2. **Ganesh Holidays logo**
3. **Form fields:**
   - Name (required)
   - Phone (optional)
   - Trip Destination (required)
   - Star Rating (1-5 stars, clickable — default 5)
   - Feedback text (required)
   - Photo upload (optional — for your reference, not displayed on site)
4. **Submit button**

After submitting → they see a "Thank You" message with a link back to the website.

---

## How to Approve Reviews (Daily Task)

### When you get the email notification:

1. Open the Google Sheet (bookmark it on phone — use Google Sheets app)
2. You'll see a new row with the review data:

| Timestamp | Name | Phone | Destination | Rating | Feedback | Approved |
|-----------|------|-------|-------------|--------|----------|----------|
| 24/08/2026, 3:45 PM | Ravi Kumar | 9876543210 | Ooty | 5 | Amazing trip! | |

3. Read the review — Is the name real? Is the feedback appropriate?
4. **To approve:** Type `YES` in the **Approved** column (column G)
5. **To reject:** Leave the Approved column blank, or delete the row

### That's it! The website automatically shows approved reviews on next page load.

---

## How Reviews Appear on the Website

Approved reviews show up in the **"Customer Experiences"** section with:

- **Star rating** — generated from the Rating column (supports full and half stars)
- **Review text** — from the Feedback column, shown in quotes
- **Customer initials** as avatar — auto-generated (e.g., "RK" for Ravi Kumar)
- **Customer name** — from the Name column
- **Trip info** — from the Destination column

They are displayed in the **Customer Experiences** section as swiper cards with stars, text, avatar initials, name, and trip info.

---

## How the Website Fetches Reviews (Technical)

1. When someone visits the website, `main.js` runs
2. It makes a GET request to the Google Apps Script Web App URL
3. The Apps Script reads the Google Sheet
4. Filters rows where Approved = `YES`
5. Returns the data as JSON array
6. JavaScript creates review cards for each approved review
7. Appends them to the reviews swiper/grid
8. On mobile, the swiper is updated to include the new slides

**If the fetch fails** (network error, Apps Script down), the reviews section will be empty. No error is visible to visitors.

---

## Troubleshooting

| Problem | Solution |
|---------|----------|
| **Not getting email notifications** | Check spam folder. Verify email address in Apps Script code. Check Apps Script execution log (Extensions → Apps Script → Executions). |
| **Review not showing on website** | Make sure you typed `YES` in column G (Approved). The code checks case-insensitively so `yes`, `Yes`, `YES` all work. Clear browser cache and refresh. |
| **"Loading reviews..." appears then disappears but no reviews show** | The Apps Script is down or returning empty data. See "How to Fix Reviews Not Loading" below. |
| **Form submission shows error** | Check that the Web App URL is correct in `review.html`. Re-deploy the Apps Script if URL changed. |
| **Want to edit a review before displaying** | Edit the Feedback or Name cell in the Google Sheet directly. Website picks up the edited version on next load. |
| **Want to remove a published review** | Change `YES` to `NO` or blank, or delete the row. It disappears from the website on next page load. |
| **Reviews appear slowly** | Google Apps Script has ~1-2 second response time. This is normal for the free tier. A "Loading reviews..." spinner shows during this time. |
| **Apps Script says "exceeded quota"** | Google allows ~20,000 requests/day on free tier. If exceeded, reviews section will be empty until next day. |
| **"Unable to open file" error when opening Apps Script URL** | Re-deploy the Apps Script (see below). Also try clearing browser cache or opening in incognito. |
| **Reviews work on laptop but not mobile (or vice versa)** | Mobile network may be blocking `script.google.com`. Try on WiFi. Clear browser cache. Try incognito tab. |
| **Need to update the Apps Script** | Go to Extensions → Apps Script in the Sheet. Edit the code. Click Deploy → Manage deployments → Edit (pencil icon) → New version → Deploy. |

---

## How to Fix Reviews Not Loading

If the reviews section shows "Loading reviews..." then goes empty, follow these steps:

### Step 1: Test the Apps Script URL

1. Open this URL in your browser (laptop or mobile):
```
https://script.google.com/macros/s/AKfycby-KUQsQT21ieeWNWbKTj8OyLINmpC22OXIfVM3VmKEwPEM1FkbX4XTpqd12YRw6a6jEQ/exec
```

2. **If you see JSON data** like `[{"name":"...","rating":5,...}]` → URL is working. Clear browser cache on the device where reviews aren't loading.

3. **If you see "Unable to open file"** or error → re-deploy (Step 2).

4. **If the page doesn't load at all** → network issue. Try WiFi or different browser.

### Step 2: Re-deploy the Apps Script

1. Open your **Google Sheet** (`GH_Reviews`) on laptop
2. Click **Extensions → Apps Script**
3. Click **Deploy → Manage deployments**
4. Click the **pencil icon** (edit) on your deployment
5. Under **Version** → select **New version**
6. Click **Deploy**
7. Copy the **Web App URL**

### Step 3: Check if URL changed

Compare the new URL with the current URL in the code. If it's the **same URL** → you're done, test again.

If the **URL changed**, update it in 2 files:

**File 1: `review.html`**
Find near the top of the script section:
```javascript
const APPS_SCRIPT_URL = 'https://script.google.com/macros/s/OLD_URL/exec';
```
Replace with the new URL.

**File 2: `js/main.js`**
Find near the reviews section:
```javascript
const REVIEWS_SCRIPT_URL = 'https://script.google.com/macros/s/OLD_URL/exec';
```
Replace with the new URL.

### Step 4: Push to GitHub

Upload both `review.html` and `js/main.js` to GitHub.

### Step 5: Test

1. Open `ganeshholidays.in` in incognito/private tab
2. Scroll to Customer Experiences
3. Reviews should load within 1-3 seconds

---

## Re-deploying Apps Script After Changes

If you edit the Apps Script code:

1. Open the Google Sheet → **Extensions → Apps Script**
2. Make your changes
3. Click **Deploy → Manage deployments**
4. Click the **pencil icon** (edit) on your deployment
5. Under "Version", select **New version**
6. Click **Deploy**
7. The same URL now serves the updated code — no website changes needed

---

## Important Notes

- **Photo uploads:** Currently photos are accepted in the form for your reference but NOT displayed on the website. The photo is not stored anywhere — it's just a UX element for the customer. To display photos, Google Drive integration would be needed (can be added later).
- **Review order:** Reviews appear in the order they are in the Google Sheet (top to bottom).
- **No hardcoded reviews:** All reviews come from the Google Sheet. If no reviews are approved, the section shows empty.
- **No limit on reviews:** The code fetches ALL approved reviews — 4, 40, or 400. The swiper carousel handles unlimited slides.
- **Long reviews:** Reviews longer than 150 characters show "Read More" link. Click opens a popup with the full review.
- **Free limits:** Google Apps Script allows ~20,000 requests/day and 6 minutes execution time. More than enough for your usage.
- **Backup:** The Google Sheet IS your backup. You can download it as Excel/CSV anytime.
- **Domain-independent:** The review system works on any domain (ganeshholidays.github.io, ganeshholidays.in, etc.) — no code changes needed when switching domains.

---

## Quick Reference — Files Involved

| File | What it does |
|------|-------------|
| `review.html` | Customer-facing review form. Submits to Apps Script via POST. |
| `js/main.js` | Fetches approved reviews from Apps Script via GET. Renders as review cards. |
| Google Apps Script | `doPost()` saves review to Sheet + sends email. `doGet()` returns approved reviews as JSON. |
| Google Sheet | Stores all reviews. Column G (Approved) controls visibility. |

---

## Future Enhancements (Can Be Added Later)

1. **Photo display** — Upload customer photos to Google Drive, display on website
2. **Auto-notification via WhatsApp** — WhatsApp Business API to get notifications
3. **Reply to reviews** — Add a "Reply" column in the sheet, display your response below the review
4. **Filter by destination** — Let visitors filter reviews by trip destination
5. **Google Business integration** — Pull reviews from Google Maps listing automatically
6. **Rate limiting** — Prevent spam submissions (add CAPTCHA or time-based limits)


---

## Syncing Google Business Reviews to Website

Google Business reviews **cannot be auto-synced** for free (the API costs money). Instead, manually copy good Google reviews to your Google Sheet:

1. Open Google Business Profile → Reviews
2. Find the review you want on your website
3. Open your Google Sheet (`GH_Reviews`)
4. Add a new row:

| Timestamp | Name | Phone | Destination | Rating | Feedback | Approved |
|-----------|------|-------|-------------|--------|----------|----------|
| (date) | (reviewer name) | — | (if mentioned) | (star count) | (copy review text) | YES |

5. Review appears on your website automatically

**Tip:** Ask every happy customer to review on BOTH Google and your website for maximum impact.
