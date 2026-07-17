# Strapped-In profile page — deploy guide

The `/site` folder is a static website. Once deployed, the QR in the app (Me → Review card)
points students at your profile page: review stars → Google Form, tip button → Stripe.

Three one-time setups, ~20 minutes total.

## 1. GitHub Pages (the hosting)

1. Create a free account at github.com if you don't have one.
2. Create a new **public** repository named `strapped-in`.
3. Upload the contents of this `site/` folder to it (drag-and-drop works on github.com:
   Add file → Upload files). Keep the structure: `index.html` and `u/dave/index.html`.
4. In the repo: Settings → Pages → Source: "Deploy from a branch" → Branch: `main`, folder `/ (root)` → Save.
5. After a minute your page is live at
   `https://<your-username>.github.io/strapped-in/u/dave/`

Then tell Claude your GitHub username (or do it yourself): replace
`YOUR-GITHUB-USERNAME` in `app/src/data/store.tsx` (PROFILE_BASE_URL) so the
app's QR encodes the real URL.

## 2. Google Form (the reviews)

1. forms.google.com → new blank form, title e.g. "How was your lesson with Dave?"
2. Suggested questions:
   - Linear scale 1–5 — "How was your lesson?" (required)
   - Short answer — "What's one thing that stuck with you?"
   - Short answer — "Your name (optional)"
3. Send button → link tab → copy the link (use the shortened one).
4. Paste it into `u/dave/index.html` → `PROFILE.reviewFormUrl`.
5. Optional (nicer): make the tapped star pre-fill the form's scale question.
   In the form editor: ⋮ → "Get pre-filled link" → pick any rating → copy the link →
   it contains something like `entry.123456789=4`. Put `entry.123456789` into
   `PROFILE.reviewStarsEntryId`.

Responses land in the form's "Responses" tab (link it to a Sheet if you want a spreadsheet).

## 3. Stripe Payment Link (the tips)

1. stripe.com → create an account (NZ supported; you'll need bank details + IRD basics).
2. Dashboard → Payment Links → New link.
3. Product: "Lesson tip", and enable **"Let customers choose what to pay"**
   (suggested amounts like $5 / $10 / $20 work well).
4. Copy the payment link URL into `u/dave/index.html` → `PROFILE.tipUrl`.

Until you do this, the tip section simply doesn't show on the page — the review
flow works on its own, so you can experiment in a lesson before Stripe is set up.

## Updating later

Edit `u/dave/index.html` in the GitHub repo (pencil icon) and commit — the page
updates in about a minute. The QR never changes; it always points at the same URL.
