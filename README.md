# 🏦 End-to-End Loan Scoring Pipeline: Modular Feature Engineering & MLOps

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1kG1FinQY_8z0tHSCShVfcaT5boDGvTsP?usp=sharing)

## 📌 Descripción del Proyecto
Este repositorio presenta la implementación de un sistema de **Credit Scoring** utilizando una arquitectura de Pipeline robusta en Python. El proyecto nace de un desafío común en el mundo real: trabajar con **datos sintéticos de baja capacidad discriminatoria**, donde el éxito no depende solo del algoritmo, sino de la calidad del preprocesamiento y la ingeniería de variables.

El objetivo principal es demostrar la creación de un flujo de trabajo automatizado, modular y libre de *Data Leakage*, escalable a entornos de producción.

## 🛠️ Innovaciones Técnicas

### 1. Arquitectura de Pipeline Modular
En lugar de scripts lineales, el proyecto utiliza `Pipeline` y `ColumnTransformer` de **Scikit-Learn** para orquestar:
* **Ingeniería de Ratios:** Generación automática de métricas financieras (ej. Loan-to-Income).
* **Agregación de Activos:** Consolidación de múltiples fuentes de patrimonio en una sola variable robusta (`total_asset`).
* **Tratamiento de Texto:** Limpieza y normalización de variables categóricas.

### 2. Framework de Weight of Evidence (WoE) & IV
Se desarrolló un transformador personalizado (`WoeGenerator`) que:
* **Automatiza el Binning:** Discretiza variables numéricas basándose en cuantiles.
* **Previene el Data Leakage:** Aprende los límites de los intervalos (*bin edges*) en el entrenamiento y los aplica estrictamente en la inferencia.
* **Selección de Variables:** Implementa un filtro basado en **Information Value (IV)** para descartar automáticamente variables con ruido estadístico, optimizando la parsimonia del modelo.

### 3. Manejo de Datos con Baja Señal
Ante un dataset con distribuciones altamente solapadas, se aplicaron técnicas de **Econometría y Machine Learning** para extraer señal:
* Uso de `class_weight='balanced'` para manejar el desbalance de clases.
* Transformación logarítmica de cuotas para linealizar la relación con el default.

## 📈 Resultados
A pesar de la naturaleza limitada de la data, la arquitectura de procesamiento permitió que una **Regresión Logística** (modelo altamente interpretable y estándar en Basilea/IFRS9) alcanzara niveles de desempeño competitivos:

* **Accuracy:** 96%
* **F1-Score (Rejected):** 0.95
* **Variables Clave:** `cibil_score`, `loan_income_ratio`, `total_asset`.

## 🚀 Cómo usar este Repositorio
1. Clona el repositorio.
2. Abre el notebook en Google Colab mediante el badge superior.
3. Asegúrate de tener instaladas las dependencias: `scikit-learn >= 1.2`, `pandas`, `numpy`.

## 👤 Autor
**Luis Mauricio** *Estudiante de Economía - UNMSM* *Interesado en Data Science, Econometría y MLOps.*
