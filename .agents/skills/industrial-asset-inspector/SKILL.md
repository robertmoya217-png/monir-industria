---
name: industrial-asset-inspector
description: Forensic inspection, curation, and subtle integration of real industrial factory media. Guides the creation of non-predominant, editorial-grade carousels and galleries that communicate tangible manufacturing authenticity and operational scale.
---

# Industrial Asset Inspector & Visual Evidence Curator

> **Protocolo de Inspección de Material Fabril y Dirección de Galerías Industriales No Predominantes**

Esta skill guía el análisis de activos visuales reales (fotografía de maquinaria pesada, naves industriales, materia prima y operaciones de planta) para respaldar la legitimidad de **Industria Monir** sin comprometer la elegancia editorial del sitio.

---

## 🔍 Criterios de Evaluación de Material Crudo

Cuando el usuario suministra fotografías o videos en bruto de la fábrica:

1. **Autenticidad Operacional:**
   - Priorizar tomas de maquinaria pesada real en proceso (abridoras, cardas, continuas de hilar, enconadoras, prensas de enfardado).
   - Identificar evidencia tangible de escala: pilas de fardos flejados, pallets preparados para despacho logístico, bobinas en hilera, detalles de la textura de fibra y urdimbre.
   - Descartar tomas borrosas o sin contexto fabril significativo.

2. **Calibración Cromática & Textura:**
   - La imagen debe dialogar armónicamente con la paleta sobria de la marca (`#141413` carbón, `#8C6D46` cuero gerencial, `#DDD0C0` arena, `#FAF7F2` hueso).
   - Si la foto presenta colores chillones o iluminación dispar de taller, aplicar tratamiento sutil: desaturación controlada, ligera inclinación sepia/cuero, o monocromo industrial contrastado.

---

## 🎞️ Reglas del Carrusel Sutil (No Predominante)

El carrusel o galería fotográfica de evidencia real **NO debe competir** con la jerarquía principal del sitio ni con el Canvas interactivo de fibras.

### Reglas de Diseño e Integración:
- **Estructura tipo Filmstrip o Dossier Documental:**
  - Altura moderada y contenida (no pantallas completas que interrumpan la lectura).
  - Controles minimalistas: sin flechas fluorescentes gigantes. Uso de arrastre táctil suave (*touch-drag*), scroll horizontal nativo o indicadores discretos tipo barra de progreso milimétrica.
  - Pausa automática al interactuar (*hover/touch*).
- **Cartelas Técnicas (Pies de Foto Sobrios):**
  - Cada imagen debe portar un pie de foto técnico y conciso que aporte contexto de ingeniería, por ejemplo:
    - *«Nave de Hilatura — Máquinas de rotor Open-End»*
    - *«Zona de Embalaje — Fardos de algodón comprimido con fleje de alta resistencia»*
    - *«Acondicionamiento térmico de bobinas de pavilo industrial»*
- **Rendimiento y Carga Silenciosa:**
  - Carga diferida obligatoria (`loading="lazy"`).
  - Relación de aspecto fija para evitar saltos de diseño (*Cumulative Layout Shift = 0*).
