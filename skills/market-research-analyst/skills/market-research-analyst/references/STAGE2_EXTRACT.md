# Stage 2 — Extract

## Purpose

Fetch each source, extract clean signal, and build a body of evidence Stage 3 turns into a verdict. This is where fabrication, vague paraphrase, and treating noise as signal do the most damage. Be rigorous here and the report writes itself.

---

## Fetch strategy

Work through sources sequentially — Claude cannot parallelise web requests in chat.

**Primary:** load the URL directly.
**Fallback (trigger immediately on failure):** these block direct fetches — Amazon.in, Flipkart, Blinkit, BigBasket, Myntra, Swiggy, sometimes Nykaa, and many gated report sites (Statista, Tracxn). Do not retry; switch to search the moment you hit a bot block, login wall, empty body, or generic error.

**Fallback query sequence** (stop when usable):
1. `"[brand] reviews site:[domain]"`
2. `"[brand] [category] review India 2025 OR 2026"`
3. `"[brand] complaints OR feedback OR honest review"`

For Reddit: `"[brand] site:reddit.com"`, then `"[brand] site:reddit.com/r/india"` or the relevant subreddit.

### Progress notation (one line in chat after each source)

**CRITICAL: Always include a clickable hyperlink to the source URL in every progress update.** Founders need to verify findings and explore sources themselves. Format: source name as markdown link, then the finding summary.

```
🔍 [Amazon.in (Yoga Bar)](https://amazon.in/s?k=yoga+bar) ✓ — 60+ reviews; sweetness complaint theme, chocolate flavour rated highest
🔍 [Reddit r/IndiaFitness](https://reddit.com/r/IndiaFitness/search?q=protein+bar) ✓ — 11 threads; savoury gap mentioned repeatedly
🔍 [Healthkart](https://www.google.com/search?q=yoga+bar+healthkart) ⚠ search fallback — ₹150/40g bar; peanut-butter top-rated flavour
🔍 [IBEF protein market report](https://www.ibef.org) + [news](https://www.google.com/search?q=protein+market+India+CAGR) ✓ — protein market ~₹33,000 Cr, ~14% CAGR (IMARC, 2024–2030)
🔍 [Inc42 (competitors)](https://inc42.com/buzz/search/?q=protein+bar+funding) ✓ — two rivals raised Series A in 2024
🔍 [IndiaMART co-packers](https://www.indiamart.com/impcat/protein-bar-manufacturer.html) ⚠ limited — co-packers exist, MOQ ~5,000 units quoted
🔍 [Ambassador search](https://www.google.com/search?q=protein+bar+brand+ambassador+India) ✓ — rivals use micro-creators, no celebrity faces yet
```

**Link priority:**
1. Direct page URL if fetched successfully
2. Search URL used for fallback (show the actual search that yielded results)
3. Domain homepage if specific page unavailable

Notation: `✓` direct/good · `⚠ search fallback` blocked but useful · `⚠ limited data` thin · `✗ no usable data` nothing found.

---

## Source-specific capture patterns

### Amazon.in, Flipkart, Healthkart, Nykaa, Myntra (review platforms)

**Priority order:** 1-2★ reviews (unmet needs, complaint themes — read carefully) → 4★ (honest praise-with-caveat, most information-dense) → 5★ (verbatim praise, repeat signals) → Q&A (purchase blockers + how the brand positions).

**Capture:**
- Complaint patterns in 3+ independent reviews → themes
- Praise patterns repeated → loyalty drivers
- Specific properties named: texture, taste, sweetness, packaging, melt, portion, price-per-unit
- **Variant/flavour signal** (see dedicated section below) — which flavour/SKU is praised or panned
- Switching to/from a named competitor
- Return/refund mentions — strong dissatisfaction
- The actual words customers use, not your summary
- **The source URL** — capture and store the exact URL for every finding so it can be linked in the report

**Thresholds:** 10+ reviews = representative; 5–10 = note the sample size; <5 = "limited data, directional only."
**Recency:** prioritise 2024–2026. A complaint resolved in recent reviews is a positive signal — note it.

### Flavour / variant / SKU capture (the "which flavour wins" track)

Review platforms tag reviews by variant. Mine that. Capture per brand:
- Which flavour/variant has the highest rating and the most reviews (the proven winner)
- Which flavour is consistently complained about (the one to avoid)
- Any flavour customers ask for that no brand offers (a format/flavour whitespace)
- Format winners too: which pack size or single-serve format repeat buyers prefer

Capture as: `Flavour/variant | rough rating or sentiment | n reviews | brand | source`. Never invent a rating — if the platform does not break it out, say "variant-level data not separable."

### Reddit

Look for: "best [category] in India" threads (decision criteria, trusted brands) · brand-specific complaint threads · two-brand comparison threads · "does anyone know a [X] that doesn't [Y]" (unmet needs as questions).
Quality: 10+ upvotes = resonated; 5+ comments = real engagement; last 18 months preferred (flag older).
**Capture verbatim** — Reddit is the closest thing to unedited customer voice. Quotes, not summaries.

### Brand websites

Hero/tagline (the bet), About (values, founder story), product pages (exact pack sizes, prices, variants, ingredients in copy), FAQ (pre-purchase questions), certifications.
Capture: the primary claim in their words, how they justify price, **what they avoid saying** (positioning gaps), exact pricing (₹X/Yg), variant names verbatim.
**Analytical move:** compare brand claim vs customer reality. The gap is often the most interesting finding.

