## <span style="font-size: 32px; font-weight: bold; color: #003366;">Proyecto Ausentismo en la administración pública de una provincia argentina</span>

## <span style="font-size: 26px; font-weight: bold; color: #5ba6f1;">Equipo de trabajo Nro 15</span>
<ul>
  <li style="color: #81c6d2;"><b>Fabiana Winterstetter</b></li>
  <li style="color: #81c6d2;"><b>Nicolás Germán Diaz</b></li>
  <li style="color: #81c6d2;"><b>Nadir Nahuel Quiroga</b></li>
   
</ul>

El estudio de las pautas de ausentismo en las organizaciones públicas constituye un campo crítico dentro del análisis organizacional y la economía del trabajo. La disponibilidad de grandes volúmenes de datos transaccionales permite ir más allá del análisis estadístico descriptivo e incursionar en la modelación predictiva del comportamiento laboral.

Este trabajo final intenta abordar el ciclo completo de un proyecto de Data Science aplicado a la administración pública: 
<p style="font-size: 16px; line-height: 1.6;">
    <mark style="background-color: #e6f2ff; color: #003366; padding: 2px 5px; border-radius: 3px;">
    Desde la ingesta, limpieza e ingeniería de variables sobre datos reales de ausentismo, 
    hasta el entrenamiento y evaluación de algoritmos de clasificación.
    </mark>
</p>

## 📋 Tabla de Contenidos

- [Descripción del Dataset](#-descripción-del-dataset)
- [Objetivos del Proyecto](#-objetivos-del-proyecto)

---
## <span style="font-size: 24px; font-weight: bold; color: #003366;">Variables Objetivo (Target Variables)</span>

* __Cantidad_días__ (Regresión / Forecasting): Predicción directa de la duración de cada evento o del acumulado de días ausentes por agente en un período (ej. trimestre/año).  
* __Reincidencia / Alta Frecuencia__ (Clasificación Binaria): Variable derivada binaria ($1$ si el agente solicita $\ge N$ licencias en el año, $0$ en caso contrario) para identificar perfiles de riesgo.
* __Ausencia_prolongada__ (Clasificación Binaria): Define si una licencia será extensa ($1$ si supera los $3$ días, $0$ si es de $1$ a $3$ días). Útil para que la gestión de RRHH planifique reemplazos tempranos.
* __Exceso de Cupo__ (Clasificación): Predictor de si el agente superará su límite normativo anual (cantidad_dias_permitido_año).

* __Es_agente_frecuente__ (Clasificación Binaria): $1$ si el agente solicita $\ge 5$ eventos de ausencia al año, $0$ en caso contrario. Permite detectar perfiles de reincidencia. 



Este repositorio contiene un proyecto end-to-end de Ciencia de Datos orientado al **Análisis Exploratorio (EDA)** y la **Modelación Predictiva del Ausentismo Laboral** en el ámbito de la administración pública. 

A través del procesamiento y la ingeniería de características (*Feature Engineering*) sobre registros masivos de licencias, el proyecto busca identificar patrones clave de ausentismo y entrenar modelos capaces de estimar el volumen, riesgo y duración de las inasistencias.


## 📊 Descripción del Dataset

El conjunto de datos (`prueba2025_c.csv`) contiene **949,038 filas registros históricos** de licencias y ausencias de agentes públicos con 15 variables originales sin valores nulos:

| Variable | Descripción |
| :--- | :--- |
| `Nro legajo` | Identificador único del agente/empleado. |
| `Escalafon` | Agrupamiento o carrera dentro de la administración pública. |
| `Categoría` | Representa la categoría salarial a la que pertenece dentro de su escalafón. |
| `Cod Art ausencia` | Código del artículo de la licencia según la normativa laboral. |
| `Descripcion articulo ausencia` | Detalle o motivo de la ausencia (ej. *Enfermedad Común*, *Razones Particulares*). |
| `Es de Salud?` | Flag categórico (`yes` / `no`) para licencias de índole médica. |
| `Fecha Desde` / `Fecha Hasta` | Periodo de inicio y fin de la licencia tomada. |
| `Cantidad dias` | Días corridos de duración de la ausencia. |
| `Cant Dias Permitido Mes/Año` | Límites normativos de días permitidos por periodo. |
| `Dependencia` | Oficina o área de trabajo del agente. |
| `Año Nacimiento` / `Genero` | Datos demográficos del agente. |
| `Antigüedad` | Años de servicio prestados por el agente. |
| `Remuneración Mensual` | remuneración o sueldo que percibe el agente mensualmente. |

---
