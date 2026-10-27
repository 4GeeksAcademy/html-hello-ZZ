# DESIGNS.md — Guía Visual de MAISON NOIRE

> **Guía de estilo y diseño del proyecto.** Todo el desarrollo visual debe respetar este documento para mantener coherencia y equilibrio entre las páginas.

---

## 🎨 Filosofía Visual

MAISON NOIRE se inspira en la **elegancia parisina silenciosa** combinada con la **actitud del streetwear contemporáneo**. La paleta es sofisticada, contenida y cálida — evita los contrastes agresivos y busca una atmósfera envolvente, íntima y lujosa.

```
"Lujo silencioso. Calidez monocromática. Elegancia táctil."
```

---

## 🟤 Paleta de Colores

### Colores de Marca

| Muestra | Nombre | Hex | RGB | Uso |
|---|---|---|---|---|
| ████ | **Taupe Noir** (primario) | `#5F5449` | `rgb(95, 84, 73)` | Fondos oscuros, headers, footers, textos principales |
| ████ | **Rose Poudré** (secundario) | `#9B6A6C` | `rgb(155, 106, 108)` | Botones primarios, acentos, hover states, precio |
| ████ | **Mauve Doux** (terciario) | `#B09398` | `rgb(176, 147, 152)` | Bordes, separadores, fondos de cards, hover suave |
| ████ | **Sage Pâle** (fondo claro) | `#CEDFD9` | `rgb(206, 223, 217)` | Fondos alternos, badges, tags, secciones destacadas |
| ████ | **Blanc Glacé** (fondo base) | `#EBFCFB` | `rgb(235, 252, 251)` | Fondo principal de página, contraste limpio |

### Jerarquía de Aplicación

```
Fondo general     → #EBFCFB (Blanc Glacé)
Fondos oscuros    → #5F5449 (Taupe Noir) 
Fondos alternos   → #CEDFD9 (Sage Pâle)
Textos principales → #5F5449 (Taupe Noir)
Textos claros     → #EBFCFB (Blanc Glacé) [sobre fondos oscuros]
Acentos llamada   → #9B6A6C (Rose Poudré)
Acentos suaves    → #B09398 (Mauve Doux)
```

### Modo Claro (único modo)

