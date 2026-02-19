# 📚 KuttyTeachers — Complete Website Guide

**Your personal reference for everything about this website.**
Written for you — not for coders. No technical background needed to follow this guide.

---

## 📋 Table of Contents

1. [How the Website is Built — The Big Picture](#1-how-the-website-is-built--the-big-picture)
2. [File Map — What Connects to What](#2-file-map--what-connects-to-what)
3. [Adding a Logo & Favicon](#3-adding-a-logo--favicon)
4. [Adding Content to Each Page](#4-adding-content-to-each-page)
   - [Photography Page](#photography-page)
   - [Gardening Page](#gardening-page)
   - [Tutoring & Class Pages](#tutoring--class-pages)
   - [Piano Page](#piano-page)
   - [About Page](#about-page)
   - [Home Page (index)](#home-page-index)
5. [Copyright & Ownership — How It Works](#5-copyright--ownership--how-it-works)
6. [Social Media Links — Making Them Work](#6-social-media-links--making-them-work)
7. [robots.txt & llms.txt — What They Are](#7-robotstxt--llmstxt--what-they-are)
8. [What to Upload When Asking AI for Help](#8-what-to-upload-when-asking-ai-for-help)
9. [Future Content — Things to Keep in Mind](#9-future-content--things-to-keep-in-mind)

---

## 1. How the Website is Built — The Big Picture

Your website is a collection of plain HTML files hosted on GitHub Pages. Think of it like this:

```
Your GitHub Repo (niharsona/1)
│
├── Shared files (used by ALL pages)
│   ├── kutty-extras.css     ← shared visual styles: header, footer, mobile menu
│   └── kutty-extras.js      ← shared behaviour: hamburger menu, footer injection
│
├── Each page has its own files
│   ├── index.html           ← Home page
│   ├── photography.html     ← Photography page
│   ├── photography.css      ← Photography styles
│   ├── photography.js       ← Photography logic
│   ├── photos.json          ← ⭐ YOUR PHOTO DATA — edit this to add photos
│   │
│   ├── gardening.html       ← Gardening page
│   ├── gardening-styles.css ← Gardening styles
│   ├── gardening-script.js  ← Gardening logic
│   ├── plants-data.json     ← ⭐ YOUR PLANT DATA — edit this to add plants
│   │
│   ├── tutoring.html        ← Tutoring hub page
│   ├── class-1.html         ← Class 1 page (same template for 2–8)
│   ├── class-1.json         ← ⭐ CLASS 1 DATA — edit this to add class content
│   ├── class.css            ← Shared style for all class pages
│   ├── class.js             ← Shared engine for all class pages
│   │
│   ├── piano.html           ← Piano/Music page
│   ├── about.html           ← About page
│   │
├── robots.txt               ← Tells search engines what to do
├── llms.txt                 ← Tells AI systems what to do
└── llms.txt                 ← This README
```

### The Golden Rule of Your Website

> **You almost never need to touch the CSS or JS files.**
> All your content lives in the `.json` files and the `.html` files.
> For data (photos, plants, classes) — edit the JSON.
> For text on the page (hero heading, description) — edit the HTML.

---

## 2. File Map — What Connects to What

This table tells you exactly which files are connected for each page.
When asking AI for help, upload only the files listed for that page.

| Page | HTML file | Data file | Style file | JS file |
|------|-----------|-----------|------------|---------|
| Home | `index.html` | — | Inside `index.html` | Inside `index.html` |
| Photography | `photography.html` | `photos.json` ⭐ | `photography.css` | `photography.js` |
| Gardening | `gardening.html` | `plants-data.json` ⭐ | `gardening-styles.css` | `gardening-script.js` |
| Tutoring | `tutoring.html` | — | Inside `tutoring.html` | Inside `tutoring.html` |
| Class 1 | `class-1.html` | `class-1.json` ⭐ | `class.css` | `class.js` |
| Class 2–8 | `class-2.html` etc | `class-2.json` etc ⭐ | `class.css` | `class.js` |
| Piano | `piano.html` | — | Inside `piano.html` | — |
| About | `about.html` | — | Inside `about.html` | — |

**Shared by every page:**
- `kutty-extras.css` — header, footer, mobile menu appearance
- `kutty-extras.js` — hamburger button, footer building, active nav link

---

## 3. Adding a Logo & Favicon

### What is a Favicon?
The tiny icon you see in the browser tab next to the page title. Currently your site has none — the browser shows a blank icon.

### What is a Logo?
An image shown in the top-left of your website header instead of (or alongside) the text "KuttyTeachers".

### Step 1 — Prepare Your Image

- Format: **PNG** (transparent background recommended)
- Size for logo: **any size**, but keep it under 200KB
- Size for favicon: ideally **512 × 512 pixels** square — browsers will auto-resize it down
- You can use the **same image file** for both logo and favicon

### Step 2 — Upload to GitHub

In your GitHub repo, create this folder path and upload your image there:

```
assets/
  logo/
    logo.png       ← put your image here
```

To create folders on GitHub: click "Add file" → "Create new file" → type `assets/logo/logo.png` in the name box → GitHub will create the folders automatically.

### Step 3 — Add Favicon to Every HTML Page

Open each HTML file and find the line that says `</head>`. Add this line **just before** it:

```html
<link rel="icon" type="image/png" href="assets/logo/logo.png">
```

You need to add this to these files:
- `index.html`
- `photography.html`
- `gardening.html`
- `tutoring.html`
- `class-1.html` (and class-2 through class-8 when you create them)
- `piano.html`
- `about.html`

### Step 4 — Show Logo in the Header (Optional)

Find this block in every HTML file:

```html
<a href="index.html" class="logo">
    <div class="logo-english">KuttyTeachers</div>
    <div class="logo-malayalam">കട്ടിടീച്ചേഴ്സ്</div>
</a>
```

Replace it with this (image + text together):

```html
<a href="index.html" class="logo">
    <img src="assets/logo/logo.png" alt="KuttyTeachers" height="36" style="vertical-align:middle; margin-right:8px;">
    <div class="logo-english">KuttyTeachers</div>
    <div class="logo-malayalam">കട്ടിടീച്ചേഴ്സ്</div>
</a>
```

Or image only (no text):

```html
<a href="index.html" class="logo">
    <img src="assets/logo/logo.png" alt="KuttyTeachers" height="48">
</a>
```

### Asking AI to do this for you
Upload: the HTML file you want changed + tell AI: "Add my logo from assets/logo/logo.png to the header and favicon."

---

## 4. Adding Content to Each Page

---

### Photography Page

**Files involved:** `photos.json` ⭐ (data), `photography.html` (page), `photography.js` (reads the data)

All your photos are stored in `photos.json`. You **never need to touch** `photography.html` or `photography.js` to add new photos. Just edit the JSON file.

#### How to add a new photo album

Open `photos.json`. It looks like this:

```json
[
  {
    "id": "album-1",
    "title": "Morning Views",
    "title_ml": "രാവിലെ കാഴ്ചകൾ",
    "description": "Early morning shots from Palakkad",
    "cover": "assets/photos/morning/cover.jpg",
    "photos": [
      {
        "src": "assets/photos/morning/photo1.jpg",
        "caption": "Sunrise over the fields",
        "caption_ml": "വയലിനു മേൽ സൂര്യോദയം",
        "video": ""
      }
    ]
  }
]
```

To add a **new album**, copy one album block from `{` to `}` and paste it after the last `}`, separated by a comma. Change the values.

To add a **new photo to an existing album**, find that album's `"photos": [...]` section and add a new photo object:

```json
{
  "src": "assets/photos/morning/photo2.jpg",
  "caption": "The river at dawn",
  "caption_ml": "പുലർച്ചയിലെ നദി",
  "video": ""
}
```

#### Where to put photo image files

Upload your photos to GitHub under:
```
assets/
  photos/
    morning/       ← folder per album
      photo1.jpg
      photo2.jpg
    garden/
      photo1.jpg
```

#### Adding a video to a photo

If a photo has a YouTube video, fill in the `"video"` field:
```json
"video": "https://www.youtube.com/watch?v=YOUR_VIDEO_ID"
```
A play button badge will appear on the photo card automatically.

#### Changing the hero text on the Photography page

Open `photography.html` and find:
```html
<h1>Photography</h1>
<div class="page-header-ml">പാലക്കാടിന്റെ കഥകൾ</div>
<p>സ്ഥാനിക ക്ഷണങ്ങൾ...</p>
```
Edit those three lines directly.

---

### Gardening Page

**Files involved:** `plants-data.json` ⭐ (data), `gardening.html` (page), `gardening-script.js` (reads the data)

Same principle as photography — all plant content is in `plants-data.json`.

#### How to add a new plant

Open `plants-data.json`. Each plant looks like this:

```json
{
  "id": "tulsi",
  "name": "തുളസി",
  "name_en": "Tulsi / Holy Basil",
  "scientific": "Ocimum tenuiflorum",
  "emoji": "🌿",
  "category": "herbs",
  "description": "ഞങ്ങളുടെ തോട്ടത്തിലെ ഏറ്റവും പ്രധാനപ്പെട്ട ചെടി...",
  "images": ["assets/garden/tulsi1.jpg", "assets/garden/tulsi2.jpg"],
  "care": {
    "water": "Daily",
    "sun": "Full sun",
    "soil": "Well-drained",
    "fertilizer": "Monthly"
  },
  "harvest": "60–90 days",
  "tips": "Additional growing tips here..."
}
```

Copy this block, paste it after the last plant (separated by a comma), and fill in your new plant's details.

#### Categories (for the filter buttons)

The category buttons at the top of the page are auto-generated from whatever categories exist in your data. Current categories used:
- `"herbs"` — Herbs
- `"vegetables"` — Vegetables
- `"flowers"` — Flowers
- `"trees"` — Trees
- `"indoor"` — Indoor plants

You can create any new category just by typing it in the `"category"` field of a new plant.

#### Changing the hero text on the Gardening page

Open `gardening.html` and find:
```html
<h1>തോട്ടം</h1>
<div class="hero-ml">പാലക്കാടിലെ നമ്മുടെ തോട്ടം സാഹസിക യാത്ര</div>
<p>വിവിധ ചെടികൾ...</p>
```
Edit those lines directly.

---

### Tutoring & Class Pages

**The tutoring page** (`tutoring.html`) is mostly static — it shows the 8 class cards and some info sections. You don't need a data file to edit it.

**Each class page** (`class-1.html` through `class-8.html`) reads from its own JSON file.

#### How class pages work

`class-1.html` has one special line:
```html
<script>const CLASS_DATA_FILE = 'class-1.json';</script>
```
This tells the page to load data from `class-1.json`. That's the **only difference** between class-1.html and class-2.html. The engine (`class.js`) and styles (`class.css`) are identical for all 8 classes.

#### How to add content to a class page

Open `class-1.json`. It contains tabs like Overview, Subjects, Games, Tips etc. Find the tab you want and add content there.

A typical subject entry looks like:
```json
{
  "subject": "ഗണിതം",
  "subject_en": "Maths",
  "icon": "🔢",
  "curricula": {
    "SCERT": "Chapter details and approach for SCERT...",
    "NCERT": "How NCERT handles this topic...",
    "Finland": "Finland's approach — project-based..."
  }
}
```

#### Creating class-2.html through class-8.html

Copy `class-1.html` exactly. Change only this one line:
```html
<script>const CLASS_DATA_FILE = 'class-1.json';</script>
```
to:
```html
<script>const CLASS_DATA_FILE = 'class-2.json';</script>
```
Then create `class-2.json` with that class's content.

#### Changing the tutoring page hero

Open `tutoring.html` and find:
```html
<h1>Learn Together</h1>
<div class="hero-ml">ഒരുമിച്ച് പഠിക്കാം</div>
```
Edit directly.

---

### Piano Page

**File:** `piano.html` only (no separate data file)

Currently a "coming soon" page. When you're ready to add music content, open `piano.html` and find the main content section. You can add:
- YouTube video embeds (copy embed code from YouTube → Share → Embed)
- Song titles and descriptions directly in the HTML

Ask AI: "Help me add a YouTube video to piano.html" — upload just `piano.html`.

---

### About Page

**File:** `about.html` only

All your personal story, mission statement, photos of you, and contact details live directly in this HTML file. Open it and edit the text sections directly — no JSON needed.

---

### Home Page (index)

**File:** `index.html` only (no separate data file)

The home page has sections like the hero banner, the 4 service cards (Photography, Tutoring, Music, Garden), and the footer. All content is directly in the HTML.

To change the hero tagline, find:
```html
<h1>KuttyTeachers</h1>
```
and the paragraphs near it.

---

## 5. Copyright & Ownership — How It Works

### What protection you currently have

Your site has **three layers** of copyright protection:

#### Layer 1 — Meta Tags (in every HTML file's `<head>`)
```html
<meta name="author"    content="KuttyTeachers — Palakkad, Kerala">
<meta name="copyright" content="© 2026 KuttyTeachers. All rights reserved.">
<meta name="robots"    content="index, follow">
<meta name="license"   content="https://creativecommons.org/licenses/by-nc/4.0/">
```
These tell search engines and browsers who made this content.

**Where to verify:** Open any of your HTML files → look for the comment `<!-- ═══ COPYRIGHT & OWNERSHIP META ═══ -->` near the top inside `<head>`.

#### Layer 2 — Schema.org JSON-LD (in every HTML file)
This is the block that starts with `<script type="application/ld+json">`. It declares you as the author in a format that Google and AI systems can read clearly.

**Where to verify:** Same `<head>` section — look for the `@type`, `"author"` and `"license"` fields.

#### Layer 3 — CC BY-NC 4.0 License
Your content is under **Creative Commons Attribution NonCommercial 4.0**.

This means:
- ✅ Others CAN share or reference your content
- ✅ Others CAN translate or adapt it
- ❌ Others CANNOT use it commercially (sell it, put it in paid products)
- ❌ Others CANNOT use it without crediting you as the author

### How to verify your email/name in the copyright

Your email appears in two forms in the code:
1. **Obfuscated by Cloudflare** (looks like `/cdn-cgi/l/email-protection#...`) — this is automatic spam protection
2. **Plain text** in `llms.txt` and `robots.txt` — `contact@kuttyteachers.in`

**To verify:** Open `llms.txt` → look for `Contact: contact@kuttyteachers.in`.

### How to change your name or email everywhere

Because the copyright appears in **every HTML file**, use AI to do a batch change. Upload all your HTML files and say:

> "Change the author name from 'KuttyTeachers' to '[new name]' and the email from 'contact@kuttyteachers.in' to '[new email]' in all the copyright meta tags and schema blocks."

Also manually update `robots.txt` and `llms.txt` — those are plain text files you can edit directly on GitHub.

### What the license year means

Currently set to `© 2026`. Update this each year. The easiest way: do a search-and-replace in GitHub or ask AI to update it across all files.

---

## 6. Social Media Links — Making Them Work

### Where the social links live

Social media icons are in the **footer**, which is injected by `kutty-extras.js`. Open `kutty-extras.js` and find the `injectFooter()` function. Inside it, look for the social icons section — it has Facebook, Instagram, YouTube, and WhatsApp icons.

### How to add your actual URLs

Find this section in `kutty-extras.js`:

```javascript
// Social links — replace # with your actual URLs
{ icon: '...facebook svg...', url: '#', label: 'Facebook' },
{ icon: '...instagram svg...', url: '#', label: 'Instagram' },
{ icon: '...youtube svg...', url: '#', label: 'YouTube' },
{ icon: '...whatsapp svg...', url: '#', label: 'WhatsApp' },
```

Replace each `'#'` with your actual link:

| Platform | What to put in `url` |
|----------|----------------------|
| Facebook | `https://facebook.com/YourPageName` |
| Instagram | `https://instagram.com/YourHandle` |
| YouTube | `https://youtube.com/@YourChannelName` |
| WhatsApp | `https://wa.me/91XXXXXXXXXX` (your 10-digit number with country code) |

Example:
```javascript
{ icon: '...', url: 'https://instagram.com/kuttyteachers', label: 'Instagram' },
```

### Ask AI to do this
Upload just `kutty-extras.js` and say: "Add my social media links — Instagram: [your handle], YouTube: [your channel], WhatsApp: [your number]."

Since the footer is shared across all pages through `kutty-extras.js`, **changing it in one place updates every page automatically**.

---

## 7. robots.txt & llms.txt — What They Are

### robots.txt — For Search Engines

**What it is:** A text file that tells Google, Bing, and other search engine crawlers what they are and aren't allowed to index on your site.

**Your current settings:**
- ✅ Google and Bing CAN index all your pages (good for visibility)
- ❌ AI training bots (GPTBot, Claude-Web, CCBot etc.) are BLOCKED from scraping your content
- ❌ Your JSON data files (`photos.json`, `plants-data.json`) are blocked from crawlers

**When to edit it:** If you add new JSON data files, add a new `Disallow:` line for each one. Example: if you create `class-2.json`, add:
```
Disallow: /class-2.json
```

**How to edit:** Open `robots.txt` directly on GitHub (click the file → pencil icon → edit → commit). It's plain text — no code knowledge needed.

### llms.txt — For AI Systems

**What it is:** A newer standard file (like robots.txt but for AI) that tells AI systems like ChatGPT, Claude, Gemini etc. how they may use your content.

**Your current settings:**
- ✅ AI CAN answer questions about your site and summarise pages for users
- ✅ AI CAN cite your site (with attribution)
- ❌ AI CANNOT train on your content
- ❌ AI CANNOT use your content commercially
- ❌ AI CANNOT scrape your JSON files

**When to edit it:** Update it when you:
- Add a new page to your site (add a new section under `## Content Sections`)
- Change your contact email
- Change the site URL
- Add new types of content (e.g. if you start posting videos)

**How to edit:** Open `llms.txt` on GitHub → pencil icon → edit the relevant section → commit. It's written in plain English with `#` comments — easy to read and change.

**Example — adding a new page entry:**
```
## Class 2
- URL: https://niharsona.github.io/1/class-2.html
- Description: Second class learning hub with subject guides.
- Language: Malayalam (ml), English (en)
```

### Do these files actually stop people?

Honest answer: **they help but don't fully prevent** determined scrapers. What they do:

- Tell **ethical crawlers** (most major AI companies and Google) your rules — these companies generally respect `robots.txt`
- Create a **legal paper trail** — if someone misuses your content, these files prove you declared your ownership and restrictions
- **Improve your SEO** — robots.txt helps Google index only what you want

---

## 8. What to Upload When Asking AI for Help

Use this as a quick reference so you don't have to upload everything every time.

### "I want to change the header/nav on all pages"
Upload: `kutty-extras.css` + one HTML file (e.g. `index.html`) as reference

### "I want to change the footer"
Upload: `kutty-extras.js` only

### "I want to add photos"
Upload: `photos.json` only (no HTML needed)

### "I want to add a plant"
Upload: `plants-data.json` only

### "I want to change the photography page layout"
Upload: `photography.html` + `photography.css` + `photography.js`

### "I want to change the gardening page layout"
Upload: `gardening.html` + `gardening-styles.css` + `gardening-script.js`

### "I want to change the home page"
Upload: `index.html` only (it has its own CSS inside it)

### "I want to change the tutoring page"
Upload: `tutoring.html` only

### "I want to change a class page"
Upload: `class-1.html` + `class-1.json` + `class.js` + `class.css`

### "I want to change the copyright/author details"
Upload: all HTML files + `robots.txt` + `llms.txt`

### "I want to add a favicon/logo"
Upload: the HTML file you want to change (or all HTML files if all pages)

### "I want to add social media links"
Upload: `kutty-extras.js` only

---

## 9. Future Content — Things to Keep in Mind

### Data Entry Best Practices

**For JSON files (`photos.json`, `plants-data.json`, `class-1.json`):**

- Always validate your JSON after editing. Go to [jsonlint.com](https://jsonlint.com), paste your JSON, click Validate. A missing comma or extra bracket will break the whole page.
- Every item in a list needs a comma after it **except the last one**
- Text with apostrophes inside JSON must use `\'` or wrap in double quotes carefully
- Malayalam text works fine in JSON — just type or paste it normally

**For images:**
- Keep file sizes under 300KB per image for fast loading
- Use descriptive file names: `tulsi-plant-morning.jpg` not `IMG_20240101.jpg`
- Stick to lowercase and hyphens in filenames — no spaces

### When You Add New Class Pages (class-2 through class-8)

For each new class, do these 4 things:
1. Copy `class-1.html` → rename to `class-2.html`
2. Change the one line: `CLASS_DATA_FILE = 'class-1.json'` → `'class-2.json'`
3. Create `class-2.json` with that class's content
4. Update `robots.txt` → add `Disallow: /class-2.json`
5. Update `llms.txt` → the URL pattern already covers all classes, so no change needed there

### Copyright — Update Every Year

At the start of each year, update the copyright year in:
- Every HTML file's `<meta name="copyright">` tag
- `llms.txt` → `Last updated:` line
- `robots.txt` → top comment line
- The footer in `kutty-extras.js` → the `© 2026` text in `injectFooter()`

Ask AI: "Update all copyright years from 2026 to 2027" — upload all HTML files + `kutty-extras.js`.

### When You Add Real Photos (replacing Unsplash placeholders)

Your current photos use Unsplash URLs as placeholders. When you replace them with your own Canon 1500D shots:
1. Upload your photos to `assets/photos/` in GitHub
2. Open `photos.json`
3. Replace the Unsplash URLs with your file paths like `assets/photos/album-name/photo.jpg`
4. This is the most important step for copyright — your own photos are the strongest protection

### SEO — Getting Found on Google

Your site already has good SEO basics. As you add more content:
- Write descriptions in both Malayalam and English where possible
- The `alt` text on images matters — describe the image in plain language
- Each page's `<meta name="description">` should accurately describe that page

### Backup Your JSON Files

Your JSON files are your most valuable data — they contain all your content. Keep copies of `photos.json`, `plants-data.json`, and all `class-*.json` files on your computer. GitHub already acts as a backup, but having a local copy is a good habit.

### When the Site Gets Bigger — Consider a Domain

Currently your site lives at `niharsona.github.io/1/` — not very memorable. When ready, buy `kuttyteachers.in` and point it to your GitHub Pages. This also strengthens your copyright claim (a domain in your name is strong ownership evidence).

---

## Quick Reference Card

| Task | File to edit | Need AI? |
|------|-------------|----------|
| Add a photo album | `photos.json` | No |
| Add a plant | `plants-data.json` | No |
| Add class content | `class-1.json` | No |
| Change hero text | The page's `.html` file | No |
| Add social links | `kutty-extras.js` | Optional |
| Add favicon | All `.html` files | Yes (batch) |
| Change footer | `kutty-extras.js` | Optional |
| Change page layout | `.html` + `.css` files | Yes |
| Update copyright year | All `.html` + `kutty-extras.js` | Yes (batch) |
| Add new page | New `.html` file | Yes |
| Block a new JSON file | `robots.txt` | No |
| Update AI permissions | `llms.txt` | No |

---

*Last updated: February 2026 — KuttyTeachers, Palakkad, Kerala*
*This guide was written for KuttyTeachers by Claude (Anthropic) based on the actual website codebase.*
