Desde VMWare creamos una nueva máquina virtual:

![[Pasted image 20220326115554.png]]

Cargamos la ISO de Arch Linux:

![[Pasted image 20220326115610.png]]

En la selección del sistema operativo, seleccionamos Linux:

![[Pasted image 20220326115636.png]]

Ponemos un nombre a la máquina virtual:

![[Pasted image 20220326115652.png]]

Configuramos un tamaño máximo de disco de 80G (Esto a elección de cada uno), con la opción `Store virtual disk as a single file`:

![[Pasted image 20220326115822.png]]

Le metemos toda la siguiente configuración presente en el lado izquierdo:

![[Pasted image 20220326115907.png]]

Finalizamos la creación de la máquina virtual y arrancamos:

![[Pasted image 20220326115932.png]]

En este menú, seleccionamos la primer opción para proceder con la instalación de Arch Linux. Veremos lo siguiente:

![[Pasted image 20220326123239.png]]

Aquí comenzaremos a cacharrear. Validamos que tengamos internet:

![[Pasted image 20220326124424.png]]

Vamos a cambiar el teclado a Español para que no sea un dolor de cabeza el escribir:

![[Pasted image 20220326124453.png]]

Abriremos el siguiente menú con el comando `cfdisk`:

![[Pasted image 20220326124517.png]]

Desde aquí, seleccionaremos la opción `dos`, llegando al siguiente menú:

![[Pasted image 20220326124538.png]]

Comenzaremos definiendo una nueva partición primaria de 512M:

![[Pasted image 20220326124615.png]]

Podremos escoger entre primaria o extendida en el siguiente punto:

![[Pasted image 20220326124632.png]]

Una vez hecho, deberíamos de ver la siguiente estructuración de particiones:

![[Pasted image 20220326124652.png]]

Volveremos a crear una nueva partición primaria, esta vez de 75G:

![[Pasted image 20220326124854.png]]

Por último, crearemos una última partición con el espacio restante, correspondiente al SWAP:

![[Pasted image 20220326124918.png]]

Una vez hecho, sobre `/dev/sda3` nos iremos a la opción `Type` y seleccionaremos la opción **Linux swap / Solaris**:

![[Pasted image 20220326125009.png]]

Finalmente, nos debería quedar tal que así:

![[Pasted image 20220326125022.png]]

Seleccionamos la opción `Write` y posteriormente salimos. En este punto, deberíamos tener las cosas tal que así:

![[Pasted image 20220326125109.png]]

Posteriormente, ejecutamos los siguientes comandos:

![[Pasted image 20220326125210.png]]

Creamos las siguientes monturas y ejecutamos el comando indicado al final:

![[Pasted image 20220326125315.png]]

Este último comando tardará un rato en terminar, ya que se procederá a instalar ciertos paquetes:

![[Pasted image 20220326125339.png]]

Una vez finalizada la instalación, ejecutamos el siguiente comando:

![[Pasted image 20220326125509.png]]

Procedemos a crear los usuarios dentro de nuestro sistema:

![[Pasted image 20220326125623.png]]

Procedemos a instalar `sudo` para definir una regla:

![[Pasted image 20220326125700.png]]

Es recomendable instalar `nano` y `vim`:

![[Pasted image 20220326125725.png]]

En el `/etc/sudoers`, descomentaremos la siguiente línea:

![[Pasted image 20220326130813.png]]

De esta forma, nos pedirá contraseña siempre que tratemos de ejecutar un comando privilegiado partiendo de nuestro usuario principal.

Nos abriremos el archivo `/etc/locale.gen` y descomentaremos por un lado la siguiente línea:

![[Pasted image 20220326125941.png]]

Así como esta otra:

![[Pasted image 20220326125956.png]]

Una vez hecho, ejecutaremos el comando `locale-gen`:

![[Pasted image 20220326130016.png]]

Para quedarnos con el teclado en Español, vamos a crear un archivo en `/etc/vconsole.conf` con el siguiente contenido:

