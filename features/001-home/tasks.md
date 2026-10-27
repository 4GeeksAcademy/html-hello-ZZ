# tasks.md — Home (home.html)

> **Tareas atómicas para implementar la página de inicio de MAISON NOIRE.**  
> Basado en `plan.md`. Cada tarea es un paso pequeño y verificable.  
> Tachar el checkbox al completar la tarea. No pasar a la siguiente hasta terminar la anterior.

## Alcance actualizado

- Archivo de implementación: `features/001-home/home.html`, no `index.html`.
- Productos: rejilla de 1 columna en móvil, 2 desde 768px y 4 desde 1024px, sin desplazamiento horizontal obligatorio.
- Interfaz y metadatos en español; nombres propios de producto sin traducir.
- Los commits, el push y la apertura de PR requieren autorización explícita antes de ejecutarlos.
- Los enlaces a otras vistas son relativos a la ubicación de `home.html`: `../../catalogo.html` y `../../producto.html`.
- Ejecución de todas las fases autorizada. Las comprobaciones HTTP omitidas y los hitos Git pendientes no se marcarán como realizados ni bloquearán las siguientes fases de implementación.
- Añadir URL canónica, `og:url` e imagen social cuando se confirme el dominio de publicación y exista una imagen de campaña; no inventar una URL de producción.

## Estado de entrega

- Las cinco fases de implementación están realizadas en `home.html`, en el orden previsto.
- Editor: sin errores detectados. Revisión estática: dos listas, doce productos y ofertas, textos alternativos y jerarquía de encabezados presentes.
- Pendientes: comprobación HTTP, carga real de imágenes y fuentes, navegación por teclado y capturas a 375px, 768px y 1280px. Los comandos de validación fueron omitidos por el usuario.
- Catálogo, producto y carrito todavía no existen; sus enlaces relativos están preparados, pero no pueden darse por funcionales hasta implementar esas vistas.
- Las fotografías son ilustrativas. La búsqueda y las opciones de cuenta no tienen lógica de aplicación; las opciones de cuenta están deshabilitadas.
- No se han ejecutado commits, push ni apertura de PR. La URL canónica y `og:url` requieren confirmar el dominio público; la imagen social ya está añadida.

---

## 🚧 Fase 1 — Esqueleto HTML + Head + Navbar

### Tareas de preparación

- [x] **T1.1** — Confirmar que la rama Git activa es `features/home` (`git branch`)
- [x] **T1.2** — Preparar el archivo existente `features/001-home/home.html` como destino de la implementación

### Tareas de estructura base

- [x] **T1.3** — Escribir `<!DOCTYPE html>` y `<html lang="es">` con las meta etiquetas obligatorias (`charset`, `viewport`, `description`, `title`)
- [x] **T1.4** — Añadir el CDN de Tailwind CSS v4 (`<script src="https://cdn.jsdelivr.net/npm/@tailwindcss/browser@4"></script>`)
- [x] **T1.5** — Añadir Google Fonts: preconnect + Playfair Display (500,600,700,italic) + Inter (300,400,500,600)
- [x] **T1.6** — Añadir Open Graph tags (`og:title`, `og:description`, `og:type`, `og:locale`, `og:site_name`); reservar `og:url` hasta confirmar la URL pública

### Tareas de Schema.org y Skip Link

- [x] **T1.7** — Añadir `<body itemscope itemtype="https://schema.org/WebSite">` con propiedades `url`, `name`, `description` e idioma español
- [x] **T1.8** — Añadir Skip Link como primer elemento del body: `<a href="#main-content">` con clases `sr-only` y estilos focus, y crear su destino `<main id="main-content">`

### Tareas del Navbar

