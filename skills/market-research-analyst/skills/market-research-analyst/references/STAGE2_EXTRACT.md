# Stage 2 — Extract

## Purpose

Fetch each source in the plan, extract clean signal from it, and build up a body of data that Stage 3 can synthesise into insights. This stage is where bad habits — fabrication, vague paraphrasing, treating noise as signal — do the most damage. Be rigorous here and the report writes itself. Be sloppy here and no amount of good synthesis will save it.

---

## Fetch strategy

Work through sources sequentially, one at a time. Claude cannot parallelise web requests in a chat context.

### Two-level approach for every source

**Primary — direct page fetch:**
Use your web browsing capability to load the URL directly.

**Fallback — web search (trigger immediately on failure):**
These platforms actively block direct fetches and will rarely return useful content: Amazon.in, Flipkart, Blinkit, BigBasket, Myntra, Swiggy Instamart, Nykaa (sometimes).

Do not retry the direct fetch. Switch to the fallback immediately when a page returns a bot-detection block, login wall, empty body, or generic error.

### Fallback query sequence

Try these queries in order, stopping when you get usable data:

1. `"[brand name] reviews site:[blocked domain]"` — returns indexed review snippets directly
2. `"[brand name] [product category] review India 2024 OR 2025"` — broader query, more snippets
3. `"[brand name] complaints OR feedback OR honest review"` — surfaces emotional language faster

**For Reddit specifically:**
If `reddit.com/search` returns nothing, try:
- `"[brand name] site:reddit.com"`
- `"[brand name] site:reddit.com/r/india"` or the relevant subreddit

### Progress notation after each source

Post a one-line status in chat after completing each source. Make it informative — the founder is watching the research happen in real time.

```
🔍 Amazon.in (Darkins) ✓ — 52 reviews, strong complaint theme around sweetness
🔍 Reddit r/india ✓ — 9 threads, several direct brand comparisons
🔍 Blinkit ⚠ search fallback — pricing: ₹299/100g, ₹499/200g
🔍 Darkins website ✓ — positions as "India's first bean-to-bar", ₹280–₹450 range
🔍 Google news ✓ — ₹2Cr seed funding 2023, mostly D2C sales
```

Notation guide:
- `✓` — direct fetch succeeded, good data
- `⚠ search fallback` — blocked, fallback used, data still useful
- `⚠ limited data` — fallback used but thin results
- `✗ no usable data` — nothing found after all attempts

---

## Source-specific capture patterns

Different sources yield different types of signal. Here is what to extract from each.

### Amazon.in and Flipkart (review platforms)

**Priority order within reviews:**
1. **1-star and 2-star reviews** — this is where unmet needs and complaint themes live. Read them carefully. They are the most direct window into what the product fails to deliver.
2. **4-star reviews** — often the most honest: praise with a specific caveat. More information-dense than 5-star reviews.
3. **5-star reviews** — useful for verbatim praise language and repeat-purchase signals.
4. **Q&A section** — questions reveal purchase blockers (what stops someone from buying); brand answers reveal how the company positions itself.

**What to capture:**
- Complaint patterns that appear in 3 or more reviews independently — these are themes
- Praise patterns that appear repeatedly — these are loyalty drivers
- Specific product properties customers name: texture, taste, sweetness, packaging, melt resistance, portion size, price-per-unit
- Whether reviews mention switching to or from a competitor by name
- Return or refund mentions — strong dissatisfaction signal
- The actual language customers use, not your summary of it

**Quality threshold:**
10+ reviews to treat as representative. Fewer than 5 → flag as "limited data, directional only." Between 5 and 10 → note the sample size.

**Recency:**
Prioritise reviews from 2023–2025. Products change, formulas evolve, brands improve. A 2021 complaint about packaging may have been addressed. Note review dates on significant findings, especially complaints.

---

### Reddit

