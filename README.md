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

## Request Sandbox Access form (Formspree)

The form uses **Formspree** so submissions work from **any** mail setup (Gmail, Outlook, Yahoo, webmail-only). No `mailto:` – the form posts to Formspree and they email you.

**One-time setup:**

1. Go to [formspree.io](https://formspree.io) and sign up (free).
2. Create a new form and set the notification email to **valentine.nsukuzonke@gmail.com**.
3. Copy your **form ID** (the string in the URL they give you, e.g. `https://formspree.io/f/xyzabc` → `xyzabc`).
4. In `index.html`, find `FORMSPREE_FORM_ID` and replace it with your form ID:
   - `action="https://formspree.io/f/FORMSPREE_FORM_ID"` → `action="https://formspree.io/f/xyzabc"` (your ID).
5. Push to GitHub; the live form will then submit to Formspree and you’ll get emails at valentine.nsukuzonke@gmail.com with subject `[GNCE Sandbox Access]`.

Until you replace `FORMSPREE_FORM_ID`, the form will post to an invalid URL. Do the setup above so requests reach your inbox.

## Local preview

Open `index.html` in a browser, or serve the folder with any static server (e.g. `npx serve .`).
