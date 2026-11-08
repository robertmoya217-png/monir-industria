# 📐 Industrial Editorial Design System (Furrow Style) — Industrias Monnir
> **Guía Rápida de Diseño y Tokens Reutilizables para Nuevos Sitios y Subpáginas**

Este archivo contiene la especificación visual completa, paleta de colores y componentes interactivos listos para producción. Puedes referenciarlo directamente en futuros prompts o proyectos con un simple: *"Usa el estilo visual de DESIGN_SYSTEM.md"*, ahorrando tokens y manteniendo coherencia absoluta.

---

## 🎨 Paleta de Colores Oficial (HEX & Variables CSS)

```css
:root {
  /* ── PALETA BASE & ESTRUCTURA ── */
  --color-dark:        #16283C; /* Fondo principal oscuro, Navbar, Footer, Overlays */
  --color-primary:     #1F3A5F; /* Contenedores secundarios, Cards oscuras, Slip card */
  --color-secondary:   #3E598C; /* Hover interactivo, bordes secundarios */
  --color-gray:        #5A6E85; /* Texto secundario en fondos claros */
  --color-medium-gray: #8FA3BC; /* Texto secundario en fondos oscuros / líneas */

  /* ── GAMA BEIGE / ARENA / CREMA (ACENTOS & DETALLES) ── */
  --color-accent:      #D4B28C; /* Acento primario, botones hero, badges, estrellas */
  --color-brown:       #C4A77D; /* Acento secundario dorado */
  --color-sand:        #F2E8DC; /* Cursivas elegantes <em>, texto arena */
  --color-cream:       #F5EFEF; /* Fondos neutros de secciones claras */
  --color-bg:          #F5EFEF; /* Fondo general del <body> */
  --color-white:       #FFFFFF; /* Blanco puro para titulares de alto contraste */
}
```

---

## 🔤 Tipografía Oficial

- **Titulares Primarios**: `'Host Grotesk', -apple-system, sans-serif`
  - Pesos: 500, 600
  - Altura de línea: `1.02` - `1.04`
  - Espaciado: `letter-spacing: -0.035em`
- **Cursivas Institucionales (`<em>`)**: `'Lora', Garamond, serif`
  - Color: `#F2E8DC` (`--color-sand`)
- **Cuerpo y Datos**: `'Host Grotesk'`, `'DM Sans'` (regular 400)

```html
<link href="https://fonts.googleapis.com/css2?family=Host+Grotesk:ital,wght@0,400;0,500;0,600;0,700;1,400&family=Lora:ital,wght@0,400;0,500;1,400&family=DM+Sans:ital,opsz,wght@0,9..40,400;0,9..40,500&display=swap" rel="stylesheet" />
```

---

## 🚫 Reglas de Simplificación Visual

1. **Cero Fondos Animados ni Canvas de Partículas**: Nada de mallas flotantes ni scripts en loop.
2. **Cero Granulado / Noise**: Prohibido aplicar texturas `fractalNoise` o capas de ruido en CSS.
3. **Fotografía Real a Sangre**: Fondos fotográficos de planta y maquinaria real (`object-fit: cover`, opacidad `0.35 - 0.45`) con degradado vertical en `#16283C`.
4. **Botones Cápsula / Píldora (`border-radius: 9999px`)**: Con sombra oscura sutil y micro-animación en hover.

---

## 🔘 Componentes Insignia

### 1. Botón Píldora con Estrella Giratoria (`.m-btn-furrow`)
```css
.m-btn-furrow {
  display: inline-flex;
  align-items: center;
  gap: 0.65em;
  min-height: 42px;
  padding: 0.65em 1.25em 0.65em 1.4em;
  border: 0;
  border-radius: 9999px;
  background: var(--color-accent);
  color: var(--color-dark);
  font-family: var(--font-headline);
  font-size: 0.78rem;
  font-weight: 600;
  line-height: 1;
  letter-spacing: 0.08em;
  text-transform: uppercase;
  white-space: nowrap;
  cursor: pointer;
  box-shadow: 0 4px 16px rgba(0, 0, 0, 0.28);
  transition: background-color 0.35s ease, transform 0.35s ease, color 0.35s ease, box-shadow 0.35s ease;
}
.m-btn-furrow .m-btn__star {
  width: 0.95em;
  height: 0.95em;
  flex: none;
  transition: transform 0.6s cubic-bezier(0.3, 1.5, 0.5, 1);
}
.m-btn-furrow:hover {
  background: #FFFFFF;
  color: var(--color-dark);
  transform: translateY(-2px);
  box-shadow: 0 10px 24px rgba(0, 0, 0, 0.35);
}
.m-btn-furrow:hover .m-btn__star {
  transform: rotate(60deg);
}
```

```html
<button class="m-btn-furrow">
  <span>Ver Catálogo Mayorista</span>
  <svg class="m-btn__star" viewBox="-100 -100 200 200" aria-hidden="true" focusable="false">
    <g fill="currentColor">
      <rect x="-100" y="-19" width="200" height="38" />
      <rect x="-100" y="-19" width="200" height="38" transform="rotate(60)" />
      <rect x="-100" y="-19" width="200" height="38" transform="rotate(120)" />
    </g>
  </svg>
</button>
```

---

### 2. Enlace con Subrayado Re-trazado (`.m-link-furrow`)
```css
.m-link-furrow {
  position: relative;
  display: inline-block;
  padding-bottom: 3px;
  font-family: var(--font-headline);
  font-size: 0.78rem;
  font-weight: 600;
  letter-spacing: 0.1em;
  text-transform: uppercase;
  color: var(--color-sand);
  background: none;
  border: none;
  cursor: pointer;
}
.m-link-furrow::after {
  content: "";
  position: absolute;
  left: 0;
  right: 0;
  bottom: 0;
  height: 1px;
  background: currentColor;
  transform-origin: 0% 50%;
}
.m-link-furrow:hover::after {
  animation: m-link-redraw 0.7s cubic-bezier(0.6, 0, 0.2, 1);
}
@keyframes m-link-redraw {
  0% { transform-origin: 100% 50%; transform: scaleX(1); }
  45% { transform-origin: 100% 50%; transform: scaleX(0); }
  46% { transform-origin: 0% 50%; transform: scaleX(0); }
  100% { transform-origin: 0% 50%; transform: scaleX(1); }
}
```

---

### 3. Tarjeta Flotante del Hero (`.hero-slip-card`)
```css
.hero-slip-card {
  max-width: 440px;
  width: 100%;
  background: rgba(31, 58, 95, 0.94);
  backdrop-filter: blur(18px);
  -webkit-backdrop-filter: blur(18px);
  border: 1px solid rgba(212, 178, 140, 0.32);
  border-radius: 6px;
  padding: clamp(22px, 2.6vw, 32px);
  display: flex;
  flex-direction: column;
  gap: 18px;
  box-shadow: 0 24px 50px rgba(0, 0, 0, 0.42);
}
```

---

## ⚡ Cómo Usar en Próximas Peticiones
Para aplicar este diseño a una nueva vista, landing page o sección sin gastar tokens, solo debes indicar:

> *"Aplica el sistema de diseño definido en `DESIGN_SYSTEM.md` para esta nueva sección/página."*