- [x] **T1.9** — Añadir `<header itemscope itemtype="https://schema.org/Store">` con `<nav aria-label="Navegación principal">`, usando los roles semánticos nativos
- [x] **T1.10** — Añadir el logo enlazado a `home.html`, con Playfair Display italic y nombre accesible en español
- [x] **T1.11** — Añadir el formulario `role="search"` con `<input type="search">`, etiqueta asociada y botón Buscar
- [x] **T1.12** — Añadir el menú de cuenta con `<details>` y `<summary>`, accesible por teclado y táctil sin JavaScript, con "Mi perfil", "Mis pedidos", "Cerrar sesión"
- [x] **T1.13** — Aplicar estilos al navbar: fondo `bg-[#5F5449]`, texto `text-[#EBFCFB]`, búsqueda en segunda fila en móvil y cabecera en una fila en escritorio

### Tareas de cierre de Fase 1

- [ ] **T1.14** — Verificar que la página carga en Flask sin errores (`python3 server.py`)
- [ ] **T1.15** — Hacer commit: `feat: add HTML skeleton, navbar and SEO meta tags`
- [ ] **T1.16** — Marcar fase 1 como completada en el plan

---

## 🚧 Fase 2 — Hero Section

### Tareas del Hero

- [x] **T2.1** — Añadir sección de campaña con fotografía, superposición de contraste y espaciado adaptable
- [x] **T2.2** — Añadir el `<h1>` con MAISON NOIRE en Playfair Display y el mensaje "La elegancia de la sombra" como texto de apoyo
- [x] **T2.3** — Añadir el subtítulo sobre la nueva colección otoño-invierno
- [x] **T2.4** — Añadir CTA "Descubrir la colección" enlazado a `../../catalogo.html`, con hover, foco visible y nombre accesible

### Tareas de cierre de Fase 2

- [ ] **T2.5** — Verificar gradiente, tipografía, hover y focus del CTA
- [ ] **T2.6** — Hacer commit: `feat: add hero section with gradient and CTA`

---

## 🚧 Fase 3 — Listado "Novedades" (6 productos)

### Tareas de estructura de la sección

- [x] **T3.1** — Añadir sección `ItemList`, título Novedades en Playfair Display y nombre accesible mediante `aria-labelledby`
- [x] **T3.2** — Añadir lista en rejilla `.product-grid` con 1/2/4 columnas y nombre accesible "Lista de novedades"

### Tareas de cards de producto (Novedades)

- [x] **T3.3** — Añadir card del producto 1: **Blouson Nocturne** (490€) con badge "Nuevo", fotografía ilustrativa, Schema.org Product+Offer y alt text
- [x] **T3.4** — Añadir card del producto 2: **Sneakers Minuit** (450€) con badge "Nuevo"
- [x] **T3.5** — Añadir card del producto 3: **Veste Ébène** (520€) con badge "Nuevo"
- [x] **T3.6** — Añadir card del producto 4: **Écharpe Cendré** (180€) con badge "Nuevo"
- [x] **T3.7** — Añadir card del producto 5: **Sac Nocturne** (350€) con badge "Nuevo"
- [x] **T3.8** — Añadir card del producto 6: **Blazer Brume** (620€) con badge "Nuevo"

### Tareas de cierre de Fase 3

- [ ] **T3.9** — Verificar rejilla 1/2/4 sin desbordamientos, estados hover y focus de tarjetas, y enlaces a `../../producto.html`
- [ ] **T3.10** — Hacer commit: `feat: add Novedades section with horizontal scroll and 6 products`

---

## 🚧 Fase 4 — Listado "Más Vendidos" (6 productos)

### Tareas de estructura de la sección

- [x] **T4.1** — Añadir sección `ItemList`, título Más vendidos y nombre accesible mediante `aria-labelledby`
- [x] **T4.2** — Añadir lista en rejilla `.product-grid` con 1/2/4 columnas y nombre accesible "Lista de más vendidos"

### Tareas de cards de producto (Más Vendidos)

