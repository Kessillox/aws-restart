# Laboratorio: 231-Lab - Edición de archivos

![Logo ReCoders](assets/logoReCoders.png)

**ReCoders® 2026 · Autor: Felipe Kessi Bustos**

> **Privacidad:** paquete para revisión personal. Las capturas originales contienen IP públicas y nombres del equipo. Difumina estos datos antes de subirlas a un repositorio público. No se incluye la clave privada.

## Ficha

| Campo | Detalle |
|---|---|
| Curso | AWS re/Start — Morris & Opazo |
| Módulo | Linux |
| Fecha de documentación | 2026-09-15 |
| Estado | Pendiente de validación integral |
| Duración estimada | 1 hora |
| Región AWS declarada | us-west-2 |
| Autor | Felipe Kessi Bustos |
| Material disponible | Seis fragmentos y 24 capturas |

## Alcance de la evidencia recibida

Se recibieron seis fragmentos, incluido el desafío adicional, y 24 capturas. No se contó con una guía descargable completa. No se recibieron los pasos 5-12. La evidencia muestra estados del editor y de la terminal; no permite verificar todas las teclas ejecutadas.

## Instrucciones originales recibidas

Registro resumido fiel al material pegado; no es una transcripción íntegra.

### Fragmento 1: Inicio del entorno

> Pasos 1-4: Start Lab, esperar Lab status: ready, abrir AWS y disponer la consola junto a la guía.

### Fragmento 2: Acceso desde macOS/Linux

> Pasos 13-20: Details > Show, descargar labsuser.pem, anotar PublicIP, entrar al directorio de la clave, aplicar chmod 400 y conectar por SSH; aceptar con yes la primera conexión.

### Fragmento 3: Tutorial de Vim

> Pasos 21-23: ejecutar vimtutor, completar lecciones 1-3 según el paso 22 y salir con :q!. Si falta Vim, la guía propone sudo yum install vim.

### Fragmento 4: Archivo helloworld

> Pasos 24-29: crear el archivo, insertar dos líneas, guardar con :wq, reabrir, agregar una tercera línea, salir con :q! y comparar.

### Fragmento 5: Desafío adicional

> Pasos 30-32: eliminar una línea con dd, deshacer con u y guardar sin salir con :w.

### Fragmento 6: Nano y finalización

> Pasos 33-39: crear cloudworld, escribir el texto indicado, guardar con Ctrl+O e Intro, salir con Ctrl+X, reabrir y finalizar con End Lab > Yes.

**Explicación complementaria:** el objetivo menciona `/var/log/secure`, pero la tarea recibida usa `cloudworld`. La introducción menciona tareas 1-4 de vimtutor, mientras el paso 22 pide lecciones 1-3. Estos puntos quedan pendientes de aclaración.

## Objetivo

Practicar Vim y nano, crear archivos, guardar contenido y reconocer la diferencia entre guardar y descartar cambios. El objetivo declarado sobre `/var/log/secure` no cuenta con instrucciones ni evidencia de ejecución.

## Criterios de éxito

- [x] Observar una conexión SSH a Amazon Linux 2.
- [x] Observar apertura y práctica de vimtutor.
- [x] Observar contenido de `helloworld` y `cloudworld`.
- [ ] Verificar toda la cobertura solicitada de vimtutor.
- [ ] Confirmar la secuencia de guardado y descarte de `helloworld`.
- [ ] Aclarar y verificar el objetivo de `/var/log/secure`.
- [ ] Confirmar End Lab.

## Conceptos y servicios

| Concepto | Función |
|---|---|
| Amazon EC2 | Servidor virtual del laboratorio |
| SSH | Conexión remota cifrada |
| Clave PEM | Archivo de autenticación usado con SSH |
| Vim | Editor con modos Normal e inserción |
| nano | Editor con escritura directa y atajos visibles |
| Buffer | Contenido en memoria antes de guardarlo |

## Relación con AWS Well-Architected

