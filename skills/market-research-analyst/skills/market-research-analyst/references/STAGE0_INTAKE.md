# Stage 0 — Intake

## Purpose

Parse what the user has told you, fill in sensible defaults for what they have not, then produce an intake form that arrives mostly complete. The goal: a founder looks at the form, adjusts one or two things, and hits Start Research within 30 seconds. The form is not an interrogation — it is a confirmation.

---

## Step 1: Parse the opening message

Extract these four fields from whatever the user has said:

| Field | What to look for | Default if missing |
|---|---|---|
| `product` | What they are building or launching — category, format, target customer | Leave blank — form will prompt |
| `market` | Geography — explicit ("India", "SEA") or implied by platform/currency/city | India |
| `competitors` | Any named brands, products, or companies mentioned | Empty — user fills the form |
| `mode` | Research intent — competitor focus, PMF focus, or general | Comprehensive |

### Parse conservatively

When uncertain whether a word is a competitor name or a category descriptor, leave competitors empty. Let the user confirm in the form.

- "competing in the chocolate space" → no named competitors, leave field empty
- "competing with Darkins" → one competitor: Darkins
- "going up against Darkins and Paul & Mike" → two competitors: Darkins, Paul & Mike

A wrong pre-filled competitor wastes an extraction slot and skews the report. Conservative parsing is safer than aggressive guessing.

### Mode inference rules

| What the user says | Mode |
|---|---|
| "competitor analysis", "how do my competitors do", "map the competition", "who else is in this space" | Competitor Analysis |
| "product market fit", "PMF", "do people want this", "is there demand", "validate my idea" | PMF Analysis |
| "full research", "comprehensive", "everything about the market", nothing stated | Comprehensive |
| Ambiguous — e.g. "help me research the chocolate market" | Comprehensive (default) |

When in doubt, use Comprehensive. It is always adjustable in the form.

---

## Step 2: Determine pre-fill completeness

Before generating the artifact, assess what you know and set your approach:

**All four fields known** (product + market + competitors + mode):
Generate the form fully pre-filled. Chat message: "I've pre-filled everything I caught — check it and hit Start Research, or adjust anything first."

**Product known, some fields missing** (most common case):
Pre-fill what you have, leave the rest for the user. Do not guess at the missing fields.

**Product unknown:**
Generate the form with the product field empty. Do not attempt to infer the product from context — leave it blank and let the user describe it. The product description shapes the entire research plan.

**Never pre-fill competitor names you did not read explicitly in the message.** Inference about competitors is Stage 1's job, not Stage 0's.

---

## Step 3: Generate the intake form artifact

Produce a single self-contained HTML artifact — the intake form. All CSS and JavaScript inline, zero external dependencies.

### Design principles

This form may be the first thing a non-technical founder sees in a live demo. It must:
- Look polished and professional at first glance
- Feel intuitive without any instruction
- Reduce friction, not add it — the founder should not need to think hard

