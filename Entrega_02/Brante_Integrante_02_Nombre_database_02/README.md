## Explicación del Proceso de Limpieza, Decisiones y Herramientas Utilizadas

El proceso de curaduría y limpieza de los datos se diseñó en función de lo que se buscaba demostrar al relacionar la natalidad y la mortalidad neonatal. La intención periodística central fue cruzar ambas bases para construir un relato sólido que mostrara cómo, mientras la natalidad se mantiene en niveles sociodemográficamente poco saludables o experimenta caídas drásticas, la mortalidad infantil aumenta o se sostiene en cifras críticas en las zonas más afectadas por el conflicto en Gaza y Medio Oriente hasta el año 2024. Este enfoque nos permite dar cuenta de qué tan colapsado y frágil se encontraba el sistema sanitario incluso antes del comienzo de la fase más drástica del conflicto actual, utilizando esta información como una contextualización indispensable antes de presentar nuestra problemática mayor.

Para comenzar con la base de datos de la Tasa Bruta de Natalidad por cada 1.000 habitantes del Banco Mundial, se aplicó un filtro territorial centrado en los países más expuestos al conflicto en la región, acompañados por un grupo de países con índices más equilibrados que sirvieran de control. En esta selección se cuidó no incluir naciones con tasas demasiado bajas que evidenciaran un envejecimiento poblacional severo ni países con cifras desmedidas que representaran sobrepoblación, identificando que el umbral de equilibrio sociodemográfico roza los 15 puntos. Todo este trabajo de exploración, ordenamiento y filtrado de países se realizó a través de las herramientas de tablas dinámicas y filtros en Microsoft Excel, lo cual hizo que el proceso de identificación fuera mucho más sencillo y visual antes de estructurar la matriz definitiva.

Posteriormente se abordó la limpieza en torno al eje temporal. Con el objetivo de ofrecer un contexto histórico profundo, decidimos retroceder en la serie de tiempo hasta el año 1998, ya que al revisar los registros del Banco Mundial descubrimos que en ese año la cifra de natalidad en varios países de la zona del conflicto era casi exactamente el doble de la registrada en 2024. Esta disminución de aproximadamente un 50% en la natalidad a lo largo de 26 años resultó ser un hallazgo clave para comprender el impacto prolongado del entorno socioeconómico y de violencia en la reproducción de la población.

Con ese rango territorial y temporal ya definido, dimos el salto a la base de datos de mortalidad infantil mundial de UNICEF para aplicar exactamente la misma selección de 12 países y el período de 1998 a 2024. Durante este paso descubrimos un factor fundamental sobre la relación entre ambos indicadores: existen países donde la natalidad no parece del todo "sana" en términos del umbral del 15%, pero su mortalidad resulta ser sumamente baja en proporción al tamaño de su población. Por ejemplo, en Estados Unidos se registra una cifra absoluta de muertes neonatales cercana a los 13 mil casos, lo cual a primera vista podría parecer elevado en comparación con países pequeños de la zona de conflicto, pero que responde en realidad a su enorme volumen de habitantes.

De esta manera, al seleccionar países con natalidades moderadas y mortalidades bajas en relación con su escala poblacional, la limpieza de datos se planteó para permitir en las siguientes etapas del proyecto la construcción de índices de mortalidad infantil que sean directamente comparables y complementables con la natalidad bruta por cada 1.000 habitantes, siguiendo la misma línea técnica que busca reflejar la UNICEF en sus estudios. Con este procedimiento, la curaduría de datos queda fundamentada de forma clara y proporciona la base necesaria para desarrollar la investigación a futuro.

Para la fase final de integración en el entorno de análisis en Python y Google Colab, las tablas resultantes se exportaron en formato CSV con codificación UTF-8 para garantizar la integridad de los caracteres y tildes. En el script de carga se aplicaron comandos de Pandas para eliminar las filas de metadatos sobrantes y las etiquetas automáticas generadas por Excel, consolidando una estructura estándar donde las filas representan a los 12 países de la muestra y las columnas contienen la serie temporal continua desde 1998 hasta 2024.

---

## Fuentes de Datos Utilizadas y Justificación Periodística

1. **Banco Mundial (World Bank Open Data) — Tasa Bruta de Natalidad:** Se eligió esta fuente oficial por ser la referencia internacional estandarizada para medir el volumen de nacimientos vivos por cada 1.000 habitantes. Sus datos permiten monitorear los cambios en la tendencia reproductiva a lo largo de un período de 27 años y evaluar cómo la población responde ante dinámicas de crisis.

2. **UNICEF (Child Mortality Estimates - UN IGME) — Mortalidad Neonatal:** Se seleccionó este repositorio institucional porque recopila los registros de fallecimientos en los primeros 28 días de vida con una metodología armonizada a nivel global. Aportó la masa de datos necesaria para contrastar el riesgo de supervivencia de los recién nacidos con el volumen de natalidad de cada país.

### Justificación de la Muestra (12 Países)
La muestra se estructuró dividiendo los 12 países en dos bloques de 6 integrantes cada uno para permitir una comparación analítica justa:
* **Bloque de Conflicto:** Palestina/Gaza, Siria, Líbano, Jordania, Israel e Irán. Permite analizar el comportamiento demográfico y la supervivencia infantil en territorios directamente marcados por la inestabilidad geopolítica y la fragilidad hospitalaria.
* **Bloque de Control y Equilibrio:** México y Arabia Saudita (que bordean el umbral equilibrado de natalidad cercano a los 15 puntos), junto a Estados Unidos, Francia, Noruega y Australia. Este grupo permite observar el estándar de mortalidad en economías estables y sirve como referencia para evaluar el sesgo por volumen poblacional en el análisis de indicadores.

---

## Preguntas de Investigación Analizables con la Base Limpia

A partir de la estructuración de la base de datos limpia mediante tablas dinámicas y análisis cruzados en Pandas, es posible dar respuesta a las siguientes tres interrogantes periodísticas:

1. **¿Cómo varió la Tasa Bruta de Natalidad en los países de la zona de conflicto en comparación con el bloque de control desde 1998 hasta 2024, y qué tan drástica fue la caída porcentual en Palestina/Gaza?**
   * *Abordaje:* A través de una tabla dinámica que promedie los valores de natalidad por grupo de países a lo largo del tiempo, contrastando la reducción cercana al 50% en la región afectada con la estabilidad del grupo de control.

2. **¿De qué manera el tamaño de la población distorsiona la percepción de la mortalidad neonatal absoluta al comparar países grandes como Estados Unidos con naciones de la zona de conflicto?**
   * *Abordaje:* Utilizando una visualización comparativa entre la cantidad absoluta de fallecimientos y el indicador proporcional de nacimientos vivos para demostrar la necesidad de normalizar las cifras antes de evaluar la fragilidad sanitaria.

3. **¿Existe una correlación directa entre los momentos de mayor caída en la natalidad y los incrementos en la mortalidad neonatal en los países en conflicto antes del escenario de 2024?**
   * *Abordaje:* Cruzando año a año ambas series de tiempo limpias para identificar picos de vulnerabilidad en los sistemas de salud de la región en el marco previo a la crisis actual.
