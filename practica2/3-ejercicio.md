### Crear contenedor de Postgres sin que exponga los puertos. Usar la imagen: postgres:11.21-alpine3.17
```
docker run -d --name postgres_container postgres:11.21-alpine3.17
```
![image](https://github.com/JhonMeza7/2024A-ISWD633-GR1/assets/89060377/1b672f39-f625-409c-8e77-b460437bd13a)

### Crear un cliente de postgres. Usar la imagen: dpage/pgadmin4

![image](https://github.com/JhonMeza7/2024A-ISWD633-GR1/assets/89060377/c840a85f-2179-4215-9fc6-f59b249d657f)


![image](https://github.com/JhonMeza7/2024A-ISWD633-GR1/assets/89060377/c5030484-42ce-4237-8251-56085d574a8e)
![image](https://github.com/JhonMeza7/2024A-ISWD633-GR1/assets/89060377/de62b957-97c5-4492-b1c9-3403fe788efd)

La figura presenta el esquema creado en donde los puertos son:
- a: 5050
- b: 80
- c: 172.17.0.6/ 5432

![Imagen](imagenes/esquema-ejercicio3.PNG)

## Desde el cliente
### Acceder desde el cliente al servidor postgres creado.

![image](https://github.com/JhonMeza7/2024A-ISWD633-GR1/assets/89060377/604d8a4e-316d-453d-9c49-9345c66491bd)
![image](https://github.com/JhonMeza7/2024A-ISWD633-GR1/assets/89060377/491814b0-c80c-4865-a914-bc7c77582336)

### Crear la base de datos info, y dentro de esa base la tabla personas, con id (serial) y nombre (varchar), agregar un par de registros en la tabla, obligatorio incluir su nombre.

## Desde el servidor postgresl
### Acceder al servidor
### Conectarse a la base de datos info
# COMPLETAR
### Realizar un select *from personas
# AGREGAR UNA CAPTURA DE PANTALLA DEL RESULTADO
