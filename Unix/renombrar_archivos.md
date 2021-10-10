# Renombrar archivos

En determiandas circunstancias, vamos a necesitar renombrar uno o varios archivos, ya sea por contener errores en el nombre, porque queremos darle un nombre más adecuado, etc. Para ello, disponemos de varias alternativas.

## `mv`

Si bien la funcionalidad principal de este comando es mover archivos o directorios desde el origen al destino, se suele utilizar también para renombrar  archivos.

La ejecución de este comando sería similar a realizar una copia del archivo asignándole un nuevo nombre y, seguidamente, borrar el archivo original.

La sintaxis de este comando es la siguiente:
`mv [opciones] archivo_antiguo archivo_nuevo`

### Opciones

* `-i` Pregunta antes de sobreescribir un archivo existente en el directorio destino.
* `-f` Borrar los archivos de destino existentes sin preguntar al usuario.
* `-v` Muestra el nombre de cada archivo a ser movido.

## `rename`

Es una herramienta que facilita el renombrado de varios archivos utilizando expresiones regulares, reemplazando la aparación de la expresión regular facilitada, por el valor de sustitución establecido.Así con la ayuda de las opciones y las expresiones regulares facilitadas, se procede al renombrado de los archivos.

No viene con el standard de Linux, por lo que debemos proceder a su instalación. En distribuciones derivadas de Debian, podemos instalarlo con el comando:
`$ sudo apt install rename`.

La sintaxis de este comando es la siguiente:
`rename [opcioness] expresión_regular archivo...`

### Opciones

* `-v` saca por pantalla los nombres de los archivos correctamente renombrados
* `-n` no realiza ninguna acción simplemente muestra los archivos renombrados. Esto es una buena opción para probar cual será el resultado del renombrado, sin que luego nos tiremos las manos a la cabeza.
* `-f` sobre escribe los archivos existente.

### Expresiones regulares

Las expresiones regulares a utilizar tendrán el siguiente formato:
`'s/old-name/new-name/[gi]'`

Los parámetros g e i son dos modificadores que nos permiten lo siguiente,

* `g` sustituir todas las apariciones de expresion1 en expresion2. Si no lo hacemos así, solo se reemplazará la primera de las apariciones.
* `i` no hace distinción entre mayúsculas y minúsculas.

### Ejemplos

`rename 's/.html/.orc/' *.html`
: El comando anterior, dentro del directorio actual, cambiará la extensión .html a .orc de todos los archivos .html que encuentre.

`rename -n 's/\.php$/\.html/' *.php`
: El comando busca todos los archivos del directorio actual con extensión .php, para cambiar la extensión por .html, pero al incluir la opción `-n`, se limitará a mostrar los cambios que se realizarían, sin llegar a efectuarlos.

## Links

* [Introduction to mv command in Linux](https://www.educba.com/mv-command-in-linux/?source=leftnav)
* [mv](https://es.wikipedia.org/wiki/Mv)

***

* [Rename o renombrado desde el terminal](https://atareao.es/software/utilidades/rename-o-renombrando-desde-el-terminal/)
* [How to Use the rename Command on Linux](https://www.howtogeek.com/423214/how-to-use-the-rename-command-on-linux/)
* [Introduction to Linux Rename Command](https://www.educba.com/linux-rename-command/)
[Renombrar: una herramienta de línea de comandos para cambiar el nombre de varios archivos en Linux](https://es.linux-console.net/?p=642)
