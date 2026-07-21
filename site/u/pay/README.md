# Wallet marks

Both pages look for two files in this folder:

- `apple-pay.svg`
- `google-pay.svg`

If either is missing, that mark falls back to plain text ("Apple Pay" /
"Google Pay") automatically — the page never shows a broken image. So this is
safe to leave empty until you get round to it.

## Where to get them

Use the **official** artwork, not a recreation — both companies require it,
and hand-drawn versions look subtly wrong.

**Apple Pay** — Apple Pay Marketing Guidelines:
https://developer.apple.com/apple-pay/marketing/
Download the "Apple Pay mark" (the badge with the Apple logo + "Pay").
Save it here as `apple-pay.svg`.

**Google Pay** — Google Pay brand guidelines:
https://developers.google.com/pay/api/web/guides/brand-guidelines
Download the Google Pay mark. Save it here as `google-pay.svg`.

## The rules that actually matter

- Only show a mark for a wallet you genuinely accept. You do — Stripe enables
  both — so this is exactly the "indicate acceptance" use both guidelines allow.
- Use the artwork as supplied: don't recolour it, stretch it, or rebuild it.
- Keep clear space around it and respect the minimum size (the pages render
  the marks at 15px tall, which is comfortably above both minimums).
- Dark background: take the **white/monochrome** variant of each mark where
  the guidelines offer one — it'll sit better on the granite palette than the
  black-on-white version.

The pages render the marks at 72% opacity so they read as quiet reassurance
rather than advertising; that's a CSS opacity on the whole image, not an
alteration of the artwork itself.
