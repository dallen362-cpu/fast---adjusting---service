# Setup Cheat-Sheet — fastadjustingservice.com

Everything you need to go live + get email working. Do these in order once the
domain is registered and its nameservers point at Cloudflare.

---

## 1. Email — contact@fastadjustingservice.com  (FREE via Cloudflare)
Cloudflare **Email Routing** forwards mail to an inbox you already own (e.g. Gmail).
Best free option — no mailbox to manage.

1. Cloudflare dashboard → select **fastadjustingservice.com** → **Email** → **Email Routing** → **Get started**.
2. Cloudflare auto-adds the required **MX + SPF (TXT)** records — click **Add records / Enable**.
3. **Routing rules** → **Create address**:
   - Custom address: `contact@fastadjustingservice.com`
   - Action: **Send to** → your inbox (e.g. `dallen362@gmail.com`) → verify the confirmation email.
4. (Optional) add a **catch-all** → forward `*@fastadjustingservice.com` to the same inbox.
5. To **send AS** contact@ from Gmail: Gmail → Settings → Accounts → "Send mail as" → add
   contact@fastadjustingservice.com (uses Gmail's SMTP; no extra cost).

**Want a full mailbox (not just forwarding)?**
- **Zoho Mail** — free tier, 1 domain, real inbox. MX: `mx.zoho.com`, `mx2.zoho.com`, `mx3.zoho.com`.
- **Google Workspace** — $6/user/mo, best deliverability. MX: `smtp.google.com`.

> Don't run Cloudflare Email Routing AND another mail host at the same time — pick one MX set.

---

## 2. Hosting the site

### Option A — Cloudflare Pages (recommended; matches your existing setup)
1. Cloudflare → **Workers & Pages** → **Create** → **Pages** → **Connect to Git** → pick the repo.
2. Build settings: **Framework preset = None**, **Build command = (blank)**, **Output dir = `/`**.
3. Deploy → live at `https://<project>.pages.dev`.
4. **Custom domains** → add `fastadjustingservice.com` and `www` → Cloudflare wires DNS + SSL automatically. (No manual records needed — this is why Cloudflare is easiest.)

### Option B — GitHub Pages
Repo → **Settings → Pages** → Source: `main` / root. Then add DNS at Cloudflare:

| Type | Name | Value | Proxy |
|---|---|---|---|
| A | @ | 185.199.108.153 | DNS only (grey cloud) |
| A | @ | 185.199.109.153 | DNS only |
| A | @ | 185.199.110.153 | DNS only |
| A | @ | 185.199.111.153 | DNS only |
| AAAA | @ | 2606:50c0:8000::153 | DNS only |
| AAAA | @ | 2606:50c0:8001::153 | DNS only |
| AAAA | @ | 2606:50c0:8002::153 | DNS only |
| AAAA | @ | 2606:50c0:8003::153 | DNS only |
| CNAME | www | dallen362-cpu.github.io | DNS only |

Then rename `CNAME.txt` → `CNAME` in the repo (contents already `fastadjustingservice.com`).

> Note: GitHub Pages requires the A/AAAA records set to **DNS only** (grey cloud), not proxied.

---

## 3. Wire the site's CONFIG (in index.html, bottom `<script>`)
- `GOOGLE_REVIEW_URL` → your Google Business "write a review" link
- `GOOGLE_PROFILE_URL` → your Google Maps profile link
- `FORM_ENDPOINT` → Zapier/Make webhook (so intake, referral, franchise, member & review leads hit your CRM/email at contact@)
- `GCAL_BOOKING_URL` → Google Calendar appointment-schedule embed URL

---

## 4. Marketing launch checklist
- [ ] Google Business Profile (Google Listings) — verify, photos, request reviews
- [ ] Yelp for Business — claim + complete
- [ ] Google Search Console + Bing Webmaster — add & verify the domain
- [ ] Submit sitemap / request indexing
- [ ] Test: call + text 855-2-ADJUST, submit each form, install the PWA
