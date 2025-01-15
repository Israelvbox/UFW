# UFW

En esta guía aprenderás qué es UFW, cómo configurarlo básicamente y explotar todas sus funcionalidades para gestionar correctamente el firewall de tu sistema.

<img src="https://github.com/Israelvbox/UFW/blob/main/images/Firewall.png " width=300px>

<br>

## ¿Qué es UFW?
UFW (Uncomplicated Firewall) es una herramienta sencilla y potente diseñada para gestionar las reglas de cortafuegos en sistemas basados en Linux. Actúa como una interfaz para iptables, facilitando la configuración y gestión de las reglas de red. Ideal tanto para principiantes como para administradores experimentados.

<br>

## Instalación
En la mayoría de distribuciones modernas, UFW viene preinstalado. Si no está instalado, puedes hacerlo con los siguientes comandos:

```shell
# En distribuciones basadas en Debian/Ubuntu
apt update && sudo apt install ufw
```
```shell
# En distribuciones basadas en Red Hat (con soporte para DNF)
dnf install ufw
```

<br>

## Políticas predeterminadas
```shell
# Toda conexión entrante que no este en las reglas, sera denegada
ufw default deny incoming
```

```shell
# Toda conexion saliente esta permitida
ufw default allow outgoing
```

<br>

## Activar, Deactivar, Reiniciar, Restablecer y ver el estado de UFW

### Activar
```shell
# Para Activar UFW, debemos escribir este comando:
ufw enable
```

### Desactivar
```shell
# Para Desactivar UFW, debemos escribir este comando:
ufw disable
```

### Reiniciar
```shell
# Si UFW ya esta Activo y modifica, agrega o elimina una regla debera reiniciar UFW.
ufw reload
```

### Restablecer
```shell
# Si deseamos volver a las reglas predeterminadas, debemos escribir esto:
ufw reset
```
### Ver Estado
```shell
# Para ver el estado de  UFW, debemos escribir este comando:
ufw status
```

<br>

## Permitir y Denegar conexíones

### Permitir un Puerto especifico
```shell
ufw allow 22
```

### Denegar un Puerto especifico
```shell
ufw deny 22
```

### Permitir por Puerto y Protocolo
```shell
ufw allow 80/tcp
```

<br>

## Eliminar Reglas

### Eliminar una regla especifica
```shell
ufw delete allow 22
```

### Eliminar una regla especifica mediante su identificador

```shell
ufw delete allow 22
```

<br>

## Listar Reglas

```shell
# Esto muestra todas las reglas con un numero asociado como identificador.
ufw status numbered
```

<br>

## Configuración Avanzada

### Permitir Rango de IP
```shell
# Esto permite solo conexiones de esa subred
ufw allow from 192.168.1.0/24
```

### Limitar conexiones
```shell
# Util para prevenir ataques de fuerza bruta, limitando los intentos por IP
ufw limit ssh
```
### Reglas por interfaz
```shell
# Esto permite conexiones entrantes al puerto 80 en la interfaz eth0
ufw allow in on eth0 to any port 80
```
