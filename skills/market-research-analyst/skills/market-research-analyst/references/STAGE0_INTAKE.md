# Stage 0 — Intake

## Purpose

Parse what the user told you, fill sensible defaults for the rest, and produce an intake form that arrives mostly complete. A founder should look at it, adjust one or two things, and hit Start Research within 30 seconds. The form is a confirmation, not an interrogation.

The form must stay light for the two quick modes and get richer only when the founder picks **Full Launch Assessment** — the strategic questions appear then, not before. Friction is the enemy; never make a founder answer a question the research could infer.

---

## Step 1: Parse the opening message

Extract what you can:

| Field | What to look for | Default if missing |
|---|---|---|
| `product` | What they are building/launching — category, format, customer | Leave blank — form prompts |
| `market` | Geography — explicit or implied by platform/currency/city | India |
| `competitors` | Named brands/products/companies mentioned | Empty — user fills |
| `mode` | Research intent (see rules below) | Full Launch Assessment if they describe starting a business; else Competitor or PMF per cues |

### Parse competitors conservatively

When unsure whether a word is a competitor or a category descriptor, leave competitors empty.
- "competing in the chocolate space" → none named
- "competing with Darkins" → Darkins
- "up against Darkins and Paul & Mike" → both

A wrong pre-filled competitor wastes an extraction slot and skews the verdict. Conservative beats aggressive.

### Mode inference

| What the user says | Mode |
|---|---|
| "competitor analysis", "map the competition", "who else is in this space", "how do rivals price" | Competitor Analysis |
| "product-market fit", "PMF", "do people want this", "is there demand", "validate my idea" | Product-Market Fit |
| "should I start/launch this", "is it worth building", "I want to launch a [product]", "go/no-go", "full research", or nothing stated while describing a new product business | **Full Launch Assessment** |

When a founder is clearly weighing whether to start a product business, default to **Full Launch Assessment** — that is the question they are actually asking. It is always adjustable in the form.

---

## Step 2: Determine pre-fill completeness

- **All known** → pre-fill fully. Chat: "I've pre-filled everything I caught — check it and hit Start Research, or adjust first."
- **Product known, some missing** (common) → pre-fill what you have, leave the rest.
- **Product unknown** → leave product blank; do not infer it. The product description shapes the entire plan.

**Never pre-fill competitor names you did not read explicitly.** Inferring competitors is Stage 1's job.

For the strategic fields (stage, price, decision, manufacturing, tracks): pre-fill only if the user stated them outright. Otherwise leave at default — the form is faster to confirm than to correct.

---

## Step 3: Generate the intake form artifact

One self-contained HTML artifact, all CSS/JS inline, zero external dependencies. Build elements in this exact order.

