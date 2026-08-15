# KLIXMANT — Catálogo de referencias, stock, tela y ventas 2026

Documento de referencia del archivo **`Catalogo_KLIXMANT_referencias_stock_2026.html`**: qué contiene, cómo funciona cada vista y qué reglas de conversión usa. Todo el archivo funciona de forma local en el navegador (no requiere internet).

## Fuentes de datos

- **`REFERENCIAS Y COLORES POLOS NUEVOS KLIXMANT 2023.pdf`** — imágenes de los polos por referencia y color.
- **`Inventario_clasificacion_telapolo_2026.xlsx`**:
  - Hoja **Clasificación** → 252 referencias (SKU) con stock por talla y clasificación tela antigua / tela nueva.
  - Hoja **Inventario de Telas** → metros de tela por proveedor y color.

## Cifras clave

| Concepto | Valor |
|---|---|
| Unidades en stock (prendas) | 1.884 |
| Referencias globales | 12 |
| Colores | 90 |
| Unidades tela antigua | 1.851 |
| Unidades tela nueva | 33 |
| Tela disponible | 994,85 m ≈ 994 polos por producir |
| — de tela antigua (Buda + Centauro) | 566 m |
| — de tela nueva (Catar + Cotton) | 428,85 m |

## Vista 1 · Prendas terminadas

Una sección por **referencia global** (B4MLR, B4MCRV, BCVLML, B2ML, BCML, BCMCR, texturizadas, etc.). Cada tarjeta muestra el color, la referencia, el **stock total**, el desglose por talla y la etiqueta **Tela antigua / Tela nueva** según la clasificación del inventario.

- **Imágenes:** solo se coloca imagen cuando corresponde exactamente a esa referencia. 51 colores tienen foto confirmada y 39 quedan como **«Imagen pendiente»** (recuadro del color) para actualizarlas después.
- Se retiraron dos imágenes mal emparejadas: **B4MCRV Azul Rey** (era un buzo negro manga larga) y **B2ML Rojo Vino** (era rosada).
- Buscador por color/referencia y filtros: Todas, Tela antigua, Tela nueva, Con stock, Por agotarse, Imagen pendiente.

## Vista 2 · Tela · polos por producir

Convierte el inventario de tela a **polos fabricables** con la regla **1 metro de tela = 1 polo**. El número grande de cada tarjeta son los polos posibles con la tela medida actualmente; abajo aparecen los metros reales y la comparación contra la cantidad inicial.

- **Buda** y **Centauro** = tela antigua · **Catar** y **Cotton** = tela nueva.

## Vista 3 · Cruce de ventas

Se sube el reporte de ventas en **Excel (.xlsx / .xls) o CSV** y el sistema descuenta las ventas del inventario.

**Cómo funciona:**

1. Detecta automáticamente la columna de referencia y la de cantidad (se pueden cambiar a mano) y la hoja.
2. **Reconoce las referencias** comparándolas con el inventario, ignorando espacios y mayúsculas (ej. «B4 ML R MOSTAZA M» = «B4MLRMOSTAZAM»).
3. Cada venta se separa en:
   - **De stock** = lo que hay disponible de esa talla (descuenta del inventario de prendas).
   - **Faltante (a producir)** = cuando la venta supera el stock de esa talla. Como esa unidad hay que producirla, **se descuenta de la tela** con la regla **1 unidad faltante = 1 metro** de la tela de ese color.
4. Las referencias que no existan en el inventario se listan aparte como **no encontradas**.

**Acciones:** aplicar el descuento al inventario mostrado (actualiza prendas y metros/polos de tela), descargar el **inventario resultante en CSV** (prendas + consumo de tela) o reiniciar para otro reporte.

### Mapeo color de polo → tela

212 de 252 referencias se enlazan a una tela del inventario. Cuando un polo tiene dos telas posibles (Negro y Blanco existen como tela antigua **Buda** y tela nueva **Catar**), por defecto se toma la **tela antigua**, salvo que la referencia sea claramente de tela nueva.

**Colores de polo sin tela en el inventario** (sus faltantes se marcan «Sin tela en inventario» y no descuentan metros): **Amarillo, Azul Rey, Caqui, Rojo Vino, Verde Manzana**.

## Alertas de stock bajo

Insignia en cada tarjeta cuando el stock está por agotarse o agotado, con **umbral configurable**:

- **Polos:** aviso cuando quedan **≤ 5 unidades** (por defecto). «Agotado» en 0.
- **Tela:** aviso cuando quedan **≤ 15 metros** (por defecto). «Agotada» en 0.

Cada vista muestra un resumen (cuántas referencias/telas están por agotarse y cuántas agotadas), un filtro **«Por agotarse»** en prendas y **«Ver solo por agotarse»** en tela. Las alertas se recalculan automáticamente al aplicar un cruce de ventas.

## Reglas de conversión (resumen)

- **1 metro de tela = 1 polo.**
- **1 unidad faltante en el cruce = 1 metro de tela descontado** del color correspondiente.
- El stock terminado nunca baja de 0; el excedente vendido pasa a producción (tela).

---

*Generado desde el inventario de clasificación de tela polo 2026 y el documento de referencias y colores KLIXMANT.*
