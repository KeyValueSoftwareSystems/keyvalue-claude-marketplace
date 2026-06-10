# Source Reference Map

Loaded in Stage 1. Two parts:
- **Part A — Customer-voice & pricing sources**, organised by product category. Pick 4–7 of these.
- **Part B — Strategic sources** (market sizing, funding, manufacturing, ambassador). Add these only for **Full Launch Assessment** mode, or when the founder selects the matching focus tracks.

Quality beats volume. Five strong sources beat ten thin ones. Cap a Full Launch Assessment at ~9 sources total so extraction stays deep.

---

# PART A — Customer-voice & pricing sources (by category)

## Food and FMCG — India

| Priority | Source | What to look for | URL pattern | Fallback query |
|---|---|---|---|---|
| High | Amazon.in reviews | Ratings, review text, Q&A, complaint patterns, variant-level reviews | `amazon.in/s?k=[product]` or product page | `"[brand] reviews site:amazon.in"` |
| High | Reddit | Unfiltered opinion, brand comparisons, recommendations | `reddit.com/search/?q=[brand]` | `"[brand] site:reddit.com india"` |
| High | Blinkit | Pricing, pack sizes, quick-commerce visibility | `blinkit.com/search?q=[product]` | `"[brand] blinkit price 2025 OR 2026"` |
| Medium | BigBasket | Pricing, alternatives shown alongside, reviews | `bigbasket.com/ps/?q=[product]` | `"[brand] bigbasket"` |
| Medium | Swiggy Instamart | Availability, pricing, listing depth | Search within swiggy.com | `"[brand] swiggy instamart"` |
| Medium | Brand website | Positioning, range, pricing, variants, certifications | Official URL | `[brand] official site India` |
| Medium | Flipkart reviews | Review text, Q&A | `flipkart.com/search?q=[product]` | `"[brand] reviews site:flipkart.com"` |
| Lower | Google news | Press, D2C funding mentions, founder interviews | Google search | `"[brand] India D2C 2025 OR 2026"` |

**Reddit communities:** r/india · r/desifoodporn · r/fitness · r/IndiaFitness · r/IndianFitness · r/IndiaInvestments (D2C chatter)

## Health and Fitness (Supplements, Protein, Wellness) — India

| Priority | Source | What to look for | Fallback query |
|---|---|---|---|
| High | Amazon.in reviews | Star breakdown, review text, Q&A, ingredient complaints, flavour-level reviews | `"[brand] protein reviews site:amazon.in"` |
| High | Reddit r/india + r/IndiaFitness | Community comparisons, complaints, trusted brands | `"[brand] site:reddit.com"` |
| High | Brand website | Ingredient list, certifications, pricing, flavours, origin claims | `[brand] official site` |
| Medium | Healthkart | Listing, pricing, alternatives, user reviews, flavour ratings | `"[brand] healthkart"` |
| Medium | Flipkart | Reviews, pricing | `"[brand] flipkart reviews"` |
| Lower | YouTube | Influencer reviews — recurring complaints across reviewers | `"[brand] review india youtube"` |

## Fashion and Apparel — India

| Priority | Source | What to look for | Fallback query |
|---|---|---|---|
| High | Myntra reviews | Ratings, review text, return reasons, sizing issues | `"[brand] reviews site:myntra.com"` |
| High | Amazon.in | Reviews, pricing, alternatives | `"[brand] site:amazon.in"` |
| High | Reddit r/india r/IndianFashion | Sizing/quality debates, community sentiment | `"[brand] site:reddit.com"` |
| Medium | Ajio | Pricing, range, reviews | `"[brand] site:ajio.com"` |
| Medium | Brand website | Positioning, price list, materials, sizing guide | `[brand] official India` |
| Lower | Nykaa Fashion | If listed there | `"[brand] nykaa fashion"` |

## Beauty and Personal Care (incl. oral care, toothpaste, deodorant) — India

| Priority | Source | What to look for | Fallback query |
|---|---|---|---|
| High | Nykaa reviews | Ratings, review text, Q&A, before/after mentions | `"[brand] reviews site:nykaa.com"` |
| High | Amazon.in | Broad review pool, ingredient mentions, variant reviews | `"[brand] site:amazon.in"` |
| High | Reddit r/IndianSkincareAddicts r/india | Ingredient deep-dives, trusted/avoided brands | `"[brand] site:reddit.com"` |
| Medium | Purplle | Secondary platform reviews, pricing | `"[brand] purplle"` |
| Medium | Brand website | Claims, range, pricing, certifications (e.g. SLS-free, fluoride) | `[brand] official India` |
| Lower | YouTube | Influencer / dermatologist breakdowns | `"[brand] review india"` |

## SaaS and Tech Products

| Priority | Source | What to look for | Fallback query |
|---|---|---|---|
| High | G2 | Structured pros/cons, use-case fit, implementation pain | `"[product] site:g2.com reviews"` |
| High | Reddit (category subreddits) | Comparisons, alternatives, complaints | `"[product] site:reddit.com"` |
| High | Product Hunt | Launch comments, early-adopter sentiment, feature requests | `"[product] site:producthunt.com"` |
| Medium | Capterra | SMB reviews, pricing complaints | `"[product] site:capterra.com"` |
| Medium | Hacker News | Technical reactions, architecture critiques | `"[product] site:news.ycombinator.com"` |
| Lower | Trustpilot | General reviews, support sentiment | `"[product] site:trustpilot.com"` |

