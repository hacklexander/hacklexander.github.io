---
title: "Herramienta Semi-pasiva -> DNS-Dumpster"
layout: post
date: 2024-06-15 23:40
star: true
image: /assets/images/DNSdumpster/logo.jpg 
headerImage: true
tag:
    - Hacking 
    - Metodologías 
    - Semi-pasiva 
    - DNS
category: blog
author: hacklexander
description: Herramienta utilizada para protocolos DNS.
---

[DNS-Dumpster](https://dnsdumpster.com/) es una herramienta en línea utilizada para obtener información detallada sobre un dominio y su infraestructura de DNS. Proporciona un conjunto de funciones que permiten realizar investigaciones de DNS de manera rápida y sencilla. Ahora veremos los servicios con los que disponemos en esta herramienta:


- **Descubrimiento de subdominios** 
-> Nos permite encontrar subdominio asociados a un dominio específico. Esto es útil para identificar todos los hosts visibles desde la perspectiva de un atacante.

- **Registros DNS**
-> Además de los subdominios, muestra información sobre registros DNS del dominio. Esto incluye registros MX (para correo electrónico), registros TXT (para autenticidad) y otros detalles relacionados con la configuración DNS.

- **Búsqueda inversa de DNS**
-> Podemos buscar dominios asociados a una dirección IP especifica. Esto es útil para investiga las relaciones entre diferentes dominios e IP dentro de una infraestructura dada.

- **Fuente de datos**
-> Utiliza recursos de inteligencia de código abierto para consultar datos relacionados con el dominio. Estos datos se recopilan de rastreos de los 1 millón de sitios principales según Alexa, motores de búsqueda, Common Crawl, Certificate Transparency, Max Mind, Team Cymru, Shodan y Scans.io.



