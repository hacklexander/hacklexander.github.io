---
title: "Recopilación de datos Pasiva"
layout: post
date: 2024-06-13 21:00
star: true
tag:
    - Hacking 
    - Metodologías 
    - Pasiva
category: blog
author: hacklexander
description: Recopilación de datos Pasiva 
---


# Recopilación Pasiva de información 


Recolección de información sobre un objetivo determinado sin que las actividades realizadas por el analista **sean mínimamente detectadas** por el objetivo.

Difícil de realizar y a menudo proporciona resultado poco concluyentes. 

La manera mas habitual de recolección pasiva de información es mediante el acceso a la información almacenada en lugares **públicos.**

Raramente se utiliza de manera individual.


---


### Técnicas pasivas


- #### Hacking con buscadores


**Google Hacking Comandos y Operadores Booleanos**

comandos:

   - **comando:consulta**

        -> **site:dominio** (site:drive)

        -> **filetype:extencion-de-fichero** (filetype:txt or pdf)

        -> **"cadena-texto" / "otra-cadena-texto"** ("index of" / "chat/log")

        -> **inurl:cadena-texto** (inurl:index.php?id=)

        -> **allintitle:cadena-texto**



Si quisiéramos buscar un dump de una base de datos podemos usar este comando: > **filetype:sql "MySQL dump"**

Si queremos buscar una contraseña podemos agregar: > **(pass|password|passwd|pwd)** 

Entonces el ejemplo quedaría así: > **filetype:sql "MySQL dump" (pass|password|passwd|pwd)**


### -> **[Google Hacking Database (GHDB)](https://www.exploit-db.com/google-hacking-database?category=8)**


---
---


## Herramientas

- [Archive.org]({{site.url}}/pasiva-archive_org/)
- [Whois]({{site.url}}/pasiva-whois/)
- [Censys]({{site.url}}/pasiva-cencys/)
- [Google Hacking Comandos y Operadores Booleanos]({{site.url}}/pasiva-google-hacking/)
- [Maltego]({{site.url}}/pasiva-maltego/)
- [Recon-ng]({{site.url}}/pasiva-recon-ng/)
- [Shodan]({{site.url}}/pasiva-shodan/)
- [TheHarvester]({{site.url}}/pasiva-theHarvester/)

