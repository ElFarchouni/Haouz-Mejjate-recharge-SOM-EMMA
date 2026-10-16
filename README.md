# Haouz-Mejjate groundwater recharge: data and code (SOM, EMMA, isotopes)

Data and Python code supporting the article:

> El Farchouni, A., et al. *Groundwater Recharge Mechanisms in the Haouz-Mejjate Aquifer (Morocco): Insights from Environmental Tracers and Self-Organizing Maps.* Groundwater for Sustainable Development (under review, manuscript GSD-D-26-00633R1).

Dataset DOI (Zenodo): `TODO: https://doi.org/10.5281/zenodo.XXXXXXX`

## Contents

| Folder | What it holds |
|---|---|
| `data/` | Hydrochemical and stable-isotope data used in the study, with a note on coordinates |
| `notebooks/` | Jupyter notebooks, one subfolder per method (`01_data_preparation`, `02_hydrochemistry`, `03_PCA_SOM_HCA`, `04_isotopes`, `05_EMMA`), numbered in run order |
| `outputs/` | Figures (PNG, named by manuscript number), tables and intermediate files produced by the notebooks |
| `scripts/` | Helper module used by the notebooks (modified Gibbs diagram) |

## Data

- `data/All_data1.xlsx`: the 540 water samples used in the article (74 collected for this study in January to April 2025, 466 compiled from eight published studies; the `Reference` column gives the source). Concentrations in mg/L, stable isotopes in ‰ VSMOW. The tritium column is not included in the shared file.
- `data/README.md`: note on the coordinate columns (the sources use different coordinate reference systems).

TODO before publication: `data/data_dictionary.md` (column names, units and methods); confirm with the co-authors which data are shared.

## How to run

1. Install Python 3.11 (for example with Anaconda).
2. Install the packages: `pip install -r requirements.txt`
3. Open the notebooks in `notebooks/` in the order given in `notebooks/README.md`. Running the ten notebooks in order takes about six minutes.

Figures 1, 2, 12 and 13 of the article (maps and conceptual model) were drawn in QGIS and Adobe Illustrator and are not produced by the notebooks; Figure 12 uses `outputs/tables/EMMA_results.xlsx`. Figure SM13 needs the tritium data, which are not included (available on request).

The Piper and Gibbs diagrams use WQChartPy (version 0.1.10). The Gibbs diagram was drawn with an adapted copy of its Gibbs module (label "Evaporation Dominance" instead of "Seawater", repositioned labels), provided in `scripts/`.

## Licences

- Code: GNU General Public License v3.0 (`LICENSE`), because the Gibbs module is derived from WQChartPy (GPL-3.0).
- Data: Creative Commons Attribution 4.0 International (`LICENSE-DATA.md`).

## How to cite

Please cite the article and the dataset (see `CITATION.cff`).

## Contact

Abderrahman El Farchouni, Mohammed VI Polytechnic University (UM6P), Morocco.
