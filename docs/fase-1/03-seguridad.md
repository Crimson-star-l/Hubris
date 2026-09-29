# Seguridad 

La seguridad de Hubris se basa en limitar el acceso al servidor, reducir la exposición de servicios y separar las diferentes partes de la infraestructura.

Las principales medidas implementadas en esta fase son:

- firewalld para controlar el tráfico.
- Tailscale para el acceso privado.
- SSH para administración remota.
- Restricción del acceso a Cockpit.
- Contenedores para aislar servicios.

## Firewall
Hubris utiliza `firewalld` para controlar las conexiones entrantes y separar el tráfico mediante zonas.

Las interfaces utilizadas se encuentran distribuidas de la siguiente manera:

|Zona|Interfaz|Propósito|
-------------------------
|public|wlp2d0|Red local|
|tailscale|tailscale0|Accesoprivado|
|docker|docker0|Redes de contenedores|

La configuración puede consultarse con:

```bash
sudo firewall-cmd --get-active-zones
sudo firewall-cmd --list-all
```

La intención es mantener únicamente los servicios necesarios accesibles desde cada red.

## Principio de mínimo privilegio

La administración del sistema se realiza mediante un usuario normal y `sudo` cuando se requieren privilegios administrativos.

No se utiliza `root` como usuario habitual.

Además, los servicios únicamente se exponen cuando existe una necesidad concreta de acceso.

