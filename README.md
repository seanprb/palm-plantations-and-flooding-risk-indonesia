# Palm Plantations and Flooding Risk in Indonesia

An Independent Study looking at the causal effects of Palm Plantations on Flooding Risk in Indonesia using [clo-author](https://github.com/seanprb/clo-author), a set of specialised AI agents customised for the purpose of economic research.

---

## Folder Structure

```
palm-oil-flooding-indonesia/
│
├── CLAUDE.md                        # Project configuration and agent instructions
├── MEMORY.md                        # Persistent project memory and learnings
├── Bibliography_base.bib            # Centralised bibliography
│
├── Paper/                           # Main LaTeX manuscript (source of truth)
│   ├── main.tex                     # Primary paper file
│   └── sections/                    # Section-level .tex files
│
├── Talks/                           # Derivative Beamer presentations
│
├── Data/
│   ├── raw/                         # Original untouched data (gitignored)
│   └── cleaned/                     # Processed datasets ready for analysis
│
├── scripts/                         # Analysis code (R, Stata, Python)
├── Figures/                         # Final figures (.pdf, .png)
├── Tables/                          # Final tables (.tex)
├── Output/                          # Intermediate results and logs
├── Supplementary/                   # Online appendix and supplements
├── Replication/                     # Replication package for deposit
├── Preambles/                       # Shared LaTeX headers
│
├── explorations/                    # Research sandbox and experimental work
├── master_supporting_docs/          # Reference papers and data documentation
├── templates/                       # Session log, quality report, skill templates
│
├── quality_reports/                 # Quality assurance outputs
│   ├── lit_review_palm-oil-flooding.md   # Literature review
│   ├── research_journal.md          # Append-only agent activity log
│   ├── plans/                       # Session plans (YYYY-MM-DD_description.md)
│   ├── session_logs/                # Per-session detailed logs
│   ├── specs/                       # Requirements specifications
│   └── merges/                      # Quality reports generated at merge time
│
└── .claude/                         # clo-author infrastructure
    ├── agents/                      # Specialised agent definitions
    ├── rules/                       # Governing rules and protocols
    ├── skills/                      # Slash-command skill definitions
    └── hooks/                       # Lifecycle automation hooks
```

---

## Agent System

This project uses **clo-author** — a multi-agent research system built on Claude Code. Agents operate in adversarial worker-critic pairs:

| Worker | Critic | Role |
|--------|--------|------|
| librarian | librarian-critic | Literature search and annotation |
| explorer | explorer-critic | Data sourcing and feasibility |
| strategist | strategist-critic | Identification strategy design |
| coder | coder-critic | Empirical analysis and scripts |
| writer | writer-critic | Manuscript drafting |
| storyteller | storyteller-critic | Presentation design |

## Key Skills

| Command | Description |
|---------|-------------|
| `/discover --lit [topic]` | Literature review |
| `/discover --data` | Data source identification |
| `/strategize` | Identification strategy design |
| `/analyze` | End-to-end data analysis |
| `/write [section]` | Draft paper sections |
| `/review` | Simulated peer review |

## Current Status

| Component | File | Status |
|-----------|------|--------|
| Literature Review | `quality_reports/lit_review_palm-oil-flooding.md` | Started |
| Research Specification | `quality_reports/research_spec_palm-oil-flooding.md` | Not started |
| Data Discovery | `quality_reports/data_exploration_palm-oil-flooding.md` | Not started |
| Strategy Memo | `quality_reports/strategy_memo.md` | Not started |
| Analysis Scripts | `scripts/` | Not started |
| Paper | `Paper/main.tex` | Not started |
