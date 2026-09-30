# Administración

Hubris CLI es una herramienta desarrollada para centralizar la administración de la infraestructura de Hubris desde la terminal.

Su objetivo es proporcionar una interfaz sencilla para consultar y controlar los componentes principales del servidor sin tener que ejecutar manualmente múltiples comandos de `systemd` y `Podman`.

## Objetivo 
Hubris CLI busca simplificar las tareas administrativas más frecuentes mediante un único comando.

Actualmente permite:

- Iniciar la infraestructura.
- Detener la infraestructura.
- Consultar su estado.
- Consultar el estado de los contenedores.
- Ejecutar tareas de mantenimiento.
- Mostrar la ayuda disponible.

## Comandos

```bash
hubris start
```
Inicia los componentes principales de Hubris mediante `hubris.target`

```bash
hubris stop
```
Detiene los componentes administrados por `hubris.target`

```bash
hubris status
```
Muestra el estado actual de la infraestructura.

La información mostrada incluye:

- Nombre del servidor.
- Tiempo de actividad.
- Estado de los servicios.
- Estado de los contenedores.

```bash
hubris maintenance
```
Actualiza los contenedores 

```bash
hubris help
```
Muestra los comandos disponibles y su función.

## Integración con systemd
Hubris utiliza `hubris.target` como punto central para administrar los servicios que forman parte de la infraestructura base.

hubris.target
├── sshd.service
├── tailscaled.service
├── firewalld.service
└── cockpit.socket

Una de las características de Hubris CLI es que no mantiene una lista fija de servicios dentro del código. En lugar de ello, obtiene las dependencias de hubris.target mediante systemd.
Esto permite que un nuevo servicio asociado al objetivo pueda ser detectado automáticamente por hubris status sin modificar manualmente una lista dentro del programa.

## Integración con podman
Hubris también obtiene información de los contenedores administrados mediante Podman.

El comando hubris status consulta los contenedores existentes y muestra su estado junto con los servicios de systemd.

De esta manera, la infraestructura puede visualizarse desde un único comando.


