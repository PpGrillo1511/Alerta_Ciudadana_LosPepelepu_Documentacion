# 📊 Análisis Supervisado – Base de Datos Alerta Ciudadana

![Estado](https://img.shields.io/badge/Proyecto-Activo-brightgreen) ![MySQL](https://img.shields.io/badge/MySQL-8.0-blue) ![Análisis](https://img.shields.io/badge/Tipo-Supervisado-orange)

## 📝 Descripción

La base de datos **Alerta Ciudadana** se diseñó para gestionar incidentes reportados por la ciudadanía con el objetivo de **mejorar la seguridad y la atención a emergencias** en entornos urbanos.  
Este proyecto aplica técnicas de **aprendizaje supervisado** para predecir y clasificar incidentes, aprovechando tanto datos estructurados (categorías, usuarios, fechas) como no estructurados (descripciones).

---

## 🗂️ Tablas principales

- **`categorias`** → Tipos de incidentes (seguridad pública, emergencias, infraestructura, etc.).
- **`comentarios`** → Observaciones adicionales ligadas a los reportes.
- **`incidentes`** → Reportes principales (descripción, ubicación, fecha, estado y categoría).
- **`usuarios`** → Información de ciudadanos que realizan reportes.

---

## 🎯 Objetivo del Análisis Supervisado

El análisis busca **predecir información relevante de los incidentes** a partir de los datos registrados:

- **Variable objetivo (`y`):**
  - Categoría del incidente.
  - Estado del incidente (ej. resuelto/no resuelto).

- **Características (`X`):**
  - Texto de la descripción.
  - Fecha y hora del reporte.
  - Ubicación geográfica.
  - Usuario que reporta.
  - Comentarios asociados.

---

## 🔎 Modelos Aplicados

En el notebook se implementan y comparan distintos algoritmos supervisados:

- **Regresión Logística**
- **Random Forest**
- **XGBoost**

Cada modelo es evaluado con métricas como:

- **Accuracy**
- **Precision**
- **Recall**
- **F1-Score**
- **Matriz de confusión**

---

## 📊 Resultados Principales

- Se entrenaron modelos con un pipeline de **imputación de valores faltantes, codificación categórica y estandarización**.
- Se obtuvo un buen desempeño en la predicción de la categoría de incidentes, destacando **Random Forest y XGBoost** como los más robustos.
- Se generaron visualizaciones de métricas, importancia de variables y distribuciones de la base de datos.

---

## 🚀 Flujo de Trabajo

1. **Extracción de datos** desde MySQL.
2. **Limpieza y normalización** (manejo de nulos, codificación categórica, escalado).
3. **División del dataset** en entrenamiento y prueba.
4. **Entrenamiento de modelos supervisados**.
5. **Evaluación de métricas y visualizaciones**.
6. **Interpretación de resultados** para la toma de decisiones urbanas.

---

## 📌 Notas Técnicas

- Motor de base de datos: **MySQL 8.0**
- Lenguaje: **Python 3.10+**
- Librerías principales: `scikit-learn`, `xgboost`, `pandas`, `matplotlib`
- Proyecto: **Alerta Ciudadana**
- Enfoque: **Aprendizaje Supervisado en seguridad urbana**
