![Logo ReCoders](assets/logoReCoders.png)

# ReCoders Academy — Desafío de automatización con Bash

**Autor: Felipe Kessi Bustos · ReCoders® 2026**

Este laboratorio combina una academia online ficticia con tres misiones de un escape room. El estudiante se conecta por SSH a una instancia de Amazon Linux y desarrolla un script Bash que crea lotes de 25 archivos vacíos, continuando la numeración desde el mayor número existente.

Cada archivo representa un cupo simbólico de la academia. La actividad no crea cuentas de estudiantes ni inscripciones reales. El prefijo utilizado es `Alumno`: `Alumno1`, `Alumno2` y así sucesivamente, sin extensión.

## Los tres documentos

| Documento | Destinatario | Contenido y uso |
| --- | --- | --- |
| [01 · Guía del estudiante](01GuiaEstudiante.md) | Estudiante | Desafío paso a paso, preparación del entorno, pistas progresivas, pruebas y evidencias que debe reunir. No incluye el script resuelto. |
| [02 · Informe del alumno](02Documentacion.md) | Estudiante y docente | Registro de la ejecución realizada, redactado desde la perspectiva del alumno, con 14 capturas entre los pasos y resultados observados. |
| [03 · Guía docente](03GuiaDocente.md) | Docente o facilitador | Orientaciones para conducir la actividad, tiempos sugeridos, preguntas, solución de referencia explicada y criterios de revisión. |

## Objetivo del laboratorio

Construir y comprobar una automatización que:

- Cree exactamente 25 archivos vacíos por ejecución.
- Use nombres con el patrón `Alumno` seguido de un número.
- Comience en 1 cuando el destino esté vacío.
- Busque el mayor sufijo numérico existente y continúe desde el siguiente.
- Calcule el rango automáticamente, conservando los archivos anteriores.
- Permita verificar nombres, cantidad y tamaño mediante la terminal.

El tamaño del lote puede fijarse en 25. Los números inicial y final deben calcularse, sin modificar el script entre ejecuciones.

## Las tres misiones

| Puerta | Situación inicial | Resultado que permite validarla |
| --- | --- | --- |
| 1 · Abre la academia | Directorio `cupos` vacío | `Alumno1` a `Alumno25`: 25 archivos de 0 bytes. |
| 2 · Recibe otra cohorte | Los primeros 25 archivos ya existen | Nuevo lote `Alumno26` a `Alumno50`: 50 archivos en total, todos vacíos. |
| 3 · Supera la auditoría | Directorio separado con `Alumno1`, `Alumno3` y `Alumno7` | Nuevo lote `Alumno8` a `Alumno32`: 28 archivos en total, todos vacíos. |

La tercera misión es una extensión didáctica del desafío original. Permite comprobar que el script busca el máximo y no se limita a contar archivos. Los números faltantes anteriores al máximo no se rellenan.

## Cómo utilizar el material

1. **Para realizar el desafío**, comienza con la [guía del estudiante](01GuiaEstudiante.md). Predice cada resultado antes de ejecutar y guarda las evidencias indicadas.
2. **Para preparar una clase**, revisa la [guía docente](03GuiaDocente.md). Comparte primero la guía del estudiante y reserva la solución para la revisión o el cierre de la actividad.
3. **Para revisar un ejemplo documentado**, consulta el [informe del alumno](02Documentacion.md). Sus capturas corresponden a la ejecución registrada; cada estudiante debe aportar las de su propio trabajo.

El informe y la guía docente contienen la solución. Para conservar el carácter de desafío, evita consultarlos antes de desarrollar tu propuesta.

## Entorno y organización

Se utiliza la instancia de Amazon Linux y las credenciales SSH proporcionadas por el laboratorio del curso. Se requieren nociones previas de terminal, rutas, variables, bucles y edición de archivos. La guía incluye acceso desde macOS o Linux y una orientación para Windows con PuTTY.

El tiempo orientativo es de **55 minutos**:

| Etapa | Tiempo sugerido |
| --- | --- |
| Acceso y preparación | 10 minutos |
| Diseño y programación | 20 minutos |
| Pruebas de las tres puertas | 15 minutos |
| Evidencias, reflexión y cierre | 10 minutos |

La dinámica usa predicción, ejecución, observación y explicación. Un tablero con las columnas **Pendiente → En curso → Validado** permite registrar el avance de cada misión. Cada puerta se valida con evidencia técnica y una explicación del resultado.

## Qué demuestra el informe resuelto

Las capturas muestran la conexión SSH, la creación del directorio, la escritura y edición del script, la comprobación de sintaxis y las tres pruebas. Se documenta el cambio del prefijo `Felipe` a `Alumno` antes de las ejecuciones mostradas, así como los conteos de **25, 50 y 28 archivos**, todos vacíos.

La última captura acredita la salida de SSH mediante `exit`. No muestra la acción **End Lab** de la plataforma. Tampoco se atribuyen al alumno predicciones, uso del tablero o reflexiones personales que no fueron aportadas.

## Estructura de archivos

```text
.
├── README.md
├── 01GuiaEstudiante.md
├── 02Documentacion.md
├── 03GuiaDocente.md
└── assets/
    ├── logoReCoders.png
    └── capturas del laboratorio
```

## Publicación en GitHub

Descomprime el paquete y sube su contenido manteniendo los cuatro archivos Markdown y la carpeta `images` en el mismo nivel. Los enlaces entre documentos y las imágenes utilizan rutas relativas y funcionarán con esta estructura.

Las capturas están intercaladas en los pasos del informe. Conserva la carpeta `images` junto a los documentos para que GitHub pueda mostrarlas.

---

**Felipe Kessi Bustos · ReCoders® 2026**
