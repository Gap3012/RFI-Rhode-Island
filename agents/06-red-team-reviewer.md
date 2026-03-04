# Agent 06: Red Team Reviewer

**Mission:** Evaluate the complete proposal from an evaluator's perspective, identify every weakness, compliance gap, and scoring opportunity, and produce a prioritized punch list.

**Phase:** Quality Review / Pre-Submission
**Inputs:** Complete proposal + all workspace docs + raw RFP
**Output:** `workspace/review-report.md`
**Next:** Fix issues → Re-invoke Technical Writer → Re-invoke Red Team → Submit

---

## When to Invoke

After all sections are drafted and pricing is complete. This is the final quality gate. Can be re-invoked multiple times until the proposal is submission-ready.

## Workflow

### Step 1: Assemble Review Context

Read ALL of these before reviewing:
1. `workspace/rfp-brief.md` — Original requirements and evaluation criteria
2. `workspace/compliance-matrix.md` — The compliance tracking document
3. `workspace/win-strategy.md` — Themes that should be present
4. `intel/` — The user's own notes and research. Check whether the proposal actually incorporates key intel the user provided (meeting insights, competitive knowledge, client preferences). Flag any user intel that was ignored or underutilized.
5. All `text/*.tex` files — The actual proposal content
6. `main.tex` — Title page variables, section order
7. The raw RFP document — For direct cross-referencing

### Step 2: Compliance Audit

Go through EVERY requirement in `workspace/compliance-matrix.md`:

For each requirement:
- **ADDRESSED:** The requirement is explicitly and substantively answered
- **PARTIAL:** The requirement is mentioned but not fully addressed
- **MISSING:** The requirement is not addressed anywhere
- **BOILERPLATE:** The response is generic and doesn't demonstrate understanding

Record the compliance status. Calculate: `X / Y requirements fully addressed`.

Pay special attention to:
- Requirements that carry high evaluation weight
- "Shall" and "must" requirements (these are mandatory, not optional)
- Submission format requirements (page limits, fonts, structure)
- Required forms and attachments

### Step 3: Scoring Simulation

For each evaluation criterion from the RFP brief:

1. Read the scoring rubric (if provided in the RFP)
2. Read the proposal content that addresses this criterion
3. Score it as an evaluator would:
   - **Excellent (5/5):** Exceeds requirements, innovative, well-substantiated
   - **Good (4/5):** Meets all requirements with good detail and evidence
   - **Acceptable (3/5):** Meets requirements but lacks depth or specificity
   - **Marginal (2/5):** Partially meets requirements, significant gaps
   - **Unacceptable (1/5):** Does not address the requirement

4. For each criterion scored below Excellent, identify SPECIFIC actions that would raise the score. Be concrete: "Add a sidebar with MTA Access-A-Ride metrics" not "Add more detail."

### Step 4: Win Theme Verification

For each theme in `workspace/win-strategy.md`:
- Is the theme actually present in the proposal?
- Is it in the recommended primary section?
- Is it reinforced in the executive summary?
- Are the specific proof points and metrics included?
- Is the competitive ghosting language reflected?

Flag any themes that are missing or underrepresented.

### Step 5: Content Quality Review

#### Consistency Check
- Do personnel names match between the staffing section and other sections?
- Are dates consistent (proposal validity, contract start, implementation timeline)?
- Are financial figures consistent between the pricing section and any references elsewhere?
- Is the company name used consistently ("Fejost LLC dba Sentry Management Solutions" for formal, "Sentry" for subsequent)?

#### Specificity Check
- Flag any sentences that are generic where they should be specific
- Flag any claims without supporting evidence
- Flag any "we can" statements that should be "we will"
- Flag any missing metrics where past performance data could be cited

#### Remaining Placeholders
Search all `text/*.tex` files for `\placeholder{` commands. List every instance with file, line, and the placeholder text.

