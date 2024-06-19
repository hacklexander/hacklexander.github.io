---
title: "Herramienta Semi-pasiva -> TCP-Dump"
layout: post
date: 2024-06-15 23:50
star: true
image: /assets/images/TCP-Dump/logo.png 
headerImage: true
tag:
    - Hacking 
    - Metodologías 
    - Semi-pasiva      
category: blog
author: hacklexander
description: Herramienta para capturar y analizar el trafico de red.
---

## ¿Qué es [TCPDUMP y LIBPCAP](https://www.tcpdump.org/)?

TCPdump es una herramienta de línea de comando completamente gratuita que te permite captura y analizar todo el tráfico de red en una o varias interfaces. 

---

## Características calve

1. **Captura de tráfico**

	-> **Interfaces compatibles:** Se puede capturar tráfico de interfaces como Ethernet, WI-FI, PPPoE e incluso interfaces virtuales sutilizada en redes privadas virtuales (VPNs).

	-> **Análisis en tiempo real:** Podemos analizar el tráfico en tiempo real mientras lo capturas.

2. **Compatibilidad con sistemas operativos**

	-> TCPdump es compatible con sistemas operativos basados en UNIX, como Linux, BSD y MacOS.

	-> Utiliza la biblioteca **libpcap** para capturar paquetes que circulan a través de una interfaz, ya sea física o virtual.

3. **Privilegios de superusuario**

	-> Para ejecutar TPCdump, necesitas privilegios de superusuario (administrador) debido a que estás capturando y visualizando tráfico de res sensible.

4. **Funcíon Principal**

	-> **Sniffing:** TCPdump se utiliza para monitorizar redes. Realiza funciones de **Sniffing**, lo que significa que captura y analiza paquetes en la red.

5. **Filtros personalizados** 

	Podemos aplicar filtros para ver solo trafico relevante.

	-> Filtrar por dirección IP, protocolo, puerto, etc.

	-> Sin filtros, verás todo el tráfico de la interfaz seleccionada.


