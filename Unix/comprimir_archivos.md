# Comprimir Archivos

Un archivo comprimido es una copia de menor tamaño de un archivo ofiginal. Para ello se utilizan modelos y algoritmos matemáticos de forma que la información del mismo ocupa un menor espacio de almacenamiento en disco duro.

Al comprimir un archivo, este normalmente queda ilegible en su formato habitual. Para leerlo será necesario descomprimirlo nuevamente.

Empaquetar archivos se refiere a la acción de comprimir en un sólo archivo la información de diferentes archivos, ocupando menos espacio en el disco duro que si están desempaquetados.

## Tar

El nombre .TAR corresponde al acrónimo de “Tape ARchiver”, Archivador en Cinta en su traducción al español y proviene de su uso original, que era unificar múltiples archivos en uno para simplificar el proceso de almacenamiento de archivos en cintas magnéticas.

Originalmente, este proceso de unificación no incluía compresión. Esta funcionalidad surgió posteriormente de forma no nativa gracias a la popularidad que recibió este formato para generar archivos descargables desde internet. Gracias a este último factor, .TAR ha integrado motores de compresión que permiten reducir el tamaño del archivo final.

Es importante comprender que el formato .TAR no permite comprimir la información de forma nativa, sino que es necesario el uso de una librería externa tal como GZip, 7-Zip, PeaZip u alguna otra nativa o de tercero. Podemos validar estos formatos en las extensiones: .TAR.GZ, .GZ o TGZ.

A estos archivos .TAR compresos se les conoce como tarballs y pueden ser fácilmente identificados por utilizar “doble” extensión (.TAR.GZ). Para no caer en confusiones, las extensiones .GZ y .TGZ son formas cortas de renombrar .TAR.GZ.

Si deseásemos crear un archivo .TAR comprimido, podemos ejecutar el siguiente comando:

`tar -czvf nombre-del-archivo.tar /path/del/archivo/a/comprimir [/otros]`

Si analizamos y desglosamos el comando descrito, podremos comprender de forma detallada las acciones solicitadas:

tar
: Corresponde al comando de ejecución del programa tar para la manipulación de archivos .TAR.

c
: Flag o bandera que representa la acción “create” e informa al comando principal que se desea crear un archivo .TAR con los archivos o carpetas señalados en el comando.

z
: Flag o bandera que representa la acción “compress” e informa al comando principal que se desea comprimir el .TAR resultante con GZip para disminuir el peso del archivo .TAR.

v
: Flag o bandera que representa la acción “verbose” e informa al comando principal que se desea mostrar todo lo que sucede en la ejecución, mostrando los archivos agregados o extraídos según corresponda y al mismo tiempo mostrar el progreso de la operación.

f
: Flag o bandera que representa la acción “file” e informa al comando principal que se desea definir un nombre específico al archivo resultante.

nombre-del-archivo.tar
: Corresponde al nombre del archivo .TAR a crear. Este nombre puede ser establecido dado a que fue ejecutado el flag o bandera “f” en la ejecución del comando .TAR.

/path/del/archivo/a/comprimir
: Corresponde a la ruta de la carpeta o archivo que desea ser añadido al .TAR.

[/otros]
: Al estar entre Brakes o Corchetes “[]” se aplica a una parte del comando que puede ser opcional. Corresponde a la ruta de archivos o carpetas adicionales que pueden ser añadidas al .TAR.

## Gzip, gunzip

gzip, abreviatura de GNU zip, es una herramienta de compresión que se utiliza para truncar el tamaño de un archivo. Por defecto, el fichero original será reemplazado por el archvio comprimido con extensión (.gz) siempre que sea posible, manteniendo los mismo modos de propiedad, acceso y tiempo de modificación.

Para comprimir un archivo, utilizamos el comando `gzip filename.ext`. El archivo será comprimido y guardado como filename.ext.gz.

Para descomprimirlo, utilizamos el comando `gunzip filename.ext.gz`. El archivo filename.ext.gz se descomprime y obtendremos todo el contenido de filename.ext.

Los sistemas no-Linux pueden tener problemas de compatibilidad con los ficheros comprimidos con gzip.
