# Childhood Adversity and Adult Health

**A reproducible Python exploration of published aggregate estimates, with depression as the primary outcome.**

Can a question about childhood relationships and adult emotional responses be translated into a defensible data project? This repository demonstrates the first step: matching a research question to what a source actually measures.

![Published associations](figures/published_associations.png)

## Research question
How do published associations with adult depression differ across cumulative childhood-adversity categories? Smoking and heavy drinking provide descriptive context; they were selected before this implementation, not selected by an automated search for large effects.

## Data and scope
Nine published adjusted odds ratios and their 95% confidence intervals were manually transcribed from Table 2 of Merrick et al. (2019), based on BRFSS 2015–2017 in 25 states. The source study included 144,017 respondents; this repository analyzes **nine summary rows, not those individual records**. Zero ACEs is the reference. Models in the source adjusted for age group, sex, and race/ethnicity.

Source: https://www.cdc.gov/mmwr/volumes/68/wr/mm6844e1.htm
DOI: https://doi.org/10.15585/mmwr.mm6844e1

## What the code does
- Validates category coverage, uniqueness, missing values, positivity, and CI bounds.
- Produces a forest plot using the published confidence intervals.
- Exports checked estimates, log odds ratios, and a machine-readable summary.
- Keeps the original exploratory question separate from the available measurements.

## What the results mean
Published depression AORs increase from 1.6 to 2.6 to 5.3 across 1, 2–3, and 4+ ACE types. These are odds ratios, not risk ratios or probabilities. The source intervals are reproduced; no regressions or significance tests were performed here. Confidence intervals sharing a reference do not establish differences between exposure categories.

## Measurement limits
This extract contains no emotional-recovery duration, stress-triggered sleep changes, appetite changes, or individual parent-behavior measurements. Depression is not a substitute for those constructs. The analysis cannot establish causation, identify a person's childhood history, or support diagnosis. Aggregate estimates cannot recover individual-level confounding, missingness, survey weights, or mechanisms. Selection of three outcomes does not make this a systematic review.

## Reproduce
Python 3.10+:
```bash
python -m venv .venv
# macOS/Linux
source .venv/bin/activate
# Windows: .venv\Scripts\activate
pip install -r requirements.txt
python src/analyze.py
python -m unittest discover -s tests
```
No account, network download, private records, or credentials are required after installing dependencies. See `notebooks/analysis.ipynb` for a walkthrough; Jupyter installation is optional and separate.

## Repository guide
| Path | Purpose |
| --- | --- |
| data/published_estimates.csv | Attributed aggregate input |
| data/DATA_DICTIONARY.md | Variables, provenance, and transcription checks |
| src/analyze.py | Reproducible analysis |
| notebooks/analysis.ipynb | Notebook walkthrough |
| figures/ | Generated figure |
| reports/ | Outputs, interpretation, and proposed next study |
| tests/ | Data and statistical-encoding checks |

## Portfolio positioning
This is a small **aggregate-data research project**, not original participant recruitment, a new clinical study, or a replication of CDC's respondent-level analysis. Review and run the code yourself before describing it as your work. AI assisted preparation of this repository; take responsibility for any version you publish.

## Publish to GitHub
Create an empty repository named `childhood-adversity-adult-health`, unzip this folder, and upload its **contents** to the repository root. Keep the folder structure. Start with README.md and the figure to check rendering. Do not upload personal questionnaires or participant records. No GitHub repository has been created by this package.

## Credits and reuse
Original research: Merrick MT, Ford DC, Ports KA, et al. MMWR. 2019;68:999–1005. The CDC authors collected/analyzed the underlying survey data; this repository supplies an attributed visualization and validation workflow. No CDC endorsement is implied. Project code is offered under the MIT license; third-party material retains its original terms.
