# Work plan: GitHub + Zenodo deposit (Editorial Issue 4)

Guide: https://claude.ai/artifact/8vmTZyLF46YxUeTi18ZNLq (Route A: DOI now, files open at acceptance)

Folder: `Article_Hydrochemistry&Isotopes\haouz-mejjate-recharge-som-emma` (in OneDrive, so upload to GitHub through the website, not GitHub Desktop)

## Before resubmission (28 October 2026)
- [ ] 1. Agree with the supervisors what goes in (74 new samples + notebooks; compiled literature data only if approved; well coordinates only if allowed)
- [ ] 2. Prepare this folder
  - [x] Folder created and moved into the article main folder
  - [x] README.md, LICENSE-DATA.md, requirements.txt, .gitignore
  - [x] data/All_data1.xlsx = copy of SOM1/01_Data/All_data1.xlsx (540 samples) with the 3H column REMOVED (user request 2026-10-16: tritium data sensitive); 29 columns; cell values identical except float noise in the 16th decimal (openpyxl rewrite). CONSEQUENCE: 05_EMMA/01_EMMA cannot reproduce SM13 (3H by dominant source, 44 samples) from this file; decide later (restore 3H, or note SM13 as on request).
  - [x] data/README.md: note on coordinates (sources in different CRS)
  - User decision 2026-10-16: do NOT edit the data for now. Coordinate differences between file versions come from different CRS, not errors. The NO3 11.975 placeholder (11 Sahraoui samples) stays as it is.
  - [ ] data/new_samples_2025.csv + data/data_dictionary.md
  - [ ] data/compiled_literature.csv (only if approved)
  - [x] notebooks/ cleaned and re-run (table below; 10 notebooks, all checked against the published figures)
  - [x] notebooks/README.md (run order)
  - [x] scripts/gibbs_som1.py (copy of SOM1/08_Scripts/gibbs_som1.py with a provenance header; derived from WQChartPy gibbs.py, GPL-3.0)
  - [ ] CITATION.cff (all co-authors, ORCID)
- [ ] 3. GitHub: new private repository with the GPL-3.0 licence, upload the files through the website, invite supervisors and co-authors
- [ ] 4. Practise on sandbox.zenodo.org (optional)
- [ ] 5. Zenodo: upload the ZIP, reserve the DOI, files restricted, publish
- [ ] 6. Put the DOI in Draft 2.6 (Data availability, line 1136), the response letter (Issue 4) and Editorial Manager

## When the paper is accepted
- [ ] 7. Zenodo: Edit > files Public > publish
- [ ] 8. GitHub: Settings > Change visibility > Public
- [ ] 9. Zenodo: add the paper DOI under Related works ("Is supplement to")

## Data: which version (checked 2026-10-16)

- **Correct base file: `SOM1/01_Data/All_data1.xlsx`** (31 Mar 2026; `EMMA1/01_Data/All_data1.xlsx` is an identical copy). All article notebooks read it, and the Scatter_plots processed files (`Data_for_ScatterPlots.xlsx`, 27 Mar) hold the same values.
- **Do not use `Scatter_plots/01_Data/All_data1.xlsx`** (5 Apr). It is newer but not corrected: for 8 Sahraoui samples (W57, SP2, S1, S3, S4, S6, S7, S8) Na, SO4 and NO3 are shifted by one column, and Y is wrong (466,908 to 501,966) for 8 of our 2025 samples (S47, S51-S56, S61). No article figure used it.
- One fix needed in the copy we share (originals stay unchanged): NO3 = 11.975 is a placeholder for 11 Sahraoui samples (W26, W36, W48, W57, SP2, S1, S3, S4, S6, S7, S8); Sahraoui et al. (2025) Table 1 gives no NO3 for them, so the cell must be empty. Effect on the article: none on SOM, EMMA or Figures 3-13 (NO3 not used); in SM2 the CAI-II of these 11 points changes by 0.03 at most, no sign change, so SM2 stays as published.
- To confirm (user, field sheet): coordinates of S26 and S27 (the two versions disagree); 4 Rochdane coordinates (S172-S175) exist only in the 5 Apr file, check them against Rochdane et al. (2015) before adding.

## Notebooks (clean names, from the latest versions; originals in SOM1, EMMA1 and Scatter_plots are never changed)

Structure: one subfolder per method, numbered in run order; outputs kept apart in `outputs/` (figures named by manuscript number, tables, intermediate files passed between notebooks). Every notebook finds its paths from the repository root.

