# fullsupply.org — Static Mirror

A static, archival snapshot of [fullsupply.org](https://fullsupply.org/) (a WordPress /
Elementor site), published via GitHub Pages at:

**https://CRinATL.github.io/fullsupply-web-mirror/**

The content is owned/managed by the site operator and hosted here with permission.

- **Source:** https://fullsupply.org/
- **Snapshot date:** 2026-06-11
- **Captured with:** `wget --mirror` (full recursive crawl, page requisites, link conversion to
  relative paths so it works under the `/fullsupply-web-mirror/` Pages subpath).

## Known limitations (dynamic components that do NOT work in a static mirror)

This is a static copy with no PHP/WordPress backend, so any server-side or interactive feature is
non-functional. These need to be handled separately (e.g. embeds, third-party hosted widgets, or a
real backend):

| Component | Where | Why it won't work |
|-----------|-------|-------------------|
| **Gravity Forms** signup (`gform_3`) | Home page and likely contact/partner pages | Submits via AJAX to the WordPress backend, which does not exist here. |
| **Google reCAPTCHA** | On the Gravity Form(s) | Requires a Google + server verification round-trip. |
| **The Events Calendar** ticketing/checkout | `/events/`, `tickets-checkout`, `tickets-order` | Server-rendered cart/checkout; checkout/order pages and iCal export were excluded from the crawl. |
| **PayPal / 10to8 donation & booking buttons** | `/ways-to-give/` | External payment/booking widgets whose flows depend on the live backend. Buttons may render but won't complete a transaction. |
| **Site search / dynamic WordPress queries** | site-wide | No PHP backend on GitHub Pages. |

## Notes

- Google Fonts and reCAPTCHA assets load from their live CDNs (left as absolute URLs), so the site
  renders correctly when viewed online but is not fully self-contained for offline use.
- Internal page-to-page links were rewritten to relative local paths by `wget --convert-links`.
