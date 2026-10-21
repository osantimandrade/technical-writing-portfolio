# Guía de configuración: Flujo de trabajo con Proxies en DaVinci Resolve

**Autor:** Santiago M. Andrade  
**Categoría:** Documentación técnica / Postproducción audiovisual  
**Nivel:** Intermedio  

## Introducción
En proyectos de edición con material de alta resolución (4K, 6K, RAW), la reproducción en la línea de tiempo puede volverse lenta, afectando la fluidez del trabajo. Una solución estándar en la industria es el uso de **proxies**: versiones de menor resolución y peso de los archivos originales que permiten editar con fluidez. 

Esta guía detalla el proceso paso a paso para generar proxies de manera automatizada en DaVinci Resolve, optimizando así el rendimiento de la estación de trabajo sin comprometer la calidad del resultado final.

## Requisitos previos
* Tener instalado DaVinci Resolve (versión gratuita o Studio).
* Contar con el material original importado en el explorador de medios del proyecto.

---

## Paso a paso para generar proxies

### Fase 1: Preparación del material
1. Localiza el material original en el **Explorador de Medios** de DaVinci Resolve.
2. Selecciona las carpetas o archivos correspondientes y arrástralos hacia el contenedor principal denominado **Master**.
   * *Nota:* Deberías ver una estructura de árbol con tus carpetas en el panel de medios.

### Fase 2: Creación de la línea de tiempo (Timeline)
1. Haz clic derecho sobre la carpeta que acabas de mover a "Master".
2. Selecciona la opción **Create New Timeline Using Selected Bin...** (Crear nueva línea de tiempo usando el contenedor seleccionado).
3. En la ventana emergente, asigna un nombre a la línea de tiempo (se recomienda usar el mismo nombre de la carpeta para mantener el orden).
4. Haz clic en **Create** (Crear).

### Fase 3: Configuración de la exportación (Render)
1. Dirígete a la página de **Deliver** (Entrega) haciendo clic en el ícono correspondiente en la parte inferior de la pantalla.
2. En el panel de configuración de Render, selecciona la ubicación de destino (Location) haciendo clic en **Browse**. 
   * *Recomendación:* Crea una carpeta específica para los proxies (ej. `Proxy_ProyectoX`) para mantener los archivos organizados.
3. En la sección de renderizado, selecciona la opción **Individual clips** (Clips individuales). 
   * *Verificación:* Asegúrate de que la línea de selección esté resaltada en amarillo.

### Fase 4: Ajustes de formato del Proxy
Configura los siguientes parámetros para garantizar un rendimiento óptimo:

* **Format (Formato):** `QuickTime` o `MXF OP-Atom` (según la preferencia de tu flujo de trabajo).
* **Codec (Códec):** `DNxHR`.
* **Type (Tipo):** `DNxHR LB` (Low Bandwidth). *Esta opción genera archivos de menor peso, ideales para edición ágil.*
* **Resolution (Resolución):** `1280 x 720 HD 720P`.
* **Render timeline effects:** Desmarcar esta casilla (los proxies no necesitan efectos pre-renderizados).
* Deja el resto de los parámetros (Frame rate, Data Levels, etc.) tal como están por defecto.

### Fase 5: Ejecución y vinculación
1. Haz clic en **Add to Render Queue** (Agregar a la cola de renderizado).
2. En la esquina superior derecha, verifica que el trabajo esté en la lista y haz clic en **Render All** (Renderizar todo).
3. Una vez finalizado el proceso, DaVinci Resolve vinculará automáticamente los proxies a los archivos originales, permitiéndote editar con fluidez y renderizar el proyecto final con la máxima calidad original.

---
*Fin del documento.*
