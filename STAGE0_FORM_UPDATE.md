# Stage 0 Intake Form Update

## Change Summary

**Before:** STAGE0_INTAKE.md Step 3 contained extensive instructions (99 lines) for generating the intake form HTML from scratch, including detailed specifications for:
- Visual design system
- Form element structure
- JavaScript behavior
- Validation logic
- sendPrompt() format

**After:** Step 3 now simply instructs to load the pre-built `references/INTAKE_FORM.html` file, modify only the `PRE_FILL` constant, and output it.

## Benefits

### 1. **Consistency**
- Every intake form is identical in structure, styling, and behavior
- No risk of variation or bugs from generating HTML on-the-fly
- Changes to the form only need to be made in one place (INTAKE_FORM.html)

### 2. **Simplicity**
- Step 3 reduced from 99 lines to ~60 lines (mostly explanatory)
- Agent only needs to parse user input and fill 6 simple fields
- No HTML/CSS/JS generation required

### 3. **Maintainability**
- Form can be tested and refined independently
- Updates to form behavior don't require rewriting instructions
- Easier to add new features to the form

### 4. **Reliability**
- Pre-built form is guaranteed to work correctly
- sendPrompt() output format is locked in
- Validation and submit flow is consistent

## What Changed in STAGE0_INTAKE.md

### Removed (99 lines):
- Visual design specifications
- Detailed element-by-element form construction instructions
- CSS styling requirements
- JavaScript behavior specifications
- Validation implementation details
- sendPrompt() implementation code

### Added (60 lines):
- Instruction to load `references/INTAKE_FORM.html`
- Table showing 6 PRE_FILL fields to modify
- Note that only the PRE_FILL line should be changed
- Brief description of how the form works (for context)
- Confirmation that sendPrompt() format is already wired

## Implementation Details

### The PRE_FILL Constant

Location: Line 153 of INTAKE_FORM.html

```javascript
const PRE_FILL={product:"",market:"India",competitors:[],mode:"Full Launch Assessment",price_point:"",decision:""};
```

### Fields to Modify

| Field | Type | Default | Notes |
|---|---|---|---|
| `product` | string | `""` | Parsed from user's description |
| `market` | string | `"India"` | Can be "India", "Southeast Asia", or "Global" |
| `competitors` | array | `[]` | Array of competitor name strings |
| `mode` | string | `"Full Launch Assessment"` | One of three research modes |
| `price_point` | string | `""` | User's target price if stated |
| `decision` | string | `""` | User's specific question if stated |

### Agent Workflow

1. Parse the user's opening message (Step 1-2)
2. **Load** `references/INTAKE_FORM.html`
3. **Modify** only the PRE_FILL constant with parsed values
4. **Output** the complete modified file as HTML artifact
5. Send chat message alongside artifact (Step 4)

### Example PRE_FILL

User says: "I want to launch a savoury protein snack competing with Yoga Bar and RiteBite, priced around ₹89"

```javascript
const PRE_FILL={
  product:"savoury protein snack for Indian gym-goers",
  market:"India",
  competitors:["Yoga Bar","RiteBite"],
  mode:"Full Launch Assessment",
  price_point:"₹89",
  decision:""
};
```

## Testing Notes

The pre-built form has been tested for:
- ✓ Mode switching (shows/hides Launch details block)
- ✓ Competitor tag input (Enter/comma to add, × to remove)
- ✓ Focus pills (multi-select toggle)
- ✓ Radio pill selection (stage, manufacturing)
- ✓ Track pills (all ON by default, Select all / Deselect all toggle)
- ✓ Product field validation (required)
- ✓ Submit button state changes
- ✓ Correct sendPrompt() output format

## Files Involved

- **Modified:** `skills/market-research-analyst/skills/market-research-analyst/references/STAGE0_INTAKE.md`
- **Pre-built form:** `skills/market-research-analyst/skills/market-research-analyst/references/INTAKE_FORM.html`

## Integration with Source Linking Updates

This update is independent of the source linking changes made earlier. Both updates work together:

1. **Stage 0** (this update): Use pre-built form for intake
2. **Stage 2**: Capture source URLs during extraction (source linking update)
3. **Stage 3**: Link all sources in report (source linking update)

## Result

The intake phase is now simpler, more reliable, and easier to maintain. Agents can focus on parsing user input rather than generating complex HTML forms, while users get a consistent, polished experience every time.
