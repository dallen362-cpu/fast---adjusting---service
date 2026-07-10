# Deploy Guide — fastadjustingservice.com

This site is a static bundle (`index.html` + `manifest.webmanifest` + `service-worker.js`).
It hosts anywhere. Recommended: **Cloudflare Pages** (free, fast, free SSL, easy custom domains).

---

## Option A — FREE now, buy domains later (recommended to start)
Go live today on a free `*.pages.dev` subdomain; attach the real domain whenever you buy it.

1. Push this repo to GitHub (see "GitHub" below).
2. Cloudflare dashboard → **Workers & Pages** → **Create** → **Pages** → **Connect to Git**.
3. Pick this repo. Build settings: **Framework = None**, **Build command = (blank)**,
   **Output directory = `/`** (root). Deploy.
4. You're live at `https://<project>.pages.dev` — free, with SSL. Start marketing.

## Option B — With the custom domains
1. Register the domains (Cloudflare Registrar = at-cost, free WHOIS privacy):
   - `fastadjustingservice.com` (primary)
   - `8552adjust.com` (vanity redirect → main site)
   - `fastadjusting.app` (app)
2. In the Pages project → **Custom domains** → add `fastadjustingservice.com` and `www`.
   Cloudflare auto-creates the DNS + SSL.
3. For `8552adjust.com`: add a **Redirect Rule** → 301 to `https://fastadjustingservice.com`.
4. `fastadjusting.app`: point at the same Pages project (`.app` requires HTTPS — already covered).

---

## GitHub
```bash
# from inside this folder (already committed locally)
git branch -M main
git remote add origin https://github.com/<YOUR_USERNAME>/<YOUR_REPO>.git
git push -u origin main
```
Then connect the repo in Cloudflare Pages (Option A, step 2). Every future `git push`
auto-redeploys the live site.

---

## After launch — marketing checklist
- [ ] Google Business Profile (Google Listings) — verify address, add photos, request reviews
- [ ] Yelp for Business — claim + complete listing
- [ ] Point `GOOGLE_REVIEW_URL` in `index.html` at your GBP "write a review" link
- [ ] Set `FORM_ENDPOINT` to a Zapier/Make webhook so leads hit your CRM/email
- [ ] Set `GCAL_BOOKING_URL` to your Google Calendar appointment-schedule embed
- [ ] Submit `fastadjustingservice.com` to Google Search Console + Bing Webmaster

## Backend (to make simulated features real)
Smart DID provisioning + two-way SMS (Telvergence/Twilio/Bandwidth), AI photo
assessment, QR claim authorization, auth + claim database, secure photo storage.
Front-end already has config hooks/endpoints ready to point at these services.

---

## Standalone repo notes (this dedicated repo)
- `index.html` is at the ROOT, so a custom domain maps straight to the FAST homepage.
- To activate the custom domain on **GitHub Pages**: rename `CNAME.txt` → `CNAME`
  (its contents are already `fastadjustingservice.com`), then set the domain in
  repo Settings → Pages. Leave it as `CNAME.txt` until the domain is live so the
  free `*.github.io` preview keeps working.
- On **Cloudflare Pages**: ignore CNAME.txt; attach the domain in the Pages project
  UI. `_headers` and `_redirects` are already Cloudflare-ready.
