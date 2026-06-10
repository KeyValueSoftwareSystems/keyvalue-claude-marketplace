# Stage 1 — Plan

## Purpose

Select the right sources, present a clear and specific research plan, and confirm with the user before starting extraction. A good plan names exactly what you will look for at each source and why — not just which URLs to visit. It gives the founder confidence that the research will answer their actual question.

---

## Step 1: Parse the [RESEARCH_REQUEST]

Read all five fields carefully:

- `mode` — drives which sources to prioritise and how many to include
- `product` — used to infer product category and therefore which section of SOURCES.md applies
- `market` — determines geography-specific platform selection
- `competitors` — named brands go directly onto the source list; "none named" triggers a discovery step
- `focus` — specific focus areas tilt source selection toward particular platforms

---

## Step 2: Infer the product category

Use the product description to identify the category. This determines which section of SOURCES.md to draw from. Work through this decision tree:

**Does the product involve food or drink?**
→ Yes: Is it primarily health or wellness (protein, supplement, low-calorie, diabetic-friendly)?
  → Yes → **Health and Fitness** category
  → No → **Food and FMCG** category

**Is it clothing, footwear, or accessories?**
→ Yes → **Fashion and Apparel** category

**Is it a skincare, haircare, or cosmetics product?**
→ Yes → **Beauty and Personal Care** category

**Is it software, an app, or a digital tool?**
→ Yes → **SaaS and Tech** category

### Ambiguous and crossover cases

Some products straddle categories. Apply these rules:

- **Health × Food crossover** (e.g. protein chocolate, functional beverage): Use the primary purchase driver. A protein chocolate is bought for health first — draw from Health category, supplement with Food review platforms (Amazon.in, Reddit food communities).
- **Beauty × Wellness crossover** (e.g. supplements that claim to improve skin): Use Beauty if the claim is about appearance, Health if the claim is about physiology.
- **Category still unclear after reading the description**: Default to Food/FMCG for India-market physical products, SaaS for digital products. Note the assumption in the plan so the user can correct it.

---

## Step 3: Handle "none named" competitors

If the competitors field is "none named", add a discovery step as the first item in the plan:

```
1. Google / Amazon.in / [primary platform for category] — search "[product category] brands India" to find main competitors before diving into reviews
```

This gives you 3–5 competitor names to work with during extraction. Note this in the plan: "I'll surface competitors first, then research each one."

If fewer than 3 named competitors were provided, consider whether adding a discovery step alongside the named ones would round out the research.

---

## Step 4: Select sources from SOURCES.md

Apply these selection rules to the SOURCES.md tables for the identified category:

### Source count targets

| Mode | Target count | Emphasis |
|---|---|---|
| Competitor Analysis | 6–8 | Review platforms + brand websites + pricing pages |
| PMF Analysis | 5–6 | Community sources (Reddit, forums) + review text |
| Comprehensive | 7–8 | Balanced — at least one community source, one pricing source, one brand site |

Quality beats volume. 5 strong, well-chosen sources produce a better report than 10 sources with thin data.

### Mandatory inclusions

For every named competitor, always include:
- Their brand website (positioning, range, pricing)
- Their top review platform for the category (Amazon.in for most India D2C; G2 for SaaS)
- At least one Reddit search covering the brand

For every plan regardless of mode, always include:
- At least one community source (Reddit). Real customer voice is irreplaceable.
- The highest-priority source in SOURCES.md for the identified category.

### Focus-area tilts

If the user selected specific focus areas, adjust source weighting:

| Focus area selected | Add or prioritise |
|---|---|
| Pricing and pack sizes | Blinkit, BigBasket, Swiggy Instamart — even if lower priority in SOURCES.md |
| Customer complaints | Weight review platforms (Amazon.in, Flipkart, Myntra) over brand sites |
| Ad language and copy | Maximise review text sources — Amazon, Reddit, Nykaa |
| Repeat purchase triggers | Reddit and longer-form review platforms over quick listings |
| Market gaps | Weight Reddit and community sources heavily |
| Distribution channels | Add all quick-commerce platforms (Blinkit, BigBasket, Swiggy) |

### Geography adjustments

- **India**: Use India-specific platforms as listed in SOURCES.md. Avoid global platforms (Trustpilot, G2) unless the competitor is international.
- **Southeast Asia**: Replace India platforms with Shopee, Lazada, Tokopedia, and relevant country-specific Reddit communities. Keep brand websites.
- **Global**: Shift to international review platforms (G2, Capterra, Trustpilot, Product Hunt) + Reddit. Brand websites always relevant.

### Winnowing

If you have selected more than 8 sources after applying all rules, cut starting from the lowest-priority items in SOURCES.md for the category. Never cut: brand websites of named competitors, the primary review platform, or Reddit.

---

## Step 5: Present the plan

Format the plan as a numbered list in chat. Be specific at every line — name what you are looking for, not just where you are going.

### Example of a good plan

```
Here's my research plan:

1. Amazon.in — Darkins and Paul & Mike customer reviews (what people praise, what they complain about, exact phrases they use)
2. Reddit r/india, r/desifoodporn — organic brand mentions and unfiltered community sentiment
3. Blinkit — exact pricing and pack sizes for both brands
4. Darkins website — brand positioning, full product range, certifications claimed
5. Paul & Mike website — same
6. Google news — press coverage, funding history, any notable events in the last 18 months

This covers competitive positioning, pricing structure, and authentic customer voice. Say "go" to start, or tell me anything you'd like to add or change.
```

### What makes a bad plan

Avoid these:
- **Vague sources**: "I'll search the internet for reviews" → name the platform
- **Too many sources**: 10+ is unfocused and produces thin extraction at each stop
- **Wrong sources for the category**: G2 for a chocolate brand; Blinkit for SaaS products
- **No community source**: Reddit almost always belongs in the plan — real, unfiltered customer voice
- **No explanation of intent**: "Amazon.in" with no note of what you are looking for

---

## Step 6: Handle user modifications

**User adds a source:**
Evaluate viability before accepting. If the source is likely to be blocked (bot detection) or irrelevant to the category, say why briefly and ask whether to include it anyway. If viable, add it and confirm the updated plan.

**User removes a source:**
Note if the removal creates a gap. Example: "Removing Reddit means we will not have community sentiment — that is fine if you are mainly interested in pricing." Then show the updated plan.

**User changes the mode:**
Rebuild the source selection from scratch using the new mode's rules. Present the revised plan and ask for confirmation again.

**User says "just go" or "start now":**
Proceed immediately with the current plan. Do not wait for further input.

---

## Step 7: Confirmation handling

Wait for explicit confirmation before moving to Stage 2.

Acceptable confirmations: "go", "yes", "start", "looks good", "sounds right", "proceed", a thumbs up, or any clear affirmative.

**If the user asks a question instead of confirming:**
Answer the question, then re-ask for confirmation with a simple: "Ready to start?"

**If two exchanges pass without a clear confirmation:**
Proceed and note it: "I'll proceed with this plan — let me know if you want to adjust anything mid-research."

**Do not re-open the intake form from the Plan stage.** If the user wants to change their product or mode fundamentally, rebuild the plan for the new context — do not send them back to the form.
