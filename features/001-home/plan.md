# plan.md — Home (home.html)

> **Plan de implementación para la página de inicio de MAISON NOIRE.**  
> Basado en `specs.md` (especificaciones), `DESIGNS.md` (guía visual) y `CONTEXTO/que_hacer.md` (requisitos).  
> 5 fases secuenciales. Los commits, push y PR se ejecutarán únicamente con autorización explícita.

## Estado de implementación

Las cinco fases están implementadas en `features/001-home/home.html`. La solicitud más reciente sustituye el destino `index.html` y los carruseles horizontales del plan original por rejillas: una columna en móvil, dos desde 768px y cuatro desde 1024px.

| Fase | Implementación | Verificación |
|---|---|---|
| 1 — Estructura y cabecera | Realizada | Editor sin errores; comprobación HTTP omitida |
| 2 — Campaña | Realizada con fotografía, título de marca y CTA | Prueba visual pendiente |
| 3 — Novedades | Realizada: seis productos en rejilla | Revisión estática realizada; prueba visual pendiente |
| 4 — Más vendidos | Realizada: seis productos en rejilla | Revisión estática realizada; prueba visual pendiente |
| 5 — Footer | Realizada con categorías, contacto y apartados legales | Revisión estática realizada; teclado y responsive pendientes |

El detalle actualizado y los pendientes se registran en `tasks.md`. Las fotografías son ilustrativas. No hay JavaScript propio. Las páginas de catálogo, producto y carrito aún no existen. Los enlaces a ellas usan `../../` desde la ubicación actual de Home.

No se han realizado commits ni publicación. La URL canónica y `og:url` se añadirán cuando se confirme el dominio de despliegue. Los checklists siguientes conservan la referencia original; el estado de ejecución se sigue en `tasks.md`.

---

## 📋 Estado del Proyecto

