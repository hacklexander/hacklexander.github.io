---
title: "Herramienta pasiva -> Whois"
layout: post
date: 2024-06-13 21:00
star: true
image: /assets/images/whois/logo.jpg 
headerImage: true
tag:
    - Hacking 
    - Herramienta
    - Pasiva
category: blog
author: hacklexander
description: Herramienta utilizada para la recopilación de datos pasiva  
---

## ¿Qué es Whois y cómo funciona en linux?


Whois es un comando de Linux que se usa para buscar en la base de datos que almacena la información del registrante de un dominio de internet, la dirección IP asignada a un recurso de red y mas. El comando `whois` proporciona una manera fácil de acceder a esta información desde la línea de comandos.


---


#### Instalación 


- Debian -> ```sudo apt install whois ```
- Arch     -> ```sudo pacman -S whois```


---


#### Uso básico de whois


El uso más básico del comando `whois` es buscar información sobre un dominio.
Simplemente escribe `whois` seguido del nombre del dominio que deseas consultar.

```shell 
whois example.com
```

Así proporcionará información detallada sobre el dominio `example.com` incluyendo el nombre del registrante, la organización, la dirección de contacto, los servidores de nombres, las fechas de creación y expiración del dominio, mucho mas.


---


#### Opciones comunes del comando whois


Para poder personalizar nuestras búsquedas y obtener información que necesitamos de manera mas eficiente. Tenemos las siguientes opciones:

- *-H* -> Esta opción oculta el mensaje legal que normalmente se muestra al inicio de la salida de `whois`.

- *-i* -> Permite buscar por un campo específico, como el nombre del registrante o la dirección de correo electrónico.

- *-p* -> Especifica el puerto a utilizar para la conexión con el servidor whois.

- *-h* -> Te permite especificar un servidor whois específico para la consulta.


---


#### Ejemplos práctico de whois 


Además de buscar información de dominio, `whois` también puede ser utilizado para obtener información sobre direcciones IP. Aquí realizamos un ejemplo sobre esta dirección `192.0.2.1` 

```bash
whois 192.0.2.1
```

Este comando devolverá información sobre a quién está asignada esa IP. incluyendo la organización, la ubicación, y mas.


---


#### Mejores prácticas para el use de whois en Linux


- *Privacidad:* Ten en cuenta que la información que buscas puede ser sensible. Utiliza whois de manera responsable.

- *Automatización:* Para tareas repetitivas, considera escribir scripts que utilicen whois para automatizar consultas.

- *Actualización:* Asegúrate de que tu sistema y el paquete whois estén siempre actualizados para aprovechar las últimas mejoras y características de seguridad.


---
---
