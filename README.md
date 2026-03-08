# Dragon Imperial — HTML local copy

Resumen
- Archivo principal editado: `dragon_imperial_v2 (1).html` (local)
- Objetivo: mejorar accesibilidad, performance percibida y experiencia de usuario mínima para una demo local.

Cambios principales realizados
- Eliminado el cursor personalizado (círculo rojo) por ser distractor.
- Añadido enlace "Saltar al contenido" para usuarios de teclado.
- Añadidos `type="button"` a muchos botones no-submit para evitar envíos accidentales.
- Envolví el contenido principal en `<main id="main">` para mejorar semántica.
- Añadido pequeño script de "blur-up" para imágenes lazy para mejorar la percepción de carga.
- Preconnect y preload añadidos para la imagen hero (LCP) y dominio de imágenes.
- Cambios de CSS para mejorar contraste en hover de CTAs y enfoque visible (`:focus-visible`).
- Añadidos meta tags (`robots`, `x-ua-compatible`) y mejoras menores de SEO.
- Pequeñas funciones JS añadidas: `toggleMenu`, manejo de cookies, modal y safe fallbacks.

Comandos recomendados para auditoría local
1) Servir los archivos localmente (recomendado antes de Lighthouse/axe):

```bash
# desde la carpeta Downloads donde está el HTML
npx http-server ./ -p 8080
# abrir http://localhost:8080/ en el navegador
```

2) Ejecutar Lighthouse (requiere Chrome):

```bash
# desde otra terminal, con http-server corriendo
npx lighthouse http://localhost:8080/dragon_imperial_v2%20(1).html --output html --view
```

3) Ejecutar axe-core CLI (opcional):

```bash
npm init -y
npm install -D @axe-core/cli puppeteer
npx axe http://localhost:8080/dragon_imperial_v2%20(1).html --save results.json
```

Recomendaciones siguientes (prioridad alta → baja)
- Ejecutar Lighthouse y revisar específicamente: Accessibility, Best Practices, Performance (LCP, CLS), SEO.
- Añadir atributos `alt` descriptivos a todas las imágenes (ya hay muchos, revisar los faltantes o mejorar descripciones). 
- Añadir focus trap y control de teclado para modales y lightbox (actualmente hay cierre por fondo y botón, pero falta trap de focus).
- Implementar headers de caché, compresión (brotli/gzip) y servir imágenes optimizadas desde CDN para reducir LCP.
- Implementar tests automáticos de accesibilidad en CI con axe-core.

Notas
- No ejecuté Lighthouse/axe aquí (no hay servidor ni navegador en este entorno). Las instrucciones anteriores te permiten ejecutar las auditorías localmente.
- Si quieres, creo un `package.json` con scripts para `serve`, `audit:lh` y `audit:axe`, y un pequeño `ci/` con comandos que puedas ejecutar en tu máquina o CI.

¿Quieres que añada los scripts `npm` y el `package.json` ahora?