![[Pasted image 20220326130153.png]]

En este punto, toca montar el bootloader (GRUB):

![[Pasted image 20220326130258.png]]

Creamos el archivo de configuración de GRUB:

![[Pasted image 20220326130322.png]]

Asignamos un nombre a la máquina:

![[Pasted image 20220326130356.png]]

Definimos el archivo `/etc/hosts`:

![[Pasted image 20220326130430.png]]

Instalamos `neofetch` para fardar de Arch Linux:

![[Pasted image 20220326130506.png]]

Ahora con escribir el comando `neofetch`, deberíamos ver lo siguiente:

![[Pasted image 20220326130528.png]]

Llegó el momento de reiniciar el sistema operativo, hacemos un `reboot now` desde consola y vemos si el GRUB nos carga correctamente:

![[Pasted image 20220326130617.png]]

En nuestro caso, vemos que carga perfectamente:

![[Pasted image 20220326130631.png]]

Deberíamos poder ingresar a nuestra consola, pero comprobaremos que no tenemos internet:

![[Pasted image 20220326130659.png]]

Ejecutamos los siguientes 2 comandos:

![[Pasted image 20220326130857.png]]

Ya en este punto, deberíamos volver a tener internet, incluso cuando reiniciemos la máquina:

![[Pasted image 20220326130917.png]]

También habilitaremos el siguiente servicio:

![[Pasted image 20220326130956.png]]

Instalamos a continuación un AUR Helper (PARU) para poder instalar paquetes de los AUR. Primeramente, instalaremos GIT:

![[Pasted image 20220326131117.png]]

Clonamos el siguiente repositorio:

![[Pasted image 20220326131227.png]]

Para proceder con la instalación, ejecutamos el siguiente comando:

![[Pasted image 20220326131258.png]]

Una vez completado, ya tendremos acceso a una infinidad de paquetes:

![[Pasted image 20220326131326.png]]

También instalaremos los repositorios de BlackArch en nuestro Arch:

![[Pasted image 20220330133443.png]]

Lo ejecutamos:

![[Pasted image 20220330133506.png]]

Y pasado un tiempo ya tendremos todo al punto:

![[Pasted image 20220330133515.png]]

Si aplicamos el siguiente comando para sincronizar los paquetes de la base de datos, deberíamos ver `blackarch` justo al final:

![[Pasted image 20220330133541.png]]

Para poder contar con interfaz gráfica, comenzaremos instalando los siguientes paquetes:

![[Pasted image 20220326133842.png]]

A continuación, instalamos `gnome`:

![[Pasted image 20220326133929.png]]

Una vez instalados los paquetes, ejecutaremos el siguiente comando:

![[Pasted image 20220326134116.png]]

Tras aplicar el comando, se nos abrirá la interfaz gráfica (será necesario iniciar sersión primero):

![[Pasted image 20220326134156.png]]

Dado que queremos que se nos abra la interfaz tras el reinicio del sistema, aplicaremos el siguiente comando también (Podemos obtener una nueva consola del sistema jugando con Ctrl+Alt+F3 o Ctrl+Alt+F4, etc.):

![[Pasted image 20220326134659.png]]

Ya en este punto, si reiniciamos el sistema, deberíamos llegar hasta aquí sin ningún problema:

![[Pasted image 20220326134726.png]]

Dado que las proporciones no son las adecuadas, vamos a proceder con la instalación de las VMWare Tools. Instalamos el paquete `gtkmm`:

![[Pasted image 20220326134836.png]]

Instalamos el paquete `open-vm-tools`:

![[Pasted image 20220326134908.png]]

Instalamos estos otros 2 paquetes:

![[Pasted image 20220326134942.png]]

Habilitamos el servicio de las VMWare Tools:

![[Pasted image 20220326135007.png]]

En este punto, si reiniciamos el sistema operativo, deberíamos ver todo con la proporción correcta:

![[Pasted image 20220326135040.png]]

Procedemos a instalar `Kitty`, será la consola en la que nos estaremos moviendo:

