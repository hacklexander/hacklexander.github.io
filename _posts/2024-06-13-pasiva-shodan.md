---
title: "Herramienta pasiva -> Shodan"
layout: post
date: 2024-06-13 21:00
star: true
image: /assets/images/shodan/logo.jpg 
headerImage: true
tag:
    - Hacking 
    - Herramienta
    - Pasiva
category: blog
author: hacklexander
description: Herramienta utilizada para la recopilación de datos pasiva  
---


[Shodan](https://www.shodan.io/) es un motor de búsqueda que sirve para encontrar dispositivos escaneados conectados a internet. Este buscador se vale del escaneo de puertos, realizado por miles de usuarios, cuyos resultados se almacenan en sus servidores para que otros puedan consúltalos. La ventaja de **shodan** es que pueden revisar estos datos sin necesidad de interactuar con dichos puertos.



---


### Comandos principales


A continuación se presentan algunos de los filtros más relevantes para el uso de Shodan:

- `after`: Only show results after the given date (dd/mm/yyyy) string
    
- `asn`: Autonomous system number string
    
- `before`: Only show results before the given date (dd/mm/yyyy) string
    
- `category`: Available categories: ics, malwarestring
    
- `city`: Name of the city string
    
- `country`: 2-letter country code string
    
- `geo`: Accepts between 2 and 4 parameters. If 2 parameters: latitude, longitude. If 3 parameters: latitude, longitude, range. If 4 parameters: top left latitude, top left longitude, bottom right latitude, bottom right longitude.
    
- `hash`: Hash of the data property integer
    
- `has_ipv6`: True/False boolean
    
- `has_screenshot`: True/False boolean
    
- `server`: Devices or servers that contain a specific server header flag string
    
- `hostname`: Full host name for the device string
    
- `ip`: Alias for net filter string
    
- `isp`: ISP managing the netblock string
    
- `net`: Network range in CIDR notation (ex.199.4.1.0/24) string
    
- `org`: Organization assigned the netblock string
    
- `os`: Operating system string
    
- `port`: Port number for the service integer
    
- `postal`: Postal code (US-only) string
    
- `product`: Name of the software/product providing the banner string
    
- `region`: Name of the region/state string
    
- `state`: Alias for region string
    
- `version`: Version for the product string
    
- `vuln`: CVE ID for a vulnerability string


---


#### top 5 de shodan dorks


- **Encuentra cámaras** 

	Lo primero que veremos en esta lista es que puedes encontrar cámaras conectadas a internet, cuya ciberseguridad no se haya configurado bien. Este es un fallo común debido a una mala configuración, el comando es el siguiente:
	
	```bash
	> NETSurveillance uchttpd
	```

- **Encuentra dispositivos con VNC (Visual Network Computing)**

	VNC es un software que permite manejar remotamente un ordenador, para halla algunos dispositivos que tiene este programa, puede poner los siguientes comandos:
	
	```bash
	> «authentication disabled» port:5900,5901
	```


- **Encuentra fallos en Spring Boot**
	
	Para encontrar vulnerabilidades en aplicaciones desarrolladas con Spring Boot. podemos usar el siguiente comando:
	
	```bash
	> org:Tu_Objetivo http.favicon.hash.116323821
	```


- **Encuentra bases de datos**

	Para encontrar **bases de datos** elaboradas con softwares como **MongoDB**, **MySQL** o **Elastic Search**, puede probar los siguientes comandos:

	```bash 
	> «MongoDB Server Information» port:27017 -authentication

	> mysql port:»3306″ 
	
	> port:»9200″ all:»elastic indices»
	```

- **Encuentra sistemas operativos**

	Para poder encontrar sistemas operativos como **Windows** o **Linux** podemos usar los siguientes comandos: 

	```bash
	> os:»windows 7″
	
	> os:»Linux»
	```

---
---



