---
title: "Instalación de Miniconda"
layout: post
date: 2024-06-12 21:00
star: true
tag:
    - Hacking 
    - herramientas
    - Archlinux
category: blog
author: hacklexander
description: Instalación de herramienta de entorno virtual de python
---


[Installing on Linux — conda](https://docs.conda.io/projects/conda/en/latest/user-guide/install/linux.html) 


![]({{site.url}}/{{site.anexos}}/miniconda/logo.svg)


Miniconda es un instalador mínimos proporcionado por *Anaconda*. Es una versión reducida de Anaconda que incluye solo Conda, Python y algunos paquetes esenciales.

- *Configurar*

```bash
conda config --set auto_activate_base false
```


- *Crear el entorno*
	Podemos crear un entorno con Python y paquetes específicos, por ejemplo:

```bash
conda create --name mi_entorno python=3.8
```

- *Activar el entorno* 

```bash
conda activate mi_entorno
```


