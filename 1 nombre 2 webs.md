# Un Nombre Dos Webs
## Aqui vamos a ver como crear 2 paginas distintas a las cuales se accede por el mismo url pero distinto puerto

1- Creamos las carpetas con "sudo mkdir -p /var/www/smr/web /var/www/smr/intranet" y añadimos un fichero index.html e intranet.html y le añadimos contenido a nuestras paginas

2- Creamos el usuario con el que vamos a acceder a la intranet con "sudo htpasswd -c /etc/apache2/.htpasswd admin" pedira la contraseña 2 veces con la que accederemos mas adelante a la pagina

3- Vamos a la carpeta de puertos que esta en apache y le decimos que escuche el "9999"

4- Copiamos el archivo 00 de la carpeta "sites eviable" y lo llamamos "SMR.conf"

5- Tiene que quedar asi para poder alojar las 2 paginas en 1 documento

![2paginasdoc] (https://raw.githubusercontent.com/AlexGines/aplicaciones-web-practicas/refs/heads/main/Captura%20de%202026-10-08%2017-33-21.png)

6- Ahora toca habilitar y dehabilitar con los siguientes comandos: sudo a2ensite smr.conf sudo a2dissite 000-default.conf sudo apachectl configtest sudo systemctl restart apache2

7- Y ya podriamos acceder por ip, pero si queremos acceder por url hay que hacer lo siguiente

8- Tenemos que modificar el archivo que esta en "System32 drivers etc hosts" en caso de windows y "sudo nano /etc/hosts" en caso de linux

9- Dentro añadimos en na linea nueva y añadimos "192.168.56.10 (la ip del server) www.smr.com
