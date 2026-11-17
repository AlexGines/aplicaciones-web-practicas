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
