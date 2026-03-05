# Landing Page — Setup & Deployment Guide

## What's Built
`index.html` — fully styled, mobile-responsive landing page with:
- Hero section with email capture form
- Anki deck breakdown (domain cards)
- "Why it's different" section
- About Kevin section
- Coming soon / paid tiers section
- Bottom CTA + footer

ConvertKit forms are **placeholders** until you complete Step 1 below.

---

## Step 1 — Create ConvertKit Account (10 min)

1. Go to [kit.com](https://kit.com) → click **Start for free**
2. Sign up with your email
3. Complete onboarding (pick "Creator" when asked)
4. Verify your email

---

## Step 2 — Create a Form in ConvertKit (10 min)

1. In ConvertKit dashboard → **Grow → Landing Pages & Forms**
2. Click **Create New → Form** (not landing page — we have our own)
3. Choose **Inline** form type
4. Give it a name: `SecAI Free Deck Signup`
5. Click **Embed** → select **HTML** tab
6. Copy the entire `<script>` block they give you

---

## Step 3 — Connect the Deck as an Incentive (5 min)

1. In ConvertKit → **Grow → Incentive Email**
   - Or go into your new form → **Settings → Incentive**
2. Enable the incentive email
3. Set subject: `Your free SecAI+ Anki deck is here`
4. In the email body, link to wherever you're hosting the `.apkg` file
   - Options: Google Drive link, Gumroad free product, GitHub Releases asset

> **Recommended:** Upload `SecAI_Course_Free_Deck.apkg` to a **Gumroad free product** ($0 price).
> This gives you a clean download link AND starts building your Gumroad presence.

---

## Step 4 — Paste the ConvertKit Form into the Landing Page (5 min)

Open `index.html` and find these two comment blocks (there are two — hero + bottom CTA):

```html
<!-- BEGIN CONVERTKIT FORM -->
<div class="form-fallback">
  ...placeholder form...
</div>
<!-- END CONVERTKIT FORM -->
```

Replace **both** `<div class="form-fallback">...</div>` blocks with the ConvertKit `<script>` embed code.

The outer `<div class="ck-embed-slot">` wrapper stays — just swap the inner content.

---

## Step 5 — Write the Welcome Email (15 min)

In ConvertKit → Sequences (or the Incentive email), write:

**Subject:** Your SecAI+ Anki deck + what's coming next

```
Hi [First Name],

Here's your free CompTIA SecurityAI+ Anki deck:
[DOWNLOAD LINK]

Import it into Anki desktop (free at ankiweb.net) by double-clicking the .apkg file.

A few tips for using it:
- Study Domain 2 first — it's 36% of the exam and trips most people up
- On every card, read the "Why Wrong" section — the exam uses fake-sounding distractors
- Use Anki's filtered decks to isolate one domain at a time

I'm building a full practice exam and study guide next. Subscribers get early access and launch pricing.

Talk soon,
Kevin
```

---

## Step 6 — Deploy to GitHub Pages (15 min)

### 6a — Create the GitHub Pages repo

```bash
cd ~/Desktop/SecAI_Course_Project

# Create a separate repo for the live site
# (keeps marketing separate from course content repo)
mkdir -p ~/Desktop/secai-landing
cp 05_Marketing/Landing_Page/index.html ~/Desktop/secai-landing/
cd ~/Desktop/secai-landing

git init
git add index.html
git commit -m "Initial landing page deploy"
git branch -M main
git remote add origin https://github.com/KPH3802/secai-landing.git
git push -u origin main
```

### 6b — Enable GitHub Pages

1. Go to `github.com/KPH3802/secai-landing`
2. **Settings → Pages**
3. Source: **Deploy from a branch** → `main` → `/ (root)`
4. Click **Save**
5. Your URL will be: `https://kph3802.github.io/secai-landing`

GitHub Pages usually goes live within 2-5 minutes.

---

## Step 7 — Update Links in the Page

Once GitHub Pages is live, open `index.html` and update:

| Placeholder | Replace with |
|---|---|
| `https://linkedin.com/in/kevin-heaney` | Your actual LinkedIn URL |
| YouTube link (commented out in footer) | Uncomment and add your channel URL when ready |

---

## Step 8 — Link from the Anki Deck README

Open `01_Free_Tier/Anki_Deck/README.md` and update the landing page URL with your live GitHub Pages link.

---

## Future: Custom Domain

When ready to upgrade from `kph3802.github.io/secai-landing` to a custom domain (e.g., `secaiplus.com`):
1. Buy domain from Namecheap or Cloudflare Registrar (~$12/year)
2. GitHub Pages → Settings → Pages → Custom domain → enter your domain
3. Add CNAME record at your registrar pointing to `kph3802.github.io`

---

## Files

```
05_Marketing/Landing_Page/
├── index.html        ← The live page (edit this)
└── SETUP.md          ← This file
```