![[Pasted image 20220326135229.png]]

Una vez hecho, podemos operar desde esta terminal:

![[Pasted image 20220326135343.png]]

Antes que nada, vamos a cambiar el  keyboard:

![[Pasted image 20220330134446.png]]

Tendremos por defecto esto:

![[Pasted image 20220330134455.png]]

Por tanto lo cambiamos a Español:

![[Pasted image 20220330134514.png]]

De esta forma, podremos maniobrar más cómodamente.

Ya en este punto, ejecutaremos los siguientes comandos desde consola (La instalación de los paquetes especificados tardará un poco):

![[Pasted image 20220330134832.png]]

Una vez ejecutados, procedemos a habilitar los siguientes servicios:

![[Pasted image 20220330135303.png]]

Ahora, procederemos a instalar algunas fuentes. Instalaremos primero el comando wget:

![[Pasted image 20220330135525.png]]

Nos descargamos la fuente Iosevka (esto lo haremos como root en la ruta `/usr/share/fonts/`):

![[Pasted image 20220330140247.png]]

Nos instalamos las utilidades `zip`, `unzip` y `tar`:

![[Pasted image 20220330135930.png]]

También instalamos `7z`:

![[Pasted image 20220330140021.png]]

Descomprimos el contenido:

![[Pasted image 20220330140332.png]]

El problema está en que la fuente `.ttf` reside en unos directorios que vienen dentro del descomprimido, la idea es situarlas en el directorio actual de trabajo. Para ello, podemos hacer esto:

![[Pasted image 20220330140434.png]]

Ya podemos borrar los directorios vinculados a dicha fuente:

![[Pasted image 20220330140504.png]]

Por otro lado, procedemos a instalar Firefox:

![[Pasted image 20220330140604.png]]

Ingresamos a la siguiente dirección URL para descargar la fuente IcoMoon:

![[Pasted image 20220330140655.png]]

Presionaremos en el botón Download para descargarla. Metemos la fuente en el directorio `/usr/share/fonts`:

![[Pasted image 20220330140820.png]]

Quedando tal que así:

![[Pasted image 20220330140832.png]]

Instalaremos estas otras fuentes:

![[Pasted image 20220330141101.png]]

Ejecutamos el siguiente comando en el directorio `Repos` que habíamos creado (`/home/s4vitar/Desktop/s4vitar/Repos/`):

![[Pasted image 20220330152336.png]]

En nuestro caso, vamos a aplicar la siguiente migración del proyecto existente:

![[Pasted image 20220330152501.png]]

Y ya en este punto, ejecutamos los siguientes comandos:

![[Pasted image 20220330152536.png]]


Reiniciamos el sistema operativo. Al momento de iniciar sesión, abajo a la derecha pinchamos en el icono de configuración:

![[Pasted image 20220330141822.png]]

Podremos ver `awesome` en el menú de selección. Lo seleccionamos e iniciamos sesión:

![[Pasted image 20220330152554.png]]

Deberíamos visualizar el entorno tal y como se está mostrando en la imagen anteriormente adjunta.

Instalamos desde una consola aparte (Ctrl+Alt+F3) la `zsh`:

![[Pasted image 20220330142435.png]]

Al abrir la terminal veremo el siguiente error:

![[Pasted image 20220330152627.png]]

Hay que arreglar un par de cosas. Primero que nada, vamos a cambiar la distribución de teclado contando con interfaz gráfica:

![[Pasted image 20220327160731.png]]

Nos iremos a la siguiente configuración del archivo `zshrc` compartida en mi página:

![[Pasted image 20220330152825.png]]

Nos la copiamos entera y la sustituimos en `/home/s4vitar/.zshrc`:

![[Pasted image 20220330153033.png]]

Si volvemos a abrir una consola, ahora veremos estos errores:

![[Pasted image 20220330153049.png]]

Pero esto es normal, porque hay que ir instalando una serie de cosas. Vamos a comenzar instalando estos 2 paquetes:

* zsh-syntax-highlighting
* zsh-autosuggestions

![[Pasted image 20220330153132.png]]

Instalaremos también `locate`, para disponer de mayor facilidad a la hora de buscar archivos:

![[Pasted image 20220330153211.png]]

Una vez hecho, hacemos un `sudo updatedb`:

![[Pasted image 20220330153235.png]]

Localizamos los siguientes 2 archivos:

![[Pasted image 20220330153303.png]]

Y las sustituimos donde se hace alusión a estas en el `.zshrc`:

![[Pasted image 20220330153358.png]]

Lo cambiamos por esto:

![[Pasted image 20220330153457.png]]

Antes de que tengamos problemas de movilidad con algunos comandos que aún no existen, vamos a instalarlos:

* lsd
* bat
* scrub

![[Pasted image 20220330153753.png]]

Listo, en cuanto a los siguientes errores, iremos en breve:

![[Pasted image 20220330153836.png]]

Vamos a cambiar para que en vez de abrirnos Alacritty se nos abra la Kitty (considero que es más óptima). Para ello, nos iremos al archivo `/home/s4vitar/.config/awesome/rc.lua` y en la línea donde pone Alacritty:

![[Pasted image 20220330154108.png]]

Pondremos Kitty:

![[Pasted image 20220330154123.png]]

Será necesario hacer un Ctrl+Win+R para cargar la nueva configuración. Si en este punto nos volvemos a abrir una terminal, la varemos así:

![[Pasted image 20220330154214.png]]

Operaremos desde esta. Vamos a crear un archivo en `/home/s4vitar/.config/kitty/kitty.conf` con el siguiente contenido:

![[Pasted image 20220330154357.png]]

Al abrir una nueva terminal, la veremos así:

![[Pasted image 20220330154429.png]]

Para el plugin de sudo, haremos lo siguiente:

![[Pasted image 20220330154628.png]]

Si volvemos a abrir la consola, no debería haber ningún problema con este Plugin:

![[Pasted image 20220330154704.png]]

Con la Powerlevel10k iremos en breve. Vamos a arreglar la transparencia, para ello nos abriremos el archivo `/home/s4vitar/.config/awesome/theme/picom.conf` y en la siguiente línea:

![[Pasted image 20220330154823.png]]

Cambiaremos el `true` a `false` para **vsync**:

![[Pasted image 20220330154856.png]]

Asimismo, cambiaremos la línea donde pone `use-damage` de `true` a `false`:

![[Pasted image 20220330154944.png]]

Vamos a quitar el tema actual que te trae la terminal, que a mi particularmente no me gusta mucho:

![[Pasted image 20220330155045.png]]

Nos iremos a la ruta `/home/s4vitar/.config/awesome/ui/decorations/` y nos abriremos el archivo `init.lua`:

![[Pasted image 20220330160016.png]]

Comentaremos las 2 últimas líneas:

![[Pasted image 20220330160032.png]]

En este punto, hacemos Ctrl+Win+R para reiniciar la configuración y que se apliquen los cambios. Deberíamos ver la terminal sin lo de antes:

![[Pasted image 20220330160100.png]]

Vamos a retocar el `picom.conf`. Nos situamos en la siguiente ruta, creamos por si acaso una copia de seguridad y nos traemos el siguiente archivo al directorio actual de trabajo:

![[Pasted image 20220330160244.png]]

Volvemos a poner en false el `vsync`:

![[Pasted image 20220330160310.png]]

Dado que `menu-opacity` está deprecated, vamos a cambiarlo a `opacity`:

![[Pasted image 20220330160347.png]]

Lo convertimos a esto:

![[Pasted image 20220330160359.png]]

En mi caso, no quiero BLUR, por tanto todas las líneas de la sección del BLUR las comentamos:

![[Pasted image 20220330160501.png]]

Volvemos a poner en `false` el apartado de `use-damage`:

![[Pasted image 20220330160532.png]]

En la sección de CORNERS, vamos a ponerle 20 de `round-borders`:

