# Trabajar con directorios

## `mkdir`

Este comando permite crear nuevos directorios en el sistema de archivos. Con la ayuda de este comando podemos crear múltiples directorios configurando los directorios con permisos.

Los directorios que deben crearse deben tener un nombre para que el comando mkdir cree ese directorio siempre y cuando no existe ningún directorio con ese nombre. Se pueden nombrar varios directorios para crear y también se pueden nombrar subdirectorios en el orden particular en el que también se irán creando.

Cuando proporcione solo el nombre del directorio, sin la ruta completa, se creará en el directorio de trabajo actual. Para crear un directorio en otra ubicación, debe proporcionar la ruta al archivo, ya sea absoluta o relativa al directorio raíz.

La sintaxis de este comando es:
`mkdir [OPCIONES] directorio [otro directorio]...`

### Opciones

- `-v` (--verbose) le dice a mkdir que imprima un mensaje para cada directorio que cree.
- `-m` Especifica el modo de acceso para los nuevos directorios.
- `-p` Crea directorios intermedios si no existen.
- `--version` muestra información sobre la versión de mkdir.
- `--help` muestra la ayuda del comando
- `-Z` esta opción se utiliza para establecer reglas SELinux predeterminadas en un directorio en particular en el momento de la creación. 

### Ejemplos

`mkdir sample1 sample2 sample3`
: Este comando crea los directorios sample1 sample2 y sample3, si no existen en el directorio actual.

`mkdir -m 666 test`
: El comando anterior crea el directorio "test" y establece permisos de lectura y escritura.

## `rmdir`

El comando rmdir se usa para eliminar directorios vacíos. En caso de que el directorio a eliminar contenga algún subdirectorio o archivo, el comando rmdir no podrá eliminarlo. Los directorios se eliminan en el orden en que se especifican en la línea de comando, es decir, de izquierda a derecha. Para eliminar tanto el padre como el subdirectorio del padre, el subdirectorio debe mencionarse primero para que el directorio padre quede vacío y rmdir pueda eliminarlo.

La sintaxis de este comando es
`rmdir [OPCIONES] directorio [OTRO DIRECTORIOS]...`

### Opciones

- `-v, --verbose` muestra por pantalla los directorios que se van eliminando.
- `-p` permite eliminar un directorio y sus directorios padres que se queden vacíos.

## Links

- [Introduction to Mkdir Command in Linux](https://www.educba.com/mkdir-command-in-linux/?source=leftnav)
- [Cómo crear directorios en Linux (comando mkdir)](https://noviello.it/es/como-crear-directorios-en-linux-comando-mkdir/)

---

- [Introduction to Remove dir Linux](https://www.educba.com/remove-dir-linux/?source=leftnav)
