# specs.md — Home (index.html)

> **Especificaciones de la página de inicio.**  
> Documento SDD que define qué construir, cómo y por qué.  
> Basado en `DESIGNS.md` (guía visual) y `CONTEXTO/que_hacer.md` (requisitos).

---

## 📋 Resumen

| Campo | Valor |
|---|---|
| **Funcionalidad** | Home — Página de inicio de la marca |
| **Archivo destino** | `index.html` (raíz del proyecto) |
| **Rama Git** | `features/home` |
| **Rama integración** | `main` |
| **Schema principal** | `Website` + `Store` |
| **Navegación** | Puerto de entrada a todas las demás vistas |

---

## 🎯 Objetivo

La página de inicio debe transmitir la identidad de **MAISON NOIRE** como marca francesa de streetwear de lujo: elegancia silenciosa, calidez monocromática, y una experiencia visual envolvente que invite a explorar el catálogo.

---

## 🧱 Estructura HTML (flujo semántico)

```
<body>
  ┌────────────────────────────────────────────┐
  │  Skip link (accesibilidad)                 │
  ├────────────────────────────────────────────┤
  │  <header>                                 │
  │    <nav>                                   │
  │      Logo | Búsqueda | Cuenta             │
  │    </nav>                                  │
  │  </header>                                 │
  ├────────────────────────────────────────────┤
  │  <main id="main-content">                  │
  │                                             │
  │    <section> Hero                          │
  │      Gradiente + Título + CTA             │
  │    </section>                              │
  │                                             │
  │    <section> Novedades                    │
  │      <h2> título                           │
  │      <div> scroll horizontal (6 cards)    │
  │    </section>                              │
  │                                             │
  │    <section> Más Vendidos             │
  │      <h2> título                           │
  │      <div> scroll horizontal (6 cards)    │
  │    </section>                              │
  │                                             │
  │  </main>                                   │
  ├────────────────────────────────────────────┤
  │  <footer>                                  │
  │    Categorías | Legal | Contacto           │
  │  </footer>                                 │
  └────────────────────────────────────────────┘
```

### Etiquetas semánticas obligatorias

| Etiqueta | Rol | Propósito |
|---|---|---|
| `<!DOCTYPE html>` | — | Declaración HTML5 |
| `<html lang="es">` | `document` | Idioma español |
| `<header role="banner">` | `banner` | Cabecera con navbar |
| `<nav role="navigation">` | `navigation` | Navegación principal |
| `<main id="main-content" role="main">` | `main` | Contenido único de la página |
| `<section>` | `region` | Cada bloque temático (hero, listados) |
| `<article>` | `article` | Cada card de producto (contenido autónomo) |
| `<footer role="contentinfo">` | `contentinfo` | Pie de página |
| `<h1>` a `<h3>` | `heading` | Jerarquía de títulos sin saltos |

---

## 🎨 Paleta de Colores (Aplicación)

| Componente | Color | Hex |
|---|---|---|
| Fondo general de página | Blanc Glacé | `#EBFCFB` |
| Navbar fondo | Taupe Noir | `#5F5449` |
| Navbar texto/links | Blanc Glacé | `#EBFCFB` |
| Hero fondo (gradiente) | Taupe Noir → Rose Poudré | `#5F5449` → `#9B6A6C` |
| Hero texto | Blanc Glacé | `#EBFCFB` |
| Botón CTA fondo | Rose Poudré | `#9B6A6C` |
| Botón CTA hover | Taupe Noir | `#5F5449` |
| Botón CTA texto | Blanc Glacé | `#EBFCFB` |
| Secciones título | Taupe Noir | `#5F5449` |
| Card borde | Mauve Doux | `#B09398` al 30% |
| Card hover fondo | Sage Pâle → Blanc Glacé | gradiente sutil |
| Card precio | Rose Poudré | `#9B6A6C` |
| Badge "Nuevo"/"Más vendido" | Sage Pâle fondo / Taupe Noir texto | `#CEDFD9` / `#5F5449` |
| Footer fondo | Taupe Noir | `#5F5449` |
| Footer títulos | Sage Pâle | `#CEDFD9` |
| Footer enlaces | Mauve Doux | `#B09398` |
| Footer enlaces hover | Blanc Glacé | `#EBFCFB` |
| Divisores/Separadores | Mauve Doux | `#B09398` al 30% |

---