| Pilar | Práctica | Evidencia |
|---|---|---|
| Seguridad | Autenticación por clave; permisos restringidos previstos | E01; chmod no capturado |
| Excelencia operativa | Registrar y comparar resultados | E19-E24 |
| Optimización de costos | Finalizar el entorno con End Lab | Pendiente |

## Prerrequisitos

- Entorno activo y acceso al portal del laboratorio.
- Terminal macOS/Linux, clave `labsuser.pem` y dirección pública asignada.
- Instancia Command Host, según la guía.

## Arquitectura o flujo

```text
Terminal macOS → SSH → EC2 / Amazon Linux 2 → vimtutor / Vim / nano → archivos
```

## Procedimiento

### Acceso y tutorial

1-4. En el portal del laboratorio: Start Lab > esperar Lab status: ready > AWS.

Esperado: consola disponible y Command Host iniciado. Observado: no hay captura de consola.

13-16. Details > Show > Download PEM; anotar PublicIP y cerrar el panel.

17-20. Abrir terminal, entrar al directorio de la clave y ejecutar:

    cd ~/Downloads

    chmod 400 labsuser.pem

    ssh -i labsuser.pem ec2-user@<public-ip>

Aceptar con yes la primera conexión. -i selecciona la clave; ec2-user es el usuario remoto.

Observado: acceso a Amazon Linux 2 con ec2-user (E01 y E23). Directorio local visible: keys lab.

La IP se omite del texto como [REDACTADO]. No se evidencia la descarga ni chmod.

21-23. Ejecutar vimtutor. La guía propone sudo yum install vim solo si falta Vim.

Practicar las lecciones y salir con :q!. Observado: tutor abierto y ejercicios (E02-E18).

No se observa instalación de paquetes ni el comando exacto utilizado para salir.

Por qué: practicar sobre la copia temporal del tutor permite aprender sin editar archivos del sistema.

**Ruta:** portal del laboratorio o terminal SSH, según el paso. Las acciones descritas son las instrucciones; su ejecución se acredita únicamente con las evidencias indicadas.

### Archivo helloworld

24. Ejecutar vim helloworld para abrir o crear el archivo. Evidencia de aperturas: E20.

25. Pulsar i y escribir las dos líneas; pulsar Esc para regresar al modo Normal:

    Hello World!

    This is my first file in Linux and I am editing it in Vim!

26. Escribir :wq y pulsar Intro para guardar y salir; reabrir con vim helloworld.

27. En modo inserción, añadir: I learned how to create a file, edit and save them too!

28. Pulsar Esc, escribir :q! y pulsar Intro para descartar cambios sin guardar.

29. Reabrir el archivo y comparar su contenido.

Esperado: las primeras dos líneas permanecen; la tercera se descarta si no se guardó antes.

Observado: E19 muestra tres líneas; E21 muestra dos y :w escrito. E20 muestra reaperturas.

Límite: las capturas no prueban la secuencia exacta de guardado y descarte.

Respuesta a la guía: :wq escribe en disco y sale; :q! sale sin escribir los cambios pendientes.

30-32. Desafío: dd borra la línea actual; u deshace el cambio; :w guarda sin salir.

E21 muestra :w preparado, pero no la confirmación posterior del guardado ni dd/u en acción.

**Ruta:** portal del laboratorio o terminal SSH, según el paso. Las acciones descritas son las instrucciones; su ejecución se acredita únicamente con las evidencias indicadas.

### Nano y cierre

33. Ejecutar nano cloudworld desde la sesión remota.

34. Escribir directamente, sin entrar en un modo de inserción:

    We are using nano this time! We can simply start typing! No insert mode needed.

35. Pulsar Ctrl+O y luego Intro para confirmar el nombre y guardar.

36. Pulsar Ctrl+X para salir.

37. Ejecutar nano cloudworld de nuevo para revisar y salir.

Esperado: recuperar el texto guardado. Observado: E22 muestra cloudworld y "1 línea leída";

