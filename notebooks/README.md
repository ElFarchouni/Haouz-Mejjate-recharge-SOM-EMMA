# Notebooks: run order

Run the notebooks in this order, each from top to bottom in a fresh kernel. Every notebook finds the repository from its own location, reads `data/` and `outputs/`, and writes to `outputs/`. The whole chain takes about six minutes.

| # | Notebook | What it does | Article output |
|---|---|---|---|
| 1 | `01_data_preparation/01_data_quality_control.ipynb` | loads the 540 samples, keeps the 406 with complete major ions | data check |
| 2 | `01_data_preparation/02_preprocessing.ipynb` | mg/L → meq/L → relative % → z-score (SOM input) | Figure 3 |
| 3 | `02_hydrochemistry/01_scatter_plots.ipynb` | binary ionic ratio plots | Figure 4 (8 panels + legend), SM1, SM2 |
| 4 | `03_PCA_SOM_HCA/01_PCA_SOM_training.ipynb` | PCA, SOM grid search, final 8 × 9 SOM | Figure 5, SM3-SM6 |
| 5 | `03_PCA_SOM_HCA/02_HCA_clustering.ipynb` | number of clusters, hierarchical clustering of the SOM (K = 4) | SM7-SM9 |
| 6 | `03_PCA_SOM_HCA/03_SOM_figures.ipynb` | clustered SOM map, dendrogram + Stiff diagrams, Piper, Gibbs | Figures 6, 7, 8, 9 |
| 7 | `04_isotopes/01_isotope_dataset.ipynb` | isotope dataset (342 samples with δ¹⁸O and δ²H) | data for EMMA |
| 8 | `04_isotopes/02_isotopes.ipynb` | meteoric water lines, local evaporation line, recharge altitude | Figure 10 |
| 9 | `05_EMMA/01_EMMA.ipynb` | chloride screening, end-members, mixing proportions, Monte Carlo | Figure 11, SM10-SM12 |
| 10 | `05_EMMA/02_EMMA_sensitivity.ipynb` | scenarios S1-S5 | Table SM2, SM14 |

Each notebook ends with a check of its key numbers against the article (sample counts, variance explained, cluster sizes, mixing proportions) and stops if they differ.

Not produced by the notebooks: Figures 1, 2, 12 and 13 (QGIS and Illustrator; Figure 12 uses `outputs/tables/EMMA_results.xlsx`) and Figure SM13 (needs the tritium data, available on request).
