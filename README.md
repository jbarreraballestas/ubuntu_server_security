# Configurar la seguridad del servidor ubuntu

## Fail2ban

**Instalar fail2ban**
```
sudo apt install fail2ban -y
```

**Copiar archivo de configuración**
```
sudo cp /etc/fail2ban/jail.conf /etc/fail2ban/jail.local
```

**Editar archivo de configuración local**
```
sudo nano /etc/fail2ban/jail.local
```

> En el apartado [sshd] que queremos proteger podemos configurar de la siguiente manera

```
[sshd]
maxretry = 5
bantime = 10800
```

> Donde:
> 
> **maxretry** es el número de intentos andes de bloquear el acceso 
> 
> **bantime** el numero de segundos que durará bloqueada la dirección ip
> 
> En nuestro ejemplo 10800 segundos = 180 minutos = 3 horas
> 
> Use **bantime = -1** si desea bloquear permanente 
>
> -1 = Permanente
>
> 1m = 1 minuto
>
> 1h = 1 hora
>
> 1d = 1 dia

**Reiniciar fail2ban**
```
sudo systemctl restart fail2ban
```

**Ver el estado y las jaulas**
```
sudo fail2ban-client status
```

**Ver el estado de una jaula**
```
sudo fail2ban-client status sshd
```

**Ver si la ip 192.168.1.111 se encuentra bloqueada**
```
sudo iptables -n -L | grep 192.168.1.111
```

**Desbloquear una ip 192.168.1.111**
```
sudo fail2ban-client set sshd unbanip 192.168.1.111
```
Documentación configuración en inglés [jail.conf](https://github.com/fail2ban/fail2ban/blob/master/config/jail.conf)
