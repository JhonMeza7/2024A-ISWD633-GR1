## Esquema para el ejercicio
![Imagen](imagenes/esquema-ejercicio3.PNG)

### Crear red net-wp

docker network create net-wp

![image](https://github.com/JhonMeza7/2024A-ISWD633-GR1/assets/89060377/14ae714b-1afe-413e-a802-dff89b7ea1bb)

### Para que persista la información es necesario conocer en dónde mysql almacena la información.
Para que la información persista en MySQL, es necesario conocer que la imagen oficial de MySQL para Docker almacena sus datos en el sistema de archivos del contenedor, dentro del directorio /var/lib/mysql. 

# COMPLETAR LA SIGUIENTE ORACIÓN. REVISAR LA DOCUMENTACIÓN DE LA IMAGEN EN https://hub.docker.com/)
En el esquema del ejercicio la carpeta contenedor (a) es (COMPLETAR CON LA RUTA)
Ruta carpeta host: .../ejercicio3/db

### ¿Qué contiene la carpeta db del host?
En este caso estaría vacia pero está sincronizada con var/lib/mysql
![image](https://github.com/JhonMeza7/2024A-ISWD633-GR1/assets/89060377/94453906-5b67-42b4-ba5d-e78d12ed8aba)


### Crear un contenedor con la imagen mysql:8  en la red net-wp, configurar las variables de entorno: MYSQL_ROOT_PASSWORD, MYSQL_DATABASE, MYSQL_USER y MYSQL_PASSWORD
![image](https://github.com/JhonMeza7/2024A-ISWD633-GR1/assets/89060377/0049c755-affc-4abc-925e-a061c69e8ae8)

docker run -d --name wordpress-container \
    --network net-wp \
    -e WORDPRESS_DB_HOST=mysql-container \
    -e WORDPRESS_DB_USER=nombre_usuario \
    -e WORDPRESS_DB_PASSWORD=contraseña_usuario \
    -e WORDPRESS_DB_NAME=nombre_base_datos \
    wordpress:latest

![image](https://github.com/JhonMeza7/2024A-ISWD633-GR1/assets/89060377/fac7e394-aef0-4e14-83d0-c87d5a772f2d)


### ¿Qué observa en la carpeta db que se encontraba inicialmente vacía?

En la carpeta db que estaba inicialmente vacía, observarás que ahora contiene los archivos y directorios que MySQL utiliza para almacenar sus datos. Estos archivos incluirán archivos binarios de registro, archivos de datos de las bases de datos y otros archivos de control utilizados por el motor de base de datos MySQL para administrar y almacenar la información de las bases de datos.

### Para que persista la información es necesario conocer en dónde wordpress almacena la información.
# COMPLETAR LA SIGUIENTE ORACIÓN. REVISAR LA DOCUMENTACIÓN DE LA IMAGEN EN https://hub.docker.com/)
En el esquema del ejercicio la carpeta contenedor (b) es (COMPLETAR CON LA RUTA)
Ruta carpeta host: .../ejercicio3/www

### Crear un contenedor con la imagen wordpress en la red net-wp, configurar las variables de entorno WORDPRESS_DB_HOST, WORDPRESS_DB_USER, WORDPRESS_DB_PASSWORD y WORDPRESS_DB_NAME (los valores de estas variables corresponden a los del contenedor creado previamente)

docker run -d --name wordpress-container \
    --network net-wp \
    -v /ruta/a/ejercicio3/www:/var/www/html \
    -e WORDPRESS_DB_HOST=mysql-container \
    -e WORDPRESS_DB_USER=nombre_usuario \
    -e WORDPRESS_DB_PASSWORD=contraseña_usuario \
    -e WORDPRESS_DB_NAME=nombre_base_datos \
    wordpress:latest

![image](https://github.com/JhonMeza7/2024A-ISWD633-GR1/assets/89060377/0b80d0aa-95d0-4ecd-9d43-185e07ae170a)


### Personalizar la apariencia de wordpress y agregar una entrada

### Eliminar el contenedor y crearlo nuevamente, ¿qué ha sucedido?

# COMPLETAR CON LA RESPUESTA A LA PREGUNTA



