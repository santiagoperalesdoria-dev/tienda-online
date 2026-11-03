# Verde Vivo — Tienda virtual con Vue 3

Proyecto académico para practicar **props**, **emits**, componentes reutilizables y estado compartido en `App.vue`, siguiendo la guía de la actividad.

## Requisitos
- Node.js LTS
- npm
- Visual Studio Code (recomendado)

## Cómo ejecutar
1. Descomprime el proyecto y abre esta carpeta en VS Code.
2. Abre la terminal en la carpeta del proyecto.
3. Instala las dependencias:

   ```bash
   npm install
   ```

4. Inicia el servidor de desarrollo:

   ```bash
   npm run dev
   ```

5. Abre en el navegador la dirección local que muestre Vite (normalmente `http://localhost:5173`).

Para comprobar la compilación de producción:

```bash
npm run build
npm run preview
```

## Componentes
- `App.vue`: estado compartido (`productos`, `carrito`, `mostrarFactura`, `numeroFactura`), filtros y lógica.
- `AppHeader.vue`: nombre de la tienda, contador del carrito y evento `ver-carrito`.
- `ListaProductos.vue`: recibe `productos` por props y reenvía `agregar-producto`.
- `ProductoCard.vue`: tarjeta de producto, precio con descuento calculado con `computed` y evento `agregar-al-carrito`.
- `CarritoCompra.vue`: cantidades, eliminación, resumen y evento `finalizar-compra`.
- `FacturaCompra.vue`: detalle de factura, descuentos, IVA del 19 % y evento `nueva-compra`.
- `AppFooter.vue`: pie de página de presentación.

## Decisiones importantes
- El estado compartido vive únicamente en `App.vue`.
- No se usa Pinia, Vuex, `provide/inject` ni event bus.
- Las props no se modifican dentro de los componentes hijos.
- Los eventos se declaran con `defineEmits` y se nombran en kebab-case.
- Las imágenes de muestra se cargan desde URLs externas; para una entrega sin conexión, reemplázalas por imágenes locales dentro de `public/img`.
- La factura es demostrativa: el IVA se calcula al 19 % sobre el subtotal después de descuentos. El envío se muestra como “Por calcular” y no se suma al total.

## Flujo de eventos
`ProductoCard` → `ListaProductos` → `App.vue` → actualiza el carrito.

## Personalización
Puedes cambiar el nombre de la tienda, correo, productos, categorías y precios desde `src/App.vue`.