E23 y E24 muestran dos aperturas con nano cloudworld. Compatible con guardado y reapertura.

Por qué: reabrir verifica la persistencia del contenido, no solo su presencia en pantalla.

38-39. Según la guía: End Lab > Yes; esperar el aviso de eliminación y cerrar con X.

Observado: E24 muestra exit, logout y conexión SSH cerrada.

Pendiente: la finalización del entorno en el portal. Cerrar SSH no termina la instancia.

No se recibieron instrucciones operativas ni capturas de una copia de /var/log/secure.

**Ruta:** portal del laboratorio o terminal SSH, según el paso. Las acciones descritas son las instrucciones; su ejecución se acredita únicamente con las evidencias indicadas.

## Comandos utilizados

Comandos indicados por la guía; no todos cuentan con una captura de ejecución.

```bash
cd ~/Downloads
chmod 400 labsuser.pem
ssh -i labsuser.pem ec2-user@<public-ip>
vimtutor
# Solo si Vim no está instalado, según la guía:
sudo yum install vim
vim helloworld
nano cloudworld
# Salida SSH observada:
exit
```

| Comando o tecla | Función |
|---|---|
| `-i labsuser.pem` | Selecciona la clave SSH |
| `chmod 400` | Permite lectura al propietario de la clave |
| `i`, `Esc` | Entrar en inserción y regresar al modo Normal |
| `:wq` | Guardar y salir |
| `:q!` | Salir descartando cambios pendientes |
| `dd`, `u`, `:w` | Borrar línea, deshacer y guardar |
| `Ctrl+O`, `Intro` | Guardar y confirmar nombre en nano |
| `Ctrl+X` | Salir de nano |

## Validación final

| Validación | Evidencia | Estado |
|---|---|---|
| Conexión SSH | E01, E23, E24 | Observada |
| Práctica vimtutor | E02-E18 | Parcial; no acredita toda la cobertura |
| Contenido helloworld | E19-E21 | Observado; secuencia de descarte pendiente |
| cloudworld y reapertura | E22-E24 | Respaldada por texto y comandos visibles |
| Edición de /var/log/secure | Ninguna | Pendiente |
| Cierre SSH | E24 | Observado |
| End Lab | Ninguna | Pendiente |

## Problemas y solución

- **Síntoma:** E23 muestra un intento SSH interrumpido con Ctrl+C.
- **Causa:** no confirmada; no hay mensaje concluyente.
- **Recuperación observada:** conexión posterior a otra dirección y acceso a Amazon Linux 2.
- **Límite:** no se atribuye una causa de red o autenticación sin evidencia.
- **Práctica local:** E05-E07 corresponden a `archivo.txt` en macOS; no se presentan como ejecución en EC2.
- **Configuración:** la guía menciona `t3.micro`; no hay evidencia de consola que confirme el tipo o sus recursos.

## Seguridad y privacidad

- IP públicas y nombres del equipo están visibles en capturas originales: requieren difuminado antes de publicar.
- El texto usa `<public-ip>` o `[REDACTADO]`; no se incluye la clave privada.
- `chmod 400` se registra como instrucción, sin captura de su ejecución.

## Costos potenciales

| Recurso | Puede generar costo | Acción |
|---|---|---|
| EC2 y almacenamiento asociado | Sí, según el entorno | Finalizar conforme a la guía |

No se estiman importes porque no se dispone de facturación ni configuración verificadas.

## 🧹 Cleanup (Limpieza)

- [x] Cerrar SSH: observado en E24.
- [ ] Seleccionar End Lab > Yes y confirmar el aviso de eliminación.
- [ ] Conservar evidencia de finalización del portal.
- [ ] Revisar recursos residuales en us-west-2 si el entorno lo permite.

Cerrar SSH no termina la instancia ni sustituye End Lab.

![Descripción de lo que se debe capturar: [portal del laboratorio, End Lab, eliminación iniciada y mensaje de confirmación]]

## Evidencias

