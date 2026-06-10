# Report Templates and HTML Artifact Spec

Loaded in Stage 3. Follow the content structure for the selected mode, then follow the HTML spec to produce the artifact.

---

## Four core dimensions (always present)

Regardless of mode, every report includes these four dimensions where data exists.

**Unmet needs** — What customers want but no brand delivers well. Look for: repeated complaints with no resolution, "I wish" and "if only" language, price-segment gaps (e.g. nothing between ₹100 and ₹300), format gaps (e.g. no single-serve option).

**Repeat signals** — Why customers come back or why they leave. Look for: "I keep buying because...", "I switched because...", subscription or auto-order mentions, gifting mentions (strong loyalty indicator), and high return rates (churn signal).

**Ad language worth using** — The exact phrases customers use — not your paraphrases. Copy-ready. Look for: adjectives appearing 3+ times in positive reviews, emotional language ("finally a brand that"), problem statements ("was tired of", "couldn't find"), and specific product descriptors customers reach for unprompted.

**Whitespace** — Gaps no current competitor fills well. Look for: recurring unmet needs with no good existing solution, price segments with no quality option, underserved customer segments, distribution channels with no strong player.

---

## Mode 1: Competitor Analysis

### Tabs (in this order)
**Overview · Competitor Profiles · Pricing Map · Customer Sentiment · Ad Language**

---

**Overview tab**
- 2–3 sentence market summary: who the main players are, what the competitive dynamic looks like, where the obvious opening is
- Data confidence note: which sources had strong data, which had gaps, overall confidence level

---

**Competitor Profiles tab**
For each competitor, a structured card:
```
[Competitor Name]
Positioning: how they describe themselves in their own copy
Price range: ₹X to ₹Y across pack sizes
Strengths: what customers consistently praise (with source)
Weaknesses: what customers consistently complain about (with source)
Distribution: where they sell — Amazon / Blinkit / D2C / retail / etc.
Data source: [source name]
```
If a competitor was mentioned by the user but no data was found, show the card with: "No data found — not available in market or insufficient reviews."

---

**Pricing Map tab**
An HTML table:
| Product | Pack size | Price | Price per unit | Platform |

Below the table, note any price-segment gaps explicitly:
- "No option exists between ₹X and ₹Y"
- "Single-serve format is not offered by any competitor"
- "Only one brand below ₹200 — and it has poor reviews"

---

**Customer Sentiment tab**
- Top 3 praise themes across all competitors, with source citations and representative quote for each
- Top 3 complaint themes across all competitors, same format
- 5–8 verbatim review quotes that best illustrate the themes — labelled with brand and source

---

**Ad Language tab**
Verbatim phrases worth testing in copy, grouped by type:

*Trust language:* "no refined sugar", "third-party tested", "no artificial flavours"
*Product language:* "melt-in-mouth", "single origin", "Belgian couverture"
*Emotional language:* "finally a chocolate I don't feel guilty about", "my kids ask for this by name"

Each phrase tagged with its source platform. Note frequency if a phrase appears across multiple sources.

---

## Mode 2: PMF Analysis

### Tabs (in this order)
**Overview · Unmet Needs · Repeat Signals · Customer Voice · Whitespace**

---

**Overview tab**
- Honest PMF assessment: is there clear demand signal? What's the evidence strength — strong, moderate, or weak?
- Top 2–3 most compelling signals in one paragraph
- Data confidence note

---

**Unmet Needs tab**
Each unmet need as a titled section:

```
[Need name — specific and concrete, e.g. "Dark chocolate under ₹200 with less than 5g sugar per serve"]

Evidence: 2–3 quotes or data points that demonstrate this need
Frequency: mentioned in approximately N reviews / N Reddit threads
Current best option: what people use now (and why it falls short)
Opportunity strength: Strong / Medium / Weak
```

Order by opportunity strength — strongest first.

---

**Repeat Signals tab**
What drives loyalty in this category — be specific, not generic:
- The specific product properties people mention when they say they keep buying
- What causes churn (the specific complaints that push people to switch)
- Whether customers are vocal advocates (referrals, gifting, unsolicited posts) or silent buyers

---

**Customer Voice tab**
10–15 verbatim quotes, organised under themes. Each quote labelled:
*[Source platform] · [Positive / Negative / Mixed] · [Theme tag]*

Choose quotes that would be genuinely useful for a founder writing copy or designing a product — the real language customers use, not paraphrases.

---

**Whitespace tab**
3–5 specific, actionable market gaps. Format each as:

```
Gap: No brand currently [does X] well for [Y customer]
Evidence: [what signals point to this]
Signal strength: Strong / Medium / Weak
```

