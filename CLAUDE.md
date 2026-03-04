## Agent Team

This repo includes 6 specialized AI agent personas in `agents/`. Each agent
handles a specific phase of the RFP lifecycle. To invoke an agent:

> Act as the RFP Analyst. The RFP is at [path].

Or read the file directly:

> Read agents/01-rfp-analyst.md and follow those instructions.

### Agents

| # | Agent | File | Shorthand | Output |
|---|-------|------|-----------|--------|
| 01 | RFP Analyst | `agents/01-rfp-analyst.md` | "RFP Analyst" / "Sleuther" | `workspace/rfp-brief.md` |
| 02 | Compliance Officer | `agents/02-compliance-officer.md` | "Compliance Officer" | `workspace/compliance-matrix.md` |
| 03 | Proposal Strategist | `agents/03-proposal-strategist.md` | "Strategist" / "Win Themes" | `workspace/win-strategy.md` |
| 04 | Technical Writer | `agents/04-technical-writer.md` | "Writer" | `text/*.tex` files |
| 05 | Cost Estimator | `agents/05-cost-estimator.md` | "Cost Estimator" / "Pricing" | `workspace/pricing-notes.md` |
| 06 | Red Team Reviewer | `agents/06-red-team-reviewer.md` | "Red Team" / "Reviewer" | `workspace/review-report.md` |

### Lifecycle

```
RFP Document
    |
    v
01 RFP Analyst ---------> workspace/rfp-brief.md
    |
    v
02 Compliance Officer ---> workspace/compliance-matrix.md
    |
    v
03 Proposal Strategist --> workspace/win-strategy.md
    |
    v
04 Technical Writer -----> text/*.tex (actual proposal)
    |
    v
05 Cost Estimator -------> text/07_pricing.tex + workspace/pricing-notes.md
    |
    v
06 Red Team Reviewer ----> workspace/review-report.md
    |
    v
Fix issues -> Re-invoke Writer -> Re-invoke Red Team -> Submit
```

### Workspace

Agent outputs accumulate in `workspace/`. This directory is per-RFP — each
cloned repo gets its own workspace.

| File | Producer | Consumers |
|------|----------|-----------|
| `rfp-brief.md` | 01 Analyst | All agents |
| `compliance-matrix.md` | 02 Compliance | 03, 04, 06 |
| `win-strategy.md` | 03 Strategist | 04, 06 |
| `pricing-notes.md` | 05 Cost Estimator | 04, 06 |
| `review-report.md` | 06 Red Team | User, 04 (for fixes) |

### RFP Source Documents

Drop the raw RFP files (PDFs, DOCX, addenda, cost templates) into
`rfp-source/` at the repo root. All agents check here first.

### Intel (Your Notes & Research)

Drop your own notes into `intel/` at the repo root. All agents read this
directory before starting their work. Put anything you want factored in:

- Meeting notes with the agency, incumbent, or partners
- Your own OSINT / web research
- Competitive intel, pricing benchmarks, insider knowledge
- Staffing constraints, political dynamics, bid strategy notes

Use any format (`.md`, `.txt`, `.docx`, `.pdf`). Name files descriptively.

### Contact Person

**Max Zinner** is the authorized representative, contact for clarifications,
and signatory on all transmittal letters. His name is pre-filled in
`text/01_transmittal.tex`.

---

## Reference Materials
Our past proposals, resumes, and capability statements live in the
local Google Drive sync at:
  G:\.shortcut-targets-by-id\1I5kqFUqcRpG-M-JfSIpkKBvHH06dOXX4\Sentry RFPs

When drafting any section, search this folder first for:
- Past performance narratives
- Key personnel resumes
- Previously winning technical approaches
- Pricing references

Read these files directly using the filesystem.

## LaTeX Template Structure

This repo is a **template** for generating RFP proposal PDFs. Each new RFP
should be created by cloning this repo and customizing the files below.

### Files

