# Transferencia de archivos en Unix

## `rsync`

El comando rsync de Linux transfiere y sincroniza archivos o directorios de manera eficiente entre una máquina local, un servidor remoto o cualquiera de estos. Incluso si se pierde la conexión durante la transferencia, esta herramienta continuará exactamente donde se quedó, una vez que se restablezca la conexión.

La sintaxis básica es: `rsync [optional modifiers] [SRC] [DEST]`

### Opciones

Los comandos más comunes que se usan con rsync son:

- `-a`, `--archive`: habilita el modo de archivo (no solo copia los archivos, sino que también copia los permisos, los tiempos de modificación y cualquier otra fecha).

- `-v`, `--verbose`: brinda una salida visual que muestra el progreso del proceso.

- `-h`, `--human-readable format`: genera en un formato legible para humanos.

- `-z`, `--compress`: comprime los datos del archivo durante la transferencia.

- `-r`: copiar datos de forma recursiva

- `--dry-run` (o `-n`): hace que rsync realice una ejecución de prueba que no haga ningún cambio

- `--exclude=file1, file2`: permite excluir archivos o subdirectorios específicos cuando sincronizas dos carpetas. Para especificar más de un archivo, deben ir serparados por una coma.

### Links

- [rsync(1) - Linux Man page](https://linux.die.net/man/1/rsync)
- [Comando Rsync de Linux (sincronización remota)](https://www.hostinger.es/tutoriales/rsync-linux)


## `scp`

El comando **scp (Secure Copy)** en Linux y Unix se utiliza para transferir archivos entre hosts a través del protocolo SSH.

Los nombres de archivo pueden contener una especificación de usuario y host para indicar que el archivo debe copiarse a/desde ese host. Los nombres de archivos locales se pueden hacer explícitos usando nombres de ruta absolutos o relativos para evitar que scp trate los nombres de archivos que contienen ':' como especificadores de host. También se permiten copias entre dos hosts remotos.

Al copiar un archivo de origen a un archivo de destino que ya existe, scp reemplazará el contenido del archivo de destino (manteniendo el inodo).

Si el archivo de destino aún no existe, se crea un archivo vacío con el nombre del archivo de destino y luego se rellena con el contenido del archivo de origen.

La sintaxis de este comando es: `scp [other options] [source username@IP]:/[directory and file name] [destination username@IP]:/[destination directory]`


- `[other options]` son las opciones del comando.
- `[source username@IP]` es el nombre de usuario y la IP de la máquina que tiene el archivo que deseas.
- `:/` informa al comando SCP que estás a punto de escribir en el directorio de origen
- `[directory and file name]` es donde está ubicado el archivo, y su nombre.
- `[destination username@IP]` es el nombre de usuario y la IP de la máquina de destino.
- `[destination directory]` por último, está el directorio de destino donde se guardará el archivo.

### Opciones

Las opciones más utilizadas son:

- `-P port` permite especificar una entrada diferente al servidor (el puerto predeterminado para el puerto TCP para el comando es 22)
- `-c cipher` te da la posibilidad de especificar el algoritmo de cifrado que utilizará el cliente. Algunos de los valores que puedes usar son ‘aes256-ctr’, ‘aes256-cbc’, ‘blowfish-cbc’, ‘arcfour’, ‘arcfour128’, ‘arcfour256’, ‘cast128-cbc’, aes128-ctr’, ‘aes128-cbc’, ‘aes192-ctr’, ‘aes192-cbc’, y 3des-cbc’. La opción predeterminada en la configuración de shell es ‘AnyStdCipher’
- `-q` ejecutará la operación en modo silencioso (quiet), lo que significa que solo se mostrarán los errores críticos.
- `-r` es para copia recursiva, que incluirá todos los subdirectorios.
- `-4` o `-6` se pueden usar si quieres elegir la versión de protocolo empleada, ya sea IPv4 o IPv6. También puedes configurar los requisitos de dirección IP de manera más exhaustiva con la palabra clave de la familia de direcciones (address-family keyword).
- `-p` conservará los tiempos de modificación iniciales y los atributos del archivo.
- `-u` borrará el archivo fuente después de que se complete la transferencia.
- `-c` permitirá la compresión de los datos mientras se lleva a cabo la operación de transferencia.

### Ejemplos

- `$ scp archivo.tar.gz foo@192.168.1.100:/home/foo/`: se tansfiere un archivo local al host remoto.
- `$ scp foo@192.168.1.100:/home/foo/archivo.tar.gz /home/bar/`: se transfiere una archivo de un host remoto a un directorio local.

### Links

- [scp(1) - Linux man page](https://linux.die.net/man/1/scp)
- [Comando SCP: ejemplos de uso](https://rm-rf.es/comando-scp-ejemplos-uso/)
