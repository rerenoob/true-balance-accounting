# Golden Flow Accounting & Tax

Professional website for **Golden Flow Accounting & Tax** (Golden Flow LLC) — a Texas-based accounting and tax services firm serving small businesses and individuals.

## Project Structure

```
golden-flow-accounting/
├── index.html   # Single-page website (all sections)
├── style.css    # Stylesheet
└── README.md    # This file
```

## Deploy to GitHub Pages

### Option A — New repository (quickest)

1. Create a new repository on GitHub (e.g., `golden-flow-accounting`).
2. Push the files:
   ```bash
   git init
   git add index.html style.css README.md
   git commit -m "Initial website"
   git branch -M main
   git remote add origin https://github.com/YOUR_USERNAME/golden-flow-accounting.git
   git push -u origin main
   ```
3. In your repository, go to **Settings → Pages**.
4. Under **Source**, select **Deploy from a branch**, choose `main`, folder `/` (root), and click **Save**.
5. GitHub will publish your site at:
   ```
   https://YOUR_USERNAME.github.io/golden-flow-accounting/
   ```

### Option B — Custom domain (e.g., goldenflowaccountingtax.com)

1. Complete Option A above.
2. In your domain registrar's DNS settings, add:
   - **A records** pointing to GitHub Pages IPs:
     ```
     185.199.108.153
     185.199.109.153
     185.199.110.153
     185.199.111.153
     ```
   - **CNAME record**: `www` → `YOUR_USERNAME.github.io`
3. In **Settings → Pages**, enter your custom domain and enable **Enforce HTTPS**.
4. Add a `CNAME` file to the repository root containing your domain:
   ```
   goldenflowaccountingtax.com
   ```

DNS propagation can take up to 24–48 hours.

## Activating the Contact Form

The contact form currently demonstrates client-side validation with a simulated submission. To make it actually send messages, wire it up to one of these free/low-cost options:

### Formspree (recommended for static sites)

1. Sign up at [formspree.io](https://formspree.io).
2. Create a new form — Formspree gives you an endpoint URL like:
   ```
   https://formspree.io/f/XXXXXXXX
   ```
3. In `index.html`, find the `<form>` tag and add the action:
   ```html
   <form class="contact-form" id="contactForm" action="https://formspree.io/f/XXXXXXXX" method="POST" novalidate>
   ```
4. Remove or replace the JavaScript `setTimeout` block in the `form.addEventListener('submit', ...)` handler with a real fetch call, or let the form submit natively by removing `e.preventDefault()` after validation passes.

### Netlify Forms (if migrating to Netlify)

Add `netlify` to the `<form>` tag:
```html
<form class="contact-form" netlify name="contact" ...>
```

## Local Development

No build tools required. Open `index.html` directly in a browser, or serve it locally:

```bash
# Python 3
python3 -m http.server 8000

# Node.js (npx)
npx serve .
```

Then visit `http://localhost:8000`.

## Customization Notes

| What to change | Where |
|---|---|
| Company phone number | `index.html` — Contact section `<ul class="contact-details">` |
| Email address | `index.html` — Contact section |
| Business hours | `index.html` — Contact section |
| Brand colors | `style.css` — `:root` CSS variables |
| Tagline / copy | `index.html` — Hero section |
| Google Fonts | `index.html` — `<head>` link tags |

## Technologies

- Plain HTML5, CSS3, and vanilla JavaScript — no frameworks, no build step.
- Google Fonts: Inter (body) + Merriweather (headings).
- Fully responsive — mobile, tablet, and desktop.
- Accessible: semantic HTML, ARIA labels, focus styles, reduced-motion friendly.
