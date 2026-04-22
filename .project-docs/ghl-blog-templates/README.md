# GHL Blog Templates — blog.withheart-marketing.com

**Last synced with main site:** 2026-04-22

These files are the canonical header and footer HTML pasted into Talie's GHL (GoHighLevel) sub-account templates for `blog.withheart-marketing.com`. Connor paste-and-replaces them in GHL when the main site navigation or footer changes.

## Why these live here (and not in GHL only)

GHL doesn't have git. When the main site changes (nav links, footer taglines, offerings), these templates need the same update. Keeping the source of truth in the repo means:
- Git history shows when the blog was last synced
- Future sessions can diff the blog nav against the main site nav
- If GHL loses the template, we can repaste

## Files

- `header.html` — the sticky nav at the top of every blog page (desktop + mobile)
- `footer.html` — the 4-column footer at the bottom of every blog page

## Absolute URLs are required

Since the blog lives on a subdomain (`blog.withheart-marketing.com`), every link to the main site uses absolute URLs (`https://withheart-marketing.com/work-with-me/`). Relative URLs would resolve to the blog subdomain and 404.

## Update protocol

When the main site homepage nav or footer changes:

1. Open `~/Projects/withheart-backup/index.html`
2. Compare the `<nav>` block and `<footer>` block against `header.html` and `footer.html` here
3. Update these GHL template files to match (converting relative URLs to absolute)
4. Paste into GHL template editor at blog.withheart-marketing.com
5. Commit to git with message noting the sync

## Last sync changes (2026-04-22)

- "Work With Me" link: `#services` anchor → `/work-with-me/` (new standalone services page)
- Footer tagline: "Heart-centered brand strategy..." → "Heart-centered brand marketing..."
- Applied in both desktop nav + mobile menu (header) and Quick Links (footer)
