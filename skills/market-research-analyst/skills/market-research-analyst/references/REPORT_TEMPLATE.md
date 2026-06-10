# Report Template & HTML Spec

Loaded in Stage 3 with STAGE3_REPORT.md. STAGE3 decides the content and the verdict; this file decides the structure and the look. The report is a **scrolling decision dossier**, not a tabbed browser — it reads top to bottom as an argument that builds to a verdict, with a sticky side/jump nav for skipping around.

---

## Section structure by mode

Sections are numbered because the report is a sequence — an argument — and the order carries meaning. Render only the sections the mode calls for.

### Full Launch Assessment (flagship)
```
00 · Verdict masthead   GO / CONDITIONAL-GO / NO-GO · thesis · scorecard · data confidence
01 · The Market         size, CAGR (with window + source), momentum, the read
02 · The Competition    competitor profiles + pricing map + funding/traction + competitive read
03 · The Customer       unmet needs · repeat signals · verbatim customer voice
04 · The Product        flavour/variant winners & losers · format gaps
05 · The Gap            whitespace, framed as the founder's wedge
06 · Go to Market       channel sequence + brand-ambassador call
07 · Make vs Buy        own plant vs contract, with indicative MOQ
08 · How to Win         playbook · top risks · first 90 days
09 · Go Deeper          Deep Research prompt (copy button)
```

### Competitor Analysis
```
00 · Overview (competitive read, no verdict)
01 · Competitor Profiles
02 · Pricing Map
03 · Customer Sentiment
04 · Ad Language
05 · Go Deeper
```

### Product-Market Fit
```
00 · Overview (honest PMF assessment, no verdict)
01 · Unmet Needs
02 · Repeat Signals
03 · Customer Voice
04 · Whitespace
05 · Go Deeper
```

---

## Section content specs

**Verdict masthead (00, Full Launch Assessment)** — the signature element.
- The call as a large word: GO / CONDITIONAL-GO / NO-GO, coloured by semantic token.
- One-sentence thesis naming the wedge.
- The founder's original question echoed ("You asked: …") with the verdict answering it.
- **Scorecard**: six dimensions (Market pull · Demand clarity · Whitespace · Competitive room · Price & margin headroom · Execution feasibility), each a 0–5 horizontal bar with the number.
- **Data confidence** chip: High / Medium / Low, with one line on why.
- If CONDITIONAL-GO: the gates listed as a short checklist ("Go if: …").

**The Market (01)** — size + CAGR cards (figure, window, source on each); momentum note; the read in one paragraph. Conflicting estimates shown as a range with both sources.

**The Competition (02)** — one card per competitor: positioning, price range, strengths (sourced), weaknesses (sourced), distribution, funding/traction. A pricing-map table below: `Product | Pack size | Price | Price/unit | Platform`, then explicit segment-gap callouts. Competitor named but no data → card reads "No data found — not in market or insufficient reviews." Then the competitive read.

**The Customer (03)** — unmet needs (titled blocks, ordered by strength, each with evidence/frequency/workaround/strength); repeat signals; 8–12 verbatim quotes in styled blockquotes, each labelled `[source] · [+/–/mixed] · [theme]`.

**The Product (04)** — flavour/variant winners and losers per brand (rating + volume where available), and requested-but-absent flavours/formats. If variant data wasn't separable, say so plainly.

**The Gap (05)** — 1–3 whitespace opportunities framed as product concepts ("No brand does X well for Y"), each with what exists/why it fails, evidence, strength. The lead one is the founder's wedge.

**Go to Market (06)** — recommended channel sequence (grounded in pricing/distribution data) + the ambassador call stated as a decision with its reason.

**Make vs Buy (07)** — the recommendation (usually contract/co-packer for a new brand) with reasoning and indicative MOQ; what would have to be true to justify own manufacturing; "confirm with 2–3 quotes" caveat.

**How to Win (08)** — playbook (3–5 moves) · top 3 risks · first 90 days (sequenced). First ad lines pulled verbatim from section 03.

**Go Deeper (09 / last)** — the Deep Research prompt + copy button.

---

## Design system — "The Analyst Dossier"

The report must read like a strategy-firm deliverable — a crafted document, not a web app. The look is fixed; only the data changes per run. Build it scoped under a single `#report` wrapper so styles never leak.

**Direction:** editorial two-column grid, refined navy-and-ochre palette on warm paper, structural hairlines, data presented as matrices and data-sheets, and a real PDF page architecture. Boldness is spent in exactly one place — the verdict cover and its scorecard matrix; everything else stays quiet.

