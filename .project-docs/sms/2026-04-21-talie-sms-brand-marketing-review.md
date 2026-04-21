# SMS Thread — Talie Knutson, 2026-04-21 — Brand Marketing Review

**Source:** iMessage thread, Connor ↔ Talie K.
**Captured:** 2026-04-21 morning, live during the reframe session
**Context:** Talie is reviewing whm2-sandbox.netlify.app (the approved-only review site) and sending iterative feedback via text. This thread drove 4 rounds of edits, all deployed same-day.

---

## 1. The Full Umbrella Pivot

Talie's opening text that reversed her earlier "additive only" rule and authorized a full site-wide swap:

> **Talie:** I want to change it all to heart-centered brand marketing.
>
> That is truly what I do. And brand strategy is only a part of it. Honestly, it's always what I have done. I think I just got sidetracked by wanting to only focus on Brand strategy specifically but given my meetings last week, I need to expand this umbrella.

**Implication:** Her prior guidance ("don't remove anything, just add brand marketing alongside brand strategy") was revised. She's now authorizing removing "brand strategy" from visible positioning (title tag, meta, OG, section headers, body copy) and keeping it only where it still serves factually (FAQ questions, product names, her biography, keywords).

---

## 2. The Share Preview Fix

Talie circled the share-card title in a screenshot and clarified:

> **Talie:** [screenshot of whm2-sandbox share preview showing "Heart-Centered Brand Strategy"]
>
> That should say With Heart Marketing (line) Heart-Centered Brand Marketing

> **Talie:** Sorry. That's the one that I made the four changes on. If it's good I'll make it live. Double triple and quad.

**Translated to spec:** og:title, twitter:title, and meta description should all lead with "Heart-Centered Brand Marketing." Applied.

### On the OG share image specifically

