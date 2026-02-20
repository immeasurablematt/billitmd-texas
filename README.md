# BillitMD Texas Waitlist — Landing Page

Single-file waitlist landing page for BillitMD's Texas market expansion.
Deploy-ready. No build step required.

---

## Deploy in 5 Minutes

### Option A: Vercel (Recommended — fastest)

```bash
cd /Users/bob/.openclaw/workspace-dev/projects/billitmd-texas-landing
npx vercel --prod
```

On first run: log in, set project name (`billitmd-texas`), confirm root dir is `.`
Your page will be live at `billitmd-texas.vercel.app` in ~30 seconds.

Custom domain: add `texas.billitmd.com` in Vercel dashboard → Settings → Domains.

---

### Option B: Netlify Drop

1. Go to https://app.netlify.com/drop
2. Drag the entire `billitmd-texas-landing/` folder onto the page
3. Done. You get a `random-name.netlify.app` URL instantly.

Custom domain: Site settings → Domain management → Add custom domain.

---

### Option C: GitHub Pages

```bash
cd /Users/bob/.openclaw/workspace-dev/projects/billitmd-texas-landing
git init
git add .
git commit -m "Initial deploy: BillitMD Texas landing page"
# Create repo on GitHub, then:
git remote add origin https://github.com/YOUR_ORG/billitmd-texas-landing.git
git push -u origin main
```

Enable Pages: Repo → Settings → Pages → Deploy from branch `main` → `/ (root)`.

---

## ⚠️ Before Going Live: Formspree Setup

The waitlist form uses Formspree for email capture.

1. Create a free account at https://formspree.io
2. Create a new form → copy your Form ID (looks like `xpwzqrjk`)
3. In `index.html`, find this line:

```html
<form id="waitlist-form" action="https://formspree.io/f/YOUR_FORM_ID" method="POST"
```

4. Replace `YOUR_FORM_ID` with your actual Form ID
5. In Formspree dashboard: set redirect URL to blank (AJAX handles it), set notification email

Formspree free tier: 50 submissions/month. Upgrade to $8/mo for unlimited.

**Alternative:** Netlify Forms (if deploying to Netlify) — change form tag to:
```html
<form id="waitlist-form" name="waitlist" netlify netlify-honeypot="bot-field" ...>
```
And add `<input type="hidden" name="form-name" value="waitlist" />` inside the form.

---

## UTM Tracking

The page automatically captures and stores UTM parameters from the URL:

```
https://texas.billitmd.com/?utm_source=twitter&utm_medium=paid&utm_campaign=texas-launch
```

All UTM params are included in each form submission. They persist in localStorage across page reloads within a session.

---

## Customization Checklist

| Item | Location in index.html |
|---|---|
| Formspree form ID | `action="https://formspree.io/f/YOUR_FORM_ID"` |
| Contact email | `texas@billitmd.com` (×3 in footer/form) |
| OG image URL | `<meta property="og:image"` |
| Canonical URL | `<link rel="canonical"` |
| Testimonial name/location | "Beta Participant — Frisco, TX" section |
| Waitlist count social proof | Hero subtext — "Texas physicians already on the waitlist" |

---

## File Structure

```
billitmd-texas-landing/
└── index.html        # Everything. Single file, ~50KB.
```

No dependencies. No build step. No node_modules. Just HTML.

---

## SEO

- Title: "BillitMD — AI Billing Code Optimization for Texas Physicians"
- Meta targeting: medical billing optimization Texas, CPT code optimizer, physician billing software Texas
- H1 contains primary keyword
- Open Graph + Twitter Card tags included
- Canonical URL set (update to your actual domain)

---

## Design System

| Token | Value | Use |
|---|---|---|
| Navy | `#0B1F3A` | Primary background, section bg |
| Navy Dark | `#060F1D` | Footer, nav |
| Gold | `#C8922A` | Accents, borders, logo star |
| Amber | `#F5A623` | CTAs, highlighted text |
| White | `#FFFFFF` | Body text on dark |

Fonts: Inter (sans) + Merriweather (headings) via Google Fonts.
CSS framework: Tailwind CDN (no build step).
