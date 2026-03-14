# GNCE Landing Page

Static landing page for GNCE v2.4.0 (Sovereignty as Code). Used for sandbox access requests and product positioning.

## Sandbox link

The page includes links to the **GNCE sandbox** (banking, insurance, adversarial, G42 scenarios). The default href is:

- `https://github.com/gnce-labs/gnce-sandbox`

**Replace this URL** in `index.html` with your actual sandbox repository (e.g. your GitHub org + `gnce-sandbox`) in:

1. **Nav** – the "Sandbox" link in the top-right.
2. **Hero** – the "Open Sandbox" button.
3. **Footer** – the "Sandbox" link.

Search for `gnce-labs/gnce-sandbox` in `index.html` and update all three occurrences.

## Why link to the sandbox

- **Request Sandbox Access** = for users who don’t have access yet (form + email).
- **Open Sandbox** = for users who already have access; takes them straight to the repo (clone, setup, run scenarios).

So the flow is: land on page → request access → (after approval) use the Sandbox link to get to the repo.

## Local preview

Open `index.html` in a browser, or serve the folder with any static server (e.g. `npx serve .`).
