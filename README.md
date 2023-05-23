# Proyecto Django Reactjs - Craftech

Despliegue Dockerizado que contiene una aplicación predeterminada desarrollada en  Django (backend) y React.js (frontend). 
Este procedimiento es válido para trabajar tanto de manera local como en la nube, con algunas consideraciones a tener en cuenta si lo hacemos de esta última forma.


## Estructura de Archivos

DockerCompose-django-reactjs/
- README.md
- docker-compose.yaml
- backend/
  - apps/
  - backend/ 
  - Dockerfile
  - requirements.txt
  - manage.py
- frontend/
   - config/
   - public/
   - sctripts/
   - src/
     - index.js
     - App.css
     - ...
   - Dockerfile
   - package.json
   - package-lock.jason
   - yarn.lock 


## ***Consideraciones al Desplegar en la Nube***
Asegúrate de tener en cuenta lo siguiente:
- Crear una cuenta en el proveedor de servicios en la nube (por ejemplo, AWS, Google Cloud, Azure, etc.).
- Crear una instancia de servidor virtual (VM) en la nube utilizando la plataforma elegida.
- A partir de este momento puedes continuar con el procedimiento que se describe a continuación.
  
*- Ten en cuenta que al utilizar servicios en la nube, es posible incurrir en costos asociados. Algunos servicios pueden tener niveles de capa gratuita limitados y, si se exceden esos límites, podrían generarse cargos adicionales. Recomendamos revisar la documentación del proveedor de servicios en la nube y configurar alertas o límites de uso para mantener el control sobre los costos y evitar gastos inesperados.*


## Requisitos Previos

Asegúrate de tener instalado lo siguiente en tu pc local o instancia en nube antes de continuar:
- Python v3.10.6
- Docker v20.10.21
- Docker Compose v2.18.1
- Git v2.34.1


## Preparación del Entorno de Trabajo
1. Clonar el repositorio a nuestra área de trabajo
```
git clone https://github.com/emapradomacat/DockerCompose-django-reactjs.git
```

## Despliegue de la Aplicación
1. Navega hasta el directorio raíz del proyecto clonado.
```
cd DockerCompose-django-reactjs
```
2. Ejecuta los comandos docker-compose para iniciar los servicios de contenedores. Esto creará y ejecutará los contenedores de Docker para el backend y el frontend de la aplicación.
```
docker-compose build
docker-compose up
```
4. Verifica que los contenedores estén en funcionamiento correctamente y el mapeo de puertos sea de la siguiente manera.
```
$docker ps
```
```
CONTAINER ID   IMAGE                     COMMAND                  CREATED          STATUS          PORTS                                       NAMES
8f1f488913c8   django-reactjs-backend    "python manage.py ru…"   26 seconds ago   Up 22 seconds   0.0.0.0:8000->8000/tcp, :::8000->8000/tcp   django-reactjs-backend-1
690c3bd883d1   postgres:latest           "docker-entrypoint.s…"   2 hours ago      Up 23 seconds   5432/tcp                                    django-reactjs-db-1
1553de003682   django-reactjs-frontend   "docker-entrypoint.s…"   2 hours ago      Up 23 seconds   0.0.0.0:3000->3000/tcp, :::3000->3000/tcp   django-reactjs-frontend-1

```
5. Una vez que los contenedores estén en ejecución, podrás acceder a la aplicación en tu navegador web en la siguiente dirección:

http://localhost:3000


¡Y eso es todo!



## Fin de Uso y Limpieza
Con el siguiente comando detenemos y eliminamos los contenedores.
```
docker-compose down
```
Para una limpieza total será necesario borrar las imágenes correspondientes al frontend, backend y postgres.
```
docker image rm django-reactjs-backend
docker image rm django-reactjs-frontend
docker image rm postgres
```





## Autor

Este proyecto fue creado por Emanuel Prado Macat.
Cualquier consulta a emapradomacat@gmail.com -


