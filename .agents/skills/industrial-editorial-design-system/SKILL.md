---
name: industrial-editorial-design-system
description: Sistema de diseño frontend editorial de alta gama (estilo Furrow / Minimalismo B2B Industrial) para Industrias Monnir y futuros sitios web corporativos. Incluye paleta de colores estricta, tipografía Host Grotesk, botones píldora con estrella giratoria, tarjetas flotantes asimétricas y reglas de cero granulado/cero fondos animados.
---

# 📐 Industrial Editorial Design System (Furrow Style)
> **Especificación Frontend Definitiva y Biblioteca de Tokens para Sitios Web Corporativos B2B**

Este documento recopila de forma estructurada el sistema visual completo implementado en **Industrias Monnir C. A.** (inspirado en la arquitectura visual de *Furrow / Farm Delivery*), para reutilizarlo de forma instantánea sin gastar tokens de contexto en nuevos proyectos o subportales.

---

## 🎨 1. Paleta Oficial de Colores (Tokens Obligatorios)

```css
:root {
  /* ── PALETA PRIMARIA ── */
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

## 🔤 2. Tipografía y Jerarquía Editorial

### Carga de Fuentes (Google Fonts)
```html
<link rel="preconnect" href="https://fonts.googleapis.com" />
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
<link href="https://fonts.googleapis.com/css2?family=Host+Grotesk:ital,wght@0,400;0,500;0,600;0,700;1,400&family=Lora:ital,wght@0,400;0,500;1,400&family=DM+Sans:ital,opsz,wght@0,9..40,400;0,9..40,500&display=swap" rel="stylesheet" />
```

### Reglas de Aplicación Tipográfica:
- **Titulares de Gran Impacto (`--font-headline`)**: `Host Grotesk`, peso 500 o 600, `line-height: 1.02 - 1.04`, `letter-spacing: -0.035em`.
- **Énfasis Editorial (`<em>`)**: `Lora` (o Garamond), cursiva (`font-style: italic`), peso 400, color `--color-sand` (`#F2E8DC`).
- **Cuerpo y Datos Técnicos (`--font-body`)**: `Host Grotesk` o `DM Sans`, peso 400, `line-height: 1.5 - 1.6`.

---

## 🏛️ 3. Reglas Críticas de Integridad Visual (Cero Desviaciones)

1. **🚫 Cero Fondos Animados ni Canvas de Partículas**: Nada de mallas flotantes, esferas o scripts en bucle continuo de CPU en el hero.
2. **🚫 Cero Granulado / Ruido (`noise`, `grain`)**: Suprimir por completo filtros SVG de ruido fractal (`body::before`).
3. **🖼️ Fotografía a Sangre Real (Full-Bleed Industrial Asset)**: Fondos con fotografía real de nave fabril (`object-fit: cover`, opacidad `0.35 - 0.45`), teñidos por un degradado vertical que va desde `rgba(22, 40, 60, 0.45)` a `rgba(22, 40, 60, 0.98)`.
4. **🔘 Botones Píldora (`border-radius: 9999px`)**: Todos los CTAs principales deben ser tipo cápsula redondeada con sombra difuminada y micro-interacción.

---

## 🧩 4. Componentes Clave (Copiar y Pegar)

### Componente A: Botón Píldora con Estrella Giratoria de 6 Puntas (`.m-btn-furrow`)
Al hacer hover, la estrella rota **60 grados** con un rebote elástico.

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

### Componente B: Enlace con Re-dibujado de Subrayado (`.m-link-furrow`)
Al pasar el cursor, el subrayado se retrae hacia la derecha y se redibuja desde la izquierda.

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

### Componente C: Tarjeta Flotante Asimétrica del Hero (`.hero-slip-card`)

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
.slip-status {
  display: inline-flex;
  align-items: center;
  gap: 8px;
  font-family: var(--font-headline);
  font-size: 0.68rem;
  font-weight: 600;
  letter-spacing: 0.16em;
  text-transform: uppercase;
  color: var(--color-accent);
}
.slip-pulse-dot {
  width: 6px;
  height: 6px;
  border-radius: 50%;
  background: #5cdb95;
  box-shadow: 0 0 8px #5cdb95;
}
.slip-copy {
  font-family: var(--font-headline);
  font-size: clamp(0.86rem, 1vw, 0.94rem);
  line-height: 1.55;
  color: rgba(255, 255, 255, 0.85);
  font-weight: 400;
  letter-spacing: -0.01em;
}
.slip-actions {
  display: flex;
  flex-wrap: wrap;
  align-items: center;
  gap: 14px 22px;
}
```

---

## 🏗️ 5. Estructura Completa del Hero Editorial B2B (JSX / HTML)

```jsx
<section className="hero-furrow">
  {/* Fondo fotográfico real con degradado oscuro */}
  <div className="hero-furrow-media" aria-hidden="true">
    <img
      src="assets/img/nosotros-director-planta.jpg"
      alt="Instalaciones Industriales"
      className="hero-furrow-img"
    />
    <div className="hero-furrow-overlay" />
  </div>

  <div className="hero-furrow-stage">
    {/* Encabezado Editorial Superior */}
    <div className="hero-furrow-top">
      <div className="hero-tag-badge">
        <span className="dot" />
        <span>60 Años Liderando la Transformación Textil • Santa Teresa del Tuy</span>
      </div>
      <h1 className="hero-headline">
        Cada hilo cuenta una historia de <em>transformación y solidez industrial</em>.
      </h1>
    </div>

    {/* Sección Inferior Asimétrica */}
    <div className="hero-furrow-bottom">
      {/* Métricas institucionales a la izquierda */}
      <div className="hero-metrics">
        <div className="metric-item">
          <div className="metric-value">60<span className="accent">+</span></div>
          <div className="metric-label">Años de Trayectoria</div>
        </div>
        <div className="metric-divider" />
        <div className="metric-item">
          <div className="metric-value">100<span className="accent">%</span></div>
          <div className="metric-label">Economía Circular</div>
        </div>
        <div className="metric-divider" />
        <div className="metric-item">
          <div className="metric-value">4</div>
          <div className="metric-label">Líneas de Producción</div>
        </div>
      </div>

      {/* Tarjeta flotante de acción a la derecha */}
      <div className="hero-slip-card">
        <div className="slip-status">
          <span className="slip-pulse-dot" />
          <span>Planta Activa • Despacho Nacional</span>
        </div>
        <p className="slip-copy">
          Pioneros en recuperación textil en Venezuela. Transformamos excedentes industriales en pabilo, coleto, cordón y paño amarillo con entrega continua y control de lote garantizado.
        </p>
        <div className="slip-actions">
          <button className="m-btn-furrow" onClick={() => onNavigate('productos')}>
            <span>Ver Catálogo Mayorista</span>
            <svg className="m-btn__star" viewBox="-100 -100 200 200" aria-hidden="true" focusable="false">
              <g fill="currentColor">
                <rect x="-100" y="-19" width="200" height="38" />
                <rect x="-100" y="-19" width="200" height="38" transform="rotate(60)" />
                <rect x="-100" y="-19" width="200" height="38" transform="rotate(120)" />
              </g>
            </svg>
          </button>
          <button className="m-link-furrow" onClick={() => onNavigate('contacto')}>
            Mesa Comercial B2B →
          </button>
        </div>
      </div>
    </div>
  </div>
</section>
```