| Elemento | Valor |
|---|---|
| **Rama activa** | `features/home` |
| **Archivo destino** | `features/001-home/home.html` |
| **Archivo en features/** | `features/001-home/home.html` (implementación de las cinco fases) |
| **Servidor** | `python3 server.py` (Flask en puerto 3000) |
| **Stack** | HTML semántico + Tailwind CSS v4 CDN + Google Fonts |
| **Sin** | JavaScript, frameworks, librerías externas |
| **Navbar/Footer** | Se copiarán idénticos en cada vista futura |

---

## 📐 Convenciones

- **Idioma**: Español — `lang="es"`, textos en español (los nombres de producto se mantienen en francés por ser nombres propios)
- **Precios**: En euros (€)
- **Imágenes**: `placehold.co` con colores de la paleta (`#5F5449`, `#9B6A6C`, `#B09398`, `#CEDFD9`, `#EBFCFB`)
- **Commits**: Prefijo `feat:` seguido de descripción clara
- **Schema.org**: `WebSite`, `Store`, `Product`, `Offer`, `ItemList`

---

## 🧱 Fases de Implementación

---

### Fase 1 — Esqueleto HTML + Head + Navbar

**Objetivo:** Crear `index.html` con estructura base, meta tags, Tailwind CDN, Google Fonts, Schema.org y navbar completa.

#### Archivos involucrados
- **Crear**: `/workspaces/html-hello-ZZ/index.html`

#### Checklist de implementación

- [ ] `<!DOCTYPE html>` y `<html lang="es">`
- [ ] `<head>` con:
  - `meta charset="UTF-8"`
  - `meta name="viewport" content="width=device-width, initial-scale=1.0"`
  - `meta name="description"` — descripción de MAISON NOIRE
  - `<title>MAISON NOIRE — Streetwear de Lujo</title>`
  - Tailwind CSS v4 CDN: `<script src="https://cdn.jsdelivr.net/npm/@tailwindcss/browser@4"></script>`
  - Google Fonts: preconnect + Playfair Display (500,600,700,italic) + Inter (300,400,500,600)
  - Open Graph tags: `og:title`, `og:description`, `og:type`, `og:url`
- [ ] `<body itemscope itemtype="https://schema.org/WebSite">` con:
  - `itemprop="url" content="https://maisonnoire.fr/"`
  - `itemprop="name" content="MAISON NOIRE"`
  - `itemprop="description" content="Marca francesa de streetwear de lujo"`
- [ ] **Skip link** — primer elemento del body:
  ```html
  <a href="#main-content"
     class="sr-only focus:not-sr-only focus:absolute focus:top-4 focus:left-4
            focus:z-50 focus:px-4 focus:py-2 focus:bg-[#9B6A6C] focus:text-[#EBFCFB]
            focus:ring-2 focus:ring-[#EBFCFB] focus:rounded"
     aria-label="Ir al contenido principal">
    Ir al contenido principal
  </a>
  ```
- [ ] `<header role="banner" itemscope itemtype="https://schema.org/Store">` con `<nav role="navigation" aria-label="Navegación principal">`
  - **Logo**: `<a href="/" aria-label="Ir al inicio">MAISON NOIRE</a>` con `font-['Playfair_Display'] italic tracking-widest`
  - **Búsqueda**: `<div role="search">` con `<label class="sr-only">` + `<input type="search">` con `placeholder="Buscar..."`, `aria-label="Buscar un producto"` y estilos focus
  - **Cuenta**: `<div class="group relative">` con botón "Cuenta" y dropdown CSS-only (`.invisible group-hover:visible group-focus-within:visible`) con enlaces: Mi perfil, Mis pedidos, Cerrar sesión
- [ ] Estructura navbar:
  - Fondo: `bg-[#5F5449]`
  - Texto: `text-[#EBFCFB]`
  - Altura: `h-16 lg:h-20`
  - Contenedor: `flex justify-between items-center max-w-7xl mx-auto px-4 lg:px-8`
  - Input búsqueda: `border border-[#B09398]/30 bg-[#5F5449] text-[#EBFCFB] placeholder:text-[#B09398] focus:ring-2 focus:ring-[#9B6A6C] focus:border-[#9B6A6C]`

#### Elementos Schema.org en esta fase
- `WebSite` en `<body>`
- `Store` en `<header>`

#### Commit
```
feat: add HTML skeleton, navbar and SEO meta tags
```

#### Criterios de validación
- [ ] La página carga en Flask sin errores
- [ ] Tailwind CDN se carga (los estilos se aplican)
- [ ] Google Fonts se cargan (Playfair Display + Inter)
- [ ] Skip link visible solo al navegar con teclado (Tab)
- [ ] Navbar visible con logo, búsqueda y dropdown cuenta
- [ ] Dropdown cuenta se abre con hover
- [ ] Schema.org presente en body y header

---

### Fase 2 — Hero Section

**Objetivo:** Implementar el Hero con gradiente, título, subtítulo y CTA.

#### Archivos involucrados
- **Editar**: `/workspaces/html-hello-ZZ/index.html`

#### Checklist de implementación

- [ ] `<section aria-label="Colección otoño-invierno" itemprop="mainEntityOfPage">`
- [ ] Gradiente: `bg-gradient-to-r from-[#5F5449] to-[#9B6A6C]`
- [ ] Padding: `py-20 lg:py-32`
- [ ] Contenedor: `max-w-7xl mx-auto px-4 lg:px-8`
- [ ] `<h1>` con `font-['Playfair_Display'] font-bold text-5xl lg:text-7xl tracking-[0.1em] leading-tight text-[#EBFCFB]`
  - Texto: `La Elegancia de la Sombra`
- [ ] `<p>` subtítulo con `font-['Inter'] text-lg lg:text-xl leading-relaxed text-[#EBFCFB]`
  - Texto: `La nueva colección otoño-invierno — donde el silencio encuentra el estilo.`
- [ ] CTA `<a href="catalogo.html">` con:
  - `bg-[#9B6A6C] hover:bg-[#5F5449] text-[#EBFCFB] transition-all duration-300`
  - `px-8 py-3 lg:px-10 lg:py-4 inline-block font-['Inter'] font-semibold tracking-widest uppercase`
  - `ring-2 ring-[#9B6A6C] ring-offset-2 focus:ring-[#EBFCFB] focus:outline-none`
  - `aria-label="Descubrir la colección otoño-invierno"`
  - Texto: `Descubrir →`

#### Elementos Schema adicionales
- Propiedades `url`, `name`, `description` del `WebSite` en body

#### Commit
```
feat: add hero section with gradient and CTA
```

#### Criterios de validación
- [ ] Gradiente visible de Taupe Noir a Rose Poudré
- [ ] Título h1 visible con Playfair Display
- [ ] CTA funcional que enlaza a `catalogo.html`
- [ ] CTA cambia de color en hover
- [ ] Focus visible con ring blanco en CTA
- [ ] Contraste AA: `#EBFCFB` sobre gradiente oscuro ✅

---

### Fase 3 — Listado "Novedades"

**Objetivo:** Sección de nuevos lanzamientos con 6 productos en scroll horizontal.

#### Archivos involucrados
- **Editar**: `/workspaces/html-hello-ZZ/index.html`

#### Checklist de implementación

- [ ] `<section itemscope itemtype="https://schema.org/ItemList" aria-label="Novedades">` con `py-12 lg:py-16`
- [ ] `<h2>` con `font-['Playfair_Display'] font-semibold text-2xl lg:text-3xl text-[#5F5449] tracking-widest`
  - Texto: `Novedades`
- [ ] Contenedor scroll: `flex gap-4 lg:gap-6 overflow-x-auto snap-x snap-mandatory px-4 lg:px-8 pb-4 scroll-px-4` con `role="list" aria-label="Lista de novedades"`
- [ ] 6 `<article itemscope itemtype="https://schema.org/Product" role="listitem" class="min-w-[220px] lg:min-w-[280px] snap-start">`
  - Estructura por card:
    ```html
    <article class="bg-white border border-[#B09398]/30 rounded-sm
                    transition-all duration-300 hover:shadow-md hover:-translate-y-1
                    min-w-[220px] lg:min-w-[280px] snap-start"
             itemscope itemtype="https://schema.org/Product"
             role="listitem">

      <!-- Badge opcional -->
      <div class="relative">
        <span class="absolute top-2 left-2 z-10 bg-[#CEDFD9] text-[#5F5449]
                     text-xs px-2 py-1 uppercase tracking-widest font-['Inter'] font-semibold">
          Nuevo
        </span>
        <a href="producto.html" class="block aspect-[3/4]">
          <img src="..." alt="..." class="object-cover w-full h-full"
               itemprop="image" loading="lazy" />
        </a>
      </div>

      <div class="p-4 lg:p-6">
        <h3 class="font-['Playfair_Display'] text-sm lg:text-base text-[#5F5449]"
            itemprop="name">Nombre del producto</h3>
        <p class="font-['Inter'] font-semibold text-[#9B6A6C] text-base lg:text-lg mt-1"
           itemprop="offers" itemscope itemtype="https://schema.org/Offer">
          <span itemprop="price" content="XXX">XXX</span>
          <span itemprop="priceCurrency" content="EUR">€</span>
        </p>
        <a href="producto.html"
           class="inline-block mt-2 text-[#9B6A6C] hover:text-[#5F5449] text-xs uppercase tracking-widest
                  transition-colors duration-200"
           aria-label="Ver producto [nombre]">
          Ver producto →
        </a>
      </div>
    </article>
    ```

#### Productos "Novedades"

| # | Producto | Precio | Imagen (placehold.co) | Alt text |
|---|---|---|---|---|
| 1 | **Blouson Nocturne** | 490€ | `https://placehold.co/600x800/5F5449/EBFCFB?text=Blouson+Nocturne&font=playfair` | `Blouson Nocturne — chaqueta de streetwear de lujo` |
| 2 | **Sneakers Minuit** | 450€ | `https://placehold.co/600x800/5F5449/EBFCFB?text=Sneakers+Minuit&font=playfair` | `Sneakers Minuit — zapatillas streetwear elegantes` |
| 3 | **Veste Ébène** | 520€ | `https://placehold.co/600x800/5F5449/EBFCFB?text=Veste+%C3%89b%C3%A8ne&font=playfair` | `Veste Ébène — chaqueta negra de colección` |
| 4 | **Écharpe Cendré** | 180€ | `https://placehold.co/600x800/9B6A6C/EBFCFB?text=%C3%89charpe+Cendr%C3%A9&font=playfair` | `Écharpe Cendré — accesorio de lana` |
| 5 | **Sac Nocturne** | 350€ | `https://placehold.co/600x800/B09398/5F5449?text=Sac+Nocturne&font=playfair` | `Sac Nocturne — bolso bandolera` |
| 6 | **Blazer Brume** | 620€ | `https://placehold.co/600x800/5F5449/EBFCFB?text=Blazer+Brume&font=playfair` | `Blazer Brume — blazer casual de lujo` |

#### Consideraciones
- `loading="lazy"` en imágenes para rendimiento
- `min-w-[220px]` en móvil, `min-w-[280px]` en desktop
- Badge "Nuevo" en todos (toda la sección son novedades)
- El scroll horizontal es CSS nativo, sin JavaScript

#### Commit
```
feat: add Novedades section with horizontal scroll and 6 products
```

#### Criterios de validación
- [ ] Sección "Novedades" visible con título en Playfair Display
- [ ] 6 cards en scroll horizontal con snap
- [ ] Cada card tiene imagen, nombre, precio y badge "Nuevo"
- [ ] Hover eleva la card (`-translate-y-1` + `shadow-md`)
- [ ] Las imágenes cargan con los colores de la paleta
- [ ] Schema `Product` y `Offer` en cada card
- [ ] Enlace "Ver producto" lleva a `producto.html`

---

### Fase 4 — Listado "Más Vendidos"

**Objetivo:** Sección de más vendidos con 6 productos en scroll horizontal.

#### Archivos involucrados
- **Editar**: `/workspaces/html-hello-ZZ/index.html`

#### Checklist de implementación

- [ ] `<section itemscope itemtype="https://schema.org/ItemList" aria-label="Más Vendidos">` con `py-12 lg:py-16`
- [ ] `<h2>`: mismo estilo que Novedades, texto `Más Vendidos`
- [ ] Misma estructura de scroll que Fase 3, con `aria-label="Lista de más vendidos"`
- [ ] 6 `<article>` con misma estructura que Fase 3
- [ ] Badge "Más vendido" en todos (estilo `bg-[#CEDFD9] text-[#5F5449]`)

#### Productos "Más Vendidos"

| # | Producto | Precio | Imagen (placehold.co) | Alt text |
|---|---|---|---|---|
| 1 | **Chemise Ombre** | 280€ | `https://placehold.co/600x800/9B6A6C/EBFCFB?text=Chemise+Ombre&font=playfair` | `Chemise Ombre — camisa elegante` |
| 2 | **Pantalon Cendré** | 320€ | `https://placehold.co/600x800/B09398/5F5449?text=Pantalon+Cendr%C3%A9&font=playfair` | `Pantalon Cendré — pantalón streetwear` |
| 3 | **T-shirt Velours** | 180€ | `https://placehold.co/600x800/CEDFD9/5F5449?text=T-shirt+Velours&font=playfair` | `T-shirt Velours — camiseta de terciopelo` |
| 4 | **Sacoche Sépia** | 260€ | `https://placehold.co/600x800/B09398/EBFCFB?text=Sacoche+S%C3%A9pia&font=playfair` | `Sacoche Sépia — riñonera de cuero` |
| 5 | **Manteau Brume** | 680€ | `https://placehold.co/600x800/9B6A6C/EBFCFB?text=Manteau+Brume&font=playfair` | `Manteau Brume — abrigo de invierno de lujo` |
| 6 | **Bottes Crépuscule** | 490€ | `https://placehold.co/600x800/5F5449/EBFCFB?text=Bottes+Cr%C3%A9puscule&font=playfair` | `Bottes Crépuscule — botas de cuero` |

#### Commit
```
feat: add Más Vendidos section with horizontal scroll and 6 products
```

#### Criterios de validación
- [ ] Sección "Más Vendidos" visible debajo de Novedades
- [ ] 6 cards con badge "Más vendido"
- [ ] Scroll horizontal funcional
- [ ] Schema `ItemList` en la sección

---

### Fase 5 — Footer + Cierre y Validación

**Objetivo:** Implementar el footer y validar la página completa.

#### Archivos involucrados
- **Editar**: `/workspaces/html-hello-ZZ/index.html`

#### Checklist de implementación

- [ ] `<footer role="contentinfo" class="bg-[#5F5449] text-[#EBFCFB] py-12 lg:py-16">`
- [ ] Grid: `max-w-7xl mx-auto px-4 lg:px-8 grid grid-cols-1 md:grid-cols-3 gap-8 lg:gap-12`
- [ ] **Columna 1 — Categorías:**
  - `<h2 class="text-[#CEDFD9] uppercase tracking-widest text-sm font-semibold">Categorías</h2>`
  - 4 enlaces: Calzado, Camisas, Pantalones, Accesorios
  - Cada uno: `href="catalogo.html"`, `text-[#B09398] hover:text-[#EBFCFB] transition-colors duration-200`
  - `aria-label` descriptivo en cada enlace
- [ ] **Columna 2 — Legal:**
  - `<h2>`: "Legal"
  - 3 enlaces: Términos y condiciones, Política de privacidad, Sobre MAISON NOIRE
  - Mismos estilos que columna 1
- [ ] **Columna 3 — Contacto:**
  - `<h2>`: "Contacto"
  - `<address class="not-italic text-[#B09398] space-y-2">`
  - Dirección: 48 Rue de l'Université, 75007 París, Francia
  - Email: contact@maisonnoire.fr
  - Iconos sociales: `<span aria-hidden="true">IG FB X</span>` con `text-[#B09398]`
- [ ] **Línea divisoria**: `<div class="border-t border-[#B09398]/30 max-w-7xl mx-auto mt-8">`
- [ ] **Copyright**: `<p class="text-center text-[#B09398] text-xs mt-4">© 2026 MAISON NOIRE — Todos los derechos reservados</p>`

#### Validación final (post-implementación)

- [ ] **Sin JavaScript**: revisar que no hay `<script>` tags (solo Tailwind CDN y Google Fonts, que son CSS)
- [ ] **Navegación por teclado**: Tab por toda la página, Enter en enlaces, focus visible en todos
- [ ] **Responsive**: reducir ventana a 375px (móvil), verificar scroll horizontal y layout
- [ ] **Contraste AA**: verificar todos los textos
- [ ] **Schema.org completo**: WebSite, Store, 2× ItemList, 12× Product, 12× Offer
- [ ] **Enlaces correctos**: Logo → `/`, CTA → `catalogo.html`, Cards → `producto.html`, Footer → `catalogo.html`
- [ ] **Alt text**: 12 imágenes con alt text descriptivo
- [ ] **ARIA**: roles, labels, hidden en iconos decorativos
- [ ] **Headings**: `h1` (Hero) → `h2` (Novedades, Más Vendidos, Categorías, Legal, Contacto) → `h3` (nombre producto)
- [ ] **Dropdown cuenta**: funcional con hover y focus-within

#### Commit
```
feat: add footer with categories, legal, contact and final accessibility validation
```

#### Post-implementación
1. Ejecutar `python3 server.py` y verificar en navegador
2. Actualizar `PROGRESS.md` con nueva entrada
3. Hacer push de rama `features/home`
4. Abrir PR de `features/home` → `main`

---

## 📊 Resumen de Commits

| Fase | Commit | Archivos |
|---|---|---|
| 1 | `feat: add HTML skeleton, navbar and SEO meta tags` | `index.html` (crear) |
| 2 | `feat: add hero section with gradient and CTA` | `index.html` (editar) |
| 3 | `feat: add Novedades section with horizontal scroll and 6 products` | `index.html` (editar) |
| 4 | `feat: add Más Vendidos section with horizontal scroll and 6 products` | `index.html` (editar) |
| 5 | `feat: add footer with categories, legal, contact and final accessibility validation` | `index.html` (editar) |

---

## 🧪 Post-Implementación Inmediata

```
1. python3 server.py           → Verificar que el servidor sirve la página
2. Abrir http://localhost:3000  → Prueba visual completa
3. Tab + Enter                  → Navegación por teclado
4. Reducir ventana              → Responsive test
5. git add index.html           → Staging
6. git commit -m "feat: ..."    → Commit por fase
7. git push origin features/home
8. PR features/home → main
9. Actualizar PROGRESS.md
```

---

> ⚠️ **Este plan está listo para ejecutarse. Cada fase debe implementarse secuencialmente.**  
> No saltar fases. Cada fase termina con un commit antes de empezar la siguiente.