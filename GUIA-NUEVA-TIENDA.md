# Guía: montar una web de colchones nueva con este tema

El tema (diseño) trae TODO hecho. Lo único que hay que crear en cada tienda nueva son los **datos** (productos, colecciones, menús, descuentos, páginas) y conectar el **aviso de leads** (Telegram). Sigue esta checklist y en un rato tienes una tienda igual.

---

## 1) Subir el tema
**Opción A (GitHub, recomendada):** Tienda online → Temas → *Añadir tema* → **Conectar desde GitHub** → repo `dormidarte-theme`, rama `main`.
**Opción B (ZIP):** *Añadir tema* → **Subir archivo zip** → `Dormidarte-plantilla-colchones.zip`.

> El tema queda SIN publicar. Publícalo cuando esté todo listo.

---

## 2) Productos (¡los "handles" deben coincidir!)
El tema llama a los productos por su **handle** (URL). Crea los productos con **exactamente** estos handles y asígnales su **plantilla** (en la ficha del producto → *Plantilla de tema*):

| Producto | Handle exacto | Plantilla |
|---|---|---|
| Prestance | `prestance` | `product.prestance` |
| Iris | `colchon-iris-muelles-ensacados` | `product.iris` |
| Prestance Plus | `prestance-plus` | `product.prestance-plus` |
| Carbon | `carbon` | `product.carbon` |
| AloeVera Doble Cara | `aloevera-doble-cara` | `product.aloevera` |
| Beginn | `beginn` | `product.beginn` |
| Sahara Dual | `sahara-dual` | `product.sahara-dual` |
| Blue Vi | `blue-vi` | `product.blue-vi` |
| Canapé Noblia | `canape-noblia` | `product.canape` |
| Canapé Magna | `canape-magna` | `product.canape` |
| Canapé Imperial | `canape-imperial` | `product.canape` |

- **Variantes/medidas:** usa opciones "Ancho" y "Largo" (o "Medida"). Las medidas estándar del quiz: 90×190, 135×190, 140×200, 150×190. El Iris es el "comodín" (todas las medidas).
- **Precios:** pon `Precio` y `Precio de comparación` (para que salga el tachado y "Oferta").
- **Fotos del producto:** súbelas en cada producto (la 1ª = render sobre blanco; luego ambiente y detalles → así el mosaico queda bien).
- Forma rápida: en la tienda original, **Productos → Exportar** (CSV) y en la nueva **Importar** ese CSV (trae productos, variantes, precios y fotos).

---

## 3) Colecciones
- **`colchones`** (título "COLCHONES"): los 8 colchones de arriba (todos menos canapés).
- **`canapes`** (título "CANAPÉS"): canape-noblia, canape-magna, canape-imperial.

(Usa colecciones **manuales** o automáticas por tipo/etiqueta.)

---

## 4) Menú principal (Navegación → "Menú principal")
- **Ofertas** → `/collections/colchones` *(el tema lo redirige al quiz automáticamente)*
- **Colchones** → `/collections/colchones`
  - Blandos → `/collections/colchones`
  - Medios → `/collections/colchones`
  - Firmes → `/collections/colchones`
- **Canapés** → `/collections/canapes`
  - Canapé Noblia → `/products/canape-noblia`
  - Canapé Magna → `/products/canape-magna`
  - Canapé Imperial → `/products/canape-imperial`
- **Encuentra tu colchón** → `/#quiz`
- **Sobre nosotros** → `/pages/sobre-nosotros`
- **FAQ** → `/pages/faq`
- **Contacto** → `/pages/contacto`

---

## 5) Descuentos (Descuentos → Crear código)
- **`10MICOLCHON`** → 10% en colección `colchones`. **No combinable** con otros descuentos de producto/pedido.
- **`COMPRAYA5`** → 5% en todo el pedido. **No combinable**. (Es la oferta flash de la notificación de carrito.)

---

## 6) Páginas (Contenido → Páginas)
Crea estas páginas y asígnales su plantilla:

| Página | Handle | Plantilla |
|---|---|---|
| Sobre Dormidarte | `sobre-nosotros` | `page.sobre-nosotros` |
| Preguntas frecuentes | `faq` | `page.faq` |
| Contacto | `contacto` | `page.contact` |
| Devoluciones y garantía | `devoluciones-y-garantia` | `page.devoluciones-y-garantia` |

(Los textos base ya están en las plantillas; solo ajusta datos de la empresa: email, teléfono, dirección, CIF.)

---

## 7) Aviso de leads del quiz (Telegram)
El quiz manda cada lead por **email** (al email de la tienda) y, opcional, un **aviso a Telegram**:
1. Telegram → **@BotFather** → `/newbot` → copia el **TOKEN**.
2. Abre tu bot y pulsa **Iniciar**. Consigue tu **Chat ID** con **@userinfobot**.
3. Crea un **Cloudflare Worker** (proxy) con el código de `snippets/pro-toast.liquid` (ver README interno) que reenvía a Telegram con el TOKEN oculto.
4. Pega la **URL del worker** en: Editor → sección *Quiz encuentra tu colchón* → **URL del proxy de avisos**.

> Importante: NUNCA metas el token de Telegram directamente en el tema (queda público). Usa siempre el proxy.

---

## 8) Logo y remates
- **Logo:** Editor → Configuración → **Logo** → sube el logo (recortado, sin márgenes) → Guardar. Aparece en cabecera y en la notificación de carrito.
- **Email de la tienda:** Configuración → verifica el email donde llegan los leads del quiz.
- **Publicar** el tema cuando todo esté listo.

---

## Resumen de lo que YA trae el tema (no tocar)
Hero slider, quiz con recomendación + 3 precios + descuento, galería estilo Apple, escaparate visual, ficha estilo Sklum (mosaico, medidas en botones, precio en botón, estrellas), mega-menú con fotos, notificaciones iOS (añadido + oferta flash con cuenta atrás), badges Klarna/Pepper, financiación, WhatsApp "¿Tienes dudas?", secciones de ventajas, y todas las fotos de diseño.
