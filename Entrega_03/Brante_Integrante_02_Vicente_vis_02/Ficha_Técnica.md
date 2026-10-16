# Ficha Técnica 

## Información general
- **Nombre del archivo:** `01-base-de-datos-natalidad-limpia`
- **Fuente de los datos:** Banco Mundial / UNICEF (Estimaciones oficiales de natalidad)[cite: 7].
- **Países incluidos:** Palestina (Gaza y Ribera Occidental), países vecinos de Medio Oriente y países de referencia internacional[cite: 7].
- **Años registrados:** 1998 a 2024[cite: 7].
- **Formato del archivo:** CSV (separado por comas, texto UTF-8).

---

## Variables de la base de datos

| Variable | Tipo de dato | Descripción |
| :--- | :--- | :--- |
| `Pais` | Texto / Nombre | Nombre del país o territorio en español. |
| `Año` | Número / Tiempo | Año del registro (1998 al 2024). |
| `Tasa_Natalidad` | Número decimal | Nacimientos registrados por cada 1.000 habitantes. |

---

## Observaciones
1. **Unificación territorial:** Los datos de Palestina junta la información oficial para la Franja de Gaza y la Ribera Occidental[cite: 7].
2. **Uso de tasas por habitantes:** Se usaron nacimientos por cada 1.000 habitantes y no números totales, para poder comparar países grandes y pequeños de forma justa[cite: 7].
