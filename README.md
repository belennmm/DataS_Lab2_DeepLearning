# DataS_Lab2_DeepLearning

Análisis de la migración internacional (turismo/viajeros) hacia Guatemala entre **enero 2009 y junio 2026**, a partir de una base mensual de ingresos por país, región, vía de entrada y frontera. El proyecto avanza en tres etapas: análisis exploratorio de datos, caracterización estadística de series de tiempo con **catch22**, y pronóstico con **redes LSTM**.

> **Fuente de datos:** base de ingreso de viajeros internacionales a Guatemala, de uso exclusivamente académico (no son cifras oficiales).

## Contenido del repositorio

| Archivo / carpeta | Descripción |
|---|---|
| `Laboratorio 1. Series de Tiempo 2026 - Base_Migracion_2009-2026jun.xlsx` | Base de datos original (formato largo: mes, vía, frontera, país, región, tipo de viajero). |
| `migracion_guatemala_2009_2026.csv` | Misma base convertida a CSV para su uso en los notebooks. |
| `Analisis exploratorio.ipynb` | EDA: limpieza, valores faltantes/duplicados/atípicos, estadísticas descriptivas, comportamiento temporal, países/regiones/vías con mayor flujo. |
| `serie_obligatoria_total_mensual.ipynb` | Construcción de la serie mensual total de viajeros (Turista + Excursionista) y su media móvil de 12 meses. |
| `serie_viasde_ingreso.ipynb` | Construcción de las series por vía de ingreso (Aérea, Terrestre, Marítima), descomposición estacional y preparación para modelado/pronóstico. |
| `laboratorio2_catch22.ipynb` | Extracción de características **catch22** por serie, PCA, clustering, correlación entre características y mapa de distancias entre series. |
| `resultados_lstm_aerea.csv` | Resultados de la búsqueda de hiperparámetros (tuning) de los modelos LSTM entrenados sobre la serie de vía **Aérea**. |
| `figs/` | Figuras del análisis exploratorio (serie mensual/anual, estacionalidad, boxplot de atípicos, top países/regiones, vías y fronteras). |
| `figurasLab2/` | Figuras del laboratorio de catch22 (heatmap de características, matriz de correlación, dispersión y cargas de PCA, importancia de características, mapa de distancias). |

## Metodología

### 1. Análisis exploratorio (`Analisis exploratorio.ipynb`)
- Limpieza y verificación de calidad (sin valores faltantes ni duplicados tras la conversión Excel → CSV).
- Nota metodológica clave: existe un quiebre entre 2022 y 2023 en la categoría *Viajero* (trabajadores/tránsito fronterizo), por lo que el análisis usa consistentemente **Turista + Excursionista** para comparar visitantes a lo largo del tiempo.
- Serie mensual/anual: tendencia creciente 2009–2019, caída abrupta en 2020 (pandemia) y recuperación posterior.
- Ranking de países (El Salvador, Guatemala, Estados Unidos), regiones (dominadas por América del Centro) y vías/fronteras de mayor flujo (Terrestre > Aérea >> Marítima).

### 2. Caracterización con catch22 (`laboratorio2_catch22.ipynb`)
- Se extraen las 22 características catch22 para las series relevantes (total, países, regiones, vías, fronteras, tipo de viajero).
- Se analizan: matriz de correlación entre características, heatmap de características por serie, PCA (varianza explicada, cargas, importancia de características) y clustering jerárquico.
- Se calcula el mapa de distancias entre series para identificar qué series se comportan de forma similar y cuáles son atípicas.

### 3. Pronóstico con LSTM (`serie_viasde_ingreso.ipynb`)
- Construcción de las series por vía de ingreso y partición entrenamiento/prueba (70/30).
- Búsqueda de hiperparámetros (ventana temporal, unidades, dropout, learning rate, batch size) para arquitecturas **LSTM simple** y **LSTM apilada**, guardando resultados en `resultados_lstm_aerea.csv`.
- Entrenamiento del mejor modelo por serie (Aérea y Terrestre), evaluación con MAE/RMSE y comparación contra un modelo de referencia (Holt-Winters).

## Cómo ejecutar

```bash
pip install pandas numpy matplotlib seaborn scikit-learn scipy statsmodels tensorflow keras-tuner pycatch22
```

Abrir los notebooks en el orden sugerido:
1. `Analisis exploratorio.ipynb`
2. `serie_obligatoria_total_mensual.ipynb`
3. `serie_viasde_ingreso.ipynb`
4. `laboratorio2_catch22.ipynb`

## Notas y limitaciones

- Las cifras son de uso académico y no corresponden a estadísticas oficiales.
- La categoría *Viajero* no es comparable entre 2022 y 2023 por un cambio de reclasificación; se excluye de los análisis de tendencia.
- La vía Marítima tiene mucha menos cobertura temporal (pierde detalle desde ~2016/2022) que las vías Aérea y Terrestre, lo que limita su comparabilidad directa en los análisis de series de tiempo.
