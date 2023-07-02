---
layout: single
title: 
excerpt: "En este artículo vamos a ver como conseguir las contraseñas guardadas en GOOGLE desde Windows 10. No debes de guardar tus contraseñas en el navegador!"
date: 2023-6-29
classes: wide
header:
  teaser: /assets/images/decrypt-chrome-passwords/google-password-manager.jpg
  teaser_home_page: true
categories:
  - Herramientas
  - Consejos
tags:
  - Herramientas
  - Windows
  - Guías
  - Chrome Passwords
---
![](/assets/images/decrypt-chrome-passwords/portada2.png)

Cabe recalcar que esta herramienta es solo para fines educativos, para que aprendáis del mundo del Hacking Ético. Recordad no usar esta herramienta contra una persona, ya que es ilegal. 

## Como se guardan estas contraseñas?

Empezamos entrando a cualquier página, por ejemplo HTB, iniciamos sesión y arriba a la derecha nos sale una pestaña para guardar la contraseña y nosotros la guardamos. Y aquí es donde vamos a caer, guardando la contraseña en el navegador y corriendo el peligro de ser hackeados y nos roben nuestras contraseñas.

<p align="center">
<img src="/assets/images/decrypt-chrome-passwords/pagina_htb.png">
</p>


## Donde se guardan las contraseñas de Chrome? 

Para ver las contraseñas guardadas en nuestro navegador lo que tenemos que hacer será ir a la ruta. 

```

C:\Users\$tu nombre$\AppData\Local\Google\Chrome\User Data\Default\Login Data

```

Buscamos por la parte de abajo **Login Data** y abrimos el archivo, vemos que el texto está encriptado y lo que hará nuestro script será atacar a este archivo.

<p align="center">
<img src="/assets/images/decrypt-chrome-passwords/logindata.png">
</p>


## Como usar la herramienta?

Primero de todo, esta herramienta está hecha por **ohyicong** y podéis echar un vistazo a su GitHub, ya que tiene buenos repositorios.

Vamos directos al repositorio y el archivo que nos interesa será **decrypt-chrome-passwords.py** que podéis clonar u os metéis en el archivo, RAW y copias el link para seguidamente poder hacer un curl a la URL y cambiando el nombre añadiendo al final un -o “nombre.py”

```

https://github.com/ohyicong/decrypt-chrome-passwords

```

Antes de iniciar el programa lo que tenemos que hacer es instalar algunas dependencias. Necesitaremos _sqlite_, _pycryptodomex_, _pywin32_.

Para tener sqlite ir a la página oficial https://sqlite.org/index.html y descargar. Pero con las dependencias de Python lo que tendremos que hacer será abrir un CMD y ejecutamos los siguientes comandos.

```python

pip install pycryptodomex

pip install pywin32

```

<p align="center">
<img src="/assets/images/decrypt-chrome-passwords/cmd.png">
</p>

En mi caso que ya tengo las dependencias instaladas y me sale un mensaje corto, pero si no la tienen se descargará sin ningún problema.

El script ya está listo y lo podemos ejecutar. (Si no funciona python provar py, es lo mismo)

```python

python .\decrypt.py
py .\decrypt.py 

```

Podemos ver en la terminal las contraseñas guardadas en nuestro navegador. 

<p align="center">
<img src="/assets/images/decrypt-chrome-passwords/contras.jpg">
</p>