![[Pasted image 20220330160651.png]]

También definiremos un `corner-radius` de 20:

![[Pasted image 20220330162401.png]]

Una vez hecho esto, nos situamos en el directorio `/home/s4vitar/.config/kitty/` y nos descargamos el siguiente archivo `color.ini`:

![[Pasted image 20220330160949.png]]

En este punto, hacemos un Ctrl+Win+q para salir del entorno y volveremos a iniciar sesión. Una vez iniciada la sesión, deberíamos ver la terminal y el entorno tal que así:

![[Pasted image 20220330162509.png]]

Nos iremos al archivo `picom.conf` y en la línea donde pone `backend = "glx"` lo cambiaremos a lo siguiente:

![[Pasted image 20220330161305.png]]

Vamos a incorporar un nuevo fondo de pantalla. Para ello, será necesario que te descargues aquel que más te gusta para configurarlo.

En mi caso, voy a estar configurando el siguiente fondo de pantalla:

![[Pasted image 20220330161905.png]]

Para ello, nos iremos a la ruta `/home/s4vitar/.config/awesome/` y nos abriremos el archivo `rc.lua` para editarlo. Incorporaremos las siguientes líneas al final:

![[Pasted image 20220330162208.png]]

Una vez incorporadas, instalamos `feh`:

![[Pasted image 20220330162242.png]]

Si recargamos con Ctrl+Win+R deberíamos ver el fondo sin problema:

![[Pasted image 20220330162619.png]]

Cabe destacar que en nuestro caso la terminal se ve transparente, pero esto no es por `PICOM`, dado que hemos configurado un 1.0 de opacidad:

![[Pasted image 20220330162648.png]]

Lo que hace que sea transparente es la propia configuración que le hemos metido a la Kitty:

![[Pasted image 20220330162719.png]]

Aquí cada uno podrá ajustar las cosas a su manera, además de configurar la opacidad para todas las aplicaciones del sistema (se pueden generar excepciones sin problema mediante la definición de reglas).

Vamos a por la terminal, que se ve bastante fea:

![[Pasted image 20220330162818.png]]

Ejecutamos los siguientes comandos:

![[Pasted image 20220330162906.png]]

Posteriormente, ejecutamos el comando `zsh` para entrar en el siguiente modo:

![[Pasted image 20220330162932.png]]

Aquí la idea es que cada uno configure su shell como desee, es todo guiado en un principio, así que no deberían de haber problemas.

Una vez esté completamente configurada, deberíamos ver algo tal que así:

![[Pasted image 20220330163059.png]]

Cabe destacar que si atendemos al archivo `kitty.conf`, hemos definido una fuente que hasta ahora no existe:

![[Pasted image 20220330163124.png]]

Lo que haremos será dirigirnos a la ruta `/usr/share/fonts/` y posteriormente a la siguiente dirección URL:

![[Pasted image 20220330163243.png]]

Descargaremos la fuente `Hack Nerd Font`, será un comprimido. Este comprimido lo descomprimimos en la ruta de las fonts:

![[Pasted image 20220330163323.png]]

Si cerramos y volvemos a abrir una terminal, ya deberíamos verlo con al fuente adecuada:

![[Pasted image 20220330163343.png]]

En caso de que el tamaño de fuente sea grande, este puede ajustarse en el `kitty.conf`, concretamente en esta línea:

![[Pasted image 20220330163410.png]]

Podemos comprobar antes que nada con Ctrl+Win+L que el bloqueo de pantalla esté correctamente configurado:

![[Pasted image 20220330165139.png]]

Simplemente ponemos la contraseña y vemos si nos deja ingresar de vuelta al entorno.

Ahora, editaremos este archivo:

![[Pasted image 20220330165329.png]]

Lo haremos primeramente como el usuario con bajos privilegios (s4vitar). En esta sección, aplicaremos algunos cambios:

![[Pasted image 20220330165401.png]]

Pondremos estos 2 nuevos componentes:

![[Pasted image 20220330165444.png]]

