# Actividades-de-las-tareas
Actividades relacionadas con las tareas asignadas durante el curso, específicamente en la Semana pre-Hackatón para los días martes y jueves.

¿De qué trata éste repositorio?
El presente repositorio contiene las actividades realizadas para entrega de semana previa al Hackatón Intercoonecta, cuyo objetivo principal consistió en realizar el procesamiento, exploración y visualización de datos meteorológicos disponibles en los materiales de estudio empleando el lenguaje R, el entorno en la nube JupyterHub (Git/GitHub).
Estructura general del repositorio

a) Descripción del conjunto de datos

El análisis utiliza la base de datos meteorológicos recolectados por el CIBNOR en la zona costera de La Paz, Baja California Sur, México. Derivado de lo cual, fue posible observar de manera general lo siguiente:
* Registros totales: se obtuvieron 17,364 observaciones cada 30 minutos.
* Cobertura temporal: se contempló un clico anual de junio de 2006 a diciembre de 2007.

Las principales variables consideradas fueron las siguientes: 
* Temperatura del aire (°C), crítica para el intercambio térmico entre el océano- atmósfera.
* Humedad relativa (%), vinculada íntimamente con la evaporación costera.
* Velocidad del viento (m/s): clave para el mezclado vertical y procesos de afloramiento (upwelling).
* Dirección del viento en grados azimutales (0 a 360°).

Actividad 1: Carga y exploración de datos

* Conversión de datos: se utilizó el código en R para exportar.
* Exploración de datos: se cargaron CSV para realizar la inspección de dimensiones tipos de variables y resumen estadístico de los datos.
* Control de versiones: registro del primer commit en GitHub.

Actividad 2: Funciones documentadas y visualización de gráficos realizados en R
* Función propia: implementación de documentada con Roxygen2 para filtrar observaciones y calcular estadísticos agregados.
* Visualización 1: generación de Boxplot diurno de temperatura horaria con gradiente cromático continuo.
* Visualización 2: elaboración de gráfico de dispersión y regresión lineal simple para establecer la relación existente entre humedad relativa y la temperatura.
* Control de versiones: registro del segundo commit en GitHub.

Guía práctica de replicación de código en JupyterHub

1. Clonar o abrir el repositorio en la sesión de JupyterHub de Intercoonecta.
2. Seleccionar el Kernel de R en JupyterLab.
3. Ejecutar celdas en cada notebook de la carpeta “Tareas_Eduardo”.
4. Subida a GitHub. 
