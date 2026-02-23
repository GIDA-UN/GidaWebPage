GidaWebPage
Officiall Web page for GIDA UN vamos a usar una plantilla llamada jekyll de minimal mistakes , para las personas que mas adelante desarrollen codigo, posteriormente , quizas nos toque hacer nmodificaciones , voy a crear un repo de prueba en Github , actualizare el link, para que clonen la plantilla y adicional , pues trabajen sobre algo , ya mas sugerido para GIDA link https://github.com/nherreno/GIDAWEBPAGE_test- link visualizar: https://nherreno.github.io/GIDAWEBPAGE_test-/ si hay algun problema para editar o acceder a este repo , escribir a nherreno@unal.edu.co, posdata mas adelante generaremos el link de la pagina oficial 

1. Configuración del Motor (Gemfile)
Lo primero que se realizó fue modificar el archivo Gemfile para asegurar la compatibilidad con los servidores de GitHub.

Se definieron las librerías base: github-pages y el plugin jekyll-include-cache.

Esto permitió que las GitHub Actions dejaran de marcar error y pudieran compilar el sitio correctamente.

2. Identidad y Rutas (_config.yml)
Posteriormente, modificamos el archivo maestro de configuración para darle identidad al grupo:

Identidad: Se cambió el título a "GIDA UNAL" y se ajustó la biografía del autor con los datos del grupo.

Skin: Se seleccionó el tema visual air, que ofrece un fondo gris claro más profesional que el predeterminado.

Rutas Críticas: Se configuró el baseurl como "/GIDAWEBPAGE_test-". Sin este paso, el navegador no encontraba los archivos de estilo y la página se veía como texto plano.

3. Estructura de Navegación (_data/navigation.yml)
Para organizar la información, creamos un sistema de pestañas en la parte superior derecha:

Se eliminaron los links de ejemplo del tema original (como el "Quick-Start Guide").

Se añadieron los accesos directos estratégicos: Profesores, Proyectos de Investigación, Miembros, Publicaciones, Convocatorias y Semilleros.

NOTA:index  permite modificar como la pantallaza de inicio por partes , ya de manera mas tecnica hace parte del front 
------------------------------------------------------------------------------------------------------------------------------------------

🛠️ Estado Actual: Refinando el Inicio
Actualmente, nos encontramos en la fase de pulir la Página de Inicio (index.md).

El objetivo es pasar de una lista simple de entradas a un diseño de alto impacto visual con cabeceras y una biografía de autor completa en la barra lateral.

Nota: El paso de creación de archivos individuales para cada pestaña del menú aún no se ha ejecutado, priorizando la estabilidad y estética de la fachada principal.