# Data Science Project: Análisis y Predicción de Ausentismo en la Administración Pública

[![Python 3.14+](https://img.shields.io/badge/python-3.14+-blue.svg)](https://www.python.org/downloads/) [![Pandas](https://img.shields.io/badge/pandas-1.5+-150458.svg)](https://pandas.pydata.org/) [![Scikit-Learn](https://img.shields.io/badge/scikit--learn-1.0+-F7931E.svg)](https://scikit-learn.org/)

Este repositorio contiene un proyecto end-to-end de Ciencia de Datos orientado al **Análisis Exploratorio (EDA)** y la **Modelación Predictiva del Ausentismo Laboral** en el ámbito de la administración pública. 

A través del procesamiento y la ingeniería de características (*Feature Engineering*) sobre registros masivos de licencias, el proyecto busca identificar patrones clave de ausentismo y entrenar modelos capaces de estimar el tipo de inasistencias, volumen, riesgo, duración de las mismas, etc.


---

## <span style="font-size: 26px; font-weight: bold; color: #0d3c6c;">Equipo de trabajo Nro 15</span>
<span style="font-size: 18px; font-weight: bold; color: #0d3c6c;">
  <!-- Icono SVG escalado a 34px para acompañar el texto grande -->
  <svg xmlns="http://w3.org" width="34" height="34" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round" style="vertical-align: middle; margin-right: 10px; color: #0d3c6c;">
    <path d="M16 21v-2a4 4 0 0 0-4-4H6a4 4 0 0 0-4 4v2" />
    <circle cx="9" cy="7" r="4" />
    <path d="M22 21v-2a4 4 0 0 0-3-3.87" />
    <path d="M16 3.13a4 4 0 0 1 0 7.75" />
  </svg><b>Sobre Nosotros</b></span>
<ul>
  <li style="color: #81c6d2;"><b>Fabiana Winterstetter</b></li>
  Soy ingeniera en sistemas y desde hace 30 años trabajo en una empresa en la que nos dedicamos a hacer sistemas para gestion financiera y de RRHH en la Administración Pública. </br>
  Siempre me gustaron los desafíos y mi curiosidad es interminable, a pesar de los años que han pasado de carrera siempre quiero aprender cosas nuevas. Empecé con Análisis de Datos y me anoté en este curso para dar el siguiente paso.
  <li style="color: #81c6d2;"><b>Nicolás Germán Diaz</b></li>
  Soy Técnico electrónico, actualmente me desempeño en el área de Calidad en una empresa ferroviaria. Entusiasta de la tecnología y de las nuevas herramientas. 
  Trato de conocer más de los temas que me interesan, en los últimos años realicé cursos de programación, base de datos, automatización con n8n y ahora me encuentro realizando este curso de Data Science. Creo que es importante actualizarse, desarrollar nuevas habilidades y siempre seguir aprendiendo.
  
  <li style="color: #81c6d2;"><b>Nadir Nahuel Quiroga</b></li>
   
</ul>

---

## 📋 Tabla de Contenidos

- [Descripción del Dataset](#-descripción-del-dataset)
- [Objetivos del Proyecto](#-objetivos-del-proyecto)
- [Ingeniería de Variables (Feature Engineering)](#-ingeniería-de-variables-feature-engineering)
- [Modelos Predictivos Propuestos](#-modelos-predictivos-propuestos)

---

## 📊 Descripción del Dataset
Este dataset contiene datos sobre el ausentismo (faltas), en la administración pública de una provincia Argentina. 
Por razones de confidencialidad no se dan mayores datos sobre la provincia a la que pertenecen los datos, ya que los mismos se obtuvieron del sistema de registración de faltas y novedades.
El conjunto de datos obtenidos se almacenaron en un archivo csv (`prueba2025_b.csv`). Contiene **949,038 registros históricos** de licencias y ausencias de agentes públicos con 16 variables originales sin valores nulos:

| Variable | Descripción |
| :--- | :--- |
| `Nro legajo` | Identificador único del agente/empleado. |
| `Escalafon` | Agrupamiento o carrera dentro de la administración pública. |
| `Categoría` | Categoría o clase dentro del escalafón de la administración pública. |
| `Cod Art ausencia` | Código del artículo de la licencia según la normativa laboral. |
| `Descripcion articulo ausencia` | Detalle o motivo de la ausencia (ej. *Enfermedad Común*, *Razones Particulares*). |
| `Es de Salud?` | Flag categórico (`yes` / `no`) para licencias de índole médica. |
| `Fecha Desde` / `Fecha Hasta` | Periodo de inicio y fin de la licencia tomada. |
| `Cantidad dias` | Días corridos de duración de la ausencia. |
| `Cant Dias Permitido Mes/Año` | Límites normativos de días permitidos por periodo. |
| `Dependencia` | Oficina o área de trabajo del agente. |
| `Año Nacimiento` / `Genero` | Datos demográficos del agente. |
| `Género (Sexo)` |  |
| `Antigüedad` | Años de servicio prestados por el agente. |
| `Remuneración Mensual` | Sueldo que percibe el agente mensualmente. |

---

## 🎯 Objetivos del Proyecto

1. **Análisis Exploratorio de Datos (EDA):** Identificar la estacionalidad, los artículos de licencia más solicitados y las métricas de ausentismo según rango etario, género, antigüedad y dependencia.
2. **Feature Engineering Temporal y Acumulado:** Derivar variables continuas y categóricas a partir de los datos históricos de cada legajo.
3. **Predicción de Licencias por "Razones Particulares" u Otras Causas No Médicas**
   Predecir si una solicitud de ausencia iniciada en determinado día corresponderá a Razones Particulares / Permisos frente a Salud.

---

## 💡 Ingeniería de Variables (Feature Engineering)

El pipeline de preparación transforma el dataset original agregando las siguientes dimensiones de análisis:

* **Variables Temporales y Estacionales:**
  * `Edad_Agente`: Edad calculada al momento del evento.
  * `Mes_Inicio` y `Trimestre`: Estacionalidad anual (picos invernales / fin de año).
  * `Es_Fin_De_Semana_Adyacente`: Indicador de inicio en día Lunes/Viernes ("efecto puente").

---

## 🤖 Modelos Predictivos Propuestos

1. **Clasificación Supervisada (Predecir si una falta es de salud o razon particular):**
   * *Algoritmos:* kNN, SVM, Random Forest.
   * *Métricas:* ROC-AUC, F1-Score, Precision-Recall Curve.
2. **Validación cruzada** y optimización de hiperparámetros

---

