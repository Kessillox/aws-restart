[Volver al README](README.md)

![Logo ReCoders](assets/logoReCoders.png)

# Desafío ReCoders Academy

Guía del estudiante • Misión apertura del aula online

Autoría: Felipe Kessi Bustos • ReCoders® 2026

Estudiante: ____________________    Fecha: ____________________

### Tu misión

La academia está por abrir un curso online. Cada nueva cohorte necesita 25 cupos simbólicos, representados por archivos vacíos. Eres responsable de automatizar su preparación en Amazon Linux y demostrar que la numeración continúa sin repetir identificadores.

Supera tres puertas: abre la academia, recibe otra cohorte y resuelve una auditoría con números faltantes. Las puertas se abren cuando puedes mostrar y explicar la evidencia técnica. Los archivos representan cupos; no crean cuentas ni inscripciones reales.

### Qué debes construir

Un script Bash llamado crear_cupos.sh que cree exactamente 25 archivos vacíos por ejecución. Sus nombres deben usar el prefijo Alumno, con mayúscula inicial, seguido de un número y sin extensión: Alumno1, Alumno2 y así sucesivamente.

El script debe buscar el número máximo existente y comenzar en el siguiente. Si no hay archivos válidos, debe empezar en 1. No escribas manualmente los 25 nombres ni cambies el inicio del lote entre ejecuciones. Conserva los archivos anteriores.

Para poder usar el mismo script en la auditoría, recibe el directorio de destino como primer argumento. Mantén el script fuera de ese directorio. Esta condición organiza la actividad adicional y permite probarla sin alterar las cohortes.

### Organiza tu desafío

Tiempo orientativo: 55 minutos. Dedica 10 al acceso, 20 al desarrollo, 15 a las pruebas y 10 al registro y cierre. La auditoría es una extensión creativa del laboratorio original.

Dibuja tres columnas: Pendiente, En curso y Validado. Añade una tarjeta por puerta. Antes de cada prueba, escribe tu predicción; después ejecuta, observa y explica. Mueve una tarjeta a Validado sólo al cumplir sus criterios.

## 1 Accede y prepara tu espacio

1. Selecciona Start Lab en la plataforma. Espera Lab status: ready y cierra el panel. Abre AWS desde el enlace del laboratorio. Utiliza la instancia y las credenciales proporcionadas por la actividad.

### Conexión desde macOS o Linux

2. En Details → Show, descarga labsuser.pem y anota PublicIP. Cierra el panel. Abre una terminal local y entra en la carpeta donde guardaste la clave. Si está en Descargas:

```bash
cd ~/Downloads
chmod 400 labsuser.pem
ssh -i labsuser.pem ec2-user@PUBLIC_IP
```

Sustituye PUBLIC_IP por la dirección del laboratorio. Confirma la primera conexión con yes cuando corresponda. La clave permite autenticarte sin una contraseña de usuario.

### Alternativa desde Windows

Descarga labsuser.ppk desde Details → Show y anota PublicIP. Usa PuTTY y la guía de conexión enlazada en las instrucciones originales del laboratorio. Configura la IP de la instancia y la clave PPK e inicia sesión como ec2-user. Una vez conectado, sigue los mismos pasos remotos de esta guía.

Evidencia 1. Guarda la conexión SSH establecida como 01-conexion.png. No muestres el contenido de tu clave privada. Inserta tu captura aquí al completar este paso.

### Prepara los directorios en Amazon Linux

3. A partir de este punto, trabaja en la terminal SSH de la instancia. Ejecuta:

```bash
mkdir -p ~/recoders-academy/cupos
cd ~/recoders-academy
pwd
ls -la cupos
```

Comprueba que cupos esté vacío antes de la primera misión. Si ya contiene archivos de otro intento, conserva esa carpeta y prepara otra vacía. Usa su ruta en lugar de cupos durante las dos primeras puertas.

Guarda crear_cupos.sh dentro de recoders-academy, no dentro de cupos. Así, el conteo de la misión incluirá únicamente los archivos que representan cupos.

Evidencia 2. Guarda la ubicación de trabajo y el estado inicial del directorio como 02-directorio.png. Inserta tu captura aquí al completar este paso.

## 2 Diseña y programa tu solución

4. Antes de escribir código, completa el plan siguiente con tus propias palabras. Puedes anotarlo en tu cuaderno o en un archivo fuera de cupos.