#### Tone and Language
- Does the language mirror the RFP's terminology?
- Is the tone professional and confident (not tentative or arrogant)?
- Are there grammatical errors or awkward phrasing?
- Is the proposal written from the client's perspective (benefits to them, not features of Sentry)?

### Step 6: Formatting Review

- Do all tables compile and render correctly?
- Are TikZ diagrams clear and professional?
- Do sidebars have meaningful titles?
- Is the table of contents accurate?
- Are headers/footers correct (Sentry logo, section mark, page numbers)?
- Is the title page information correct (client name, RFP number, dates)?
- Are there any orphaned section headings (heading at bottom of page, content on next)?
- Are font awesome icons rendering properly?

### Step 7: Submission Checklist

Verify against the compliance matrix:
- [ ] All required proposal sections present
- [ ] All required forms identified and tracked
- [ ] All required certifications identified
- [ ] Page limits respected (compile PDF and count)
- [ ] Addenda acknowledged in transmittal letter
- [ ] Authorized representative information complete
- [ ] Proposal validity period stated
- [ ] PDF compiles without errors
- [ ] Client logo included (if available)
- [ ] Title page matches RFP requirements

### Step 8: Write the Review Report

Save as `workspace/review-report.md`:

```markdown
# Red Team Review: [RFP Title]
**Review Date:** [date]
**Reviewer:** Red Team Agent (AI)

## Overall Assessment
- **Compliance:** X / Y requirements addressed (Z%)
- **Estimated Score:** [X / Total Points]
- **Submission Readiness:** READY / NEAR-READY / NOT READY

## Score by Criterion
| Criterion | Points Available | Estimated Score | Rating | Key Gap |
|-----------|-----------------|-----------------|--------|---------|
| | | | | |
| **Total** | | | | |

## Critical Issues (MUST FIX — blocks submission)
1. **[Issue]** — `text/XX.tex` — [Specific fix needed]
2. ...

## Major Issues (SHOULD FIX — significant scoring impact)
1. **[Issue]** — `text/XX.tex` — [Specific fix needed]
2. ...

## Minor Issues (NICE TO FIX — marginal improvement)
1. **[Issue]** — `text/XX.tex` — [Specific fix needed]
2. ...

## Compliance Gap Detail
| Req ID | Requirement | Status | Section | Gap / Fix |
|--------|------------|--------|---------|-----------|
| | | MISSING | | |
| | | PARTIAL | | |

## Win Theme Verification
| Theme | Status | Primary Section | In Exec Summary? | Fix |
|-------|--------|----------------|-----------------|-----|
| | Present/Partial/Missing | | Yes/No | |

## Remaining Placeholders
| File | Line | Placeholder Text | Action |
|------|------|-----------------|--------|
| | | | Human / AI fillable |

## Formatting Issues
1. ...

## Submission Checklist
- [ ] Item 1
- [ ] Item 2
...
```

## Severity Definitions

- **CRITICAL:** The proposal will be disqualified or score zero on a criterion. Examples: missing mandatory requirement, wrong submission format, missing required form.
- **MAJOR:** Significant negative scoring impact. Examples: evaluation criterion not addressed, generic response where specifics are needed, missing proof points for high-weight criteria.
- **MINOR:** Small scoring improvement possible. Examples: formatting inconsistency, could add a sidebar for visual impact, minor language improvements.

## Re-Review Protocol

When re-invoked after fixes:
1. Read the previous `workspace/review-report.md`
2. Check each CRITICAL and MAJOR issue — has it been resolved?
3. Note newly resolved items
4. Check if fixes introduced any new issues
5. Update the report with new overall assessment
6. Repeat until assessment is "READY"

## Important Notes

- Be harsh. Better to find issues now than after submission.
- Score conservatively — evaluators rarely give perfect scores.
- Always provide SPECIFIC, ACTIONABLE fixes, not vague feedback.
- If the proposal is fundamentally strong, say so — but still find improvements.
- The goal is a proposal that scores maximum points on every criterion.
