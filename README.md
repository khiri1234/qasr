# Smoking UAE store

Static storefront hosted on GitHub Pages.

| File | What it is |
|---|---|
| `index.html` | The store customers see |
| `admin.html` | Store admin portal (products, photos, hero banner, offer, delivery, WhatsApp) |
| `data/site-data.js` | All store content: products, hero slides, offer, delivery cities, WhatsApp number |
| `images/` | Product photos |
| `data/admin-users.json` | Admin accounts (created from the admin Team tab) |

## Managing the store

Open `admin.html` on the live site: `https://khiri1234.github.io/qasr/admin.html`.

**Everyday:** sign in with your username and password, make changes, then press **Publish**.
Each publish is one commit to `main`; the live store updates within 1–3 minutes.

**First-time setup (once):**
1. Create a GitHub fine-grained access token at https://github.com/settings/personal-access-tokens/new
   - Repository access: only `khiri1234/qasr`
   - Permissions: **Contents → Read and write**
2. On the admin sign-in page choose *First-time setup: sign in with a GitHub token* and paste it.
3. In the **Team** tab, create your username and password. Add staff accounts there too.

**When the GitHub token expires:** sign in with your password as usual; the page asks for a new
token and saves it for everyone. Or replace it any time under **Team → GitHub token**.

### How accounts work

`data/admin-users.json` stores the GitHub token encrypted with a random team key, and each account
stores that team key encrypted with a key derived from its password (PBKDF2-SHA256, 600,000
iterations → AES-GCM). Passwords are never stored. The file is public, so use strong passwords
(at least 10 characters). Removing an account stops that password from working; if you think the
token itself leaked, delete it on GitHub and paste a new one under **Team → GitHub token**.
