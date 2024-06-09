## Esquema para el ejercicio
![Imagen](imagenes/esquema-ejercicio5.PNG)

### Crear la red
![image](https://github.com/JhonMeza7/2024A-ISWD633-GR1/assets/89060377/be1b6c0d-67c1-480b-b20f-c8b30532d78d)

### Crear el contenedor mysql a partir de la imagen mysql:8, configurar las variables de entorno necesarias

![image](https://github.com/JhonMeza7/2024A-ISWD633-GR1/assets/89060377/c2e5323c-6583-4a17-bac8-c186b9878e7d)

### Crear el contenedor wordpress a partir de la imagen: wordpress, configurar las variables de entorno necesarias
![image](https://github.com/JhonMeza7/2024A-ISWD633-GR1/assets/89060377/d165616f-b272-4fe1-aeec-414c8d964bc2)


De acuerdo con el trabajo realizado, en la el esquema de ejercicio el puerto a es **(completar con el valor)**

Ingresar desde el navegador al wordpress y finalizar la configuración de instalación.
![image](https://github.com/JhonMeza7/2024A-ISWD633-GR1/assets/89060377/8f555515-7f4a-4ae8-8b9a-ed3576b44b8d)
![image](https://github.com/JhonMeza7/2024A-ISWD633-GR1/assets/89060377/5dd545f4-8c99-4218-aaee-fef2f7f1bb7a)


Desde el panel de admin: cambiar el tema y crear una nueva publicación.
Ingresar a: http://localhost:9300/ 
recordar que a es el puerto que usó para el mapeo con wordpress

![image](https://github.com/JhonMeza7/2024A-ISWD633-GR1/assets/89060377/b779befd-5eec-4e44-8813-f26bd607d272)


### Eliminar el contenedor wordpress
# COMPLETAR

### Crear nuevamente el contenedor wordpress
Ingresar a: http://localhost:9300/ 
recordar que a es el puerto que usó para el mapeo con wordpress

![image](https://github.com/JhonMeza7/2024A-ISWD633-GR1/assets/89060377/465dd954-e502-45cb-a2d1-e0ada1ce7b7e)

### ¿Qué ha sucedido, qué puede observar?

![image](https://github.com/JhonMeza7/2024A-ISWD633-GR1/assets/89060377/3ef8a873-766f-4765-8817-214ebb20b01c)
Al eliminar y recrear el contenedor de WordPress, observamos que todos los datos y configuraciones previas deberían estar intactos. Esto se debe a que los datos de WordPress se almacenan en la base de datos MySQL, y mientras el contenedor de MySQL no se haya eliminado, los datos permanecerán disponibles. Por lo tanto, la nueva instancia del contenedor de WordPress se conecta a la misma base de datos, recuperando todos los datos y configuraciones anteriores.

Comandos!

```
docker network create net-wp

```
```
docker run -d --name mysql-container \
  --network net-wp \
  -e MYSQL_ROOT_PASSWORD=root_password \
  -e MYSQL_DATABASE=wordpress_db \
  -e MYSQL_USER=wordpress_user \
  -e MYSQL_PASSWORD=wordpress_password \
  mysql:8

```

``` 
docker run -d --name wordpress-container \
  --network net-wp \
  -e WORDPRESS_DB_HOST=mysql-container:3306 \
  -e WORDPRESS_DB_NAME=wordpress_db \
  -e WORDPRESS_DB_USER=wordpress_user \
  -e WORDPRESS_DB_PASSWORD=wordpress_password \
  -p 9300:80 \
  wordpress

```