**What to look for and where:**
- Threads asking "best [product category] in India" → reveals decision criteria and trusted brands
- Threads complaining about a specific brand → unfiltered, often highly specific
- Comment threads comparing two brands directly → direct competitive intelligence
- "Does anyone know a [X] that doesn't [Y]?" → unmet needs phrased as questions

**How to evaluate thread quality:**
- Upvotes on the thread: 10+ means the question resonated broadly
- Comment depth: 5+ comments means enough people engaged to yield signal
- Post age: prioritise threads from the last 18 months; flag older threads when surfacing them

**What communities to search:**
Choose based on product category. For food/FMCG India: r/india, r/desifoodporn, r/fitness, r/IndiaFitness, r/IndianFitness. For skincare: r/IndianSkincareAddicts. For SaaS: the relevant product subreddits. Check SOURCES.md for category-specific communities.

**Verbatim priority:**
Reddit comments are the closest thing to unedited customer voice you will find in writing. Capture actual quotes, not summaries. A Reddit comment is far more copy-ready than a manufactured paraphrase.

---

### Brand websites

**Where to look:**

- **Hero section and tagline** — the primary positioning claim. What is the brand betting on?
- **About page** — founder story, brand values, what they signal they believe in
- **Product listing pages** — exact pack sizes, prices, product names, ingredients highlighted in the copy
- **FAQ section** — the questions customers ask before buying; the answers reveal brand positioning choices
- **Certifications and awards section** — signals what the brand believes matters to its customers (organic, vegan, FSSAI, international awards)

**What to capture:**
- The primary claim in their own words (health? taste? ethics? heritage? value?)
- How they justify their price point
- What they do not say — positioning gaps are visible in what a brand avoids mentioning
- Exact pricing (₹X for Yg), product names verbatim, key copy phrases verbatim

**A useful analytical move:** Compare what the brand says on their website with what customers say in reviews. The gap between brand claim and customer experience is often the most interesting finding.

---

### Blinkit, BigBasket, Swiggy Instamart

**What these platforms are for:** Pricing and distribution data — not review content. Most of these platforms have few or no meaningful product reviews. Do not spend time looking for review content here.

**What to capture:**
- Exact prices and pack sizes for each competitor
- Whether the brand is listed at all (absence is a distribution finding)
- Whether the brand appears on the first page of a category search (prominence = traction)
- Price-per-gram or price-per-unit if multiple pack sizes are available

**Capture format:** Product name | Pack size | Price (₹) | Platform. That is all you need.

---

### Google news and press

**What to capture:**
- Funding announcements (brand is growing, has runway — or has not raised, which is also signal)
- Founder interviews (reveals strategy, target customer, long-term vision)
- Negative press — product recalls, regulatory issues, public controversy
- Analyst or media coverage of the category (size estimates, growth rates, emerging trends)

**Interpretation:**
- Funded brand = has runway, likely investing in growth → stronger competitive threat
- No press coverage at all = early stage, offline-heavy, or struggling → may be less relevant to benchmark
- Category-level coverage helps the Overview tab in Stage 3

---

## What to capture and how

### The verbatim rule — the single most important practice in this stage

Always capture customer language verbatim. Never paraphrase what a customer said.

**Why this matters:**

1. Founders use this language in their own ads. Your paraphrase is useless to them; the customer's exact words are valuable.
2. Verbatim quotes are evidence. A summary is just your interpretation of evidence.
3. The "Ad Language" dimension of the report is entirely worthless if everything is paraphrased.

**Good verbatim capture:**
> "finally a chocolate that doesn't melt in 10 minutes" — Amazon.in, 4-star review, Darkins

**Bad paraphrase:**
> Customers appreciate the product's heat resistance.

These look similar. They are not. The first is a copy line. The second is a characterisation that tells the founder nothing they can act on.

**Target: 3–6 strong verbatim quotes per source.** Do not capture 20 mediocre quotes. One strong, specific, surprising quote beats five generic ones.

### What makes a verbatim quote worth capturing

