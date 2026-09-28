# Smoking UAE store

Static storefront hosted on GitHub Pages.

| File | What it is |
|---|---|
| `index.html` | The store customers see |
| `admin.html` | Store admin portal (products, photos, hero banner, offer, delivery, WhatsApp) |
| `data/site-data.js` | All store content: products, hero slides, offer, delivery cities, WhatsApp number |
| `images/` | Product photos |
| `i18n.js` | Storefront translations: English, Arabic, Russian, Filipino, Hindi, Urdu, Persian |
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

**Roles:** *Admin* can do everything. *Staff* can manage products, photos, the hero banner and the
offer, and change their own password; the Delivery & WhatsApp settings and team management are
hidden from them. Admins change a member's role in the Team tab. Accounts created before roles
existed count as admin. Roles control what the admin page shows: every account unlocks the same
GitHub token, so only give accounts to people you trust.

**When the GitHub token expires:** sign in with your password as usual; the page asks for a new
token and saves it for everyone. Or replace it any time under **Team → GitHub token**.

### How accounts work

`data/admin-users.json` stores the GitHub token encrypted with a random team key, and each account
stores that team key encrypted with a key derived from its password (PBKDF2-SHA256, 600,000
iterations → AES-GCM). Passwords are never stored. The file is public, so use strong passwords
(at least 10 characters). Removing an account stops that password from working; if you think the
token itself leaked, delete it on GitHub and paste a new one under **Team → GitHub token**.

## Languages

The store has a language button (globe icon) with English, العربية, Русский, Filipino, हिन्दी, اردو and
فارسی. Arabic, Urdu and Persian switch the layout to right-to-left. The first visit follows the
browser's language; the choice is remembered. Text entered in the admin (product names and
descriptions, hero slides, the offer) is shown as typed. Orders sent on WhatsApp stay in English
and note the customer's language. To change a translation, edit `i18n.js`.
