Mini-proyecto de análisis de datos meteorológicos con R

- Actividad final de la primera semana de Hackatón Interconecta-
1. Descripción general del proyecto
Este proyecto representa todo el trabajo realizado para la evaluación de la “semana pre-Hackatón” del evento Hackatón Intercoonecta. El objetivo general de trabajo es analizar la serie temporal hidro-meteorológica “cibmeteo”, misma que registrada los datos meteorológicos recabados en la zona costera de La Paz, Baja California Sur durante poco más de un año. Utilizando para el análisis de datos lenguaje R, dentro del entorno JupyterHub (Git y GitHub).
2. Estructura requerida 
El proyecto fue desarrollado conforme la arquitectura de carpetas recomendada en el material de estudio de Interconecta:
* Carga de datos.
* Exploración básica.
* Al menos una visualización.
* Una función propia.
* Conclusiones breves.

3. Conjunto de datos de la base denominada “Cibmeteo”.

a) Registros totales: en total se registraron 17,364 observaciones semi-horarias durante el muestreo.
b) Periodo de recolección de datos: junio de 2006 a diciembre de 2007.
c) Variables analizadas: las variables estudiadas fueron el año, mes, día, hora, la temperatura del aire (°C), la humedad relativa (%), velocidad (m/s) y dirección del viento.   
4. . Componentes clave del Notebook (notebook.ipynb)
* Carga de datos: se llevó a cabo la conversión del archivo base cibmeteo.txt a datos/cibmeteo.csv y lectura optimizada con la función read.csv().
* Exploración básica: inspección de dimensiones (dim), estructura de tipos de datos (str), muestreo inicial (head) y resumen descriptivo (summary) de los mismos.
* Función propia documentada: se efectuó una implementación de analizar_eventos_viento() con especificación Roxygen2, validaciones de seguridad de columnas y retorno estructurado como lista.
* Visualizaciones: se generaron tres gráficos de alta calidad con la librería “ggplot2” exportados automáticamente a la carpeta figuras/.
* Conclusiones generales: síntesis de los patrones microclimáticos y oceanográficos observados durante el análisis de los datos.


5. Código R de la función personalizada

# analizar_eventos_viento
#
# @description: filtra el dataset meteorológico según un rango de velocidad del viento (m/s) y calcula métricas descriptivas de temperatura y humedad asociada.
#
# @param df: data frame con las variables 'wind_spd', 'temperature' y 'rel_hum'.
# @param viento_min: límite inferior de velocidad del viento (m/s). Por defecto 0.
# @param viento_max: ímite superior de velocidad del viento (m/s). Por defecto 10.
#
# @return: lista con dos elementos: $estadisticas (resumen) y $datos_filtrados (subconjunto).
analizar_eventos_viento <- function(df, viento_min = 0, viento_max = 10) {cols_requeridas <- c("wind_spd", "temperature", "rel_hum")
  if (!all(cols_requeridas %in% colnames(df))) {stop("Error: El data frame no contiene las columnas requeridas (wind_spd, temperature, rel_hum).")}

  subconjunto <- df %>%
    filter(wind_spd >= viento_min & wind_spd <= viento_max)

  resumen <- subconjunto %>%
    summarise(
      n_registros      = n(),
      viento_promedio  = round(mean(wind_spd, na.rm = TRUE), 2),
      viento_maximo    = round(max(wind_spd, na.rm = TRUE), 2),
      temp_promedio    = round(mean(temperature, na.rm = TRUE), 2),
      humedad_promedio = round(mean(rel_hum, na.rm = TRUE), 2))

  return(list(estadisticas = resumen, datos_filtrados = subconjunto))}

6. Conclusiones generales del análisis de datos
Los datos obtenidos indican la serie meteorológica registra una clara oscilación diurna presentaron valores mínimos al amanecer (05:00-06:00 hrs, ~17.8 °C) y picos térmicos en las horas de máxima insolación (13:00-15:00 hrs, ~30.5 °C). Así como un acoplamiento termohigrométrico inverso, ya que existe una sólida relación inversa entre la humedad relativa y la temperatura, donde los incrementos térmicos reducen la humedad relativa debido a la capacidad de saturación de la masa de aire costera. Por último, los valores del régimen de los vientos y la ventilación sugieren que las mayores velocidades del viento ocurren en las horas más cálidas del día, favoreciendo el mezclado vertical en la interfaz mar-aire.
7. Guía de ejecución y replicación del proyecto en JupyterHub
1. Abrir el repositorio en JupyterHub (2i2c) y seleccionar el Kernel R.
2. Ejecutar todas las celdas del archivo notebook.ipynb (Run --> Run All Cells).
3. Confirmar la generación de datos/cibmeteo.csv y los archivos gráficos en figuras/.
4. Enviar los cambios finales a GitHub desde la Terminal: 
5. git add README.md notebook.ipynb datos/ figuras/
6. git commit -m "Actividad Final: Entrega del Mini Proyecto de Analisis Meteorologico" 
git push origin main

