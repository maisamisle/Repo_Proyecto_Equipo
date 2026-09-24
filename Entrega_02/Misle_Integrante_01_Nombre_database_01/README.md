# Documentación: limpieza y análisis de la base de datos

## 1. Explicación del proceso de limpieza

La limpieza se realizó en Microsoft Excel a partir de la base original (`database_raw_01.csv`), compuesta por **34 columnas y 799 filas**. El objetivo fue analizar los ataques a la infraestructura hospitalaria de Gaza y mostrar cómo se afectaron las estructuras que permiten sobrevivir.

### Paso 1: Formato e importación

Se importó el archivo CSV, delimitado por punto y coma, a Excel para organizar la información en columnas independientes.

### Paso 2: Selección de columnas conservadas

De las 34 columnas iniciales, se conservaron **8** en la base limpia (`ataques_hospitales_database_limpia.csv`):

1. **Attack ID:** Identificador numérico único de cada incidente.
2. **Type of attack:** Descripción de la agresión (bombardeo, disparos, orden de evacuación, sitio, entre otras).
3. **Category:** Clasificación general del tipo de ataque.
4. **Hospital name:** Nombre del centro hospitalario afectado.
5. **Governorate:** Gobernación o zona territorial de Gaza.
6. **Date:** Fecha en que ocurrió el evento.
7. **Closure:** Fecha de cierre del hospital a causa del ataque.
8. **Reopening:** Fecha de reapertura del centro de salud.

### Paso 3: Eliminación de columnas superfluas

Se eliminaron las **26 columnas restantes**, por no formar parte del foco del reporte:

- **Source 1, Report number y Source 2:** Códigos internos e identificadores de agencias reportantes.
- **Month-year, Year-month, Month y Year:** Columnas redundantes contenidas en `Date`.
- **Killed staff FU/II, Killed patients FU/II y Killed individuals FU/II:** Seis columnas de fallecidos por agencia.
- **Detained staff FU/II, Detained patients FU/II y Detained individuals FU/II:** Seis columnas de detenidos por agencia.
- **Injured staff FU/II, Injured patients FU/II y Injured individuals FU/II:** Seis columnas de heridos por agencia.
- **Comments:** Columna con texto libre y notas cualitativas inconsistentes.

### Paso 4: Exportación

Se mantuvieron vacías las celdas de `Closure` y `Reopening` cuando no hubo cierre ni reapertura registrada. Finalmente, la base se exportó en formato CSV.

## 2. Fuentes de datos utilizadas

- **UN OCHA (informes *Flash Update*):** Fuente oficial que recopila información humanitaria y de infraestructura en zonas de conflicto, otorgando validación institucional a los registros.
- **Insecurity Insight (*Aid in Danger*):** Organización especializada en el monitoreo y verificación de incidentes de violencia contra instalaciones y personal médico.

## 3. Preguntas de investigación

### ¿Cuáles fueron los hospitales más atacados en la Franja de Gaza?

De los **799 ataques en 43 centros de salud**, los principales fueron:

1. **Kamal Adwan Hospital:** 113 ataques.
2. **Al Awda Hospital (Norte):** 94 ataques.
3. **Nasser Hospital:** 82 ataques.
4. **Al Shifa Medical Hospital:** 70 ataques.

### ¿Qué tipo de agresiones fueron las más recurrentes?

- **Violencia con armas pesadas, fuego o agentes químicos:** 289 incidentes.
- **Obstaculización de la atención médica:** 205 incidentes.
- **Órdenes de evacuación:** 119 incidentes.
- **Violencia contra personas:** 113 incidentes.
- **Sitio, ocupación o uso militar:** 62 incidentes.

### ¿Cómo se distribuyeron los ataques y cierres por gobernación?

- **Gaza Norte:** 296 ataques y 24 cierres.
- **Ciudad de Gaza:** 248 ataques y 30 cierres.
- **Khan Younis:** 190 ataques y 9 cierres.
- **Deir al Balah:** 43 ataques y 3 cierres.
- **Rafah:** 18 ataques y 5 cierres.