Este prototipo usa **un único modo visual** con fondos claros (#EBFCFB) y acentos en la gama taupe-rose. No hay modo oscuro — la calidez de la paleta reemplaza la necesidad de contraste agresivo.

### Gradientes Sugeridos

- **Hero gradient**: `from-[#5F5449] to-[#9B6A6C]`
- **Card hover**: `from-[#CEDFD9] to-[#EBFCFB]`
- **Botón primario**: `bg-[#9B6A6C] hover:bg-[#5F5449]`

---

## 🔤 Tipografía

### Propuesta Tipográfica

| Rol | Fuente | Peso | Tamaños |
|---|---|---|---|
| **Títulos (h1-h3)** | `"Playfair Display", Georgia, serif` | 600-700 | `text-4xl` a `text-6xl` |
| **Subtítulos (h3-h4)** | `"Playfair Display", Georgia, serif` | 500-600 | `text-2xl` a `text-3xl` |
| **Cuerpo / Nav** | `"Inter", -apple-system, sans-serif` | 300-400 | `text-sm` a `text-base` |
| **Precios / Acentos** | `"Inter", sans-serif` | 500-600 | `text-lg` a `text-xl` |
| **Mono / Código** | No aplica en este proyecto | — | — |

### Reglas Tipográficas

- **Tracking (letter-spacing)**: Títulos en mayúsculas usan `tracking-widest` o `tracking-[0.15em]`
- **Altura de línea**: `leading-relaxed` en cuerpo, `leading-tight` en títulos
- **Mayúsculas**: Usar en navbar, títulos de sección, etiquetas de producto (`uppercase tracking-widest`)
- **Minúsculas elegantes**: Body text en sentence case, no gritar

### Importación (CDN)

```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600&family=Playfair+Display:ital,wght@0,500;0,600;0,700;1,400&display=swap" rel="stylesheet">
```

---

## 📐 Layout y Espaciado

### Sistema de Rejilla

- **Contenedor máximo**: `max-w-7xl mx-auto` (1280px)
- **Padding lateral**: `px-4 sm:px-6 lg:px-8`
- **Grid productos (catálogo)**: `grid grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-4 lg:gap-6`
- **Grid cards (home)**: `flex gap-6 overflow-x-auto snap-x snap-mandatory`

### Jerarquía de Espaciado

| Uso | Clase Tailwind |
|---|---|
| Entre secciones grandes | `py-16 lg:py-24` |
| Entre secciones normales | `py-12 lg:py-16` |
| Entre componentes | `py-8 lg:py-12` |
| Padding interno card | `p-4 lg:p-6` |
| Gap entre elementos | `gap-4 lg:gap-6` |

### Breakpoints

| Alias | Ancho | Objetivo |
|---|---|---|
| `sm` | 640px | Móvil grande |
| `md` | 768px | Tablet |
| `lg` | 1024px | Desktop |
| `xl` | 1280px | Desktop grande |

---

## 🧩 Componentes Visuales

### Navbar
- Fondo: `bg-[#5F5449]` (Taupe Noir)
- Texto: `text-[#EBFCFB]`
- Logo: `font-["Playfair_Display"] italic text-xl lg:text-2xl tracking-widest`
- Altura: `h-16 lg:h-20`
- Búsqueda: input con borde sutil, placeholder claro
- Menú cuenta: icono + dropdown visual (CSS-only)

### Hero
- Fondo con gradiente o imagen de campaña
- Overlay semitransparente si usa imagen
- Título grande en Playfair Display
- Botón CTA: `bg-[#9B6A6C] text-[#EBFCFB] hover:bg-[#5F5449]`
- Transición suave en hover

### Product Card
- Fondo: `bg-white` con borde `border-[#B09398]/30`
- Hover: sombra sutil y elevación (`shadow-md hover:shadow-lg`)
- Imagen: `aspect-[3/4] object-cover`
- Nombre: Playfair Display, tamaño `text-sm lg:text-base`
- Precio: `text-[#9B6A6C] font-semibold`
- Tag "Nuevo" / "Más vendido": `bg-[#CEDFD9] text-[#5F5449] text-xs px-2 py-1`

### Botones

| Tipo | Fondo | Texto | Hover |
|---|---|---|---|
| Primario | `#9B6A6C` | `#EBFCFB` | `#5F5449` |
| Secundario | Transparente | `#5F5449` | `#CEDFD9` |
| Outline | Transparente | `#5F5449` | `#5F5449` con borde `#B09398` |
| Tag/Badge | `#CEDFD9` | `#5F5449` | — |

### Formularios
- Inputs: `border border-[#B09398]/50` → focus: `border-[#9B6A6C] ring-1 ring-[#9B6A6C]`
- Labels: `text-[#5F5449] text-sm font-medium`
- Placeholder: `text-[#B09398]`
- Checkbox/Radio: acento `#9B6A6C`
- Estados de error: `border-red-400` con mensaje en rojo

### Footer
- Fondo: `bg-[#5F5449]`
- Texto títulos: `text-[#CEDFD9] uppercase tracking-widest text-sm`
- Texto enlaces: `text-[#B09398] hover:text-[#EBFCFB]`
- Divisores: `border-[#B09398]/30`
- Iconos redes sociales: tono `#B09398`

### Separadores y Líneas
- Color: `#B09398` con opacidad 30-50%
- Grosor: `border` (1px) o `border-t` según contexto

---

## 📸 Imágenes y Medios

- **Formato de placeholder**: Usar imágenes de `https://placehold.co/` con colores de la paleta
- **Proporciones**:
  - Hero: `aspect-[16/7]` o `aspect-[21/9]`
  - Card producto: `aspect-[3/4]`
  - Carrito miniatura: `aspect-square w-20 lg:w-24`
- **Estilo**: Imágenes en escala de grises o tono sepia para mantener cohesión con la paleta
- **Alt text**: Siempre descriptivo para accesibilidad

---

## ✨ Animaciones y Transiciones

Solo CSS (sin JavaScript):

| Elemento | Transición |
|---|---|
| Botones | `transition-all duration-300 ease-in-out` |
| Cards (hover) | `transition-transform duration-300 hover:-translate-y-1` |
| Navbar links | `transition-colors duration-200` |
| Filtros activos | `transition-all duration-200` |
| Checkout pasos | `transition-opacity duration-400` (radio buttons) |

---

## ♿ Accesibilidad Visual

- **Contraste**: La paleta cumple ratio AA:
  - `#5F5449` sobre `#EBFCFB` → ratio ~8.5:1 ✅
  - `#9B6A6C` sobre `#EBFCFB` → ratio ~3.5:1 (usar solo para elementos grandes o decorativos)
  - `#EBFCFB` sobre `#5F5449` → ratio ~8.5:1 ✅
  - `#EBFCFB` sobre `#9B6A6C` → ratio ~3.5:1 (solo para texto grande >18px bold o >24px)
- **Focus visible**: Outline con `ring-2 ring-[#9B6A6C] ring-offset-2` en todos los elementos interactivos
- **Tamaño mínimo táctil**: 44×44px para targets en móvil

---

## 🧪 Consistencia y Checklist

Antes de dar por terminada cualquier página, verificar:

- [ ] ¿Los colores usados pertenecen exclusivamente a la paleta?
- [ ] ¿Tipografía Playfair Display solo en títulos y acentos?
- [ ] ¿Tipografía Inter en cuerpo, navbar y footer?
- [ ] ¿Navbar y footer son visualmente idénticos al de otras páginas?
- [ ] ¿Los botones siguen el sistema de estados (normal, hover, focus)?
- [ ] ¿Los formularios usan el borde y focus definido?
- [ ] ¿Las imágenes tienen la proporción correcta?
- [ ] ¿Los espaciados entre secciones siguen la jerarquía definida?
- [ ] ¿Las transiciones y hovers son consistentes?
- [ ] ¿El contraste de color cumple AA?
- [ ] ¿Los componentes interactivos tienen focus visible?

---

## 📚 Referencia Rápida para Tailwind v4

Dado que Tailwind v4 no incluye colores personalizados por defecto en `tailwind.config.js`, usamos **valores arbitrarios**:

```html
<!-- Fondo -->
<div class="bg-[#5F5449]">...</div>

<!-- Texto -->
<p class="text-[#9B6A6C]">Precio</p>

<!-- Bordes -->
<div class="border border-[#B09398]/30">...</div>

<!-- Hover -->
<button class="bg-[#9B6A6C] hover:bg-[#5F5449] text-[#EBFCFB]">Comprar</button>

<!-- Gradiente -->
<section class="bg-gradient-to-r from-[#5F5449] to-[#9B6A6C]">...</section>

<!-- Ring focus -->
<input class="focus:ring-2 focus:ring-[#9B6A6C] focus:border-[#9B6A6C]" />

<!-- Placeholder -->
<input class="placeholder:text-[#B09398]" />
```

---

> ⚠️ **Este archivo es la única fuente de verdad para decisiones visuales.**
> Cualquier desviación debe ser consultada antes de implementarse.