# Stage 1 — Plan

## Purpose

Select the right sources, present a specific plan, and confirm before extracting. A good plan names exactly what you will look for at each source and why — not just which URLs. For Full Launch Assessment it also covers the strategic tracks (market size, funding, flavours, GTM, ambassador, make-vs-buy) so the founder sees the verdict is actually being built, not just review-mining dressed up.

---

## Step 1: Parse the [RESEARCH_REQUEST]

Read every field:

- `mode` — drives source mix and how many to include
- `product` — infers category → which SOURCES.md section applies
- `market` — geography-specific platform selection
- `competitors` — named brands go on the list; "none named" triggers discovery
- `focus` — focus areas tilt source weighting
- `stage` — founder's stage; shapes how the verdict is framed (idea = more validation caveats; launched = benchmark against their own traction)
- `price_point` — their intended price; anchors the pricing-gap analysis
- `decision` — their core question; the verdict must answer THIS specifically
- `manufacturing` — own / contract / undecided; decides how hard to dig on the make-vs-buy track
- `tracks` — which Part-B strategic sources to include (Full Launch Assessment only)

If `mode` is Competitor Analysis or Product-Market Fit, ignore the strategic fields (they carry defaults) and plan the lighter run.

---

## Step 2: Infer the product category

Decision tree (picks the SOURCES.md Part-A section):

**Food or drink?**
→ Health/wellness-first (protein, supplement, low-cal, diabetic, functional)? → **Health and Fitness**
→ Else → **Food and FMCG**

**Clothing, footwear, accessories?** → **Fashion and Apparel**
**Skincare, haircare, cosmetics, oral care, deodorant?** → **Beauty and Personal Care**
**Software, app, digital tool?** → **SaaS and Tech**

### Crossover and unclear cases
- **Health × Food** (protein chocolate, functional drink): use the primary purchase driver. Protein chocolate is bought for health first → Health, supplemented by Food review platforms.
- **Beauty × Wellness** (skin-improving supplement): Beauty if the claim is about appearance, Health if about physiology.
- **Still unclear**: default to Food/FMCG for India physical products, SaaS for digital. Use the "category not listed" quartet from SOURCES.md if it is a genuinely novel category (home, pet, baby, gadgets). Note the assumption in the plan so the founder can correct it.

---

## Step 3: Handle "none named" competitors

If competitors is "none named", add discovery as item 1:

```
1. Google / Amazon.in / [primary platform] — search "[category] brands India" to surface the main competitors before diving into reviews
```

Note it: "I'll surface competitors first, then research each one." This yields 3–5 names for extraction.

If fewer than 3 named, consider a discovery step alongside them to round out the field.

---

## Step 4: Select Part-A customer-voice sources

### Count targets
| Mode | Part-A target | Emphasis |
|---|---|---|
| Competitor Analysis | 6–8 | Review platforms + brand sites + pricing |
| PMF Analysis | 5–6 | Community + review text |
| Full Launch Assessment | 5–6 Part-A (+ Part-B below) | Balanced: ≥1 community, ≥1 pricing, ≥1 brand site |

Quality beats volume. For every named competitor always include their brand website, their top category review platform, and at least one Reddit search. For every plan always include at least one Reddit source and the highest-priority source for the category.

### Focus-area tilts
| Focus selected | Add / prioritise |
|---|---|
| Pricing & pack sizes | Blinkit, BigBasket, Swiggy |
| Customer complaints | Weight review platforms over brand sites |
| Ad language & copy | Maximise review-text sources (Amazon, Reddit, Nykaa) |
| Repeat-purchase triggers | Reddit + longer-form review platforms |
| Market gaps | Weight Reddit / community heavily |
| Distribution channels | Add all quick-commerce platforms |

### Geography
- **India**: India platforms as listed. Avoid global (G2, Trustpilot) unless a competitor is international.
- **SEA**: replace India platforms with Shopee, Lazada, Tokopedia + country subreddits; keep brand sites.
- **Global**: G2, Capterra, Trustpilot, Product Hunt + Reddit; brand sites always relevant.

