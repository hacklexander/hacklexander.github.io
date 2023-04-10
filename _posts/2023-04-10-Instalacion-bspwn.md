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

para esto debemos ir a mi [***repositorio***](https://github.com/hacklexander/dotfiles-bspwm) en git hub donde estaran unos directorios y archivos de configuracion que necesitaremos para darle vida a bspwm.

# Instalacion de dependencias

Primero instalamos el AUR Helper  **`yay`**:

```bash
cd $HOME
git clone https://aur.archlinux.org/yay.git
cd yay
makepkg -si --noconfirm
cd ..
rm -rf yay
```


Instalamos todos los paquetes necesarios:

```bash
yay -Syy polybar sxhkd todotxt xclip kitty \
		brightnessctl dunst rofi lsd bat jq \
		xfce-polkit playerctl mpd nautilus \
		ncmpcpp ranger mpc picom xfce4-power-manager-git \
		feh ueberzug maim pamixer libwebp \
		webp-pixbuf-loader xorg-xprop xorg-xkill \
		physlock papirus-icon-theme betterlockscreen zsh \
		zsh-autosuggestions zsh-history-substring-search \
		zsh-syntax-highlighting zsh-theme-powerlevel10k
```

Habilitamos servicios:

```bash
sudo systemctl enable mpd.service
sudo systemctl start mpd.service
```
# Instalacion Dotfiles

Posteriormente a esto lo que tendremos que hacer un git clone para descargar el repositorio y tenerlo localmente, aconsejo clonarlo en la carpeta **`/tmp`**, los comandos son los siguientes:

```bash
cd /tmp
git clone https://github.com/hacklexander/dotfiles-bspwm.git
cd dotfiles-bspwm/
```

Una vez tengamos el repositorio de manera local, lo que tenemos que hacer es copear las carpetas del directorio **`config/`**, los comandos son lo siguientes:

```bash
cp -r config/* ~/.config
```

Ahora haremos lo mismo con el direcorio **`fonts/`**:

```bash
mkdir -p ~/.fonts
cp -r fonts/* ~/.fonts
```

Copiamos el directorio **`bin/`** en **`$HOME/.local/bin`**:

```bash
cp -r bin/* ~/.local/bin
```

Copiamos los archivos de configuracion que esta en **`home/`** 

```bash
cp -r home/* $HOME
```

---



# ----------------------------------------------------------------------------
Estas configuraciones estan basadas mayormente en los dotfiles de ***[gh0stzk](https://github.com/gh0stzk/dotfiles)*** y de ***[rxyhn](https://github.com/rxyhn/tokyo)***, dejo los creditos correspondientes, tambien hay configuraciones personales, puede que a todos no les guste, pero no esta de mas que las puedan probar y darme su opinion constructiva.
# ----------------------------------------------------------------------------
















