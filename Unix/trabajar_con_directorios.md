# Trabajar con directorios

## `mkdir`

Este comando permite crear nuevos directorios en el sistema de archivos. Con la ayuda de este comando podemos crear múltiples directorios configurando los directorios con permisos.

Los directorios que deben crearse deben tener un nombre para que el comando mkdir cree ese directorio siempre y cuando no existe ningún directorio con ese nombre. Se pueden nombrar varios directorios para crear y también se pueden nombrar subdirectorios en el orden particular en el que también se irán creando.

Cuando proporcione solo el nombre del directorio, sin la ruta completa, se creará en el directorio de trabajo actual. Para crear un directorio en otra ubicación, debe proporcionar la ruta al archivo, ya sea absoluta o relativa al directorio raíz.

La sintaxis de este comando es `mkdir [OPCIONES] directorio [otro directorio]...`

### Opciones

- `-v`, `--verbose`: imprime un mensaje por pantalla para cada directorio que cree.
- `-m`, `--mode`: especifica el modo de acceso para los nuevos directorios (como `chmod`).
- `-p`, `--parents`: crea directorios intermedios si no existen.
- `-Z`, `--context`: esta opción se utiliza para establecer reglas SELinux predeterminadas en un directorio en particular en el momento de la creación. 
- `--version`: muestra información sobre la versión de mkdir.
- `--help`: muestra la ayuda del comando

### Ejemplos

`mkdir dir1 dir2 dir3`
: Crea los directorios dir1 dir2 y dir3, si no existen en el directorio actual.

`mkdir -m 666 test`
: Crea el directorio "test" y establece permisos de lectura y escritura.

## `rmdir`

Este comando se utiliza para eliminar directorios vacíos. En caso de que el directorio a eliminar contenga algún subdirectorio o archivo, el comando rmdir no podrá eliminarlo. Los directorios se eliminan en el orden en que se especifican en la línea de comando, es decir, de izquierda a derecha. Para eliminar tanto el padre como el subdirectorio del padre, el subdirectorio debe mencionarse primero para que el directorio padre quede vacío y rmdir pueda eliminarlo (aunque también se puede utilizar la opción `-p`).

La sintaxis de este comando es `rmdir [OPCIONES] directorio [OTROS DIRECTORIOS]...`

### Opciones

- `-v`, `--verbose` muestra por pantalla los directorios que se van eliminando.
- `-p`, `--parents` permite eliminar un directorio y sus directorios padres que se queden vacíos.
- `--ignore-fail-on-non-empty` normalmente, cuando rmdir recibe instrucciones de eliminar un directorio no vacío, informa un error. Esta opción suprime esos mensajes de error.
- `--help` muestra un mensaje de ayuda.
- `--version` información de la versión de salida.

### Ejemplos

`rmdir dir1`
: Elimina el directorio dir1 si está vacío.

## `ls`

Este comando nos permite listar el contenido de un directorio. Si no se especifica como argumento el parámetro directorio, por defecto se listará el contenido del directorio donde nos encontremos ubicados.

### Opciones 

