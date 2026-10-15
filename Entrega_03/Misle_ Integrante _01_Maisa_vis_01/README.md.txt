
# Visualización y decisiones tomadas

Para hacer los gráficos de este trabajo, el objetivo principal fue mostrar cómo se fue destruyendo la red de hospitales en Gaza y cómo esto afectó las posibilidades de las mujeres embarazadas de recibir atención médica y las condiciones de supervivencia de los recién nacidos.

## Proceso de visualización

Al principio, nos enfocamos principalmente en los datos sobre nacimientos y muertes. Sin embargo, al revisar los datos sobre los ataques a los centros de salud, nos dimos cuenta de que también era importante mostrar cómo se fue afectando el sistema médico que permite atender a las mujeres embarazadas y a los recién nacidos.

### Simplificación de los tipos de ataques

La columna original `Type of attack` tenía 31 tipos de ataques diferentes, desde bombardeos y disparos hasta problemas relacionados con la falta de combustible. Mostrar todas estas categorías en un solo gráfico podía hacerlo difícil de entender, por lo que decidí agruparlas en tres categorías principales:

- **Direct Attacks / Armed Violence:** incluye ataques directos con armas, como bombardeos, disparos de francotiradores y ataques de artillería.
- **Obstruction / Logistical Blockade:** incluye problemas de acceso y suministro, como la falta de combustible y medicamentos, además de las restricciones para el ingreso de personal médico.
- **Control Operations & Siege:** incluye acciones de control y bloqueo, como asedios, incursiones militares en hospitales, órdenes de evacuación y arrestos.

Esta agrupación permitió reducir la cantidad de categorías y facilitar la comparación entre los distintos tipos de ataques.

### Herramienta utilizada

Para crear la visualización, utilicé Python y la librería Altair. Organicé los datos en un gráfico de barras interactivo, dividido en tres columnas correspondientes a los años 2023, 2024 y 2025. De esta manera, es posible comparar cómo fueron cambiando los tipos de ataques durante el periodo estudiado.

También agregué un menú desplegable para seleccionar la gobernación (`Governorate`). Esto permite observar los datos de una zona específica, como Gaza North o Khan Younis, sin tener que revisar todas las observaciones al mismo tiempo.


Durante el desarrollo del proyecto, realicé varios cambios en la base de datos y en el enfoque de la visualización.

### Eliminación de registros sin hospital identificado

Volví a revisar la base de datos que había limpiado anteriormente y eliminé los registros en los que el nombre del hospital aparecía como `Not specified`. Esta decisión se tomó porque, en un principio, quería realizar un mapa interactivo y necesitaba identificar la ubicación de los hospitales afectados.

### Limpieza de la columna de conteo

También eliminé la columna que numeraba los registros, ya que, después de borrar algunas filas, la numeración había quedado desactualizada. Como esta columna no aportaba información relevante para la visualización, decidí quitarla.

### Obtención de coordenadas geográficas

Inicialmente, utilicé ChatGPT para ayudarme a identificar las ubicaciones de los hospitales atacados en Gaza y obtener sus coordenadas geográficas, con la idea de incorporarlas a la base de datos para construir un mapa interactivo.

Sin embargo, las coordenadas debían verificarse con fuentes geográficas confiables, ya que era necesario asegurar que correspondieran a los hospitales correctos.

### Cruce de datos en Pandas

Después, utilicé la función `merge` de Pandas para unir la base de datos de los ataques con la base de datos que contenía las coordenadas de los hospitales. Para realizar este cruce, utilicé la columna `Hospital name` como identificador común.

El código utilizado fue el siguiente:

```python
import pandas as pd

df_hospitales = pd.read_csv(
    '/content/hospitales_coordenadas.csv',
    sep=';'
)

df_ataques = pd.read_csv(
    '/content/registro_ataques.csv',
    sep=';'
)

df_resultado = pd.merge(
    df_ataques,
    df_hospitales[['Hospital name', 'Latitud', 'Longitud']],
    on='Hospital name',
    how='left'
)

df_resultado.to_csv(
    'registro_ataques_con_coordenadas.csv',
    index=False
)
```

