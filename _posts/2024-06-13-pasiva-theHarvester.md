---
title: "Herramienta pasiva -> theHarvester"
layout: post
date: 2024-06-13 21:00
star: true
image: /assets/images/theHarvester/logo.webp 
headerImage: true
tag:
    - Hacking 
    - Herramienta
    - Pasiva
category: blog
author: hacklexander
description: Herramienta utilizada para la recopilación de datos pasiva  
---

[TheHarvester](https://github.com/laramies/theHarvester) es una herramienta de seguridad informática utilizada para recopilar información en investigaciones de OSINT **(Inteligencia de Fuentes Abiertas)**. Fue desarrollada  por Christian Martorella y es ampliamente utilizada para obtener información de sitios web, bases de datos, directorios y redes sociales. 

Durante la fase de reconocimiento en una evaluación de red team o penetration test, theHarvester realiza la recopilación de inteligencia de fuentes abiertas para ayudar a determinar el panorama de amenazas externas de un dominio. Algunos de los datos que puede extraer incluyen:

- **Nombres**
- **Correos electrónicos**
- **IPs**
- **Subdominios**
- **URLs**


La herramienta utiliza múltiples recursos públicos, como motores de búsqueda y bases de datos, para obtener esta información. 
Algunos de los módulos pasivos que utiliza son:


- **Anubis-DB ->** Base de datos de Anubis.

- **Baidu ->** Motor de búsqueda de Baidu.

- **Bing ->** Motor de búsqueda de Microsoft.

- **Censys ->** Motor de búsqueda que utiliza certificados para enumerar subdominios y recopilar correos electrónicos.

- **DuckDuckGo ->** Motor de búsqueda de DuckDuckGo.

- **Github ->** Motor de búsqueda de código en GitHub.

- **Hunter ->** Motor de búsqueda de correos electrónicos.

- **Intelx ->** Motor de búsqueda de Intelx.

- y otros....


---


### Ejemplos 


1. Para buscar correos electrónicos relacionados con un dominio, por ejemplo **microsoft.com**. Utilizamos google como fuente de datos y limitando los resultados a 500:

```bash
> theharvester -d microsoft.com -l 500 -b google
```


2. Para buscar claves PGP **(Pretty Good Privacy)** y relacionadas con el dominio **microsoft.com**: 
```bash
> theharvester -d microsoft.com -b pgp
```


3. Para buscar nombres de empleados relacionados con el dominio **microsoft** utilizando **Linkedln** como fuente de datos y limitando los resultados a 200:
```bash
> theharvester -d microsoft -l 200 -b linkedin
```


4. Para buscar correos electrónicos relacionados con el dominio **apple.com** utilizando **Google Custom Search Engine** (GoogleCSE) como fuente de datos, limitando los resultados a 500 y comenzando desde el resultado número 300:

```bash
> theharvester -d apple.com -b googleCSE -l 500 -s 300
```
 
> Para poder enviar todo el output a un fichero podemos usar el parámetro **-f** seguido del nombre del archivo donde lo queremos guardar.


---


### Bloqueo temporal de dirección IP pública


Después de realizar algunas peticiones con TheHarvester es posible que aparezca un error similar al siguiente:

![]({{site.url}}/{{site.anexos}}/theHarvester/picture.png)


Este error nos indica que Google ha bloqueado nuestra dirección IP pública. Lo que quiere decir que no nos deja realizar peticiones a su servicio desde ningún dispositivo que se encuentre dentro de nuestra red local. 

Este comportamiento es muy frecuente y también debe tenerse en cuenta para las siguientes herramientas que se presentan en esta sección. Si realizas muchas peticiones automatizadas en poco tiempo a servicio como Google, Bing, Shodan, etc. Utilizando herramientas como TheHarvester, estos servicios suelen bloquear temporalmente tu dirección IP publica para que no los satures.

Para resolver este problema tienes varias alternativas:

1. La mas sencilla es esperar un tiempo hasta que el servicio correspondiente desbloquee tu dirección IP pública. Esto suele tardar unos minutos o, como mucho, unas pocas horas. Probablemente si repites el mismo ejercicio dentro de unos minutos, comprobarás que ya te ha desbloqueado la IP.

2. La segunda mas sencilla es reiniciar tu router. en muchas ocasiones tu proveedor de internet te asigna una dirección IP pública de manera dinámica, por lo tanto, apagando y encendiendo el router fuerzas a que se te asigne una dirección IP pública nueva que no estará bloqueada. Ten en cuenta que esto depende de tu proveedor de interne y que no siempre funciona, podemos comprobar nuestra dirección IP pública, podemos usar el siguiente link -> https://www.whatsmyip.org/

3. Podemos utilizar algún mecanismo de anonimización que te permita conectarte a internet a través de otra región y, por lo tanto, con otra dirección IP pública. El mecanismo mas común es utilizar una VPN. Existen muchos servicios de VPN gratuitos, por mi experiencia personal te recomiendo ProtonVPN. Este servicio tiene una versión gratuita que puedes utilizar. 

4. Por último, puedes cambiar la fuente en la que realizar la búsqueda y utilizar otras diferente. Por ejemplo, si te bloquea Google, puedes realizar las peticiones a Bing o DuckDuckGo, para ello utiliza la opción `-b` de TheHarvester.


Estas serían las opciones mas sencillas para resolver el problema. También existirán otras alternativas interesantes un poco mas complejas, como por ejemplo, utilizar un proxy público para la salida a internet o conectarte mediante la red TOR.


---


Para poder usar la versión anterior que exporta el output en formato HTML y que es mas legible, debemos hacer uso de una herramienta llamada **miniconda** que se va encargar de crear un entorno virtual donde instalaremos dicha versión sin alterar el resto del sistema.

La versión recomendada en esta ocasión es la 3.2.2 


----------


### Instalación 


Lo primero que debemos hacer una vez instalado minconda es crear nuestro nuevo entorno, y usaremos el siguiente comando:

```bash
conda create -n old_theharvester python=3.8
```


Una vez creado nuestro entorno debemos ingresar con el siguiente comando:

```bash
conda activate old_theharverster
```


Ahora para tener mas organización en nuestro entorno creamos un nuevo directorio donde instalaremos la herramienta, con el comando:

```bash
mkdir old_theharvester
cd old_theharvester
```


En este punto lo que debemos hacer es descargar el código fuente en el directorio actual, el programa que usaremos será **wget** seguido de la url:

```bash
wget https://github.com/laramies/theHarvester/archive/refs/tags/3.2.2.zip
```


Después de que este en el directorio debemos descomprimirlo con **unzip**:

```bash
unzip 3.2.2.zip
cd theHarvester-3.2.2
```


Ahora debemos instalar los requerimientos con el siguiente comando:

```bash
pip install -r requirements/base.txt
```


Una vez instalados todos los requerimientos necesarios podemos empezar a usar esta herramienta con una versión diferente a la que usamos en nuestro sistema normalmente, el comando que debemos usar es:

```bash
python theharvester -h
```


Ahora para poder usar la herramienta con el y volcar el output a otros archivos diferentes a la ultima versión debemos hacer las consultas igual que con la ultima versión, por ejemplo:

```bash
theharvester -d microsoft.com -l 500 -b google -f resultados
```


Para poder visualizar el resultado debemos abrir el archivo .html con cualquier navegador que tengamos instalado.


---
---

