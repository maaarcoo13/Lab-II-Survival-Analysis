# Lab II: Survival Analysis of Children with Bone Marrow Transplant

Authors: Eduardo Cañas Madroñal and Marco Andrea Gil González

In this lab we study the [Bone marrow transplant: children](https://archive.ics.uci.edu/dataset/565/bone+marrow+transplant+children) dataset (UCI repository: 187 patients, 37 variables). We explore the data, cluster the patients and compare the survival of the clusters with Kaplan-Meier and Cox regression.

## Contents

| File | Description |
|---|---|
| `lab2_survival_analysis.ipynb` | Full analysis, saved with all the outputs. |
| `requirements.txt` | Python libraries needed to run the notebook. |
| `README.md` | This file. |

The report (PDF) is submitted separately.

## How to run it

1. Create an environment with Python 3.11 or newer and install the libraries:

   ```bash
   python -m venv venv
   source venv/bin/activate        # on Windows: venv\Scripts\activate
   pip install -r requirements.txt
   ```

   With conda: `conda create -n survival python=3.11`, `conda activate survival` and then the same `pip install`.

2. Open `lab2_survival_analysis.ipynb` in Jupyter or VS Code and use *Run All*. It usually takes a few minutes.

## Data

The notebook downloads the dataset automatically with `ucimlrepo` (it needs an internet connection). If the download fails, get `data.csv` from the UCI page and put it in the same folder as the notebook: the notebook uses it as a fallback.

## Reproducibility

All the random steps use `RANDOM_STATE = 42` (set at the top of the notebook), so the results should be the same in every run. These are the main values reported in the paper, which you can use to check your run (the last decimal may change with other library versions):

- 85 deaths among 187 patients (45.5%).
- K-means with k = 3: clusters of 77, 43 and 67 patients; silhouette 0.34 and bootstrap stability (ARI) of about 0.96.
- Global log-rank test: p = 0.012.
- Cox model with only the cluster: HR of 2.24 (cluster 1) and 1.61 (cluster 2) against cluster 0.
- Cross-validated C-index: 0.591 (only the cluster) and 0.616 (all the variables, ridge penalty 30).

## Output files

Running the notebook also creates a `figures/` folder (the plots of the report) and some `results_*.csv` tables. They are not included in the repository because the notebook generates them.
