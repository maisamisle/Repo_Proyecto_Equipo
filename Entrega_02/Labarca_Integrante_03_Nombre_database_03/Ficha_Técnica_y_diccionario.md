# Ficha Técnica de la Base de Datos

## Fuente de los Datos
* **Repositorio oficial:** [Tech For Palestine](https://data.techforpalestine.org/docs/killed-in-gaza/)
* **Formato de importación:** Archivo delimitado por comas (`.csv`).

## Metodología de Construcción de la Base
Para la obtención de los datos, se accedió directamente al sitio de *Tech For Palestine* para descargar el documento consolidado de víctimas fatales. 

Por su parte, la organización recopiló de forma periódica las cifras emitidas por el **Ministerio de Salud de Gaza**, complementando y actualizando los registros a través de los reportes oficiales difundidos progresivamente en su canal de Telegram.

## Alcance de los Datos
La base de datos original recopila información de ingresos hospitalarios y decesos registrados a partir del 2 de noviembre de 2023 —coincidiendo con una de las etapas más intensas del conflicto— hasta el 31 de julio de 2025. Sin aplicar filtros, el archivo inicial cuenta con **72.835 registros**.

Posteriormente, las edades fueron delimitadas a dos grupos de interés prioritarios para el estudio:
1. **Bebés (Infantes):** Niños y niñas desde su nacimiento (0 años) hasta el día previo a cumplir los 2 años (1 año cumplido).
2. **Madres Potenciales:** Mujeres en edad fértil comprendidas entre los 15 y 49 años. Este rango se ajusta a las definiciones del portal de metadatos de la Organización Mundial de la Salud (OMS) y a estudios demográficos de fertilidad en el sector (referenciados en fuentes como [Statista](https://www.statista.com/statistics/1423019/gaza-fertility-rate/)).

Tras aplicar estos criterios, la base de datos se redujo a una muestra final de **13.070 personas**.

## Características de los Datos
* **Unidad de análisis:** Cada fila representa a una persona fallecida e identificada dentro del rango temporal señalado.
* **Variables incluidas:** Número de documento de identificación nacional (`id`), número de actualización del reporte (`update`), nombres en inglés y árabe (`en_name`, `ar_name`), fecha de nacimiento (`dob`), edad (`age`) y sexo (`sex`).
* **Dimensiones de la base limpia:** 13.070 filas y 8 columnas (incluyendo la variable de clasificación del grupo).
* **Calidad de la información:** El **100% de la muestra** corresponde a personas completamente identificadas. No existen celdas vacías o datos faltantes, lo cual garantiza la consistencia e integridad metodológica del análisis

## Otras Observaciones
Habría sido de gran utilidad disponer de una columna que detallara la fecha exacta de publicación de cada una de las actualizaciones (*updates*). Esto habría permitido realizar un análisis temporal más preciso de las distintas etapas del conflicto y correlacionar picos de bajas dentro de los grupos observados con eventos específicos en la línea de tiempo.



## Diccionario de Datos

| Columna | Nombre de Variable | Descripción | Tipo de Dato | Valores Posibles | Observaciones Editoriales |
| :---: | :--- | :--- | :--- | :--- | :--- |
| **A** | `id` | Número de documento de identidad de la persona fallecida. | Numérico (*int64*) | Números enteros de identificación. | Clave única de registro en la base de datos oficial. |
| **B** | `en_name` | Nombre completo de la persona expresado en alfabeto latino (inglés). | Texto (*string*) | Cadena de texto / nombres trasliterados. | Facilita la lectura y búsqueda nominal en entornos occidentales. |
| **C** | `ar_name` | Nombre completo de la persona expresado en alfabeto árabe. | Texto (*string*) | Cadena de texto en caracteres árabes. | Nombre original tal como figura en los registros oficiales de origen. |
| **D** | `age` | Edad cumplida al momento del deceso. | Numérico (*int64*) | `0` a `1` y `15` a `49` | Acotado durante la limpieza: `0`-`1` años (lactantes) y `15`-`49` años (mujeres en edad fértil). |
| **E** | `dob` | Fecha de nacimiento de la víctima. | Fecha (*YYYY-MM-DD*) | Fechas en formato de año, mes y día. | Permite validar el cálculo de la edad registrada. |
| **F** | `sex` | Género o sexo asignado de la persona registrada. | Categórico (*string*) | `"f"` (femenino)<br>`"m"` (masculino) | En el grupo de `15-49` años solo existen registros `"f"`. En `0-1` años se incluyen `"f"` y `"m"`. |
| **G** | `update` | Número de entrega/reporte del Ministerio de Salud en que se incorporó. | Numérico (*int64*) | Enteros del `1` al `10` | Corresponde a las 10 entregas de listas publicadas por la fuente oficial. |
| **H** | `GRUPO` | Calificación nominal y categórica creada durante la limpieza. | Categórico (*string*) | `"BEBE"`<br>`"MADRE POTENCIAL"` | Los registros clasificados como `"NO SIRVE"` (o no aplica) fueron eliminados durante el filtrado. |
