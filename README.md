# Post-contenido — Unidad 3: CSS3 Básico

## Descripción
Repositorio del laboratorio de la Unidad 3 de Programación Web — Séptimo Semestre. Contiene dos partes: página de perfil con selectores CSS avanzados, Box Model y posicionamiento (`parte-1-perfil-css3/`) y dashboard responsivo con CSS Grid y Flexbox (`parte-2-dashboard-grid/`).

## Parte 1 — Página de perfil
Página de perfil personal que implementa selectores CSS avanzados, `box-sizing: border-box`, posicionamiento (fixed/relative/absolute), una escala de espaciado con Custom Properties (`--space-3xs` a `--space-3xl`), tipografía fluida con `clamp()` en el nombre de perfil y formulario de contacto accesible con estados `:focus`. Ver `parte-1-perfil-css3/`.

## Parte 2 — Dashboard con Grid y Flexbox
Dashboard responsivo con layout principal en CSS Grid (`grid-template-areas`), sidebar y topbar en Flexbox, stat-cards con Grid auto-fill responsivo, panel de contenido en proporción 2fr/1fr con un tercer panel ("Notas del Sprint") posicionado mediante colocación explícita de Grid (`grid-column: 1 / -1`), y tabla de proyectos con franjas zebra vía `:nth-child(even)`. Sin frameworks CSS externos. Ver `parte-2-dashboard-grid/`.

## Decisiones de diseño

### Parte 1 — Estrategia de especificidad para validación
Se eligió la **Estrategia A**: `input:invalid:not(:placeholder-shown)`. Se prefirió sobre la Estrategia B (`.contact-form input:invalid`) porque aprovecha la validación HTML5 nativa de `required`/`type="email"` y solo se activa después de que el usuario haya escrito algo en el campo, gracias a `:not(:placeholder-shown)`. Esto evita que los campos vacíos se muestren en rojo al cargar la página por primera vez, sin necesidad de JavaScript ni lógica adicional en el HTML. Su especificidad (0,0,2,0) es igual a la de `input:focus` del Paso 7; al declararse después en el archivo, la regla de error gana cuando el campo no está enfocado, y al hacer foco sobre un campo inválido, el ring de `:focus` vuelve a aplicarse con normalidad. No se usó `!important` en ningún punto.

### Parte 2 — Breakpoint y estrategia de layout responsivo
Se eligió un breakpoint de **768px** y la **estrategia Grid**. Se probó en DevTools (Toggle device toolbar) que por debajo de este ancho el sidebar fijo de 220px dejaba muy poco espacio para el contenido de las stat-cards y la tabla de proyectos, generando texto apretado. Se prefirió la estrategia Grid (redefinir `grid-template-areas` a una columna: `"topbar" "sidebar" "main"`) sobre la estrategia Flex porque reutiliza el mismo sistema de áreas nombradas ya declarado en el Paso 2 del layout principal, sin necesidad de cambiar la asignación `grid-area` de `.sidebar`, `.topbar` y `.dashboard-main`: solo se redefine el mapa de columnas, filas y áreas dentro del media query.

## Cómo visualizar el proyecto
1. Clonar el repositorio: `git clone https://github.com/richardrabt21/boada-post1-u3.git`
2. Abrir la carpeta en Visual Studio Code
3. Clic derecho en `index.html` (de cada parte) → "Open with Live Server"

##