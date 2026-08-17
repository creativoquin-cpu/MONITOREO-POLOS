# Cambios realizados — Catálogo KLIXMANT

**Archivo:** `Catalogo_KLIXMANT_referencias_stock_2026_2.html`
**Fecha:** 15 de agosto de 2026

Resumen de todo lo que se ajustó en esta sesión, en orden.

---

## 1. Filtro por cantidad de unidades (regla obligatoria)

**Antes:** el rango "Stock entre X y Y" solo funcionaba si había una talla seleccionada. Con la talla en "Todas" el rango se ignoraba por completo y mostraba un mensaje "elige una talla para filtrar por rango".

**Ahora:**
- La etiqueta cambió de *"Stock entre… uds"* a **"Cantidad para filtrar: entre… uds"**.
- Si **no** hay talla seleccionada (Todas), el rango filtra por el **total de unidades** de cada prenda.
- Si hay una talla seleccionada (S, M, L…), el rango filtra por el **stock de esa talla**.
- Se quitó el mensaje bloqueante; siempre se muestra el conteo de productos resultantes.
- La regla aplica a todos los botones que usan el rango: **✓ Aplicar**, **▲ Más stock**, **▼ Menos stock** y **Seleccionar todo**.

## 2. Selección de talla vuelve a aplicar el filtro

**Antes:** al hacer clic en una talla el filtro no se reejecutaba; quedaba mostrando el resultado anterior.

**Ahora:** al elegir una talla, **si hay una cantidad puesta en el rango**, se reaplica la regla al instante (solo quedan las prendas cuyo stock de esa talla esté dentro del rango, y se seleccionan automáticamente). Si el rango está en los valores por defecto (1–999), elegir talla no fuerza selección.

## 3. Collage — botón "Editar orden"

Se agregó la opción de **reordenar los polos** dentro del collage:
- Botón **✎ Editar orden** en la ventana del collage.
- El orden define cómo se agrupan los polos (**4 por imagen**) y en qué orden se descargan.
- Afecta tanto a **"Descargar todas"** como a cada botón **"Descargar imagen N"**.

## 4. Ventana del collage más compacta y en 3 columnas

**Antes:** la ventana ocupaba casi toda la pantalla y las vistas previas se apilaban en una sola columna muy larga.

**Ahora:**
- Los collages se muestran en una **cuadrícula de hasta 3 columnas** (se adapta a menos en pantallas angostas).
- Ancho de ventana acotado (máx. 900 px) para que no invada toda la pantalla.
- **Importante:** solo cambia la vista previa en pantalla; los PNG se descargan en **alta resolución** sin pérdida de calidad.

## 5. Edición arrastrando las imágenes (sin panel superior)

**Antes:** la edición se hacía en un panel superior con miniaturas pequeñas y flechas ▲▼.

**Ahora:**
- Se **eliminó** ese panel superior.
- En modo edición, cada polo aparece como su **imagen real** (en 3 columnas) con su número de posición y nombre.
- Se **arrastra una imagen sobre otra** para reordenar; el borde se resalta en amarillo donde se va a soltar.
- El botón cambia a **✓ Ver collage** para volver a ver los collages armados con el nuevo orden.

## 6. Modo día / noche (que no se vea nocturno)

- Se agregó un botón **🌙 Noche / ☀️ Día** en la esquina superior derecha del encabezado.
- El catálogo abre por **defecto en modo día (claro)**.
- Se puede alternar en cualquier momento; la preferencia se recuerda en el navegador (cuando el navegador lo permite).
- De paso se corrigió un detalle del encabezado: el recuadro **"Imagen pendiente"** se salía de lugar y ahora se ve como un contador más de la fila.

## 7. Polos con referencia BTEX → Tela nueva

Los **8 polos** cuya referencia empieza por **BTEX** se pasaron de *Tela antigua* a **Tela nueva**:

| Referencia | Color |
|---|---|
| BTEXCMLNEGROROJO | Negro Rojo |
| BTEXCMLNEGROVERDE | Negro Verde |
| BTEXCMLNEGROBLANCO | Negro Blanco |
| BTEXCMCNEGROROJO | Negro Rojo |
| BTEXCMCROJONEGRO | Rojo Negro |
| BTEXCMCNEGROVERDE | Negro Verde |
| BTEX4MLNEGROVERDE | Negro Verde |
| BTEX4MCNEGROROJO | Negro Rojo |

Se actualizó en cada tarjeta la **etiqueta** (ahora verde "Tela nueva"), la **clase** y el atributo `data-tela`, por lo que también quedan bien clasificados en el **filtro "Tela nueva"** y en los collages.

**Contadores del encabezado actualizados** (son 214 unidades que pasan de antigua a nueva):
- Und. tela antigua: **1,851 → 1,637**
- Und. tela nueva: **33 → 247**
- Total en stock: 1,884 (sin cambios)

---

### Notas
- Todos los cambios están dentro del mismo archivo HTML; no se agregaron dependencias externas.
- Se verificó la sintaxis del JavaScript y se renderizó la página para confirmar el aspecto en modo día y noche.
