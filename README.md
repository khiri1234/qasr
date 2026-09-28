# Smoking UAE store

Static storefront hosted on GitHub Pages.

| File | What it is |
|---|---|
| `index.html` | The store customers see |
| `admin.html` | Store admin portal (products, photos, hero banner, offer, delivery, WhatsApp) |
| `data/site-data.js` | All store content: products, hero slides, offer, delivery cities, WhatsApp number |
| `images/` | Product photos |

## Managing the store

1. Open `admin.html` on the live site, e.g. `https://khiri1234.github.io/qasr/admin.html`.
2. Sign in with a GitHub fine-grained access token:
   - GitHub → Settings → Developer settings → Fine-grained tokens → Generate new token
   - Repository access: only `khiri1234/qasr`
   - Permissions: **Contents → Read and write**
3. Make changes, then press **Publish**. Each publish is one commit to `main`; the live store updates within 1–3 minutes.

Keep tokens private: anyone with one can edit the store. To revoke access, delete the token on GitHub.
