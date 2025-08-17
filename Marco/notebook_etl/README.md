# 🌐 Proceso ETL — Extracción, Transformación y Carga

Este módulo documenta el flujo **ETL** desarrollado para preparar los datos del proyecto **Alerta Ciudadana**.  
El objetivo es transformar los datos en bruto en un **dataset limpio y estructurado**, listo para análisis avanzados y carga en el Data Warehouse.

---

## 🔎 Fases del Proceso

### 1️⃣ Importación de Librerías
Se cargan las librerías necesarias para la manipulación y visualización de datos:  
`pandas`, `numpy`, `matplotlib`, `seaborn`, entre otras.

---

### 2️⃣ Carga de Datos
- Lectura desde la fuente definida (**MySQL**).  
- Validación de la estructura y los tipos de datos.  
- Verificación de la integridad inicial de las tablas.

---

### 3️⃣ Creación del DataFrame
- Construcción del **DataFrame principal** consolidando información de varias tablas.  
- Normalización de nombres de columnas.  
- Definición de índices para optimizar consultas.

---

### 4️⃣ Análisis Exploratorio de Datos (EDA)
- Estadísticos descriptivos: media, mediana, desviación estándar.  
- Distribución de variables principales.  
- Identificación de valores atípicos y datos faltantes.

---

### 5️⃣ Limpieza de Datos
- Eliminación o imputación de valores nulos.  
- Estandarización de **formatos de fechas, textos y categorías**.  
- Corrección de inconsistencias y duplicados.  

---

### 6️⃣ Visualización de Datos
Se generan entre **5 gráficas clave** para comprender el comportamiento de los datos:  
- Histogramas y distribuciones.  
- Diagramas de dispersión.  
- Gráficas de tendencia temporal.  
- Mapas o dispersión geográfica de incidentes.

---

### 7️⃣ Conclusiones de la Fase
- Resumen de hallazgos relevantes en los datos.  
- Decisiones tomadas respecto a qué información se mantiene, transforma o descarta.  
- El dataset final queda **listo para análisis supervisado / no supervisado** o su carga en el **Data Warehouse**.

---

## 📂 Evidencias
- **Notebook** en formato `.ipynb` dentro de esta carpeta.  

---
