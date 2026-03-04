# Sentry RFP Template

LaTeX template for generating professional RFP proposal PDFs for
Sentry Management Solutions (Fejost LLC).

## Quick Start

1. Create a new repo from this template (or clone it)
2. Drop the raw RFP documents into `rfp-source/` (PDFs, addenda, cost templates)
3. Drop a client logo at `img/client-logo.png` (or `.jpg`, `.jpeg`, `.pdf`) — optional
4. Edit the variables at the top of `main.tex` (RFP title, client name, etc.)
5. Add/remove/rename section files in `text/` to match the RFP's required structure
6. Replace placeholder content with actual proposal text
7. Run `compile.bat` to build the PDF

## Project Structure

```
├── main.tex              Main document — RFP variables at the top
├── package.tex           Packages, colors, custom commands (rarely edit)
├── compile.bat           Build script (runs pdflatex twice for TOC)
├── CLAUDE.md             Instructions for Claude Code AI assistant
├── rfp-source/           Drop raw RFP docs here (gitignored)
├── agents/               AI agent personas for each RFP lifecycle phase
│   ├── 01-rfp-analyst.md         Extracts requirements from raw RFP
│   ├── 02-compliance-officer.md  Maps requirements to sections
│   ├── 03-proposal-strategist.md Develops win themes & scoring strategy
│   ├── 04-technical-writer.md    Drafts LaTeX proposal content
│   ├── 05-cost-estimator.md      Develops pricing & cost analysis
│   └── 06-red-team-reviewer.md   Reviews from evaluator's perspective
├── workspace/            Agent outputs (per-RFP, populated during work)
├── img/
│   ├── sentry-logo-new.jpg   Sentry logo (header + title page)
│   └── client-logo.*          Client logo (png/jpg/jpeg/pdf, add per-RFP)
└── text/
    ├── 01_transmittal.tex         Cover letter
    ├── 02_executive_summary.tex   Executive summary
    ├── 03_qualifications.tex      Company qualifications & experience
    ├── 04_technical_approach.tex  Technical solution, timeline, risks
    ├── 05_staffing.tex            Key personnel & resource allocation
    ├── 06_references.tex          Past performance references
    ├── 07_pricing.tex             Cost components & pricing
    └── 08_appendices.tex          Appendix checklist
```

## Customizing Sections

The 8 sections above are **examples, not fixed requirements**. Every RFP
dictates its own format. To customize:

- **Add a section:** Create a new `text/XX_name.tex` file and add
  `\input{text/XX_name}` to `main.tex`
- **Remove a section:** Delete or comment out the `\input` line in `main.tex`
- **Reorder sections:** Move the `\input` lines in `main.tex`
- **Rename a section:** Change the `\section` title inside the `.tex` file

## Requirements

- A LaTeX distribution with `pdflatex` (e.g., MiKTeX on Windows, TeX Live on
  Linux/Mac)
- Required packages: `fontawesome5`, `tcolorbox`, `awesomebox`, `tikz`,
  `tabularx`, `longtable`, `fancyhdr`, `hyperref`, `etoc`, `enumitem`,
  `graphicx`, `xcolor`, `geometry`, `microtype`, `lmodern`

MiKTeX will auto-install missing packages on first compile.

## What's Gitignored

Only build artifacts and OS junk are excluded from version control.
Since each RFP gets its own repo, `rfp-source/`, `workspace/`, `intel/`,
and `main.pdf` are all committed for a complete archive.

- LaTeX build artifacts (`*.aux`, `*.log`, `*.toc`, `*.out`, etc.)
- OS files (`Thumbs.db`, `.DS_Store`, `desktop.ini`)

## Reference Materials

Past proposals, resumes, and capability statements are in the company
Google Drive under `Sentry RFPs/`. Check `Submitted/` for past winning
proposals to reuse content from.

## AI Agent Team

This repo includes 6 specialized AI agent personas in `agents/` that cover
the full RFP lifecycle. Each agent reads the instructions in its markdown
file and produces specific outputs to the `workspace/` directory.

### The Dream Team

| # | Agent | Role | Output |
|---|-------|------|--------|
| 01 | **RFP Analyst** | Reads the raw RFP, extracts every deadline, requirement, and evaluation criterion | `workspace/rfp-brief.md` |
| 02 | **Compliance Officer** | Maps requirements to proposal sections, tracks forms and certifications | `workspace/compliance-matrix.md` |
| 03 | **Proposal Strategist** | Develops win themes, competitive positioning, and scoring strategy | `workspace/win-strategy.md` |
| 04 | **Technical Writer** | Drafts polished LaTeX proposal sections using the full formatting arsenal | `text/*.tex` files |
| 05 | **Cost Estimator** | Develops pricing, cost narratives, and margin analysis | `workspace/pricing-notes.md` |
| 06 | **Red Team Reviewer** | Reviews the complete proposal from an evaluator's perspective | `workspace/review-report.md` |

### Workflow

1. Clone this repo for the new RFP
2. Run agents in order: Analyst → Compliance → Strategist → Writer → Pricing → Red Team
3. Fix issues from Red Team review
4. Re-run Writer and Red Team until ready
5. Submit

To invoke an agent with Claude Code:
```
Act as the RFP Analyst. The RFP is at [path to RFP folder].
```

See `CLAUDE.md` for full agent documentation and shorthand names.

## Using with Claude Code

This repo includes a `CLAUDE.md` with detailed instructions for the AI
assistant. Claude Code can:

- Run the full agent pipeline from RFP analysis through final review
- Draft new sections from scratch using reference materials
- Adapt the template structure to match a specific RFP's requirements
- Fill in placeholder content based on past proposals
- Add or modify TikZ diagrams, tables, and formatting elements
- Compile and verify the output PDF
