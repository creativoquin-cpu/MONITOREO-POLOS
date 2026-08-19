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

---

# Segunda tanda — 19 de agosto de 2026

**Archivo:** `catalogo_4.html`

## 8. Una sola barra de filtros en vez de cuatro cajas apiladas

**Antes:** antes de ver el primer polo había nueve bloques apilados: logo, pestañas,
cifras, buscador con seis botones, párrafo de ayuda, barra de alertas, «Selección
rápida» y «Filtrar por talla». Unos 554 px de controles.

**Ahora:** una sola barra dentro del encabezado, agrupada por **frecuencia de uso**:

- **Siempre a la vista:** buscador · **Talla** (las tallas ya no son una fila aparte) ·
  **Ver** (Todas, Tela antigua, Tela nueva, ⚠ Por agotarse).
- **A un clic, en ⚙ Más opciones:** el aviso de stock bajo, la selección por rango de
  cantidad y los filtros de poco uso (Solo con stock, Tela mixta, Sin foto).
- **Franja de estado permanente:** «Mostrando 34 de 90 polos» con una etiqueta por cada
  filtro activo, cada una con su ✕ para quitarla, más el botón **✕ Quitar filtros**.
- El encabezado **se encoge al bajar**: las cifras y el título se ocultan y quedan ~168 px.
- El párrafo de ayuda ahora es plegable: se ve solo la línea de «haz clic en el polo»
  y el resto se abre con **Ver más ayuda**.

## 9. Se retiran «▲ Más stock» y «▼ Menos stock»

Estos dos botones **no hacían lo que decían**. `runQuick()` llamaba a `showOnly()`, que
solo cambia qué tarjetas se ven, **sin reordenarlas nunca**. Al pulsarlos la cuadrícula
quedaba idéntica. Su único efecto real era el orden de las celdas del collage, algo
imposible de adivinar desde el botón. Se quitaron en vez de dejarlos engañando.

## 10. Mis filtros guardados (nuevo)

Botón **⭐ Mis filtros** en la barra. Permite crear filtros con nombre combinando:

- **Categoría:** Tela antigua, Tela nueva, Tela mixta, Con stock, Por agotarse, Sin foto.
- **Tallas:** XS a 4XL, varias a la vez.
- **Cantidad desde / hasta.**

Reglas: no marcar nada = no restringe. Dentro de «tallas» y dentro de cada grupo de
categoría se combinan con **o**; los grupos entre sí con **y**. El rango de cantidad se
mide sobre la **suma de las tallas marcadas**; si no marcas tallas, sobre el total de la
prenda — la misma regla del punto 1 de este documento.

Los filtros guardados **se combinan** con el buscador y con los botones de arriba, así
que puedes afinar encima de uno.

## 11. Llevarse los filtros a otro computador ~~(descartado, ver punto 17)~~

**El problema:** los filtros se guardan en la memoria del navegador donde se crearon.
Esa memoria **no viaja** cuando copias el archivo HTML, así que en otro equipo no salen.

**No se puso un botón de «actualizar página»** porque no habría servido de nada: no hay
nada que refrescar, el dato sencillamente no está en ese computador.

**Lo que sí se hizo:**

- **📤 Llevar mis filtros a otra computadora** — descarga `mis-filtros-KLIXMANT.json`,
  de unos pocos KB. Se manda por WhatsApp o se copia en la USB junto al catálogo.
- **📥 Traer filtros de otra computadora** — abre ese archivo y añade los filtros a los
  que ya haya. Si alguno se llama igual, lo reemplaza.
- Si tienes el catálogo abierto en **dos pestañas del mismo equipo**, al volver a una se
  relee la lista sola. Ese es el único «actualizar» que tiene sentido aquí.
- Si el navegador no deja guardar (Firefox abierto con doble clic, o modo incógnito), el
  panel **sigue funcionando** durante la sesión y avisa de que hay que exportar antes de
  cerrar.

## 12. Tela mixta: 5 referencias que no salían en ningún filtro

Al revisar los datos aparecieron **5 tarjetas con `data-tela="mixta"`** (unidades de tela
antigua y nueva a la vez): B4MCRV Gris Jaspe, B4MLR Gris Jaspe, BCMCR Rojo, BCMCR Azul
Oscuro y BCML Blanco.

Los botones eran solo «Tela antigua» y «Tela nueva», así que **esas 5 solo aparecían en
«Todas»**. Se añadió **Tela mixta** como botón (en ⚙ Más opciones) y como categoría del
filtro guardado. No se cambió qué significa «antigua» ni «nueva»: una prenda mixta sigue
sin colarse en ninguna de las dos.

### Comprobaciones

- Los tres bloques de JavaScript compilan (`node --check`).
- **26 pruebas** del filtro guardado contra las 90 tarjetas reales del catálogo,
  ejecutando el código tal como quedó en el archivo. Todas correctas.
- **22 pruebas** del saneado de importación (archivo corrupto, ajeno, campos con basura,
  nombres larguísimos, rangos al revés). Todas correctas.
- Datos intactos: 252 registros SKU, 1.884 unidades, 1.637 antigua / 247 nueva.
- Sin verificación visual en navegador: la apertura de páginas quedó bloqueada en esta
  sesión. **Falta abrirlo y mirarlo.**

## 13. Varias tallas a la vez

**Antes:** los botones de talla eran excluyentes. Al marcar M se desmarcaba S.

