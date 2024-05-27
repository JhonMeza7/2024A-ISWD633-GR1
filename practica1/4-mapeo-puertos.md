# Mapeo de puertos
El mapeo de puertos es un mecanismo que permite redirigir el tráfico de red desde un puerto en el host (tu máquina local o servidor) hacia un puerto específico en un contenedor Docker.
Por ejemplo, supongamos que tienes un contenedor que ejecuta un servidor web en el puerto 80 dentro del contenedor, pero quieres acceder a ese servidor desde tu navegador en la máquina host. Puedes usar el mapeo de puertos para redirigir el tráfico del puerto 80 del contenedor al puerto 3000 en el host. De esta manera, cuando accedas a http://localhost:3000 en tu navegador, el tráfico se dirigirá al servidor web dentro del contenedor en el puerto 80.

![mapeo](imagenes/mapeoPuertos.PNG)

### Para crear un mapeo de puertos (puerto host y puerto contenedor)
El mapeo de puertos se especifica al ejecutar un contenedor Docker utilizando la opción -p o --publish seguida de los puertos que deseas mapear
```
docker run -d --name <nombre contenedor> -p <puerto host>:<puerto contenedor> <nombre imagen>:<tag>

```
Crear un contenedor a partir de la imagen nginx version alpine con el mapeo de puertos del ejemplo gráfico, host 3000 y contenedor 80

En este caso no he podido usar el puerto 3000 debido a que lo tengo en uso, he ocupado el siguiente:

```
docker run -d --name srv-web -p 1024:80 nginx:alpine
```
![image](https://github.com/JhonMeza7/2024A-ISWD633-GR1/assets/89060377/91214947-1822-4691-a507-cccb6b6aabab)


# COLOCAR UNA CAPTURA DE PANTALLA  DEL ACCESO http://localhost:3000

```
http://localhost:1024/

```
![image](https://github.com/JhonMeza7/2024A-ISWD633-GR1/assets/89060377/d550a55a-49e3-4d9e-a7f4-c6689d53539c)


### Para mapear más de un puerto

```
docker run -d --name <nombre contenedor> -p <puerto host 01>:<puerto contenedor 01> -p <puerto host 02>:<puerto contenedor 02> <nombre imagen>:<tag>
```

Crear un contenedor a partir de la imagen rabbitmq version management-alpine, para este mapeo de puertos usar en el host los mismos puertos del contenedor.

```
docker run -d --name rabbitmq-container -p 15672:15672 -p 5672:5672 rabbitmq:management-alpine
```
![image](https://github.com/JhonMeza7/2024A-ISWD633-GR1/assets/89060377/94c48b0b-bee1-4c47-8cdf-12ef3c4e97ae)