| ID | Archivo | Qué demuestra | Sanitizada |
|---|---|---|---|
| E01 | [Captura 01](assets/01.png) | Acceso SSH | Pendiente de revisión |
| E02 | [Captura 02](assets/02.png) | Inicio de vimtutor | Pendiente de revisión |
| E03 | [Captura 03](assets/03.png) | Lección 1.4: insertar | Pendiente de revisión |
| E04 | [Captura 04](assets/04.png) | Lección 1.5: añadir | Pendiente de revisión |
| E05 | [Captura 05](assets/05.png) | Práctica local: abrir archivo.txt | Pendiente de revisión |
| E06 | [Captura 06](assets/06.png) | Práctica local: contenido | Pendiente de revisión |
| E07 | [Captura 07](assets/07.png) | Práctica local: :wq preparado | Pendiente de revisión |
| E08 | [Captura 08](assets/08.png) | Operadores y movimientos | Pendiente de revisión |
| E09 | [Captura 09](assets/09.png) | Operadores y movimientos | Pendiente de revisión |
| E10 | [Captura 10](assets/10.png) | Contadores de movimiento | Pendiente de revisión |
| E11 | [Captura 11](assets/11.png) | Borrado con contador | Pendiente de revisión |
| E12 | [Captura 12](assets/12.png) | Deshacer y rehacer | Pendiente de revisión |
| E13 | [Captura 13](assets/13.png) | Pegar: líneas ordenadas | Pendiente de revisión |
| E14 | [Captura 14](assets/14.png) | Reemplazar: líneas coincidentes | Pendiente de revisión |
| E15 | [Captura 15](assets/15.png) | Resumen de lección 3 | Pendiente de revisión |
| E16 | [Captura 16](assets/16.png) | Lección 4.1: ubicación | Pendiente de revisión |
| E17 | [Captura 17](assets/17.png) | Estado mostrado con Ctrl+G | Pendiente de revisión |
| E18 | [Captura 18](assets/18.png) | Lección 4.1 e inicio de 4.2 | Pendiente de revisión |
| E19 | [Captura 19](assets/19.png) | helloworld con tres líneas | Pendiente de revisión |
| E20 | [Captura 20](assets/20.png) | Aperturas de helloworld | Pendiente de revisión |
| E21 | [Captura 21](assets/21.png) | helloworld con dos líneas | Pendiente de revisión |
| E22 | [Captura 22](assets/22.png) | cloudworld reabierto en nano | Pendiente de revisión |
| E23 | [Captura 23](assets/23.png) | Historial de comandos | Pendiente de revisión |
| E24 | [Captura 24](assets/24.png) | Salida de la sesión SSH | Pendiente de revisión |

### E01 — Acceso SSH

![Acceso SSH](assets/01.png)

Evidencia parcial: muestra el estado visible, no certifica acciones fuera de pantalla.

### E02 — Inicio de vimtutor

![Inicio de vimtutor](assets/02.png)

Evidencia parcial: muestra el estado visible, no certifica acciones fuera de pantalla.

### E03 — Lección 1.4: insertar

![Lección 1.4: insertar](assets/03.png)

Evidencia parcial: muestra el estado visible, no certifica acciones fuera de pantalla.

### E04 — Lección 1.5: añadir

![Lección 1.5: añadir](assets/04.png)

Evidencia parcial: muestra el estado visible, no certifica acciones fuera de pantalla.

### E05 — Práctica local: abrir archivo.txt

![Práctica local: abrir archivo.txt](assets/05.png)

Evidencia parcial: muestra el estado visible, no certifica acciones fuera de pantalla.

### E06 — Práctica local: contenido

![Práctica local: contenido](assets/06.png)

Evidencia parcial: muestra el estado visible, no certifica acciones fuera de pantalla.

### E07 — Práctica local: :wq preparado

![Práctica local: :wq preparado](assets/07.png)

Evidencia parcial: muestra el estado visible, no certifica acciones fuera de pantalla.

### E08 — Operadores y movimientos

![Operadores y movimientos](assets/08.png)

