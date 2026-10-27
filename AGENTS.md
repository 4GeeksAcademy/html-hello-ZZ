# AGENTS.md — MAISON NOIRE

> **Léeme al inicio de cada sesión.** Contengo el contexto, las reglas y la arquitectura del proyecto.

> 📐 **Para decisiones visuales, consulta siempre [`DESIGNS.md`](./DESIGNS.md)** — es la única fuente de verdad sobre colores, tipografía, componentes y estilo.

---

## 🧾 Descripción del Proyecto

**MAISON NOIRE** es una marca francesa ficticia de *streetwear de lujo*.  
Estamos construyendo un **prototipo de e-commerce** en HTML + Tailwind (sin JavaScript, sin frameworks) para que los clientes de la marca puedan hacerse una idea visual de cómo funcionará el sitio.

| Dato | Valor |
|---|---|
| **Marca** | MAISON NOIRE (francés — "Casa Negra") |
| **Estilo** | Streetwear de lujo |
| **Origen** | Francia 🇫🇷 |
| **Propósito** | Prototipo visual no funcional |
| **Stack** | HTML semántico + Tailwind CSS v4 CDN |
| **Sin** | JavaScript, frameworks, librerías externas |

---

## 🏛️ Arquitectura del Proyecto

### Estructura de archivos

```
/
├── AGENTS.md            ← Este archivo. Léeme al inicio.
├── DESIGNS.md           ← Guía visual. Fuente de verdad para diseño.
├── PROGRESS.md          ← Registro de cambios. Actualizar al completar cada implementación.├── features/            ← Carpetas SDD — una por funcionalidad
│   ├── home/            ← Documentación y assets de la vista Home
│   ├── catalogo/        ← Documentación y assets de la vista Catálogo
│   ├── producto/        ← Documentación y assets de la vista Producto
│   ├── carrito/         ← Documentación y assets de la vista Carrito
│   └── checkout/        ← Documentación y assets de la vista Checkout├── index.html           → Home (navbar, hero, listados, footer)
├── catalogo.html        → Catálogo (filtros + grid 4×5)
├── producto.html        → Vista de producto (2 columnas + descripción)
├── carrito.html         → Carrito (3 productos + resumen)
├── checkout.html        → Checkout (3 pasos con radio buttons)
├── estilos.css          → (opcional) Estilos adicionales a Tailwind
├── assets/
│   └── images/          → Imágenes placeholder de productos
├── server.py            → Servidor Flask para desarrollo local
├── learn.json           → Metadata del proyecto 4Geeks
├── README.md            → Documentación
├── README.es.md         → Documentación en español
├── README.cn.md         → Documentación en chino
└── CONTEXTO/
    ├── CONTEXT.md       → Contexto general del proyecto
    └── que_hacer.md     → Lista detallada de requerimientos
```

### 📐 SDD — Style-Driven Development

Trabajamos por **ramas separadas**, una por cada vista:

| Rama | Archivo | Vista |
|---|---|---|
| `feature/home` | `index.html` | Home |
| `feature/catalogo` | `catalogo.html` | Catálogo |
| `feature/producto` | `producto.html` | Producto |
| `feature/carrito` | `carrito.html` | Carrito |
| `feature/checkout` | `checkout.html` | Checkout |

**Navbar y footer se reutilizan** en todas las páginas con la misma estructura semántica.

### Paleta de la Marca

> **Ver [`DESIGNS.md`](./DESIGNS.md) para la guía visual completa con usos, gradientes, modos y ejemplos.**

| Muestra | Nombre | Hex | Uso |
|---|---|---|---|
| ████ | **Taupe Noir** (primario) | `#5F5449` | Fondos oscuros, headers, footers, textos principales |
| ████ | **Rose Poudré** (secundario) | `#9B6A6C` | Botones primarios, acentos, hover, precio |
| ████ | **Mauve Doux** (terciario) | `#B09398` | Bordes, separadores, fondos de cards, hover suave |
| ████ | **Sage Pâle** (fondo claro) | `#CEDFD9` | Fondos alternos, badges, tags, secciones destacadas |
| ████ | **Blanc Glacé** (fondo base) | `#EBFCFB` | Fondo principal de página, contraste limpio |

---

## ⚙️ Reglas Técnicas Absolutas

1. **HTML semántico obligatorio** — Usar `<header>`, `<main>`, `<nav>`, `<section>`, `<article>`, `<footer>`, etc. Nada de `<div>` cuando exista una etiqueta semántica.
2. **Tailwind CSS v4** — Cargar desde CDN en el `<head>`:
   ```html
   <script src="https://cdn.jsdelivr.net/npm/@tailwindcss/browser@4"></script>
   ```
3. **Cero JavaScript** — Nada de `<script>`. Nada de JS. Solo CSS.
4. **Sin frameworks** — No React, Vue, Angular, Alpine, etc.
5. **Sin librerías externas** — Tailwind es la única dependencia.

---

## ♿ Accesibilidad (Pilar Fundamental)

Toda marca de lujo debe ser inclusiva. La accesibilidad no es opcional:

- [ ] Usar roles ARIA donde la semántica HTML5 no sea suficiente (`role="navigation"`, `role="banner"`, `role="contentinfo"`)
- [ ] `aria-label` descriptivo en todos los elementos interactivos (enlaces, botones, inputs, iconos)
- [ ] `aria-hidden="true"` en iconos decorativos
- [ ] Contraste de color mínimo AA (4.5:1 texto normal, 3:1 texto grande) — nuestra paleta negra/blanca/dorada lo cumple
- [ ] Navegación por teclado completa: `tabindex="0"` donde sea necesario, `:focus-visible` siempre visible
- [ ] `alt` texts descriptivos en todas las imágenes
- [ ] Etiquetas `<label>` asociadas a todos los `<input>`
- [ ] Skip link al inicio (`<a href="#main-content">Saltar al contenido</a>`)
- [ ] Estructura de headings jerárquica (`<h1>` → `<h2>` → `<h3>`) sin saltos

---

## 🔍 Schema.org para SEO

Cada página debe incluir los siguientes tipos de schema:

| Página | Schema Principal |
|---|---|
| Home | `Website`, `Store` |
| Catálogo | `ItemList`, `CollectionPage` |
| Producto | `Product`, `Offer` |
| Carrito | `ShoppingCart` |
| Checkout | `CheckoutPage` |

Usar atributos `itemscope` e `itemtype` en el HTML.

---

## 🌐 Navegación y Flujo entre Páginas

Todas las páginas se enlazan entre sí:

```
Home (index.html)
  ├── Catálogo (catalogo.html)
  │     └── Producto (producto.html)
  ├── Producto (producto.html)
  └── Carrito (carrito.html)
        └── Checkout (checkout.html)
```

---

## 🗂️ Git Workflow

- Trabajar siempre en **ramas separadas** (`feature/xxx`)
- **Nunca hacer push directo a `main`**
- Commits frecuentes con mensajes claros en español o inglés
- Antes de abrir PR, hacer `git pull origin main` para actualizar
- Abrir Pull Request por cada rama antes de integrar a `main`
- Resolver conflictos en equipo, sin force-push

---

## 📋 Checklists por Vista

### Home (`index.html`)
- [ ] Navbar: logo, búsqueda, menú cuenta
- [ ] Hero section con campaña destacada
- [ ] "Nuevos lanzamientos" — cards en scroll horizontal
- [ ] "Más vendidos" — cards en scroll horizontal
- [ ] Footer: categorías (calzado, camisas, pantalones, accesorios), legal, contacto

### Catálogo (`catalogo.html`)
- [ ] Navbar y footer idénticos al home
- [ ] Barra de filtros: categoría + talla
- [ ] Grid 4×5 (20 productos como referencia)
- [ ] Cada producto enlaza a `producto.html`

### Producto (`producto.html`)
- [ ] Navbar y footer
- [ ] 2 columnas: izquierda imagen, derecha info
- [ ] Info: nombre, referencia, talla, precio, selector cantidad, botón "Agregar al carrito"
- [ ] Sección descripción: materiales, uso recomendado

### Carrito (`carrito.html`)
- [ ] Navbar y footer
- [ ] 3 productos de ejemplo con miniatura, precio unitario, cantidad, total
- [ ] Resumen: subtotal, impuestos, total
- [ ] Botón "Comprar" → enlaza a `checkout.html`

### Checkout (`checkout.html`)
- [ ] Navbar y footer
- [ ] Paso 1: Datos personales
- [ ] Paso 2: Dirección de entrega
- [ ] Paso 3: Pago con tarjeta
- [ ] Navegación entre pasos con radio buttons (CSS-only)

---

## 🌐 Idioma (Decisión de Proyecto)

- **Toda la interfaz, navegación, textos, ARIA y accesibilidad van en español** (`lang="es"`).
- **Los nombres de producto se mantienen en francés** (Blouson Nocturne, Chemise Ombre…) por ser nombres propios de la marca.
- Aunque la marca sea ficticia y francesa, **el único idioma audible en la página es el español**.
- No traducir nombres propios de marca ni de producto.

---

## 🧠 Comportamiento del Agente

Como agente trabajando en MAISON NOIRE, debes:

1. **Leer este archivo completo** al inicio de cada sesión antes de hacer cualquier otra cosa.
2. **Leer [`DESIGNS.md`](./DESIGNS.md)** para conocer la guía visual — colores, tipografía, componentes y estilo.
3. **Actualizar [`PROGRESS.md`](./PROGRESS.md)** al completar cada implementación significativa (nueva vista, cambio mayor).
4. **No modificar estos archivos** (`AGENTS.md`, `DESIGNS.md`, `PROGRESS.md`) sin consultarme explícitamente.
4. **Recordar que NO hay JavaScript** — cualquier interacción debe resolverse con CSS puro.
5. **Verificar la rama actual** antes de empezar a trabajar. Si trabajas en `feature/xxx`, asegúrate de que sea la rama correcta.
6. **Preguntar antes de crear nuevas ramas** o desviarte del plan establecido.
7. **Mantener consistencia visual** entre páginas: navbar y footer deben ser iguales en todas, siguiendo los valores de `DESIGNS.md`.
8. **Validar accesibilidad** en cada componente que crees o modifiques.
9. **Ante la duda, preguntar.** No asumas.