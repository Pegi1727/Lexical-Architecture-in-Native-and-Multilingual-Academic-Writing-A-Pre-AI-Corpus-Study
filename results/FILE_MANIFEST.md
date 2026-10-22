# File Manifest — permitted and excluded files

## Permitted inputs (analysis is based EXCLUSIVELY on these three)
| File | Role | Shape |
|---|---|---|
| l1_corpus_openaccess_first_updated.csv | L1 text records | 1041 rows × 12 cols, 40 distinct authors |
| workbook (6).xlsx | Cohort definitions (L1 and L2 author lists) | 2 sheets: L1=41, L2=45 names |
| l2_writing_corpus_sample-(2).csv | L2 sample essays | 2 essays, no author column |

## Permanently excluded author
- Jung Chang (workbook L1 row 29) — excluded by research rule; not present in the L1 CSV.

## Excluded legacy / prior files (NOT read, merged, or cited)
- final_balanced_dataset.csv, final_balanced_dataset_10000.csv (prior 10,000-row master outputs)
- balanced_writing_corpus.csv, l2_writing_corpus_sample.csv (older corpus versions)
- l1_corpus_openaccess_first.csv (pre-update version)
- workbook.xlsx (older version)
- All PDFs and image files (source documents superseded by the three authoritative files)
- Any other previous master outputs or scripts

## Generated outputs (in authoritative_outputs/)
- text_level_metrics_authoritative.csv
- author_level_metrics_L1_authoritative.csv
- cohort_coverage_audit.csv
- inferential_analysis_blocked.txt
- authoritative_analysis_summary.xlsx
