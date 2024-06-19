---
title: "Herramienta Semi-pasiva -> FOCA"
layout: post
date: 2024-06-15 23:10
star: true
image: /assets/images/FOCA/logo.jpg 
headerImage: true
tag:
    - Hacking 
    - Metodologías 
    - Semi-pasiva 
    - Metadatos
category: blog
author: hacklexander
description: Herramienta para hacer escaneo de Metadatos en Windows.
---



## ¿Qué es [FOCA](https://github.com/ElevenPaths/FOCA)?

FOCA -> Fingerprinting Organizarions with Collected Archives

Es una herramienta desarrollada principalmente por **EkevenPaths** que se utiliza para encontrar metadatos e información oculta en los documentos que escanea. Estos documentos pueden estar en páginas web y se pueden descargar y analizar con FOCA. La herramienta es capaz de analizar una amplia variedad de documentos, siendo los más comunes los archivos de **Microsoft Office, Open Office o PDF**, aunque también analiza archivos de **Adobe inDesing o SVG**, por ejemplo. 

FOCA busca esto documentos utilizando tres motores de búsqueda posibles -> **Google, Bing y DuckDuckGo**. La suma de los resultados de los tres motores arroja una gran cantidad de documentos. Además, es posible agregar archivos locales para extraer la información **EXIF** de los archivos gráficos, y se realiza un análisis completo de la información descubierta a través de la **URL** incluso antes de descargar el archivo. 