Visual direction:
- White background (#ffffff), text in near-black (#1a1a1a)
- Indigo (#4f46e5) as the only accent colour
- Body font size 16px, generous line height
- Card padding of 1.5rem, form field padding of 0.75rem
- Rounded corners on cards and inputs (8px)
- Subtle 1px border on inputs (#e5e7eb) that shifts to indigo on focus
- Mobile-friendly — single column on narrow viewports

Opening line in the artifact (not in chat):
"Let's set up your research. I've pre-filled what I caught — adjust anything and hit Start Research when ready."

### Form elements

Build them in this exact order:

---

**1. Research Mode — three styled radio cards**

Not plain radio inputs. Three cards laid out side by side (on mobile: stacked vertically). Each card:
- Mode name in bold, 16px
- One-line description below it in muted grey, 14px
- Entire card is clickable — clicking anywhere selects it
- Selected state: 2px indigo border, light indigo background tint (#eef2ff)
- Unselected state: 1px light grey border (#e5e7eb), white background

Card content:
- **Competitor Analysis** / "Map competitors, their pricing, and what customers say"
- **Product-Market Fit** / "Find unmet needs, repeat purchase signals, and market gaps"
- **Comprehensive** / "Full picture: competitors + PMF + whitespace opportunities"

Pre-select the inferred mode. Default to Comprehensive if mode was not inferred.

---

**2. Product description — text input**

Label: "What are you building?"
Placeholder: "e.g. healthy dark chocolate brand for Indian urban consumers, launching D2C"
Pre-fill with the parsed product description if available.
This field is required. Do not allow submission without it.
On focus: indigo outline, placeholder text fades.

---

**3. Target market — dropdown**

Label: "Target market"
Options: India / Southeast Asia / Global
Pre-select the inferred market. Default to India.

---

**4. Competitors — tag-style input**

Label: "Competitors"
Helper text below the label: "Optional — type a name and press Enter to add"

Behaviour:
- User types a competitor name into a text input
- Pressing Enter or typing a comma adds it as a tag and clears the input
- Each tag displays the name + a × button to remove it
- Tags stored in a JavaScript array
- No limit on number of tags

Visual: tags as small pills — indigo background (#4f46e5), white text, 6px padding, rounded

Pre-fill with any parsed competitor names as tags.

If no competitors were parsed, leave empty. Add helper text: "Leave blank and we'll surface competitors during research."

---

**5. Research focus — multi-select pill buttons (optional)**

Label: "What matters most?"
Helper text: "Optional — select any focus areas, or leave blank to cover everything"

Six pill buttons in a wrapped row. Each toggles independently:
- Pricing and pack sizes
- Customer complaints
- Repeat purchase triggers
- Ad language and copy
- Market gaps
- Distribution channels

Default state: unselected (light grey background, grey text)
Selected state: indigo background, white text

Pre-select none by default.

---

**6. Submit button**

Label: "Start Research →"
Style: full-width, indigo background, white text, 48px height, 16px font, bold
This must be unmistakably the primary action on the page.

On click:
1. Run validation (see below)
2. If validation fails: highlight the failing field, show inline error, stop
3. If validation passes: disable the button, change label to "Setting up research…" to signal something is happening
4. Call `sendPrompt()` with the structured output

---

### Form validation

Check before allowing submission:

- **Product description is empty** → highlight the field, show: "Tell us what you're building — this shapes the entire research plan."
- **Research mode not selected** → always pre-selected, so this should not occur; handle defensively: "Please select a research mode."
- Everything else (competitors, focus) is optional — no validation needed.

Do not block submission for missing optional fields.

---

### sendPrompt output format

When validation passes and the user clicks submit, call:

```javascript
sendPrompt(`[RESEARCH_REQUEST]
mode: ${selectedMode}
product: ${productDescription.trim()}
market: ${selectedMarket}
competitors: ${competitorTags.join(', ') || 'none named'}
focus: ${selectedFocus.join(', ') || 'all'}
[/RESEARCH_REQUEST]`);
```

This format is parsed exactly by Stage 1. Do not alter the field names or the `[RESEARCH_REQUEST]` wrapper.

---

## Step 4: Chat message alongside the artifact

> "I've set up the research form on the right. I've pre-filled what I caught — check it and adjust anything, then hit Start Research."

If product description was not parseable from the opening message, add:
> "I didn't catch what product you're building — fill that in first, it shapes everything."

Keep the chat message short. The form is on the right; the user's attention should go there.

---

## Edge cases

**User says they do not know their competitors yet**
Leave competitors empty. Add helper text to the competitors field: "Leave blank and we'll surface competitors during research." In Stage 1, the planner will add a competitor discovery step at the top of the source list.

**User pastes a long product brief or document**
Extract product, market, and competitors from it. Summarise the product to one clear sentence for pre-filling — do not paste the full brief into the product field. The intake form is a triage tool, not a document editor.

**User asks what the research modes mean**
Explain briefly in chat first, then generate the form. The one-line descriptions under each card in the form should make the choice self-evident.

**Opening message is already a `[RESEARCH_REQUEST]` block**
Skip the form entirely. Parse the fields directly and proceed to Stage 1. Load `references/STAGE1_PLAN.md`.

**User changes their mind after submitting**
The `[RESEARCH_REQUEST]` is already in the conversation. Handle the change in Stage 1 — update the plan to reflect the new intent. There is no need to reopen the intake form.

**Opening message is extremely vague** (e.g. "help me" with no product context)
Ask one clarifying question in chat before generating the form: "What product or market are you researching?" Generate the form after their reply.
