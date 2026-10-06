acceder a carpeta hosts desde anfitrion y escribir ip seguido de nombre de la web
practica guiada apache 2 punto 7
Pedir contraseña por el puerto 5555
mira los sites enable con -l y los desactivas

hace 2 copias del archivo 00 y los llama smr80com.conf y smr5555com.conf
Canvia el nombre de ServerName y añade la ruta smrcom

vas a var www html y crea el directorio añadido anteriormente
crea un index.html y añade info a la pagina

vuelve a etc apache2 y edita el archivo 5555
cambia el puerto, el server name que es el mismo y document root añade el mismo de antes sumado a /intranet

añadimos lo que pone en la practica de aules y lo escribimos debajo de document root, poniendo el directorio de arriba

instalamos el apache utils
aqui me quedo

y creamos la ruta que hemos puesto donde va a estar la pass y le añadimos un nombre de usuario
añadimos tambien una contraseña para el usuario
creamos la carpeta /intranet
en puertos añadimos que escuche el 5555 y habilitamos los sitios y hacemos reload
ahora modificariamos el fichero host en windows esta en system32 drivers etc y el archivo hosts y añadimos la ip y 
