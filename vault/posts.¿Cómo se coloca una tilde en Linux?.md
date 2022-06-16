---
id: zo0d5grlpor8gkspfbbs9or
title: ¿Cómo se coloca una tilde en Linux?
desc: ''
updated: 1655352158466
created: 1655352043243
categories:
- guide
---

Author: @Francisco
Tags: #linux #commands

> Fecha original de publicación: 2021-06-23 22:45:44

## ¿Qué es el compose key?

La tecla compose o componer, es básicamente una característica del sistema operativo que le permite escribir símbolos o caracteres especiales que no están en el teclado en cuestión. Existen algunas maneras de poder activar la tecla componer, pero me voy a enfocar está vez en entornos de escritorio de GNOME.

En el escritorio GNOME, se puede definir una de las teclas ya existentes en su teclado para poder usar la tecla componer. Se pueden usar secuencias, una combinación o una sola tecla.

Cabe mencionar que la tecla componer se puede habilitar para los usuarios de manera individual o global en el sistema.

## Usando el compose key

Como habrán notado varias veces ya, cuando publico en mis redes sociales, usualmente no hago una advertencia por que no tengo teclados que tengan tildes, y durante muchos años ha sido un pain in the ass. Fue hasta poco, relativamente poco, descubrí que existe la manera de poder usar caracteres que no se encuentran en el teclado por defecto.

## Habilitando la compose key con la aplicación Tweaks

Necesitamos primero instalar Tweaks en nuestro sistema. Y para eso usamos el siguiente comando:

```shell
# yum install gnome-tweaks
```

Una vez tenemos la aplicación instalada, procedemos con los siguientes pasos:

1. Abrimos Tweaks.
2. Navegamos a la sección de **Keyboard & Mouse** < **Compose Key** y lo habilitamos.
3. Ahora escogemos una de las teclas que se encuentran disponibles en la lista.

![tweaks](https://i.imgur.com/tDcqzf1.png)

## Habilitando la compose key con G Settings

Para habilitar la tecla componer para un usuario de manera individual usando el comando `gsettings` hay que seguir el siguiente paso:

```shell
$ gsettings set org.gnome.desktop.input-sources xkb-options "['compose:ralt']"
```

Para configurar una tecla distinta al Right Alt, les recomiendo ver la documentacion usando `man xkeyboard-config(7)`.

Cualquier duda o comentario, me lo pueden hacer saber de las decenas de formas que existen para contactarme lol.

Gracias por leerme. Take care.
