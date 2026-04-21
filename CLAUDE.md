# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

**AlcHep — Alcoholic Hepatitis vs. Non-AH in the HARMONY Terlipressin Registry**

Sub-project of the HARMONY Terlipressin Registry. Compares clinical characteristics and 90-day mortality (as a competing risk against liver transplant) between patients with and without alcoholic hepatitis (`etoh_hepatitis`) who received terlipressin for HRS-AKI.

Shared context (master dataset path, derived variables, conventions) lives in the parent `/Users/to909/Desktop/Terlipressin projects/CLAUDE.md` — do not duplicate that content here.

## Data Request

- `Requests/AlcHep Data Request 04162026.docx` — current (supersedes 01292026 version)

## Repository Layout

- `Code/` — placeholder for auxiliary scripts (empty)
- `Requests/` — data-request docs from collaborators
- `Results/` — CSV exports of tables (e.g. `Table1_etoh_hepatitis.csv`)
- `docs/` — Quarto site (analysis + docs); symlinks `redcap_variables.qmd` and `derived_variables.qmd` back to the shared docs in `Terlipressin/docs/`

## Analyses (from 04162026 request)

1. **Table 1** — Demographics and clinical characteristics stratified by `etoh_hepatitis` (AH vs. non-AH)
2. **Unadjusted Fine-Gray** — 90-day cumulative incidence of mortality, with liver transplant as the competing risk, comparing AH vs. non-AH
3. **Adjusted Fine-Gray (MELD 3.0)** — covariates: `age`, `sex_male`, `hispanic`, `admit_meld_3`, `etoh_hepatitis`
4. **Adjusted Fine-Gray (ACLF)** — covariates: `age`, `sex_male`, `hispanic`, `aclf_grade`, `etoh_hepatitis`

The primary exposure throughout is `etoh_hepatitis`. The competing-risk outcome uses the shared pipeline variables `time_to_death_90days_cmp` / `time_to_death_status_90days_cmp`.

## Rendering

```bash
quarto render "/Users/to909/Desktop/Terlipressin projects/AlcHep/docs"
open "/Users/to909/Desktop/Terlipressin projects/AlcHep/docs/_site/index.html"
```

