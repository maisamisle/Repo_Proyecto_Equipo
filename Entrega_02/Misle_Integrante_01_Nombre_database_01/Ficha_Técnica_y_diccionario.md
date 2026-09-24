### 1. Fuente de los Datos

Los datos los sacamos juntando la información de dos fuentes que hacen seguimiento a lo que pasa con la salud en el conflicto:

- **OCHA Flash Updates:** Reportes e informes rápidos de la Oficina de Naciones Unidas para la Coordinación de Asuntos Humanitarios (*Flash Update*).
- **Insecurity Insight:** Una base de datos global que registra los ataques y la violencia contra hospitales y personal médico (*Insecurity Insight*).

### 2. Cómo armamos la base

- **Cruzar la información:** Registramos cada ataque anotando si venía de la primera fuente (*Source 1*) y si también lo confirmaba la segunda fuente (*Source 2*).
- **Ordenar el tipo de ataque:** Clasificamos los ataques según lo que pasó (`Type of attack`) y los agrupamos en categorías más generales (`Category`).
- **Separar los datos de las víctimas:** Para no confundir las cifras, pusimos por separado los datos de personas muertas, detenidas o heridas según lo que reportaba cada fuente (unas columnas para *Flash Update* y otras para *Insecurity Insight*).
- **Fechas y cierres:** A cada hecho le pusimos la fecha, el mes, el año, el hospital atacado, la zona de Gaza y las fechas de cuando tuvo que cerrar (`Closure`) o si pudo volver a abrir (`Reopening`).

### 3. Qué abarca la base

- **Dónde:** Toda la Franja de Gaza, dividida por zonas (*Gaza North*, *Gaza City*, *Khan Younis*, *Deir al Balah*, *Rafah* y algunos casos no especificados).
- **Centros de salud:** Cubre un total de **43 hospitales y centros médicos**.
- **Tiempo:** Abarca desde **octubre de 2023 hasta octubre de 2025** (incluyendo el seguimiento de cierres y reaperturas).
- **Total de registros:** Tiene anotados **799 ataques o incidentes en total**.

### 4. Cómo son los datos

- Es una tabla de Excel/CSV que tiene **799 filas** y **34 columnas**.
- Las partes principales (el nombre del hospital, la fecha, la zona y el tipo de ataque) están completas en todos los registros.
- En las partes de conteo de víctimas o heridos, cuando una fuente no tenía el dato exacto o no hubo afectados, en vez de un cero pusieron un guion `-`.
- Las fechas de cierre y reapertura solo aparecen en los casos donde el hospital tuvo que frenar sus operaciones o intentó abrir de nuevo más adelante.

### 5. Cosas importantes a tener en cuenta

- **No sumar directo:** Como las dos fuentes anotan sus propias cifras de víctimas por separado (columnas `FU` y columnas `II`), no hay que sumarlas a lo loco para no duplicar gente.
- **Hospitales atacados muchas veces:** Un mismo hospital aparece varias veces en la lista porque recibió ataques en diferentes días. Por ejemplo, los hospitales *Kamal Adwan* y *Al Awda* son de los que más ataques registran.

# Diccionario de Datos