Con este procedimiento, incorporé las columnas de latitud y longitud a los registros de ataques, manteniendo todos los registros de la base de datos original gracias al uso de `how='left'`.

### Cambio de enfoque gráfico

Finalmente, decidí cambiar la visualización, ya que el mapa no funcionó como esperaba. En lugar de mostrar los ataques mediante su ubicación geográfica, opté por un gráfico de barras interactivo que permite seleccionar una gobernación y observar la cantidad y los tipos de ataques registrados entre 2023 y 2025.

Las zonas consideradas fueron Deir al Balah, Gaza City, Gaza North, Khan Younis y Rafah.

Este cambio permitió centrar el análisis en la evolución de los ataques a lo largo del tiempo y en las diferencias entre las zonas afectadas.

Además, mantuve una categoría adicional para los registros cuyo tipo de ataque no estaba especificado: `Not specified`.



## Base de datos utilizada y proceso de limpieza

La base de datos inicial utilizada fue `ataques_hospitales_database_limpia.csv`.

Durante el proceso de trabajo, se generaron distintas versiones del archivo según los cambios realizados:

1. **`ataques_hospitales_database_limpia.csv`:** base de datos inicial con los registros de ataques a hospitales.
2. **`registro_ataques_con_coordenadas.csv`:** versión que incorporaba las coordenadas geográficas de los hospitales para intentar realizar el mapa interactivo.
3. **`dB_ataques_hospitales_con_macrocategorias.csv`:** versión final, en la que se dejó de lado el enfoque geográfico y se agregó la columna `Macro attack category` para agrupar los tipos de ataques.

### ¿Por qué escogí esta base de datos?

Escogí esta base de datos porque contiene información relevante para analizar los ataques a la infraestructura hospitalaria de Gaza durante el periodo estudiado. Entre sus variables se encuentran las fechas de los ataques, las zonas afectadas, los hospitales involucrados y los tipos de ataques registrados.

Esta información permite comparar los ataques entre distintas zonas y años, además de observar cómo fueron cambiando sus características durante el periodo analizado.

## ¿Qué preguntas ayuda a responder el gráfico?

### ¿Cómo cambiaron los tipos de ataques con el tiempo?

El gráfico permite comparar los tipos de ataques registrados en 2023, 2024 y 2025. De esta manera, se puede observar si existen cambios en la frecuencia de los ataques armados directos, las restricciones de acceso y suministro o las operaciones de control y asedio.

### ¿Qué zonas sufrieron más ataques?

La posibilidad de seleccionar una gobernación permite comparar las zonas afectadas y observar qué tipos de ataques se registraron con mayor frecuencia en cada una. Esto ayuda a identificar diferencias entre lugares como Gaza City, Gaza North, Khan Younis, Rafah y Deir al Balah.

### ¿Qué relación existe entre los ataques a hospitales y las condiciones para dar a luz?

La visualización permite analizar el contexto de los ataques a la infraestructura hospitalaria y las posibles consecuencias para el acceso a la atención médica de las mujeres embarazadas y los recién nacidos.

Sin embargo, el gráfico por sí solo no permite demostrar una relación causal entre los ataques y los riesgos asociados al nacimiento. Para profundizar en esta pregunta, es necesario complementar los datos con información sobre la disponibilidad de servicios de maternidad, el funcionamiento de los hospitales y las condiciones en que las mujeres dieron a luz durante el periodo estudiado.

En conjunto, esta visualización busca facilitar la comprensión de cómo evolucionaron los ataques a los hospitales en Gaza entre 2023 y 2025, aportando información para analizar el deterioro de la infraestructura sanitaria y sus posibles consecuencias para las mujeres embarazadas y los recién nacidos.
