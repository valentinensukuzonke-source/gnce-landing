# GNCE Landing Page

Static landing page for GNCE v2.4.0. Prospects **try the hosted sandbox** with one curl — no install, no GitHub access, no forms.

## Prospect flow (Option 1)

1. Open the landing page → **Try sandbox**
2. Copy the curl command (or download the JSON sample)
3. `POST /v1/evaluate` → constitutional verdict + L0–L8 trace + SARS receipt

No wheel, no `gnce-sandbox` repo, no Formspree. Extended scenario packs and Khazna deploy are **post-eval** licensing steps.

## Configure the sandbox URL

Edit **`sandbox-config.js`**:

```javascript
window.GNCE_SANDBOX = {
  url: "https://sandbox.gnce.co.za",
  healthPath: "/healthz",
  evaluatePath: "/v1/evaluate",
  sampleFile: "samples/uae_healthcare_evaluate_sample.json",
};
```

Deploy the gateway: see **`HOSTED_EVAL_SANDBOX.md`** in the private `gnce-framework` repo (`docker-compose.eval.yml` + Cloudflare Tunnel or VPS).

## Files

| File | Purpose |
|------|---------|
| `index.html` | Landing + try-sandbox section |
| `sandbox-config.js` | Hosted eval base URL (single place to update) |
| `samples/uae_healthcare_evaluate_sample.json` | G42 Smart Hospital UAE payload |
| `assets/gn_logo_mark.png` | Logo |

## Local preview

```bash
npx serve .
```

Or open `index.html` in a browser (fetch of sample JSON works when served, not from `file://`).

## GitHub Pages + custom domain

**Live site:** `https://www.gnce.co.za` (after DNS propagates)

### 1. GitHub (this repo) — one-time

1. Open **Settings → Pages** on this repo.
2. **Build and deployment → Source:** **GitHub Actions** (workflow [`.github/workflows/pages.yml`](.github/workflows/pages.yml) deploys on every push to `main`).
3. **Custom domain:** **`www.gnce.co.za`** (must match [`CNAME`](CNAME)).
4. After DNS verifies, enable **Enforce HTTPS**.

### 2. Cloudflare DNS (`gnce.co.za` zone)

Add or update:

| Type | Name | Target | Proxy |
|------|------|--------|-------|
| **CNAME** | `www` | `valentinensukuzonke-source.github.io` | **DNS only** (grey cloud) at first |

After GitHub shows “DNS check successful” and HTTPS is active, you may turn the orange cloud on if desired (SSL mode: **Full**).

Optional apex redirect: Page Rule or Redirect Rule `gnce.co.za` → `https://www.gnce.co.za`.

### 3. Verify

```bash
curl -sSI https://www.gnce.co.za | head -5
curl -sS https://sandbox.gnce.co.za/healthz
```

Sandbox API stays at **`https://sandbox.gnce.co.za`** (separate Cloudflare tunnel — not GitHub Pages).

## Related repos

| Repo | Role |
|------|------|
| **gnce-landing** (this) | Public — hosted eval entry point |
| **gnce-framework** | Private — kernel + `docker-compose.eval.yml` |
| **gnce-sandbox** | Private — extended PoC scenarios (post-eval license only) |