## 🔤 Tipografía

| Uso | Fuente | Peso | Tracking | Tamaño |
|---|---|---|---|---|
| Logo navbar | Playfair Display | 600 italic | `tracking-widest` | `text-xl lg:text-2xl` |
| Título Hero (h1) | Playfair Display | 700 | `tracking-[0.1em]` | `text-5xl lg:text-7xl` |
| Subtítulo Hero | Inter | 400 | normal | `text-lg lg:text-xl` |
| Títulos sección (h2) | Playfair Display | 600 | `tracking-widest` | `text-2xl lg:text-3xl` |
| Nombre producto | Playfair Display | 500 | normal | `text-sm lg:text-base` |
| Precio producto | Inter | 600 | normal | `text-base lg:text-lg` |
| Navbar enlaces | Inter | 400 | normal | `text-sm` |
| Cuerpo/descripciones | Inter | 300 | normal | `text-sm` |
| Footer títulos | Inter | 500 | `tracking-widest uppercase` | `text-sm` |
| Footer enlaces | Inter | 300 | normal | `text-sm` |

---

## 🧩 Componentes (Especificación)

### 1. Skip Link

```
Posición: Primer elemento del <body>
Texto: "Ir al contenido principal"
Destino: #main-content
Estilo: Posicionado absolutamente, visible solo en focus
ARIA: aria-label="Ir al contenido principal"
Clases Tailwind: sr-only focus:not-sr-only focus:absolute focus:px-4 focus:py-2
```

### 2. Navbar

```
Estructura:
  <header role="banner" class="bg-[#5F5449] text-[#EBFCFB]">
    <div class="flex justify-between items-center max-w-7xl mx-auto px-4 lg:px-8 h-16 lg:h-20">
      <!-- Logo -->
      <a href="/">MAISON NOIRE</a>

      <!-- Búsqueda -->
      <div role="search">
        <label class="sr-only" for="search-home">Buscar...</label>
        <input id="search-home" type="search"
               placeholder="Buscar..."
               class="border border-[#B09398]/30 bg-[#5F5449]"
               aria-label="Buscar un producto" />
      </div>

      <!-- Cuenta (CSS-only dropdown) -->
      <div class="group">
        <button aria-label="Mi cuenta">Cuenta</button>
        <!-- dropdown con :hover / :focus-within -->
        <ul class="invisible group-hover:visible group-focus-within:visible">
          <li><a href="#">Mi perfil</a></li>
          <li><a href="#">Mis pedidos</a></li>
          <li><a href="#">Cerrar sesión</a></li>
        </ul>
      </div>
    </div>
  </header>
```

**Estados:**
- Normal: fondo `#5F5449`, texto `#EBFCFB`
- Hover links: `text-[#B09398] hover:text-[#EBFCFB]`
- Focus input: `ring-2 ring-[#9B6A6C] border-[#9B6A6C]`
- Dropdown cuenta: visible con `group-hover` (CSS-only)

**Accesibilidad:**
- `aria-label="Navegación principal"`
- `aria-current="page"` en el link activo
- Input search con `role="search"` y `aria-label`

### 3. Hero Section

```
<section class="bg-gradient-to-r from-[#5F5449] to-[#9B6A6C] text-[#EBFCFB] py-20 lg:py-32">
  <div class="max-w-7xl mx-auto px-4 lg:px-8">
    <h1 class="font-['Playfair_Display'] font-bold text-5xl lg:text-7xl
               tracking-[0.1em] leading-tight">
      La Elegancia<br>de la Sombra
    </h1>
    <p class="font-['Inter'] text-lg lg:text-xl leading-relaxed">
      La nueva colección otoño-invierno — donde el silencio encuentra el estilo.
    </p>
    <a href="catalogo.html"
       class="bg-[#9B6A6C] hover:bg-[#5F5449] text-[#EBFCFB]
              transition-all duration-300 px-8 py-3 lg:px-10 lg:py-4
              inline-block font-['Inter'] font-semibold tracking-widest uppercase
              ring-2 ring-[#9B6A6C] ring-offset-2 focus:ring-[#EBFCFB]"
       aria-label="Descubrir la colección otoño-invierno">
      Descubrir →
    </a>
  </div>
</section>
```

**Textos (Español):**
- Título h1: `La Elegancia de la Sombra`
- Subtítulo: `La nueva colección otoño-invierno — donde el silencio encuentra el estilo.`
- CTA: `Descubrir →`

