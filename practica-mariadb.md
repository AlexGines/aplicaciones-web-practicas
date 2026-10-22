# Instalación de MariaDB y PHP en Ubuntu 24.04

### ¿Qué es una base de datos?
Una base de datos es como una carpeta ordenada que tiene tablas compuestas por columnas y filas

## Instalación
1- Actualiza la lista de paquetes y comprueba que Apache sigue funcionando
```html
sudo apt update
systemctl is-active apache2
```
![Imagen apache2 activo](https://github.com/AlexGines/aplicaciones-web-practicas/blob/main/capturas/apache2%20active.png?raw=true)

2- Instalamos MariaDB y comprobamos la version
```html
sudo apt install mariadb-server -y
mariadb --version
```
Deberías ver
```html
mariadb Ver 15.1 Distrib 10.11.14-MariaDB, for debian-linux-gnu (x86_64)
```
![Imagen version maria](https://github.com/AlexGines/aplicaciones-web-practicas/blob/main/capturas/mariaversion.png?raw=true)

Preguntas: ¿Qué diferencia hay entre active (running) y enabled?
            Active: Significa que funciona
            Enabled: Que esta disponible o tiene permiso
¿Qué pasaría con la web de WordPress si MariaDB estuviera active pero no enabled y se reiniciara el servidor?
Dejaría de funcionar y mostraría un error de conexión al reiniciar

### Comandos principales para mariaDB
1- sudo systemctl start mariadb     Arranca el servicio
2- sudo systemctl stop mariadb      Detiene el servicio
3- sudo systemctl restart mariadb   Reinicia el servicio
4- sudo systemctl status mariadb    Muestra su estado
5- sudo systemctl enable mariadb    Lo arranca automáticamente al encender el equipo

![imagen error maria](https://github.com/AlexGines/aplicaciones-web-practicas/blob/main/capturas/error%20y%20recu%20de%20la%20maria.png?raw=true)

Pregunta: Si WordPress no pudiera conectar con la base de datos, ¿qué dos comandos de este apartado usarías para saber si el problema es que MariaDB está parado?
          sudo systemctl status mariadb
          sudo service mariadb status

![php-v](https://github.com/AlexGines/aplicaciones-web-practicas/blob/main/capturas/php%20-v.png?raw=true)
![modulosphp](https://github.com/AlexGines/aplicaciones-web-practicas/blob/main/capturas/modulosphp.png?raw=true)

Pregunta: ¿Por qué es peligroso dejar info.php en un servidor real?
          porque expone información técnica sensible del entorno 
          
¿Para qué sirve el paquete php-mysql?
conectar los scripts de PHP con una base de datos MySQL o MariaDB


