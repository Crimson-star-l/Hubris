# Contenedores

Podman es el motor de contenedores utilizado por Hubris.

Su instalación permite ejecutar y administrar contenedores mediante la línea de comandos sin depender de un daemon central.

Algunos comandos utilizados para administrar los contenedores son:

podman ps
podman ps -a
podman images
podman network ls

## Red de contenedores
Los contenedores utilizan redes independientes para permitir la comunicación entre los servicios sin depender directamente de la red física del servidor.

Actualmente Hubris utiliza la red:

`nextcloud-net`

Esta red permite la comunicación entre los contenedores que forman parte de la infraestructura actual.

## Contenedores actuales

|Contenedor|Imagen|Función|
|---------|-------|---------|
|nextcloud|nextcloud:latest|Aplicación de nube local|
|nextcloud-db|postgres:17|Base de datos|

Los contenedores se comunican mediante la red nextcloud-net.

La aplicación utiliza PostgreSQL como base de datos, mientras que la comunicación entre ambos se mantiene dentro de la red de contenedores.

## Administración
Administración

El estado de los contenedores puede consultarse mediante:
```bash
podman ps -a
```

Los registros de un contenedor pueden consultarse mediante:
```bash
podman logs <contenedor>
```

Y los detalles de la red:
```bash
podman network inspect nextcloud-net
```
