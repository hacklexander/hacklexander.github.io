---
title: "Instalación de Metasploitable3"
layout: post
date: 2024-06-12 21:00
star: true
tag:
    - Hacking 
    - herramientas 
    - Archlinux
category: blog
author: hacklexander
description: Instalación de la herramienta para hacer pruebas de pentesting  
---


[Metasploitable3 - Github](https://github.com/rapid7/metasploitable3)


Metasploitable3 es una máquina virtual (VM) creada desde cero con **una gran cantidad de vulnerabilidades de seguirdad.** Su propósito principal es servir como objetivo para probar exploits con Metasploit. En otras palabras, es un entorno de laboratorio diseñado específicamente para que los profesionales de la seguridad puedan simular ataques y evaluar cómo funcionan las herramientas de explotación. 

---

### Detalles clave


- **Origen:** Metasploitable3 es un proyecto de **Rapid7**, una empresa de seguridad informática.

- **Licencia:** Está disponible bajo la licencia de tipo **BSD**.

- **Uso:** Los profesionales de la seguridad pueden utilizar Metasploitable3 para:

	-> Probar exploits y vulnerabilidades. 

	-> Aprender sobre técnicas de ataque y defensa.
	
	-> Realizar pruebas de penetración en un entorno controlado.

- **Configuración:** Utiliza Vagrant y una imagen ligera de Ubuntu 14.04 para configurar y personalizar rápidamente Metasploitable3 para desarrollo o personalización.


---
---


# Instalación


En el repositorio oficial no ofrece varias formas para poder instalar y configurar este entorno virtual, pero en esta ocasión vamos a utilizar una forma bastante sencilla y practica.



1. entramos al siguiente [Link](https://app.vagrantup.com/rapid7/)


![]({{site.url}}/{{site.anexos}}/metasploitable3/captura-07.png)


---


2. Ahora lo que debemos hacer es descargar los archivos en el programa donde la queramos configurar.


|<img src="{{site.url}}/{{site.anexos}}/metasploitable3/captura-08.png" align="center" width="400px">|<img src="{{site.url}}/{{site.anexos}}/metasploitable3/captura-09.png" align="center" width="400px">|


![]({{site.url}}/{{site.anexos}}/metasploitable3/captura-10.png)


---


3. Después de que las tengamos descargadas, lo que debemos hacer es renombras los archivos agregándole **.zip** sin borrar ninguna letra, solo le agregamos eso y procedemos a descomprimir ambos archivos.


|<img src="{{site.url}}/{{site.anexos}}/metasploitable3/captura-11.png" align="center" width="400px">|<img src="{{site.url}}/{{site.anexos}}/metasploitable3/captura-12.png" align="center" width="400px">|


![]({{site.url}}/{{site.anexos}}/metasploitable3/captura-13.png)


---


4. Ahora nos quedaron 2 carpetas con el mismo nombre del archivo.

![]({{site.url}}/{{site.anexos}}/metasploitable3/captura-14.png)


---


5. Lo que tenemos que hacer ahora es ingresar en ambas carpetas y repetir el procedimiento con los archivos que están en dichas carpetas.



|<img src="{{site.url}}/{{site.anexos}}/metasploitable3/captura-15.png" align="left" width="400px">|<img src="{{site.url}}/{{site.anexos}}/metasploitable3/captura-16.png" align="left" width="400px">|


---


6. Descomprimimos los archivos renombrados de ambas carpetas. 


![]({{site.url}}/{{site.anexos}}/metasploitable3/captura-17.png)


---


7. Nos quedaran los siguientes archivos que podremos utilizar para agregarlos al programa de virtualización que seleccionamos para configurar Metasploitable3 


|<img src="{{site.url}}/{{site.anexos}}/metasploitable3/captura-20.png" align="left" width="400px">|<img src="{{site.url}}/{{site.anexos}}/metasploitable3/captura-19.png" align="left" width="400px">|


---


8. Ahora lo que debemos hacer es agregarlas a nuestro programa de virtualización con las carpetas renombradas preferiblemente para mayor comodidad.


|<img src="{{site.url}}/{{site.anexos}}/metasploitable3/captura-21.png" align="left" width="400px">|<img src="{{site.url}}/{{site.anexos}}/metasploitable3/captura-22.png" align="left" width="400px">|


---


9. En este punto ya tenemos las máquinas listas para usar.


![]({{site.url}}/{{site.anexos}}/metasploitable3/captura-23.png)


--- 
---


## Configuración de maquinas


#### Ubuntu


1. Procedemos a iniciar en Metasploitable3 de Ubuntu para empezar a configurarla. 

**user** -> vagrant
**password** -> vagrant


![]({{site.url}}/{{site.anexos}}/metasploitable3/captura-24.png)


---


2. Ahora lo que debemos hacer es eliminar las reglas por defecto de *iptables* para que no haya limitación de conexión con las otras maquinas de nuestro entorno.

Lo podemos hacer con el comando:

```bash
sudo iptables -F
```


![]({{site.url}}/{{site.anexos}}/metasploitable3/captura-25.png)


---
---


#### Windows


1. Iniciamos la maquina para configurarla. 

![]({{site.url}}/{{site.anexos}}/metasploitable3/captura-26.png)


**password** -> vagrant

![]({{site.url}}/{{site.anexos}}/metasploitable3/captura-27.png)


![]({{site.url}}/{{site.anexos}}/metasploitable3/captura-28.png)

---


2. Lo que sigue es entrar en los ajustes de red

![]({{site.url}}/{{site.anexos}}/metasploitable3/captura-30.png)

---


3. Entramos ahora a los ajustes avanzados.

![]({{site.url}}/{{site.anexos}}/metasploitable3/captura-31.png)

---


4. Activamos todas las opciones que nos muestra.

![]({{site.url}}/{{site.anexos}}/metasploitable3/captura-32.png)

----


> Esto lo hacemos para permitir que esta maquina se pueda comunicar con otros nodos que tengamos en nuestra red virtual.


---


## Probamos conexión entre maquinas

Teniendo las dos maquinas funcionando simultáneamente comprobamos que IP tienen asignada cada maquina.


![]({{site.url}}/{{site.anexos}}/metasploitable3/captura-33.png)


---

Ahora procedemos a hacer un ping desde alguna de las maquinas para comprobar si se están comunicando.

![]({{site.url}}/{{site.anexos}}/metasploitable3/captura-34.png)


