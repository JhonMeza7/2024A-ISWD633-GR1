# Imagen
Es un archivo único que contiene todos los programas, librerías, dependencias y configuraciones necesarias para instalar y/o ejecutar una aplicación o un conjunto de aplicaciones.
![Imagen](imagenes/imagen.PNG)


## ¿Cuál es la relación entre una imagen y un contenedor? 

```markdown
## Relación entre Imagen y Contenedor

### Creación:

- Una imagen actúa como una plantilla para crear contenedores.
- Cuando ejecutas un contenedor, Docker utiliza una imagen especificada para crear el contenedor.

### Instanciación:

- Un contenedor es una instancia en ejecución de una imagen.
- Múltiples contenedores pueden ser creados a partir de la misma imagen, cada uno funcionando de manera independiente.

### Aislamiento y Portabilidad:

- La imagen proporciona una forma de empaquetar la aplicación y todas sus dependencias en un formato portátil y replicable.
- El contenedor utiliza esta imagen para proporcionar un entorno de ejecución aislado.

### Persistencia:

- Las imágenes son inmutables y se almacenan en el sistema de archivos de Docker.
- Los contenedores pueden ser volátiles o persistentes. Los datos generados dentro de un contenedor pueden persistir
a través de volúmenes o ser descartados al terminar el contenedor.
```

![Imagen y contenedores](imagenes/imagenYcontenedores.JPG)
## Comandos para imágenes

### Descargar imagen
Descarga la última versión de la imagen disponible en el registro de Docker.

```
docker pull <nombre imagen> 
```

Descarga una versión específica de la imagen, cada imagen tiene etiquetas (tags) para diferentes versiones.
Una imagen puede tener la etiqueta latest para representar la última versión, si no se especifica una etiqueta se hará referencia a la versión latest.

```
docker pull <nombre imagen>:<tag>
```

Descargar la imagen **hello-world**

![image](https://github.com/JhonMeza7/2024A-ISWD633-GR1/assets/89060377/ca8713ff-e3dc-4a6d-9a97-3946ab534c41)

**¿Qué es nginx**

¿Qué es Nginx?
Nginx (pronunciado "engine x") es un servidor web de alto rendimiento que también puede funcionar como un proxy inverso, un equilibrador de carga, un proxy de correo y un caché HTTP. Es conocido por su alta eficiencia, estabilidad y bajo uso de recursos. Nginx fue desarrollado originalmente por Igor Sysoev y lanzado en 2004, y ha ganado popularidad rápidamente debido a su capacidad para manejar una gran cantidad de conexiones simultáneas con un uso mínimo de memoria.

Características de Nginx:
Servidor Web: Sirve contenido web estático de manera rápida y eficiente.
Proxy Reverso: Puede actuar como un intermediario entre clientes y servidores backend, manejando las solicitudes entrantes y distribuyéndolas entre varios servidores backend.
Balanceador de Carga: Distribuye el tráfico entre múltiples servidores para optimizar el rendimiento y garantizar la alta disponibilidad.
Proxy de Correo: Soporta protocolos IMAP, POP3 y SMTP.
Caché HTTP: Almacena respuestas para acelerar las solicitudes posteriores.


Descargar la imagen  **nginx** en la versión **alpine**
![image](https://github.com/JhonMeza7/2024A-ISWD633-GR1/assets/89060377/6a4ddcdf-a456-4581-a659-828aacd16ac5)

### Listar imágenes

```
docker images
```

![image](https://github.com/JhonMeza7/2024A-ISWD633-GR1/assets/89060377/e1ec773a-69b0-4751-85e9-2cd05912eb99)


**Identificadores**
En Docker, se utilizan varios identificadores para diferenciar de manera única los elementos del sistema, como imágenes, contenedores, volúmenes y redes. Estos identificadores son generados automáticamente por Docker y son únicos dentro del contexto del sistema Docker en el que se encuentran. 

### Inspeccionar una imagen
El comando docker inspect se utiliza para obtener información detallada sobre un objeto de Docker específico, como un contenedor, una imagen, un volumen o una red.  Proporciona información en formato JSON sobre el objeto especificado.

```
docker inspect <nombre imagen>
docker inspect <nombre imagen>:<tag>
```

Inspeccionar la imagen hello-world 

![image](https://github.com/JhonMeza7/2024A-ISWD633-GR1/assets/89060377/21b86c35-eb3a-4792-bc0f-550167abc1d4)

**¿Con qué algoritmo se está generando el ID de la imagen**
```
 "Id": "sha256:d2c94e258dcb3c5ac2798d32e1249e42ef01cba4841c2234249495f87264ac5a",
        "RepoTags": [
            "hello-world:latest"
        ],
```
### Filtrar imágenes

```
docker images | grep <termino a buscar>

```

### Para eliminar una imagen
Eliminar permanentemente la imagen de tu sistema Docker.

```
docker rmi <nombre imagen>:<tag>
```

Eliminar la imagen hello-world 

-f: Es la opción para forzar la eliminación de la imagen incluso si hay contenedores en ejecución que utilizan esa imagen.
Cuando eliminas una imagen Docker, Docker no elimina automáticamente los contenedores que se han creado a partir de esa imagen. Esto significa que, aunque hayas eliminado la imagen, el contenedor seguirá ejecutándose normalmente.  
**Considerar**
Eliminar una imagen no afecta a los contenedores que se han creado a partir de esa imagen, a menos que esos contenedores dependan de archivos o configuraciones específicas de la imagen eliminada. En ese caso, es posible que los contenedores se comporten de manera inesperada después de eliminar la imagen.
Es una buena práctica detener y eliminar todos los contenedores que dependan de una imagen antes de eliminar la imagen en sí.

```
docker rmi -f <nombre imagen>:<tag>
```

![image](https://github.com/JhonMeza7/2024A-ISWD633-GR1/assets/89060377/a03ebe96-30ef-40d5-b732-ae55afb6cb7f)