**Density is a requirement, not a preference.** Short content in wide columns reads as empty and unfinished — the opposite of a consultancy deliverable. Keep vertical rhythm tight (section margins ~2.5rem, body line-height ~1.6), and make every section fill its column: use card grids, data-sheets, tables, and badge-anchored lists so content reads as deliberate objects, not floating fragments. The Deep Research prompt (section 09) is shown in FULL — no inner scroll box — so the founder can read the whole thing before copying.

### Tokens (CSS variables — set on `#report`)
```css
#report{
  --paper:#FBFAF7;   /* warm document paper */
  --ink:#1B1B1F;     /* primary text */
  --soft:#6B6B73;    /* secondary text */
  --faint:#9A968C;   /* labels, captions */
  --line:#E6E2D9;    /* structural hairlines */
  --brand:#1B2A4A;   /* navy — section numbers, active nav, buttons */
  --cover:#131C2E;   /* deep navy — verdict cover surface */
  --accent:#B7791F;  /* ochre — verdict + scorecard + key figures ONLY */
  --accent-soft:#F4EBD8;
  --go:#2F7A4D; --conditional:#B7791F; --nogo:#A13434;
  --mono:ui-monospace,"SF Mono",Menlo,Consolas,monospace;
  --sans:-apple-system,BlinkMacSystemFont,"Segoe UI",Roboto,Helvetica,Arial,sans-serif;
}
```

### Type (no external fonts — refined system stack + a mono utility face)
- Body/display: the `--sans` stack; body 16px / line-height 1.7 (document-like).
- **Mono is the analyst signature** — every eyebrow, label, price, score, and source tag uses `--mono`, uppercase, letter-spacing ~0.1–0.16em, small (9.5–11px).
- Scale: verdict word clamp 2.8–4.6rem / weight 800 / tracking −0.035em; section titles ~1.6rem / 700; big section number ~2.1rem in `--mono`, weight 500, `--brand`.

### Key components
- **Document bar (sticky top):** left = product title (bold 14px) + a `--mono` meta line (mode · stage · month-year); right = `[Copy Deep Research Prompt]` (filled navy) + `[Download PDF]` (ghost navy). Blurred paper background, hairline bottom.
- **Two-column shell:** `grid-template-columns:200px minmax(0,760px)` centred, ~3rem gap. Left = sticky numbered **rail nav** (`00`…`09`, mono number + label, active item gets ochre left-border + bold). On mobile the rail becomes a horizontal scroll strip and the labels hide, numbers stay.
- **Section header pattern:** big `--brand` section number on the left, then a mono eyebrow + bold `<h2>` title, with a hairline rule underneath. This grid is what makes it read "designed."
- **Verdict cover (00):** `--cover` deep-navy panel with a 3px ochre top-rule; mono "THE VERDICT" eyebrow; the verdict word in its semantic tint (go `#7FCB97` / conditional `#E8B864` / nogo `#E08A8A` on the dark cover); thesis; a hairline-divided "You asked" block (the word *you* in ochre italic); the scorecard; a "Data confidence" callout; and, for CONDITIONAL-GO, a numbered "Go if all three hold" gates list with ochre circular markers.
- **Scorecard = 5-segment matrix (the signature element):** each dimension is one row — mono label · five small segment blocks (filled = ochre `#E8B864`, empty = faint) · the `N/5` value in mono. Two-column grid of six rows. Fill the first *score* segments; stagger their reveal on load (≈90ms each), respecting `prefers-reduced-motion`. This rating-matrix device is what reads "consultancy," not a progress bar.
- **Competitor profiles = data-sheet, not prose:** a card per competitor with name + a mono "COMPETITOR · NAMED" tag, then `label : value` rows (Positioning, Price range, Strengths, Weaknesses, Distribution, Funding) on a 130px label column with hairline dividers. Verbatim phrases sit inline as small mono chips on `--accent-soft`.
- **Tables:** mono uppercase headers with a 1.5px ink underline, subtle zebra rows (`--zebra` on even rows) and tight padding for scan-density, figures in `--mono` `--brand`. Used for the wider-field map and the flavour/variant table.
- **Numbered steps (playbook, 90-days) — badge-anchored, never faint detached numbers.** Each step is a `grid` of `[number badge | body]`: a solid filled square badge (~1.7rem, white mono numeral) sits tight against a bold lead-in + description. Navy badges for the How-to-Win playbook, ochre badges for the 90-day action list to distinguish principle from action. Tight rows with light dividers — the number and its step must read as one unit.
- **Customer voice — feature + dense card grid (do NOT use full-width floating quotes; they read as empty).** Lead with ONE feature pull-quote (the strongest demand signal) in a bordered card at ~1.3rem. Then a responsive **2-column grid of anchored quote cards** — each a white card with a coloured polarity tag (POSITIVE/MIXED/NEGATIVE), the quote, and a mono attribution pinned to the bottom. End with any brand-positioning lines as a "don't echo them" callout, not a quote. The grid fills the column width and gives the section rhythm; single full-width quotes leave dead space and look unfinished.
- **Callouts:** white box, 3px ochre left border, mono eyebrow label — used for segment-gap, confidence notes, and the ambassador call. "The read" lines use a 2px solid ink top-rule instead, to mark a conclusion.
- **Wedge cards & playbook:** wedge cards carry a strength chip (mono); the How-to-Win playbook and 90-day list use leading-zero mono counters (`01`,`02`…).

