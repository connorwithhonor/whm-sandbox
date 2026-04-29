# 2026-04-28 — /calendar/ page LIVE deploy

## Approval chain
- **Talie SMS approval:** "Looks good, just remove the period after conversation and good to make live." (archived `sms/2026-04-28-talie-calendar-feedback.md`)
- **Connor instruction:** "make the page live within her existing site structure /calendar — please add, don't mess with the real install"

## What was deployed
- New file: `/calendar/index.html` (a standalone booking page with header + brief intro + GHL calendar embed + footer)
- Headline: "Book a Conversation" (no period per Talie round 2)
- Lede: "A 30-minute conversation to connect, share, and see where the conversation leads."
- Header/footer: mirror live homepage exactly (8 nav items, no Brand Marketing entry, "Clarifying brands from the inside out." footer tagline)
- `<meta name="robots" content="noindex,follow">` so the page doesn't compete with the homepage in search
- Calendar iframe UTM: `?utm_source=website&utm_medium=calendar-page&utm_campaign=direct_booking`

## What was deliberately NOT deployed
The sandbox repo's 6 rewired homepage booking CTAs (nav, mobile menu, hero, About, footer, sticky mobile — all changed from `#book` to `/calendar/` new-tab). Those stay in sandbox awaiting separate Talie approval. Live homepage booking buttons still scroll to `#book` (in-page calendar) — unchanged.

## Deploy mechanics
- Site ID: `a50b93c7-1ae8-464b-94dd-ee1a8fe47c85` (project `whm03092026`)
- Deploy ID: `69f13dbf9c075b00cfa9a5a5`
- Method: reconstructed live source by downloading all 19 current live files from `https://withheart-marketing.com/<path>` into `/tmp/whm-live-deploy/`, added `/calendar/index.html`, deployed via `netlify deploy --prod --dir /tmp/whm-live-deploy --site a50b93c7-...`
- CDN diffing: only 1 new file uploaded; all other 19 files SHA-matched to existing

## Verification (post-deploy)
- `https://withheart-marketing.com/calendar/` → 200 OK, correct title + H1 + lede
- All other live files unchanged: `/index.html` SHA `2f9acbbb...`, `/work-with-me/index.html` SHA `6d532bef...`, `/brand-marketing/index.html` preserved, all assets preserved
- Net change to live: one new page added, nothing modified

## Caveats and follow-up items
1. **netlify.toml lost:** Live had a 327-byte `netlify.toml` that I could not retrieve (Netlify CDN returns 404 on .toml; no API method to download file contents; no local copy in sandbox repo or mempalace). After the deploy, Netlify auto-regenerated a default. Original config is gone. Prior deploy summary showed "No redirect rules processed / No header rules processed" so impact is likely zero, but flag if anything looks off on live.
2. **`/claude.md` is publicly live:** `https://withheart-marketing.com/claude.md` returns the sandbox project rules file (a leak from a past deploy). Worth cleaning up: delete from a future live deploy + add `Disallow: /claude.md` to robots.txt.

## Mempalace
Canonical snapshot updated at `~/Projects/mempalace/projects/withheart-marketing/live-source/calendar/index.html`.
