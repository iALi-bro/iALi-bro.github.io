# iPayment site

Home page, privacy policy, and terms of service for the iPayment iOS app —
the three URLs Google Cloud Console requires on the OAuth **Branding** page.

## Before publishing

Replace `ikhaled.dev@icloud.com` in all three HTML files with a real address:

    grep -rl ikhaled.dev@icloud.com . | xargs sed -i '' 's/ikhaled.dev@icloud.com/you@example.com/g'

## Deploy to GitHub Pages

1. Create a repo named `<your-username>.github.io` (a *user* site, so pages sit at the root).
2. Copy these files in, commit, push.
3. Settings → Pages → deploy from `main`, folder `/ (root)`.
4. Confirm the pages are live over HTTPS.

## Verify the domain with Google

1. Open https://search.google.com/search-console and add a **URL prefix** property
   for `https://<your-username>.github.io/`.
2. Choose the **HTML file** verification method, commit the `google*.html` file it
   gives you to the repo root, push, then click Verify.
   (DNS verification is not possible on `github.io` — you do not control its DNS.)
3. Use the same Google account as your Cloud Console project, or add that account
   as an owner of the verified property.

## Fill in the Branding page

In Cloud Console → APIs & Services → OAuth consent screen → Branding:

1. Add `<your-username>.github.io` under **Authorized domains** *first* — the URL
   fields will not validate until the domain is registered there.
2. Application home page:  `https://<your-username>.github.io/`
3. Privacy policy link:    `https://<your-username>.github.io/privacy.html`
4. Terms of service link:  `https://<your-username>.github.io/terms.html`

## Note on the Drive scope

iPayment requests `drive.appdata`, which Google classifies as a **sensitive** scope,
so publishing to production triggers a verification review (scope justification plus
a demo video). The privacy policy already carries the Limited Use disclosure that
review looks for.
