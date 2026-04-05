# -cognitive-motor-assessment-analysis
# Cognitive-Motor Assessment Analysis
### Visuospatial Cognition & Task-Pacing Analytics in a Clinical Study Context

> **Course:** Health Informatics — Data Analysis Assignment 1  
> **Team:** Group 8 | Indiana University Indianapolis  
> **Role (Sri Ramya Panja):** Data analysis lead, PCI metric design, statistical interpretation  
> **Status:** Completed ✓

---

## Overview

This project analyzes behavioral and cognitive data from 13 participants completing a structured motor-cognitive task — the **Simple Stew recipe completion task** — in a clinical study context. Participants were assessed on both their **visuospatial reasoning ability** (Block Design scores) and their **task execution behavior** (step-by-step timing data).

The central research question: *Does the consistency with which a participant paces themselves through a task predict their cognitive performance score?*

This is a meaningful clinical question — pacing irregularity during instrumental activities of daily living (IADLs) like cooking may serve as an early behavioral marker of cognitive decline. The analysis bridges **neuropsychological assessment**, **wearable/behavioral sensing data**, and **clinical informatics** methodology.

---

## Key Contribution: Pacing Consistency Index (PCI)

A novel quantitative metric was proposed and implemented to capture how consistently participants pace themselves across sequential task steps.

**Formula:**

```
PCI = 1 / (1 + CV)

where CV = SD_interval / Mean_interval
```

- **CV** (Coefficient of Variation) measures relative variability in inter-step timing
- **PCI** maps CV onto a bounded [0, 1] scale where higher values = more consistent pacing
- Participants ranged from PCI = 0.372 (most erratic) to 0.550 (most consistent)

This metric draws on established use of CV in rehabilitation and performance research (e.g., stride-time variability in gait analysis) and applies it to upper-extremity task performance — a methodology suitable for publication or extension in clinical informatics research.

---

## Tasks Completed

| Task | Description | Method |
|------|-------------|--------|
| 1 | Descriptive statistics for Block Design scores | `pandas.describe()` with custom column labeling |
| 2 | Total recipe completion time per participant | CSV file parsing with `glob`, session time extraction |
| 3 | Scatter plot: completion time vs. Block Design score | `matplotlib` scatter |
| 4 | Merged dataset construction | `pandas` merge on participant ID |
| 5 | Linear regression: time → Block Design score | `numpy.polyfit` |
| 6 | Overlapping regression line on scatter plot | Combined `plt.scatter` + `plt.plot` |
| 7 | Clinical implications of regression results | APA-style statistical interpretation |
| 8 | Pacing Consistency Index (PCI) computation | Custom metric: CV → PCI per participant |
| 9 | Scatter plot: PCI vs. Block Design score | Regression of PCI on cognitive performance |
| 10 | Clinical interpretation of PCI findings | Written analysis with regression equation |

---

## Key Findings

- Mean Block Design score: **39.31** (SD = 12.32, N = 13), indicating moderate spread in visuospatial ability
- Regression equation (time → score): **Y = −0.036X + 52.83** — participants who took longer tended to score lower, suggesting a modest inverse relationship
- PCI regression: **Y = −113.07X + 87.49** — a weak negative association between pacing consistency and Block Design score; more consistent pacers did not necessarily score higher, highlighting that pacing behavior and visuospatial cognition are partially independent constructs
- These findings support the importance of **multimodal assessment** — neither timing data nor cognitive scores alone fully characterizes participant ability

---

## Tech Stack

| Tool | Use |
|------|-----|
| Python 3 | Core scripting language |
| pandas | Data loading, merging, descriptive statistics |
| numpy | Interval computation, regression coefficients |
| matplotlib | Scatter plots, regression overlays |
| IPython / Jupyter | Interactive notebook environment, styled table output |
| glob / os | Multi-file CSV ingestion across 13 participant files |

---

## Data Structure

```
data/
├── Assessments.xlsx                        # Block Design scores (N=13)
├── C008_SimpleStew_CompletedStepsData.csv  # Per-participant step timing
├── C009_SimpleStew_CompletedStepsData.csv
├── ...
└── C041_SimpleStew_CompletedStepsData.csv
```

> **Privacy note:** All participant data is de-identified. Participant IDs (C008–C041) are study-assigned codes with no personally identifiable information.

---

## Clinical Relevance

This analysis demonstrates core health informatics competencies applicable to real-world clinical settings:

- **Digital phenotyping**: Extracting behavioral patterns from time-series task data — the same methodology used in wearable health monitoring and remote patient monitoring platforms
- **Cognitive biomarker research**: Block Design is a validated neuropsychological instrument (from the WAIS) used in clinical assessment of dementia, TBI, and cognitive aging
- **IADL analysis**: Cooking tasks are a standard clinical measure of functional independence in occupational therapy and geriatric care
- **Reproducible research**: Fully documented, code-driven analysis pipeline with parameterized outputs suitable for audit or extension

---

## How to Run

```bash
# Clone the repository
git clone https://github.com/sriramyapanja/<repo-name>.git
cd <repo-name>

# Install dependencies
pip install pandas numpy matplotlib openpyxl jupyter

# Launch the notebook
jupyter notebook Assignment1Group8.ipynb
```

> Place participant CSV files and `Assessments.xlsx` inside a `data/` folder before running.

---

## Authors

| Name | Role |
|------|------|
| **Sri Ramya Panja** | Data analysis lead, PCI metric design, regression analysis, clinical interpretation |
| Group 8 Members | Collaborative analysis, peer review |

**Sri Ramya Panja** — MS Health Informatics, Indiana University Indianapolis  
[LinkedIn](https://www.linkedin.com/in/sriramyapanja) · [GitHub](https://github.com/sriramyapanja) · panjasriramya@gmail.com

---

## License

For educational and research purposes. Data is de-identified and used under course IRB protocols.
