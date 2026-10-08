# PDF a mapa mental (para GitHub Pages)

Página de un solo archivo (`index.html`). El PDF se procesa en el navegador de quien la usa: no se sube a ningún servidor y no usa IA generativa.

## Publicarla en GitHub Pages (gratis)

1. En github.com crea un repositorio **público** (por ejemplo `pdf-a-mapa-mental`).
2. Entra al repositorio y elige **Add file → Upload files**. Sube `index.html` a la raíz y pulsa **Commit changes**.
3. Ve a **Settings → Pages**. En *Build and deployment* elige **Deploy from a branch**, rama **main**, carpeta **/ (root)**, y guarda.
4. En uno o dos minutos la página queda en `https://TU-USUARIO.github.io/NOMBRE-DEL-REPO/`.

## Qué necesita
- Conexión a internet al abrir la página: carga pdf.js, d3 y markmap desde jsDelivr (versiones fijas).
- PDF con texto seleccionable. Los escaneados necesitan OCR antes.
- También se puede abrir `index.html` haciendo doble clic (funciona, pero pdf.js va más lento sin su proceso aparte).

## Qué hace
- **Libros:** usa los marcadores (índice) del PDF si existen; si no, detecta títulos por tamaño y estilo de letra.
- **Papers:** reconoce Introducción, Método, Resultados, Discusión, Limitaciones y Conclusiones, extrae el abstract y las palabras clave del autor, y omite referencias.
- **Cada sección:** palabras clave (TF-IDF entre secciones) y oraciones centrales (TextRank).
- **Descargas:** Markdown (`.md`) y un HTML interactivo que funciona sin internet.
- **Editable:** en la pestaña Markdown puedes corregir el resultado y actualizar el mapa.

## Límites conocidos
- Las palabras clave y oraciones se eligen por estadística; conviene revisarlas.
- Si el PDF no trae índice y la letra de los títulos no se distingue del texto, el mapa sale pobre.
- Libros muy grandes (cientos de páginas) pueden tardar varios segundos y la pestaña se queda ocupada mientras tanto.
- Dos secciones del libro que empiezan en la misma página comparten el texto de esa página.
