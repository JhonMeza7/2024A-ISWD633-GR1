# Variables de Entorno
### ¿Qué son las variables de entorno

Las variables de entorno son un mecanismo que los sistemas operativos utilizan para almacenar información que puede ser utilizada por procesos y aplicaciones en ejecución. Estas variables contienen valores que son necesarios para la configuración y operación de dichos procesos y pueden influir en el comportamiento del sistema.

### Para crear un contenedor con variables de entorno

```
docker run -d --name <nombre contenedor> -e <nombre variable1>=<valor1> -e <nombre variable2>=<valor2>
```

### Crear un contenedor a partir de la imagen de nginx:alpine con las siguientes variables de entorno: username y role. Para la variable de entorno rol asignar el valor admin.

![image](https://github.com/JhonMeza7/2024A-ISWD633-GR1/assets/89060377/a30b0a25-5b32-4712-998e-62fa91fb0301)


## CAPTURA CON LA COMPROBACIÓN DE LA CREACIÓN DE LAS VARIABLES DE ENTORNO DEL CONTENEDOR ANTERIOR
```
docker exec mi_contenedor sh -c 'echo $username'
docker exec mi_contenedor sh -c 'echo $role'
```
![image](https://github.com/JhonMeza7/2024A-ISWD633-GR1/assets/89060377/5ca83497-66d6-44b1-8ed9-5852c5509037)

### Crear un contenedor con mysql:8 , mapear todos los puertos

![image](https://github.com/JhonMeza7/2024A-ISWD633-GR1/assets/89060377/018a6232-b0f5-45df-9ac4-ec7a58bb020d)


### ¿El contenedor se está ejecutando?

No:
![image](https://github.com/JhonMeza7/2024A-ISWD633-GR1/assets/89060377/241d79f9-3e9e-4394-89a0-29836b64f761)


### Identificar el problema
Se necesitan las variables de entorno
![image](https://github.com/JhonMeza7/2024A-ISWD633-GR1/assets/89060377/0036b92a-60c0-459c-9f52-faa6cc63331c)


### Eliminar el contenedor creado con mysql:8 

![image](https://github.com/JhonMeza7/2024A-ISWD633-GR1/assets/89060377/dc5c9e51-d1d2-4733-b6c4-17f46d25a883)


### Para crear un contenedor con variables de entorno especificadas
- Portabilidad: Las aplicaciones se vuelven más portátiles y pueden ser desplegadas en diferentes entornos (desarrollo, pruebas, producción) simplemente cambiando el archivo de variables de entorno.
- Centralización: Todas las configuraciones importantes se centralizan en un solo lugar, lo que facilita la gestión y auditoría de las configuraciones.
- Consistencia: Asegura que todos los miembros del equipo de desarrollo o los entornos de despliegue utilicen las mismas configuraciones.
- Evitar Exposición en el Código: Mantener variables sensibles como contraseñas, claves API, y tokens fuera del código fuente reduce el riesgo de exposición accidental a través del control de versiones.
- Control de Acceso: Los archivos de variables de entorno pueden ser gestionados con permisos específicos, limitando quién puede ver o modificar la configuración sensible.

Previo a esto es necesario crear el archivo y colocar las variables en un archivo, **.env** se ha convertido en una convención estándar, pero también es posible usar cualquier extensión como **.txt**.
```
docker run -d --name <nombre contenedor> --env-file=<nombreArchivo>.<extensión> <nombre imagen>
```
**Considerar**
Es necesario especificar la ruta absoluta del archivo si este se encuentra en una ubicación diferente a la que estás ejecutando el comando docker run.

### Crear un contenedor con mysql:8 , mapear todos los puertos y configurar las variables de entorno mediante un archivo
Primero crear el archivo variables.env

![image](https://github.com/JhonMeza7/2024A-ISWD633-GR1/assets/89060377/2c704ac4-9e28-4fdd-870a-c06d029468ef)


```
docker run -d --name mysql_container --env-file=variables.env -p 3306:3306 -p 33060:33060 mysql:8
```
![image](https://github.com/JhonMeza7/2024A-ISWD633-GR1/assets/89060377/ca24bf59-69fc-4b01-aa00-b43fa9d573c3)


# CAPTURA CON LA COMPROBACIÓN DE LA CREACIÓN DE LAS VARIABLES DE ENTORNO DEL CONTENEDOR ANTERIOR 

![image](https://github.com/JhonMeza7/2024A-ISWD633-GR1/assets/89060377/87a282d8-e5d2-4d9d-9078-f22371c26af5)
![image](https://github.com/JhonMeza7/2024A-ISWD633-GR1/assets/89060377/3cfbd3f8-9e7b-4c3f-968d-7e82f9a16c38)

### ¿Qué bases de datos existen en el contenedor creado?

![image](https://github.com/JhonMeza7/2024A-ISWD633-GR1/assets/89060377/8964072a-01e3-4187-b20e-1bbc36d5bf9e)
![image](https://github.com/JhonMeza7/2024A-ISWD633-GR1/assets/89060377/91e28bd7-5760-425d-ae3a-314090b1fece)
