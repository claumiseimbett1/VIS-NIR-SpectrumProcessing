# Procesamiento de espectros VIS–NIR

Notebooks en Python para calcular **valores de reflectancia** e **índices de vegetación (29)** a partir de mediciones espectrales VIS–NIR.

Estos códigos fueron desarrollados en el marco del trabajo de **AGROSAVIA**, por **Claudia Milena Serpa Imbett** (Posdoctorado, 2023–2025). El contexto de los notebooks también se relaciona con el proyecto SATREPS–F7 / Minciencias.

[English version](README.md)

## Instrumentación

| Elemento | Descripción |
|----------|-------------|
| Espectrorradiómetro | Ocean Insight **SR-4VN500-5** VIS–NIR |
| Rango espectral | **350–1100 nm** |
| Óptica | Tubos de fibra **Ghersum** |

## Contenido del repositorio

| Notebook | Propósito |
|----------|-----------|
| `1-READ_SPECTRUM.ipynb` | Cargar y graficar un espectro de reflectancia exportado por Ocean Insight (`.txt`) |
| `2-SPECTRUM_PROCESSING_SINGLE.ipynb` | Procesar un espectro: reflectancias por banda, 29 índices de vegetación, pico del verde y pendiente del red-edge; exportar CSV |
| `3-SPECTRUM_PROCESSING_GROUP.ipynb` | Promediar varios espectros réplica y calcular la misma firma espectral y diagnósticos asociados |

## Flujo de trabajo

1. **Cargar** archivos de reflectancia separados por tabulaciones (formato Ocean Insight; se omiten las filas de encabezado).
2. **Limpiar** los valores de reflectancia al rango válido \(0 \leq \%R \leq 100\).
3. **Extraer** la reflectancia media en bandas de interés:
   - Azul (~450 nm), Verde (~560 nm), Rojo (~668 nm), Red-edge (~717 nm), NIR (~840 nm)
4. **Calcular** 29 índices de vegetación (ver abajo).
5. **Obtener** características espectrales adicionales:
   - Reflectancia en el pico del verde
   - Pendiente del red-edge (≈680–730 nm)
6. **Exportar** la firma espectral a CSV.

## Índices de vegetación (29)

**Coincidentes con índices tipo dron comercial (3):** NDVI, GNDVI, NDRED

**Otros índices (26):** SRI, TVI, SAVI, OSAVI, ARVI, SARVI, SARVI2, EVI2, NLI, VARI, CLGR, CLRE, NDWI, RDVI, WDRVI, NGRVI, GRVI, LAI, ARI1, ARI2, BGI, BRI, NPCI, NPQI, PSRI, SIPI

## Requisitos

- Python 3
- [NumPy](https://numpy.org/)
- [Polars](https://pola.rs/)
- [Matplotlib](https://matplotlib.org/)
- [Seaborn](https://seaborn.pydata.org/)
- [SciPy](https://scipy.org/) (usado en el notebook de lectura)
- Jupyter Notebook o JupyterLab

Ejemplo de instalación:

```bash
pip install numpy polars matplotlib seaborn scipy jupyter
```

## Cómo usar

1. Abra el notebook según el caso (espectro individual o promedio de grupo).
2. Configure la ruta del directorio de trabajo a la carpeta con los archivos `.txt` de reflectancia de Ocean Insight.
3. Actualice el o los nombres de archivo de entrada según corresponda.
4. Ejecute todas las celdas.
5. Los resultados se guardan en CSV (p. ej. `SpectralSignature.cvs` / `SpectralSigProcessed.csv`), con índices de vegetación, reflectancias por banda, pico del verde y pendiente del red-edge.

> **Nota:** Las rutas en los notebooks apuntan a carpetas locales de datos de AGROSAVIA. Cámbielas a sus propios directorios de medición antes de ejecutar.

## Autora y afiliación

**Claudia Milena Serpa Imbett**  
Investigadora posdoctoral, 2023–2025  
Desarrollado para el análisis espectral de reflectancia vegetal VIS–NIR en **AGROSAVIA**.

## Licencia

**Licencia propietaria / cerrada.** Todos los derechos reservados.  
Consulte [LICENSE](LICENSE) para los términos. El uso, copia, modificación o distribución requiere autorización previa por escrito del titular o titulares de los derechos.
