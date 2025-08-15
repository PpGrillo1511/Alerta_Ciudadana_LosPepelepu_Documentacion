# 📊 Generador de Datos de Prueba

Este módulo permite la creación y carga de datos simulados para entornos de desarrollo y pruebas.

---

## 🛠 Código y Repositorio
El código fuente se encuentra incluido en este proyecto.  
En caso de estar integrado al repositorio del API, puedes acceder directamente aquí:  
🔗 **[Ver Repositorio del API](https://github.com/PpGrillo1511/Alerta_Ciudadana_LosPepelepu_API.git)**

---

## 📂 Estructura de Base de Datos (Vacía)
Archivo **`estructura_bd.sql`** que contiene únicamente el esquema de la base de datos, sin registros, para iniciar un entorno limpio de pruebas.

---

## 🚀 Endpoints Disponibles
| Ruta         | Método | Funcionalidad                                                                                  |
|--------------|--------|------------------------------------------------------------------------------------------------|
| `/seeder`    | POST   | Inserta un conjunto masivo de datos simulados (1 millón de usuarios, incidentes y comentarios).|
| `/usuario`   | POST   | Inserta un usuario con los datos requeridos.                                                   |
| `/categoria` | POST   | Inserta las categorias ya predefinidas.                                                        |
| `/comentario`| POST   | Inserta un comentario con los datos requeridos.                                                |
| `/incidente` | POST   | Inserta un incidente con los datos requeridos.                                                 |

---

## 🖼 Registro Visual
Imágenes y capturas de pantalla que muestran la ejecución y respuesta de los endpoints encargados de generar los datos.

---

## 💾 Base de Datos Poblada
Archivo **`AlertaCiudadana_BD.sql`** con la base de datos ya cargada con información simulada.  
Este respaldo es utilizado para pruebas avanzadas y procesos de análisis.

---
