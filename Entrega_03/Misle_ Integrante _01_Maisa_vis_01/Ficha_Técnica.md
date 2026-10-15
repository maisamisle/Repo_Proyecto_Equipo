# Ficha Técnica de la Base de Datos

## 1. Información General

- **Nombre del archivo:** `dB_ataques_hospitales_con_macrocategorias.csv`
- **Temática:** Registro detallado de incidentes y ataques dirigidos a infraestructuras hospitalarias en la Franja de Gaza.
- **Dimensiones:** 795 registros (filas) y 8 variables (columnas).
- **Periodo registrado:** Del 07/10/2023 al 03/10/2025.
- **Cobertura geográfica:** 5 gobernaciones de la Franja de Gaza (*Gaza North*, *Gaza City*, *Deir al Balah*, *Khan Younis* y *Rafah*).
- **Alcance:** 42 centros hospitalarios registrados.

## 2. Distribución por Macrocategorías de Ataque

- **Direct Attacks / Armed Violence:** 343 eventos (43,1%)
- **Control Operations & Siege:** 230 eventos (28,9%)
- **Obstruction / Logistical Blockade:** 201 eventos (25,3%)
- **Not Specified:** 21 eventos (2,6%)

## 3. Observaciones sobre los Datos

- **Concentración espacial:** Existe una alta densidad de incidentes en la zona norte de la Franja. La combinación de las gobernaciones de Gaza North (296 eventos) y Gaza City (248 eventos) concentra más del 68% de los registros totales del dataset.
- **Incompletitud en datos operativos:** Las columnas `Closure` (cierre) y `Reopening` (reapertura) muestran un porcentaje muy elevado de valores nulos (~91% y ~94% respectivamente). Esto ocurre debido a que no todos los incidentes implicaron el cierre inmediato de la instalación o a que varios centros afectados no han logrado reabrir.
