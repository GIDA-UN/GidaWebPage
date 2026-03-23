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



se creo una carpeta en assets que guarda las imagenes de recuerdos , y se implemento recuerdos.md la parte de container es la que vamos a modificar para que sea dinamica cada vez que cargemos va a generarse de manera aleatoria el orden de las imagenes 
-------------------------------------------------------------------------------------------------------------------------------------------
---

## 📂 Gestión de Miembros (Actualización de Información)

Se ha centralizado la gestión de la información de los miembros del grupo mediante herramientas compartidas en el Drive de GIDA.

Actualmente se dispone de:
- Un formulario (Forms) para el registro de nuevos integrantes.  
- Un archivo Excel consolidado con toda la información recolectada.

### 🔄 Flujo recomendado de actualización

Para garantizar consistencia y facilitar la gestión del sitio web, se debe seguir el siguiente proceso:

1. **Registro de información**  
   Todos los nuevos miembros deben diligenciar el formulario.  
   Esto asegura que la información quede almacenada correctamente en el Excel.

2. **Actualización de datos**  
   A partir del Excel, se obtienen los datos para actualizar el archivo:
----------------------------------------------------------------------------------------------------------------------------------------------

3. **Gestión de imágenes**  
- Las imágenes deben guardarse en:
  ```
  /assets/images/miembros/
  ```
- Se debe respetar el nombre original del archivo de la imagen.

4. **Actualización del archivo YAML**  
- Se deben añadir o actualizar los registros en:
  ```
  _data/miembros.yml
  ```
- Verificar que:
  - El campo `tipo` sea exactamente: `pregrado`, `posgrado` o `egresado`
  - La ruta de la imagen (`foto`) sea correcta
  - La sangría sea de 2 espacios (formato YAML válido)

---

### ⚠️ Consideraciones importantes

- Toda la información debe diligenciarse primero en el Forms.  
- No se recomienda editar directamente el YAML sin pasar por el Excel.  
- Errores en el campo `tipo` o en la ruta de la imagen impedirán que el miembro se visualice correctamente en la página.

---

### 🚀 Buenas prácticas

- Mantener el Excel actualizado antes de modificar el YAML  
- Verificar rutas de imágenes antes de hacer commit  
- Evitar registros duplicados  
- Revisar la página después de cada cambio  

---