| Repo notebook | Source (latest version) | Manuscript output | Cleaned | Re-run OK |
|---|---|---|---|---|
| 01_data_preparation/01_data_quality_control.ipynb | SOM1/02_Notebooks_V2/Notebook_01 | data check (no figure); export identical to SOM1 (406 x 13); checked by user 2026-10-16 | [x] | [x] |
| 01_data_preparation/02_preprocessing.ipynb | SOM1/02_Notebooks_V2/Notebook_02 | Figure 3 (pixel-identical to the published file); 3 exports identical to SOM1; checked by user 2026-10-16 | [x] | [x] |
| 02_hydrochemistry/01_scatter_plots.ipynb | Scatter_plots/02_Notebooks/Scatter_plots3 (reads data/All_data1.xlsx directly) | Figure 4 (8 panels + legend), SM1, SM2: all 11 images pixel-identical to the published files; checked by user 2026-10-16 | [x] | [x] |
| 03_PCA_SOM_HCA/01_PCA_SOM_training.ipynb | SOM1/02_Notebooks_V2/Notebook_03 | Figure 5 (166 px differ by 1/255, invisible), SM5, SM6 identical; SM3, SM4 identical except a dash in the title; SOM model, BMU table and grid table identical to SOM1; PC signs fixed explicitly (scikit-learn 1.9.0 flips them vs 1.3.0); your check pending | [x] | [x] |
| 03_PCA_SOM_HCA/02_HCA_clustering.ipynb | SOM1/02_Notebooks_V2/Notebook_04 | SM7, SM8, SM9 pixel-identical; data_final_with_clusters identical to SOM1; your check pending | [x] | [x] |
| 03_PCA_SOM_HCA/03_SOM_figures.ipynb | SOM1 Notebook_05_V4 + dendrogram and Stiff cells of Notebook_05_V3 | Figures 6, 8, 9 and the 5 Figure 7 panels pixel-identical; Piper must run BEFORE the SOM map (WQChartPy changes global font sizes); your check pending | [x] | [x] |
| 04_isotopes/01_isotope_dataset.ipynb | EMMA1/02_Notebooks/Notebook_01 | data for EMMA (no figure); 345 samples = 342 with stable isotopes + 3 tritium-only (S406, S419, S437) kept explicitly so the Cl screening set is the article's 214; export = EMMA1 original minus the 3H column; your check pending | [x] | [x] |
| 04_isotopes/02_isotopes.ipynb | EMMA1/02_Notebooks_V2/Notebook_02_V3 | Figure 10 pixel-identical; LEL 6.40/-7.4/0.71/n=57 and 2231-3919 m checked; your check pending | [x] | [x] |
| 05_EMMA/01_EMMA.ipynb | EMMA1/02_Notebooks_V2/Notebook_03b_V3 | Figure 11 NEW VERSION v4 (user request 2026-10-16: panel labels EM1/EM2/EM3 only, meanings in the in-panel legend; copied to Revision2 Figures/Main as Figure11_..._v4.png, to be swapped into Draft 2.6 by the user), SM10 (= V3 export; the published SM10 is the older May export, same data, smaller fonts), SM11, SM12 pixel-identical; 214/202/12, 148/132, 53.5/6.4/40.1, SE 5.2/0.7/5.3 checked; SM13 skipped (no 3H); EMMA_results.xlsx = original; your check pending | [x] | [x] |
| 05_EMMA/02_EMMA_sensitivity.ipynb | EMMA1/11_Sensitivity_S1S5/Sensitivity_S1S5_V3 | Table SM2 csv identical, SM14 pixel-identical; summary md without the reviewer/ready-to-use sections; your check pending | [x] | [x] |
| 05_EMMA/03_EMMA_spatial.ipynb | EMMA1/02_Notebooks_V2/Notebook_04_V2 | NOT INCLUDED: needs the GIS shapefiles of the wells (not shared); Figure 12 was made in QGIS from EMMA_results.xlsx (noted in the README) | - | - |

Not in the repo: EMMA1 Notebook_03 and Notebook_03a (exploration, replaced by 03b); Scatter_plots1/2 (older versions). Figures 1, 2, 12 (assembly) and 13 are drawn in QGIS / Illustrator, not in Python.

Cleaning checklist (each notebook):
1. One paths cell that finds the repository root and builds `data/`, `outputs/...` from it, no `C:\Users\...` paths.
2. Keep only the cells that make the final results; remove old variants and draft notes.
3. Names as in the manuscript (cluster names, Regional MBR / Front-slope MBR, Groundwater (Wells)).
4. Output files named by manuscript number (Figure6_..., SM11_...) and one shared name for files passed between notebooks.
5. Header cell: what the notebook does, inputs, outputs, manuscript figures.
6. Fixed random seeds (SOM, Monte Carlo).
7. Re-run top to bottom in a fresh kernel; the key numbers must match the manuscript (540 samples, 406 with complete major ions, 8 x 9 SOM, K = 4, 148 EMMA samples, 132 valid, 53.5 / 40.1 / 6.4 %).
FULL CHAIN RE-RUN 2026-10-16: outputs/ emptied, 5 notebooks executed in order (4 min), all outputs re-verified against published figures and SOM1 files.

PNG ONLY (user rule 2026-10-16): all notebooks save .png only; no .svg in outputs/ (strip_svg post-processing applied to every notebook).
FULL CHAIN RE-RUN 2026-10-16 (second time): outputs/ emptied, 10 notebooks executed in order (~6 min), every figure verified pixel-identical (Figure 5: 166 px at 1/255; SM3/SM4: title dash only).
