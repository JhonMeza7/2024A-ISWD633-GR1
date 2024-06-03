![image](https://github.com/JhonMeza7/2024A-ISWD633-GR1/assets/89060377/ce009de7-0a73-4db2-9b9f-5879cd84e126)# VOLUMEN TIPO HOST
Un volumen host (o bind mount) es un tipo de volumen donde se monta un directorio o archivo específico del sistema de archivos del host en un contenedor.

```
docker run -d --name <nombre contenedor> -v <ruta carpeta host>:<ruta carpeta contenedor> <imagen> 
```

### Crear un volumen tipo host con la imagen nginx:alpine, para la ruta carpeta host: directorio en donde se encuentra la carpeta html en tu computador y para la ruta carpeta contenedor: /usr/share/nginx/html esta ruta se obtiene al revisar la se obtiene desde la documentación
![Volúmenes](imagenes/volumen-host.PNG)
# COMPLETAR CON EL COMANDO
```
docker run -d --name nginx-container -v ./html:/usr/share/nginx/html:ro -p 8080:80 nginx:alpine
```
![image](https://github.com/JhonMeza7/2024A-ISWD633-GR1/assets/89060377/44fbb29a-8d57-4d1c-ae77-35b9dc61fb85)

### ¿Qué sucede al ingresar al servidor de nginx?
Al ingresar al servidor Nginx (por ejemplo, visitando http://localhost:8080 en tu navegador), Nginx servirá el contenido desde el directorio /usr/share/nginx/html dentro del contenedor. Dado que hemos montado un volumen desde /path/to/your/html en el host a /usr/share/nginx/html en el contenedor, verás el contenido de esa carpeta de tu host. Si no hay un archivo index.html en esa carpeta, Nginx probablemente mostrará una página de error o un listado de directorios, dependiendo de la configuración de Nginx.

### ¿Qué pasa con el archivo index.html del contenedor?
No hay, está vacío 
![image](https://github.com/JhonMeza7/2024A-ISWD633-GR1/assets/89060377/e515bade-d53a-4989-b683-0256c60a6a4c)


### Ir a https://html5up.net/ y descargar un template gratuito, descomprirlo dentro de nginx/html
### ¿Qué sucede al ingresar al servidor de nginx?
Se copian los ementos en la carpeta que fue montada
![image](https://github.com/JhonMeza7/2024A-ISWD633-GR1/assets/89060377/c23cb761-d787-436d-944b-f19ae78958d2)


### Eliminar el contenedor
![image](https://github.com/JhonMeza7/2024A-ISWD633-GR1/assets/89060377/81288b37-ab2d-43e0-8de2-a738ee0c7628)

### ¿Qué sucede al crear nuevamente el mismo contenedor con volumen de tipo host a los directorios definidos anteriormente?

Se quedan los archivos:
![image](https://github.com/JhonMeza7/2024A-ISWD633-GR1/assets/89060377/7001d777-0039-4254-987c-977ebe27889c)
![image](https://github.com/JhonMeza7/2024A-ISWD633-GR1/assets/89060377/e1d4987e-ffd1-4533-a6f3-950610da29da)


### ¿Qué hace el comando pwd?
Me da la direccion de la ruta actual.

Si quieres incluir el comando pwd dentro de un comando de Docker, lo puedes hacer de diferentes maneras dependiendo del shell que estés utilizando.


### Volumen tipo host usando PWD y PowerShell
```
docker run -d --name <nombre contenedor> --publish published=<valorPuertoHost>,target=<valor> -v ${PWD}/<ruta relativa>:<ruta absoluta> <nombre imagen>:<tag> 
```

### Volumen tipo host usando PWD (Git Bash)

```
docker run -d --name <nombre contenedor> --publish published=<valorPuertoHost>,target=<valor> -v $(pwd -W)/html:/usr/share/nginx/html <nombre imagen>:<tag> 
```

### Volumen tipo host usando PWD (en Linux)

```
docker run -d --name <nombre contenedor> --publish published=<valorPuertoHost>,target=<valor> -v $(pwd)/html:/usr/share/nginx/html <nombre imagen>:<tag> 
```

