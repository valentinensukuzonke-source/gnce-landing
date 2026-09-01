# GNCE Landing Page

Static landing page for GNCE v2.4.0 (Sovereignty as Code). Prospects land here, then use the **hosted eval sandbox** — no clone or GitHub repo required.

## Hosted sandbox (official domain)

| Item | URL |
|------|-----|
| **Sandbox base** | `https://sandbox.gnce.co.za` |
| **Health check** | `https://sandbox.gnce.co.za/healthz` |
| **Evaluate API** | `POST https://sandbox.gnce.co.za/v1/evaluate` |

All sandbox links on the page read from [`sandbox-config.js`](sandbox-config.js). Change the URL in one place if the hostname ever moves.

## Page flow

- **Try Live Sandbox** → hosted health check (proves tunnel + gateway are up)
- **API Quick Start** → curl examples for `/healthz` and `/v1/evaluate`
- **Request Extended Evaluation** → Formspree form for enterprise pilot / private scenario packs (not required for first API screen)

## Local preview

Open `index.html` in a browser, or:

```bash
npx serve .
```

## Deploy

Push to `main` on [gnce-landing](https://github.com/valentinensukuzonke-source/gnce-landing). Enable GitHub Pages if the site should be served from the repo (optional — can also CNAME `www.gnce.co.za` to GitHub Pages).

## Formspree

The extended-evaluation form posts to Formspree (`xaqpdnvv`). Notifications go to valentine.nsukuzonke@gmail.com with subject `[GNCE Extended Evaluation Request]`.
