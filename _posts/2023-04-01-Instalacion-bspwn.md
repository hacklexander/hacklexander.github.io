---
title: "Instalacion/configuracion de bspwm"
layout: post
date: 2023-04-10 21:00
image: /assets/arch/bspwm/bspwm.jpg
headerImage: true
star: true
tag:
- bspwm
- Archlinux
- instalacion
category: blog
author: hacklexander
description: Instalaremos y configuraremos el administrador de ventanas llamado bspwm
---

# actualizamos repositorios

Antes que instalemos cualquier cosa debemos tener los repositorios actualizados, solo debemos escribir el siguiente comando:

```bash
sudo pacman -Syy
```
---
# instalacion de bspwm y sxhkd

Procedemos a instalar con el siguiente comando:

```bash
sudo pacman -S bspwm sxhkd --noconfirm
```

una vez instalados debemos crear un archivo de configuracion en el directorio ~/.config, podemos encontrar un archivo de ejemplo en el directorio /usr/share/doc/. Lo que debemos hacer es copiar el archivo con terminacion **rc** que se encuantra en estos direcorios, lo haremos de la siguiente forma.

```bash
mkdir ~/.config/bspwm
sudo cp -r /usr/share/doc/bspwm/examples/bspwmrc ~/.config/bspwm
cat ~/.config/bspwm/bspwmrc
```
![gdm slect]({{site.url}}/{{site.bspwm}}bspwmrc.png)

Tambien debemos hacer esto para el archivo sxhkd.

```bash
mkdir ~/.config/sxhkd
sudo cp -r /usr/share/doc/sxhkd/examples/background_shell/sxhkdrc ~/.config/sxhkd
cat ~/.config/sxhkd/sxhkdrc
```
![gdm slect]({{site.url}}/{{site.bspwm}}sxhkdrc.png)

--- 


Lo que haremos ahora, es reiniciar el equipo y sleccionar bspwm:

![gdm slect]({{site.url}}/{{site.bspwm}}gdm-index.png)

Despues de autenticarnos nos aparecera una pantalla totalmente en negro, pero no te preocupes. En este momento es donde empieza lo bueno!
Empezaremos a instalar todas las herramientas que necesitaremos para nuestro arch y se vea genial!.

para esto debemos ir un repositorio en git hub donde habran unos directorios y archivos de configuracion que necesitaremos para darle vida a bspwm.


Antes de esto instalaremos todo lo que necesitamos, lo haremos con el siguiente comando:

```bash
sudo pacman -S pacman-contrib polybar brightnessctl dunst rofi lsd \
			  jq polkit-gnome git playerctl mpd ncmpcpp geany ranger mpc picom \
			  feh ueberzug maim pamixer libwebp webp-pixbuf-loader xorg-xprop \ xorg-xkill physlock papirus-icon-theme \
			  ttf-jetbrains-mono ttf-jetbrains-mono-nerd ttf-terminus-nerd ttf-inconsolata ttf-joypixels --noconfirm
```


![install dependences]({{site.url}}/{{site.bspwm}}gdm-index.png)

Una vez instalado debemos hacer usa de los repositorios de AUR para instalar eww, el comando es:


```bash
paru -S eww --noconfirm
```
![install eww]({{site.url}}/{{site.bspwm}}gdm-index.png)

Una vez instaladas todas las dependencias vamos a clonar un repositorio y copiar los directorios a la ruta ~/.config:

```bash
git clone 
```


|<img src="{{site.url}}/{{site.bspwm}}primer-parte.gif" alt="inicio grub" align="center" width="400px">|<img src="{{site.url}}/{{site.bspwm}}segunda-parte.gif" alt="neofetch" align="center" width="400px">|

















