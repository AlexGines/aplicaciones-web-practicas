# Instalación Ubuntu server

1- Hacemos clic en "Nueva" para empezar a crear una maquina virtual

2- Ponemos el nombre que queramos que tenga la MV

3- Seleccionamos donde esta la iso para que podamos crear la MV

4- Si el "check" esta activado lo desactivamos y le damos a "siguiente"

5- Le ponemos 2MB  de memoria, 2 CPU's y el espacio del disco lo dejamos en 25GB

6- Le damos a siguiente y posteriormente en finalizar

Al iniciar la maquina nos da el siguiente error

![Imagen error VB](https://github.com/AlexGines/aplicaciones-web-practicas/blob/main/Error%20VB.png?raw=true)

Significa que la version de linux  la de Virtual Box no son compatibles y toca reinstalar VB 

Volvemos a hacer los pasos anteriores e iniciamos la maquina

## Pasos de configuracion

1- Primero elegimos el idioma, en nuestro caso elegimos el español

2- Nos saldra que hay una actualizacion del instalador, le damos a actualizar

3- Elegimos la distribucion de nuestro teclado

4- Elegimos que el tipo de instalacion sea "ubuntu server" (La version "minimized NO)

5- La Network configuration le damos a Done, mas adelante la configuraremos

6- El proxy configuration lo dejamos en blanco y la mirror address la dejamos por defecto

7- Elegimos usar el disco entero (es el disco que hemos creado en VB) y en la siguiente pantalla le damos "done"

8- Ahora introducimos el nombre de usuario, server y contraseña

9- Nos va a preguntar si queremos upgradear a ubuntu pro, lo saltamos por ahora

10- Marcamos la casiilla "Install OpenSSH server"

11- Le decimos qu eno queremos instalar ningun snaps

12- una vez finalize la instalacion le damos a "reboot Now

## Crear red host only y config 2do adaptador

1- Selecionamos "archivo - herramientas - red"

2- Le damos a crear

3- Le damos doble click y en servidor DHCP lo deshabilitamos y le damos a aplicar

4- Ahora en la configuracion de la maquina, en el apartado de red, seleccionamos el 2do adaptador

5- Le damos a habilitar y conectamos a "Adaptador Only"

6- Le damos a acepter e iniciamos la maquina

7- Si ponemos "ls /etc/netplan" vemos el archivo para editar la ip

8- Ponemos "sudo nano y el archivo con la raiz"

9- Escribimos "enp0s8" a la altura de enp0s 3

10- debajo escribimos "dhcp4: false"

11- A la altura de "dhcp4" ponemos "addresses:"

12- y debajo escribimos la ip

