# Box The Box — Going Live

Two paths, depending on what you want today.

---

## Path 1 — Get a shareable public link in 60 seconds (no domain needed)

Use this if you just want to **share the website with someone today** — a partner, a client, a friend who wants to see it. You don't need to buy `boxthebox.in` for this.

### Steps

1. Go to **https://app.netlify.com/drop**
2. Drag this entire folder (the one containing `index.html`) onto the page
3. Wait 30 seconds
4. You get a link like `https://shiny-jellyfish-9a7e2c.netlify.app`
5. Sign up free with Google (so the link doesn't expire and so you can update it later)
6. In Netlify dashboard → Site settings → "Change site name" → rename it to `box-the-box.netlify.app`

That link works for anyone in the world. **Share it however you want — WhatsApp, email, on a business card.**

You can keep using this Netlify link forever (it's free), or upgrade to your own domain whenever you want.

---

## Path 2 — Use your own domain (boxthebox.in)

Do this when you're ready to look like a real business with your own URL. ≈ 15 minutes total.

### Step 1 — Buy the domain (5 min, ≈ ₹600–900/year for `.in`)

Pick any of these registrars:

- **Cloudflare Registrar** (cheapest, no markup) — https://dash.cloudflare.com
- **GoDaddy** — https://in.godaddy.com
- **Namecheap** — https://www.namecheap.com
- **Hostinger** or **BigRock** — both popular for `.in`

If `boxthebox.in` is taken, alternatives: `boxthebox.co.in`, `boxthebox.co`, `getboxthebox.com`, `boxthebox.shop`.

### Step 2 — You already deployed the site (Path 1 above)

If you skipped Path 1 and want to go straight to a custom domain, the steps are the same: drag the folder onto **https://app.netlify.com/drop** to get it live first.

### Step 3 — Connect the domain

In your Netlify site dashboard:

1. **Domain management** → **Add a domain you already own** → enter `boxthebox.in`
2. Netlify shows you DNS records to set up. There are two ways to do it:

#### Option A — Quick (CNAME)
In your registrar's DNS panel, add these two records:

| Type | Name | Value |
|---|---|---|
| CNAME | `@` (or "root") | `<your-site>.netlify.app` |
| CNAME | `www` | `<your-site>.netlify.app` |

(If your registrar doesn't allow CNAME on the root, use **ALIAS** or **ANAME** — same thing.)

#### Option B — Move DNS to Netlify (recommended)
1. In Netlify → **Set up Netlify DNS for this domain**
2. Netlify gives you 4 nameservers (like `dns1.p01.nsone.net`)
3. Go to your registrar's website → find Nameservers setting
4. Replace the existing nameservers with Netlify's 4
5. Save

### Step 4 — Wait

DNS propagation usually takes 15 minutes to 2 hours (rarely up to 24). When it's done, `https://boxthebox.in` shows your site with a free SSL padlock automatically.

You can check status at **https://dnschecker.org** by entering your domain.

---

## Updating the site later

Whenever you make changes (edit `index.html` or replace an image):

- Drag the folder onto **https://app.netlify.com/drop** again — it updates the live site.
- Or, in Netlify dashboard → Deploys → "Drag and drop your site folder here" → drop the folder → it deploys.

You don't have to redo DNS or anything else. Just re-upload the folder.

---

## Things to do in week 1 (after launch)

- [ ] Sign up at **https://search.google.com/search-console** → add your domain → submit `sitemap.xml`
- [ ] Claim your **Google Business Profile** at https://www.google.com/business — huge for "fulfilment Bhiwandi" / "warehouse near me" searches
- [ ] Set up **Web3Forms** so the contact form delivers to your inbox (see `HOW-TO-EDIT.md`, Part 5)
- [ ] Take real photos of your floor and team (replace the AI ones — see `HOW-TO-EDIT.md`, Part 3)
- [ ] Get a **business email** at your domain — Zoho Mail offers free email at custom domains, Google Workspace is ₹125/user/month

---

## If something breaks

| Problem | Likely cause | Fix |
|---|---|---|
| Domain doesn't resolve after 24 hours | DNS not propagated | Check at https://dnschecker.org |
| Site shows "Not secure" | SSL still provisioning (takes 5-15 min after DNS resolves) | Wait. If still broken after an hour, check Netlify SSL settings |
| Form doesn't deliver | You haven't connected Web3Forms yet | See `HOW-TO-EDIT.md` Part 5 |
| Images don't show | The `images/` folder isn't deployed alongside `index.html` | Re-upload the whole folder |

---

That's it. You're live. Welcome to the internet.