---

## Step 5: Add Part-B strategic sources (Full Launch Assessment only)

For each selected track in `tracks`, add the matching Part-B source(s) from SOURCES.md. If `tracks` is "all", include one source from each:

| Track selected | Add from SOURCES.md Part B |
|---|---|
| Market size & growth (CAGR) | B1 — one market-sizing source (IBEF or Mordor/IMARC) + a recent news search |
| Funding & competitor traction | B2 — one funding source (Inc42 / YourStory / Entrackr) per major competitor |
| Flavours / variants that win | No new source — flag the named review platforms (Amazon.in, Healthkart) to capture variant-level data during extraction |
| Go-to-market plan | Reuses pricing + distribution sources already selected; no new source unless ambassador track is also on |
| Brand-ambassador call | B4 — one ambassador/influencer search |
| Make vs buy (manufacturing) | B3 — one contract-manufacturer / MOQ search |

Keep the total at ~9 sources. If a track adds a source that pushes past the cap, drop a lower-priority Part-A source first (never drop the last community source, the primary review platform, or a named competitor's brand site).

If `manufacturing` is "own" or "contract" (not undecided), the make-vs-buy track matters more — keep its source even under pressure.

---

## Step 6: Present the plan

Numbered list in chat. Be specific at every line — name what you are looking for. Group Part-A (customer & competition) and Part-B (strategic) so the founder sees both halves.

**IMPORTANT: While presenting the plan, you don't need to include URLs yet (they'll be captured during extraction), but note that every finding will be linked to its source in the final report and progress updates.**

### Example — Full Launch Assessment, savoury protein snack

```
Here's my research plan. Two halves: what customers and competitors tell us, then the strategic picture that drives the verdict.

CUSTOMERS & COMPETITION
1. Amazon.in — top protein-snack brands' reviews (praise, complaints, the exact phrases people use, flavour-level ratings)
2. Reddit r/IndiaFitness, r/india — unfiltered sentiment, brand comparisons, "what should I buy" threads
3. Healthkart — pricing, pack sizes, and which flavours rate highest across brands
4. Two leading competitors' websites — positioning, range, price justification

STRATEGIC PICTURE
5. IBEF + recent news — India protein/snacking market size and growth rate
6. Inc42 / YourStory — funding and traction of the main competitors
7. IndiaMART — contract manufacturers and indicative MOQ for protein bars/snacks
8. Ambassador search — whether rivals use creators or celebrities, and organic creator coverage

This builds toward a clear GO / NO-GO on a savoury protein snack under ₹100, with how-to-win and 90-day moves. Every finding will be linked to its source so you can verify and explore. Say "go" to start, or tell me what to add or change.
```

### Bad plans avoid
Vague sources ("search the internet"), too many (10+), wrong-category sources (G2 for chocolate), no community source, no statement of intent, and — for Full Launch Assessment — skipping the strategic half so there is no basis for a verdict.

---

## Step 7: Handle modifications

- **Adds a source** → check viability (likely blocked? off-category?); if fine, add and re-show.
- **Removes a source** → note the gap it creates ("removing Reddit loses community sentiment — fine if you only want pricing"), then re-show.
- **Changes mode** → rebuild source selection from scratch under the new mode; re-confirm.
- **Changes a track** → add/drop the matching Part-B source; re-show the updated plan.
- **"Just go" / "start now"** → proceed immediately with the current plan.

---

## Step 8: Confirmation

Wait for explicit confirmation: "go", "yes", "start", "looks good", "proceed", a thumbs up, any clear affirmative.

- **Question instead of confirmation** → answer it, then "Ready to start?"
- **Two exchanges without confirmation** → proceed and note: "I'll proceed with this plan — tell me if you want to adjust anything mid-research."

Do not reopen the intake form from here. If the founder wants to change product or mode fundamentally, rebuild the plan for the new context.
