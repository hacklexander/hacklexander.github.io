---
title: "Primeros pasos"
layout: post
date: 2023-03-27 20:10
image: /assets/images/markdown.jpg
headerImage: false
star: true
tag:
- Inicio
- VMWare
- VirtualBox
category: blog
author: hacklexander
description: comenzamos hablar sobre las formas de que se puede instalar la imagen de Arch
---



# Vamos a crear nuestra distribucion personalizada a nuestro gusto¡

Bueno primero que todo tenemos que preparar nuestro equipo para empezar con la descarga e instalacion de nuestro sistema.

Nuestra distribucion en este caso sera basada en una muy reconocida llamada Arch, para las personas que llevan un tiempo conociendo el tema de del kernel y como interactua el sistema con el hardware de nuestros equipos, Arch es una muy buena distribucion de linux; porque viene practicamente limpia, es decir. tenemos solo una linea de comandos y por ahi tenemos que hacer todos los pasos necesarios para la instalacion.

---
# Formas de instalacion

## Hardware
- En disco duro (HDD)
- Unidad de estado solido (SDD)
- Unidad de memoria flash
- Pendrive (USB)
- CD's / DVD's

>Si vamos hacer esta instlacion tenemos que descargar una utilidad que nos ayude a montar una unidad con la imagen del sistema, aqui abajo les voy a dejar unas que son muy conocidas en **Windows** y en **Linux**.
Claro esta que estas no son las unicas herramientas que hay para estos sistemas, pero son de las mas conocidas y mas utilizadas por las personas nuevas y que ya llevan cierto tiempo.
>- Windows --> [RUFUS](https://rufus.ie/es/)
>- Linux --> [ETCHER](https://www.balena.io/etcher)

## Maquina-Virtual
Las mas usadas son:

### [VirtualBox](https://www.virtualbox.org/)

Es una herramienta para hacer máquinas virtuales de sistemas operativos. Esto quiere decir que si tienes un ordenador con sistemas operativos como: (Windows, GNU/Linux, macOS), puedes crear una **máquina virtual** con cualquier otro sistema operativo para utilizarlo dentro del que estés usando y poder usarlos en pararelo.

[VMWare](https://www.vmware.com/)

Esta herramienta es muy similar a la anterior, tambien crea las maquinas virtuales, pero tiene unas opciones diferentes a la anterior, tambien es compatible con los sistemas operativos (Windows, GNU/Linux, macOS)

---

# Descarga de Recursos

En este caso vamos a crear nuestra distro en una maquina virtual con la herramienta de **VMWare** y utilizare otra herramienta donde guardaremos nuesto imagen de Arch linux, pero en simultaneo podremos agregar otras y poder usarlas al tiempo sin ninguno conflicto entre ellas, esta se llama **Ventoy** la dejare abajo en los links.

- ### Imagen [Archlinux](https://archlinux.org/download/)


- ### Maquina Virtual

    - Herramienta --> [**VMWare**](https://customerconnect.vmware.com/downloads/details?downloadGroup=WKST-PLAYER-1701&productId=1377&rPId=100675)

    - Herramienta --> [**VirtualBox**](https://www.virtualbox.org/wiki/Downloads)

- ### Boot USB
    - Windows --> [RUFUS](https://rufus.ie/downloads/)
    - Linux --> [ETCHER](https://www.balena.io/)
    - [Ventoy](https://www.ventoy.net/en/download.html)


---
# creacion de la maquina virtual

Entramos en VMWare y creamos una nueva máquina virtual:


>![Primera ventana]({{site.url}}/{{site.install}}01.png)

Cargamos la ISO de Arch Linux:


>![carga de imagen]({{site.url}}/{{site.install}}02.png)

Seleccionamos Linux en la parte de sistema operativo:


>![linux]({{site.url}}/{{site.install}}03.png)

Asignamos el nombre con el que queremos identificar nuestra maquina virtual:


>![Nuevo nombre]({{site.url}}/{{site.install}}04.png)

Asignamos un tamaño máximo de disco de 80G en mi caso (Puedes elegir un tamaño a tu gusto), con la opción **Store virtual disk as a single file**:

>![Disco]({{site.url}}/{{site.install}}05.png)

Asignamos una cantidad de memoria RAM a criterio de cada uno, en mi caso elegi 4GB :

>![Configuracion]({{site.url}}/{{site.install}}06.png)

Finalizamos la creación de la máquina virtual, arrancamos y verificamos que todo funciona:

>![Final de creacion]({{site.url}}/{{site.install}}07.png)

---


Como pudimos ver, en este post nombramos todos los requisitos para empezar a instalar nuestro sistema, en el siguiente post tendremos todos los pasos a seguir para finalizar nuestra instalacion base.

Gracias¡¡

---



