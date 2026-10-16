# Data

`All_data1.xlsx` is the dataset used in the article (540 water samples, sheet `Sheet1`), provided unchanged.

## Note on coordinates (columns X and Y)

- X and Y are projected coordinates in metres, as given in the source datasets.
- They are **not all in the same coordinate reference system (CRS)**: the samples were compiled from several studies, which use different Moroccan Lambert projections (Merchich datum, for example Nord Maroc, EPSG:26191). Coordinates from different sources can therefore differ for nearby points.
- Reproject each source to a common CRS before mapping or comparing locations. The maps in the article (Figures 1 and 12) were made from GIS layers reprojected to WGS 84 / UTM zone 29N (EPSG:32629).
- Samples from Rhoujjati et al. (2021) have no coordinates.
- Coordinates are not used in the statistical analyses (PCA, HCA, SOM, EMMA), so the CRS has no effect on the results.

## Note on tritium

The tritium (³H) measurements are not included in the shared file (available from the corresponding author on reasonable request). Figure SM13 of the article therefore cannot be regenerated from this repository. Three groundwater samples with a tritium analysis only (S406, S419, S437) are kept in the isotope dataset because they belong to the chloride-screening set of the EMMA notebook.
