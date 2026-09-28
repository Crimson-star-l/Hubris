# Sistema Base


La primera etapa de Hubris consiste en prepara el sistema operativo y el harware que serviran como base para la infraestructura, el equipo utilizado es una HP ProBook 440 G3 reutilizado para funcionar como servidor doméstico. Sobre este equipo se instaló openSUSE Tumbleweed KDE y se configuró el entorno necesario para administrar el sistema

El objetivo de esta etapa es disponer de un sistema funcional y estable antes de incorporar de los componentes de red, seguridad y servicios de Hubris.

## Hardware

| Componente | Especificación |
|------------|----------------|
| Equipo | HP ProBook 440 G3 |
| CPU | Intel Core i7-6500U |
| RAM | 16 GB |
| Almacenamiento | SSD ~500 GB |
| GPU | Intel HD Graphics 520 |

El equipo fue seleccionado como servidor debido a que permite reutilizar hardware existente y dispone de recursos suficientes para ejecutar los servicios iniciales de Hubris.

## Sistema operativo 

Se eligio openSUSE Tumbleweed como base debido a su modelo rolling release y a las herramientas disponibles para la administración del sistema.
Aunque el equipo funciona como servidor, se mantiene el entorno KDE para conservar la posibilidad de utilizar el equipo directamente cuando sea necesario.
Se puede decir que de cierto modo es un servidor hibrido mantiene las funcionalidades del entorno gráfico y no en una maáquina de servidor en la cual se interactua solo mediante el terminal.

## Configuración inicial
Podremos comprobar el hostname de nuestro servidor con el comando:
```bash
hostnamectl``` 

Se utiliza como shell principal zsh debido a su conveniencia y manejo de plugins y atajos, además de que es bastante modificable

```bash
echo $SHELL```

Resultado esperado: /usr/bin/zsh

Plugins y apps instalados sobre zsh 

| Herramienta | Función                   |
| ----------- | ------------------------- |
| Zsh         | Shell principal           |
| eza         | Listado de archivos       |
| bat         | Visualización de archivos |
| fzf         | Búsqueda interactiva      |
| zoxide      | Navegación rápida         |
| Neovim      | Editor de texto           |
| Git         | Control de versiones      |


