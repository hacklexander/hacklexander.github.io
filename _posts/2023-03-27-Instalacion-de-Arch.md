---
title: "Instalacion de Arch"
layout: post
date: 2023-04-01 21:00
image: /assets/arch/install-arch/install-guide.jpg
headerImage: true
star: true
tag:
    - Instalacion
    - VMWare
    - Archlinux
category: blog
author: hacklexander
description: Instalacion de Archlinux
---

# Carga de la imagen.

una vez tengamos todos los recursos descargados, creada la maquina virtual en VMWare o VirtualBox, tendremos una terminal de comandos para empezar con la instalacion.

A continuacion muestro la terminal de comandos que nos sale.

![first][1]

<figcaption class="caption">Primera vista</figcaption>
[1]: {{site.url}}/{{site.install}}08.png

---

## cambiamos distribucion de teclado

Despues de esto, lo que tenemos que hacer es poner nuestra distribucion de teclado en el lenguaje **Español** o **Ingles** como prefieras, esto para que los caracteres especiales se escriban de forma correcta.

El comando que debemos escribir es:

```bash
root@archiso ~# loadkeys es
```

![loadkeys]({{site.url}}/{{site.install}}loadkeys.png)

---

## verificamos si tenemos internet

Si estamos usando una maquina virtual, lo mas probable es que el internet ya este configurado, pero podemos verificar usando un pequeño comando en la linea de comandos que es:

```bash
root@archiso ~# ping -c3 8.8.8.8
```

Si efectivamente contamos con internet, tendremos una salida en la linea de comando como la siguiente:

```bash
root@archiso ~# ping -c3 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=118 time=4.61 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=118 time=4.85 ms
64 bytes from 8.8.8.8: icmp_seq=3 ttl=118 time=4.91 ms

--- 8.8.8.8 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2008ms
rtt min/avg/max/mdev = 4.608/4.788/4.910/0.130 ms
```

Si nuestro caso es el contrario podemos utilizar un cable ethernet y conectarlo directamente al equipo por dicho puerto. En el caso contrario tenemos que usar una lista de comandos para poder conectarnos a una red inalambrica.

La herramienta que vamos a utilizar en esta ocacion sera **wpa_supplicant**, esta herramienta nos permite conectarnos a una red solamente creado un archivo de configuracion donde agregaremos los datos de nuestra red (nombre, contraseña) que se hace de la siguiente forma:

```bash
root@archiso ~# wpa_passphrase "NOMBRE DE RED" "PASSWORD" > /$HOME/wpa_supplicant/wpa_suplicant.conf
```

> El comando **wpa_passphrase** nos ayuda con la creacion del archivo de configuracion de red, nos hace una sintaxis mas organizada y que wpa_supplicant pueda enterder y que no de errores.

Para poder verificar que los datos quedaron correctamente agregados al archivo usaremos un comando:

```bash
cat $HOME/wpa_supplicant.conf
```

Tendremos una salida como la siguiente:

```bash
───────┬───────────────────────────────────
       │ File: $HOME/wpa_supplicant/wpa_supplicant.conf
───────┼───────────────────────────────────
   1   │ network={
   2   │     ssid="NOMBRE DE RED"
   3   │     #psk="PASSWORD"
   4  psk=6a3bcf1c686f9ab7f267cc8f9e1e199019e6274fccde69dc10467f35339a8f
       │ 9a
   5   │ }
───────┴───────────────────────────────────
```

-   Una vez ya tengamos nuestro archivo de configuracion procedemos a usar **wpa_supplicant**:

```bash
wpa_supplicant -B -D nl80211,wext -c $HOME/wpa_supplicant.conf -i interface-de-red
```

---

-   Despues de esto tenemos que empezar a crear nuestras particiones para la instalacion, para empezar tendremos que usar una herramienta la cual es **cfdisk**
    Seleccionamos la opción (**dos**):

![cfdisk index]({{site.url}}/{{site.install}}09.png)

---

-   Comenzaremos creando una nueva partición primaria de 512M:

![cfdisk]({{site.url}}/{{site.install}}11.png)

---

-   Podremos escoger entre primaria o extendida en el siguiente punto:

![cfdisk]({{site.url}}/{{site.install}}12.png)

---

-   Sì hicimos todos los pasos correctamente, deberíamos de ver la siguiente estructuración de particiones:

![cfdisk]({{site.url}}/{{site.install}}13.png)

---

-   En este punto vamos a crear una nueva partición primaria, esta vez de 75G:

![cfdisk]({{site.url}}/{{site.install}}14.png)

---

-   Por último, crearemos una última partición con el espacio que nos queda, esta sera la SWAP:

![cfdisk]({{site.url}}/{{site.install}}15.png)

---

-   Ya en este punto nos posicionaremos sobre /dev/sda3, nos iremos a la opción Type y seleccionaremos la opción Linux swap / Solaris:

![cfdisk]({{site.url}}/{{site.install}}16.png)

---

-   Nos debería quedar así:

![cfdisk]({{site.url}}/{{site.install}}17.png)

---

-   Por ultimo seleccionamos la opción Write y salimos. En este punto, ejecutamos el siguiente comando:

> `root@archiso ~# lsblk`

![lista de particiones]({{site.url}}/{{site.install}}18.png)

---

-   Como pudimos ver, las particiones quedaron correctamente creadas, el paso a seguir en este momento es darles un formato.
    Usaremos los siguientes comandos para formatear todas las particiones recien creadas.

```bash

mkfs.vfat -F 32 /dev/sda1
mkfs.ext4 /dev/sda2
mkswap /dev/sda3
swapon

```

![formateo de particiones]({{site.url}}/{{site.install}}19.png)