| **Nombre de la columna** | **¿Qué significa?** | **Tipo de dato** | **Valores que puede tener / Ejemplos** | **Notas sencillas** |
|---|---|---|---|---|
| **Attack ID** | El número de identificación de cada ataque. | Número | `1`, `2`, `3`, ..., `799` | Es el número único para no confundir un ataque con otro. |
| **Source 1** | La primera fuente que reportó el ataque. | Texto | `Flash Update`, `Insecurity Insight` | De dónde salió la información principal. |
| **Report number** | El número de informe que le dio la fuente. | Texto / Número | `1`, `3`, `48`, `NA`, `No` | Dice `NA` si venía directo de *Insecurity Insight*. |
| **Source 2** | La segunda fuente que confirmó el ataque. | Texto | `No`, `Insecurity Insight` | Si dice `No`, es porque solo una fuente lo reportó. |
| **Type of attack** | Qué fue lo que pasó exactamente en el ataque. | Texto | Bombardeo aéreo (`Airstrike`), Disparos de artillería (`Shelling`), Orden de evacuación (`Order of evacuation`), Bloqueo/Sitio (`Siege`), Falta de combustible o insumos (`Lack of fuel/medical supply`), etc. | Describe la forma en que atacaron. |
| **Category** | El tipo de agresión agrupado en categorías más grandes. | Texto | Violencia con armas pesadas, Ataques a personas, Orden de evacuación, Sitio u ocupación del hospital, etc. | Sirve para agrupar los ataques por tipo. |
| **Hospital name** | Nombre del hospital afectado. | Texto | `Indonesian Hospital`, `Al Shifa Medical Hospital`, `Nasser Hospital`, `Kamal Adwan Hospital`, etc. | Hay 43 hospitales distintos en la lista. |
| **Governorate** | La zona o distrito de Gaza donde está el hospital. | Texto | `Gaza North` (Norte de Gaza), `Gaza City` (Ciudad de Gaza), `Khan Younis`, `Deir al Balah`, `Rafah`, `Unkown` | Sirve para saber en qué parte de Gaza fue. |
| **Date** | La fecha exacta del ataque. | Fecha | `07-10-2023`, `15-11-2023`, etc. | Escrito en formato día-mes-año. |
| **Month-year** | El mes y año en texto. | Texto | `oct-23`, `nov-23`, `ene-24`, etc. | Para hacer gráficos o tablas por mes. |
| **Year-month** | Año y mes en formato ordenado. | Texto | `2023-10`, `2023-11`, `2024-01`, etc. | Ayuda a ordenar los meses cronológicamente. |
| **Month** | El número del mes. | Número | Del `1` al `12` | El mes en número. |
| **Year** | El año. | Número | `2023`, `2024`, `2025` | El año en número. |
| **Killed staff FU** | Personal médico muerto según *Flash Update*. | Texto / Número | `-`, `1`, `2`, `3` | Si no hay dato o fue 0, sale un guion `-`. |
| **Killed staff II** | Personal médico muerto según *Insecurity Insight*. | Texto / Número | `-`, `1`, `2` | Si no hay dato o fue 0, sale un guion `-`. |
| **Killed patients FU** | Pacientes muertos según *Flash Update*. | Texto / Número | `-`, `1`, `2`, `40` | Si no hay dato o fue 0, sale un guion `-`. |
| **Killed patients II** | Pacientes muertos según *Insecurity Insight*. | Texto / Número | `-`, `1`, `2`, `7` | Si no hay dato o fue 0, sale un guion `-`. |
| **Killed individuals FU** | Civiles o personas no especificadas muertas según *Flash Update*. | Texto / Número | `-`, `1`, `3`, `7` | Si no hay dato o fue 0, sale un guion `-`. |
| **Killed individuals II** | Civiles o personas no especificadas muertas según *Insecurity Insight*. | Texto / Número | `-`, `1`, `2`, `5` | Si no hay dato o fue 0, sale un guion `-`. |
| **Detained staff FU** | Personal médico detenido según *Flash Update*. | Texto / Número | `-`, `1`, `2`, `5` | Si no hay dato o fue 0, sale un guion `-`. |
| **Detained staff II** | Personal médico detenido según *Insecurity Insight*. | Texto / Número | `-`, `1`, `3`, `10` | Si no hay dato o fue 0, sale un guion `-`. |
| **Detained patients FU** | Pacientes detenidos según *Flash Update*. | Texto / Número | `-`, `1`, `2` | Si no hay dato o fue 0, sale un guion `-`. |
| **Detained patients II** | Pacientes detenidos según *Insecurity Insight*. | Texto / Número | `-`, `1`, `3` | Si no hay dato o fue 0, sale un guion `-`. |
| **Detained individuals FU** | Civiles detenidos según *Flash Update*. | Texto / Número | `-`, `1`, `5` | Si no hay dato o fue 0, sale un guion `-`. |
| **Detained individuals II** | Civiles detenidos según *Insecurity Insight*. | Texto / Número | `-`, `1`, `10` | Si no hay dato o fue 0, sale un guion `-`. |
| **Injured staff FU** | Personal médico herido según *Flash Update*. | Texto / Número | `-`, `1`, `2` | Si no hay dato o fue 0, sale un guion `-`. |
| **Injured staff II** | Personal médico herido según *Insecurity Insight*. | Texto / Número | `-`, `1`, `3` | Si no hay dato o fue 0, sale un guion `-`. |
| **Injured patients FU** | Pacientes heridos según *Flash Update*. | Texto / Número | `-`, `1`, `2` | Si no hay dato o fue 0, sale un guion `-`. |
| **Injured patients II** | Pacientes heridos según *Insecurity Insight*. | Texto / Número | `-`, `1`, `4` | Si no hay dato o fue 0, sale un guion `-`. |
| **Injured individuals FU** | Civiles heridos según *Flash Update*. | Texto / Número | `-`, `1`, `5` | Si no hay dato o fue 0, sale un guion `-`. |
| **Injured individuals II** | Civiles heridos según *Insecurity Insight*. | Texto / Número | `-`, `1`, `2` | Si no hay dato o fue 0, sale un guion `-`. |
| **Closure** | Fecha en que el hospital tuvo que cerrar por el ataque. | Fecha / Vacío | `09-10-2023`, `13-11-2023`, en blanco | Solo aparece si el ataque provocó el cierre del lugar. |
| **Reopening** | Fecha en que el hospital pudo volver a funcionar. | Fecha / Vacío | `01-04-2025`, `23-04-2025`, en blanco | La mayoría está en blanco porque muchos no han vuelto a abrir. |
| **Comments** | Notas aclaratorias sobre el ataque. | Texto libre | Comentarios breves explicando detalles del hecho. | Aclaraciones adicionales sobre lo que pasó. |