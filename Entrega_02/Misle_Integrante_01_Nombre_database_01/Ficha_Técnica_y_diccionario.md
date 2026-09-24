### 1. Fuente de los Datos

Los datos fueron recopilados a partir de la información reportada por dos fuentes especializadas en el monitoreo del conflicto y el sector salud:

- **OCHA Flash Updates:** Reportes e informes rápidos publicados por la Oficina de Naciones Unidas para la Coordinación de Asuntos Humanitarios (*Flash Update*).
- **Insecurity Insight:** Base de datos global que registra ataques y hechos de violencia contra instalaciones sanitarias y personal médico (*Insecurity Insight*).

### 2. Metodología de la construcción de la base

- **Cruce y verificación de fuentes:** Quienes construyeron la base registraron cada ataque verificando si provenía de la primera fuente (*Source 1*) y si además contaba con la confirmación de una segunda fuente (*Source 2*).
- **Clasificación de los hechos:** Los ataques se ordenaron según la acción específica ocurrida (`Type of attack`) y luego se agruparon en categorías más amplias (`Category`).
- **Desagregación del impacto:** Para evitar duplicaciones o confusiones, los registros de personas fallecidas, detenidas o heridas se mantuvieron separados según lo reportado por cada entidad (se asignaron columnas independientes para *Flash Update* y para *Insecurity Insight*).
- **Seguimiento temporal y de funcionamiento:** A cada incidente se le asignó su fecha exacta, mes, año, el hospital afectado, la gobernación correspondiente dentro de Gaza y, cuando estuvo disponible, las fechas de cierre (`Closure`) y reapertura (`Reopening`) del establecimiento.

### 3. Alcance de los datos

- **Cobertura geográfica:** La Franja de Gaza, abarcando las zonas de *Gaza North*, *Gaza City*, *Khan Younis*, *Deir al Balah*, *Rafah* (además de algunos registros categorizados como *Unknown*).
- **Centros de salud:** Incluye registros vinculados a **43 hospitales y centros de atención médica**.
- **Periodo temporal:** Registros que van desde **octubre de 2023 hasta octubre de 2025** (incluyendo el seguimiento de cierres y proyecciones de reaperturas).
- **Total de registros:** La base consolida un total de **799 incidentes o ataques documentados**.

### 4. Características de los datos

- Es un archivo estructurado en formato CSV con **799 filas** (registros) y **34 columnas** (variables).
- Las variables descriptivas clave (nombre del hospital, ubicación, fecha y clasificación del ataque) presentan un 100% de completitud.
- En los conteos numéricos sobre víctimas o heridos, cuando la fuente no reportó datos o no hubo personas afectadas, se utilizó un guion `-` como valor de relleno.
- Las columnas de cierre y reapertura solo contienen datos en aquellos eventos donde se documentó la suspensión o el reinicio de actividades del centro de salud.

### 5. Otras observaciones sobre la base

- **Manejo de fuentes independientes:** Dado que cada fuente mantiene sus propios conteos de víctimas en columnas separadas (identificadas como `FU` para *Flash Update* e `II` para *Insecurity Insight*), se debe evitar la suma directa entre ellas para no duplicar eventos o personas.
- **Frecuencia de agresiones por centro:** Varios hospitales cuentan con múltiples registros en la base, lo que refleja reiterados ataques a una misma instalación a lo largo del periodo analizado (destacando casos como los hospitales *Kamal Adwan* y *Al Awda*).

# Diccionario de Datos