### 4. Product Card

Cada card de producto sigue esta estructura:

```
<article class="bg-white border border-[#B09398]/30 rounded-sm
                transition-all duration-300 hover:shadow-md hover:-translate-y-1"
         itemscope itemtype="https://schema.org/Product">

  <a href="producto.html" class="block aspect-[3/4]">
    <img src="..." alt="..." class="object-cover w-full h-full"
         itemprop="image" />
  </a>

  <div class="p-4 lg:p-6">
    <h3 class="font-['Playfair_Display'] text-sm lg:text-base text-[#5F5449]"
        itemprop="name">Blouson Nocturne</h3>

    <p class="font-['Inter'] font-semibold text-[#9B6A6C] text-base lg:text-lg"
       itemprop="offers" itemscope itemtype="https://schema.org/Offer">
      <span itemprop="price" content="490">490</span>
      <span itemprop="priceCurrency" content="EUR">€</span>
    </p>

    <a href="producto.html"
       class="text-[#9B6A6C] hover:text-[#5F5449] text-xs uppercase tracking-widest
              transition-colors duration-200"
       aria-label="Ver producto Blouson Nocturne">
      Ver producto →
    </a>
  </div>
</article>
```

**Tags opcionales (badge):**
- `Nuevo` — `bg-[#CEDFD9] text-[#5F5449] text-xs px-2 py-1 uppercase tracking-widest`
- `Más vendido` — mismo estilo
- Posición: esquina superior izquierda de la imagen

### 5. Listado Horizontal (Scroll)

```
<section class="py-12 lg:py-16">
  <div class="max-w-7xl mx-auto px-4 lg:px-8">
    <h2 class="font-['Playfair_Display'] font-semibold text-2xl lg:text-3xl
               text-[#5F5449] tracking-widest">Novedades</h2>
  </div>

  <!-- Scroll horizontal con snap -->
  <div class="flex gap-4 lg:gap-6 overflow-x-auto snap-x snap-mandatory
              px-4 lg:px-8 pb-4 scroll-px-4"
       role="list" aria-label="Novedades">
    <!-- 6 product cards aquí -->
  </div>
</section>
```

**Consideraciones:**
- `snap-x snap-mandatory` para scroll con snapping (CSS nativo)
- `role="list"` y `aria-label` para accesibilidad
- Los ítems individuales llevan `role="listitem"`
- En móvil el scroll es táctil; en desktop con rueda del ratón

### 6. Footer

```
<footer role="contentinfo" class="bg-[#5F5449] text-[#EBFCFB] py-12 lg:py-16">
  <div class="max-w-7xl mx-auto px-4 lg:px-8 grid grid-cols-1 md:grid-cols-3 gap-8 lg:gap-12">

    <!-- Columna 1: Categorías -->
    <div>
      <h2 class="text-[#CEDFD9] uppercase tracking-widest text-sm font-semibold">Categorías</h2>
      <ul class="space-y-2">
        <li><a href="catalogo.html" class="text-[#B09398] hover:text-[#EBFCFB] transition-colors duration-200"
               aria-label="Ver calzado">Calzado</a></li>
        <li><a href="catalogo.html" class="text-[#B09398] hover:text-[#EBFCFB] transition-colors duration-200"
               aria-label="Ver camisas">Camisas</a></li>
        <li><a href="catalogo.html" class="text-[#B09398] hover:text-[#EBFCFB] transition-colors duration-200"
               aria-label="Ver pantalones">Pantalones</a></li>
        <li><a href="catalogo.html" class="text-[#B09398] hover:text-[#EBFCFB] transition-colors duration-200"
               aria-label="Ver accesorios">Accesorios</a></li>
      </ul>
    </div>

    <!-- Columna 2: Legal -->
    <div>
      <h2 class="text-[#CEDFD9] uppercase tracking-widest text-sm font-semibold">Legal</h2>
      <ul class="space-y-2">
        <li><a href="#" class="text-[#B09398] hover:text-[#EBFCFB] transition-colors duration-200">Términos y condiciones</a></li>
        <li><a href="#" class="text-[#B09398] hover:text-[#EBFCFB] transition-colors duration-200">Política de privacidad</a></li>
        <li><a href="#" class="text-[#B09398] hover:text-[#EBFCFB] transition-colors duration-200">Sobre MAISON NOIRE</a></li>
      </ul>
    </div>

    <!-- Columna 3: Contacto -->
    <div>
      <h2 class="text-[#CEDFD9] uppercase tracking-widest text-sm font-semibold">Contacto</h2>
      <address class="text-[#B09398] not-italic space-y-2">
        <p>48 Rue de l'Université</p>
        <p>75007 París, Francia</p>
        <p>contact@maisonnoire.fr</p>
      </address>
      <!-- Iconos sociales (CSS-only, letras como iconos) -->
      <div class="flex gap-3 mt-4">
        <span aria-hidden="true" class="text-[#B09398]">IG</span>
        <span aria-hidden="true" class="text-[#B09398]">FB</span>
        <span aria-hidden="true" class="text-[#B09398]">X</span>
      </div>
    </div>

  </div>

  <!-- Línea divisoria + copyright -->
  <div class="border-t border-[#B09398]/30 max-w-7xl mx-auto mt-8"></div>
  <p class="text-center text-[#B09398] text-xs mt-4 max-w-7xl mx-auto">
    © 2026 MAISON NOIRE — Todos los derechos reservados
  </p>
</footer>
```

