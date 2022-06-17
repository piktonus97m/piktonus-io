---
id: qgtu7wovqjdejt1xyt063ya
title: ¿Cómo usar man pages?
desc: ''
updated: 1655354324732
created: 1655354228863
---

Author: @Francisco
Tags: #linux #commands

> Fecha original de publicación: 2021-09-19 13:30:05

## Uso eficiente de las paginas del Manual - Man Pages

Considero que para cualquier persona que se encuentre especializando y afinando su conocimiento en Linux, sabe que las Man Pages en algún momento u otro se tienen que saber usar.

Hoy vamos a aprender algunos trucos y consejos sencillos para leer las páginas de manual de forma eficaz. Como ya sabrá, una página de manual se divide en varias partes, cada una con un encabezado distinto.
Es posible que tengamos que movernos hacia abajo durante bastante tiempo cuando estemos buscando algún tipo información en particular sobre el flag u opción específica. Es una tarea realmente ineficiente y que requiere de mucho tiempo. Por eso es importante aprender a usar las páginas de manual de manera eficiente para averiguar qué es exactamente lo que deseamos saber.

Primero comencemos abriendo un man page de uno de los comandos más sencillos; `mkdir`. Para eso escribimos en la terminal:

```bash
man mkdir
```

Así se ve una página del manual para el comando de `mkdir`:

