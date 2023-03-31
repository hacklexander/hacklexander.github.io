---
title: "Instalacion de Arch"
layout: post
date: 2023-03-28 21:00
image: /assets/images/markdown.jpg
headerImage: false
star: true
tag:
- Inicio
- VMWare
category: blog
author: hacklexander
description: Instalacion de Archlinux
---



## Carga de la imagen.

una vez tengamos todos los recursos descargados, creada la maquina virtual en VMWare o VirtualBox, tendremos una terminal de comandos para empezar con la instalacion.

A continuacion muestro la terminal de comandos que nos sale.

![first][1]
<figcaption class="caption">Primera vista</figcaption>
[1]: {{site.url}}/{{site.arch}}08.png

---

## cambiamos distribucion de teclado

Despues de esto, lo que tenemos que hacer es poner nuestra distribucion de teclado en el lenguaje **Español** o **Ingles** como prefieras, esto para que los caracteres especiales se escriban de forma correcta.

El comando que debemos escribir es: 


```bash

root@archiso ~# loadkeys es

```

![loadkeys]({{site.url}}/{{site.arch}}loadkeys.png)

---

## verificamos si tenemos internet

Si estamos usando una maquina virtual, lo mas probable es que el internet ya este configurado, pero podemos verificar usando un pequeño comando en la linea de comandos que es:

```bash
root@archiso ~# ping -c3 8.8.8.8
```

Si efectivamente contamos con internet, tendremos una salida en la linea de comando como la siguiente:

```bash
root@archiso ~# ping -c3 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=118 time=4.61 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=118 time=4.85 ms
64 bytes from 8.8.8.8: icmp_seq=3 ttl=118 time=4.91 ms

--- 8.8.8.8 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2008ms
rtt min/avg/max/mdev = 4.608/4.788/4.910/0.130 ms
```

Si nuestro caso es el contrario podemos utilizar un cable ethernet y conectarlo directamente al equipo por dicho puerto. En el caso contrario tenemos que usar una lista de comandos para poder conectarnos a una red inalambrica.

La herramienta que vamos a utilizar en esta ocacion sera **wpa_supplicant**, esta herramienta nos permite conectarnos a una red solamente creado un archivo de configuracion donde agregaremos los datos de nuestra red (nombre, contraseña) que se hace de la siguiente forma:

```bash
root@archiso ~# wpa_passphrase "NOMBRE DE RED" "PASSWORD" > /$HOME/wpa_supplicant/wpa_suplicant.conf
```
El comando **wpa_passphrase** nos ayuda con la creacion del archivo de configuracion de red, nos hace una sintaxis mas organizada y que wpa_supplicant pueda enterder y que no de errores.
Para poder verificar que los datos quedaron correctamente agregados al archivo usaremos un comando:

```bash
cat $HOME/wpa_supplicant.conf
```

Tendremos una salida como la siguiente:

```bash
───────┬───────────────────────────────────
       │ File: $HOME/wpa_supplicant/wpa_supplicant.conf
───────┼───────────────────────────────────
   1   │ network={
   2   │     ssid="NOMBRE DE RED"
   3   │     #psk="PASSWORD"
   4  psk=6a3bcf1c686f9ab7f267cc8f9e1e199019e6274fccde69dc10467f35339a8f
       │ 9a
   5   │ }
───────┴───────────────────────────────────
```

Una vez ya tengamos nuestro archivo de configuracion procedemos a usar **wpa_supplicant**:

```bash
wpa_supplicant -B -D nl80211,wext -c $HOME/wpa_supplicant.conf -i interface-de-red
```




