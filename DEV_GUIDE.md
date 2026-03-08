# NESAC CSC Hub — Developer Handoff Guide

Built by NESAC · National Engineering Students Association of Cameroon

---

## Files in This Package

```
nesac_template/
│
├── index.html        Home page
├── about.html        About page
├── courses.html      Courses page
├── resources.html    Resources page
├── projects.html     Projects page
├── blog.html         Blog / Articles page
├── community.html    Community page
├── contact.html      Contact page (with form)
│
├── style.css         All styles — single file
├── script.js         All JavaScript — single file
│
└── DEV_GUIDE.md      This file
```

No build tools, no npm, no dependencies.
Open any HTML file in a browser and it works immediately.

---

## How to Find and Replace Content

### Text content  →  look for  `<!-- ✏️ -->`
Every piece of placeholder text (headings, body copy, labels, CTAs)
is marked with a `<!-- ✏️ -->` comment immediately before or after it.
Search the file for `✏️` to jump straight to every editable text block.

### Image slots  →  look for  `<!-- 📸 IMAGE SLOT -->`
Every image placeholder is wrapped in a comment block that says:

```html
<!-- ===========================================================
     📸 IMAGE SLOT — [description]
     Recommended size: [dimensions]
     HOW TO SET: Replace the src below with your image path
     Example:  src="assets/images/your-image.jpg"
     =========================================================== -->
```

Search any file for `📸` to jump to every image location.

---

## Setting Images

1. Create a folder:  `assets/images/`  in the same directory as the HTML files
2. Place your image files there
3. In the HTML, find the `<img>` tag inside the image slot comment
4. Replace the `src="..."` value with your path:

```html
<!-- BEFORE (placeholder) -->
<img src="https://images.unsplash.com/photo-..." alt="[ALT TEXT]">

<!-- AFTER (your image) -->
<img src="assets/images/hero-home.jpg" alt="Students working in the computer lab">
```

5. Always update the `alt=""` attribute with a real description — this is
   important for accessibility and SEO.

### Recommended image sizes by slot type:

| Slot type               | Recommended size      | Aspect ratio |
|-------------------------|-----------------------|--------------|
| Hero background         | 1600 × 900 px min     | 16:9         |
| Split section image     | 900 × 600 px min      | 3:2 (tall)   |
| Full-width banner       | 1600 × 500 px min     | 3:1          |
| Card thumbnail (4:3)    | 600 × 450 px          | 4:3          |
| Card thumbnail (16:9)   | 800 × 450 px          | 16:9         |
| Blog article thumbnail  | 600 × 375 px          | 16:10        |
| Process step image      | 700 × 440 px          | 16:10        |

---

## Activating the Contact Form (Email Delivery)

The contact form uses **Formspree** — a free service that forwards
form submissions to any email address, with zero backend code needed.

### Steps:

1. Go to  https://formspree.io  and create a free account
2. Click **"+ New Form"**
3. Enter the email address where you want messages delivered
   (e.g. `support@nesac.cm` or any team inbox)
4. Formspree gives you an endpoint URL like:
   `https://formspree.io/f/xpwzabcd`
5. Open `contact.html` and find this line:

```html
<form
  id="contactForm"
  action="https://formspree.io/f/REPLACE_WITH_YOUR_ID"
```

6. Replace  `REPLACE_WITH_YOUR_ID`  with your actual form ID:

```html
<form
  id="contactForm"
  action="https://formspree.io/f/xpwzabcd"
```

7. Save and deploy — done. Submissions now arrive in your inbox.

### Free plan limits:
- 50 submissions per month
- Email notifications
- Spam filtering included
- Upgrade at formspree.io for higher volume

### Alternative (higher volume): EmailJS
If you expect more than 50 messages/month, use EmailJS instead:
https://www.emailjs.com — the free tier handles 200 emails/month.

---

## Fonts

The template uses two Google Fonts loaded via CDN:

- **Playfair Display** — all headings, display text, pull quotes
- **Open Sans** — all body text, labels, navigation, buttons

They are imported at the top of `style.css`. No installation needed —
they load from Google's servers automatically when the page opens.

If you need to host fonts locally (e.g. for offline use), download them
from  https://fonts.google.com  and update the `@import` line in style.css.

---

## Colors (Quick Reference)

To change the color palette, edit these variables at the top of `style.css`:

```css
:root {
  --color-navy:       #0b2b4f;   /* Primary — headings, buttons, navbar */
  --color-navy-deep:  #071a30;   /* Darker navy — footer background      */
  --color-blue:       #2e7dba;   /* Accent — logo bar, links, highlights  */
  --color-blue-light: #b3d9ff;   /* Light accent — used on dark backgrounds */
  --color-cream:      #f4f1ec;   /* Page background                       */
  --color-white:      #ffffff;   /* Card/section backgrounds              */
}
```

---

## Adding the Active Nav State

On each page, the current page's link in the navbar should have
`class="active"` so the underline indicator appears correctly.

In `index.html`:     `<a href="index.html" class="active">Home</a>`
In `about.html`:     `<a href="about.html" class="active">About</a>`
In `courses.html`:   `<a href="courses.html" class="active">Courses</a>`
...and so on.

---

## Scroll Animations

Any element with `data-reveal` on it will fade in from below when
it enters the viewport. Use `data-delay="1"` through `data-delay="4"`
to stagger animations within a group:

```html
<div data-reveal>Appears first</div>
<div data-reveal data-delay="1">Appears 0.1s later</div>
<div data-reveal data-delay="2">Appears 0.2s later</div>
```

---

## Deployment

This is a static site — no server required.

You can host it on:
- **GitHub Pages** (free) — push files to a repo and enable Pages
- **Netlify** (free) — drag and drop the folder at app.netlify.com
- **Vercel** (free) — connect a GitHub repo at vercel.com
- Any shared hosting (upload files via FTP to public_html/)

---

Built by NESAC — National Engineering Students Association of Cameroon
