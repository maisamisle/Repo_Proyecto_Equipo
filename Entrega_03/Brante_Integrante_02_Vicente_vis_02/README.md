# Documentación 

## 1. Explicación del proceso 
- **Elección del indicador:** Se trabajó con la **Tasa Bruta de Natalidad** (nacimientos por cada 1.000 habitantes) entre 1998 y 2024[cite: 7]. Se descartó usar cifras de población total o números absolutos de muertes para comparar países de distinto tamaño sin distorsionar la información.
- **Tipo de gráfico:** Se usó un gráfico de líneas por ser el formato adecuado para mostrar evolución y cambios a lo largo del tiempo[cite: 7].
- **Diseño y contraste visual:** En Altair se destacó la curva de Palestina con una línea más gruesa (`3.5px`) y en color azul[cite: 7]. Las demás líneas (países vecinos de Medio Oriente y referentes mundiales) se dejaron más delgadas (`1.5px`) para servir como punto de comparación sin desordenar la gráfica[cite: 7].
- **Funcionalidad y formatos:** Se agregó interacción en la leyenda para poder hacer clic y aislar cualquier país. La imagen se exportó en `JPG` (`vis_01`) para la entrega[cite: 7].

## 2. Selección y proceso de la base de datos (CSV)
- **Origen de los datos:** Se usó la base de datos oficial de natalidad del Banco Mundial y UNICEF por tener registros continuos entre 1998 y 2024[cite: 7].
- **Limpieza en Python:**
  - **Limpieza inicial:** Se borraron filas con datos faltantes y se corrigieron nombres de países.
  - **Arreglo de columnas:** Se removió el guión `-` de los nombres de los años (por ejemplo, `-1998` pasó a ser `1998`).
  - **Reorganización de la tabla:** Se transformó la tabla a formato largo con la función `melt()` de Pandas para dejarla ordenada en tres columnas: `Pais`, `Año` y `Tasa_Natalidad`.
  - **Formato numérico:** Se cambiaron las comas por puntos en los decimales para que el sistema los reconociera como números.
  - **Nombres en español:** Se tradujeron los nombres de los países para mantener coherencia en el texto.

## 3. Preguntas que se buscan responder con la visualización
- ¿Cómo varió la tasa de natalidad en Palestina en los últimos 25 años comparada con países de su misma región?[cite: 7]
- ¿Hubo una caída más rápida de nacimientos en Palestina durante los años recientes (2022–2024)?[cite: 7]
- ¿Cómo se compara la situación de Palestina frente a países estables como Francia, Noruega o Estados Unidos?[cite: 7]
