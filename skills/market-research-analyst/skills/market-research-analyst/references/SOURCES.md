# Source Reference Map

Loaded in Stage 1. Use this to select 5–8 sources based on product category, market, and research mode.

---

## Food and FMCG — India

| Priority | Source | What to look for | URL pattern | Fallback query |
|---|---|---|---|---|
| High | Amazon.in reviews | Ratings, review text, Q&A, complaint patterns | `amazon.in/s?k=[product]` or product page | `"[brand] reviews site:amazon.in"` |
| High | Reddit | Unfiltered opinions, brand comparisons, recommendations | `reddit.com/search/?q=[brand]` | `"[brand] site:reddit.com india"` |
| High | Blinkit | Pricing, pack sizes, quick-commerce visibility | `blinkit.com/search?q=[product]` | `"[brand] blinkit price 2024 OR 2025"` |
| Medium | BigBasket | Pricing, alternatives shown alongside, reviews | `bigbasket.com/ps/?q=[product]` | `"[brand] bigbasket"` |
| Medium | Swiggy Instamart | Availability, pricing, listing depth | Search within swiggy.com | `"[brand] swiggy instamart"` |
| Medium | Brand website | Positioning copy, product range, pricing, certifications | Official URL | Google: `[brand] official site India` |
| Medium | Flipkart reviews | Review text, Q&A | `flipkart.com/search?q=[product]` | `"[brand] reviews site:flipkart.com"` |
| Lower | Google news | Press coverage, D2C funding mentions, founder interviews | Google search | `"[brand] India D2C 2024 OR 2025"` |

**Relevant Reddit communities:** r/india · r/desifoodporn · r/fitness · r/IndiaFitness · r/IndianFitness · r/IndiaInvestments (for D2C discussion)

**Common blockers:** Amazon.in, Blinkit, Flipkart, and BigBasket all frequently block direct fetches. Use search fallback immediately — do not retry the direct fetch.

---

## Health and Fitness (Supplements, Protein, Wellness) — India

| Priority | Source | What to look for | Fallback query |
|---|---|---|---|
| High | Amazon.in reviews | Star breakdown, review text, Q&A, ingredient complaints | `"[brand] protein reviews site:amazon.in"` |
| High | Reddit r/india + r/IndiaFitness | Community comparisons, complaints, trusted brands | `"[brand] site:reddit.com"` |
| High | Brand website | Ingredient list, certifications, pricing, origin claims | Google: `[brand] official site` |
| Medium | Healthkart | Product listing, pricing, alternatives shown, user reviews | `"[brand] healthkart"` |
| Medium | Flipkart | Reviews, pricing | `"[brand] flipkart reviews"` |
| Lower | YouTube | Influencer reviews — look for recurring complaints across multiple reviewers | `"[brand] review india youtube"` |

---

## Fashion and Apparel — India

| Priority | Source | What to look for | Fallback query |
|---|---|---|---|
| High | Myntra reviews | Ratings, review text, return reasons, sizing issues | `"[brand] reviews site:myntra.com"` |
| High | Amazon.in | Reviews, pricing, alternatives shown | `"[brand] site:amazon.in"` |
| High | Reddit r/india r/IndianFashion | Community discussions, sizing/quality debates | `"[brand] site:reddit.com"` |
| Medium | Ajio | Pricing, product range, reviews | `"[brand] site:ajio.com"` |
| Medium | Brand website | Positioning, price list, materials, sizing guide | Google: `[brand] official India` |
| Lower | Nykaa Fashion | If brand is listed there | `"[brand] nykaa fashion"` |

---

## Beauty and Personal Care — India

| Priority | Source | What to look for | Fallback query |
|---|---|---|---|
| High | Nykaa reviews | Ratings, review text, Q&A, before/after mentions | `"[brand] reviews site:nykaa.com"` |
| High | Amazon.in | Broad review pool, ingredient mentions | `"[brand] site:amazon.in"` |
| High | Reddit r/IndianSkincareAddicts | Community sentiment, ingredient deep dives, trusted/avoided brands | `"[brand] site:reddit.com"` |
| Medium | Purplle | Secondary platform reviews, pricing | `"[brand] purplle"` |
| Lower | YouTube | Influencer reviews, dermatologist breakdowns | `"[brand] review india skincare"` |

---

## SaaS and Tech Products

| Priority | Source | What to look for | Fallback query |
|---|---|---|---|
| High | G2 | Structured pros/cons, use case fit, implementation pain | `"[product] site:g2.com reviews"` |
| High | Reddit (category subreddits) | Community comparisons, alternatives discussed, complaints | `"[product] site:reddit.com"` |
| High | Product Hunt | Launch comments, early-adopter sentiment, feature requests | `"[product] site:producthunt.com"` |
| Medium | Capterra | SMB-focused reviews, pricing complaints | `"[product] site:capterra.com"` |
| Medium | Hacker News | Technical audience reactions, architecture critiques | `"[product] site:news.ycombinator.com"` |
| Lower | Trustpilot | General reviews, customer support sentiment | `"[product] site:trustpilot.com"` |

---

## Source selection by research mode

| Mode | Emphasis | What to deprioritise |
|---|---|---|
| Competitor Analysis | Review platforms, brand websites, pricing pages — you want concrete numbers and direct comparisons | Deep forum dives, long Reddit threads |
| PMF Analysis | Community sources (Reddit, forums), review text — you want authentic customer language and unmet need signals | Pricing pages, brand websites |
| Comprehensive | Balance across both — cap at 7-8 sources total to keep extraction manageable | Nothing entirely, but don't go past 8 |

---

## General fallback strategy

If a site blocks direct fetch (common for Amazon.in, Blinkit, Flipkart, Myntra, Swiggy):

1. Try a `site:` search: `"[brand] reviews site:amazon.in"`
2. If search returns nothing useful: `"[brand] [product category] review India 2024 OR 2025"`
3. As a last resort: `"[brand] India feedback OR complaints OR praise"`
4. If all three fail, mark the source as unavailable in the report — note it explicitly

The absence of data is itself a finding. A brand with near-zero reviews is a data point: they may be new, niche, or underperforming.
