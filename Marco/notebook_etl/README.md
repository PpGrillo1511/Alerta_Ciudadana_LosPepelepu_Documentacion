# 📌 ETL

## 📂 Código Fuente
Este proyecto incluye el código fuente necesario para su funcionamiento, el cual puede encontrarse en la carpeta correspondiente (`.py`, `.js`, `.java`, `.ts`) o bien en un repositorio externo.  
En caso de estar en un repositorio independiente, se puede acceder mediante el siguiente enlace:  
🔗 [Repositorio API](URL-DEL-REPOSITORIO)

---

## ⚙️ Operaciones CRUD Básicas
El sistema implementa las operaciones básicas **GET**, **POST**, **PUT**, **PATCH** y **DELETE** para la gestión de las entidades del software.  
Estas operaciones permiten:
- **GET** → Consultar datos de las entidades.
- **POST** → Crear nuevos registros.
- **PUT/PATCH** → Actualizar registros existentes.
- **DELETE** → Eliminar registros de la base de datos.

---

## 📑 Listado de Endpoints de las Entidades
| Método | Endpoint | Descripción |
|--------|----------|-------------|
| GET    | `/entidad` | Obtiene la lista de entidades registradas. |
| POST   | `/entidad` | Crea una nueva entidad. |
| PUT    | `/entidad/{id}` | Actualiza los datos de una entidad específica. |
| DELETE | `/entidad/{id}` | Elimina una entidad específica. |

---

## 🖼️ Screenshots (Capturas de Pantalla)
A continuación se muestran ejemplos de las interfaces generadas por las operaciones CRUD:  
*(Aquí puedes incluir imágenes con capturas de las pantallas del sistema)*

---

## 🤖 Endpoints que utilizan ML (Machine Learning)
El sistema cuenta con endpoints que aplican algoritmos de Machine Learning para el análisis de datos y la toma de decisiones.  
Operaciones disponibles:
- **GET** → Consultar resultados de modelos entrenados.
- **POST** → Enviar datos para obtener predicciones.
- **PUT/PATCH** → Actualizar configuraciones del modelo.
- **DELETE** → Eliminar modelos entrenados.

---

## 📑 Listado de Endpoints que consumen ML
| Método | Endpoint | Descripción |
|--------|----------|-------------|
| GET    | `/ml/predict` | Devuelve predicciones basadas en el modelo entrenado. |
| POST   | `/ml/train` | Entrena un nuevo modelo con los datos proporcionados. |

---

## 🖼️ Screenshots (Capturas de Pantalla de ML)
Se incluyen imágenes que muestran ejemplos de:
- Análisis supervisado.
- Análisis no supervisado.
*(Aquí agregar capturas relacionadas con ML)*

---
✍ **Autor:** *[Tu nombre o equipo de desarrollo]*  
📅 **Última actualización:** *Agosto 2025*  