**Ahora:** se marcan **las que quieras**. Si marcas S, M y XL salen las prendas que tengan
stock en **alguna** de esas tres. **Todas** limpia la selección. El contador dice
«N prendas en talla S, M, XL».

Además, **dentro de cada tarjeta solo se ven las tallas filtradas**. Si filtras por S, la
tarjeta muestra únicamente el stock de S, no el desglose completo. Sin filtro se ven todas.

## 14. Botón «Seleccionar estos» por referencia

A la derecha de cada cabecera de referencia (Buzo texturizado, Buzo 4 botones, etc.) hay
un botón que mete al collage, de una vez, **todos los polos visibles de esa referencia**.
Respeta el filtro que tengas puesto: si estás en talla S, selecciona solo los que tienen S.
Cuando ya están todos seleccionados el botón cambia a **✓ Quitar selección**. Las
referencias sin polos disponibles lo muestran deshabilitado.

## 15. Textos más cortos y desplegable sin barra lateral

- «Cantidad para filtrar: entre X y Y uds» → **«Cantidad: de X a Y uds»**
- «Seleccionar todo» → **«Todos»** · «✓ Aplicar» → **«Seleccionar»**
- «Aviso de stock bajo» → **«Aviso de stock»** · «Otros filtros» → **«Otros»**
- «Seleccionar varios polos a la vez» → **«Selección rápida»**
- «Avisarme cuando queden X unidades o menos» → **«Avisar con X unidades o menos»**
- El desplegable **⚙ Más opciones** ya no pide barra de desplazamiento lateral: todo
  el contenido se ajusta al ancho.

## 16. El cruce de ventas ya reevalúa los filtros

**Bug encontrado:** al aplicar un cruce (y al restaurar el inventario) se repintaban las
tarjetas con el stock nuevo, pero **nunca se volvía a llamar a `apply()`**. Los filtros
seguían calculados sobre las cifras de antes del descuento: una prenda que quedaba
agotada seguía apareciendo bajo «Con stock», y el filtro por talla no se enteraba.
Corregido en los dos sitios.

### Comprobaciones de esta tanda

- Los tres bloques de JavaScript compilan.
- **70 pruebas** en total contra las 90 tarjetas reales, ejecutando el código tal como
  quedó en el archivo: 26 del filtro guardado, 22 del filtro de varias tallas, 22 del
  saneado de importación. Todas correctas.
- Datos intactos: 252 registros SKU, 1.884 unidades, 1.637 antigua / 247 nueva.
- Sigue **sin verificación visual**: la apertura del navegador está bloqueada en esta
  sesión. Hay que abrirlo y mirarlo.

## 17. Los filtros ahora viajan dentro del archivo (sustituye al punto 11)

**Por qué cambió:** el punto 11 resolvía el problema descargando un archivito `.json` y
abriéndolo en el otro equipo. Funcionaba, pero era un paso manual cada vez y llenaba de
archivos sueltos. Además el catálogo se publica en una **URL**, así que todo el equipo
abre la misma página: no hay nada que llevar de un lado a otro.

**Qué se quitó:**

- El botón «📤 Llevar mis filtros a otra computadora».
- El botón «📥 Traer filtros de otra computadora».
- El archivo `mis-filtros-KLIXMANT.json` y el helper de descarga.

**Qué hay ahora.** El panel ⭐ Mis filtros tiene dos listas:

1. **Filtros del catálogo** — van escritos dentro del propio HTML, en la lista
   `FILTROS_BASE`. Como viajan con el archivo, **aparecen en cualquier equipo** que abra
   la URL. No se pueden borrar desde la interfaz.
2. **Mis filtros** — los que crea cada persona. Se guardan en su navegador y solo los ve
   ella. Esos sí se borran.

**Para cambiar los filtros del catálogo** se edita la lista `FILTROS_BASE` en el HTML.
Cada entrada lleva `nombre`, `cats`, `tallas`, `min` y `max`, con las mismas reglas del
punto 10. Pasan por el mismo saneado que los filtros del usuario, así que una entrada mal
escrita se descarta sola en vez de romper el panel.

Los cinco que quedaron de arranque, verificados contra los datos reales:

| Filtro | Criterio | Polos |
|---|---|---|
| Por agotarse | Por agotarse, hasta 5 uds | 51 |
| Tela nueva | Tela nueva | 12 |
| Tela mixta | Tela mixta | 5 |
| Con harto stock | Con stock, desde 20 uds | 23 |
| Sin foto | Sin foto | 6 |

**Pendiente:** son los que se deducen de los datos, no los del negocio. Falta que se
definan los reales y se sustituyan en `FILTROS_BASE`.

## 18. Anchos de los recuadros en los desplegables

`.controls input` (línea 19) le impone `min-width:220px` y `flex:1` a **todo `<input>`**
que viva dentro de `#controls-p`, y los dos desplegables están ahí dentro. Por eso las
cajas de cantidad salían del ancho de una barra y **cada casilla de talla o de tela
también**, ya que un checkbox también es un `<input>`.

Corregido con reglas por `id` (`#adv-pop`, `#fg-pop`), que ganan a cualquier otra:

- **números** → 46 px, tres dígitos, sin flechas de subir/bajar (ahorran ~15 px)
- **casillas** → ancho propio, sin mínimo, sin estirarse
- **texto** → ancho completo pero sin mínimo forzado
- más un `min-width:0` general para cualquier campo que se añada en el futuro