### Visual direction
Clean, confident, modern — this may be the first thing a founder sees in a live demo.
- Warm paper background (#F7F5F0), near-black ink (#18181B)
- Single accent: deep indigo #4338CA; selected/active states tint #EEF0FF
- Body 16px, generous line height (1.6)
- Cards/inputs: 10px radius, 1px border #E4E0D7 that shifts to accent on focus
- Card padding 1.5rem, field padding 0.75rem
- Eyebrow labels and any data in a monospace stack (`ui-monospace, "SF Mono", Menlo, monospace`), uppercase, letter-spaced — this is the type signature, reused in the report
- Single column on mobile

Opening line inside the artifact:
"Let's set up your research. I've pre-filled what I caught — adjust anything and hit Start Research when ready."

### Form elements, in order

**1. Research Mode — three styled radio cards** (side by side; stacked on mobile)
Each card: mode name bold 16px, one-line description in muted grey 14px below. Entire card clickable. Selected = 2px accent border + tint background; unselected = 1px #E4E0D7 + white.
- **Competitor Analysis** / "Map competitors, pricing, and what customers say"
- **Product-Market Fit** / "Find unmet needs, repeat-purchase signals, and gaps"
- **Full Launch Assessment** / "The full picture, ending in a GO / NO-GO verdict and how to win"

Pre-select the inferred mode; default to Full Launch Assessment.

**Selecting Full Launch Assessment reveals the "Launch details" block (element 6). The two lighter modes keep it hidden.** Wire this with a JS toggle on mode change.

**2. Product description — required text input**
Label: "What are you building?"
Placeholder: "e.g. high-protein savoury snack for Indian gym-goers, launching D2C"
Pre-fill if parsed. Required — block submission without it. Accent outline on focus.

**3. Target market — dropdown**
Label: "Target market" · Options: India / Southeast Asia / Global · Pre-select inferred; default India.

**4. Competitors — tag input**
Label: "Competitors" · Helper: "Optional — type a name and press Enter to add"
Enter or comma adds a pill (accent bg, white text, × to remove); stored in a JS array; no limit. Pre-fill parsed names.
If none parsed, helper: "Leave blank and we'll surface competitors during research."

**5. Research focus — multi-select pills (optional)**
Label: "What matters most?" · Helper: "Optional — select any, or leave blank to cover everything"
Pills toggle independently. Default unselected (grey); selected = accent bg, white text.
Pills: Pricing & pack sizes · Customer complaints · Repeat-purchase triggers · Ad language & copy · Market gaps · Distribution channels

**6. Launch details — strategic block (only when Full Launch Assessment is selected)**
Header: "Launch details" · Sub: "Optional — the more you tell us, the sharper the verdict."

  **6a. Your stage** — three small radio pills: Just an idea · Pre-launch (building) · Launched (iterating). Default: none (treated as "not specified").

  **6b. Target price point** — short text input. Label: "Target price (optional)". Placeholder: "e.g. ₹99 for a 40g bar". Pre-fill if stated.

  **6c. Your biggest question** — short text input. Label: "What's the decision you're trying to make?". Placeholder: "e.g. is there room for a savoury protein snack under ₹100?". This becomes the spine of the verdict — capture it if offered.

  **6d. Manufacturing** — three radio pills: Own plant · Contract / co-packer · Undecided. Default: Undecided.

  **6e. Deep-dive tracks — multi-select pills with a Select all toggle.**
  Header row: "Go deeper on:" with a small **"Select all"** link/button on the right that toggles every pill on or off.
  Pills (all default ON for Full Launch Assessment — these are the new strategic tracks):
  - Market size & growth (CAGR)
  - Funding & competitor traction
  - Flavours / variants that win
  - Go-to-market plan
  - Brand-ambassador call
  - Make vs buy (manufacturing)

  These tracks decide which Part-B sources Stage 1 pulls. All-on by default gives the founder the complete verdict; they can switch off any track to keep the run lighter.

**7. Submit button**
Label: "Start Research →" · Full-width, accent bg, white text, 48px, 16px bold — unmistakably the primary action.
On click: validate → if fail, highlight field + inline error + stop → if pass, disable button, change label to "Setting up research…", call `sendPrompt()`.

### Validation
- Product empty → highlight, show "Tell us what you're building — this shapes the entire research plan."
- Mode not selected → defensive only (always pre-selected): "Please select a research mode."
- Everything else optional — no validation.

### sendPrompt output format

When validation passes, call exactly this (Stage 1 parses it verbatim — do not rename fields or alter the wrapper):

```javascript
sendPrompt(`[RESEARCH_REQUEST]
mode: ${selectedMode}
product: ${productDescription.trim()}
market: ${selectedMarket}
competitors: ${competitorTags.join(', ') || 'none named'}
focus: ${selectedFocus.join(', ') || 'all'}
stage: ${selectedStage || 'not specified'}
price_point: ${priceInput.trim() || 'not specified'}
decision: ${decisionInput.trim() || 'general assessment'}
manufacturing: ${selectedManufacturing || 'undecided'}
tracks: ${selectedTracks.join(', ') || 'all'}
[/RESEARCH_REQUEST]`);
```

For the two lighter modes the launch-details fields are hidden, so `stage`, `price_point`, `decision`, `manufacturing`, and `tracks` will carry their defaults — that is correct and Stage 1 handles it.

---

## Step 4: Chat message alongside the artifact

> "I've set up the research form on the right. I've pre-filled what I caught — check it, adjust anything, then hit Start Research."

If product wasn't parseable, add:
> "I didn't catch what product you're building — fill that in first, it shapes everything."

Keep it short. The form is on the right; attention goes there.

---

## Edge cases

**No competitors yet** → leave empty, helper "Leave blank and we'll surface competitors during research." Stage 1 adds a discovery step.

**Long product brief pasted** → extract product/market/competitors; summarise product to one sentence for the field. The form triages, it does not edit documents.

**User asks what the modes mean** → explain briefly in chat, then generate the form.

**Opening message is already a `[RESEARCH_REQUEST]`** → skip the form; parse and go to Stage 1.

**User changes their mind after submitting** → handle in Stage 1; do not reopen the form.

**Extremely vague opener** (e.g. "help me") → ask one question in chat — "What product or market are you researching?" — then generate the form after the reply.
