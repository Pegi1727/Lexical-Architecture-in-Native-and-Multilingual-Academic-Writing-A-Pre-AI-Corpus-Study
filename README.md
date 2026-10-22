# Lexical Architecture in Native and Multilingual Academic Writing: A Pre-AI Corpus Study

[![License](https://img.shields.io/badge/license-see%20repository%20metadata-lightgrey)](#license) [![Python](https://img.shields.io/badge/python-3.9%2B-blue.svg)](#reproduction) [![Zenodo](https://zenodo.org/badge/DOI/10.5281/zenodo.23037713.svg)](https://doi.org/10.5281/zenodo.23037713) [![GitHub](https://img.shields.io/badge/GitHub-Pegi1727%2FLexical--Architecture-informational?logo=github)](https://github.com/Pegi1727/Lexical-Architecture-in-Native-and-Multilingual-Academic-Writing-A-Pre-AI-Corpus-Study)

**A pre-generative-AI baseline for comparing lexical patterns in academic writing by first-language (L1) and additional-language (L2) writers.** The study tests whether lexical diversity and length-based measures support a simple “deficit” account of multilingual academic writing.

> **Read the headline results first:** observed word length and author-level text length do not differ significantly between cohorts, while reported TTR-family measures do. The results do not establish overall writing quality, proficiency, or causal effects of language background.

## Figures

Figures are embedded from the repository's `main` branch so they display directly on this page.

### Figure 1 — Structural parity
![Figure 1: Structural parity in the L1 and L2 cohorts](https://github.com/Pegi1727/Lexical-Architecture-in-Native-and-Multilingual-Academic-Writing-A-Pre-AI-Corpus-Study/raw/main/figures/figure1_structural_parity.png)

### Figure 2 — Lexical bifurcation
![Figure 2: Lexical bifurcation across L1 and L2 writing](https://github.com/Pegi1727/Lexical-Architecture-in-Native-and-Multilingual-Academic-Writing-A-Pre-AI-Corpus-Study/raw/main/figures/figure2_lexical_bifurcation.png)

### Figure 3 — Overall TTR distribution
![Figure 3: Overall type-token ratio distribution](https://github.com/Pegi1727/Lexical-Architecture-in-Native-and-Multilingual-Academic-Writing-A-Pre-AI-Corpus-Study/raw/main/figures/figure3_overall_ttr_distribution.png)

### Figure 4 — Cliff's delta effect sizes
![Figure 4: Cliff's delta effect sizes for L1–L2 comparisons](https://github.com/Pegi1727/Lexical-Architecture-in-Native-and-Multilingual-Academic-Writing-A-Pre-AI-Corpus-Study/raw/main/figures/figure4_effect_sizes_cliff_delta.png)

A separate graphical abstract is not included here because no graphical-abstract filename is specified in the repository materials available for this README.

## Core summary results

The figures and table summarize author-level comparisons reported in `master_statistical_report.xlsx`: **38 L1 authors and 45 L2 authors**, two-sided Mann–Whitney U tests, and α = .05. Median values below are the reported cohort medians. The sign of Cliff's δ follows the comparison orientation in the report (the sign is not a statement of which group is better).

| Measure (reported field) | L1 median | L2 median | Mann–Whitney U | p-value | Cliff's δ | Result at α = .05 |
|---|---:|---:|---:|---:|---:|---|
| Token count / text length (`text_length`) | 12,346 | 8,801 | 904 | .657234 | +0.057310 | Not significant |
| Mean word length (`mean_wl`) | 5.451464 | 5.460782 | 871 | .887228 | +0.018713 | Not significant |
| Raw TTR (`ttr`, as labelled in the author-level report) | 0.627257 | 0.200431 | 1,708 | < .001* | +0.997661 | Significant |
| Overall TTR (`overall_ttr`) | 0.352085 | 0.200431 | 1,428 | < .001* | +0.670175 | Significant |
| Carroll's corrected TTR (`cttr`) | 5.840537 | 14.068313 | 47 | < .001* | −0.945029 | Significant |

\* The spreadsheet stores these very small p-values as `0.0` due to display/rounding; they are **not zero**. The independently tabulated comparison file reports p = 9.767098×10⁻¹⁵ for `ttr`, 2.891147×10⁻⁷ for `overall_ttr`, and 2.434086×10⁻¹³ for `cttr`, but that file uses **37 L1 / 45 L2** and therefore represents a different analysis snapshot. For reproducibility and consistency within this table, the 38/45 workbook's U, medians, and Cliff's δ are retained; use full-precision outputs from the matching analysis script if available.

**Macro vs. micro:** these inferential tests compare one aggregated record per author (macro/author-level analysis). `text_length` is the reported per-author token/text-length total; it is not a separately tested token-level sample. A separate corpus-pooled micro-analysis, with its own inferential statistics, is not supplied in the summary workbook and is not asserted here. `ttr`, `overall_ttr`, and `cttr` are reproduced using the report's field names; the README does not silently reinterpret them as interchangeable estimators. Verify formula and tokenization conventions against the analysis code before reusing these measures.

## Key empirical conclusions and methodological takeaways

1. **A simple lexical-deficit model is not supported by every measure.** Mean word length and author-level text length are statistically indistinguishable in the reported comparison. Lexical-diversity indices do differ, but their direction and magnitude depend on the index and its length sensitivity; no single TTR statistic is a global measure of writing ability.
2. **Length compensation matters.** Raw TTR is sensitive to sample length. Carroll's CTTR applies a length correction, and the reported CTTR contrast is large but points in the opposite direction from raw TTR. Read the two together, report text length, and avoid interpreting lexical richness without accounting for corpus size and metric definition.
3. **Treat the corpus as a pre-AI human baseline.** These materials provide a historical/human-authored comparison set rather than an AI-generated reference. Preserve source, date, authorship, and inclusion metadata. Do not use language-background-associated lexical patterns as a shortcut for AI detection: detector error and bias can disproportionately affect multilingual writers. The study itself does not validate an AI detector.
4. **Association is not causation or a quality ranking.** The cohort comparison is observational and combines texts and authors from different source contexts. Statistical significance does not imply educational importance, and neither group should be treated as homogeneous.

## DOI and archived record

[![Zenodo DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.23037713.svg)](https://doi.org/10.5281/zenodo.23037713)

**DOI:** [10.5281/zenodo.23037713](https://doi.org/10.5281/zenodo.23037713) · [Zenodo record](https://zenodo.org/records/23037713)

## Citation

### BibTeX

```bibtex
@dataset{lexical_architecture_pre_ai_corpus,
  title        = {Lexical Architecture in Native and Multilingual Academic Writing: A Pre-AI Corpus Study},
  author       = {{Pegi1727}},
  year         = {2025},
  publisher    = {Zenodo},
  doi          = {10.5281/zenodo.23037713},
  url          = {https://doi.org/10.5281/zenodo.23037713}
}
```

### APA 7

Pegi1727. (2025). *Lexical architecture in native and multilingual academic writing: A pre-AI corpus study* [Data set]. Zenodo. https://doi.org/10.5281/zenodo.23037713

> **Citation note:** The author/date above are repository-level citation metadata used to provide a usable citation block. If the Zenodo record specifies different creator names or publication year, prefer the record's exported BibTeX/APA citation.

## Corpus architecture and cohorts

### Pre-AI human baseline

The project frames its materials as a **pre-AI baseline** of human-authored academic writing. This distinction is central to future evaluation: a baseline should be retained as collected and clearly distinguished from synthetic or AI-assisted text. “Pre-AI” describes the study's intended corpus framing, not a guarantee that every source or text has independently documented AI-use provenance.

### Stratified multilingual writing corpus

The comparison is organized into two writer cohorts:

- **L1:** writers classified in the project materials as native/first-language or UK-origin writers.
- **L2:** multilingual/additional-language writers, represented across multiple language backgrounds and academic contexts.
- **Unit of inference:** author, not individual token. In the reported statistical workbook, the analyzed cohorts are 38 L1 and 45 L2 authors.
- **Source and text coverage:** the repository's accompanying materials include author/source inventories and full-text corpus files. A separate workbook summary describes 718 L1 documents with full text and 45 L2 documents; these document counts should not be conflated with the author counts used in the reported comparison.

The cohort labels are operational classifications from the project, not claims that all authors share one language history. Source genre, discipline, publication context, text length, and corpus composition may differ between groups and should be considered in interpretation.

### Author-level aggregation

Texts are grouped by credited author before between-group inference. The results sheet provides `n_docs`, `total_tokens`, `mean_wl`, `ttr`, `cttr`, `overall_ttr`, `text_length`, and group. Treat each author as one observation for the reported Mann–Whitney tests; do not treat each text or each token as an independent writer. When reproducing any measure, document the tokenization, normalization, aggregation, and treatment of short texts used by the analysis.

### Verified-author criteria

The supplied author inventories mark entries as verified and associate writers with institutional/source evidence. For a reproducible extension, retain an author only when identity and cohort assignment can be checked against a credible source (for example, a source publication's author byline/affiliation plus reliable biographical or institutional evidence for the cohort criterion). Record the evidence and source for each decision, resolve homonyms, and do not infer L1 status from a name, nationality, or affiliation alone. “Verified” means that the project's listed identity/source checks were satisfied; it is not independent confirmation of every biographical variable.

## Repository file structure

The repository page and requested figure names establish the following paths. Other filenames may change between releases; inspect the checked-out repository rather than assuming every optional file exists.

```text
.
├── README.md
└── figures/
    ├── figure1_structural_parity.png
    ├── figure2_lexical_bifurcation.png
    ├── figure3_overall_ttr_distribution.png
    └── figure4_effect_sizes_cliff_delta.png
```

The project data and statistical workbook used to document the summary are distributed with the accompanying corpus/repository materials or Zenodo record. Respect any access, licensing, privacy, and attribution notes included alongside those materials.

## Reproduction

Clone the repository and inspect the available scripts, data, and environment files before running analyses:

```bash
git clone https://github.com/Pegi1727/Lexical-Architecture-in-Native-and-Multilingual-Academic-Writing-A-Pre-AI-Corpus-Study.git
cd Lexical-Architecture-in-Native-and-Multilingual-Academic-Writing-A-Pre-AI-Corpus-Study
python --version
```

Python **3.9+** is suggested for a compatible analysis environment; install dependencies from the repository's `requirements.txt` or `pyproject.toml` if present. The exact script/command is intentionally not guessed here because no analysis-script or dependency-manifest path is established by the available repository metadata. To reproduce the table, use the 38/45 analysis snapshot, calculate one author-level record per writer, run two-sided Mann–Whitney U tests and calculate Cliff's δ, then check medians, sample sizes, p-values, and effect-size orientation against the corresponding output. Do not mix that snapshot with the separate 37/45 CSV comparison.

### License

The applicable code, text, and data licenses should be taken from the repository's `LICENSE` file and the source/Zenodo record. This README does not assign a license to third-party corpus text. Check permissions and source licenses before redistributing or reusing texts.

## Limitations

This README summarizes the available project workbook and metadata, not a fresh execution of the full corpus pipeline. The workbook and a separate comparison CSV disagree on the L1 author count and numerical test results, so they must be treated as distinct analysis snapshots. The table identifies the snapshot it uses and preserves that caveat. The exact metric formulas, filtering choices, and statistical implementation should be verified from the matching source code and data before publication or secondary analysis.

---

For questions, corrections, or updated analyses, please open an issue in the [GitHub repository](https://github.com/Pegi1727/Lexical-Architecture-in-Native-and-Multilingual-Academic-Writing-A-Pre-AI-Corpus-Study).
