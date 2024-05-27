# Contenedores

### Crear un contenedor
Para crear un nuevo contenedor Docker a partir de una imagen específica, pero sin iniciarlo automáticamente. 

```
docker create --name <nombre contenedor> <nombre imagen>:<tag>
```
Crear el contenedor  **srv-web** usando la imagen nginx version alpine

![image](https://github.com/JhonMeza7/2024A-ISWD633-GR1/assets/89060377/5a3a8774-f0a8-4232-8cb6-79018aebe8fe)

Si creas un contenedor en Docker sin asignarle un nombre específico utilizando la opción --name, Docker asignará automáticamente un nombre aleatorio al contenedor. Este nombre suele consistir en una combinación de palabras y números.  

Crear el contenedor usando la imagen hello-world

![image](https://github.com/JhonMeza7/2024A-ISWD633-GR1/assets/89060377/c41bb551-9df2-40b8-b301-b4801aae8aa8)


### Listar los contenedores ejecutándose o no

```
docker ps -a
```

![image](https://github.com/JhonMeza7/2024A-ISWD633-GR1/assets/89060377/9d3d13bb-5eac-4fc9-bbb3-aad80af31514)
---
![image](https://github.com/JhonMeza7/2024A-ISWD633-GR1/assets/89060377/d4560091-2b9b-488d-8818-06dba8dc82ea)

### Para iniciar un contenedor

```
docker start <nombre contenedor o identificador>
```
Iniciar el contenedor srv-web 

![image](https://github.com/JhonMeza7/2024A-ISWD633-GR1/assets/89060377/6cd198d0-56e2-49ae-b783-c76348ba3112)
---
![image](https://github.com/JhonMeza7/2024A-ISWD633-GR1/assets/89060377/7570a60f-4030-4cb3-b0af-5d53c72b4ce4)


### Listar los contenedores ejecutándose
```
docker ps 
docker ps | grep <nombre contenedor>
```

### Para detener un contenedor

```
docker stop <nombre contenedor>
```

### Para crear un contenedor y ejecutarlo inmediatamente

```
docker run --name <nombre contenedor> <nombre imagen>:<tag>
```
![Ecosistema de Docker](imagenes/dockerRun.PNG)

Crear y ejecutar inmediatamente el contenedor **srv-web2** usando la imagen nginx:alpine

```
docker run --name srv-web2 nginx:alpine
```

![image](https://github.com/JhonMeza7/2024A-ISWD633-GR1/assets/89060377/062952a1-be6d-47e5-8585-b70967b5ecdb)
---
![image](https://github.com/JhonMeza7/2024A-ISWD633-GR1/assets/89060377/8f0560ba-488d-4fc4-b4ee-a7ca97c5bcb4)


**¿Qué sucede luego de la ejecución del comando?**

Cuando ejecutas el comando `docker run --name srv-web2 nginx:alpine`, Docker realiza varias acciones secuenciales para crear y ejecutar un contenedor. Aquí está el desglose de lo que sucede:

#### Descarga de la Imagen:

- Si la imagen `nginx:alpine` no está presente localmente en tu sistema, Docker la descarga desde Docker Hub (o desde el registro configurado).

#### Creación del Contenedor:

- Docker crea un nuevo contenedor a partir de la imagen `nginx:alpine`.
- El contenedor es nombrado `srv-web2` según lo especificado por la opción `--name`.

#### Asignación de un ID de Contenedor:

- Docker asigna un ID único al contenedor.

#### Configuración del Entorno:

- Docker configura el entorno de ejecución para el contenedor basado en la imagen, incluyendo el sistema de archivos, las variables de entorno, la configuración de red, etc.

#### Ejecución del Contenedor:

- Docker inicia el contenedor, ejecutando el proceso predeterminado definido en la imagen `nginx:alpine`. Para `nginx`, esto típicamente significa iniciar el servidor web Nginx.

#### Visualización de la Salida:

- Si no se ha especificado `-d` (modo desacoplado o "detached"), la salida del contenedor (stdout y stderr) se mostrará en tu terminal.
- Si Nginx se inicia correctamente, verás los mensajes de inicio del servidor web en la terminal.


Cuando ejecutas un contenedor en primer plano sin la opción -d (modo detach), el contenedor captura la entrada estándar (stdin) del terminal, lo que significa que el terminal queda "atrapado" y no puedes introducir más comandos hasta que detengas el contenedor.

### Para crear un contenedor y ejecutarlo inmediatamente sin estar vinculados al mismo
-d: Es la opción que indica a Docker que ejecute el contenedor en segundo plano (en modo "detach").
Cuando un contenedor se ejecuta en segundo plano, Docker devuelve el control al terminal inmediatamente después de iniciar el contenedor, lo que permite al usuario seguir ejecutando otros comandos en el mismo terminal sin que el contenedor detenga la interacción.

```
docker run -d --name <nombre contenedor> <nombre imagen>:tag
```
Crear y ejecutar inmediatamente el contenedor **srv-web3** en modo detach usando la imagen nginx:alpine

```
docker run -d --name srv-web3 nginx:alpine

```
![image](https://github.com/JhonMeza7/2024A-ISWD633-GR1/assets/89060377/15e8a413-f834-411b-a380-ae8b1b25332f)

### Para eliminar un contenedor

```
docker rm <nombre contenedor>
```
Eliminar el contenedor que se creó a partir de la imagen hello-world 

```
docker rm hello-world
```

![image](https://github.com/JhonMeza7/2024A-ISWD633-GR1/assets/89060377/396a0b01-0287-490c-b23f-abcb60a3f488)


Verificar que el contenedor que se eliminó

```
docker ps -a
```
![image](https://github.com/JhonMeza7/2024A-ISWD633-GR1/assets/89060377/2daeed12-7070-41fb-9d6f-ac75741310ca)


### Para eliminar un contenedor que esté ejecutándose

```
docker rm -f <nombre contenedor>
```
Eliminar el contenedor **srv-web3** 

```
docker rm -f srv-web3
```
![image](https://github.com/JhonMeza7/2024A-ISWD633-GR1/assets/89060377/62977c7d-1005-4802-8bb1-4681d87d64e9)


Verificar que el contenedor que se eliminó

```
docker ps -a
```
![image](https://github.com/JhonMeza7/2024A-ISWD633-GR1/assets/89060377/d78907c7-3159-46b5-b983-e4753d094ee8)


### Para inspecionar un contenedor 

Inspeccionar el contenedor **srv-web** 

```
docker inspect srv-web
```
![image](https://github.com/JhonMeza7/2024A-ISWD633-GR1/assets/89060377/f7971f7d-8bc1-4878-ae4d-0c1a7d75d7bd)


Resultados de la práctica:
![image](https://github.com/JhonMeza7/2024A-ISWD633-GR1/assets/89060377/d0986746-507d-4b31-aa19-3e97aae0998a)