---

## 🛍️ Productos de Ejemplo

### Novedades (6 productos)

| # | Producto | Categoría | Precio | Tag | Placeholder |
|---|---|---|---|---|---|
| 1 | **Blouson Nocturne** | Chaquetas | 490€ | Nuevo | `https://placehold.co/600x800/5F5449/EBFCFB?text=Blouson+Nocturne&font=playfair` |
| 2 | **Sneakers Minuit** | Calzado | 450€ | Nuevo | `https://placehold.co/600x800/5F5449/EBFCFB?text=Sneakers+Minuit&font=playfair` |
| 3 | **Veste Ébène** | Chaquetas | 520€ | Nuevo | `https://placehold.co/600x800/5F5449/EBFCFB?text=Veste+%C3%89b%C3%A8ne&font=playfair` |
| 4 | **Écharpe Cendré** | Accesorios | 180€ | Nuevo | `https://placehold.co/600x800/9B6A6C/EBFCFB?text=%C3%89charpe+Cendr%C3%A9&font=playfair` |
| 5 | **Sac Nocturne** | Accesorios | 350€ | Nuevo | `https://placehold.co/600x800/B09398/5F5449?text=Sac+Nocturne&font=playfair` |
| 6 | **Blazer Brume** | Chaquetas | 620€ | Nuevo | `https://placehold.co/600x800/5F5449/EBFCFB?text=Blazer+Brume&font=playfair` |

### Más Vendidos (6 productos)

| # | Producto | Categoría | Precio | Tag | Placeholder |
|---|---|---|---|---|---|
| 1 | **Chemise Ombre** | Camisas | 280€ | Más vendido | `https://placehold.co/600x800/9B6A6C/EBFCFB?text=Chemise+Ombre&font=playfair` |
| 2 | **Pantalon Cendré** | Pantalones | 320€ | Más vendido | `https://placehold.co/600x800/B09398/5F5449?text=Pantalon+Cendr%C3%A9&font=playfair` |
| 3 | **T-shirt Velours** | Camisas | 180€ | Más vendido | `https://placehold.co/600x800/CEDFD9/5F5449?text=T-shirt+Velours&font=playfair` |
| 4 | **Sacoche Sépia** | Accesorios | 260€ | Más vendido | `https://placehold.co/600x800/B09398/EBFCFB?text=Sacoche+S%C3%A9pia&font=playfair` |
| 5 | **Manteau Brume** | Chaquetas | 680€ | Más vendido | `https://placehold.co/600x800/9B6A6C/EBFCFB?text=Manteau+Brume&font=playfair` |
| 6 | **Bottes Crépuscule** | Calzado | 490€ | Más vendido | `https://placehold.co/600x800/5F5449/EBFCFB?text=Bottes+Cr%C3%A9puscule&font=playfair` |

---

## 🔍 Schema.org

| Tipo | Ámbito | Ubicación |
|---|---|---|
| `Website` | Toda la página | `<body itemscope itemtype="https://schema.org/WebSite">` |
| `Store` | Marca | `<header itemscope itemtype="https://schema.org/Store">` |
| `Product` | Cada card | `<article itemscope itemtype="https://schema.org/Product">` |
| `Offer` | Precio | `<span itemprop="offers" itemscope itemtype="https://schema.org/Offer">` |
| `ItemList` | Listados | `<section itemscope itemtype="https://schema.org/ItemList">` |

