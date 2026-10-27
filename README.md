# 🧵 INDUSTRIA MONIR — DOCUMENTACIÓN TÉCNICA Y DE DISEÑO
> **Guía maestra para el próximo desarrollador / agente de IA**  
> *Fecha de última actualización: 27 de Octubre de 2026*  
> *Ubicación del proyecto local:* `C:\Users\rober\Desktop\industria-monir\`  
> *Deploy en vivo (GitHub Pages):* [https://robertmoya217-png.github.io/monir-industria/](https://robertmoya217-png.github.io/monir-industria/)  
> *Repositorio remoto:* [https://github.com/robertmoya217-png/monir-industria.git](https://github.com/robertmoya217-png/monir-industria.git)

---

## 🏛️ 1. CONTEXTO DE LA EMPRESA & MARCA

* **Nombre de la empresa:** `Industria Monir` (o `MONIR — Industria Textil`).
* **Rubro / Industria:** Textil pesada, manufactura mayorista de **Algodón**, **Hilo** y **Pavilo**.
* **Modelo de negocio:** **100% B2B masivo** (venta por toneladas/fardos/pallets para tejedurías, hilanderías y confeccionistas industriales).
* **Reglas críticas de contenido (¡IMPORTANTE!):**
  * ❌ **NO poner precios ni cotizaciones numéricas explícitas** en el front-end.
  * ❌ **NO saturar con certificaciones burocráticas duras** ni tablas de laboratorio excesivamente aburridas.
  * ❌ **NO usar fotos genéricas de stock de baja calidad ni caras IA falsas.**
  * ✅ Mantener el estilo de **landing page ejecutiva con asteroides**: elegante, espaciosa, con peso de legado y enfocada en contacto/cotización formal.

---

## 🎨 2. SISTEMA DE DISEÑO (BASADO EN EL MOOD BOARD)

Inspirado en estética gerencial, tapicería cuero, madera cálida, metal negro mate y telas crudas.

### Paleta de Colores (CSS Variables en `:root`):
* `--color-black`: `#141413` (Fondo principal nocturno/sobrio)
* `--color-charcoal`: `#1F1F1D` (Superficies secundarias y tarjetas oscuras)
* `--color-dark-gray`: `#2B2A27`
* `--color-warm-brown`: `#8C6D46` (Cuero cálido gerencial / acento primario)
* `--color-brown`: `#A68759`
* `--color-tan`: `#C4A77D` (Dorado/arena claro, acentos y hover)
* `--color-sand`: `#DDD0C0` (Texto cursivo secundario y líneas)
* `--color-cream`: `#F2ECE1` (Fondos claros de contraste)
* `--color-off-white`: `#FAF7F2` (Texto principal claro / fondos)
* `--color-white`: `#FFFFFF`

### Tipografía (Google Fonts):
* **Títulos Display:** `EB Garamond` (Serif tradicional, sólida, estilo editorial europeo sin vibe de plantilla barata).
* **Acentos Cursivos Finos:** `Lora` (`font-style: italic`, elegante y sin sobrecargar).
* **Cuerpo, UI y Botones:** `DM Sans` (Sans-serif limpia, moderna, alta legibilidad en pantallas táctiles y desktop).

---

## 🏗️ 3. ARQUITECTURA TÉCNICA (SINGLE-PAGE APPLICATION EN REACT 18)

