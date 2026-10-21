# SMWC — GitHub Replication Package

**Statistical comparison of lexical diversity in L1 (native English), L2 (non-native English), and AI-generated academic writing.**

This archive is a self-contained replication package for the "Same Meaning, Wider Codex" (SMWC) study on lexical diversity (TTR, CTTR, overall TTR, mean word length) across writer groups, including Mann–Whitney U tests and Cliff's delta effect sizes.

---

## 1. Directory structure

Place all files flat in your repository root (or mirror the layout below):

```
repository-root/
├── README_DATA.md                              <- this file
├── data/                                       (or repo root)
│   ├── final_balanced_dataset_10000.csv        primary dataset (10,000 texts)
│   ├── final_balanced_dataset.csv              primary dataset (600 texts, 200/group)
│   ├── balanced_writing_corpus.csv             seed corpus (9 texts, prompts + full text)
│   ├── l2_writing_corpus_sample.csv            L2 sample corpus
│   ├── author_level_metrics_master.csv         author-level lexical metrics (83 authors)
│   └── statistical_comparison_L1_L2_master.csv master test results (L1 vs L2)
├── scripts/
│   └── statistical_comparison_L1_L2_master.py  analysis pipeline (Python 3)
├── tables/
│   ├── master_statistical_report.xlsx          formatted Excel report (5 sheets)
│   └── workbook.xlsx                           author rosters (L1 / L2 groups)
├── figures/
│   ├── figure1_structural_parity.png
│   ├── figure2_lexical_bifurcation.png
│   ├── figure3_overall_ttr_distribution.png
│   └── figure4_effect_sizes_cliff_delta.png
└── reports/
    └── statistical_report_L1_L2.pdf            narrative statistical report
```

## 2. Data dictionary

### `final_balanced_dataset_10000.csv` — primary dataset (10,000 rows × 11 cols)
A balanced corpus of academic paragraphs: 3,333 L1 (human, native English), 3,333 L2 (human, non-native English), 3,334 AI-generated texts. Five distinct academic prompts (standardized testing, AI in academic writing, online vs. face-to-face learning, multilingual research policy, university funding).

| Column | Type | Description |
|---|---|---|
| `text_id` | string | Unique ID: base text + replicate suffix (e.g. `L2_TUR_001_R0193`) |
| `group` | category | `L1`, `L2`, or `AI` |
| `subset` | category | `A_L1_HUMAN`, `B_L2_HUMAN`, `C_AI_SYN` |
| `L1_background` | string | Writer's L1 (Turkish, Chinese, Persian/Azerbaijani, Spanish, Arabic, English...) |
| `prompt_id` | string | `P_A` or `P_B` prompt assignment |
| `prompt` | string | Full academic writing prompt text |
| `text` | string | The academic paragraph (raw text) |
| `source` | string | Provenance tag (`pilot_seed`, `synthetic_seed`, `synthetic_unique_ai`, ...) |
| `year` | integer | Publication year where known (NaN = not applicable) |
| `word_count` | integer | Number of whitespace tokens in `text` |
| `char_count` | integer | Number of characters in `text` |

### `final_balanced_dataset.csv` — pilot/balanced dataset (600 rows × 11 cols)
Identical schema; 200 texts per group (L1/L2/AI), derived from the 9-text seed corpus with replicates.

### `balanced_writing_corpus.csv` — seed corpus (9 rows × 5 cols)
The original hand-written seed texts: `text_id`, `group` (L2/L1/AI), `L1_background`, `prompt`, `text`.

### `author_level_metrics_master.csv` — author-level metrics (83 rows × 9 cols)
One row per author with ≥ 50 total tokens (38 L1, 45 L2):

| Column | Description |
|---|---|
| `author` | Author name |
| `n_docs` | Number of documents by the author |
| `total_tokens` | Total word tokens (regex `[A-Za-z]+('[A-Za-z]+)?`, lowercased) |
| `mean_wl` | Mean word length (characters) |
| `ttr` | Mean per-text type–token ratio |
| `cttr` | Mean corrected TTR = types / sqrt(2·tokens) |
| `overall_ttr` | Pooled types / pooled tokens |
| `text_length` | Total tokens (alias of `total_tokens`) |
| `group` | `L1` or `L2` |

### `statistical_comparison_L1_L2_master.csv` — test results (5 rows × 12 cols)
Mann–Whitney U tests (two-sided, α = .05) on author-level metrics:

| Column | Description |
|---|---|
| `metric` | `mean_wl`, `ttr`, `cttr`, `overall_ttr`, `text_length` |
| `n_L1`, `n_L2` | Sample sizes (38, 45) |
| `median_L1/L2`, `mean_L1/L2` | Descriptives |
| `U` | Mann–Whitney U statistic |
| `p_value` | Two-sided p-value |
| `cliffs_delta` | Cliff's δ effect size (−1 … +1) |
| `rank_biserial` | Rank-biserial correlation |
| `significant` | p < .05 |

Key result: L1 vs L2 differ hugely on per-text `ttr` (δ ≈ 0.998) and `cttr` (δ ≈ −0.945) — an artefact of text-length imbalance — while `mean_wl` and `text_length` do not differ significantly (δ ≈ 0.02–0.06). See the PDF report for the length-confound discussion.

## 3. Scripts

- `statistical_comparison_L1_L2_master.py` — computes lexical metrics per text, aggregates to author level, runs Mann–Whitney U + Cliff's delta, writes the CSV and formatted XLSX report.

## 4. Tables

- `master_statistical_report.xlsx` — sheets: `Statistical Tests`, `Author_Level_Metrics`, `L1_Authors` (38), `L2_Authors` (45), `Summary`.
- `workbook.xlsx` — verified author rosters with nationality, field, affiliation and source metadata for both groups.

## 5. Figures

1. `figure1_structural_parity.png` — structural (word-count) parity across L1/L2/AI groups.
2. `figure2_lexical_bifurcation.png` — lexical diversity split between groups.
3. `figure3_overall_ttr_distribution.png` — overall TTR distributions.
4. `figure4_effect_sizes_cliff_delta.png` — Cliff's δ effect sizes per metric.

## 6. Quick reproduction

```bash
# requirements
pip install pandas numpy scipy openpyxl matplotlib

# 1) recompute author-level statistics and test results
python scripts/statistical_comparison_L1_L2_master.py

# 2) inspect the master report
open tables/master_statistical_report.xlsx

# 3) regenerate figures (illustrative)
python - <<'PY'
import pandas as pd, matplotlib.pyplot as plt
d = pd.read_csv("data/final_balanced_dataset_10000.csv")
d.boxplot(column="word_count", by="group"); plt.savefig("figure1_structural_parity.png")
PY
```

## 7. License

- **Data & figures:** released under CC BY 4.0 (attribute the SMWC project; author metadata compiled from public/open-access sources — verify individual licensing before redistribution of source texts).
- **Code:** MIT License.
- The AI-generated texts were produced with a large language model (GPT-4o family) and are provided for research replication; no claim is made about the underlying model's output licensing.
- Third-party PDF sources referenced in `workbook.xlsx` remain under their original copyrights and are **not** included in this package.

## 8. Citation

If you use this package, please cite the SMWC study and this replication archive (add DOI/URL upon GitHub release).
