---
title: "Instalacion/configuracion de kitty & zsh"
layout: post
date: 2023-04-09 21:00
image: /assets/images/kitty-zsh/kitty.jpg
headerImage: true
star: true
tag:
- kitty
- zsh
- Archlinux
- instalacion
category: blog
author: hacklexander
description: Instalaremos kitty & zsh
---

# actualizamos repositorios

Antes que instalemos cualquier cosa debemos tener los repositorios actualizados, solo debemos escribir el siguiente comando:

```bash
sudo pacman -Syy
```
---


# ------------------ Instalacion de kitty ---------------------------------

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

Pero aqui les dejo un comando que les puede servir, es la configuracion que estoy usando actualmente en mi entorno.

Solo debemos de hacer uso de **`wget`**:

```bash
cd .config/kitty
rm -r *
wget https://raw.githubusercontent.com/hacklexander/dotfiles-bspwm/master/config/kitty/color.ini
wget https://raw.githubusercontent.com/hacklexander/dotfiles-bspwm/master/config/kitty/kitty.conf
ls
```

Ya tendriamos nuestra kitty configurada y funcionando.
pero ahora vamos a cambiar el tipo de shell que estamos usando.

---

# Instalamos la zsh

Podemos verificar la shell que estamos usando con:

```bash 
echo $SHELL 
```

Ahora instalamos la zsh:

```bash
suso pacman -S zsh 
```

Una vez la tengamos instalada la zsh, debemos comprobar que esta instalada correctamente amtes de cambiar el tipo de shell que nuestro sistema esta usando, esto lo hacemos con el siguiente comando:

```bash
chsh -l
```
Ahora el comando para cambiar a zsh es:


```bash
chsh -s /bin/zsh
```

Ahora procedemos a reiniciar nuestro equipo para que los cambios se puedan ver con el comando **`reboot`**.

---

# Plugins para zsh

Lo que mas me gusta de **zsh** es que podemos usar plugins para poder ser mas productivos y tener mas facilidades a la hora de usar nuestra terminal. zsh cuenta con un monton de plugins muy utiles, los puedes verificar con el siguiente link **"[plugins](https://ohmyz.sh/)"**.
Seguimos con la instalacion de los plugins que recomiendo para zsh:

```bash
sudo pacman -S zsh-autosuggestions zsh-history-substring-search zsh-syntax-highlighting
```

Ahora instalaremos sudo-zsh con los siguientes comandos:

```bash
cd /usr/share
mkdir -p zsh-sudo && cd zsh-sudo
wget https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/plugins/sudo/sudo.plugin.zsh
```

# Instalamos powerlevel10k

Vamos a instalar un tema muy conocido y utilizado por ser muy amigable a la vista, dejo una muestra de la configuracion:

![Powerlevel10k](
https://raw.githubusercontent.com/romkatv/powerlevel10k-media/master/configuration-wizard.gif)

>Si quieres ver mas detalles puede ingresar a siguiente link **[powerlevel10k](https://github.com/romkatv/powerlevel10k)**

Lo instalamos con el siguiente comando:

```bash
yay -S zsh-theme-powerlevel10k
```

Ahora lo que tenemos que hacer es configurar con el comando `p10k configure`.

---

Ya en este punto tendremos totalmente configurada nuestra **kitty** con **zsh**, sus plugins y el tema **powerlevel10k**, pero cuando nos convirtamos en root, veremos que la kitty estara como en el pricipio.

la solucion es muy facil, debemos generar un link simbolico para que la configuracion de usuario se refleje tambien en la de root, debemos convertirnos en usuario root con el comando **`sudo su`** y escribir este otro comando para generar el link simbolico:

```bash
ln -s -f ~/.zshrc /root/.zshrc
```
para comprobar debemos escribir **`ls -la`**

![link simbolico]({{site.url}}/{{site.anexos}}/kitty-zsh/link-simbolico-zshrc.png)

Ya con esto cuando nos convirtamos en usuario root podremos ver la misma configuracion.

---

# Instalamos complementos 

Los programas que vamos a instalar son **[lsd](https://github.com/lsd-rs/lsd)** y **[cat](https://github.com/sharkdp/bat)**. Tienen la misma funcionalidad que **`cat`** y **`ls`**, pero estos tiene un formateo mucho mas amigable a la vista. dejo un ejemplo.

|<img src="https://i.imgur.com/rGsdnDe.png" alt="bat" align="left" width="450px" title="bat">|<img src="https://raw.githubusercontent.com/Peltoche/lsd/assets/screen_lsd.png" alt="lsd" align="right" width="450px" title="lsd">|

para instalarlos debemos usar el siguiente comando:

```bash 
sudo pacman -S lsd bat
```

Con esto hermos terminado con la instalacion y configuracion tanto como de kitty como de zsh. el siguiente post veremos como instalar mis dotfiles para bspwm.....


Gracias por leer.



