# 📊 Análisis No Supervisado -- Base de Datos Alerta Ciudadana

**Estado MySQL Análisis**

------------------------------------------------------------------------

## 📝 Descripción

La base de datos **Alerta Ciudadana (V2)** permite gestionar incidentes
urbanos reportados por la ciudadanía.\
En este enfoque de **aprendizaje no supervisado**, el objetivo es
**descubrir patrones ocultos y segmentaciones** dentro de los datos
**sin una variable objetivo definida**.

Este análisis se centra en aplicar técnicas de **clustering y reducción
de dimensionalidad** para entender mejor el comportamiento de los
incidentes, categorías y usuarios, con el fin de apoyar la **gestión
urbana y la toma de decisiones**.

------------------------------------------------------------------------

## 🗂️ Tablas principales

-   **categorias**\
    Define los tipos de incidentes (ej. seguridad pública, emergencias,
    infraestructura urbana).

-   **comentarios**\
    Observaciones adicionales o retroalimentación ciudadana sobre los
    incidentes.

-   **incidentes**\
    Tabla central con los reportes: descripción, ubicación, fecha,
    estado y categoría asociada.

-   **usuarios**\
    Información básica de los ciudadanos que realizan los reportes.

------------------------------------------------------------------------

## 🎯 Enfoque de Análisis No Supervisado

A diferencia del análisis supervisado, **no existe una variable objetivo
(y)** predefinida.\
En su lugar, buscamos **grupos o clústeres** de incidentes que compartan
similitudes en sus características.

**Posibles features (X):**\
- Texto de descripción del incidente.\
- Palabras clave de comentarios asociados.\
- Ubicación geográfica (coordenadas o zonas).\
- Fecha y hora del reporte.\
- Categoría del incidente.

------------------------------------------------------------------------

## 🔎 Posibles Modelos de Machine Learning

-   **Clustering (agrupamiento):**
    -   **K-Means** → segmentación de incidentes por similitudes
        textuales o geográficas.\
    -   **DBSCAN / HDBSCAN** → detección de incidentes atípicos
        (outliers o anomalías).\
    -   **Clustering jerárquico** → clasificación jerárquica de
        incidentes por similitud.
-   **Reducción de dimensionalidad:**
    -   **PCA (Análisis de Componentes Principales)** → simplificar
        variables numéricas.\
    -   **UMAP / t-SNE** → visualización de incidentes en 2D o 3D para
        detectar grupos naturales.
-   **Procesamiento de Lenguaje Natural (NLP):**
    -   Extracción de temas o keywords en descripciones de incidentes.\
    -   Embeddings de texto para mejorar el clustering semántico.

------------------------------------------------------------------------

## 🚀 Próximos Pasos

1.  **Extracción y limpieza de datos** desde MySQL (`incidentes`,
    `categorias`, `comentarios`).\
2.  **Normalización y vectorización de texto** (TF-IDF, embeddings).\
3.  **Construcción del dataset de features (X)**.\
4.  **Aplicar algoritmos de clustering** (K-Means, DBSCAN, HDBSCAN).\
5.  **Visualizar resultados** con PCA / UMAP para interpretar los
    grupos.\
6.  **Perfilado de clústeres:** identificar patrones en categorías,
    ubicaciones y horarios.

------------------------------------------------------------------------

## 📌 Notas

-   **Motor de base de datos:** MySQL 8.0\
-   **Proyecto:** Alerta Ciudadana\
-   **Enfoque:** Aprendizaje **No Supervisado** aplicado a incidentes
    urbanos\
-   **Objetivo:** Identificación de patrones y agrupamientos de
    incidentes para mejorar la gestión ciudadana.

------------------------------------------------------------------------

👤 Autoría: **Griselda Cabrera Franco**
