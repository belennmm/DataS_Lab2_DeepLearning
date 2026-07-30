# 📊 Análisis de Series de Tiempo: Flujo Turístico y Visitantes

Este repositorio contiene un proyecto de **Ciencia de Datos y Análisis de Series de Tiempo** enfocado en el comportamiento histórico, la estacionalidad, los mercados emisores y las vías de ingreso del flujo receptor de visitantes (turistas + excursionistas).

---

## 📑 Tabla de Contenidos
- [Descripción del Proyecto](#-descripción-del-proyecto)
- [Estructura del Repositorio](#-estructura-del-repositorio)
- [Principales Hallazgos](#-principales-hallazgos)
  - [1. Tendencia Histórica e Impacto COVID-19](#1-tendencia-histórica-e-impacto-covid-19)
  - [2. Estacionalidad Mensual](#2-estacionalidad-mensual)
  - [3. Origines y Regiones Emisoras](#3-orígenes-y-regiones-emisoras)
  - [4. Vías de Ingreso y Fronteras](#4-vías-de-ingreso-y-fronteras)
- [Requisitos e Instalación](#-requisitos-e-instalación)
- [Uso](#-uso)

---

## 📌 Descripción del Proyecto

El objetivo de este análisis es entender la dinámica temporal del turismo receptor a lo largo de los años. Se evalúa:
* **Tendencias e Impactos Atípicos:** Evolución del volumen de viajeros (2009–presente) y el choque provocado por la pandemia.
* **Patrones Estacionales:** Identificación de meses de alta y baja afluencia histórica.
* **Geografía del Visitante:** Principales regiones y países de origen.
* **Logística de Entrada:** Participación por vía de transporte (terrestre, aérea, marítima) y puestos fronterizos más concurridos.

---

## 📂 Estructura del Repositorio

```text
DS_series_de_tiempo/
│
├── data/                  # Archivos de datos (raw y procesados)
├── figs/                  # Gráficas e imágenes generadas en el análisis
│   ├── boxplot_outliers.png
│   └── ...
├── notebooks/             # Notebooks de Jupyter con el código de análisis
├── README.md              # Documentación del proyecto
└── requirements.txt       # Lista de dependencias de Python
