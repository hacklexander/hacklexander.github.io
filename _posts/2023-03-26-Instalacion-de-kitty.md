---
title: "Instalacion de kitty"
layout: post
date: 2023-03-26 21:00
image: /assets/arch/kitty/kitty.jpg
headerImage: true
star: true
tag:
- kitty
- bspwm
- Archlinux
- instalacion
category: blog
author: hacklexander
description: Instalaremos kitty
---

# actualizamos repositorios

Antes que instalemos cualquier cosa debemos tener los repositorios actualizados, solo debemos escribir el siguiente comando:

```bash
sudo pacman -Syy
```
---

Una vez hecho esto, nos disponemos a instalar nuestra kitty.

```bash
sudo pacman -S kitty --noconfirm
```

una vez instalada debemos crear un archivo de configuracion en el directorio ~/.config, podemos encontrar un archivo de ejemplo en el directorio /usr/share/doc/kitty. Lo que debemos hacer es copiar el archivo .config que se encuantra en estre archivo, lo haremos de la siguiente forma.

```bash
mkdir ~/.config/kitty
sudo cp -r /usr/share/doc/kitty/kitty.conf ~/.config/kitty 
cat ~/.config/kitty/kitty.config
```



```bash
zsh zsh-autosuggestions zsh-history-substring-search zsh-syntax-highlighting
```