# Red y acceso al servidor

Hubris utiliza tailscale como mecanismo principal para establecer conexiones remotas con el servidor. Esto permite que los dispositivos autorizados formen parte de una misma red superpuesta y puedan comunicarse con los servicios que el servidor expone dentro de la tailnet.


![Diagrama de la tailnet](../assets/Diagrama-Tailnet.png)

La conexión mediante Tailscale proporciona el camino de acceso hacia el servidor, pero no concede automáticamente permisos administrativos sobre el sistema. Cada servicio mantiene sus propios mecanismos de autenticación y autorización.

## Firewalld
Tailscale proporciona el mecanismo de conectividad, mientras que firewalld se encarga de controlar que tráfico puede acceder al servidor a través de sus diferentes interfaces de red.

El servidor utiliza diferentes zonas de firewalld para aplicar políticas según la interfaz por la que llega el tráfico.

la interfaz `tailscale0` se utiliza para las conexiones provenientes de la tailnet, mientras que la interfaz de red física del servidor se encuentra asociada a la red local.

De esta forma el acceso a los servicios administrativos puede restringirse según la interfaz y las reglas configuradas en el firewalld.


## Acceso administrativo

### SSH
SHH es utilizado para administrar el servidor remotamente.

El acceso puede realizarse mediante la red de Tailscale, evitando depender de una exposición directa del servidor hacia Internet.

De modo que podemos hacer `ssh [IP del tailnet]`

### Cockpit
Cockpit proporciona una interfaz web para la administración del sistema.

Su acceso está restringido a la red de Tailscale, por lo que no se encuentra expuesto en la interfaz de red pública.

Esto permite utilizar la administración web sin publicar el puerto de Cockpit directamente en Internet.
