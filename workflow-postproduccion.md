# Flujo de Trabajo y Arquitectura de Postproducción: Proyecto "Desafiar o tempo"

**Autor:** Santiago M. Andrade  
**Categoría:** Documentación de Procesos / Pipeline de Postproducción  
**Nivel:** Avanzado  

## 1. Resumen Ejecutivo
Este documento detalla la arquitectura de almacenamiento, las convenciones de nomenclatura y los protocolos de transferencia de datos (Data Management) implementados para la postproducción del proyecto. El objetivo es garantizar la integridad del material, estandarizar el flujo de trabajo entre departamentos (Edición, Color, Sonido) y asegurar la interoperabilidad entre los diferentes softwares utilizados.

## 2. Configuración Técnica Inicial y Metadatos
Para garantizar la sincronización y el correcto ensamblaje del material, se establecieron las siguientes especificaciones por cámara:

| Cámara | Modelo | FPS (Frames per second) |
| :--- | :--- | :--- |
| **Cam A** | Sony FS5 | 23.976 / 59.94 fps |
| **Cam B** | BMPCC | 24 fps |
| **Cam C** | Sony A7III | XAVC (FPS variable) |

### 2.1. Convención de Nomenclatura (File Naming Convention)
Para evitar colisiones de nombres en los programas de edición y facilitar la trazabilidad, se aplicó un estándar de renombrado a los clips de las cámaras A y C.

*   **Formato original:** `Clip0006.MXF`
*   **Formato estandarizado:** `A25 03 21 Clip0006.MXF`

**Estructura del identificador:**
*   **Carácter 1:** Identificador de cámara (Ej. `A` para Cam A).
*   **Dígitos 2-3:** Año de grabación.
*   **Dígitos 4-5:** Mes de grabación.
*   **Dígitos 6-7:** Día de grabación.
<img width="473" height="134" alt="Captura de pantalla 2026-10-21 a la(s) 10 56 29 a m" src="https://github.com/user-attachments/assets/f66cc8f9-ded5-4ab6-9839-9d0f35ac9288" />


## 3. Arquitectura de Almacenamiento (Data Governance)
El resgualdo del material se gestiona mediante una estrategia de redundancia (Backup) utilizando dos discos duros de 2 TB y un servidor centralizado **TrueNAS**.

### 3.1. Estructura de Directorios
Para estandarizar la entrega de copias y el acceso del equipo, se definió la siguiente jerarquía de carpetas en la raíz del proyecto:

```text
/
├── 01_DOCS
├── 02_MATERIAL
│   ├── FOTOS
│   ├── HABANA 24-06-23
│   ├── IMG
│   ├── INVESTIGACION
│   ├── PLANTILLAS
│   └── SON
├── 03_PROXYS
├── 04_PROYECTOS
├── 05_INTERCAMBIOS
├── 06_LEADERS_CRDTS
├── 07_MASTER
└── 08_EXTRAS

## 4. Procedimiento de Respaldo (Clonado)

Para asegurar la integridad del material, el clonado se realizará utilizando la herramienta **Clone Tool** de DaVinci Resolve.

1. Abrir la pestaña de **Media Storage** y localizar los archivos originales.
2. Seleccionar la carpeta de origen y arrastrarla al campo **Source**.
3. Seleccionar el destino en el servidor o disco de respaldo y arrastrarlo al campo **Destination**. *(Es posible añadir múltiples destinos simultáneos para redundancia).*
4. Hacer clic en **Add Job**.
5. Ejecutar el proceso haciendo clic en **Clone** y esperar la verificación de checksums.

---

## 5. Especificaciones de Entregables (Deliverables)

El flujo de postproducción requiere la exportación de material para tres áreas específicas. Es obligatorio solicitar a cada departamento una confirmación (referencia) del material recibido para validar la transferencia.

### A. Color (DaVinci Resolve)
* **Referencia de corte:** Apple ProRes 422 Proxy.
* **Nota:** Incluir referencias de efectos pre-renderizados (quemados) en el video.

### B. Sonido (Pro Tools)
* **Referencia de corte:** Video con codec ligero.
* **Archivos de proyecto:** Medias de audio sincronizadas.
* **Configuración:** Exportación AAF (Embedded y Link to).

### C. Conformado
* **Referencia de corte:** Apple ProRes 422 Proxy.
* **Configuración:** Exportación AAF para reconstrucción del timeline.

> ⚠️ **Protocolo de QA:** Es responsabilidad del DIT verificar que los codecs, resoluciones, frame rates y timecodes coincidan entre el material original y los archivos de intercambio (AAF/Proxies).