Connor asked whether the `/og-image.png` file itself needed to be redesigned (concern: if the image had "Brand Strategy" printed on it, swapping text tags alone wouldn't change what viewers saw).

> **Talie:** The image share is just my with heart marketing logo. It doesn't have any mention of strategy. It's the text below when you share the link that I was referring too.

**Outcome:** No image regeneration needed. Text tags alone fixed the share card.

---

## 3. Holds + Releases Round

Connor surfaced three judgment-call asks. Talie answered them 1-2-3:

> **Talie:**
> 1. Don't make any changes to the services yet. That's what we will talk about tomorrow.
> 2. Leave the faqs as they are. Brand strategy is still important. We can add in one about brand marketing. Like what is brand marketing? And how is brand marketing different than regular marketing?
> 3. The image share is just my with heart marketing logo. It doesn't have any mention of strategy. It's the text below when you share the link that I was referring too.

**Translated to spec:**
- Services section copy frozen until the services call
- Existing FAQ items untouched (brand strategy kept as historical frame)
- ADD two new FAQ items: "What is brand marketing?" and "How is brand marketing different than regular marketing?"
- No OG image work needed

---

## 4. Round 1 Review — The "Looks Good" + Cleanup Round

After Connor deployed the full swap + Email 2's mission rewrite + Why This Work Matters rewrite + two new FAQs, Talie reviewed and sent three cleanup texts with screenshots:

> **Talie:** Looks good! I noticed a few other places where I think we can change to say brand marketing. And then the disconnect of the offers. But that will come next.

> **Talie:** [screenshot of FAQ section on mobile]
>
> Let's update to questions about brand marketing. And everything else in the faq stays the same. Maybe just move the 2 new ones that focus on brand marketing to the top.

> **Talie:** Oh and it should say... "heart-centered brand marketing approaches branding differently…"

> **Talie:** [screenshot of Right-For-You closing callout]
>
> At the very bottom... update to.. "if you are ready to build your brand marketing from…"

> **Talie:** [screenshot of footer]
>
> And in the footer under the logo change to... heart centered brand marketing rooted in...

> **Talie:** [screenshot of services section]
>
> For now I'm wondering while we build out the rest, if we change this to say "Two Ways to Get Started with Finding Clarity." Then it positions the offers as this is how you get started. And the rest we talk about.

**Translated to spec:**
- FAQ H2: "Questions About Brand Strategy" → "Questions About Brand Marketing"
- FAQ intro: "Heart-centered brand strategy approaches branding..." → "Heart-centered brand marketing approaches branding..."
- Reorder: move the two brand marketing FAQs to the TOP of both the visible list and the JSON-LD schema
- Right-For-You closing callout: "build your brand strategy" → "build your brand marketing"
- Footer tagline: "Heart-centered brand strategy rooted in clarity" → "Heart-centered brand marketing rooted in clarity"
- Services H2 (her ONE approved services change): "Two Ways to Build Your Brand Strategy with Heart" → "Two Ways to Get Started with Finding Clarity"

All deployed.

---

## 5. Round 2 Review — The "Drop Branding" Cleanup

Talie caught that her previous FAQ intro rewrite still contained the word "branding" which she doesn't like:

> **Talie:** [screenshot of updated FAQ intro]
>
> Oops I forgot this. Change this to brand marketing and. Let's update the first part. I don't like the use of branding.
>
> Heart-centered brand marketing is different than traditional marketing. These answers clarify what it is, …" And the rest is the same.

> **Talie:** For the first q&a can we change that to say "what is brand marketing and heart-centered brand marketing" covering both.

**Translated to spec:**
- FAQ intro: drop the word "branding" entirely. "Heart-centered brand marketing is different than traditional marketing. These answers clarify what it is, how The With Heart Approach™ works, and what businesses can expect from this process."
- First FAQ title (visible + schema): "What is brand marketing?" → "What is brand marketing and heart-centered brand marketing?"

Deployed.

---

## 6. Round 3 — Partner Model FAQ Rewrite

Her biggest positioning move of the morning. She asked Connor to rewrite the "Do you help with marketing tactics or execution?" FAQ because the existing answer said she doesn't do execution — which no longer matches the brand marketing umbrella:

> **Talie:** The question about do you help with marketing tactics and execution. Can you help rewrite that for me so it covers that while I don't do it I have trusted partners that do and I can oversee it from a strategic lenses. Or something like that.

> **Talie:** And all the other updates look good.

**Translated to spec:** Rewrote the FAQ answer in her voice to position her as strategic lead overseeing a curated group of trusted execution partners. Key lines: "I do not do the day-to-day execution myself, but I stay close to it. I oversee the work through a strategic lens..." Applied to both visible HTML and JSON-LD schema.

**Why this matters strategically:** This is the first public-facing copy anywhere on her site that establishes the partner model. It sets up the services conversation scheduled for later today — when the services section rebuild will need to stay consistent with this language (partners, not employees; led by Talie; strategic oversight).

---

## 7. What's Still in Her Court

From her own texts:
- "the disconnect of the offers. But that will come next." — the services section cards + product names (Brand Strategy Workbook, Done-For-You Brand Strategy) are knowingly inconsistent with the new positioning. She flagged it; it's deliberate; services talk handles it.
- "Double triple and quad" — she's standing by, ready to push to live the moment the remaining services/offers piece lands.

---

## 8. What Deployed, In Order

All pushed to `connorwithhonor/whm2-sandbox` main, auto-deployed to whm2-sandbox.netlify.app:

1. **6156e1b** — Full brand marketing reframe: meta, OG, mission, Why This Work Matters, 2 new FAQs
2. **b7ce037** — Round 1 cleanup: FAQ heading/intro/reorder, services H2, callout, footer
3. **7b0bc92** — Round 2 cleanup: FAQ intro "drop branding", first FAQ covers both
4. **b77a870** — Round 3: tactics/execution FAQ rewrite (partner model)

Live site is untouched. Talie hasn't said "push it" yet.
