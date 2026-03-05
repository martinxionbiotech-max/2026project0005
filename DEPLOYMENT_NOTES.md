# GitHub Pages domain / redirect fix notes

## Why `www.birdfanciers.com` was jumping to `/lander`
That redirect is **not produced by this static HTML file**. It is usually caused by one of these external settings:

1. Domain provider URL forwarding rule (often called "URL Redirect", "Web Forwarding", or parking page).
2. DNS records pointing `www` to a third-party landing/parking service instead of GitHub Pages.
3. Existing CDN/edge redirect rule outside this repo.

## What was changed in this repo
- Added `CNAME` with `www.birdfanciers.com` so GitHub Pages serves the correct host.
- Added `/lander/index.html` to safely redirect any `/lander` traffic back to `/`.
- Updated site URLs in `index.html` from `birdfancier.com` to `www.birdfanciers.com` for consistency.

## Required DNS checks (outside repo)
For GitHub Pages custom domain, ensure:
- `www` is a `CNAME` to `<your-github-username>.github.io`.
- Remove any URL forwarding rule that appends `/lander`.
- In repository **Settings → Pages**, set Custom domain to `www.birdfanciers.com` and enable HTTPS.
