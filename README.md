# Conteo de stock por estantería

App web para contar y controlar el stock de una farmacia (medicamentos y descartables) en el mismo orden en que están ubicados en los estantes. Funciona en el navegador, sin instalar nada.

**Abrir la app:** https://rutas-la.github.io/conteo-stock/

## Qué hace

- Lee el **Listado de Stock** exportado a Excel desde SIGEHOS (módulo "Medicación e insumos", con *Agrupado*, *Activos* y *Con Stock* tildados). Toma el stock de la columna **Cant Fraccionado** y el código de la columna **CODIGO**.
- Clasifica cada artículo en pestañas: **Medicamentos**, **Remediar**, **Controlados** (estupefacientes, psicotrópicos y control interno), **Programa TBC**, **Programa VIH**, **Descartables** y **Enfermería (traslado)**.
- Dentro de cada grupo separa los medicamentos por forma farmacéutica (comprimidos y cápsulas, líquidos orales, inyectables, inhalatorios, gotas, tópicos, óvulos y supositorios) y los ordena alfabéticamente por principio activo.
- Permite acomodar el orden para que coincida con el estante y corregir grupo o forma de cualquier artículo.
- Conteo con diferencia contra el sistema (coincide / faltante / sobrante), conteo ciego opcional y avance por grupo y por forma.
- 🔒 marca un medicamento para control (por ejemplo, tramadol). 🏥 lo manda a la pestaña de traslado a enfermería.
- Exporta a Excel: planilla en blanco para contar en papel, resultado del conteo con diferencias y planilla de traslado a enfermería con códigos.

## Dónde se guardan los datos

Todo queda en el navegador de la computadora donde se usa: el listado cargado, lo contado y las correcciones de clasificación. No se envía nada a ningún servidor.

- `clasificacion.json` tiene la clasificación base (controlados, traslados a enfermería y correcciones). Se carga la primera vez que se abre la app en una computadora.
- Para pasar las correcciones de una computadora a otra, o actualizar la clasificación base, usá **Exportar clasificación** / **Importar clasificación**, al final de la página. Para actualizar la base del repositorio, reemplazá `clasificacion.json` por el archivo exportado.

## Archivos

- `index.html`: la app completa (HTML, CSS y JavaScript en un solo archivo; usa SheetJS desde cdnjs para leer y escribir Excel).
- `clasificacion.json`: clasificación base.