Order by signal strength. A "weak signal" gap is still worth including — note it as early-stage validation needed.

---

## Mode 3: Comprehensive

### Tabs (in this order)
**Overview · Competitors · Pricing · Sentiment · Unmet Needs · Customer Voice · Whitespace**

Combine the content from Mode 1 and Mode 2 across the appropriate tabs.

**Overview tab additions** (beyond what Mode 1 and 2 have):
- Recommended positioning angle: one clear sentence on where the new brand should sit given what the analysis reveals
- Top 3 risks or watch-outs a founder should be aware of before entering this market

---

## HTML artifact spec

### Design system
- Background: white (#ffffff), text: #1a1a1a
- Accent (tabs, buttons, badges): indigo #4f46e5
- Active tab: indigo background, white text
- Inactive tab: #f3f4f6 background, #6b7280 text
- Font: `system-ui, -apple-system, sans-serif` (no external font imports)
- Max-width: 900px, centred with auto margins
- Padding: 1.5rem on content sections
- Fully responsive — works on mobile
- All CSS and JavaScript inline — zero external dependencies

### Structure
```
<sticky header>
  Left side: product name (bold, 18px) · mode badge (coloured pill)
  Right side: [Copy Deep Research Prompt] button · [Download PDF] button
  Border-bottom: 1px solid #e5e7eb
</sticky header>

<tab navigation>
  Horizontal row of tab buttons, full width
  Active tab: indigo bg, white text, no bottom border
  Inactive: light grey bg, grey text
  On mobile: horizontally scrollable
</tab navigation>

<tab content panels>
  One <section> per tab
  Active: display block
  Inactive: display none
  Each section: clear heading (h2), then structured content
  Competitor cards and pricing tables use light borders (#e5e7eb)
  Verbatim quotes in styled blockquotes: left border indigo, light grey background, italic text
</tab content panels>
```

### JavaScript behaviour
```javascript
// Tab switching
function switchTab(tabId) {
  document.querySelectorAll('.tab-btn').forEach(b => b.classList.remove('active'));
  document.querySelectorAll('.tab-panel').forEach(p => p.style.display = 'none');
  document.getElementById('btn-' + tabId).classList.add('active');
  document.getElementById('panel-' + tabId).style.display = 'block';
}

// Copy Deep Research Prompt
function copyPrompt() {
  const prompt = buildDeepResearchPrompt(); // assembles from report constants
  navigator.clipboard.writeText(prompt).then(() => {
    const btn = document.getElementById('copy-btn');
    const original = btn.textContent;
    btn.textContent = 'Copied!';
    setTimeout(() => btn.textContent = original, 2000);
  });
}

// Download PDF
function downloadPDF() { window.print(); }
```

### Print CSS
```css
@media print {
  header { position: static; }
  .tab-nav, .action-buttons { display: none; }
  .tab-panel { display: block !important; }
  h2 { page-break-before: always; }
  h2:first-of-type { page-break-before: avoid; }
  blockquote { break-inside: avoid; }
}
```

### Data quality display
| Situation | How to display |
|---|---|
| Strong data from source | Present with confidence. Cite source inline. |
| Partial data (fallback used) | Add "(partial — search fallback used)" after the source name |
| Source completely unavailable | Show explicit note: "No data — [source] could not be accessed" |
| Conflicting data across sources | "Amazon.in reviews suggest X; Reddit discussions suggest Y" — show both |
| Fewer than 5 data points | Add "Limited data — fewer than 5 sources. Treat with caution." |

---

## Deep Research Prompt template

The "Copy Deep Research Prompt" button dynamically assembles this from the report's actual findings. Store the key data as JavaScript constants at the top of the artifact script block, then interpolate them into this template:

```
You are a senior market research analyst. I need deeper research on a product opportunity.

PRODUCT: [product description]
MARKET: [market]
COMPETITORS: [competitor names]
RESEARCH MODE: [mode]

Initial research found these key signals:
- [top finding 1 from this report]
- [top finding 2 from this report]
- [top finding 3 from this report]

Go deeper on each of these questions:
1. [gap or open question 1 from the report]
2. [gap or open question 2 from the report]
3. [gap or open question 3 from the report]

Prioritise these sources:
[list 4-5 most relevant sources from the research plan]

Deliver a structured report covering: unmet customer needs, repeat purchase drivers, exact ad language worth using, detailed pricing analysis, and whitespace opportunities. Cite the source for every specific claim.
```

Build the three key signals and three questions directly from the report content — don't use placeholder text. These should be the most actionable items a founder needs to investigate further.
