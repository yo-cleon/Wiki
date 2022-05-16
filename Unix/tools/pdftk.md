# PDFtk

PDFtk Server es una herramienta de línea de comandos para trabajar con archivos PDF. Se usa comúnmente para el procesamiento de archivos PDF.

Viene en tres versiones: PDFtk Free, PDFtk Pro y la herramienta de línea de comandos original PDFtk Server.

Podemos instalar esta herramienta de la forma habitual:

    $ sudo apt install pdftk

## Opciones de la herramienta

  - `<input PDF files | - | PROMPT>`: Recoge la lista de los archivos PDF con los que se va a trabajar. Si se planea combinar estos archivos PDF (sin usar identificadores), enumere los archivos en el orden en que desea que se combinen. Use - para pasar un solo PDF a pdftk a través de stdin. Los archivos de entrada se pueden asociar con identificadores, donde un identificador es una sola letra mayúscula:

        <identificador de PDF de entrada>=<nombre de archivo de PDF de entrada>

  Los identificadores a menudo se omiten. Son útiles para especificar contraseñas de PDF o rangos de páginas, más adelante.

  - `[output <output filename | - | PROMPT>]`: Establece el nombre del archivo de salida. Se utiliza `-` para enviar a la salida estándar. Con la operación `dump_data`, se utiliza la salida para establecer el nombre del archivo de datos de salida. Cuando se utiliza la operación `unpack_files`, se utiliza la salida para establecer el nombre de un directorio de salida. Cuando utilice la operación `burst`, se puede utilizar la salida para controlar los nombres de archivo de las páginas PDF resultantes.

  - `cat [<rango_de_paginas>]`: Permite concatenar páginas de archivos de PDF de entrada para crear un nuevo PDF. El orden de las páginas en el nuevo PDF se especifica según el orden de los intervalos de páginas dados. Los intervalos de páginas se describen así:

        <identificador de PDF de entrada>[<número de página inicial>[-<número de página final>[<calificador>]]][<rotación de página>]

  donde el *identificador* identifica al archivo/s PDF de entrada, los *números de página inicial y final* son referencias basadas en uno a páginas en el archivo PDF, el *calificador* puede ser par o impar, y la *rotación de página* puede ser N, S, E, W, L, R o D.

  Si se omite el identificador del intervalo de páginas, las páginas se toman del primer PDF de entrada.

  El calificador **even** hace que pdftk use solo las páginas PDF pares, por lo que 1-6even extrae las páginas 2, 4 y 6 en ese orden. 6-1even extrae las páginas 6, 4 y 2 en ese orden. El calificador impar (**odd**) funciona de manera similar al par.

  La configuración de rotación de página puede hacer que pdftk gire páginas y documentos. Cada opción establece la rotación de página de la siguiente manera (en grados): **N: 0, E: 90, S: 180, W: 270, L: -90, R: +90, D: +180**. L, R y D hacen ajustes relativos a la rotación de una página.

  Si no se pasan argumentos a cat, entonces pdftk combina todos los archivos PDF de entrada en el orden en que se dieron para crear la salida.

  - `shuffle [<page ranges>]`:  Coteja las páginas de los PDF de entrada para crear un nuevo PDF. Funciona como la operación `cat` excepto que toma una página a la vez de cada rango de páginas para ensamblar el PDF de salida. Si se acaba un rango de páginas, continúa con los rangos restantes. Los rangos pueden usar todas las funciones descritas arriba para `cat`, como rangos de página inversos, rangos múltiples de un solo PDF y rotación de página. Esta característica fue diseñada para ayudar a clasificar páginas PDF después de escanear documentos en papel.

  - `burst`: Divide un único documento PDF de entrada en páginas individuales. También crea un informe llamado doc_data.txt que es lo mismo que la salida de `dump_data`. Si se omite la sección de salida, entonces las páginas PDF se denominan: pg_%04d.pdf, p. ej.: pg_0001.pdf, pg_0002.pdf, etc. Para nombrar usted mismo estas páginas, suministre una cadena de formato de estilo printf a través de la sección de salida. Por ejemplo, si desea que las páginas se llamen: *page_01.pdf*, *page_02.pdf*, etc., pase la salida `page_%02d.pdf` a pdftk.

  - `background <background PDF filename | - | PROMPT> `:  Aplica una marca de agua de PDF al fondo de un solo PDF de entrada:

        pdftk in.pdf background back.pdf salida out.pdf

  Pdftk usa solo la primera página del PDF de fondo y la aplica a cada página de la entrada PDF. Esta página se escala y rota según sea necesario para ajustarse a la página de entrada. Puede utilizar - para pasar un  PDF de fondo en pdftk a través de stdin.

  Si el PDF de entrada no tiene un fondo transparente (como un PDF creado a partir de escaneos de páginas) entonces el fondo resultante no será visible; use la operación de `stamp` en su lugar.

  - `stamp <stamp PDF filename | - | PROMPT>`: Esta operación actúa igual que `background`, excepto que superpone la página PDF del sello en la parte superior de las páginas del documento PDF de entrada. Esta operación funciona mejor si la página PDF del `stamp` tiene un fondo transparente.

  - `dump_data`: Lee un solo archivo PDF de entrada e informa varias estadísticas, metadatos, marcadores (a/k/a esquemas) y etiquetas de página al nombre de archivo de salida dado o (si no se proporciona salida) a stdout. Los caracteres que no son ASCII se codifican como entidades numéricas XML. No crea un nuevo PDF.

  - `dump_data_fields`: Lee un solo archivo PDF de entrada y reporta estadísticas de campo de formulario al nombre de archivo de salida dado o (si no se proporciona salida) a stdout. Los caracteres que no son ASCII se codifican como entidades numéricas XML. No crea un nuevo PDF.

## Ejemplos de uso

`$ pdftk portada.pdf libro.pdf cat output memoria.pdf`: combina dos archivos pdf, en un único archivo, para añadir una portada a un archivo ya existente.

`$ pdftk memoria.pdf cat 1-endeven output pares.pdf`: extrae todas las páginas pares de un archivo pdf.

`$ pdftk memoria.pdf cat 8-14 output salidas.pdf`: crea un archivo pdf con las páginas 8 a 14 extraídas desde un archivo origen.

`$ pdftk memoria.pdf background marca.pdf output memoria_H2O.pdf`: añade como marca de agua a un archivo pdf el contenido de la primera página del fichero marca.pdf.

`$ pdftk memoria.pdf burst memoria_%02d.pdf`: extrae todas las páginas de un archivo en ficheros diferentes.

## Links
  - [PDFtk Server](https://www.pdflabs.com/tools/pdftk-server/)
  - [pdftk(1) - Linux man page](https://linux.die.net/man/1/pdftk)
  - [Uso de PDFtk](https://www.elmundoenbits.com/2012/05/uso-de-pdftk.html)
