# Haouz-Mejjate groundwater recharge: data and code (SOM, EMMA, isotopes)

Data and Python code supporting the article:

> El Farchouni, A., Hadri, A., Ait Brahim, Y., Hssaisoune, M., Bouchaou, L., Ouarani, M., Miftah, M., Bouimouass, H., Castelli, G., Bresci, E., Penna, D., Kchikach, A., Fakir, Y., 2026. *Groundwater recharge mechanisms in the Haouz-Mejjate aquifer (Morocco): Insights from environmental tracers and self-organizing maps.* Groundwater for Sustainable Development, 101706. https://doi.org/10.1016/j.gsd.2026.101706

Dataset and code archive (Zenodo): https://doi.org/10.5281/zenodo.23419569

## Contents

| Folder | What it holds |
|---|---|
| `data/` | The 540 water samples used in the study (major ions, physico-chemical parameters, stable isotopes), with a note on coordinates |
| `notebooks/` | Ten Jupyter notebooks, one subfolder per method (`01_data_preparation`, `02_hydrochemistry`, `03_PCA_SOM_HCA`, `04_isotopes`, `05_EMMA`), numbered in run order |
| `outputs/` | Figures (PNG, named by article number), tables and intermediate files produced by the notebooks |
| `scripts/` | Gibbs diagram module adapted from WQChartPy, used by `03_SOM_figures.ipynb` |

## Data

- `data/All_data1.xlsx`: 540 water samples (74 collected for this study in January to April 2025; 466 compiled from seven published studies and one unpublished dataset, the `Reference` column gives the source). Concentrations in mg/L, stable isotopes in ‰ VSMOW. The tritium column is not included (available from the corresponding author on request).
- `data/README.md`: notes on the coordinate columns and on tritium.

## How to run

1. Install Python 3.11 (for example with Anaconda).
2. Install the packages: `pip install -r requirements.txt`
3. Run the notebooks in `notebooks/` in the order given in `notebooks/README.md`, each from top to bottom in a fresh kernel. Every notebook finds the repository from its own location and writes to `outputs/`. The whole chain takes about six minutes.

Each notebook ends with a check of its key numbers against the article (sample counts, variance explained, cluster sizes, end-members, mixing proportions) and stops if they differ.

Not produced by the notebooks: Figures 1, 2, 12 and 13 of the article (maps and conceptual model, drawn in QGIS and Adobe Illustrator; Figure 12 uses `outputs/tables/EMMA_results.xlsx`) and Figure SM13 (needs the tritium data).

The Piper and Gibbs diagrams use WQChartPy 0.1.10. The Gibbs diagram is drawn with an adapted copy of its Gibbs module (`scripts/gibbs_som1.py`: label "Evaporation Dominance" instead of "Seawater", repositioned labels).

## Licences

- Code: GNU General Public License v3.0 (`LICENSE`), because the Gibbs module is derived from WQChartPy (GPL-3.0).
- Data: Creative Commons Attribution 4.0 International (`LICENSE-DATA.md`).

## How to cite

Please cite the article (DOI above) and the dataset (`CITATION.cff`).

## Contact

Abderrahman El Farchouni, International Water Research Institute, Mohammed VI Polytechnic University (UM6P), Morocco: Abderrahman.ELFARCHO@um6p.ma
