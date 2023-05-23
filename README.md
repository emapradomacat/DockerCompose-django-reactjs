# Proyecto Django Reactjs - Craftech - EMA

Proyecto con despliegue Dockerizado que contiene una aplicación "Reloj/Calendario" desarrollada con Django (backend) y React.js (frontend). Muestra fecha y hora actual en un formato específico.
Este procedimiento es válido para despliegues tanto como locales o en nube, al final se revisarán algunas consideraciones a tener en cuenta para el último caso.


## Estructura de Proyecto

proyecto/
- README.md
- docker-compose.yaml
- backend/
  - Dockerfile
  - Project/
    - views.py
    - setting.py
  - ...
- frontend/
  - Dockerfile
  - src/
    - App.js
    - App.css
  - ...


## Requisitos Previos

Asegúrate de tener instalado lo siguiente en tu pc local o instancia en nube antes de continuar:
- Python v3.10.6
- Docker v20.10.21
- Docker Compose v2.18.1
- Git v2.34.1


## Preparación del Entorno de Trabajo
1. Clonar el repositorio a nuestra área de trabajo
```
git clone https://github.com/emapradomacat/django-reactjs-reloj-calendario.git
```

## Despliegue de la Aplicación
1. Navega hasta el directorio raíz del proyecto clonado.
```
cd django-reactjs-reloj-calendario
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
CONTAINER ID   IMAGE              COMMAND                  CREATED         STATUS         PORTS                                       NAMES
53c15d00c4b0   django-react-api   "bash -c 'python man…"   2 minutes ago   Up 2 minutes   0.0.0.0:8000->8000/tcp, :::8000->8000/tcp   django-react-api-1
c493f03a70f9   django-react-web   "docker-entrypoint.s…"   2 minutes ago   Up 2 minutes   0.0.0.0:3000->3000/tcp, :::3000->3000/tcp   django-react-web-1
```
5. Una vez que los contenedores estén en ejecución, podrás acceder a la aplicación en tu navegador web en la siguiente dirección:

http://localhost:3000

¡Y eso es todo! Ahora deberías ver la aplicación de Reloj/Calendario funcionando en tu entorno local.



## Fin de Uso y Limpieza
Con el siguiente comando detenemos y eliminamos los contenedores.
```
docker-compose down
```
Para una limpieza total será necesario borrar las imágenes correspondientes al frontend y backend.
```
docker image rm django-react-web
docker image rm django-react-api
```


## ***Consideraciones al Desplegar en la Nube***
Asegúrate de tener en cuenta lo siguiente:
- Crear una Cuenta en el proveedor de servicios en la nube (por ejemplo, AWS, Google Cloud, Azure, etc.).
- Crear una instancia de servidor virtual (VM) en la nube utilizando la plataforma elegida.
- Ten en cuenta que al utilizar servicios en la nube, es posible incurrir en costos asociados. Algunos servicios pueden tener niveles de capa gratuita limitados y, si se exceden esos límites, podrían generarse cargos adicionales. Asegúrate de comprender las políticas de facturación del proveedor de servicios en la nube y supervisar tu uso para evitar sorpresas en la factura.
Recomendamos revisar la documentación del proveedor de servicios en la nube y configurar alertas o límites de uso para mantener el control sobre los costos y evitar gastos inesperados.




## Autor

Este proyecto fue creado por Emanuel Prado Macat.
Cualquier consulta a emapradomacat@gmail.com -

