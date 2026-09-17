# VIS–NIR Spectrum Processing / Procesamiento de espectros VIS–NIR

Python notebooks for computing **reflectance values** and **29 vegetation indices** from VIS–NIR spectral measurements.

Notebooks en Python para calcular **valores de reflectancia** e **índices de vegetación (29)** a partir de mediciones espectrales VIS–NIR.

---

## Project / Proyecto

**EN:** This work is part of the **AGROSAVIA C.I. Turipaná** project: *Processing of Spectra and Multispectral Images of Vegetation Indices using Segmentation Techniques and Artificial Intelligence for the Spatio-Temporal and Quality Characterization of Forage*.

**ES:** Este trabajo hace parte del proyecto de **AGROSAVIA C.I. Turipaná**: *Procesamiento de Espectros e Imágenes multiespectrales de índice de vegetación a partir de técnicas de Segmentación e Inteligencia Artificial para la caracterización espacio-temporal y de calidad de forraje*.

**Author / Autora:** Claudia Milena Serpa Imbett — Postdoctoral fellowship / Posdoctorado (2023–2025).

---

## Instrumentation / Instrumentación

| Item / Elemento | Description / Descripción |
|-----------------|---------------------------|
| Spectroradiometer / Espectrorradiómetro | Ocean Insight **SR-4VN500-5** VIS–NIR |
| Spectral range / Rango espectral | **350–1100 nm** |
| Optics / Óptica | Ghersum fiber tubes / Tubos de fibra **Ghersum** |

---

## Repository contents / Contenido del repositorio

| Notebook | EN | ES |
|----------|----|----|
| `1-READ_SPECTRUM.ipynb` | Load and plot a single reflectance spectrum from Ocean Insight `.txt` exports | Cargar y graficar un espectro de reflectancia exportado por Ocean Insight (`.txt`) |
| `2-SPECTRUM_PROCESSING_SINGLE.ipynb` | Process one spectrum: band reflectances, 29 vegetation indices, green peak, and red-edge slope; export CSV | Procesar un espectro: reflectancias por banda, 29 índices de vegetación, pico del verde y pendiente del red-edge; exportar CSV |
| `3-SPECTRUM_PROCESSING_GROUP.ipynb` | Average multiple replicate spectra, then compute the same spectral signature and related diagnostics | Promediar varios espectros réplica y calcular la misma firma espectral y diagnósticos asociados |

---

## Workflow / Flujo de trabajo

1. **Load / Cargar** tab-separated reflectance files (Ocean Insight format; header rows skipped) / archivos de reflectancia separados por tabulaciones (formato Ocean Insight; se omiten las filas de encabezado).
2. **Clean / Limpiar** reflectance values to the valid range / valores de reflectancia al rango válido \(0 \leq \%R \leq 100\).
3. **Extract / Extraer** mean reflectance at key bands / la reflectancia media en bandas de interés:
   - Blue/Azul (~450 nm), Green/Verde (~560 nm), Red/Rojo (~668 nm), Red-edge (~717 nm), NIR (~840 nm)
4. **Compute / Calcular** 29 vegetation indices / índices de vegetación (see below / ver abajo).
5. **Derive / Obtener** additional spectral features / características espectrales adicionales:
   - Green peak reflectance / Reflectancia en el pico del verde
   - Red-edge slope / Pendiente del red-edge (≈680–730 nm)
6. **Export / Exportar** the spectral signature to CSV / la firma espectral a CSV.

---

## Vegetation indices / Índices de vegetación (29)

**Aligned with commercial drone-type indices / Coincidentes con índices tipo dron comercial (3):** NDVI, GNDVI, NDRED

**Additional indices / Otros índices (26):** SRI, TVI, SAVI, OSAVI, ARVI, SARVI, SARVI2, EVI2, NLI, VARI, CLGR, CLRE, NDWI, RDVI, WDRVI, NGRVI, GRVI, LAI, ARI1, ARI2, BGI, BRI, NPCI, NPQI, PSRI, SIPI

---

## Requirements / Requisitos

- Python 3
- [NumPy](https://numpy.org/)
- [Polars](https://pola.rs/)
- [Matplotlib](https://matplotlib.org/)
- [Seaborn](https://seaborn.pydata.org/)
- [SciPy](https://scipy.org/) (used in the read notebook / usado en el notebook de lectura)
- Jupyter Notebook or / o JupyterLab

```bash
pip install numpy polars matplotlib seaborn scipy jupyter
```

---

## How to use / Cómo usar

1. Open the notebook that matches your case (single spectrum or group average) / Abra el notebook según el caso (espectro individual o promedio de grupo).
2. Set the working directory to the folder with Ocean Insight reflectance `.txt` files / Configure la ruta del directorio de trabajo a la carpeta con los archivos `.txt` de reflectancia.
3. Update the input file name(s) as needed / Actualice el o los nombres de archivo de entrada según corresponda.
4. Run all cells / Ejecute todas las celdas.
5. Results are written as CSV (e.g. `SpectralSignature.cvs` / `SpectralSigProcessed.csv`), including vegetation indices, band reflectances, green peak, and red-edge slope / Los resultados se guardan en CSV, con índices de vegetación, reflectancias por banda, pico del verde y pendiente del red-edge.

> **Note / Nota:** Paths in the notebooks point to local AGROSAVIA data folders. Change them to your own measurement directories before running. / Las rutas en los notebooks apuntan a carpetas locales de datos de AGROSAVIA. Cámbielas a sus propios directorios de medición antes de ejecutar.

---

## License / Licencia

**Proprietary / closed license. Licencia propietaria / cerrada.** All rights reserved / Todos los derechos reservados.

See [LICENSE](LICENSE) for terms. Use, copy, modification, or distribution requires prior written authorization from the copyright holder(s).

Consulte [LICENSE](LICENSE) para los términos. El uso, copia, modificación o distribución requiere autorización previa por escrito del titular o titulares de los derechos.
