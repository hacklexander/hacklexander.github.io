---
title: "Herramienta Semi-pasiva -> Metagoofil"
layout: post
date: 2024-06-15 23:20
star: true
image: /assets/images/metagoofil/logo.jpg 
headerImage: true
tag:
    - Hacking 
    - Metodologías 
    - Semi-pasiva 
category: blog
author: hacklexander
description: Herramienta para hacer escaneo de Metadatos.
---


## ¿Qué es [Metagoofil](https://github.com/opsdisk/metagoofil)?

Metagoofil es una herramienta que se encarga de buscar en Google tipos específicos de archivos alojados públicamente en un sitio web y, opcionalmente, la descarga a su caja local. Esto es útil para la recopilación de inteligencia de código abierto, las pruebas de penetración o la determinación de qué archivos su organización se está filtrando a indexadores de búsqueda como Google. A modo de ejemplo utiliza la siguiente consulta de Google para encontrar todos los archivos que se alojan opcionalmente, descarga una copia local.

una búsqueda como ejemplo podría ser 

-> **site:example.com  iletype:pdf** 


Esta herramienta viene instalada por defecto en la distribución de **Kali linux** 


---

Si comienzas a recibir errores HTTP 429, Google te ha detectado correctamente como bot y bloqueará tu IP durante un período de tiempo, Una solución es usar **proxychains** y un banco de proxys para redondear las búsquedas.


para poder instalarlo podemos usar el siguiente comando en la shell

```bash
sudo apt install proxychains4 -y
```

solo hay que editar el archivo de configuración para realizar las búsquedas a través de diferentes servidores proxy. En el siguiente ejemplo se han configurado 3 proxys Socks dinámicos diferentes con diferentes puertos de escucha locales (9050 y 9051) 

En el siguiente link [Cyber Manual del fontanero y laboratorio interactivo](https://gumroad.com/l/cph_book_and_lab) podemos aprender sobre Secure Shell **(SSH)** la construcción de túneles, la redirección de puertos y la flexión de tráfico como un jefe.

el Archivo de configuración esta en la ruta -> /etc/proxychains4.conf


Copiamos la siguiente configuración en ese archivo:

```bash
round_robin
chain_len = 1
proxy_dns
remote_dns_subnet 224
tcp_read_time_out 15000
tcp_connect_time_out 8000
[ProxyList]
socks4 127.0.0.1 9050
socks4 127.0.0.1 9051
```

Coloque delante del script de Pyhton y cada búsqueda pasara por un proxy diferente (ósea por una IP diferente). Incluso podría reducir el tiempo de retardo porque aprovechará un proxy diferente buzones.


Ejemplo de una búsqueda en github.com implementado la herramienta de proxychains

```bash
proxychains4 python metagoofil.py -d https://github.com -f -t pdf,doc,xls
```




