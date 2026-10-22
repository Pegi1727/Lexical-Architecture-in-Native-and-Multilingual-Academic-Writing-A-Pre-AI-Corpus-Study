# Reproducibility Package — Authoritative Three-File Analysis

## Permitted inputs (ONLY these)
1. `l1_corpus_openaccess_first_updated.csv` — 1,041 L1 article/project records, 12 columns
   (group, author_name, affiliation, doc_type, title, doi, source_url, landing_url, text, notes, has_fulltext, word_count), 40 distinct author names.
2. `workbook (6).xlsx` — two sheets: "L1 Group (UK-Origin Writers)" (41 rows) and "L2 Group (Non-Native Writers)" (45 rows), columns: #, Full Name, Nationality/Origin, Field, Affiliation, Email, Source, Verified.
3. `l2_writing_corpus_sample-(2).csv` — 2 L2 essays (text_id, group, L1_background, prompt, text; 52 and 40 tokens). No author column.

## Authoritative cohorts & rule enforcement
- L1 cohort = 41 workbook names minus 1 (Jung Chang permanently excluded) = 40 distinct writers.
- L2 cohort = 45 workbook names.
- All 40 L1 workbook names match records in the L1 CSV (one documented surface-form alias: "Ronald E. Asher" ↔ "R. E. Asher"). Jung Chang does not appear in the L1 CSV.

## Key findings (audit only — no inferential statistics performed)
- L1 CSV: 563 records flagged `has_fulltext=yes`, 478 `partial`; doc types: 595 abstract_openalex, 344 none, 100 fulltext_pdf_oa, 2 paragraphs_book_source. 344 records have empty text.
- With a per-text eligibility threshold of ≥100 tokens: 515 eligible L1 texts from 37 distinct cohort authors (< 40 authors).
- Thresholds: text ≥100 tokens; author-level ≥100 total tokens. Metrics: token count, mean word length, TTR (V/N), Carroll's CTTR (V/√(2N)); author-level means.
- Inferential gate: requires ≥40 distinct writers with comparable text observations in EACH cohort.
  - L1: 37/40 authors → insufficient.
  - L2: 0/45 identifiable authors → the L2 CSV contains only 2 anonymous sample essays and cannot be attributed to the 45 named authors. No author IDs, no fabrication.
  - **Result: inferential statistics (Mann–Whitney U, Cliff's delta, Holm correction) are BLOCKED by the script.** No group-comparison p-values or effect sizes are reported anywhere in this package.

## Limitations
- Many L1 "texts" are abstracts, not the writers' own composed prose at comparable length/genre; this is documented, not corrected.
- The 2 L2 essays are demonstrative samples, not a 45-author corpus.
- No imputation, merging with legacy files, or invented values were used anywhere.

## Reproduce
```
python analyze_authoritative_three_files.py
```
Outputs in `authoritative_outputs/`: text_level_metrics_authoritative.csv,
author_level_metrics_L1_authoritative.csv, cohort_coverage_audit.csv,
inferential_analysis_blocked.txt, authoritative_analysis_summary.xlsx.
Dependencies: pandas, numpy, openpyxl (scipy only needed if the gate ever passes).
