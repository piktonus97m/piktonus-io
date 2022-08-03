---
id: skaa2eok4du59rw9a4mpldu
title: ¿Cómo recordar fácilmente los comandos de Linux?
desc: ''
updated: 1655352549286
created: 1655351778574
---

Author: @Francisco
Tags: #linux #commands

> Fecha original de publicación: 2021-07-21 22:14:54

Existen cientos de comandos en Linux, y pues recordarlos todos es absolutamente imposible. Además de que tampoco es necesario.
Muchas veces sucede que cuando estoy realizando mis tareas diarias me quedo en blanco enfrente de la terminal tratando un comando en particular, lo cual es completamente normal, y lo cual no es nada para avergonzarse. Además cabe aclarar que esto suele pasar aún más cuando estamos aprendiendo a utilizar la terminal como nuestra arma principal.

Lo bueno es que hay buenas noticias para todos, ya que existe un par de tips que nos ayudaran con eso.
Este comando es `apropos` y el _historial de comandos_.`apropos` es un comando de Linux se da la tarea de buscar en las `man pages` y las descripciones de los comandos, mediante una palabra u oración clave que le brindemos al comando, dando como resultado una serie de resultados relacionados.

Pongamos un ejemplo de que se te olvida cual es comando para poder listar los directorios. Veamos entonces como el comando `apropos` nos ayudaría.

```bash
apropos "list directory"
```

Y como resultado tenemos lo siguiente:

```bash
dir (1)              - list directory contents
ls (1)               - list directory contents
ntfsls (8)           - list directory contents on an NTFS filesystem
vdir (1)             - list directory contents
```

Como podemos notar, el resultado que obtenemos es una lista de comandos sugeridos, y pues a este punto seria nada mas de poder identificar el que más nos funcione para la tarea que necesitamos realizar.

Vamos a notar que cuanto más lo usamos llegaremos a un punto en donde se nos mostraran un montón de comandos que tal vez solo generan ruido en la pantalla y pues nos dificulta la búsqueda del comando que andamos buscando, por lo que ahí iremos experimentando usando palabras u oraciones u poco mas cerradas.

Hay que tener en cuenta que el comando `apropos` se puede usar corriéndolo con o sin comillas para la búsqueda de nuestro resultado.

Pongamos el ejemplo de que necesitamos encontrar cuales son los detalles de nuestro Linux Kernel

```bash
apropos "kernel"
```

```bash
apropos kernel
```

Cualquier de los dos comandos nos va mostrar lo siguiente:

```bash
systemd-time-wait-sync (8) - Wait until kernel time is synchronized
systemd-time-wait-sync.service (8) - Wait until kernel time is synchronized
systemd-udevd-kernel.socket (8) - Device event managing daemon
uname (2)            - get name and information about current kernel
urandom (4)          - kernel random number source devices
xtables-legacy (8)   - iptables using old getsockopt/setsockopt-based kernel api
xtables-legacy-multi (8) - iptables using old getsockopt/setsockopt-based kernel api
```

En este caso el comando `uname` es el indicado, ya que es el que nos nuestra los detalles que andamos buscando del Kernel.

Como les mencionaba hace un rato este comando nos va a mostrar todos los comandos relacionados a nuestro request. Por lo que habrá que hacer un mínimo esfuerzo para encontrar lo que buscamos a ese punto.

## Ahora bien, y si nos queremos acordar de algún comando largo? Cómo los podemos recordar?

No hay problema con esto, ya que hay varias maneras de recordar los comandos que andamos buscando recordar. Lo que tenemos que hacer es aplicar "reverse search", que es básicamente mirar nuestro historial de comandos.

Para esto lo que hay que hacer es usar `crtl+r` y empezar a escribir lo que nos acordamos del comando que necesitamos.
Entonces lo que va a pasar a continuación es que se verán una lista de comandos sugeridos provenientes del historial de Bash.

Hay que usar las teclas _Arriba_ y _Abajo_ para navegar entre los comandos que se muestran relacionados a lo que se escribió. Y para poder seleccionarlo, hay que presionar la tecla _TAB_ o las teclas _Izquierda_ o _Derecha_ del teclado y presionar _Enter_ para que se ejecute.

> Hay unas cuantas maneras mas avanzadas para poder gestionar los comandos que usamos con mas relevancia, usando distintas herramientas, pero ese es tema para otro apartado y muy probable cada uno de ellos requiera un entry distinto.

Gracias por llegar hasta acá, espero leernos pronto.

