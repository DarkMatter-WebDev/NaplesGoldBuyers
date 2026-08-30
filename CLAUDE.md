# NaplesGoldBuyers.com

Static site on Netlify (`publish = "."`). **Deliberately one indexable page.** Everything else
301s to `naplesestatejewelry.com`. Read the "Why this is one page" section before adding anything.

## The business

This domain is a marketing funnel for **Naples Estate Jewelry** — it is not a separate business.

| | |
|---|---|
| Owner | Chris Surette |
| Showroom | 6240 Shirley St, Ste 104, Naples, FL 34109 (a shared suite inside Sharon Lynch Collections, Naples Art District) |
| Phone | (239) 404-8505 |
| Email | info@naplesestatejewelry.com |
| Main site | https://naplesestatejewelry.com |
| Google Business Profile | https://maps.google.com/?cid=17050430560749692864 |

Buys gold, silver, coins, diamonds, watches, and whole estates. Also sells retail (~52 pieces
online). Showroom hours plus private appointments and home visits across Collier and Lee counties.

**NAP must be byte-identical everywhere it appears.** Inconsistent name/address/phone across the
network is a real local-SEO negative.

## Layout

```
index.html              The only indexable page. Photo-upload lead portal (Netlify form
                        "estimate-request"), WebGL background, full service coverage.
styles.css              Shared stylesheet for the sub-pages. No WebGL — these must stay fast.
sunscroll.js            Raw WebGL fragment shader for index.html's background.
logo.webp               1024px. logo-512 / logo-768 are the srcset variants.
og-image.png            1200x630, 256-colour quantised (~101 KB).
netlify.toml            publish + security headers + all six 301s.
robots.txt / sitemap.xml
sell-gold-*/            Four city pages. SHADOWED by forced redirects — not live.
vender-oro-naples/      Spanish page. SHADOWED by a forced redirect — not live.
logo-animated.html      Internal tools. Both carry noindex.
og-image-generator.html
```

The `sell-gold-*` and `vender-oro-naples` directories are kept on disk so the redirects are a
one-line revert per page, but `force = true` means Netlify never serves them.

## Why this is one page

`naplesestatejewelry.com` already has **198 sitemap URLs**, including `/sell/<city>` for naples,
marco-island, bonita-springs, estero, fort-myers, cape-coral — and a **complete Spanish mirror**
under `/es/` (98 of those URLs). Anything built here for those queries competes with pages on a
domain that has the reviews, the Business Profile, and the entity behind it.

The network also has **essentially zero independent backlinks** — every external link traces back
to a domain the owner controls — and `naplesestatejewelry.co` has 117 pages Google declined to
index, 66 of them "Discovered – currently not indexed". Two weak pages lose to one good page here.

**Before adding any page: check whether naplesestatejewelry.com already covers the query. If it
does, improve that page instead.**

## Rules

- **Never hardcode opening hours.** They live on the GBP and naplesestatejewelry.com. Pages here
  link to `naplesestatejewelry.com/contact` for hours. Hardcoding them guarantees they go stale.
- **Never reference `naplesjewelrybuyers.com` or the name "Naples Jewelry Buyers."** A different
  real business trades under that name locally (11542 Tamiami Trl E, 38 reviews). The owner does
  not want visitors seeing it. He owns the domain, but it must not appear on this site.
- **Never create a second Google Business Profile** for this brand. An unverified duplicate existed
  and was deleted on 2026-08-29. A second listing at 6240 Shirley St risks the verified profile.
- **Structured data describes Naples Estate Jewelry**, with `alternateName: "Naples Gold Buyers"`
  and `@id: https://naplesestatejewelry.com/#business`. Keep the entity consolidated.
- **Keep claims accurate.** "One small shared showroom, largely by appointment" — not a full retail
  sales floor, not appointment-only.

## Local dev

```bash
python -m http.server 3333
```

`.claude/launch.json` defines this. **Netlify redirects do not run under it** — the six 301s can
only be verified against the deployed site.

## Post-deploy checks

1. Click one city redirect and the Spanish redirect (`/vender-oro-naples/`) to confirm they 301.
2. Confirm www and http still fold into `https://naplesgoldbuyers.com`.
3. Search Console: property `sc-domain:naplesgoldbuyers.com` (verified 2026-08-29, DNS TXT).

## Where the real wins are

Nothing in this repo moves revenue much. It is a one-page site with no backlinks. As of
2026-08-29 the levers that matter are all outside it, in rough order: **grow Google reviews
(22 vs the competitor's 38)**, add interior photos to the GBP, open at 10 AM to match the
competitor, and spend the unclaimed $500 Google Ads credit on "sell gold naples" — a SERP with
no local map pack, which is why an organic/paid result is the only thing that can win it.