**Category not listed (e.g. home, kitchen, pet, baby, gadgets):** use Amazon.in + Flipkart + Reddit + the brand website as the default customer-voice quartet, and the most relevant quick-commerce/marketplace for pricing. Note the improvisation in the plan.

---

# PART B — Strategic sources (Full Launch Assessment, or when the matching track is selected)

These answer the questions reviews cannot: how big is the market, is it growing, are competitors funded, and can I actually make this. Pick the ones the founder's selected tracks call for — do not add all of them by default.

## B1 · Market size & category health (Market track)

| Source | What to look for | Fallback query |
|---|---|---|
| IBEF (ibef.org) | India sector size, growth, government data | `"[category] market India IBEF"` |
| Mordor Intelligence / IMARC / Grand View | Market size estimate, CAGR, forecast horizon | `"[category] market size India CAGR"` |
| Statista | Revenue, volume, per-capita figures (often gated — use snippet) | `"[category] India statista market size"` |
| RedSeer / Bain / BCG / Kearney reports | D2C and consumer-trend reports, quick-commerce share | `"[category] India RedSeer OR Bain report 2025 OR 2026"` |
| News (ET, Mint, Business Standard) | Recent category growth claims, festive/seasonal data | `"[category] India market growth 2025 OR 2026"` |

**How to use CAGR honestly:** different reports give wildly different numbers. Capture the figure, the source, AND the forecast window (e.g. "14% CAGR 2024–2030, IMARC"). If estimates conflict, report the range, not a single number. Never invent a CAGR.

## B2 · Funding, traction & competitive intelligence (Competition track)

| Source | What to look for | Fallback query |
|---|---|---|
| Inc42 | Funding rounds, D2C trackers, founder interviews | `"[brand] funding Inc42"` |
| YourStory | Funding, founder story, milestones | `"[brand] YourStory funding"` |
| Entrackr / The Arc | Funding amounts, financials, revenue/loss filings | `"[brand] funding Entrackr"` or `"[brand] revenue FY"` |
| Tracxn / Crunchbase | Total raised, investors, stage (often snippet-only) | `"[brand] tracxn funding"` |
| Economic Times Startups / Moneycontrol | Larger rounds, MCA-filed financials | `"[brand] funding round 2025 OR 2026"` |

**Interpretation:** A well-funded competitor has runway and is a real threat → raises the bar. A category with lots of recent funding signals investor conviction (tailwind) but also incoming competition. A brand with revenue filings but heavy losses is buying growth — note it. No findable funding = early/bootstrapped/offline; that is a data point about how contestable the space is.

## B3 · Manufacturing — own plant vs contract (Make-vs-Buy track)

| Source | What to look for | Fallback query |
|---|---|---|
| IndiaMART / TradeIndia | Contract manufacturers / co-packers for the category, indicative MOQs | `"[product] contract manufacturer India IndiaMART"` |
| Category co-packer / private-label listings | Who already white-labels this; typical MOQ and lead time | `"[product] private label manufacturer India MOQ"` |
| Industry / news articles | Whether leading brands own plants or outsource | `"[category] brands own manufacturing OR contract India"` |
| Reddit / founder forums | First-hand MOQ, cost, and co-packer experiences | `"[product] manufacturing MOQ site:reddit.com"` |

**What to capture:** typical minimum order quantity (MOQ), rough per-unit cost direction, lead time, and whether reputable co-packers exist for this category. This feeds the make-vs-buy recommendation — it does NOT need to be exhaustive. Two or three reference points are enough to frame the decision honestly.

## B4 · Brand-ambassador & influencer landscape (GTM track)

| Source | What to look for | Fallback query |
|---|---|---|
| News / brand press | Whether competitors use celebrity or creator ambassadors, and who | `"[category] brand ambassador India"` |
| Influencer-marketing reports (e.g. EY, Kofluence) | Category norms, typical spend, ROI signals | `"India influencer marketing [category] 2025 OR 2026"` |
| Instagram / YouTube (via search) | Which creators already talk about the category organically | `"[category] india creator OR influencer review"` |

**What to capture:** do competitors lean on ambassadors? celebrity or micro-creator? is there organic creator coverage already (cheaper) or would it need paid? This feeds the should-you-do-an-ambassador recommendation in GTM.

---

# Source selection by mode

| Mode | Part A emphasis | Part B included? | Cap |
|---|---|---|---|
| Competitor Analysis | Review platforms, brand sites, pricing | B2 (funding) only | 6–8 |
| PMF Analysis | Community (Reddit), review text | None by default | 5–6 |
| Full Launch Assessment | Balanced A — at least one community, one pricing, one brand site | B1, B2, B3, B4 as the selected tracks require | ~9 |

---

# General fallback strategy

Amazon.in, Blinkit, Flipkart, BigBasket, Myntra, Swiggy, and sometimes Nykaa block direct fetches. Do not retry the direct fetch — switch to search immediately:

1. `"[brand] reviews site:[domain]"` — indexed review snippets
2. `"[brand] [category] review India 2025 OR 2026"` — broader snippets
3. `"[brand] complaints OR feedback OR honest review"` — surfaces emotion faster

For Reddit, if `reddit.com/search` is empty: `"[brand] site:reddit.com"`, then `"[brand] site:reddit.com/r/india"`.

If all attempts fail, mark the source unavailable in the report and interpret the absence. The absence of data is itself a finding: a brand with near-zero reviews may be new, niche, or underperforming; a category with no market reports may be nascent or too small to have been sized.
