# Documentación Técnica de las Bases de Datos Limpias

## 1. Ficha Técnica: Base de Datos de Natalidad

### Fuente de los datos
* **Institución:** Banco Mundial (*World Bank Open Data* / *World Development Indicators*).
* **Indicador oficial:** Tasa bruta de natalidad por cada 1.000 habitantes (`SP.DYN.CBRT.IN`).
* **Enlace de origen:** [World Bank Open Data](https://data.worldbank.org/).

### Metodología de la construcción de la base
1. **Extracción:** Descarga del dataset global de indicadores de desarrollo social y demográfico del Banco Mundial.
2. **Filtrado Geográfico:** Selección de un panel estratificado de 12 países en dos bloques comparativos:
   * *Bloque de Conflicto en Medio Oriente (6 países):* Irán, Israel, Jordania, Líbano, Palestina y Siria.
   * *Bloque de Contraste / Sostenibilidad (6 países):* Arabia Saudita, Australia, Estados Unidos, Francia, México y Noruega.
3. **Filtrado Temporal:** Reducción de la serie de tiempo continua para comprender el período 1998–2024 (27 años).
4. **Homogenización:** Apertura y limpieza de etiquetas regionales, eliminación de filas descriptivas sin datos y estandarización a codificación UTF-8.

### Alcance de los datos
* **Espacial:** Panel de 12 países seleccionados por criterios de representatividad bélica/geopolítica y estabilidad sociodemográfica.
* **Temporal:** Anual, desde 1998 hasta 2024.
* **Unidad de Análisis:** País-Año.

### Características de los datos
* **Estructura:** Matriz tabular de datos cuantitativos continuos.
* **Tipo de Variable Principal:** Tasa proporcional por mil ($‰$).
* **Frecuencia:** Registros consolidados con carácter anual.

### Otras observaciones
* La tasa bruta de natalidad refleja el número de nacimientos vivos por cada 1.000 habitantes a mitad de año.
* No ajusta por estructura de edades ni sexo de la población, por lo que debe ser interpretada como un indicador macrodemográfico general.

### Diccionario de Datos: Natalidad

| Nombre de la Variable | Descripción | Tipo de Dato | Valores Posibles | Observaciones Editoriales |
| :--- | :--- | :---: | :---: | :--- |
| `Country Name` | Nombre formal del país en español o inglés | Texto | Nombres de los 12 países seleccionados | Estandarizado según la nomenclatura de la fuente de origen. |
| `Country Code` | Código de identificación ISO 3166-1 alfa-3 del país | Texto | `AUS`, `FRA`, `IRN`, `ISR`, `JOR`, `LBN`, `MEX`, `NOR`, `PSE`, `SAU`, `SYR`, `USA` | Llave primaria estandarizada para cruces y uniones (*joins*). |
| `1998` – `2024` | Tasa bruta de natalidad para el año correspondiente | Numérico Continuo | Valores mayores a $0.0$ (rango típico: $8.0$ a $35.0$) | Expresado en nacimientos por cada 1.000 habitantes. Guardado con coma/punto decimal según estándar CSV. |

---

## 2. Ficha Técnica: Base de Datos de Mortalidad Neonatal

### Fuente de los datos
* **Institución:** Fondo de las Naciones Unidas para la Infancia (UNICEF) / *UN Inter-agency Group for Child Mortality Estimation* (UN IGME).
* **Indicador oficial:** Estimaciones de mortalidad neonatal (muertes de recién nacidos dentro de los primeros 28 días de vida).
* **Enlace de origen:** [UNICEF Data](https://data.unicef.org/).

### Metodología de la construcción de la base
1. **Extracción:** Filtrado del repositorio global de estimaciones de mortalidad infantil de UNICEF.
2. **Filtrado Geográfico:** Alineación exacta con la muestra de 12 países del estudio demográfico comparativo.
3. **Depuración de Variables:** Selección exclusiva del estimador central (excluyendo rangos de incertidumbre límite superior e inferior para simplificar el DataFrame de análisis).
4. **Filtrado Temporal y Formateo:** Extracción del período 1998–2024, depuración de totales acumulados o filas resumidas (*Total general*), y exportación a formato `.csv` codificado en `UTF-8`.

### Alcance de los datos
* **Espacial:** Los mismos 12 países seleccionados para la comparativa.
* **Temporal:** Cobertura de la serie histórica continua de 1998 a 2024.
* **Unidad de Análisis:** País-Año.

### Características de los datos
* **Estructura:** Matriz tabular de conteos o estimaciones absolutas de muertes.
* **Tipo de Variable Principal:** Frecuencia absoluta (conteo entero).

### Otras observaciones
* El dato reportado representa el **número total absoluto de muertes neonatales** ocurridas en el año.
* Debido a que no está ponderado por el tamaño total de la población del país, para análisis comparativos rigurosos se recomienda calcular la *Tasa de Mortalidad Neonatal por cada 1.000 nacidos vivos* combinándola con la base de natalidad o población.

### Diccionario de Datos: Mortalidad Neonatal

| Nombre de la Variable | Descripción | Tipo de Dato | Valores Posibles | Observaciones Editoriales |
| :--- | :--- | :---: | :---: | :--- |
| `Country Name` | Nombre del país analizado | Texto  | Nombres de los 12 países elegidos | Identificador del país. |
| `Country Code` | Código ISO 3166-1 alfa-3 | Texto | Lista de 12 códigos ISO de 3 letras | Clave única de emparejamiento inter-dataset. |
| `1998` – `2024` | Número absoluto estimado de muertes neonatales en dicho año | Numérico Entero | Enteros positivos ($\ge 0$) | Muertes registradas en los primeros 28 días de vida. |
