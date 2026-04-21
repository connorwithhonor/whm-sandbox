# Services Rebuild — Architecture Plan (Draft)

**Created:** 2026-04-21, post-10:30 call with Talie
**Basis:** Meeting transcript `2026-04-21-services-rebuild-call-transcript.md` + existing rebrand on live
**Status:** Draft pending Talie's sketches + Word doc
**Owner:** Connor. Build executed against `claude/services-rebuild` branch.

---

## What's changing

### Homepage (`withheart-marketing.com/`)

**Stays unchanged:**
- Hero
- Proof bar (Disney / Princess Cruises / MTV / Jada Toys)
- Why This Work Matters (the "Heart-Centered Brand Marketing" copy from Talie's Email 2)
- About / Case Studies / Testimonials
- FAQ section
- Book a Conversation (calendar)
- Footer

**Removed:**
- The current services section ("Two Ways to Get Started with Finding Clarity" / DIY / DFY cards). Relocates to the new services page. The `#services` anchor on the homepage nav can repurpose to `#approach` or be removed.

**Added:**
- New subsection appended to The With Heart Approach section:
  - Background: **light teal** (signals a different thought process)
  - Headline: **"You walk away with"**
  - Brief intro paragraph under headline
  - Four boxes mirroring the Approach box structure
  - Styling: **teal background, white boxes** (inverse of existing Approach boxes)
  - Icons: **yellow** versions of the Root/Reveal/Rise/Radiate icons, smaller than in the Approach section

  | Phase | Walk-away headline | Deep link target |
  |-------|-------------------|------------------|
  | ROOT | Brand Foundation | `/work-with-me/#brand-strategy` |
  | REVEAL | Brand Messaging | `/work-with-me/#brand-strategy` |
  | RISE | Marketing Strategy | `/work-with-me/#marketing-strategy` |
  | RADIATE | Activation and Guidance | `/work-with-me/#activation` |

  Each box: small phase label on top, bold walk-away phrase, short description (from Talie's Word doc), button labeled "Explore Root" / "Explore Reveal" / etc. pointing to the corresponding deep link.

### New Services Page (`/work-with-me/`)

**URL rationale:** Matches Talie's verbal language ("Work With Me" appears in nav, she repeatedly said "work with me page" in the call). Can add a `/services/` → `/work-with-me/` redirect for SEO hedge.

**Structure (top to bottom):**

1. **Work With Me header section**
   - Eyebrow: "Work With Me"
   - Headline: TBD (she hadn't decided — possibly "What you walk away with")
   - Brief intro paragraph
   - (Possibly) repeated four "You walk away with" boxes — she was leaning yes for consistency. Decision: build with them in, make them removable if she changes her mind.

2. **Brand Strategy section** (`#brand-strategy`)
   - Eyebrow: small dash "Root / Reveal" label
   - Headline: "Brand Strategy"
   - Brief intro
   - The existing "Two Ways to Get Started with Finding Clarity" content:
     - DIY Workbook card
     - Done-For-You Brand Strategy card
     - Both essentially unchanged from current homepage content, just relocated
   - Button: "Book a Complimentary Conversation" → jumps to homepage calendar (anchor or redirect)
   - Small downward-arrow hint pointing to next section: "Marketing Strategy ↓"

3. **Marketing Strategy section** (`#marketing-strategy`)
   - Eyebrow: small dash "Rise"
   - Headline: "Marketing Strategy"
   - Brief intro (from Talie's Word doc)
   - Single box with what-they-get bullets (mirrors the Brand Strategy box design)
   - Button: "Book a Complimentary Conversation"
   - Small downward-arrow hint: "Activation and Guidance ↓"

4. **Activation and Guidance section** (`#activation`)
   - Eyebrow: small dash "Radiate"
   - Headline: "Activation and Guidance"
   - Brief intro
   - Single box with what-they-get bullets
   - Button: "Book a Complimentary Conversation"

5. **(Maybe) Brand Audit soft-CTA** — Talie was unresolved. Leaning toward a subtle line: "Don't know where to start? Let's talk about a brand audit" → books a conversation. Recommendation: include it as a low-commitment on-ramp.

6. **Right For You checklist** — Connor and Talie agreed in the call: REMOVE this section from the new services page. It's already on the homepage and duplicating isn't valuable here.

7. **FAQ section** — retain. Same FAQs as homepage work, or a new set focused on services (decision TBD). Default: reuse homepage FAQs for consistency.

8. **Book a Complimentary Conversation section** — same widget as homepage (iframe calendar). Keeps users on-page so they can make the booking decision without bouncing back.

9. **Footer** — site-wide, unchanged.

### Navigation + Wiring

- Nav bar "Work With Me" button → `/work-with-me/`
- Homepage deep-link buttons (Explore Root / Reveal / Rise / Radiate) → `/work-with-me/#<section>`
- Blog post CTAs can link to `/work-with-me/`
- No new window, opens in same tab, nav stays consistent — page should feel like part of the existing site

---

## Design system tokens

| Element | Homepage Approach (current) | New "Walk Away With" | Services page sections |
|---------|----------------------------|---------------------|----------------------|
| Background | White | Light teal | White |
| Box bg | Teal | White | Existing box design (white on white bg) |
| Icon color | Current (teal) | Yellow, smaller | (same as current approach section) |
| Font/spacing | Existing | Match existing | Match existing |

Icons are in Talie's asset folder, yellow versions. Connor needs to confirm the exact file paths when starting the build.

---

## Critical constraints (from Talie during call)

1. **Main site content above the services section stays identical.** Don't touch hero, proof bar, Why This Work Matters, About, Case Studies, Testimonials.
2. **Services section moves entirely off the homepage.** Don't leave a ghost.
3. **Keep `The With Heart Approach` framing** — everything she built around Root/Reveal/Rise/Radiate stays the spine.
4. **Meta/schema changes are deferred to the final pass,** and the rule for that pass is **additive, not replace.** Brand strategy STAYS in all back-end tags. Brand marketing gets ADDED alongside.
5. **No pricing anywhere.**

---

## Flagged tension: meta/schema rework

The live deploy earlier today (2026-04-21 morning) **removed brand strategy from much of the back end** — title tag, meta description, OG title/description, schema description, keywords lead position all lead with "brand marketing" only.

Talie's instruction at the end of the call reverses this: "not removing anything we have. Like, the brand strategy part is still very important."

**Resolution for the final schema pass (after the services page is live):**
- Re-add brand strategy to title tag (pipe-separated or equivalent)
- Re-add brand strategy phrases to meta description, og:description, twitter:description
- Update ProfessionalService schema description to mention both
- OfferCatalog should list all three services: Brand Strategy (Root+Reveal), Marketing Strategy (Rise), Activation and Guidance (Radiate)
- knowsAbout and keywords arrays already have both — leave those
- Visible body copy (hero, Why This Work Matters, etc.) can stay brand-marketing-led since that's her umbrella positioning

This schema pass happens **after** the services page is built and Talie approves the whole flow end-to-end.

---

## Build order

1. **Wait for Talie's sketches** (photos she's sending after the luncheon)
2. **Wait for her Word doc** (the full copy, targeting ~1:30 PM delivery)
3. Confirm URL slug with Connor: `/work-with-me/` vs `/services/`
4. Branch from `claude/services-rebuild` (already has: rebrand + legacy companion page as reference)
5. Strip homepage services section; extend Approach section with "You walk away with" subsection
6. Build new `/work-with-me/` page with the three service sections
7. Wire all the deep links, buttons, anchor navigation
8. Deploy to `whm-sandbox.connorcoded.com` for Talie's first look
9. Iterate per her feedback (expect 2-3 rounds based on this morning's pace)
10. When she blesses the flow end-to-end: the additive meta/schema pass
11. Deploy to `whm2-sandbox.netlify.app` as the final approval mirror
12. Deploy to live `withheart-marketing.com` using the temp-staging-dir pattern

**Rough estimates:** Initial build ~2-3 hours once copy lands. Iterations ~30 min each. Total to live: probably 1-2 working sessions after copy arrives, depending on her review pace.

---

## Open questions for next touchpoint

1. URL slug confirmation (`/work-with-me/` recommended)
2. Brand audit CTA: include or defer? (recommendation: include as soft button)
3. FAQ on services page: reuse homepage FAQs or draft new set? (default: reuse)
4. Homepage `#services` anchor disposition: repurpose to `#approach`, remove entirely, or leave in place for redirect purposes?

---

## Mempalace references

- Session log: `sessions/2026-04-21-whm-brand-marketing-reframe.md` (covers the full day including morning reframe, live deploy, and this afternoon's call)
- Client brief: `projects/withheart-marketing/client-brief.md` (standing orders, path traps, current state)
- CURRENT-STATE.md: WHM section updated with services-rebuild branch and open items
