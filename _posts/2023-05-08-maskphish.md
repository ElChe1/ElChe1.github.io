---
layout: single
title: ¿Cómo camuflar un link con Maskphish?
excerpt: "En este artículo vamos a ver como camuflar un enlace malicioso."
date: 2023-5-8
classes: wide
header:
  teaser: /assets/images/maskphish/portadalink.png
  teaser_home_page: true
categories:
  - Herramientas
tags:
  - Herramientas
  - Linux
  - Guías
  - Camuflar links
---
![](/assets/images/maskphish/portada.jpg)

Cabe recalcar que esta herramienta es solo para fines educativos, para que aprendáis del mundo del Hacking Ético. Recordad no usar esta herramienta contra una persona, ya que es ilegal. 

## ¿Como instalar Maskphish?

Como siempre, clonaremos el repositorio de **jaykali**. Podéis ver su perfil donde tiene algunas otras herramientas interesantes.

```bash

git clone https://github.com/jaykali/maskphish

```

Nos movemos al directorio de maskphish y nos encontraremos con un archivo llamado maskphish.sh y lo abrimos. 

```bash

bash maskphish.sh

```
<p align="center">
<img src="/assets/images/maskphish/inicio_programa.png">
</p>

Ahora nos pide que pongamos nuestro link malicioso, yo pondré mi página web. Seguidamente, nos pide el dominio, dependientemente del trabajo que estés haciendo, ya sea Phishing u otros tendrás que adaptarte a tus necesidades. En mi caso yo simularé que es un video de YouTube.

<p align="center">
<img src="/assets/images/maskphish/medio.png">
</p>

Ahora nos pide que usemos ingeniería social, esto depende del trabajo tuyo. Para poner palabras en mi caso pondré **como-ganar-dinero**. Recordar en cada espacio poner el guion.

<p align="center">
<img src="/assets/images/maskphish/link.png">
</p>

Ya acabando se nos ha generado nuestro link camuflado, podemos ver que si ponemos este link en nuestro navegador nos dirige a la página que hemos puesto anteriormente, en mi caso a mi página web. 

<p align="center">
<img src="/assets/images/maskphish/final.png">
</p>