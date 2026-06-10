# Source Linking Updates — Market Research Analyst Skill

## Issue Addressed
Sources were mentioned but not consistently linked throughout the skill execution. Users need clickable hyperlinks to verify findings and explore sources themselves.

## Changes Made

### 1. **SKILL.md** (Main skill file)
- Updated core rule: "Cite everything" now explicitly requires hyperlinks, not just source names
- Added requirement that founders need to verify evidence and explore sources

### 2. **STAGE2_EXTRACT.md** (Extraction phase)

#### Progress notation updates:
- **CRITICAL addition**: Every progress update must include clickable hyperlinks
- Updated all example progress lines to show markdown link format: `[source name](URL)`
- Added link priority guidance:
  1. Direct page URL if fetched successfully
  2. Search URL used for fallback (show actual search that yielded results)
  3. Domain homepage if specific page unavailable

#### Verbatim quote capture:
- Updated format to: `"verbatim quote" — [source name, rating, brand](URL)`
- Emphasized capturing URLs alongside every quote
- URLs should go directly to the page where quote was found

#### Data organization buckets:
- Every bucket now explicitly requires "source + URL"
- Examples:
  - `PRAISE — what customers love (source + URL, ideally verbatim)`
  - `VERBATIM — strong exact quotes (source + URL, polarity, theme tag)`
  - `PRICING — exact price/size data (platform + URL, date)`
  - And all others follow same pattern

### 3. **STAGE3_REPORT.md** (Report generation)

#### Synthesis requirements:
- Added explicit requirement to capture source URLs for everything
- Every finding, quote, data point, and claim must have clickable source link

#### Insight quality criteria:
- **CRITICAL addition**: Every data point, quote, finding, and claim MUST include hyperlinked source citation
- Updated examples to show markdown link format throughout
- Examples now include: `"based on [18 Amazon.in reviews](URL)…"`

#### Section-specific updates:
- **Unmet Needs**: Sources must be linked inline: `[r/IndiaFitness threads](URL)`
- **Ad Language**: Format changed to `"phrase" — [source name](URL)`
- **Whitespace**: Price ranges and sources must be linked
- **Market**: Format as `[~₹33,000 Cr](URL1), [14% CAGR 2024–2030](URL2) (IMARC)`
- **Competition**: Positioning, price ranges, and funding all require source links

#### Quality checklist:
- Added requirement: "Every finding cites a source by name AND includes a clickable hyperlink"
- Added: "All Ad-Language quotes are actually verbatim and linked to their source"
- Added: "Customer voice quotes include attribution with [source link](URL) format"

### 4. **REPORT_TEMPLATE.md** (HTML/CSS specification)

#### Section specifications:
- **The Market**: Sources must be clickable hyperlinks on figures
- **The Competition**: All source references in profiles must be hyperlinks
- **The Customer**: Quote labels formatted as `[source name](URL) · [+/–/mixed] · [theme]`
- **Tables**: Platform names in pricing maps should link to actual product listings

#### Design system additions:
- Added CSS variables for link styling:
  - `--link:#1B2A4A` (navy, matches brand colour)
  - `--link-hover:#B7791F` (ochre accent on hover)
- Added complete hyperlink styling spec:
  ```css
  #report a{
    color:var(--link);
    text-decoration:underline;
    text-decoration-color:var(--line);
    text-underline-offset:0.15em;
    transition:color 0.15s, text-decoration-color 0.15s;
  }
  #report a:hover{
    color:var(--link-hover);
    text-decoration-color:var(--accent);
  }
  ```

#### Accessibility additions:
- All source links must have meaningful link text (not "click here" or bare URLs)
- Links must have visible underlines in body text
- Link colour must have sufficient contrast (AA standard)
- `:focus` state must be clearly visible (ochre outline)

#### Print/PDF updates:
- **CRITICAL**: Added CSS to display full URLs after link text in print: 
  ```css
  #report a[href^="http"]:after{ 
    content:" (" attr(href) ")"; 
    font-size:9pt; 
    color:#666; 
  }
  ```
- This ensures founders can access sources from printed reports

#### Data quality display:
- Updated all examples to show hyperlinked format
- Strong data: `[source name](URL)`
- Partial: `(partial — [search fallback](search-URL))`
- Unavailable: `[source](attempted-URL) could not be accessed`
- Conflicting: `[Amazon reviews](URL1) suggest X; [Reddit](URL2) suggests Y`

### 5. **STAGE1_PLAN.md** (Planning phase)
- Added note that findings will be linked during extraction and in final report
- Updated example plan to mention: "Every finding will be linked to its source so you can verify and explore"

## Implementation Impact

### For Chat Progress Updates (Stage 2):
Every source fetch now appears with a clickable link:
```
🔍 [Amazon.in (Yoga Bar)](https://amazon.in/s?k=yoga+bar) ✓ — findings...
```

### For Report Content (Stage 3):
Every citation is now a hyperlink:
- Market figures: `[₹33,000 Cr](URL)`
- Customer quotes: `"quote" — [Amazon.in](URL)`
- Competitor data: `[Series A funding](URL)`
- Pricing: Platform names link to listings

### For PDF/Print:
URLs automatically appear after link text in parentheses, making sources accessible from printed reports.

## Quality Enforcement

The skill now enforces source linking through:
1. **Progress notation requirements** — won't pass review without links
2. **Verbatim capture format** — URL is part of the required format
3. **Report quality checklist** — explicit checkbox for hyperlinked sources
4. **HTML template spec** — styling and structure expect links
5. **Data organization** — every bucket requires "source + URL"

## Result

Every finding in the skill output (chat and report) is now traceable to a clickable source, enabling founders to:
- Verify evidence independently
- Explore source context
- Build their own intuition from raw data
- Access sources from printed reports via inline URLs