**Capture it if:**
- It uses specific product language customers reach for unprompted (not marketing copy echoed back)
- It shows a purchase decision being made or reversed ("stopped buying X because...", "finally switched to Y")
- It contains real emotion — relief, frustration, delight, disappointment
- It compares the brand to a competitor by name
- It appears across multiple independent sources (same phrase = very strong signal)

**Skip it if:**
- It is generic praise: "great product, highly recommended" — zero information content
- It is about logistics, not the product: "delivered fast", "good packaging" — not useful for PMF
- It is very short with no context: "good" — not actionable

---

## Identifying themes versus one-offs

**One-off:** A complaint or praise appears in a single review or comment. Note it internally but do not elevate it as a theme in the report.

**Theme:** The same complaint or praise appears in 3 or more independent sources. This is a signal worth surfacing prominently. Mention it in the report with the number of occurrences.

**Strong theme:** The same or similar language appears verbatim across multiple independent sources. Customers are reaching for the same words independently to describe the same experience. This is a finding. Highlight it in the Ad Language section.

---

## Data quality thresholds

| Source type | Minimum for "representative" | Flag at |
|---|---|---|
| Product reviews (Amazon, Myntra, Nykaa) | 10+ reviews | Under 5: "limited data" |
| Reddit threads | 3+ relevant threads with 5+ comments each | Under 3: "limited data" |
| Brand website | Any accessible page | N/A — always some data |
| Price listings | Any accessible listing | N/A |
| News articles | 1 is enough to note | Note the date |

---

## Recency weighting

When you find reviews from multiple years, apply this weighting:
- 2024–2025: full weight
- 2022–2023: moderate weight — note if a significant complaint appears resolved in recent reviews
- 2021 and earlier: flag if using — products and brands change significantly over 3+ years

A complaint pattern that existed in 2022 but disappears entirely in 2024–2025 reviews is a positive signal for the brand — it suggests they addressed it. Note this in the report.

---

## Internal data organisation

As you extract, mentally organise findings into these four buckets. You do not need to show the user this structure — it is internal scaffolding for Stage 3.

- **PRAISE** — what customers consistently love (with source, ideally verbatim)
- **COMPLAINTS** — what they dislike, what is missing, what frustrates them (with source)
- **VERBATIM** — strong exact quotes worth surfacing (with source, polarity, theme tag)
- **PRICING** — exact price/size data (with platform and date if available)

Keeping this structure in mind during extraction means Stage 3 does not have to untangle a disorganised pile of notes. It can go straight to synthesis.

---

## The honesty standard

This distinction matters. It prevents the report from presenting fabrication as research.

**Analysis (allowed):**
- Inferring a theme because the same complaint appears in 5 independent reviews
- Drawing a connection between a complaint and a market opportunity
- Noting that a brand's absence from Blinkit suggests limited quick-commerce presence
- Saying "limited data from this source — treat as directional"

These are conclusions drawn from real evidence. They are legitimate analysis.

**Fabrication (never):**
- Inventing a specific customer quote
- Asserting "customers say X" when you found no evidence of X
- Treating 1 review as representative of broad sentiment
- Extrapolating a pricing figure you did not verify from a source

**Grey area — handle with explicit disclosure:**
If you found only 3 reviews and they all say the same thing, surface the finding but flag it:
> "Early signal from 3 reviews — not confirmed at scale. Recommend monitoring as review count grows."

That is honest, specific, and still useful to the founder.

---

## When a source returns nothing

If both the primary fetch and all fallback queries fail:

1. Mark it `✗ no usable data` in the progress update
2. In Stage 3, note it explicitly in the report — do not silently omit the source
3. If possible, interpret the absence: "No Blinkit listing found for Paul & Mike — they may be D2C-only or not yet on quick-commerce platforms."

An unavailable source is not a failure of the research. It is data. A brand with no findable reviews may be very new, very niche, or operating primarily offline. The report should note what that might mean for the competitive picture.
