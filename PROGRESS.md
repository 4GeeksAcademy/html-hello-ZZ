# PROGRESS.md — MAISON NOIRE

> **Registro de cambios significativos del proyecto.**  
> Se actualiza automáticamente con cada implementación completada.

---

## 📋 Estado General del Proyecto

| Vista | Archivo | Estado | Rama |
|---|---|---|---|
| Home | `features/001-home/home.html` | Implementada; validación visual pendiente | `features/home` |
| Catálogo | `catalogo.html` | ❌ Pendiente | `feature/catalogo` |
| Producto | `producto.html` | ❌ Pendiente | `feature/producto` |
| Carrito | `carrito.html` | ❌ Pendiente | `feature/carrito` |
| Checkout | `checkout.html` | ❌ Pendiente | `feature/checkout` |

**Progreso de implementación:** 20% (1/5 vistas). Home pendiente de aceptación visual e integración con las demás vistas.

---

## 🧱 Fase 0 — Base del Proyecto

### [2026-10-27] Configuración inicial

| Archivo | Descripción |
|---|---|
| `AGENTS.md` | Documento de contexto y reglas para agentes. Leer al inicio de cada sesión. |
| `DESIGNS.md` | Guía visual completa: paleta, tipografía, componentes, layout, accesibilidad. |
| `PROGRESS.md` | ✅ **Este archivo.** Registro de progreso del proyecto. |
| `features/` | Carpeta SDD con 5 subcarpetas (`home/`, `catalogo/`, `producto/`, `carrito/`, `checkout/`) para organizar documentación y assets por funcionalidad. |

**Resumen:** Se estableció la base documental del proyecto. Se definió la nueva paleta de colores de la marca (Taupe Noir `#5F5449`, Rose Poudré `#9B6A6C`, Mauve Doux `#B09398`, Sage Pâle `#CEDFD9`, Blanc Glacé `#EBFCFB`), la tipografía (Playfair Display + Inter), y las reglas técnicas (HTML semántico, Tailwind v4 CDN, zero JS, sin frameworks). Se creó la estructura `features/` con una carpeta por funcionalidad para seguir el flujo SDD.

---

## 📝 Historial de Cambios

### [2026-10-27] Home implementada por fases

Implementación en `features/001-home/home.html`: estructura semántica y SEO en español, cabecera responsive, menú de cuenta nativo, campaña fotográfica, dos colecciones con doce productos y footer con contacto y apartados legales desplegables.

- Productos en una columna en móvil, dos desde 768px y cuatro desde 1024px.
- Microdatos `WebSite`, `Store`, dos `ItemList`, doce `Product` y doce `Offer`.
- Imágenes ilustrativas con dimensiones y textos alternativos, carga diferida en productos y prioridad alta en campaña.
- Sin JavaScript propio. Navegación entre colecciones mediante anclas y opciones de cuenta deshabilitadas.
- Editor sin errores. Comprobaciones ejecutables omitidas por el usuario; carga de recursos externos, teclado y pruebas visuales pendientes.
- Catálogo, producto y carrito pendientes; los enlaces están preparados para su integración.
- No se han realizado commits, push ni PR. No se han modificado los README, `server.py`, `learn.json` ni `.vscode/`.

> *(Los nuevos cambios se agregarán aquí al completar cada implementación)*

| Fecha | Tipo | Descripción | Detalle |
|---|---|---|---|
| 2026-10-27 | 📄 Docs | Creación de `AGENTS.md` | Contexto, reglas, arquitectura SDD, workflow Git |
| 2026-10-27 | 🎨 Docs | Creación de `DESIGNS.md` | Guía visual completa con paleta, tipografía, componentes |
| 2026-10-27 | 📊 Docs | Creación de `PROGRESS.md` | Registro de progreso del proyecto |
| 2026-10-27 | � Estructura | Creación de `features/` | 5 subcarpetas SDD: home, catalogo, producto, carrito, checkout || 2026-10-27 | 📋 Especificación | Creación de `features/001-home/specs.md` | Especificación completa del Home: componentes, paleta, tipografía, schema, accesibilidad, 12 productos |
| 2026-10-27 | 📋 Plan | Creación de `features/001-home/plan.md` | Plan de implementación del Home: 5 fases secuenciales con checklist detallado y criterios de validación |
| 2026-10-27 | 🌐 Idioma | Migración a español (`lang="es"`) | Toda la UI, navegación, ARIA y accesibilidad pasan a español. Los nombres de producto se mantienen en francés (nombres propios). Actualizados `specs.md`, `plan.md`, `AGENTS.md` (nueva sección de idioma) y `DESIGNS.md` (tag "Más vendido"). |
---

## 🚀 Próximos Pasos

1. **Home** (`features/001-home/home.html`) — Validación en navegador, recursos externos e integración pendientes; rama `features/home`
2. ⬜ **Catálogo** (`catalogo.html`) — Rama `feature/catalogo`
3. ⬜ **Producto** (`producto.html`) — Rama `feature/producto`
4. ⬜ **Carrito** (`carrito.html`) — Rama `feature/carrito`
5. ⬜ **Checkout** (`checkout.html`) — Rama `feature/checkout`

---

> ⚠️ **Nota:** Cada vez que se complete una vista o un cambio significativo, este archivo debe actualizarse agregando una entrada al historial y marcando el progreso en la tabla de estado general.