![manmkdir](https://i.imgur.com/bm59ESQ.png)

Y asi es como la mayoria de las veces se logra ver una pagina de manual, y las lineas mostradas en la captura de pantalla obedecen al comportamiento y diseno usual de las paginas del manual, cambian a para pocas excepcionies, pero usualmente asi se ven todas.

Pero aprendamos a como leerlas, por que la sintaxis para cada una de ellas es igual para todas, y ademas tambien cumple con el formato standard de un comando basado en Unix.

## Estructura de las páginas de manual

Una pagina de manual se divide en varias secciones; usualmente dirigidas para cada seccion del manual, en donde se puede ver categorias como:

- **NAME**,
- **SYNOPSIS**,
- **CONFIGURATION**,
- **DESCRIPTION**,
- **OPTIONS**,
- **EXIT STATUS**,
- **RETURN VALUE**,
- **ERRORS**,
- **ENVIRONMENT**,
- **FILES**,
- **VERSIONS**,
- **CONFORMING TO**,
- **NOTES**,
- **BUGS**,
- **EXAMPLE**,
- **AUTHORS** y
- **SEE ALSO**.
  
Algunos man pages como comentaba ahora, suelen tener todas estas secciones y otras no, dependiendo de que tan bien esté documentado el comando referido.

### Formato de las páginas del manual

Ahora analicemos lo como se tiene que leer el formato de las man pages. El formato hace que todo lo que dice las paginas del manual cobren un sentido logico. Usualmente los autores la mayoria de las veces van asumir el uso comun de los comandos en Linux y ademas de eso asumirán que sabemos como interpretar el formato, haciendo referencia a esta estrategia para poder nosotros descifrar como usar el comando, y llegar a reemplazar o complementar los valores, argumentos o flags requeridas.

- Letras en **bold** o **negrita**, deben de escribirse exactamente como están.
- Las palabras entre `[]` son opciones, es decir, se pueden enviar como argumentos al comando.
- Las letras en *italics* o *cursiva* deben sustituirse por sus argumentos.

Se presiona la tecla flecha *ARRIBA* y *ABAJO* para poder movernos de línea por línea, bien podemos usar `j` o `e` para irnos hacía arriba y `k` o `y` para irnos hacía abajo.  

Se presiona la tecla *IZQUIERDA* y *DERECHA* para movernos media página. O bien podemos usar `d` y `u` para movernos media página respectivamente.

Usamos "ESPACIO" para poder movernos una página entera. O bien podemos usar "f" y "b" para movernos una página entera hacía arriba o hacía abajo respectivamente.

 > Nota: Cuando me refiero a página o media página es básicamente el tamaño de la ventana en pixeles de la terminal que actualmente se está usando.

Así mismo podemos usar las teclas *HOME* y *END* para poder irnos al principio o al final de la manual respectivamente.

Estando dentro de cualquier manual, podemos usar `h` para que se nos muestre toda la sección de ayuda para poder navegar dentro de las páginas.

![helpman](https://i.imgur.com/bk2VOSy.png)

Para poder salir de un manual podemos usar varias opciones. Presiona `q`, o `:q` o `Q` e incluso podemos usar `ZZ`. 

## Buscar un manual a base de palabras clave

Muchas veces vamos a querer buscar como funciona algún comando, pero no nos vamos a recordar de ese comando incluso para poder verificarlo. Pues resulta que hay una manera bastante sencilla de poder solucionar este problema, pero debemos de ser cautelosos por la potencial cantidad de contenido que nos puede desplegar.

Usando el comando `apropos` en sistemas operativos basados en RPM. Hace poco realicé un [blog](https://blog.piktonus97m.xyz/2021/07/21/Como-recordar-facilmente-los-comandos-de-Linux/) dedicado a este comando. O alternativamente en todos los sistemas operativos podemos usar `man -k`.

Suponiendo que queremos crear un nuevo directorio y agregarle un flag en particular, y no recordamos cual era el comando, si corremos `man -k directory`, el output será el siguiente:

```shell
[piktonus97m@fedora ~]$ man -k directory
adcli (8)            - Tool for performing actions on an Active Directory domain
alphasort (3)       - scan a directory for matching entries
alphasort (3p)       - scan a directory
basename (1)         - strip directory and suffix from filenames
basename (1p)        - return non-directory portion of a pathname
bundle-clean (1)     - Cleans up unused gems in your bundler directory
bundle-init (1)      - Generates a Gemfile into the current working directory
bundle-open (1)      - Opens the source directory for a gem in your bundle
...
```

Por obvias razones, no se puede colocar todo el output, pero partir de acá podemos leer cual comando se nos hace familiar y poder identificarlo.

```shell
ls (1)               - list directory contents
ls (1p)              - list directory contents
mcd (1)              - change MSDOS directory
mdeltree (1)         - recursively delete an MSDOS directory and its contents
mdir (1)             - display an MSDOS directory
mdu (1)              - display the amount of space occupied by an MSDOS direc...
mkdir (2)            - create a directory
mkdir (3p)           - make a directory
mkdirat (2)          - create a directory
mkdtemp (3)          - create a unique temporary directory
...
```

Y como pueden ver, ahí se encuentra el comando que andabamos buscando: `mkdir`. Ya sabiendo esto, procederiamos a realizar el comando `man mkdir` para referirnos más información y documentación.

Podemos incluso limpiar nuestra busqueda usando el siguiente comando  `man -k directory | grep create`.

![mangrep](https://i.imgur.com/2A0KH5J.png)

## Búsqueda dentro del manual

Una vez nos encontremos dentro de cualquier manual, podemos realizar una búsqueda de texto, ya sea una cadena o una sola palabra.

Usando `/<cadena>` o `/patrón` nos permitirá realizar la búsqueda.

![mansearch](https://i.imgur.com/Tx2okOb.png)

Y para poder movernos entre esos resultados usamos la tecla `n` y `N` para movernos hacía adelante o atrás respectivamente.

Para hacer una búsqueda invertida usamos `?<cadena>` o `?patrón`. Aplicando la misma dinamica para poder movernos entre los resultados.

## Pensamientos finales

Las man pages son un recurso indispensable para aquellos que usamos las herramientas y comandos de Linux a diario por cuestiones de aprendizaje, investigación o trabajo, y saber como recurrir a la documentación sin necesidad de una conexión a internet es sumamente importante. Ya que si estamos en un servidor, probablemente no vayamos a tener acceso a un navegador web, entonces reconocer el funcionamiento de las paginas del manual es un skill que no debe de ser subestimado.

Muchas gracias por llegar hasta acá. Ya saben cualquier corrección, o sugerencia. GitHub está a la mano dandole click a mi nombre. Espero que les haya funcionado.