El proyecto completo vive en un único archivo auto-contenido optimizado para GitHub Pages:
📁 [`index.html`](file:///c:/Users/rober/Desktop/industria-monir/index.html)

### Tecnologías & Librerías Utilizadas:
1. **React 18 & ReactDOM (UMD):** Manejo de estado del portal activo (`useState`, `useCallback`, `useRef`).
2. **Babel Standalone:** Transpilación JSX en caliente sin necesidad de un bundler pesado (Node.js/Vite/Webpack no requeridos para correr o editar).
3. **GSAP 3.12 (GreenSock):**
   * Control del telón cinemático superior/inferior (`.curtain-panel-top` y `.curtain-panel-bottom`).
   * Transición sincronizada con el resplandor de la marca `INDUSTRIA MONIR`.
4. **HTML5 Canvas:**
   * Componente `<FiberFieldCanvas />`: Genera partículas conectadas que simulan urdimbre/trama textil flotante interactiva en el fondo del Hero.
5. **Micro-textura SVG:**
   * Textura procedural SVG incrustada como background en `body::before` para eliminar la sensación plástica de colores digitales planos (*anti-AI vibe*).

---

## 📱 4. LOS 6 SUB-PORTALES IMPLEMENTADOS

El estado `page` en React gobierna qué sub-portal se renderiza dentro del contenedor `<main>`:

| ID | Nombre en UI | Componente | Descripción |
|---|---|---|---|
| `inicio` | Inicio | `<PortalInicio />` | Hero principal 100dvh con canvas interactivo, marquee textil continuo, presentación asimétrica de la empresa, preview de las 3 líneas de producto y CTA banner. |
| `nosotros` | Nosotros | `<PortalNosotros />` | Historia de la industria, enfoque mayorista, pilares (Misión, Visión, Valores) y diferenciadores. |
| `productos` | Productos | `<PortalProductos />` | Las 3 líneas maestras: **Algodón Industrial**, **Hilo de Alta Tenacidad** y **Pavilo Homogéneo** con ilustraciones abstractas vectoriales y fichas descriptivas. |
| `procesos` | Procesos | `<PortalProcesos />` | Timeline de 6 fases del proceso productivo (Selección, Apertura, Cardado, Hilatura, Acondicionamiento y Embalaje Mayorista). |
| `clientes` | Clientes | `<PortalClientes />` | Sectores B2B atendidos (Tejedurías de punto, Tejido plano, Talleres, Cordonerías, Agro/Empaque y Distribuidores). |
| `contacto` | Contacto | `<PortalContacto />` | Mesa comercial B2B con formulario accesible de solicitud de cotización por lote y enlaces directos. |

---

## ⚙️ 5. REGLAS MOBILE & RESPONSIVE RESUELTAS

* **Transición 100dvw / 100dvh:** El telón de cambio de portal tiene `position: fixed; width: 100dvw; height: 100dvh; z-index: 99990;`. Se bloquea temporalmente el scroll del body con `document.body.style.overflow = 'hidden'` durante la animación para evitar saltos o desbordes en Safari iOS y Chrome Android.
* **Texto central clamp:** `.curtain-brand-glow` utiliza `font-size: clamp(1.2rem, 5.5vw, 2.5rem)` y ancho del `90%` con saltos de línea permitidos para que nunca se desborde horizontalmente en pantallas pequeñas (320px–390px).
* **Menú Drawer Lateral:** En pantallas `< 992px`, la barra de navegación se oculta y da paso a un botón hamburguesa de 48px táctiles que despliega un drawer desde la derecha con desenfoque de fondo (*backdrop-filter: blur(20px)*).
* **Botón Flotante de WhatsApp:** Acceso rápido fijo en la esquina inferior derecha (`#25D366`) con touch target generoso.

---

## 🚀 6. COMANDOS DE DESPLIEGUE RÁPIDO

Si realizas cambios en `index.html`, para sincronizar tanto la rama de código como el hosting en vivo de GitHub Pages:

```powershell
# 1. Entrar a la carpeta
cd "C:\Users\rober\Desktop\industria-monir"

# 2. Agregar cambios y commitear
git add index.html
git commit -m "update: descripcion del cambio"

# 3. Subir a la rama principal
git push origin main

# 4. Actualizar el despliegue de GitHub Pages
git checkout gh-pages
git merge main
git push origin gh-pages
git checkout main
```

---

*Documento creado automáticamente para garantizar continuidad absoluta y preservar cada decisión de diseño tomada con el usuario.* 🧵
