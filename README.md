# README - BY_KMI Minidonuts

## Descripción del Proyecto

Este proyecto es un sitio web e-commerce para "BY_KMI", una tienda virtual especializada en la venta de minidonuts artesanales, anchetas y desayunos sorpresas. La plataforma permite a los usuarios explorar productos, agregarlos a un carrito de compras y realizar pedidos a través de WhatsApp.

## Características Principales

- **Catálogo de productos** con imágenes y descripciones
- **Carrito de compras** funcional
- **Sistema de autenticación** (registro e inicio de sesión)
- **Integración con WhatsApp** para finalizar pedidos
- **Diseño responsive** que funciona en dispositivos móviles y desktop
- **Galería de imágenes** para cada producto

## Tecnologías Utilizadas

- HTML5
- CSS3 (con variables CSS)
- JavaScript (ES6)
- Bootstrap 5
- Font Awesome (para íconos)
- Google Fonts (Fredoka)

## Estructura del Proyecto

```
by-kmi-minidonuts/
├── index.html          # Página principal
├── ventascoorporativas.html # Página de ventas corporativas
├── assets/
│   ├── images/         # Todas las imágenes del proyecto
│   │   ├── Mini1.jpg
│   │   ├── Mini2.jpg
│   │   ├── ...
│   │   └── Logoby.jpeg
│   └── styles/         # (Opcional) CSS personalizado
└── README.md           # Este archivo
```

## Instalación y Uso

1. Clona el repositorio:
   ```bash
   git clone https://github.com/tu-usuario/by-kmi-minidonuts.git
   ```

2. Abre el archivo `index.html` en tu navegador web.

3. Para desarrollo, puedes usar Live Server en VS Code o cualquier servidor local.

## Personalización

Para personalizar el sitio:

1. **Productos**: Modifica las secciones de productos en el HTML y actualiza las imágenes correspondientes.

2. **Estilos**: Edita las variables CSS en la sección `<style>` del `<head>` para cambiar colores y fuentes.

3. **Redes sociales**: Actualiza los enlaces en la sección de contacto.

4. **WhatsApp**: Cambia el número de teléfono en la función `finalizarCompra()` del JavaScript.

## Funcionalidades JavaScript

- Gestión del carrito de compras
- Sistema de registro e inicio de sesión (con localStorage)
- Contador de productos en el carrito
- Galerías de imágenes para productos
- Validación de formularios

## Consideraciones

- El sitio usa localStorage para persistir datos (usuarios, carrito), por lo que los datos se mantendrán solo en el navegador del usuario.
- Para un entorno de producción real, se recomienda implementar un backend para manejar usuarios y pedidos.
- Las imágenes de ejemplo deben ser reemplazadas por las imágenes reales de los productos.

## Licencia

Este proyecto está bajo la licencia MIT. Puedes usarlo como base para tu propio e-commerce de alimentos.

## Contacto

Para más información, contáctanos a través de nuestros canales oficiales:

- WhatsApp: [+57 321 9437192](https://wa.me/573219437192)
- Instagram: [@by_kmii](https://www.instagram.com/by_kmii)
- TikTok: [@by_kmii](https://www.tiktok.com/@by_kmii)
