# SMS Thread — Talie Knutson, 2026-04-23 — Post-Launch Mobile + Desktop Feedback

**Source:** iMessage thread, Connor ↔ Talie K., relayed to Claude via screenshots throughout the day
**Context:** Day after services page went live. Talie walk-tested on her phone and desktop, flagged bugs across 3 separate rounds. All fixes deployed same day.

---

## Thread 1 — Morning Mobile Review

> **Talie (screenshot of mobile menu):** On mobile in the nav it does not say Home can we add that?
>
> Can you also make the with heart marketing logo in the top nav clickable to go to home? So it says home in the drop down and the logo is also clickable.
>
> Make sure it's all consistent too across the site and blogs
>
> From the new work with me services page there is no way to get back to the home page.

Also in the same message she asked about the Google search snippet:

> **Talie (screenshot of Google search result for "withheart-marketing"):** In google on my phone I typed in my website in the search bar and this is what shows up. The description only talks about the with heart approach. Is this the best description for this from a search perspective?

**Translated to spec:**
- Mobile menu needs Home at top (was being clipped by CSS)
- Logo in nav clickable to home (homepage + services page)
- From services page, Home link + logo both need to return to homepage
- Apply same changes to GHL blog
- Google snippet talks about brand strategy — Google's cache is pre-rebrand, needs re-index

Connor submitted homepage re-index via Google Search Console URL Inspection. Services page still pending.

## Thread 2 — Walk Test (mid-morning)

> **Talie:** The navigation on the work with me page is not clicking out. I tried to get to the approach from that page and it didn't click anywhere and then tried case studies and it didn't click anywhere.
>
> Also from the approach page when I click explore route [root] and it goes to the new brand strategy page there's this weird loading where it loads and then it just jumps. Not sure what that was. I'm looking at this now while I'm out walking on my phone.

**Translated to spec:**
- Services page mobile menu links to The Approach, Case Studies were bare `#approach`, `#cases` — dead clicks on services page
- Anchor navigation "load then jumps" = no scroll-padding-top + instant scroll behavior, target sections were landing behind the fixed nav

## Thread 3 — Desktop Nav (later)

> **Talie (screenshot of Walk Away boxes):** On my desktop - when I am on the Work With Me page and I click Work With Me in the nav, it links here. Look at the URL as well. [URL shown: /work-with-me/#walkaway]
>
> **Talie (screenshot of Work With Me header):** Instead of where it should go and link to here.

**Translated to spec:**
- Services page desktop nav "Work With Me" goes to `#walkaway` (Walk Away With section) — should go to `#top` (page-intro with "Work With Me" H1)

## Fixes Deployed (All Live Same Day)

1. **Commit `41d69b1`** — Mobile menu CSS fix (flex-start + scroll so Home visible) + services page nav-logo/mobile Home `href="/"` + GHL template mobile CSS fix
2. **Commit `d4db10a`** — Services page mobile menu cross-page anchors `/#approach` etc. + smooth scroll + `scroll-padding-top:100px`
3. **Commit `64b8d46`** — Services page "Work With Me" nav `#walkaway` → `#top`
4. **Commit `ad6172c`** — Post-launch audit: services footer anchors + sitemap + photo alt

All live on https://withheart-marketing.com

## Text Recap Sent to Talie (End of Day)

Connor asked Claude to draft a recap text in his voice. Sent to Talie via iMessage:

> Hey Talie, everything you flagged is now fixed and live:
> - Home link is visible at the top of the mobile menu again
> - Logo in the top nav is clickable back to home from both the homepage and the Work With Me page
> - On the Work With Me page, tapping Work With Me in the nav now lands at the top of the page (the Work With Me header), not halfway down into the phase boxes
> - Nav links from the Work With Me page to The Approach, Case Studies, Testimonials, About, etc. all correctly jump back to the right section on the homepage
> - Fixed the loading-and-then-jumps feel when you click Explore Root or any of the phase buttons. Smooth now.
>
> While I was in there I also cleaned up a few things you would not have seen:
> - Footer Quick Links on the Work With Me page were pointing to dead spots, fixed those
> - Added the Work With Me page to the sitemap so Google can find it
> - Updated one photo alt tag to say brand marketing consultant instead of brand strategist
>
> Already submitted the homepage to Google for a re-index so the cached title should update in the next day or two. All good. Let me know if you see anything else on your end.