Con estos comandos lo que hicimos fue formatear cada particion que creamos anteriormente, la particion de 512MB quedo con formato **_fat32_** que sera para el /boot, la particion **_sda2_** quedo en formato **_ext4_** que sera la del sistema y la ultima quedo con formato **_swap_** y la activamos con el ultimo comando que es `swapon`

---

## Instalacion de paquetes

-   lo que haremos ahora es montar las particiones con sus nuevos formatos y posteriormente, empezaremos a instalar los paquetes necesarios para tener nuestra distribucion linux. Es una descarga algo pesada, entonces debemos esperar que termine la instalacion para poder continuar.

```bash
mount /dev/sda2 /mnt
mkdir /mnt/boot
mount /dev/sda1  /mnt/boot
pacstrap /mnt linux linux-firmware networkmanager grub wpa_supplican base base-devel

```

> Con este comando en **_/mnt_** le estamos diciendo que queremos instalar todos estos paquetes en este directorio.

|<img src="{{site.url}}/{{site.install}}20.png" alt="Montura de particiones" align="center" width="400px">|<img src="{{site.url}}/{{site.install}}21.png" alt="instalaciones de paquetes" align="center" width="400px">|

---

-   Procedemos a crear los usuarios dentro de nuestro sistema:

![user add]({{site.url}}/{{site.install}}useradd.png)

-   Procedemos a instalar sudo para definir una regla:

![sudo install]({{site.url}}/{{site.install}}sudo-instal.png)

-   Es recomendable instalar nano y vim:

![nano vim install]({{site.url}}/{{site.install}}nano-vim.png)

-   En el /etc/sudoers, descomentaremos la siguiente línea:

![sudoers edit]({{site.url}}/{{site.install}}sudoers.png)

-   De esta forma, nos pedirá contraseña siempre que tratemos de ejecutar un comando privilegiado partiendo de nuestro usuario principal.
    Nos abriremos el archivo /etc/locale.gen y descomentaremos por un lado la siguiente línea:

![locale edit]({{site.url}}/{{site.install}}locale-edit.png)

-   Adicional a esto, tendremos que editar el archivo **/etc/locale.conf** y nos debe quedar una salida como la siguiente:

![locale edit conf]({{site.url}}/{{site.install}}locale-conf.png)

-   Una vez hecho, ejecutaremos el comando locale-gen.
    Para quedarnos con el teclado en Español, vamos a crear un archivo en /etc/vconsole.conf con el siguiente contenido:

![locale-gen]({{site.url}}/{{site.install}}locale-gen.png)

---

-   En este punto, toca montar el bootloader (GRUB):

![grub install]({{site.url}}/{{site.install}}grub-install.png)

-   Creamos el archivo de configuración de GRUB:

![grub config]({{site.url}}/{{site.install}}grub-config.png)

---

-   Asignamos un nombre a la máquina:

![hostname]({{site.url}}/{{site.install}}hostname.png)

-   Definimos el archivo /etc/hosts:

![hosts]({{site.url}}/{{site.install}}hosts.png)

---

-   Instalamos neofetch para presumir nuestro nuevo sistema, con el siguiente comando:

> `pacman -S neofetch`

-   Ahora con escribir el comando **neofetch**, deberíamos ver lo siguiente:

![neofetch]({{site.url}}/{{site.install}}neofetch.png)

---

-   Llegó el momento de reiniciar el sistema operativo, hacemos un reboot now desde consola y vemos si el GRUB nos carga correctamente. En nuestro caso, vemos que carga perfectamente:

![inicio-grub]({{site.url}}/{{site.install}}inicio-grub.png)

---

-   Deberíamos poder ingresar a nuestra consola, pero comprobaremos que no tenemos internet:

![first-auth]({{site.url}}/{{site.install}}first-auth.png)

-   Ejecutamos los siguientes 2 comandos:

![networkmanager]({{site.url}}/{{site.install}}networkmanager.png)

-   Ya en este punto, deberíamos volver a tener internet, incluso cuando reiniciemos la máquina:

![ping-full]({{site.url}}/{{site.install}}ping-full.png)

-   También habilitaremos el siguiente servicio de wpa_supplicant con el siguiente comando

> `systemctl enable wpa_supplicant.service`

---

-   Instalamos a continuación un AUR Helper (PARU) para poder instalar paquetes de los AUR. Primeramente, instalaremos GIT:

> `pacman -S git`

-   Clonamos el siguiente repositorio:

![gitclone-paru]({{site.url}}/{{site.install}}gitclone-paru.png)

-   Para proceder con la instalación, ejecutamos el siguiente comando:

![makepkg-paru]({{site.url}}/{{site.install}}makepkg-paru.png)

-   Ahora instalaremos todos los repositorios de **blackarch**, estos contienen todas las herramientas de hacking que usaremos mas adelante. nos pocicionamos en la terminal de comando y digitaremos los siguientes comandos:

![blackarch install]({{site.url}}/{{site.install}}blackarch.png)

Por ultimo isntalaremos un **dispay manager** en este caso sera el gnome, me parece muy bonito. los comandos que tenemos que usar son:

```bash
sudo pacman -S gdm
```

![gdm install]({{site.url}}/{{site.install}}gdm-install.png)

Ahora los comandos para habilitarlo y ejecutarlo, son los siguientes:

```bash
sudo systemctl enable gdm.service
sudo systemctl start gdm.service
```

Tendremos por fin una interface grafica para poder autenticarnos e iniciar en nuestro arch.

![gdm start]({{site.url}}/{{site.install}}gdm-start.png)

---

---

En este post vimos como poder intalar ArchLinux desde 0, gracias por leer!

En el siguiente post, seguiremos viendo mas herramientas que nos serviran para llegar a nuestra distro final para poder empezar con las auditorias de seguridad informatica!!