Entrada: ¿qué dato recibe el script?  
Búsqueda: ¿cómo reconocerás los archivos AlumnoN?  
Decisión: ¿cómo encontrarás el número más alto?  
Creación: ¿cómo generarás los 25 nombres siguientes?  
Comprobación: ¿cómo demostrarás que los archivos están vacíos?

### Construye una primera versión

5. Usa el editor de terminal practicado en el curso para crear crear_cupos.sh. Si utilizas vi, abre el archivo con el comando siguiente, pulsa i para escribir y, al terminar, pulsa Esc y escribe :wq seguido de Enter para guardar y salir.

```bash
vi crear_cupos.sh
```

Tu solución debe recibir la ruta de destino como primer argumento, reconocer nombres formados por Alumno y un número, calcular el máximo y crear el siguiente lote con touch. No uses el conteo total de archivos como sustituto del máximo.

Puedes fijar el tamaño del lote en 25 porque es un requisito. Los límites de la numeración deben calcularse automáticamente. Usa el mismo código para las tres puertas y ejecuta una sola copia a la vez.

### Pistas progresivas

Pista 1. Separa el problema en dos recorridos: uno para inspeccionar lo que existe y otro para crear lo que falta en el nuevo lote.

Pista 2. Parte de un máximo igual a 0. Compara cada sufijo numérico válido con el máximo guardado. Ignora nombres ajenos al patrón AlumnoN.

Pista 3. En Bash, $1 permite acceder al primer argumento. Las comparaciones numéricas y un bucle te permitirán recorrer el rango. Usa comillas alrededor de las rutas.

Pista 4. El inicio es máximo + 1 y el final es máximo + 25. touch crea un archivo vacío cuando ese nombre todavía no existe. No necesitas escribir los 25 comandos por separado.

### Revisa antes de ejecutar

6. Comprueba la sintaxis. Si aparece un error, corrígelo antes de abrir la primera puerta. Una comprobación sin mensajes no demuestra aún que la lógica sea correcta.

```bash
bash -n crear_cupos.sh
cat crear_cupos.sh
```

Evidencia 3. Guarda el código legible y la revisión de sintaxis como 03-script.png. Usa varias capturas si es necesario. Inserta tu captura aquí al completar este paso.

## 3 Abre la academia y recibe otra cohorte

### Puerta 1 Abre la academia

7. Predice el primer nombre, el último y la cantidad de archivos al ejecutar sobre cupos vacío. Registra tu respuesta antes de continuar.

```bash
bash crear_cupos.sh "$HOME/recoders-academy/cupos"
ls -lv cupos
find cupos -maxdepth 1 -type f | wc -l
find cupos -maxdepth 1 -type f ! -size 0c -print
```

Criterio de desbloqueo: deben existir exactamente Alumno1 a Alumno25, todos de 0 bytes. El conteo debe dar 25. El último comando no debe mostrar nombres, porque busca archivos que no están vacíos. Revisa también la columna de tamaño de ls -lv.

Evidencia 4. Guarda la primera ejecución y sus verificaciones como 04-primera-cohorte.png. Inserta tu captura aquí al completar este paso.

### Puerta 2 Recibe otra cohorte

8. Sin modificar el script ni vaciar cupos, predice qué debería cambiar en una segunda ejecución. Repite:

```bash
bash crear_cupos.sh "$HOME/recoders-academy/cupos"
ls -lv cupos
find cupos -maxdepth 1 -type f | wc -l
find cupos -maxdepth 1 -type f ! -size 0c -print
```

Criterio de desbloqueo: aparecen 25 archivos nuevos, Alumno26 a Alumno50, y permanecen los anteriores. Debe haber 50 archivos, todos vacíos. No cambies a mano el número inicial del script.

Evidencia 5. Guarda la segunda ejecución y sus verificaciones como 05-segunda-cohorte.png. Inserta tu captura aquí al completar este paso.

### Lee la evidencia

ls -lv muestra una lista larga ordenada por número en Amazon Linux. find selecciona archivos regulares del directorio y wc -l cuenta los resultados. Que la búsqueda de archivos no vacíos no muestre nada debe acompañarse del conteo y la revisión de nombres.

Si una lista no cabe en pantalla, toma capturas consecutivas. Para repetir una captura, ejecuta sólo los comandos de verificación: volver a ejecutar el script creará otro lote de 25.

## 4 Supera la auditoría de continuidad

9. La academia debe comprobar que tu automatización tolera números faltantes. Crea un entorno de prueba separado para conservar intacta la evidencia de las cohortes:

```bash
cd ~/recoders-academy
auditoria=$(mktemp -d "$HOME/recoders-academy/auditoria.XXXXXX")
touch "$auditoria/Alumno1" "$auditoria/Alumno3" \
    "$auditoria/Alumno7"
ls -lv "$auditoria"
```

mktemp crea un directorio con nombre único y guarda su ruta en la variable auditoria. Los tres archivos iniciales son la preparación de esta prueba adicional; no reemplazan la creación automática del lote.

Evidencia 6. Guarda el estado inicial de la auditoría como 06-auditoria-inicial.png. Inserta tu captura aquí al completar este paso.

### Predice y prueba

10. Hay tres archivos y el mayor sufijo es 7. Explica dónde debería comenzar el siguiente lote y por qué. Después usa el mismo script y conserva abierta esta sesión SSH para mantener la variable auditoria:

```bash
bash crear_cupos.sh "$auditoria"
ls -lv "$auditoria"
find "$auditoria" -maxdepth 1 -type f | wc -l
find "$auditoria" -maxdepth 1 -type f ! -size 0c -print
```

Criterio de desbloqueo: se crean Alumno8 a Alumno32. El total es 28 archivos: los tres iniciales y los 25 nuevos. Todos deben estar vacíos. No se deben rellenar los números faltantes anteriores a 7.

Evidencia 7. Guarda el resultado y las verificaciones como 07-auditoria-final.png. Inserta tu captura aquí al completar este paso.

### Si una puerta no se abre

Compara tu predicción con los nombres, la cantidad y el tamaño reales. Anota el error observado, qué parte del código lo explica y el cambio que hiciste. Si comenzaste en 4, revisa si confundiste cantidad de archivos con número máximo.

Después de corregir, repite la prueba en un directorio nuevo. Para repetir la auditoría, vuelve al paso 9; para reiniciar las dos primeras puertas, prepara otro destino vacío. Conserva las evidencias de tus intentos y distingue el resultado corregido.

## 5 Entrega y cierra el laboratorio

### Comprueba tu entrega

11. Antes de finalizar, verifica que tienes crear_cupos.sh, las capturas 01 a 07 y tus respuestas de predicción. Guarda las capturas en tu equipo, fuera del directorio cupos.

La entrega debe permitir comprobar los tres resultados: 25 archivos en la primera cohorte, 50 tras la segunda y 28 en la auditoría. Incluye la lista de nombres y el tamaño 0 bytes, además del conteo.

### Recupera el código antes de cerrar

En macOS o Linux, abre una segunda terminal local, entra en la carpeta de tu clave y copia el script. Sustituye PUBLIC_IP. Ejecuta estos comandos en tu equipo, no en la sesión SSH:

```bash
cd ~/Downloads
scp -i labsuser.pem \
    ec2-user@PUBLIC_IP:~/recoders-academy/crear_cupos.sh \
    ./crear_cupos-entrega.sh
```

Comprueba que crear_cupos-entrega.sh esté guardado y contenga tu solución. Si usas Windows, conserva el archivo con el método de transferencia utilizado en el curso; también puedes copiar el texto mostrado por cat crear_cupos.sh a un archivo local .sh y comprobar su contenido.

### Reflexiona sobre tu solución

12. Responde brevemente con base en lo que observaste:  
• ¿Cómo encuentra tu script el máximo existente?  
• ¿Por qué tres archivos no implican que el siguiente número sea 4?  
• ¿Qué evidencia demuestra que cada ejecución añade 25 archivos vacíos?  
• ¿Qué corregiste o qué mejorarías en otro intento?

### Finaliza la sesión

13. Cuando hayas guardado tu entrega, ejecuta exit en la terminal SSH. En la plataforma, selecciona End Lab, confirma Yes y espera el mensaje que indica el inicio de la eliminación. Cierra el panel.

Evidencia 8. Guarda el cierre de la sesión y la finalización del laboratorio como 08-cierre.png; puedes usar dos capturas. Inserta tu captura aquí al completar este paso.

### Registro de aprendizaje

Puerta 1: __________    Puerta 2: __________    Puerta 3: __________  
Dificultad principal: __________________________________________  
Cómo la abordé: ______________________________________________  
Evidencia que respalda mi solución: _____________________________

Entrega tu código, las evidencias 01 a 08 y la reflexión. Describe únicamente lo que realizaste y observaste. Si no completaste una puerta, indica hasta dónde avanzaste y conserva la evidencia disponible.