### Quality floor
Responsive to mobile (rail → strip, grids → single column); visible focus rings (ochre); `prefers-reduced-motion` honoured; semantic `<h2>` per section; AA contrast.

### Behaviour (inline `<script>`, all scoped to `#report`)
- `jumpTo(e,id)` — smooth-scroll to a section.
- IntersectionObserver scroll-spy adds `.active` to the current rail link (`rootMargin:'-35% 0px -60% 0px'`).
- On load, build and fill the scorecard segments (append five `<i>` per `.sc-seg`, add `.on` to the first `data-score`, staggered unless reduced-motion).
- `copyPrompt()` writes `buildDeepResearchPrompt()` to the clipboard and flips both copy buttons to "Copied!" for 2s.
- `downloadPDF()` → `window.print()`.

### Print / PDF architecture (a stated priority — get this right)
```css
@media print{
  @page{ margin:16mm 14mm 20mm; }
  #report{ background:#fff; font-size:11pt; line-height:1.5; }
  #report .docbar, #report .rail{ display:none!important; }
  #report .shell{ display:block; max-width:none; padding:0; }
  /* verdict prints as an ink-friendly COVER page */
  #report .cover{ background:#fff!important; color:#000!important; border:1.5px solid #000; break-after:page; }
  #report .cover .verdict-word,#report .cover .thesis,#report .cover .asked p,#report .cover .asked em{ color:#000!important; }
  #report .sc-seg i{ border:1px solid #000; background:#fff!important; }   /* matrix → outline boxes */
  #report .sc-seg i.on{ background:#000!important; }
  #report .gates li:before{ background:#000; color:#fff; }
  #report .callout.dark,#report .promptbox{ background:#f4f4f4!important; color:#000!important; }
  /* each numbered section starts a fresh page; nothing splits mid-element */
  #report main>section{ break-before:page; }
  #report main>section:first-child{ break-before:avoid; }
  #report .profile,#report .wedge,#report .fig,#report .callout,#report blockquote,#report table,#report .pb li,#report .sec-head{ break-inside:avoid; }
  #report .pfoot{ display:block!important; }   /* fixed confidential footer */
}
```
A `.pfoot` element (hidden on screen, shown in print, `position:fixed; bottom:6mm`) carries a mono confidential footer line. The scorecard matrix is deliberately built from boxes so it survives the colour-to-ink conversion — filled segments become solid black, empty become outlines.

All CSS in one `<style>`, all JS in one `<script>`, both inline under `#report`. No external requests.

### Data-quality display conventions
| Situation | Display |
|---|---|
| Strong data | Present confidently; cite source inline |
| Partial (fallback used) | "(partial — search fallback)" after the source |
| Source unavailable | Explicit note: "No data — [source] could not be accessed" + interpretation |
| Conflicting sources | Show both: "Amazon reviews suggest X; Reddit suggests Y" |
| <5 data points | "Limited data — fewer than 5 sources. Treat as directional." |
| Market estimate | Always show figure + forecast window + source; conflicts as a range |

---

## Deep Research Prompt template

The copy button assembles this from the report's real findings. Store `SIGNALS`, `QUESTIONS`, `SOURCES`, and the header fields as JS constants, then interpolate:

```
You are a senior market research analyst. I need deeper research on a product launch decision.

PRODUCT: [product]
MARKET: [market]
COMPETITORS: [competitors]
MY DECISION: [the founder's stated decision/question]
INITIAL VERDICT: [GO / CONDITIONAL-GO / NO-GO] — [one-line thesis]

Initial research surfaced these signals:
- [signal 1]
- [signal 2]
- [signal 3]

Go deeper on these specific questions:
1. [question 1]
2. [question 2]
3. [question 3]

Prioritise these sources (thin or inaccessible in the first pass):
[4–5 named sources + why each]

Deliver a structured report covering: market size and growth, competitor funding and traction, unmet customer needs, repeat-purchase drivers, exact ad language worth using, pricing and margin analysis, manufacturing options (contract vs own), and a refined go/no-go with how-to-win. Cite the source for every specific claim; flag anything you cannot verify.
```

Build signals and questions from actual report content — never placeholders. These should be the items where more data would most change the founder's decision.
