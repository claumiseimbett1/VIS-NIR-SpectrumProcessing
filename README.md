# VIS–NIR Spectrum Processing

Python notebooks for computing **reflectance values** and **29 vegetation indices** from VIS–NIR spectral measurements.

These codes were developed within the framework of **AGROSAVIA** research by **Claudia Milena Serpa Imbett** (Postdoctoral fellowship, 2023–2025). Related work also connects to the SATREPS–F7 / Minciencias project context documented in the notebooks.

[Versión en español](README_ES.md)

## Instrumentation

| Item | Description |
|------|-------------|
| Spectroradiometer | Ocean Insight **SR-4VN500-5** VIS–NIR |
| Spectral range | **350–1100 nm** |
| Optics | **Ghersum** fiber tubes |

## Repository contents

| Notebook | Purpose |
|----------|---------|
| `1-READ_SPECTRUM.ipynb` | Load and plot a single reflectance spectrum from Ocean Insight `.txt` exports |
| `2-SPECTRUM_PROCESSING_SINGLE.ipynb` | Process one spectrum: band reflectances, 29 vegetation indices, green peak, and red-edge slope; export CSV |
| `3-SPECTRUM_PROCESSING_GROUP.ipynb` | Average multiple replicate spectra, then compute the same spectral signature and related diagnostics |

## Workflow overview

1. **Load** tab-separated reflectance files (Ocean Insight format; header rows skipped).
2. **Clean** reflectance values to the valid range \(0 \leq \%R \leq 100\).
3. **Extract** mean reflectance at key bands:
   - Blue (~450 nm), Green (~560 nm), Red (~668 nm), Red-edge (~717 nm), NIR (~840 nm)
4. **Compute** 29 vegetation indices (see below).
5. **Derive** additional spectral features:
   - Green peak reflectance
   - Red-edge slope (≈680–730 nm)
6. **Export** the spectral signature to CSV.

## Vegetation indices (29)

**Aligned with commercial drone-type indices (3):** NDVI, GNDVI, NDRED

**Additional indices (26):** SRI, TVI, SAVI, OSAVI, ARVI, SARVI, SARVI2, EVI2, NLI, VARI, CLGR, CLRE, NDWI, RDVI, WDRVI, NGRVI, GRVI, LAI, ARI1, ARI2, BGI, BRI, NPCI, NPQI, PSRI, SIPI

## Requirements

- Python 3
- [NumPy](https://numpy.org/)
- [Polars](https://pola.rs/)
- [Matplotlib](https://matplotlib.org/)
- [Seaborn](https://seaborn.pydata.org/)
- [SciPy](https://scipy.org/) (used in the read notebook)
- Jupyter Notebook or JupyterLab

Install example:

```bash
pip install numpy polars matplotlib seaborn scipy jupyter
```

## How to use

1. Open the notebook that matches your case (single spectrum or group average).
2. Set the working directory path to the folder that contains your Ocean Insight reflectance `.txt` files.
3. Update the input file name(s) as needed.
4. Run all cells.
5. Results are written as CSV files (e.g. `SpectralSignature.cvs` / `SpectralSigProcessed.csv`), including vegetation indices, band reflectances, green peak, and red-edge slope.

> **Note:** Paths in the notebooks point to local AGROSAVIA data folders. Change them to your own measurement directories before running.

## Author and affiliation

**Claudia Milena Serpa Imbett**  
Postdoctoral researcher, 2023–2025  
Developed for **AGROSAVIA** spectral analysis of VIS–NIR plant reflectance data.
