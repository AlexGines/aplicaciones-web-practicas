# Instalación Ubuntu Server

1- Hacemos clic en "Nueva" para empezar a crear una máquina virtual.

2- Ponemos el nombre que queramos que tenga la MV.

3- Seleccionamos dónde está la ISO para que podamos crear la MV.

4- Si el "check" está activado, lo desactivamos y le damos a "siguiente"

5- Le ponemos 2 MB de memoria, 2 CPUs y el espacio del disco lo dejamos en 25GB.

6- Le damos a siguiente y posteriormente a finalizar.

Al iniciar la máquina nos da el siguiente error:

![Imagen error VB](https://github.com/AlexGines/aplicaciones-web-practicas/blob/main/Error%20VB.png?raw=true)

Significa que la versión de Linux y la de VirtualBox no son compatibles y toca reinstalar VB. 

Volvemos a hacer los pasos anteriores e iniciamos la máquina.

## Pasos de configuración

1- Primero elegimos el idioma; en nuestro caso elegimos el español.

2- Nos saldrá que hay una actualización del instalador; le damos a actualizar.

3- Elegimos la distribución de nuestro teclado.

4- Elegimos que el tipo de instalación sea "ubuntu server" (la versión "minimized NO).

5- En la Network configuration le damos a Done; más adelante la configuraremos.

6- El proxy configuration lo dejamos en blanco y la mirror address la dejamos por defecto.

7- Elegimos usar el disco entero (es el disco que hemos creado en VB) y en la siguiente pantalla le damos "done".

8- Ahora introducimos el nombre de usuario, server y contraseña.

9- Nos va a preguntar si queremos upgrade a Ubuntu Pro; lo saltamos por ahora.

10- Marcamos la casilla "Install OpenSSH server".

11- Le decimos que no queremos instalar ningún snap.

12- Una vez finalice la instalación, le damos a "Reboot Now".

## Crear red host-only y configurar 2.º adaptador

1- Seleccionamos "Archivo - Herramientas - Red".

2- Le damos a crear.

3- Le damos doble clic y en servidor DHCP lo deshabilitamos y le damos a aplicar.

4- Ahora en la configuración de la máquina, en el apartado de red, seleccionamos el 2.º adaptador.

5- Le damos a habilitar y conectamos a "Adaptador Only".

6- Le damos a aceptar e iniciamos la máquina.

7- Si ponemos "ls /etc/netplan", vemos el archivo para editar la IP.

8- Ponemos "sudo nano y el archivo con la raíz".

9- Escribimos "enp0s8" a la altura de enp0s3.

10- Debajo escribimos "dhcp4: false".

11- A la altura de "dhcp4" ponemos "addresses:".

12- Y debajo escribimos la IP.

13- Salimos del archivo y escribimos "sudo netplan try" y pulsamos Enter.

## Conectarnos desde la maquina real

1- Comprobamos que hay conectividad haciendo "ping" a la ip que hemos configurado

2- Una vez comprobada la conectividad ponemos en la terminal "ssh "Usuario@ip" del servidor

3- Escribimos la contraseña de la MV y estamos dentro
