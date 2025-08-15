
# Propuesta de Datawarehouse — AlertaCiudadana

## 1. Contexto
**AlertaCiudadana** es una plataforma (smartwatch + panel web) para reportar y analizar incidentes urbanos ( accidentes, fallas de infraestructura, riesgos, etc.).  
El objetivo de este datawarehouse (DW) es centralizar datos operacionales y contextuales para análisis, reportes y toma de decisiones: m detección de zonas críticas,accidentes

**Alcance del DW**
- Ingesta de datos operativos, datos administrativos (municipales) y fuentes contextuales (clima, tráfico, eventos).
- Diseño para análisis histórico y generación de indicadores.
- Soporte para modelos de detección de zonas críticas y predicción de incidencias.

---

## 2. Diseño conceptual (resumen)
**Arquitectura recomendada**
1. *Capa de Ingesta RAW* — colecciones/archivos con los datos originales (por ejemplo: MongoDB o S3).
2. *ETL / ELT* — procesos que limpian, transforman y conforman datos (Airflow, Prefect, scripts Python).
3. *Datawarehouse* — esquema dimensional (Postgres/Redshift/BigQuery) con tablas de hechos y dimensiones.
4. *Capa de Consumo* — dashboards (Grafana/Metabase/Power BI), APIs analíticas y exports.

**Esquema dimensional (sugerido)**
- **Fact_Reporte**(reporte_id, ciudadano_id, dim_tiempo_id, dim_ubicacion_id, categoria_id, prioridad, estado, validez, lat, lon, foto_url)
- **Dim_Ciudadano**(ciudadano_id, nombre, edad_rango, sexo, barrio)
- **Dim_Tiempo**(dim_tiempo_id, fecha, hora, dia_semana, mes, trimestre)
- **Dim_Ubicacion**(dim_ubicacion_id, sector, polígono_geo, zona_riesgo)
- **Dim_Categoria**(categoria_id, nombre_categoria)
- **Dim_Admin**(admin_id, nombre, dependencia)
- **Dim_Contexto** (opcional para clima/tráfico por tiempo-ubicación)

---

## 3. Propuesta de 3 orígenes de datos alternativos (detallados)

### 3.1 Datos operativos de la propia app (fuente principal)
- **Contenido**: reportes con timestamp, foto, descripción, categoría, lat/lon, ID usuario, estado.
- **Frecuencia**: en tiempo real (push) o batch diario.
- **Uso**: hechos principales del DW; base para métricas y mapas de calor.

### 3.2 Datos abiertos municipales / administrativos
- **Contenido**: inventario de infraestructura (iluminación, baches, alcantarillado), horarios de recolección, cuadrillas, históricos de atención de incidencias, reportes policiales abiertos.
- **Frecuencia**: diaria / semanal (según disponibilidad).
- **Uso**: enriquecer análisis causal, cross-referencia de reportes y priorización de atención.

### 3.3 Fuentes contextuales externas (clima, tráfico y eventos)
- **Contenido**: estado meteorológico (precipitación, temperatura, viento), datos de tráfico (intensidad, accidentes), calendarios de eventos locales.
- **Fuentes posibles**: APIs públicas (servicios meteorológicos), portales abiertos, Kaggle o datasets públicos.
- **Frecuencia**: horarios o cada hora.
- **Uso**: modelado predictivo; confirmar correlaciones (ej. lluvia ↔ más reportes de inundación).

---

## 4. Cinco experimentos de asociación (mezcla) de datos

> Cada experimento incluye: objetivo, datos necesarios, técnica propuesta y resultado esperado.

### Experimento 1 — Correlación clima ↔ volumen de reportes
- **Objetivo**: medir cómo variables meteorológicas afectan el número/tipo de incidencias.
- **Datos**: Fact_Reporte (por hora), datos meteorológicos (precipitación, temp).
- **Técnica**: agregación por intervalo (por hora/día), correlación (Pearson/Spearman) y regresión lineal.
- **Resultado esperado**: identificar condiciones (ej. lluvia intensa) que aumenten reportes de anegamientos o accidentes.

### Experimento 2 — Detección de hotspots espaciales
- **Objetivo**: encontrar zonas con alta concentración de reportes (persistentes en el tiempo).
- **Datos**: lat/lon de reportes, Dim_Ubicacion y tiempo.
- **Técnica**: clustering espacial (DBSCAN o HDBSCAN), mapas de calor, kernel density estimation.
- **Resultado esperado**: polígonos / puntos de intervención prioritaria.

### Experimento 3 — Clasificación de prioridad automática
- **Objetivo**: predecir prioridad (alta/media/baja) de un reporte usando texto e imagen.
- **Datos**: descripción del reporte (texto), metadatos, etiquetas históricas de prioridad.
- **Técnica**: NLP básico (TF-IDF o embeddings) + clasificador (Random Forest / XGBoost); opcional: visión (transfer learning) para fotos.
- **Resultado esperado**: modelo que sugiera prioridad para acelerar atención.

### Experimento 4 — Clustering temporal de patrones de incidentes
- **Objetivo**: agrupar horarios/días con patrones similares (picos nocturnos, fines de semana).
- **Datos**: Fact_Reporte agregados por hora/día, categoría.
- **Técnica**: series de tiempo + clustering (KMeans sobre vectores horarios) y análisis de estacionalidad.
- **Resultado esperado**: perfiles temporales para planear turnos y patrullajes.

### Experimento 5 — Análisis de efectividad de intervención
- **Objetivo**: medir si una intervención (reparación, patrullaje intensivo) reduce reportes en la zona.
- **Datos**: reportes históricos por zona y fechas de intervenciones (logs municipales).
- **Técnica**: análisis pre/post (difference-in-differences), control temporal o zonas control.
- **Resultado esperado**: evidencia cuantitativa del impacto de acciones.

---

## 5. Toma de decisiones — 5 supuestos/escenarios apoyados por el DW

1. **Reasignación de recursos (patrullas / cuadrillas)**  
   - *Supuesto*: zonas con mayor densidad de reportes y alta prioridad requieren más recursos.  
   - *Decisión*: reasignar turnos/brigadas en planificación semanal.

2. **Mantenimiento preventivo**  
   - *Supuesto*: infraestructuras con múltiples reportes menores indican fallo inminente.  
   - *Decisión*: programar intervención preventiva antes de fallas mayores.

3. **Campañas de concientización**  
   - *Supuesto*: barrios con baja participación y alto índice de incidencias necesitan comunicación.  
   - *Decisión*: ejecutar campañas locales y medir efecto con DW.

4. **Ajustes en protocolos de emergencia**  
   - *Supuesto*: durante eventos climáticos extremos la demanda de atención cambia.  
   - *Decisión*: activar protocolos de respuesta rápida y rutas alternativas.

5. **Priorización de inversión**  
   - *Supuesto*: datos históricos y modelos de predicción indican alto retorno social al invertir en iluminación en X zonas.  
   - *Decisión*: presentar priorización para presupuesto municipal.

