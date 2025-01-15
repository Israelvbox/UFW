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
# La política predeterminada "deny incoming" bloquea todas las conexiones entrantes
# que no estén explícitamente permitidas por las reglas configuradas.
ufw default deny incoming
```

```shell
# La política predeterminada "allow outgoing" permite que cualquier conexión saliente
# se realice sin restricciones, lo que es común en la mayoría de las configuraciones de firewall.
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

## Permitir y Denegar conexiones

### Permitir un Puerto específico
```shell
# Permitir SSH (puerto 22) por nombre
ufw allow ssh 
```

```shell
# Permitir SSH (puerto 22) por puerto
ufw allow 22
```

```shell
# Permitir el puerto 22 solo desde una IP específica
ufw allow from 192.168.1.10 to any port 22
```

### Denegar un Puerto específico
```shell
# Denegar SSH (puerto 22) por nombre
ufw deny ssh 
```

```shell
 # Deniega el acceso por SSH en el puerto 22
ufw deny 22
```

### Permitir por Puerto y Protocolo
```shell
 # Permite el acceso al puerto 80 mediante el protocolo TCP
ufw allow 80/tcp
```

<br>

## Eliminar Reglas

### Eliminar una regla específica
```shell
# Elimina una regla basada en su identificador listado con 'ufw status'
ufw delete allow 22
```
o

```shell
# Elimina una regla basada en su identificador listado con 'ufw status numbered'
ufw delete <número_de_regla>

```

<br>

## Listar Reglas

```shell
# Esto muestra infromación detallada de las reglas como protocolo y rango de IP.
ufw status numbered
```

```shell
# Esto muestra todas las reglas con un numero asociado como identificador.
ufw status verbose
```

<br>

## Configuración Avanzada

### Permitir Rango de IP
```shell
# Esto permite solo conexiones de esa subred
ufw allow from 192.168.1.0/24
```

```shell
# Permitir solo acceso desde la subred 10.0.0.0/24
ufw allow from 10.0.0.0/24 to any port 22
```

### Denegar Rango de IP
```shell
# Denegar acceso a un rango de IPs
ufw deny from 192.168.1.100/24
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

<br>

## Más Recursos

Para más información, consulta la [documentación oficial de UFW](https://help.ubuntu.com/community/UFW).

---

**¡Gracias por consultar esta guía!**  
Si tienes sugerencias o encuentras errores, no dudes en contribuir o reportarlos.
