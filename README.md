# GIDA Web Portal 🚀
### Grupo de Investigación y Desarrollo Aeroespacial - Universidad Nacional de Colombia

Este repositorio alberga el código fuente y los activos digitales del portal oficial del **GIDA**. El sitio ha sido diseñado como una plataforma estática de alto rendimiento, utilizando el generador **Jekyll** y el framework **Minimal Mistakes**. Su objetivo es documentar la trayectoria investigativa, gestionar la comunidad de miembros y servir como repositorio educativo para el sector aeroespacial en Colombia.

---

## 🔗 Ecosistema de Desarrollo y Despliegue

Para garantizar la estabilidad del sitio oficial, el flujo de trabajo se divide en un entorno de pruebas (Sandbox) y una futura rama de producción institucional.

* **Repositorio de Pruebas (Desarrollo):** [https://github.com/nherreno/GIDAWEBPAGE_test-](https://github.com/nherreno/GIDAWEBPAGE_test-)
* **Visualización en Vivo (Staging):** [https://nherreno.github.io/GIDAWEBPAGE_test-/](https://nherreno.github.io/GIDAWEBPAGE_test-/)
* **Punto de Contacto Técnico:** Para reportar incidencias, solicitar permisos de colaborador o proponer cambios estructurales, contactar a: **nherreno@unal.edu.co**.

> **Nota Importante:** Actualmente el despliegue se realiza mediante **GitHub Pages**. Todos los cambios mergeados a la rama principal se compilan automáticamente mediante *GitHub Actions*.

---

## 🛠️ Especificaciones Técnicas y Configuración

### 1. Motor de Generación (`Gemfile`)
El proyecto depende de un entorno Ruby optimizado. El archivo `Gemfile` ha sido configurado para replicar con exactitud el entorno de ejecución de GitHub:
* **github-pages:** Gema principal que unifica las versiones de Jekyll y sus dependencias.
* **jekyll-include-cache:** Implementada para mejorar la velocidad de compilación local y remota, evitando procesar múltiples veces componentes estáticos como el menú de navegación.

### 2. Configuración Global (`_config.yml`)
Este es el cerebro del sitio. Se han definido parámetros críticos para la identidad y el funcionamiento:
* **Identidad Institucional:** Título configurado como "GIDA UNAL", biografía del grupo y redes sociales integradas en el sidebar.
* **Skinning:** Se utiliza el tema `contrast` (evolución estética de `air`) para garantizar un alto contraste y legibilidad profesional.
* **Rutas y Dominio:** El parámetro `baseurl: "/GIDAWEBPAGE_test-"` es **mandatorio**. Todas las rutas internas de imágenes y estilos deben usar este prefijo para evitar errores 404.
* **Plugins:** Activación de `jekyll-paginate` para la gestión de noticias y `jekyll-sitemap` para optimización SEO.

### 3. Personalización de Estilos (`assets/css/main.scss`)
Se detectó que el tema original comprimía excesivamente el texto. Por ello, se intervino el núcleo SCSS:
* **Espaciado:** Se modificó el `margin-bottom` de los párrafos dentro de `.page__content`.
* **Tipografía:** Ajustes en la escala modular para que los títulos científicos resalten sobre el cuerpo del texto.
* **Intervenciones futuras:** Cualquier cambio visual global debe realizarse al final de este archivo para no romper la herencia del tema base.

---

## 👥 Gestión de Miembros (Pipeline de Actualización)

El GIDA utiliza un sistema de actualización de integrantes basado en la separación de datos y código. Esto permite que personas sin conocimientos de programación puedan contribuir.

### 🔄 Proceso de Actualización Paso a Paso:
1.  **Captura de Datos:** El aspirante o miembro diligencia el **Google Form** oficial del grupo.
2.  **Validación en Drive:** El administrador verifica que la información en el **Excel consolidado** sea correcta y profesional.
3.  **Preparación de Multimedia:**
    * La fotografía debe ser cuadrada o con relación de aspecto 4:5.
    * Guardar en: `/assets/images/miembros/` con un nombre descriptivo (ej: `ing_pedro_perez.jpg`).
4.  **Edición del Backend Estático (`_data/miembros.yml`):**
    * Añadir el nuevo registro respetando la sangría de 2 espacios.
    * **Campo "tipo":** Debe ser obligatoriamente `pregrado`, `posgrado` o `egresado`. De lo contrario, el script de Liquid no lo mostrará en la pestaña correspondiente.

---

## 📚 Módulo de Semilleros y Educación

La sección de Semilleros (`semilleros.md`) es un componente híbrido que consume datos locales y remotos:

### 📺 Integración con YouTube
* **Canales Vinculados:** "GIDA UN" y "Cohetes de Agua GIDA-UN".
* **Gestión de Miniaturas:** Debido a que las APIs de YouTube pueden fallar al entregar portadas de Playlists, el sitio utiliza activos locales: `/assets/images/imagen_play_list_1.jpg`, `imagen_play_list_2.jpg`, etc. Esto asegura una carga instantánea y una estética controlada.
* **Contenidos Destacados:** Se incluye una sección especial para entrevistas internacionales de alto nivel (ej: NASA Johnson Space Center) mediante el ID del video directo.

---

## 📸 Sección de Recuerdos (Galería Dinámica)

Se implementó un sistema de visualización de memorias institucionales en `recuerdos.md` con las siguientes características técnicas:
* **Contenedor Masonry:** Permite una disposición orgánica de imágenes de distintos tamaños.
* **Lógica de Barajado (Shuffle):** Un script de JavaScript reorganiza las imágenes de forma aleatoria en cada carga de página. Esto evita que la galería se sienta estática y prioriza diferentes momentos históricos del grupo en cada visita.
* **Gestión de Archivos:** Las imágenes deben cargarse en la carpeta específica de recuerdos dentro de `assets/images/`.

---

## 🚀 Guía de Contribución para Desarrolladores

Para clonar y trabajar en este proyecto localmente:

1.  **Instalar Ruby y Bundler:** Asegúrate de tener una versión compatible (3.X sugerida).
2.  **Instalar Dependencias:** Ejecuta `bundle install` en la raíz del proyecto.
3.  **Correr Servidor Local:** Ejecuta `bundle exec jekyll serve`.
4.  **Verificación:** Abre `http://127.0.0.1:4000/GIDAWEBPAGE_test-/` en tu navegador.

### 📝 Buenas Prácticas:
* **Optimización:** Nunca subir imágenes de más de 500KB. Usa herramientas de compresión.
* **Markdown:** Mantener el uso de "Front Matter" (el encabezado entre `---`) en cada archivo `.md`.
* **Commits:** Usa mensajes descriptivos como `fix: corrección de link en semilleros` o `style: ajuste de márgenes en sidebar`.

---
**GIDA - Grupo de Investigación y Desarrollo Aeroespacial** *Universidad Nacional de Colombia - Facultad de Ingeniería* *Sede Bogotá, Colombia.*