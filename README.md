# Autosy (Autopsia de Memoria o Disco)
Recuperar archivos borrados de memorias y discos usando herramientas forenses.

Este tutorial describe cómo usar Autopsy para recuperar archivos borrados de memorias y discos en un entorno Linux. Sigue los pasos a continuación para crear una imagen de la memoria o disco y analizarla con Autopsy.

## Paso 1: Ubicar la memoria o disco en Linux
Primero, abre una terminal y ejecuta el siguiente comando para listar los dispositivos conectados:

```bash
sudo lsblk
```

Esto te mostrará una lista de dispositivos, ayudándote a identificar el identificador de tu memoria o disco, que tendrá una ruta como /dev/sdX.

## Paso 2: Crear una imagen del dispositivo
Una vez que hayas identificado tu dispositivo, crea una imagen con el siguiente comando:


```bash
sudo dd if=/dev/sdX of=/home/usuario/mi_imagen.iso bs=4M status=progress
```
- **dd**: Es el comando utilizado para crear la imagen.
- **if=/dev/sdX**: Especifica la ruta del dispositivo de origen.
- **of=/home/usuario/mi_imagen.iso**: Define la ruta y nombre del archivo de imagen que se va a crear.
- **bs=4M**: Establece el tamaño de los bloques para un proceso más rápido.
- **status=progress**: Muestra el progreso de la operación.

## Paso 3: Iniciar Autopsy
Abre una nueva terminal y ejecuta:

```bash
sudo autopsy
```
Introduce tu contraseña cuando se te solicite. Autopsy iniciará y te proporcionará un enlace, como **http://localhost:9999/autopsy**. Ábrelo en tu navegador.

## Paso 4: Crear un nuevo caso en Autopsy
- En la página principal de Autopsy, haz clic en "New Case".
- Completa los siguientes campos:
- **Case Name**: Nombre del caso.
- **Description (Opcional)**: Descripción del caso.
- **Investigator Name**: Nombre(s) del investigador(es).
- Haz clic en "Next" para continuar.

## Paso 5: Añadir un host
Haz clic en "Add Host".
Deja las opciones por defecto y haz clic en "Add Host".

## Paso 6: Añadir la imagen
- Haz clic en "Add Image".
- Selecciona la opción "Add Image File".
- Completa los siguientes campos:
-Location: Especifica la ruta de la imagen que creaste previamente (por ejemplo, /home/usuario/mi_imagen.iso).
### Type:
- Si es memoria: selecciona "Partition".
- Si es disco completo: selecciona "Disk".
- Import Method: Selecciona "Symlink".
- Haz clic en "Next".

## Paso 7: Configurar opciones adicionales
En la siguiente pantalla, deja todo por defecto.
Si necesitas calcular un hash para la investigación, hazlo antes y agrégalo aquí.
Haz clic en "Add".

## Paso 8: Confirmar la imagen añadida
Revisa la información mostrada y haz clic en **"OK"**.

## Paso 9: Montar y analizar la imagen
Con la imagen montada, haz clic en "Analyze".
En la nueva pantalla, selecciona "File Analysis" para comenzar el análisis.

### ¡Felicidades! Ahora Autopsy mostrará toda la información recuperada de la imagen.


