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

## Step 3: Load and output the intake form artifact

Do not generate the form HTML from scratch. The complete form is pre-built in `references/INTAKE_FORM.html`. Load it, fill in the `PRE_FILL` constant, and output it as an HTML artifact.

### What to fill in

The file has this constant near the top of its script block (line 153):

```javascript
const PRE_FILL={product:"",market:"India",competitors:[],mode:"Full Launch Assessment",price_point:"",decision:""};
```

Replace the values with what you parsed from the opening message:

| Field | Value to set | Notes |
|---|---|---|
| `product` | Parsed product description | Leave `""` if not found |
| `market` | `"India"` / `"Southeast Asia"` / `"Global"` | Default `"India"` |
| `competitors` | Array of name strings — e.g. `["Darkins","Paul & Mike"]` | Leave `[]` if none found |
| `mode` | `"Competitor Analysis"` / `"Product-Market Fit"` / `"Full Launch Assessment"` | Default `"Full Launch Assessment"` |
| `price_point` | Target price if the user stated one | Leave `""` otherwise |
| `decision` | The specific question/decision if stated | Leave `""` otherwise |

**Only modify the `PRE_FILL` line. Do not change anything else in the file.**

### How the form works

The form handles all behaviour internally:
- Mode card selection and the Full Launch Assessment conditional block (shows/hides automatically)
- Tag input for competitors (Enter or comma to add, × to remove)
- Focus pill toggling (optional multi-select)
- Stage and manufacturing radio pills (Undecided pre-selected by default for manufacturing)
- Track pills (all ON by default for Full Launch Assessment, with a Select all / Deselect all toggle)
- Validation (product required, everything else optional)
- Submit button state and `sendPrompt()` with the exact `[RESEARCH_REQUEST]` format Stage 1 expects

### Output

Output the complete file content as an HTML artifact. The form is ready to use.

### The sendPrompt output format

Already wired in the template — Stage 1 receives:

```
[RESEARCH_REQUEST]
mode: ...
product: ...
market: ...
competitors: ...
focus: ...
stage: ...
price_point: ...
decision: ...
manufacturing: ...
tracks: ...
[/RESEARCH_REQUEST]
```

For Competitor Analysis and Product-Market Fit modes, the launch-details fields are hidden and carry their defaults — that is correct and Stage 1 handles it.

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