Sólo se muestran algunas de las opciones más comunes. Para ver un listado más amplio consultar el [manual de ls](https://manpages.debian.org/bullseye/manpages-es/ls.1.es.html#s):
- `-d` lista el directorio en si, no su contenido.
- `-R` lista el contenido del directorio y subdirectorios.
- `-l` muestra una lista detallada del contenido del directorio.
- `-s` muestra el tamaño de cada fichero delante del nombre del archivo.
- `-h` conjuntamente con `-l` y `-s`, muestra el tamaño de los archivos listados, añadiendo una letra para indicar el tamaño (por defecto, el tamaño se muestra en bytes).
- `-g` como `-l`, pero no lista el propietario.
- `-a` muestra también los archivos ocultos.
- `-A`, `--almost-all` no muestra las entradas implícitas . ni ..
- `-t` muestra la lista ordenada según la marca de tiempo (fecha de modificación por defecto).
- `-S` muestra la lista de archivos ordenados por tamaño.
- `-r` invierte el orden de clasificación por defecto del listado de archivos.
- `--help` muestra la ayuda del comando.
- `--version` muestra la versión del programa.

### Ejemplos

`ls -la /home`
: muestra una lista detallada de todos los archivos del directorio `/home`.

`ls -lrth .`
: muestra una lista detalla de los archivos del directorio actual, ordenados de forma inversa según su fecha de modificación y mostrando el tamaño de forma legible para los humanos.


## `cd`

Este comando se utiliza para cambiar el directorio actual de trabajo en Linux y otros sistemas operativos similares. Si no se especifica ningún argumento, `cd` nos lleva al directorio de inicio del usuario.

La sintaxis de este comando es `cd [OPCIONES] dir`.

### Opciones

Este comando sólo acepta dos opciones, que rar vez se usan:
- `−L`, sigue los enlaces simbólicos. Por defecto, cd se comporta como si la -L opción estuviera especificada.
- `−P`, no sigue enlaces simbólicos.

### Ejemplos

`cd ../`
: nos coloca en el directorio superior al directorio actual.

`cd /home/user/Downloads`
: nos lleva al directorio Downloads del usuario user.

## `du`

Este comando muestra un resumen del uso en disco que realiza un conjunto de archivos y de manera recursiva en los directorios existentes. Si no especificamos ningún parámetro, se desplazará a través de todos los archivos y carpetas dentro del presente directorio de trabajo. Para cada archivo listado se mostrará el tamaño de archivo junto a él y, al finalizar, se mostrará el tamaño total del conjunto de archivos.

La sintaxis del comando es la siguiente `du [OPCIÓN]...`

### Opciones

Sólo se muestran algunas de las opciones más comunes. Para ver un listado más amplio consultar el [manual de cd](https://manpages.debian.org/bullseye/manpages-es/du.1.es.html):
- `-a`, `--all` muestra resultados para todos los ficheros, y no sólo para los directorios.
- `-c`, `--total` imprime un 'total' del directorio.
- `-d`,  `--max-depth=N` muestra el total para un directorio (o para un fichero, con --all) solamente si está N o menos niveles por debajo del argumento de la línea de órdenes.
- `-h`, `--human-readable` muestra los tamaños de forma legible.
- `-s`, `--summarize` muestra solamente un total para cada argumento.
- `--exclude=PATRÓN` excluye los ficheros que coinciden con PATRÓN.
- `--help` muestra la ayuda.
- `--version` muestra la versión del programa.

### Ejemplos

`du -h /`
: muestra, en formato legible, el tamaño de los subdirectorios incluidos dentro del directorio raíz.

`du --exclude='*.o'`
:saltará todos los archivos y diretorios que terminen en .o (incluso si se llama exactamente .o).

## `df`

Muestra el uso del disco duro y otras informaciones como el punto de montaje y el sistema de ficheros. Si no se proporciona ningún nombre de archivo, se muestra el nivel de uso del espacio en todos los sistemas de archivos montados. Por defecto, el espacio en disco se muestra en bloques de 1K.

La sintaxis de este comando es `df [OPCIÓN]... [FICHERO]...`

### Opciones

Algunas de las opciones más usadas de este comando son:
- `-P` produce una salida en el formato descrito en la sección de la salida estándar (STDOUT).
- `-t` incluye todas las cifras del espacio asignado.
- `-i` muestra los i-nodos usados y disponibles.
- `-h` muestra espacio en unidades comunes(KB, MB o GB).
- `-T` imprimir el tipo de sistema de archivos.
- `--help` muestra la ayuda y finaliza.
- `--version` muestra la versión del programa y termina.

### Ejemplos

`df -h`
: muestra el uso del sistema de archivos, en formato legible.

`df -T`
: muestra el tipo de sistema de archivos en el listado de uso del sistema de archivos.

## `pwd`

Muestra el nombre del directorio de trabajo actual.

La sintaxis del comando es `pwd [OPCIONES]`

### Opciones

- `-L`, `--logical` utiliza PWD del entorno, incluso si contiene enlaces simbólicos
- `-P`, `--physical` evita todos los enlaces simbólicos. Si no se especifica ningúna opción se aplica -P por defecto.
- `--help` muestra la ayuda.
- `--version` muestra la versión del programa.

## Links

- [Comandos UNIX - Trabajar con directorios](https://help.dreamhost.com/hc/es/articles/215465297-Comandos-UNIX-Trabajar-con-directorios)

---

- [mkdir man page](https://linux.die.net/man/1/mkdir)
- [Introduction to Mkdir Command in Linux](https://www.educba.com/mkdir-command-in-linux/?source=leftnav)
- [Cómo crear directorios en Linux (comando mkdir)](https://noviello.it/es/como-crear-directorios-en-linux-comando-mkdir/)

---

- [Introduction to Remove dir Linux](https://www.educba.com/remove-dir-linux/?source=leftnav)
- [Cómo usar el comando mkdir y rmdir](https://ayudalinux.com/como-usar-el-comando-mkdir/)

---

- [ls man page](https://linux.die.net/man/1/ls)
- [Aprende a listar tus ficheros en Linux con el comando ls](https://ed.team/blog/aprende-listar-tus-ficheros-en-linux-con-el-comando-ls)

---

- [Comandos Linux cd](https://www.comoinstalarlinux.com/comandos-linux-cd/)

---

- [Du y Df](https://colaboratorio.net/javierinsitu/terminal/2018/du-y-df-nuestro-espacio-en-disco-rapido-y-facil/)
- [du man page](https://manpages.debian.org/bullseye/manpages-es/du.1.es.html)

---

- [df man page](https://manpages.debian.org/bullseye/manpages-es/df.1.es.html)

---

- [pwd man page](https://manpages.debian.org/bullseye/manpages-es/pwd.1.es.html)