| **Nombre de la columna** | **¿Qué significa?** | **Tipo de dato** | **Valores que puede tener / Ejemplos** | **Notas sencillas** |
|---|---|---|---|---|
| **Attack ID** | Identificador único de cada ataque registrado. | Número | `1`, `2`, `3`, ..., `799` | Corresponde al número asignado para diferenciar cada hecho. |
| **Source 1** | Primera fuente que reportó el incidente. | Texto | `Flash Update`, `Insecurity Insight` | Indica el origen del primer reporte. |
| **Report number** | Número o código de informe asignado por la fuente. | Texto / Número | `1`, `3`, `48`, `NA`, `No` | Indica `NA` cuando el reporte proviene directo de *Insecurity Insight*. |
| **Source 2** | Segunda fuente que verificó o confirmó el ataque. | Texto | `No`, `Insecurity Insight` | Si indica `No`, significa que el reporte proviene de una sola fuente. |
| **Type of attack** | Descripción de la acción u operación ocurrida. | Texto | Bombardeo aéreo (`Airstrike`), Disparos de artillería (`Shelling`), Orden de evacuación (`Order of evacuation`), Sitio/Bloqueo (`Siege`), Falta de combustible o insumos (`Lack of fuel/medical supply`), etc. | Describe la forma específica de la agresión. |
| **Category** | Agrupación general del tipo de violencia ejercida. | Texto | Violencia con armas pesadas, Obstaculización de atención médica, Orden de evacuación, Sitio u ocupación de la instalación, etc. | Categorización utilizada para agrupar los ataques. |
| **Hospital name** | Nombre del hospital o centro de salud afectado. | Texto | `Indonesian Hospital`, `Al Shifa Medical Hospital`, `Nasser Hospital`, `Kamal Adwan Hospital`, etc. | Registra 43 instalaciones de salud distintas. |
| **Governorate** | Gobernación o distrito de Gaza donde se ubica el centro. | Texto | `Gaza North` (Norte de Gaza), `Gaza City` (Ciudad de Gaza), `Khan Younis`, `Deir al Balah`, `Rafah`, `Unkown` | Corresponde a la ubicación territorial del hospital. |
| **Date** | Fecha exacta del hecho. | Fecha | `07-10-2023`, `15-11-2023`, etc. | Registrada en formato día-mes-año. |
| **Month-year** | Identificador de mes y año en texto. | Texto | `oct-23`, `nov-23`, `ene-24`, etc. | Facilita la agrupación de ataques por mes. |
| **Year-month** | Identificador de año y mes ordenable. | Texto | `2023-10`, `2023-11`, `2024-01`, etc. | Permite ordenar la información de manera cronológica. |
| **Month** | Número del mes en que ocurrió el hecho. | Número | Del `1` al `12` | Corresponde al mes numérico. |
| **Year** | Año en que ocurrió el hecho. | Número | `2023`, `2024`, `2025` | Corresponde al año numérico. |
| **Killed staff FU** | Personal médico fallecido según *Flash Update*. | Texto / Número | `-`, `1`, `2`, `3` | Muestra un guion `-` si no hubo reporte o si la cifra fue cero. |
| **Killed staff II** | Personal médico fallecido según *Insecurity Insight*. | Texto / Número | `-`, `1`, `2` | Muestra un guion `-` si no hubo reporte o si la cifra fue cero. |
| **Killed patients FU** | Pacientes fallecidos según *Flash Update*. | Texto / Número | `-`, `1`, `2`, `40` | Muestra un guion `-` si no hubo reporte o si la cifra fue cero. |
| **Killed patients II** | Pacientes fallecidos según *Insecurity Insight*. | Texto / Número | `-`, `1`, `2`, `7` | Muestra un guion `-` si no hubo reporte o si la cifra fue cero. |
| **Killed individuals FU** | Personas o civiles no especificados fallecidos según *Flash Update*. | Texto / Número | `-`, `1`, `3`, `7` | Muestra un guion `-` si no hubo reporte o si la cifra fue cero. |
| **Killed individuals II** | Personas o civiles no especificados fallecidos según *Insecurity Insight*. | Texto / Número | `-`, `1`, `2`, `5` | Muestra un guion `-` si no hubo reporte o si la cifra fue cero. |
| **Detained staff FU** | Personal médico detenido según *Flash Update*. | Texto / Número | `-`, `1`, `2`, `5` | Muestra un guion `-` si no hubo reporte o si la cifra fue cero. |
| **Detained staff II** | Personal médico detenido según *Insecurity Insight*. | Texto / Número | `-`, `1`, `3`, `10` | Muestra un guion `-` si no hubo reporte o si la cifra fue cero. |
| **Detained patients FU** | Pacientes detenidos según *Flash Update*. | Texto / Número | `-`, `1`, `2` | Muestra un guion `-` si no hubo reporte o si la cifra fue cero. |
| **Detained patients II** | Pacientes detenidos según *Insecurity Insight*. | Texto / Número | `-`, `1`, `3` | Muestra un guion `-` si no hubo reporte o si la cifra fue cero. |
| **Detained individuals FU** | Personas o civiles detenidos según *Flash Update*. | Texto / Número | `-`, `1`, `5` | Muestra un guion `-` si no hubo reporte o si la cifra fue cero. |
| **Detained individuals II** | Personas o civiles detenidos según *Insecurity Insight*. | Texto / Número | `-`, `1`, `10` | Muestra un guion `-` si no hubo reporte o si la cifra fue cero. |
| **Injured staff FU** | Personal médico herido según *Flash Update*. | Texto / Número | `-`, `1`, `2` | Muestra un guion `-` si no hubo reporte o si la cifra fue cero. |
| **Injured staff II** | Personal médico herido según *Insecurity Insight*. | Texto / Número | `-`, `1`, `3` | Muestra un guion `-` si no hubo reporte o si la cifra fue cero. |
| **Injured patients FU** | Pacientes heridos según *Flash Update*. | Texto / Número | `-`, `1`, `2` | Muestra un guion `-` si no hubo reporte o si la cifra fue cero. |
| **Injured patients II** | Pacientes heridos según *Insecurity Insight*. | Texto / Número | `-`, `1`, `4` | Muestra un guion `-` si no hubo reporte o si la cifra fue cero. |
| **Injured individuals FU** | Personas o civiles heridos según *Flash Update*. | Texto / Número | `-`, `1`, `5` | Muestra un guion `-` si no hubo reporte o si la cifra fue cero. |
| **Injured individuals II** | Personas o civiles heridos según *Insecurity Insight*. | Texto / Número | `-`, `1`, `2` | Muestra un guion `-` si no hubo reporte o si la cifra fue cero. |
| **Closure** | Fecha en que la instalación cerró a raíz del ataque. | Fecha / Vacío | `09-10-2023`, `13-11-2023`, en blanco | Se registra únicamente en los casos en que el ataque provocó el cierre del centro. |
| **Reopening** | Fecha en que el centro de salud pudo reanudar atenciones. | Fecha / Vacío | `01-04-2025`, `23-04-2025`, en blanco | La mayoría de las celdas están vacías debido a que muchos hospitales continuaron inoperativos. |
| **Comments** | Notas o texto explicativo sobre el incidente. | Texto libre | Comentarios breves agregados por la fuente sobre el ataque. | Aporta contexto cualitativo adicional sobre lo sucedido. |