Evidencia parcial: muestra el estado visible, no certifica acciones fuera de pantalla.

### E09 — Operadores y movimientos

![Operadores y movimientos](assets/09.png)

Evidencia parcial: muestra el estado visible, no certifica acciones fuera de pantalla.

### E10 — Contadores de movimiento

![Contadores de movimiento](assets/10.png)

Evidencia parcial: muestra el estado visible, no certifica acciones fuera de pantalla.

### E11 — Borrado con contador

![Borrado con contador](assets/11.png)

Evidencia parcial: muestra el estado visible, no certifica acciones fuera de pantalla.

### E12 — Deshacer y rehacer

![Deshacer y rehacer](assets/12.png)

Evidencia parcial: muestra el estado visible, no certifica acciones fuera de pantalla.

### E13 — Pegar: líneas ordenadas

![Pegar: líneas ordenadas](assets/13.png)

Evidencia parcial: muestra el estado visible, no certifica acciones fuera de pantalla.

### E14 — Reemplazar: líneas coincidentes

![Reemplazar: líneas coincidentes](assets/14.png)

Evidencia parcial: muestra el estado visible, no certifica acciones fuera de pantalla.

### E15 — Resumen de lección 3

![Resumen de lección 3](assets/15.png)

Evidencia parcial: muestra el estado visible, no certifica acciones fuera de pantalla.

### E16 — Lección 4.1: ubicación

![Lección 4.1: ubicación](assets/16.png)

Evidencia parcial: muestra el estado visible, no certifica acciones fuera de pantalla.

### E17 — Estado mostrado con Ctrl+G

![Estado mostrado con Ctrl+G](assets/17.png)

Evidencia parcial: muestra el estado visible, no certifica acciones fuera de pantalla.

### E18 — Lección 4.1 e inicio de 4.2

![Lección 4.1 e inicio de 4.2](assets/18.png)

Evidencia parcial: muestra el estado visible, no certifica acciones fuera de pantalla.

### E19 — helloworld con tres líneas

![helloworld con tres líneas](assets/19.png)

Evidencia parcial: muestra el estado visible, no certifica acciones fuera de pantalla.

### E20 — Aperturas de helloworld

![Aperturas de helloworld](assets/20.png)

Evidencia parcial: muestra el estado visible, no certifica acciones fuera de pantalla.

### E21 — helloworld con dos líneas

![helloworld con dos líneas](assets/21.png)

Evidencia parcial: muestra el estado visible, no certifica acciones fuera de pantalla.

### E22 — cloudworld reabierto en nano

![cloudworld reabierto en nano](assets/22.png)

Evidencia parcial: muestra el estado visible, no certifica acciones fuera de pantalla.

### E23 — Historial de comandos

![Historial de comandos](assets/23.png)

Evidencia parcial: muestra el estado visible, no certifica acciones fuera de pantalla.

### E24 — Salida de la sesión SSH

![Salida de la sesión SSH](assets/24.png)

Evidencia parcial: muestra el estado visible, no certifica acciones fuera de pantalla.

## Aprendizajes

- Vim separa navegación y escritura mediante modos.
- Guardar escribe en disco; salir sin guardar descarta los cambios pendientes.
- Nano permite escribir directamente; reabrir ayuda a comprobar persistencia.
- Las capturas deben interpretarse con sus límites y contexto.

## Fuentes

- Seis fragmentos del laboratorio pegados por el estudiante y 24 capturas.
- Material AWS «Edición de archivos», con aviso de copyright 2024.
- Plantilla de laboratorio y logo proporcionados en el proyecto AWS Restart.
- Documentación elaborada el 2026-09-15, sin consulta web.

## Pendientes del estudiante

- Confirmar End Lab.
- Aclarar el objetivo de `/var/log/secure` y la cobertura de vimtutor.
- Confirmar la secuencia `:wq` / `:q!` si se requiere acreditación completa.
- Difuminar IP y nombres del equipo en las capturas antes de publicar.