| File | Purpose |
|------|---------|
| `main.tex` | Entry point. **RFP variables live at the top** — update them first. |
| `package.tex` | All LaTeX packages, colors, custom commands. Rarely needs changes. |
| `compile.bat` | Runs `pdflatex` twice (for TOC). Just double-click to build. |
| `rfp-source/` | Drop raw RFP docs here (PDFs, addenda, cost templates). |
| `intel/` | Your notes, meeting intel, OSINT, research. All agents read this. |
| `workspace/` | Agent outputs land here. |
| `agents/*.md` | AI agent personas — one per lifecycle phase. |
| `img/sentry-logo-new.jpg` | Company logo (used in header + title page). |
| `img/client-logo.*` | Drop the client's logo here (`.png`, `.jpg`, `.jpeg`, or `.pdf`); title page auto-detects. |
| `text/01_transmittal.tex` | Cover / transmittal letter. |
| `text/02_executive_summary.tex` | Executive summary. |
| `text/03_qualifications.tex` | Company overview, experience, expertise. |
| `text/04_technical_approach.tex` | Technical solution, architecture, timeline, risks. |
| `text/05_staffing.tex` | Key personnel and resource allocation. |
| `text/06_references.tex` | Past performance / client references. |
| `text/07_pricing.tex` | Cost components and pricing structure. |
| `text/08_appendices.tex` | Appendix checklist. |

### How to Use This Template

1. **Set the RFP variables** at the top of `main.tex`:
   ```latex
   \newcommand{\rfpTitle}{RFP \#000}
   \newcommand{\rfpSubtitle}{Lorem Ipsum Dolor Sit Amet Service}
   \newcommand{\rfpDocType}{Technical Proposal}
   \newcommand{\clientName}{Agency Name}
   \newcommand{\clientDepartment}{Department of Lorem Ipsum}
   \newcommand{\clientDivision}{Dolor Sit Amet Division}
   ```

2. **Add or remove sections** in `main.tex` by adding/removing `\input{text/...}`
   lines. Each RFP dictates its own structure — the 8 example sections are
   starting points, not fixed requirements. Rename, reorder, split, or merge
   them as needed.

3. **Replace Lorem Ipsum** in each `text/*.tex` file with actual proposal
   content. Use `\placeholder{text}` for fields that still need filling.

4. **Drop a client logo** at `img/client-logo.png` (or `.jpg`, `.jpeg`, `.pdf`).
   The title page auto-detects the format and gracefully skips if none is found.

5. **Search reference materials** in the Google Drive folder (see above) for
   reusable content: past performance narratives, resumes, technical
   approaches, and pricing.

6. **Compile** by running `compile.bat` or:
   ```
   pdflatex -interaction=nonstopmode main.tex
   pdflatex -interaction=nonstopmode main.tex
   ```

### Available Formatting Features

Use these in any section file:

- **Tables with dark-blue headers:**
  ```latex
  \begin{tabularx}{\textwidth}{|>{\bfseries}l|X|}
  \hline
  \rowcolor{tableHeader}\multicolumn{2}{|l|}{\textcolor{white}{\textbf{Title}}} \\
  \hline
  Key & Value \\ \hline
  \end{tabularx}
  ```

- **Sidebar callout boxes:**
  ```latex
  \begin{sidebar}{Title}
  Content here.
  \end{sidebar}
  ```

- **Gradient colored boxes:**
  ```latex
  \mybox{Content here.}{MidnightBlue}
  ```

- **Placeholder text** (gray italic):
  ```latex
  \placeholder{Fill this in later}
  ```

- **Requirement references** (bold MidnightBlue):
  ```latex
  \reqref{\S3.4.1}
  ```

- **Font Awesome icons:**
  ```latex
  \faIcon{bus}  \faIcon{check-circle}  \faIcon{lock}
  ```

- **Description lists with icons:**
  ```latex
  \begin{description}[style=nextline, leftmargin=0.5cm]
      \item[\faIcon{server} \textbf{Title}] Description text.
  \end{description}
  ```

- **Requirements traceability tables** (longtable for multi-page):
  ```latex
  \begin{longtable}{|p{0.8cm}|p{4cm}|p{9cm}|}
  \hline
  \rowcolor{tableHeader}
  \textcolor{white}{\textbf{Req}} & \textcolor{white}{\textbf{Requirement}} & \textcolor{white}{\textbf{Solution}} \\
  \hline \endfirsthead
  A & Requirement & Solution \\ \hline
  \end{longtable}
  ```

- **TikZ diagrams** (data flow, Gantt timelines) — see `04_technical_approach.tex`
  for working examples.

### Brand Colors

| Name | Value | Use |
|------|-------|-----|
| `sentryBlue` | `#003366` | Company brand |
| `MidnightBlue` | (xcolor built-in) | Section headings, accents |
| `tableHeader` | `RGB(0, 51, 102)` | Table header backgrounds |
