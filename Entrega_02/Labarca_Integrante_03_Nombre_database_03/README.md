# Metodología y Selección de Datos

En primer lugar, se encontró una base de datos que contaba con un sistema de calificaciones basado en actualizaciones periódicas emitidas por entidades estatales en Gaza. Los registros se encontraban ordenados en función de la recepción de dichas actualizaciones.

Para contar una historia centrada en las **infancias perdidas** y en aquellas que, incluso antes de su nacimiento, ya se ven condicionadas por el conflicto en Oriente Medio, fue necesario llevar la información a un formato de hoja de cálculo en Excel para reorganizar y reagrupar los datos.

Una vez dispuesta la plantilla en un documento editable, se ordenaron los registros en función de la edad de las víctimas fatales. Debido a que la base de datos superaba las **72.000 filas**, resultaba indispensable reducirla para enfocar el análisis en los sujetos de interés:

1. **Definición de Infancia (Lactantes / Neonatos):** Dado que el término *infancia* es amplio, se delimitó estrictamente al ajuste del proyecto, enfocado en neonatos. Para esta clasificación, se restringió la base a niños y niñas de **0 a 1 año de edad**, optimizando el uso de los datos de la columna `D` (`age`).
2. **Definición de Edad Reproductiva:** Se consultaron investigaciones que estiman la franja etaria en la que las mujeres en Gaza suelen tener hijos. La búsqueda condujo a un estudio publicado en [Statista](https://www.statista.com/statistics/1423019/gaza-fertility-rate/), el cual sitúa la edad reproductiva entre los **15 y los 49 años**. A excepción de casos particulares, se determinó que las mujeres dentro de dicho rango corresponden a **"madres potenciales"**, al formar parte de la población demográficamente fértil en ese territorio.
3. **Depuración de Registros:** A todo el resto de la población expresada en la base de datos se le asignó la etiqueta **"NO SIRVE"**, por no ser datos de utilidad directa para el estudio.

### Fórmula de Clasificación

Para acelerar la clasificación en las 72.000 filas, se empleó la siguiente regla en Excel:

SI(D2<=1; "BEBE"; SI(Y(D2>=15; D2<=49; F2="f"); "MADRE POTENCIAL"; "NO SIRVE"

## Lista de las fuentes de datos utilizadas y una explicación de por qué las eligieron.

Para encontrar la base de datos, usé a la organización Tech For Palestina, puesto que presentó una base de datos nutrida mediante diversas oleadas de información. Esto se complementa con la disponibilidad de versiones anteriores con accesibilidad de la propia web que da cuenta de que hubo un trabajo de seguimiento de parte de la organización.

La selección de Statista para la limpieza de datos responde a que los datos presentados también coinciden con información provista por la OMS, que también se respalda en sitios como [AtlasInstitute.com](https://atlasinstitute.org/wombs-under-siege-reproductive-health-as-the-missing-indicator-in-gaza-policy-debates/)

## Preguntas que puede contestar la base de datos limpia:

* ¿Qué proporción de fallecidos en Gaza corresponden a niños recién nacidos o potenciales agentes de reproducción?
* ¿Cómo se distribuye la mortalidad en la infancia entre niños y niñas de 0 y 1 año? ¿Existe una disparidad de género en este grupo etario?
* ¿De qué manera ha evolucionado la incorporación de registros de neonatos y mujeres en edad fértil a lo largo de las distintas entregas e informes del Ministerio de Salud?
