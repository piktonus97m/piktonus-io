---
id: img3xeb4ho2w36pqk56tx7r
title: 'Hexo, un framework para hacer blogs'
desc: ''
updated: 1655517290384
created: 1655517181487
---

Author: @Francisco
Tags: #archivo

> Fecha original de publicación: 2021-06-13 16:38:05

## Synopsys(?

Para estrenar el blog que hice, les voy a contar un poquito de como fue el proceso para poder realizar este blog, no sé si desde cero, pero sí asumiendo que ustedes ya saben usar varias herramientas indispensables y otras cosillas.

> Cabe destacar que este tutorial tendrá una narración desde mi perspectiva.

Tengo que admitir que hacer que la app funcionara lejos de un ambiente de desarrollo fue definitivamente la parte más frustrante. Pero fue super reconfortante cuando la puse funcionar. Al final les cuento cuales fueron  mis bloqueos mientras hacia el proyecto.

## Hexo, una herramienta para crear blogs en un abrir y cerrar de ojos

[Hexo](https://hexo.io/) es un framework para poder armar sitios web estáticos, orientados directamente a que vayan a ser blogs, debido a su engine.

Hexo soporta Markdown y literalmente las apps se despliegan con un par de comandos, es casi mágico, eh.

Primero debemos de instalar Hexo en nuestra maquina y después en nuestro proyecto.

## Vercel

[Vercel](https://vercel.com) es una plaforma para el despliegue y colaboración orientada a los frontend developers, y son los mismos creadores de [Next.js](https://nextjs.org/). Lo que me fascina de esta plataforma es lo fucking sencillo que es hacer un deploy de cualquier aplicación, la que sea y como sea. Y precisamente ese el goal de ellos, enfocarse en dar herramientas que provisionan absolutamente lo necesario sin dejar de lado su facilidad de uso. Literalmente para crear una app, solamente tenemos que apretar un par de botones y listo, ya tenemos un link, con SSL incluido, y si ya tenés un domain, lo agregás y BOOM! Lista la app para producción. :)

Ok, pero veamos como lo hice.

## Montar el proyecto en Vercel

Admito que esta no es la mejor forma de comenzar un proyecto, pero el por qué decidí hacerlo así, se los cuento al final, como parte de los blocks que tuve.

Primero lo que vamos a hacer es un proyecto desde cero en Vercel de la siguiente manera: ![new_proyect](https://i.imgur.com/9dcMpsm.png)

Bueno, no. Lo primero es que se tienen que crear la cuenta en Vercel si no lo han hecho. Ya una vez con su cuenta lista pueden proceder a crear el proyecto como lo muestro arriba.

### Agregar nuestro cliente de Git preferido a Vercel

Es importante que agreguemos el cliente de Git a nuestra cuenta, para que Vercel automáticamente haga el repositorio remoto. Soporta GitHub, BitBucket y GitLab.

### Crear el proyecto

- Y ya con eso hecho podemos clonar el template de Hexo.

    ![template](https://i.imgur.com/qRaepjE.png)

- Seleccionamos nuestra cuenta (ya ligada) al cliente de Git, en mi caso GitHub.

![account](https://i.imgur.com/FAUUKXg.png)

- Le damos un nombre al proyecto, en mi caso lo podemos nombrar como `hexo-test-blog`. Y obvio podés hacerlo privado.

![git_hub_name](https://i.imgur.com/3kWfKG7.png)

- A este punto vamos a salir con la parte para poder realizar el deploy. Hay que asegurarse de que las opciones se dejan por defecto y no se tocan a menos de que quiera hacer algo que ya sabe, y pues que venga a conveniecia. Tocamos `Deploy`.

    ![deploy](https://i.imgur.com/00RPGpf.png)

Se mostrará una pantalla con el proceso de los logs, y en donde solamente nos toca esperar. Y con un mensaje de `Felicidades` nos vamos a topar nuestra app ya en un ambiente de producción. Eso por cierto, se puede cambiar en la parte de opciones, pero es tema para otro día.

### Clonar el proyecto

Ahora lo que tenemos que hacer es irnos a GitHub, y clonar nuestro proyecto para empezar a trabajar con el. Vercel en el Dashboard nos presenta el URL del repositorio que se tomó la libertad de crear por nosotros.

A mi me gusta clonar el repositorio usando HTTPS, entonces tiro `git clone https://github.com/piktonus97m/hexo-test-blog.git` en el directorio donde vamos a trabajar, y luego hago un `code .` para que amablemente Visual Studio Code me reciba con los brazos abiertos. Pero eso ustedes lo llegarán a realizar con las herramientas que usan.

### Hora de trabajar

Usualmente las instrucciones de instalación para instalar los temas de Hexo, piden que nos movamos a la carpeta `root` del proyecto y clonar el repositorio de ellos a `/themes/nombre_del_tema`. Si es que decide hacer eso, hay que asegurarse de remover los elementos de Git, ya que tendriamos problemas el el futuro cuando se vaya a realizar un submit y luego el push. O bien solamente combinar ambas ramas.

Después de eliminar el directotio `.git`, procedemos a correr `git remote remove origin` para poder quitar la relacion del repositorio local con el repositorio remoto (El de la persona que creó el repositorio del tema).

Y ya con eso, podemos empezar a seguir las instrucciones de cada tema en especifico. Yo personalmente empecé a agregar mi información en las variables que ellos ya setean y listo.

#### Server local

Para poder hacer un servidor de desarrollo debemos asegurarnos de tener instalado en nuestra maquina en cuestión [Node.js](https://nodejs.org/en/) para poder instalar Hexo.

Entonces ejecutamos el siguiente comando probablemente con `sudo` de por medio.

```bash
npm install -g hexo-cli
```

Para montar el server de desarrollo usamos:

```bash
hexo generate
hexo server
```

`hexo generate` sirve para poder indexar los nuevos files que vamos creando.
`hexo server` realiza el deploy del server en `localhost:4000`.

Listo! Ya podemos empezar a tocar los configuration files pertenecientes al tema.

> Para ver los cambios que se van realizando, salvamos el file, y refrescamos el navegador después. En algun punto los cambios no se van a ver, entonces si eso pasa, apagamos el server con `ctrl+c` y volvemos a indexar las páginas/cambios nuevos con `hexo generate` y volvemos a encender el servidor con `hexo server`.

#### Temas

Comunmente el tema se setea en `_config.yml`, en el apartado de themes, luce algo así:

```yml
# Themes: https://hexo.io/themes/
theme: landscape
```

Yo estoy usando el tema llamado [Cactus](https://github.com/probberechts/hexo-theme-cactus), creado por [Pieter Robberechts](https://github.com/probberechts).

Cuando estaba listo seguí las instrucciones recomendadas y de vez en cuendo jugaba con las cosas. Como estamos en el server de desarrollo no hay nada de que preocuparse; equivocarse y arruinar las cosas es una regla. :)

Una vez tenemos todo listo para hacer el deploy en Vercel, solamente hay que seguir el típico workflow de Git. Le hacemos push a los cambios y listo. Ya automáticamente Vercel hace el buid del nuevo request y como por arte de magia tenemos nuestra app en producción.

#### Notas

Si por algún motivo después del deploy, nos el app nos muestra una pantalla en blanco, hay que probar eliminando el tema original y dejar solamente el tema que le pusimos. En mi caso fue así, y luego de eso, ya todo comenzó a funcionar.

## Road Blocks y otros pensamientos

Al principio tuve que plantearme de como mierda iba a hacer para montar un blog, nunca lo había hecho y el único engine que he usado para eso es Wordpress para la página de [Abysmal Sun](https://abysmalsun.com/), pero es muy sencillo de y no agrega un valor agregado más allá de ser sencillo de usar, y un montón de *code trash*, que al final del día, no me funcionaba mucho para aprender, así que decidí primero usar [Hugo](https://gohugo.io/), pero holy shit, la verdad es que me rendí después de un par de días en donde no podía hacerle el deploy a producción, por que nunca había tocado [Golang](https://golang.org/) y a pesar de no ser una vara fuera de este mundo, la verdad la sención de querer sacar la vara lo antes posible me puso una barrera mental enorme. Entonces que decidí hacerlo con Hexo, un framework basado en Next.js, cosa que ya estaba muchísimo más familiarizado. :)

El próximo goal, es poder hacer una vara similar con la página de Abysmal Sun, pero ya eso me lo tomare con un poco más de calma, además de todo lo tengo que ver con Pablo también.

Espero de todo corazón que a alguien le resulte útil esta pequeña guía. Cualquier duda o comentario, me lo pueden hacer saber de las decenas de formas que existen para contactarme lol.

Gracias por leerme. Take care.
