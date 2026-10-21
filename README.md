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
<img width="2672" height="1522" alt="Captura de pantalla 2026-03-07 a la(s) 8 22 45 p m" src="https://github.com/user-attachments/assets/f786d7eb-cf8d-4111-a4de-a4948d62ec08" />

2. Selecciona las carpetas o archivos correspondientes y arrástralos hacia el contenedor principal denominado **Master**.
<img width="399" height="253" alt="v master" src="https://github.com/user-attachments/assets/4909bb16-5eba-4d0c-b16b-6da250b61db0" />

   * *Nota:* Deberías ver una estructura de árbol con tus carpetas en el panel de medios.

### Fase 2: Creación de la línea de tiempo (Timeline)
1. Haz clic derecho sobre la carpeta que acabas de mover a "Master".
2. Selecciona la opción **Create New Timeline Using Selected Bin...** (Crear nueva línea de tiempo usando el contenedor seleccionado).
<img width="396" height="290" alt="Create New Timeline Using Selected Bin" src="https://github.com/user-attachments/assets/c4a3eaf3-0969-47f6-b043-17423442ac4e" />

3. En la ventana emergente, asigna un nombre a la línea de tiempo (se recomienda usar el mismo nombre de la carpeta para mantener el orden).
<img width="546" height="312" alt="Create New Timeline" src="https://github.com/user-attachments/assets/82a0e254-e74c-4a2f-8aa6-437a8214650a" />

4. Haz clic en **Create** (Crear).

### Fase 3: Configuración de la exportación (Render)
1. Dirígete a la página de **Deliver** (Entrega) haciendo clic en el ícono correspondiente en la parte inferior de la pantalla.
<img width="1439" height="674" alt="Captura de pantalla 2026-03-07 a la(s) 8 59 24 p m" src="https://github.com/user-attachments/assets/27557c9b-e65e-469a-a587-029ef4510909" />

2. En el panel de configuración de Render, selecciona la ubicación de destino (Location) haciendo clic en **Browse**. 
   * *Recomendación:* Crea una carpeta específica para los proxies (ej. `Proxy_ProyectoX`) para mantener los archivos organizados.
3. En la sección de renderizado, selecciona la opción **Individual clips** (Clips individuales). 
<img width="1439" height="674" alt="Captura de pantalla 2026-03-07 a la(s) 8 59 24 p m" src="https://github.com/user-attachments/assets/d3423844-64bd-4d0f-a8e7-c8008242eb49" />

<img width="578" height="490" alt="01000000" src="https://github.com/user-attachments/assets/2b517213-d4e1-4314-a290-fbfaea939f77" />
   * *Verificación:* Asegúrate de que la línea de selección esté resaltada en amarillo.

### Fase 4: Ajustes de formato del Proxy
Configura los siguientes parámetros para garantizar un rendimiento óptimo:

* **Format (Formato):** `MXF OP-Atom` (según la preferencia de tu flujo de trabajo).
<img width="439" height="314" alt=" Export Video" src="https://github.com/user-attachments/assets/1bd1ca7d-0999-45a2-aec7-2015aee82b98" />

* **Codec (Códec):** `Avid DNxHR`.
<img width="441" height="265" alt="Export Video" src="https://github.com/user-attachments/assets/5c608a94-e48c-4ca1-9921-923b1719e271" />

* **Type (Tipo):** `DNxHR LB` (Low Bandwidth). *Esta opción genera archivos de menor peso, ideales para edición ágil.*
<img width="436" height="287" alt=" Export Video" src="https://github.com/user-attachments/assets/76a81009-5212-4077-8f9e-3a0afeb682cc" />

* **Resolution (Resolución):** `1280 x 720 HD 720P`.
<img width="440" height="393" alt=" Export Video" src="https://github.com/user-attachments/assets/6e844ebf-498e-4f43-bd8a-50afa281ab91" />

* **Render timeline effects:** Desmarcar esta casilla (los proxies no necesitan efectos pre-renderizados).
* Deja el resto de los parámetros (Frame rate, Data Levels, etc.) tal como están por defecto.

### Fase 5: Ejecución y vinculación
1. Haz clic en **Add to Render Queue** (Agregar a la cola de renderizado).
<img width="450" height="1340" alt="Captura de pantalla 2026-03-07 a la(s) 10 06 19 p m" src="https://github.com/user-attachments/assets/6376c4a8-7c90-4200-b11b-169390173c97" />

2. En la esquina superior derecha, verifica que el trabajo esté en la lista y haz clic en **Render All** (Renderizar todo).
<img width="1920" height="1080" alt="Captura de pantalla 2026-10-21 a la(s) 10 34 18 a m  copia" src="https://github.com/user-attachments/assets/719fa666-4fb0-4c73-ae4b-a64da4c59040" />

3. Una vez finalizado el proceso, DaVinci Resolve vinculará automáticamente los proxies a los archivos originales, permitiéndote editar con fluidez y renderizar el proyecto final con la máxima calidad original.

---
*Fin del documento.*