Esto en cuanto a lo que queremos que nos salga en el lado izquierdo. Del lado derecho yo preferiblemente prefiero que no me salga nada, así que comentamos todas estas líneas:

![[Pasted image 20220330165514.png]]

Enteras, quedando de la siguiente forma:

![[Pasted image 20220330165553.png]]

Hasta aquí:

![[Pasted image 20220330165616.png]]

Si ahora cerramos la terminal y la volvemos a abrir tras guardar los cambios, deberíamos verla de la siguiente manera:

![[Pasted image 20220330165643.png]]

Sin ningún elemento a la derecha.

Ahora tocará hacer lo mismo pero para el usuario root, dado que si nos convertimos en root tendremos una consola normal:

![[Pasted image 20220330165710.png]]

Para ello volvemos a hacer esto:

![[Pasted image 20220330165726.png]]

Ejecutamos el comando `zsh` y volvemos a definir una configuración para la terminal del usuario.

![[Pasted image 20220330165750.png]]

Ahora bien, a la derecha de nuestra terminal veremos esto:

![[Pasted image 20220330165825.png]]

Y a mi personalmente no me gusta, por tanto abriremos el archivo situado en `/root/.p10k.zsh` y añadiremos nuevamente como elementos que queremos que nos aparezca a la izquierda lo siguiente:

![[Pasted image 20220330165925.png]]

Volvemos a comentar todo del lado derecho:

![[Pasted image 20220330165953.png]]

Y ahora buscaremos por la siguiente cadena:

![[Pasted image 20220330170010.png]]

Lo que haremos será comentar dicha línea:

![[Pasted image 20220330170051.png]]

Por otro lado, en la línea donde encontramos la cadena `POWERLEVEL9K_CONTEXT_ROOT_TEMPLATE` cambiaremos el siguiente contenido:

![[Pasted image 20220330170144.png]]

A un icono a escoger por nosotros. Podemos buscarlo de aquí:

![[Pasted image 20220330170322.png]]

Directamente podemos copiar y pegar. Yo le pondré este:

![[Pasted image 20220330170429.png]]

Tras pegar el icono, si nos abrimos una nueva consola, migramos al usuario root y spawneamos una zsh, deberíamos ver esto:

![[Pasted image 20220330170534.png]]

Será un indicativo para saber en qué momento estamos operando como root (se puede poner el icono que se desee).

Dado que al migrar al usuario root no nos da la shell que nos interesa, estando como root aplicamos el siguiente comando para configurar que el usuario root opere con esta nueva consola:

![[Pasted image 20220330170759.png]]

De esta forma ya, al migrar a root nos debería de ir todo a la primera:

![[Pasted image 20220330170823.png]]

Instalamos fzf, tanto para el usuario s4vitar como para el usuario root. Simplemente ejecutamos estos comandos para ambos:

![[Pasted image 20220330170912.png]]

Por aquí para el usuario root:

![[Pasted image 20220330170934.png]]

De esta forma, si cerramos la consola y abrimos una nueva, al dirigirnos a la raíz y hacer un `cat` para posteriormente presionar Ctrl+t debería salirnos esto:

![[Pasted image 20220330171023.png]]

Esto sirve para cualquier comando, lo mismo para el histórico de comandos semejantes escritos (lo podemos hacer con ctrl+r tras escribir parte de un comando):

![[Pasted image 20220330171107.png]]

Entrando en un menú de selección donde poder maniobrar hasta el comando deseado a introducir.

Ahora bien, haremos que el archivo `.zshrc` sea el mismo tanto para s4vitar como para root. Bajo mi experiencia a la hora de lidiar con ciertos problemas, considero que es lo más oportuno:

![[Pasted image 20220330171307.png]]

Lo hacemos mediante el uso de un enlace simbólico. 

Vamos a instalar nvim junto con un tema bastante chulo para poder editar nuestros archivos. Clonaremos el siguiente repositorio:

* https://github.com/NvChad/NvChad

Pero primeramente instalamos `neovim`:

![[Pasted image 20220330171440.png]]

Ahora si, hacemos lo siguiente:

![[Pasted image 20220330171637.png]]

Posteriormente, ejecutamos el siguiente comando:

![[Pasted image 20220330171706.png]]

Pasado unos segundos, deberíamos ver esto en la parte inferior:

![[Pasted image 20220330171719.png]]


Veremos un montón de paquetes siendo instalados al darle al **ENTER**:

![[Pasted image 20220330171737.png]]

Pasado un rato, deberíamos verlo todo instalado sin errores:

![[Pasted image 20220330171748.png]]

Ahora bien, si salimos de `nvim` y volvemos a entrar, deberíamos ver el siguiente tema:

![[Pasted image 20220330171815.png]]


Este tema cuenta con un montón de utilidades instaladas:

![[Pasted image 20220330171851.png]]

![[Pasted image 20220330171939.png]]

![[Pasted image 20220330171951.png]]

![[Pasted image 20220330171959.png]]

Cabe decir que para root habrá que volver a hacer los mismos comandos.

Vamos a por esto:

![[Pasted image 20220330172213.png]]

Para cambiar el icono que vemos en la parte superior, tan sólo tendremos que proporcionar nuestra imagen en la siguiente ruta:

![[Pasted image 20220330172257.png]]

Es ese icono que estamos viendo ahí. En mi caso borraré esa imagen y la sustituiré por esta otra:

![[Pasted image 20220330172406.png]]

De esta forma, si hacemos un Ctrl+Win+R, veremos el siguiente resultado:

![[Pasted image 20220330172426.png]]

A modo de indicación, tenemos la Kitty configurada para que cuente con la siguiente barra en la sección inferior:

![[Pasted image 20220330172541.png]]

Recomiendo estudiar un poco Kitty para entender cómo operar con esta.

Algo que notaremos, es que las teclas `Inicio`, `Fin` y `Supr` no funcionan, esto podemos arreglarlo si en el archivo `/home/s4vitar/.zshrc` añadimos las siguientes definiciones:

![[Pasted image 20220330172656.png]]

Con esto ya debería funcionar.

Vamos a configurar a modo de ejemplo práctico un atajo de teclado que nos permita abrir el Firefox. Intentaremos usar el atajo Win+Shift+F.

Para ello nos iremos al archivo `/home/s4vitar/.config/awesome/rc.lua` y crearemos la siguiente variable:

![[Pasted image 20220330172953.png]]

Una vez definida la variable `browser`, nos vamos al archivo `/home/s4vitar/.config/awesome/configuration/keys.lua` e incorporamos la siguiente definición (sólo atender a la parte seleccionada):

![[Pasted image 20220330173049.png]]

Ya con esto lo tenemos casi todo. Vamos a configurar el Firefox para ajustar la privacidad y el tema.

Una vez abierto Firefox, nos iremos a la sección `Add-ons and themes`:

![[Pasted image 20220330173332.png]]

Nos iremos a `Themes` y ajustaremos el modo Dark:

![[Pasted image 20220330173356.png]]

Ya de esta forma la vista dejará de sangrarnos:

![[Pasted image 20220330173409.png]]

Por último, en cuanto a privacidad respecta, siempre recomiendo configurarlo para que no recuerde nuestro historial:

![[Pasted image 20220330173438.png]]

Será necesario reiniciar el Firefox para que se apliquen los cambios.

Y poco más, cualquier paquete o herramienta que nos queramos instalar, podemos hacerlo. Por aquí nos podemos instalar unas cuantas de las que utilizamos para pentesting:

![[Pasted image 20220330173829.png]]

También podemos instalar `crackmapexec`:

![[Pasted image 20220330173958.png]]

Wireshark (Tarda un rato en instalarse):

![[Pasted image 20220330174932.png]]

Instalamos `mdcat` para tener la posibilidad de interpretar Markdown desde consola:

![[Pasted image 20220330175003.png]]

Y así con todos los paquetes que queramos.

A hackear!! :)
