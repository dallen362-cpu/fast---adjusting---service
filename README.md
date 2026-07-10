# FAST Adjusting Service Team Corp — Website & Claims App

Miami-Dade's premier family-owned public adjusting firm. AI-powered, fully automated,
communications-centric claims ecosystem (mold, water, fire & smoke restoration +
public adjusting), positioned for Miami's high-value / luxury market.

## Files
| File | Purpose |
|---|---|
| `index.html` | The entire single-file website + app (HTML/CSS/JS). |
| `manifest.webmanifest` | PWA manifest — makes the claims app installable. |
| `service-worker.js` | PWA service worker — install + offline caching. |
| `DEPLOY.md` | Step-by-step hosting + domain-connection guide. |

## Features
- 3D animated background (Three.js) + talking AI concierge ("Ava")
- WIN TV Storm Intelligence Network (before/after storm photo proof)
- Smart DID phone lines + toll-free smart vanity **855-2-ADJUST** (call/text)
- Instant claim-profile photo upload + AI preliminary assessment
- Real-time claim tracker (filed → paid) + installable PWA
- Insurer claim-form inventory with SKU/QR instant lock-match
- Digital-business-card referral / royalty program
- Franchise ($25k), independent-adjuster lead-fulfillment (50/50), careers
- Google review auto-logger/poster, member login portal

## ⚙️ Configure before launch
Open `index.html` and edit the single `CONFIG` block near the bottom `<script>`:
- `PHONES` — the 10 Smart DIDs + toll-free vanity (already set)
- `OWNER_ROUTE` — unpublished cell the DIDs route to (backend use only)
- `GCAL_BOOKING_URL` — Google Calendar appointment-scheduling embed URL
- `FORM_ENDPOINT` — CRM/Zapier webhook for all lead submissions
- `DID_PROVISION_ENDPOINT` — real Smart DID provisioning (Telvergence/Twilio)
- `GOOGLE_REVIEW_URL` / `GOOGLE_PROFILE_URL` — Google review links

## Domains
- Primary brand: **fastadjustingservice.com**
- Vanity redirect: **8552adjust.com** (→ 855-2-ADJUST)
- App: **fastadjusting.app**
- Showroom alt: fastadjustingservice.telvergence.com

## Notes
Simulated (need a backend to go live): Smart DID provisioning, two-way SMS,
AI photo assessment, QR authorization, claim data. See `DEPLOY.md`.
