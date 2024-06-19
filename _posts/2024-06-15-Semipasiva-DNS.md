---
title: "¿Qué es el protocolo DNS?"
layout: post
date: 2024-06-15 23:35
star: true
image: /assets/images/ProtocoloDNS/logo.png 
headerImage: true
tag:
    - Hacking 
    - Metodologías 
    - Semi-pasiva 
    - DNS
category: blog
author: hacklexander
description: Herramienta Web utilizada para protocolos DNS.
---




# ¿Qué es DNS?

- DNS -> **Domain Name System**

- Realiza una traducción de nombres de dominio a direcciones IP

- Se corresponde con uno de los protocolos más importantes de internet.

---

# ¿Por qué nos interesa el DNS?

- **Obtener información pública** sobre un dominio o una organización

- **Descubrir relaciones** entre dominio y hosts.

- Técnicas de explotación especificas para ganar acceso 
	-> (**DNS Spoofing**).

---

# ¿Cómo funciona DNS?

- DNS Zone -> Agrupación de registros (datos) DNS.

- Las DNS Zones contienen diferentes tipos de registros:


| Tipo     | Significado             | Valor                                   |
| -------- | ----------------------- | --------------------------------------- |
| SOA      | Start of Authority      | Pará metros para esta zona              |
| A / AAAA | Dirección IP de un host | 32 bits                                 |
| MX       | Mail Exchange           | Dominio para correo                     |
| NS       | Name Server             | Nombre de un servidor para este dominio |
| Cname    | Canonical Name          | Alias del nombre del dominio            |
| PTR      | Pointer                 | Alias para una dirección IP             |
| SRV      | Services Description    | Servicios Disponibles                   |
| TXT      | Text                    | Información de texto                    |



![Grafico]({{site.url}}/{{site.anexos}}/ProtocoloDNS/graphic.png)



## Herramientas

- [Central Ops]({{site.url}}/Semipasiva-DNS-centralOps/)

- [DNS-Dumpster]({{site.url}}/Semipasiva-DNS-Dumpster/)
