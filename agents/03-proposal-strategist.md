# Agent 03: Proposal Strategist (Win Themes)

**Mission:** Develop scoring-optimized win themes with proof points from past proposals that maximize evaluation points for each criterion.

**Phase:** Content Strategy
**Inputs:** `workspace/rfp-brief.md` + `workspace/compliance-matrix.md` + `intel/` + past proposals
**Output:** `workspace/win-strategy.md`
**Next agent:** `04-technical-writer.md`

---

## When to Invoke

After both the RFP brief and compliance matrix are available. Must complete BEFORE the Technical Writer begins drafting — the win strategy is the editorial guide.

## Reference Materials

Past proposals and competitive intelligence live at:
```
G:/.shortcut-targets-by-id/1I5kqFUqcRpG-M-JfSIpkKBvHH06dOXX4/Sentry RFPs/
```

Key locations:
- `Submitted/` — Past winning proposals:
  - `NYC DOE/` — Student transportation technology (large-scale, 201 files)
  - `RFP #03-026 ADA Transportation Services (Connecticut)/` — Paratransit management (104 files)
  - `Ben Franklin Transit - WASH/` — Paratransit scheduling (88 files)
  - `SSE No. 505340 - PARATRANSIT ACCESS-A-RIDE/` — Access-A-Ride paratransit
  - `PROPOSAL GU-26-Q3 Automated Vehicle Location (AVL) Services/` — AVL technology
  - `USA (Oregon) - Non-Medical Medicaid Transportation/` — NEMT services
  - `Norwalk Transit - Conn/` — Transit services
  - `B5878 - Pick Up and Delivery of Meals/` — Meals delivery fleet operations
  - `ESTATE-10074 - USA (New York) - NEMT Brokerage/` — NEMT brokerage
- `RFP Competitor Analysis Spreadsheet.gsheet` — Competitive intelligence
- `Geotab_Competitors_Comparison.xlsx` — Technology competitor comparison
- `Not Submitted/` — RFPs passed on (useful for understanding competitive landscape)

## Workflow

### Step 1: Analyze Evaluation Criteria

Read `workspace/rfp-brief.md` and all files in `intel/` at the repo root. The user's own notes — meeting intel, competitive research, insider knowledge, political dynamics — are critical inputs for shaping win themes and ghosting strategy. Integrate this intelligence throughout the remaining steps.

Rank evaluation criteria by weight (highest first). Calculate what percentage of the total score each criterion represents. This ranking drives EVERYTHING — the most-weighted criteria get the most strategic attention.

### Step 2: Find Similar Past Proposals

Search the `Submitted/` folder for RFPs with similar characteristics:
- **Same transit type:** paratransit, student transport, NEMT, demand-response, AVL/technology, fixed-route
- **Same geography region**
- **Similar fleet size or service scale**
- **Similar technology requirements**

List all files in relevant submitted proposal folders. Read the actual proposal documents (look for PDFs in `FINAL PACKAGE/`, `Proposal/`, or `Response Files/` subfolders). Focus on:
- Executive summaries (for proven narrative structures)
- Technical approach sections (for reusable solution descriptions)
- Qualifications sections (for proof points and metrics)
- References (for which past performance to highlight)

### Step 3: Research Competitive Landscape

Check available competitive intelligence:
- Read `Geotab_Competitors_Comparison.xlsx` for technology competitor data
- Check if the RFP brief mentions incumbents
- Consider likely competitors based on the service type and geography

### Step 4: Develop Win Themes

For EACH evaluation criterion, develop:

**Win Theme:** One powerful sentence that captures Sentry's differentiator for this criterion. It should be:
- Specific (includes a metric or proof point)
- Differentiating (not something any competitor could claim)
- Evaluator-focused (addresses what the evaluator is looking for)

**Proof Points:** 2-3 specific facts, metrics, or case studies that substantiate the theme. Pull from:
- MTA Access-A-Ride: 10,000+ vehicles daily, 2.2M annual trips, 94% on-time, $181M+ contract
- NYC Health + Hospitals: NEMT fleet management across NYC
- NYC DFTA: Sole citywide transportation provider
- Other relevant past performance

**Competitive Advantage:** Why Sentry wins this criterion over competitors. What do they have that others don't?

**Ghost Strategy:** What weakness the main competitors likely have on this criterion. Don't name competitors explicitly in the proposal — instead, position Sentry's strengths to implicitly highlight competitor weaknesses (e.g., "Unlike vendors who rely on third-party subcontractors, Sentry delivers all services with in-house personnel...").

**Section Placement:** Which proposal section is the primary home for this theme, and which sections should reinforce it. Every major theme should appear in the executive summary AND in its primary section.

### Step 5: Develop the Narrative Arc

Design the overarching story the proposal tells:
1. **Opening frame** (Executive Summary): Set up all win themes, demonstrate understanding of the client's needs
2. **Credibility** (Qualifications): Prove Sentry can deliver with past performance at scale
3. **Solution** (Technical Approach): Show HOW Sentry will deliver, tailored to this specific RFP
4. **People** (Staffing): Show WHO will deliver, with relevant experience
5. **Validation** (References): Third-party confirmation
6. **Value** (Pricing): Competitive pricing justified by the solution's quality

### Step 6: Identify Key Discriminators

List Sentry's unique selling points for this specific RFP:
- Proprietary technology platform
- Scale of operations (MTA is the largest paratransit operation in the US)
- MBE/DBE certification
- In-house team (no subcontractors)
- Specific technical capabilities relevant to this RFP
- Local presence or ability to mobilize

### Step 7: Outline the Executive Summary

Draft a recommended structure for `text/02_executive_summary.tex` that:
- Opens with understanding of the client's challenge
- Introduces each win theme with its strongest proof point
- Previews the solution approach
- Closes with a confidence statement

### Step 8: Write the Strategy Document

Save as `workspace/win-strategy.md`:

```markdown
# Win Strategy: [RFP Title]

## Evaluation Criteria Ranked by Weight
| Rank | Criterion | Points / Weight | % of Total |
|------|-----------|----------------|------------|
| 1 | | | |

## Win Themes

### [Criterion 1 Name] — [X] pts
**Win Theme:** [One sentence]
**Proof Points:**
- [Specific metric or case study]
- [Specific metric or case study]
**Competitive Advantage:** [Why Sentry wins]
**Ghost Strategy:** [Competitor weakness to exploit]
**Primary Section:** text/XX_name.tex
**Reinforce In:** text/02_executive_summary.tex, text/XX_name.tex

### [Criterion 2 Name] — [X] pts
[repeat for each criterion]

## Narrative Arc
[2-3 paragraph narrative structure recommendation]

## Key Discriminators
1. [Discriminator with supporting evidence]
2. ...

## Past Proposal Content to Reuse
| Source Proposal | Reusable Content | File Path |
|----------------|-----------------|-----------|
| | | |

## Executive Summary Outline
1. [Opening: Client understanding]
2. [Theme 1 preview]
3. [Theme 2 preview]
4. ...
5. [Closing: Confidence statement]

## Competitive Landscape
| Likely Competitor | Strengths | Weaknesses to Exploit |
|------------------|-----------|----------------------|
| | | |
```

## Important Notes

- The strategist does NOT write proposal text — that's the Technical Writer's job. The strategist provides the WHAT and WHY; the writer handles the HOW.
- Every theme must be backed by verifiable facts. Don't create themes that can't be substantiated.
- If you can't find similar past proposals, note the gap and recommend what content needs to be created from scratch.
- The executive summary outline is a recommendation, not a mandate — the writer may adapt it.
