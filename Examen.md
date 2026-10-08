# Guia para el examen

## Instalación ubuntu server

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

## Instalamos apache2

1- Escribimos "sudo apt-get install apache2".

2- Ahora ponemos "systemctl status apache2" para comprobar el estado del servicio.

3- Vamos a "cd /etc/apache2".

4- Entramos a la carpeta "sites-aviable", de ahí entramos en el archivo "000-default" y vamos a la ruta en la que indica dónde está nuestra página.

5- Al entrar al archivo de la ruta, lo que escribamos en HTML aparecerá en la página.

## Deshabilitar antigua pagina y crear una nueva

1- El archivo 000 que esta en sites-aviable lo duplicamos y llamamos "smr.conf"

2- Editamos el archivo duplicado y donde esta la ruta añadimos "/smr"

3- Vamos a la ruta /var/www/html y con mkdir creamos la carpeta "smr"

4- Dentro de la carpeta creamos con nano un fichero llmado "index.html" y añadimos lo que quramos que se vea en la web

5- Volvemos donde esta instalado apache, entramos a sites-aviable y desactivamos el fichero antiguo con "a2dissite 00"

6- Metemos un "systemctl reload apache2" y luego status para que se aplique y comprobar que va bien

7- Ahora ponemos "a2ensite smr.conf" para habilitar la nueva pagina y metemos otra vez un reload y status

8- Entramos en el archivo "smr.conf" y cambiamos el "virtual host" a 7654 y hacemos reload

9- y por ultimo modificamos el archivo "ports" de apache2, añadimos "Listen 7654" y hacemos reload

## Aqui vamos a ver como crear 2 paginas distintas a las cuales se accede por el mismo url pero distinto puerto

1- Creamos las carpetas con "sudo mkdir -p /var/www/smr/web /var/www/smr/intranet" y añadimos un fichero index.html e intranet.html y le añadimos contenido a nuestras paginas

2- Creamos el usuario con el que vamos a acceder a la intranet con "sudo htpasswd -c /etc/apache2/.htpasswd admin" pedira la contraseña 2 veces con la que accederemos mas adelante a la pagina

3- Vamos a la carpeta de puertos que esta en apache y le decimos que escuche el "9999"

4- Copiamos el archivo 00 de la carpeta "sites eviable" y lo llamamos "SMR.conf"

5- Tiene que quedar asi para poder alojar las 2 paginas en 1 documento

```html
<VirtualHost *:80>
        ServerName www.smr.com
        DocumentRoot /var/www/smr/web
</VirtualHost>

<VirtualHost *:9999>
        ServerName www.smr.com
        DocumentRoot /var/www/smr/intranet
        DirectoryIndex intranet.html


        <Directory /var/www/smr/intranet>
                AuthType Basic
                AuthName "Intranet SMR"
                AuthUserFile /etc/apache2/.htpasswd
                Require valid-user
        </Directory>
</VirtualHost>
```

6- Ahora toca habilitar y dehabilitar con los siguientes comandos: sudo a2ensite smr.conf sudo a2dissite 000-default.conf sudo apachectl configtest sudo systemctl restart apache2

7- Y ya podriamos acceder por ip, pero si queremos acceder por url hay que hacer lo siguiente

8- Tenemos que modificar el archivo que esta en "System32 drivers etc hosts" en caso de windows y "sudo nano /etc/hosts" en caso de linux

9- Dentro añadimos en na linea nueva y añadimos "192.168.56.10 (la ip del server) www.smr.com
