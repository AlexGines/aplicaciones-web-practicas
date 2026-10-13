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
Deberias ver
```html
mariadb Ver 15.1 Distrib 10.11.14-MariaDB, for debian-linux-gnu (x86_64)
```
![Imagen version maria](https://github.com/AlexGines/aplicaciones-web-practicas/blob/main/capturas/mariaversion.png?raw=true)