### Blinkit, BigBasket, Swiggy (pricing & distribution — not reviews)

Capture: exact prices and pack sizes per competitor; whether the brand is listed at all (absence is a distribution finding); first-page prominence (traction); price-per-unit across pack sizes.
Format: `Product | Pack size | Price (₹) | Platform`. That is all.

### Market sizing (B1 — Market track)

Capture: the market-size figure, the CAGR, AND the forecast window and source for each — e.g. "India protein supplements ~₹33,000 Cr, 14% CAGR 2024–2030 (IMARC)". If two reports disagree, capture both and report a range. Note adjacent signals: quick-commerce growth, festive/seasonal spikes, urban-vs-rural split. **Never invent or round a CAGR you did not read.** A category with no findable sizing is a finding — it may be nascent or too small to have been sized.

### Funding & traction (B2 — Competition track)

Per major competitor capture: total/last raised, round stage, investors, year; any revenue/loss figures from filings; trajectory (growing fast, plateaued, shutting down). Interpret: well-funded = real threat + runway; lots of recent category funding = investor conviction but incoming competition; revenue with heavy losses = buying growth; no findable funding = early/bootstrapped/offline.

### Manufacturing (B3 — Make-vs-Buy track)

Capture 2–3 reference points, not an exhaustive survey: do reputable contract manufacturers / co-packers exist for this category; indicative MOQ; rough lead time; whether leading brands own plants or outsource. This frames the decision — it does not need to be precise. Flag everything as indicative.

### Brand ambassador / influencer (B4 — GTM track)

Capture: do competitors use ambassadors (celebrity vs micro-creator vs none); is there organic creator coverage already (cheaper to activate); category norms on influencer spend if a report surfaces it. This feeds the should-you recommendation.

### Google news & press

Funding announcements, founder interviews (strategy, target customer), negative press (recalls, regulatory, controversy), category coverage (size, growth, trends).

---

## The verbatim rule — the most important practice in this stage

Always capture customer language verbatim. Never paraphrase what a customer said.

Why: founders put this language in their ads (your paraphrase is useless, their words are gold); verbatim quotes are evidence, summaries are interpretation; the Ad-Language section is worthless if everything is paraphrased.

**Good:** `"finally a protein bar that doesn't taste like cardboard" — [Amazon.in, 4★, Yoga Bar](https://amazon.in/product-page)`
**Bad:** `Customers appreciate the taste.`

**CRITICAL: Capture the source URL with every quote.** Format as: `"verbatim quote" — [source name, rating, brand](URL)`. The URL should go directly to the page where the quote was found (product page, Reddit thread, article), not just the homepage.

Target 3–6 strong verbatim quotes per source. One strong, specific, surprising quote beats five generic ones.

**Capture a quote if** it uses unprompted specific product language, shows a purchase decision being made/reversed, carries real emotion, names a competitor, or appears across multiple independent sources (strongest signal).
**Skip it if** generic ("great product"), logistics-only ("fast delivery"), or contextless ("good").

---

## Themes vs one-offs

- **One-off:** single mention. Note internally, do not elevate.
- **Theme:** same complaint/praise in 3+ independent sources. Surface prominently with the count.
- **Strong theme:** same/similar language verbatim across independent sources — customers reaching for the same words unprompted. Highlight in Ad Language.

---

## Internal data organisation

As you extract, sort findings into these buckets (internal scaffolding for Stage 3 — do not show the user):

- **PRAISE** — what customers love (source + URL, ideally verbatim)
- **COMPLAINTS** — dislikes, gaps, frustrations (source + URL)
- **VERBATIM** — strong exact quotes (source + URL, polarity, theme tag)
- **PRICING** — exact price/size data (platform + URL, date)
- **FLAVOURS** — variant winners/losers (brand, source + URL)
- **MARKET** — size, CAGR, growth signals (source + URL + window)
- **FUNDING** — competitor raises and traction (source + URL)
- **MANUFACTURING** — MOQ, co-packer existence, make-vs-buy reference points (source + URL)
- **AMBASSADOR** — competitor ambassador use + organic creator coverage (source + URL)

**For EVERY item in EVERY bucket, capture the source URL.** Store it alongside the finding so it can be linked in the report. No floating assertions without a clickable source link.

Keeping this structure during extraction means Stage 3 goes straight to synthesis and the verdict.

---

## The honesty standard

**Analysis (allowed):** inferring a theme from 5 matching reviews; connecting a complaint to an opportunity; reading a brand's Blinkit absence as limited quick-commerce; saying "limited data — directional."

**Fabrication (never):** inventing a quote; asserting "customers say X" with no evidence; treating 1 review as representative; stating a CAGR, MOQ, or funding figure you did not verify; manufacturing a scorecard number with no basis.

**Grey area — disclose explicitly:** "Early signal from 3 reviews — not confirmed at scale. Recommend monitoring as volume grows."

---

## Recency weighting

2024–2026 full weight · 2022–2023 moderate (note if a complaint appears resolved) · 2021 and earlier flag if used. A complaint pattern that vanishes in recent reviews is a positive signal — note it.

---

## When a source returns nothing

If primary and all fallbacks fail: mark `✗ no usable data` in progress; note it explicitly in the report (never silently omit); interpret the absence — "No Blinkit listing for Brand X after fallback — likely D2C-only or not on quick-commerce. Either a distribution gap or a deliberate channel strategy." An unavailable source is data, not failure.
