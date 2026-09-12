# Nacimientos 2018–2019: del dato a la teoría de probabilidad

Análisis estadístico que contrasta el modelo teórico de nacimientos uniformemente distribuidos a lo largo del año (`P(fecha) = 1/365`) contra datos reales de nacimientos de 2018 y 2019, y utiliza los resultados para construir formalmente un espacio de probabilidad `(Ω, ℱ, P)`.

## Archivos del proyecto

| Archivo | Descripción |
|---|---|
| `analisis_nacimientos_2018_2019.ipynb` | Notebook principal (Google Colab / Jupyter) con todo el análisis |
| `nacimientos_2018.xlsx` | Dataset de nacimientos de 2018 (`fecha_nacimiento`, `genero_nacido`) |
| `nacimientos_2019.csv` | Dataset de nacimientos de 2019 (`fecha_nacimiento`, `genero_nacido`, `descripcion_subtipo`) |

## Cómo correr el notebook

1. Abrir `analisis_nacimientos_2018_2019.ipynb` en [Google Colab](https://colab.research.google.com/) (o Jupyter local).
2. Ejecutar todas las celdas en orden (`Entorno de ejecución → Ejecutar todas`).
3. Si los archivos `nacimientos_2018.xlsx` y `nacimientos_2019.csv` no están en el entorno, el notebook detecta que corre en Colab y pide subirlos automáticamente (`files.upload()`). Si se ejecuta localmente, alcanza con tener ambos archivos en el mismo directorio que el notebook.

**Requisitos:** `pandas`, `numpy`, `matplotlib`, `scipy` (todas vienen preinstaladas en Google Colab).

## ⚠️ Limitación clave de los datos

`nacimientos_2019.csv` **solo contiene registros desde el 1 de enero hasta el 31 de agosto de 2019** (243 días, no 365). No hay ningún nacimiento cargado para septiembre–diciembre de 2019 en el archivo entregado — no significa que no hayan ocurrido, sino que no están en este dataset.

Por eso el notebook:
- Analiza cada año **por separado** con los datos realmente disponibles.
- Restringe las comparaciones **entre 2018 y 2019** al período común (enero–agosto, días 1 a 243 del año) o usa promedios por día en vez de totales, para que la distinta duración de cada serie no distorsione las conclusiones.

## Estructura del notebook

1. **Introducción** — objetivo del análisis y datasets utilizados.
2. **Carga e inspección** — shape, tipos, nulos, formato de fechas, cobertura temporal real de cada archivo.
3. **Análisis exploratorio**
   - A. Nacimientos por mes (totales, % y promedio por día).
   - B. Nacimientos por día del año (1–365), picos principales.
   - C. Fechas puntuales con más nacimientos (con aclaración de que no implica "coincidencias entre personas").
4. **Visualización** — barras por mes, series por día del año (2018, 2019 y comparación en el rango común), y distribución por día de la semana.
5. **Espacio de probabilidad (Ω, ℱ, P)** — definición de Ω bajo dos interpretaciones (días del calendario vs. registros del dataset), ejemplos de sucesos en ℱ, probabilidad teórica (`1/365`) y probabilidad empírica calculada sobre los datos.
6. **Comparación teoría vs. realidad** — prueba de bondad de ajuste chi-cuadrado contra el modelo uniforme, y prueba específica para el efecto de fin de semana.
7. **Conclusión** — síntesis de hallazgos y respuesta a las preguntas guía del trabajo.

## Principales hallazgos

- **Efecto de fin de semana (el hallazgo más fuerte):** en 2018, promedio de ~207 nacimientos/día hábil vs. ~131/día de fin de semana; en 2019 (ene-ago), ~189 vs. ~120. Patrón consistente entre ambos años.
- **Patrón mensual:** marzo es el mes con más nacimientos en los dos años; diciembre es el mínimo en 2018.
- **Prueba chi-cuadrado:** rechaza la hipótesis de uniformidad en ambos años (`p < 0,001`), principalmente por el efecto de fin de semana.
- **Probabilidad teórica vs. empírica:** para sucesos neutros respecto del calendario semanal (ej. nacer en un mes dado) la probabilidad empírica se acerca a la teórica; para sucesos ligados al día de la semana (fin de semana) la diferencia es grande (~20% empírico vs. ~28,6% teórico).
- **Posible limitación adicional:** caída de nacimientos hacia fin de agosto de 2019, tratada como posible efecto de carga incompleta de los últimos registros del archivo y no como patrón estacional real.

## Metodología estadística

- **Modelo teórico:** distribución uniforme discreta sobre los 365 días del año → `P(fecha) = 1/365`.
- **Modelo empírico:** frecuencia relativa observada en cada dataset → `P_empírica(suceso) = casos favorables / total de registros`.
- **Test de hipótesis:** bondad de ajuste chi-cuadrado (`scipy.stats.chisquare`), `α = 0,05`.
