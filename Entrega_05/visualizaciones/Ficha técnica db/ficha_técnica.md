# Documentación Técnica de las Bases de Datos Limpias

## 1. Ficha Técnica: Base de Datos de Natalidad

### Fuente de los datos
* **Institución:** Banco Mundial (*World Bank Open Data* / *World Development Indicators*).
* **Indicador oficial:** Tasa bruta de natalidad por cada 1.000 habitantes (`SP.DYN.CBRT.IN`).
* **Enlace de origen:** [World Bank Open Data](https://data.worldbank.org/).

### Metodología de la construcción de la base
1. **Extracción:** Descarga del dataset global de indicadores de desarrollo social y demográfico del Banco Mundial.
2. **Filtrado Geográfico:** Selección directa de los dos territorios bajo análisis comparativo: **Palestina (Franja de Gaza y Ribera Occidental) e Israel**.
3. **Filtrado Temporal:** Reducción de la serie de tiempo para comprender exclusivamente el período reciente **2023–2024** (2 años).
4. **Homogenización:** Limpieza de etiquetas regionales, eliminación de filas descriptivas sin datos y estandarización a codificación UTF-8.

### Alcance de los datos
* **Espacial:** Comparativa directa entre Palestina e Israel.
* **Temporal:** Anual, correspondiente a los años 2023 y 2024.
* **Unidad de Análisis:** Territorio-Año.

### Características de los datos
* **Estructura:** Matriz tabular de datos cuantitativos continuos.
* **Tipo de Variable Principal:** Tasa proporcional por mil (‰).
* **Frecuencia:** Registros consolidados con carácter anual.

### Otras observaciones
* La tasa bruta de natalidad refleja el número de nacimientos vivos por cada 1.000 habitantes a mitad de año.
* No ajusta por estructura de edades ni sexo de la población, por lo que funciona como un indicador demográfico general.

### Diccionario de Datos: Natalidad

| Nombre de la Variable | Descripción | Tipo de Dato | Valores Posibles | Observaciones Editoriales |
| :--- | :--- | :---: | :--- | :--- |
| `Country Name` | Nombre formal del territorio | Texto | `Palestina`, `Israel` | Estandarizado al español para coherencia editorial. |
| `Country Code` | Código de identificación ISO 3166-1 alfa-3 | Texto | `PSE`, `ISR` | Llave primaria estandarizada para cruces de datos. |
| `2023` – `2024` | Tasa bruta de natalidad para el año correspondiente | Numérico Continuo | Valores mayores a `0.0` (rango en la muestra: `18.6` a `27.1`) | Expresado en nacimientos por cada 1.000 habitantes. |

---

## 2. Ficha Técnica: Base de Datos de Mortalidad Neonatal

### Fuente de los datos
* **Institución:** Fondo de las Naciones Unidas para la Infancia (UNICEF) / *UN Inter-agency Group for Child Mortality Estimation* (UN IGME).
* **Indicador oficial:** Estimaciones de mortalidad neonatal (muertes de recién nacidos dentro de los primeros 28 días de vida).
* **Enlace de origen:** [UNICEF Data](https://data.unicef.org/).

### Metodología de la construcción de la base
1. **Extracción:** Filtrado del repositorio global de estimaciones de mortalidad infantil de UNICEF.
2. **Filtrado Geográfico:** Selección acotada a la comparativa directa entre **Gaza (territorio palestino) e Israel**.
3. **Depuración de Variables:** Selección exclusiva del estimador central (excluyendo rangos de incertidumbre límite superior e inferior para simplificar la tabla).
4. **Filtrado Temporal y Formateo:** Extracción exclusiva de los años **2023–2024**, depuración de filas resumidas (*Total general*) y exportación a formato `.csv` codificado en `UTF-8`.

### Alcance de los datos
* **Espacial:** Comparativa acotada entre Gaza e Israel.
* **Temporal:** Cobertura de los años 2023 y 2024.
* **Unidad de Análisis:** Territorio-Año.

### Características de los datos
* **Estructura:** Matriz tabular de conteos o estimaciones absolutas de muertes.
* **Tipo de Variable Principal:** Frecuencia absoluta (conteo entero).

### Otras observaciones
* El dato reportado representa el **número total absoluto de muertes neonatales** ocurridas en el año.
* Debido a que no está ponderado por el tamaño total de la población, debe interpretarse considerando la diferencia demográfica entre ambos territorios o cruzándolo con las tasas de natalidad.

### Diccionario de Datos: Mortalidad Neonatal

| Nombre de la Variable | Descripción | Tipo de Dato | Valores Posibles | Observaciones Editoriales |
| :--- | :--- | :---: | :--- | :--- |
| `Country Name` | Nombre del territorio analizado | Texto | `Gaza`, `Israel` | Identificador del territorio en la comparativa. |
| `Country Code` | Código ISO 3166-1 alfa-3 | Texto | `PSE`, `ISR` | Clave única de emparejamiento entre bases de datos. |
| `2023` – `2024` | Número absoluto estimado de muertes neonatales en dicho año | Numérico Entero | Enteros positivos (`≥ 0`) | Muertes registradas en los primeros 28 días de vida. |