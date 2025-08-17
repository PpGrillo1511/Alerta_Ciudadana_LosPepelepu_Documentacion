# 📊 Análisis Supervisado – Base de Datos Alerta Ciudadana

![Estado](https://img.shields.io/badge/Proyecto-Activo-brightgreen) ![MySQL](https://img.shields.io/badge/MySQL-8.0-blue) ![Análisis](https://img.shields.io/badge/Tipo-Supervisado-orange)

## 📝 Descripción

La base de datos **Alerta Ciudadana** ha sido diseñada para gestionar incidentes reportados por la ciudadanía, con el objetivo de mejorar la seguridad y atención de emergencias en entornos urbanos.  
Este esquema permite registrar incidentes, usuarios, categorías y comentarios relacionados, generando un repositorio estructurado de información que puede ser aprovechado para **modelos de aprendizaje supervisado**.


## 🗂️ Tablas principales

- **`categorias`**  
  Contiene los tipos de incidentes registrados (ej. seguridad pública, emergencias, infraestructura urbana).

- **`comentarios`**  
  Almacena las observaciones adicionales de los incidentes reportados.

- **`incidentes`**  
  Tabla central que guarda los reportes de incidentes, incluyendo descripción, ubicación, fecha, estado y categoría asociada.

- **`usuarios`**  
  Información de los ciudadanos que reportan incidentes en la plataforma.


## 🎯 Enfoque de Análisis Supervisado

El análisis supervisado requiere **features (X)** y una **variable objetivo (y)**.  
En este caso, algunas opciones son:

- **Variable objetivo (y):**
  - Categoría del incidente (`categorias`).
  - Estado del incidente (ej. resuelto / no resuelto, si existe en `incidentes`).

- **Features (X):**
  - Texto de descripción del incidente.  
  - Fecha y hora del reporte.  
  - Ubicación geográfica.  
  - Usuario que reporta.  
  - Comentarios asociados.


## 🔎 Posibles Modelos de Machine Learning

- **Clasificación supervisada:**  
  - Predecir la categoría de un incidente a partir de su descripción.  
  - Determinar si un incidente será resuelto rápidamente o no.  

- **Regresión supervisada:**  
  - Estimar el tiempo de resolución de un incidente según sus características.

- **Procesamiento de Lenguaje Natural (NLP):**  
  - Análisis de descripciones para identificar palabras clave que permitan clasificar automáticamente los incidentes.


## 🚀 Próximos Pasos

1. Normalizar y limpiar los datos de `incidentes` y `comentarios`.  
2. Generar un dataset unificado con features y variable objetivo.  
3. Dividir el dataset en **entrenamiento (train)** y **prueba (test)**.  
4. Entrenar modelos supervisados de clasificación o regresión.  


## 📌 Notas

- Motor de base de datos: **MySQL 8.0**  
- Proyecto: **Alerta Ciudadana**  
- Enfoque: **Aprendizaje Supervisado aplicado a incidentes urbanos**