- [x] **T4.3** — Añadir card del producto 1: **Chemise Ombre** (280€) con badge "Más vendido"
- [x] **T4.4** — Añadir card del producto 2: **Pantalon Cendré** (320€) con badge "Más vendido"
- [x] **T4.5** — Añadir card del producto 3: **T-shirt Velours** (180€) con badge "Más vendido"
- [x] **T4.6** — Añadir card del producto 4: **Sacoche Sépia** (260€) con badge "Más vendido"
- [x] **T4.7** — Añadir card del producto 5: **Manteau Brume** (680€) con badge "Más vendido"
- [x] **T4.8** — Añadir card del producto 6: **Bottes Crépuscule** (490€) con badge "Más vendido"

### Tareas de cierre de Fase 4

- [ ] **T4.9** — Verificar rejilla 1/2/4, etiquetas y enlaces a `../../producto.html`
- [ ] **T4.10** — Hacer commit: `feat: add Más Vendidos section with horizontal scroll and 6 products`

---

## 🚧 Fase 5 — Footer + Cierre y Validación

### Tareas del Footer

- [x] **T5.1** — Añadir `<footer>` con rol nativo `contentinfo`, fondo `bg-[#5F5449]`, texto `text-[#EBFCFB]` y rejilla de 3 columnas desde tablet
- [x] **T5.2** — Añadir columna "Categorías" con enlaces relativos para Calzado, Camisas, Pantalones y Accesorios
- [x] **T5.3** — Añadir columna "Legal" con apartados desplegables sin JavaScript: Términos y condiciones, Política de privacidad y Sobre MAISON NOIRE
- [x] **T5.4** — Añadir columna "Contacto" con dirección, email y marcas sociales decorativas (IG, FB, X) con `aria-hidden="true"`
- [x] **T5.5** — Añadir línea divisoria y copyright: "© 2026 MAISON NOIRE. Todos los derechos reservados."

### Tareas de validación final

- [x] **T5.6** — Verificar estáticamente que el único `<script>` es el CDN requerido de Tailwind y que no hay JavaScript propio; Google Fonts se carga mediante CSS
- [ ] **T5.7** — Verificar navegación por teclado: Tab, Enter, focus visible en todos los elementos
- [ ] **T5.8** — Verificar a 375px, 768px y 1280px: productos en 1, 2 y 4 columnas respectivamente, sin texto cortado ni desbordamiento horizontal
- [x] **T5.9** — Revisar estáticamente Schema.org: WebSite, Store, 2× ItemList, 12× Product y 12× Offer; validación externa pendiente
- [ ] **T5.10** — Verificar navegación: logo → `home.html`, CTA y categorías → `../../catalogo.html`, tarjetas → `../../producto.html`, carrito → `../../carrito.html`; destinos externos a Home todavía pendientes de implementación
- [x] **T5.11** — Revisar alt text descriptivo en las 12 imágenes de producto y la imagen de campaña
- [x] **T5.12** — Revisar jerarquía: un `h1` de marca, `h2` por sección y `h3` para cada producto, sin saltos

### Tareas de cierre de Fase 5

- [ ] **T5.13** — Hacer commit: `feat: add footer with categories, legal, contact and final accessibility validation`
- [x] **T5.14** — Actualizar `PROGRESS.md` con la implementación de Home y sus validaciones pendientes
- [ ] **T5.15** — Hacer push de la rama `features/home` a origin
- [ ] **T5.16** — Abrir Pull Request de `features/home` → `main`

---

## ✅ Resumen de progreso

| Fase | Tareas totales | Completadas |
|---|---|---|
| Fase 1 — Esqueleto + Navbar | 16 | 13 |
| Fase 2 — Hero | 6 | 4 |
| Fase 3 — Novedades | 10 | 8 |
| Fase 4 — Más Vendidos | 10 | 8 |
| Fase 5 — Footer + Validación | 16 | 10 |
| **Total** | **58** | **43** |

---

> **Implementación de las cinco fases terminada. Pruebas visuales y publicación pendientes.**  
> Los checkboxes sin marcar corresponden a comprobaciones no ejecutadas, integración con vistas pendientes o acciones Git que requieren autorización.