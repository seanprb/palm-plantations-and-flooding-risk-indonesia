# CLAUDE.MD -- Applied Econometrics Research with Claude Code

**Project:** To what extent do Palm Oil Plantations affect risk of flooding? Evidence from Indonesia
**Institution:** [YOUR INSTITUTION]
**Branch:** main

---

## Core Principles

- **Plan first** -- enter plan mode before non-trivial tasks; save plans to `quality_reports/plans/`
- **Verify after** -- compile and confirm output at the end of every task
- **Single source of truth** -- Paper `main.tex` is authoritative; talks and supplements derive from it
- **Quality gates** -- weighted aggregate score; nothing ships below 80/100; see `quality.md`
- **Worker-critic pairs** -- every creator has a paired critic; critics never edit files
- **[LEARN] tags** -- when corrected, save `[LEARN:category] wrong → right` to MEMORY.md

---

## Getting Started

1. Fill in `[YOUR INSTITUTION]` above
2. Run `/discover interview` to refine the research specification
3. Or continue with `/discover data` to identify datasets
4. Then `/strategize` to design the identification strategy

---

## Folder Structure

```
palm-oil-flooding-indonesia/
├── CLAUDE.MD                    # This file
├── .claude/                     # Rules, skills, agents, hooks
├── Bibliography_base.bib        # Centralized bibliography
├── Paper/                       # Main LaTeX manuscript (source of truth)
│   ├── main.tex                 # Primary paper file
│   └── sections/                # Section-level .tex files
├── Talks/                       # Derivative Beamer presentations
│   ├── job_market_talk.tex
│   ├── seminar_talk.tex
│   ├── short_talk.tex
│   └── lightning_talk.tex
├── Data/                        # Project data
│   ├── raw/                     # Original untouched data (gitignored)
│   └── cleaned/                 # Processed datasets ready for analysis
├── Output/                      # Intermediate results (logs, temp files)
├── Figures/                     # Final figures (.pdf, .png) referenced in paper
├── Tables/                      # Final tables (.tex) referenced in paper
├── Supplementary/               # Online appendix and supplements
├── Replication/                 # Replication package for deposit
├── Preambles/header.tex         # LaTeX headers / shared preamble
├── scripts/                     # Analysis code (R, Stata, Python, Julia)
├── quality_reports/             # Plans, session logs, reviews, scores
├── explorations/                # Research sandbox
├── templates/                   # Session log, quality report templates
└── master_supporting_docs/      # Reference papers and data docs
```

---

## Commands

```bash
# Paper compilation (3-pass, XeLaTeX only)
cd Paper && TEXINPUTS=../Preambles:$TEXINPUTS xelatex -interaction=nonstopmode main.tex
BIBINPUTS=..:$BIBINPUTS bibtex main
TEXINPUTS=../Preambles:$TEXINPUTS xelatex -interaction=nonstopmode main.tex
TEXINPUTS=../Preambles:$TEXINPUTS xelatex -interaction=nonstopmode main.tex

# Talk compilation
cd Talks && TEXINPUTS=../Preambles:$TEXINPUTS xelatex -interaction=nonstopmode talk.tex
```

---

## Quality Thresholds

| Score | Gate | Applies To |
|-------|------|------------|
| 80 | Commit | Weighted aggregate (blocking) |
| 90 | PR | Weighted aggregate (blocking) |
| 95 | Submission | Aggregate + all components >= 80 |
| -- | Advisory | Talks (reported, non-blocking) |

See `quality.md` for weighted aggregation formula.

---

## Skills Quick Reference

| Command | What It Does |
|---------|-------------|
| `/new-project [topic]` | Full pipeline: idea → paper (orchestrated) |
| `/discover [mode] [topic]` | Discovery: interview, literature, data, ideation |
| `/strategize [question]` | Identification strategy or pre-analysis plan |
| `/analyze [dataset]` | End-to-end data analysis |
| `/write [section]` | Draft paper sections + humanizer pass |
| `/review [file/--flag]` | Quality reviews (routes by target: paper, code, peer) |
| `/revise [report]` | R&R cycle: classify + route referee comments |
| `/talk [mode] [format]` | Create, audit, or compile Beamer presentations |
| `/submit [mode]` | Journal targeting → package → audit → final gate |
| `/tools [subcommand]` | Utilities: commit, compile, validate-bib, journal, etc. |

---

## Beamer Custom Environments (Talks)

| Environment       | Effect        | Use Case       |
|-------------------|---------------|----------------|
| `[your-env]`      | [Description] | [When to use]  |

---

## Current Project State

| Component | File | Status | Description |
|-----------|------|--------|-------------|
| Literature Review | `quality_reports/lit_review_palm-oil-flooding.md` | complete | /discover --lit completed 2026-03-15 |
| Research Spec | `quality_reports/research_spec_palm-oil-flooding.md` | not started | Run /discover interview |
| Data Discovery | `quality_reports/data_exploration_palm-oil-flooding.md` | not started | Run /discover data |
| Strategy Memo | `quality_reports/strategy_memo.md` | not started | Run /strategize |
| Paper | `Paper/main.tex` | not started | |
| Data | `scripts/` | not started | |
| Replication | `Replication/` | not started | |
| Job Market Talk | `Talks/job_market_talk.tex` | not started | |
