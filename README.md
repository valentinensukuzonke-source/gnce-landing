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

## GitHub Pages

Push to `main`; enable Pages → deploy from branch root. Update `sandbox-config.js` when the public eval URL is live.

## Related repos

| Repo | Role |
|------|------|
| **gnce-landing** (this) | Public — hosted eval entry point |
| **gnce-framework** | Private — kernel + `docker-compose.eval.yml` |
| **gnce-sandbox** | Private — extended PoC scenarios (post-eval license only) |