**Propiedades a incluir:**
- `url` — `https://maisonnoire.fr/`
- `name` — `MAISON NOIRE`
- `description` — `Marca francesa de streetwear de lujo`
- `image` — logo de la marca (placeholder)

---

## ♿ Accesibilidad (Checklist)

- [ ] Skip link como primer elemento del `<body>`
- [ ] Roles ARIA en header (`banner`), nav (`navigation`), main (`main`), footer (`contentinfo`), hero (`region`), cards (`article`)
- [ ] `aria-label` descriptivo en: nav, search, CTA, cada enlace de producto, cada categoría del footer
- [ ] `aria-hidden="true"` en iconos decorativos (social media)
- [ ] `aria-current="page"` en navbar si aplica
- [ ] `aria-live="polite"` en regiones dinámicas (no hay, solo CSS)
- [ ] Labels asociados a inputs (`<label for="...">`)
- [ ] Headings jerárquicos: `h1` (Hero) → `h2` (Novedades, Más Vendidos) → `h3` (nombre producto)
- [ ] Alt text descriptivo en todas las imágenes
- [ ] Focus visible con `ring-2 ring-[#9B6A6C] ring-offset-2`
- [ ] Contraste AA verificado (documentado en `DESIGNS.md`)
- [ ] Navegación por teclado completa (tabindex, focus-within para dropdowns)
- [ ] Tamaño mínimo táctil 44×44px en móvil

---

## ✨ Transiciones y Animaciones

| Elemento | Transición |
|---|---|
| Botón CTA Hero | `transition-all duration-300 ease-in-out` |
| Cards producto (hover) | `transition-all duration-300 hover:shadow-md hover:-translate-y-1` |
| Navbar links | `transition-colors duration-200` |
| Footer links | `transition-colors duration-200` |
| Input búsqueda (focus) | `transition-all duration-200` |

---

## 🔗 Navegación (desde Home)

| Elemento | Destino | ARIA |
|---|---|---|
| Logo | `/` (home) | `aria-label="Ir al inicio"` |
| CTA Hero | `catalogo.html` | `aria-label="Descubrir la colección"` |
| Cards producto | `producto.html` | `aria-label="Ver producto [nombre]"` |
| Footer Categorías | `catalogo.html` | `aria-label="Ver [categoría]"` |

---

## 📱 Responsive Design

| Breakpoint | Cambios |
|---|---|
| `< 640px` (sm) | Navbar colapsado, cards 1 columna, hero texto más pequeño |
| `≥ 640px` (sm) | Navbar expandido, cards en fila, hero completo |
| `≥ 768px` (md) | Footer 3 columnas |
| `≥ 1024px` (lg) | Hero tamaño completo, espaciados mayores |
| `≥ 1280px` (xl) | Contenedor max-w-7xl centrado |

---

## 🧪 Criterios de Aceptación

La Home estará completa cuando:

- [ ] La página carga sin errores en Flask (`python3 server.py`)
- [ ] Todos los colores pertenecen a la paleta definida en `DESIGNS.md`
- [ ] Las fuentes se cargan correctamente (Playfair Display + Inter)
- [ ] El skip link funciona y solo es visible al navegar con teclado
- [ ] El navbar es funcional: logo linkeable, búsqueda con placeholder, dropdown cuenta con hover
- [ ] El Hero tiene gradiente correcto y CTA con hover
- [ ] "Novedades" muestra 6 productos en scroll horizontal con snap
- [ ] "Más Vendidos" muestra 6 productos en scroll horizontal con snap
- [ ] Cada card tiene imagen, nombre, precio, y tag si corresponde
- [ ] El footer tiene 3 columnas con enlaces funcionales
- [ ] Todas las imágenes tienen alt text descriptivo
- [ ] Schema.org implementado en cada nivel
- [ ] Sin errores de contraste (AA)
- [ ] Sin JavaScript en el código
- [ ] Los enlaces entre páginas apuntan a los destinos correctos

---

> ⚠️ **Este documento es la especificación.** La implementación comenzará cuando se apruebe.  
> Cualquier cambio en estos requisitos debe reflejarse aquí antes de codificar.