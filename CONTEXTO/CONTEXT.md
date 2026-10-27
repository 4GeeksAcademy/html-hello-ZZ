# 💻 Qué debes hacer

Desarrollar el prototipo de e-commerce en equipo, aplicando lo visto hasta ahora: **HTML semántico, Tailwind, Schema.org, diseño responsivo y Git** (ramas, commits, pull requests). Usar la IA de forma ordenada y mantener el alcance en **HTML + Tailwind únicamente**.

---

## Vistas a implementar (y enlazar entre sí):

- [ ] **Home** – navbar, Hero, listados “Nuevos lanzamientos” y “Más vendidos”, footer (navbar y footer reutilizados en todas las páginas).
- [ ] **Catálogo** – navbar, barra de filtros (categoría, talla), rejilla de productos (p. ej. 4×5), footer.
- [ ] **Vista de producto** – dos columnas (imagen + datos: nombre, código, talla, precio, cantidad, “Añadir al carrito”), sección de descripción; navbar y footer.
- [ ] **Carrito** – vista completa: listado de productos (miniatura, precio unitario, cantidad, total por línea), resumen (subtotal, impuestos, total), botón “Comprar”; p. ej. 3 productos de ejemplo para ver el comportamiento; navbar y footer.
- [ ] **Formulario de pago (checkout)** – 3 pasos: (1) Datos personales, (2) Dirección de entrega, (3) Pago con tarjeta; navbar y footer.

---

## Skill de Git y trabajo en equipo:

- [ ] **Usar una rama por vista o funcionalidad** (p. ej. `feature/home`, `feature/catalogo`). No trabajar directamente en `main`.
- [ ] **Abrir una pull request (PR) por cada rama antes de integrarla en `main`**. Describir qué incluye la PR.
- [ ] **Actualizar tu rama con `main`** (p. ej. `git pull origin main`) antes de enviar la PR para reducir conflictos.
- [ ] **Resolver conflictos en equipo**; no hacer force-push ni sobrescribir el trabajo del otro sin consenso.
- [ ] **Hacer commits frecuentes con mensajes claros** (p. ej. “Añadir navbar y hero al home”, “Añadir rejilla y filtros al catálogo”). Mejor un cambio lógico por commit.

---

# Detalle de Vistas (Estructura)

## 1) Página de inicio (Home)

* **Barra superior (navbar)** con:
  * Logo
  * Barra de búsqueda
  * Menú de cuenta de usuario
* **Sección Hero** destacando productos especiales o campañas de la marca.
* **Dos secciones con listados horizontales** (*cards* de producto):
  * Nuevos lanzamientos
  * Más vendidos
* **Footer con secciones:**
  * Categorías: calzado, camisas, pantalones, accesorios
  * Legal: términos y condiciones, política de privacidad, sobre la marca
  * Contacto
* **La navbar y el footer se reutilizan en todas las demás vistas.**

## 2) Catálogo

* **Mantiene navbar y footer.**
* **Incluye una barra de filtros antes del listado:**
  * Filtro por categoría
  * Filtro por talla
* **Listado de productos en rejilla (grid) 4x5** (20 productos visibles como referencia).

## 3) Vista de producto

* **Diseño en dos columnas:**
  * **Izquierda:** foto del producto ocupando aproximadamente la mitad del ancho.
  * **Derecha:** información principal del producto:
    * Nombre
    * Código o referencia
    * Talla
    * Precio
    * Selector de cantidad
    * Botón "Agregar al carrito"
* **Debajo, una sección de descripción detallada:**
  * Materiales
  * Uso recomendado / escenarios donde se puede usar la prenda

## 4) Carrito

* **Vista completa del carrito** (no un panel lateral).
* **Listado de productos añadidos con:**
  * Miniatura
  * Precio unitario
  * Cantidad
  * Total por producto
* **Cuadro de totalización con:**
  * Subtotal
  * Impuestos
  * Total
  * Botón "Comprar"
* **Añadir 3 productos de ejemplo para mostrar el comportamiento visual.**

## 5) Formulario de pago (Checkout)

**Flujo en 3 pasos:**
1. Datos personales
2. Dirección de entrega
3. Pago con tarjeta (datos de tarjeta)