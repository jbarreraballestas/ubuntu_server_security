# Configurar la seguridad del servidor ubuntu

## Fail2ban

**Instalar fail2ban**
```
sudo apt install fail2ban
```

**Verificar el estado y las jaulas**
```
sudo fail2ban-client status
```

**Copiar archivo de configuración**
```
sudo cp /etc/fail2ban/jail.conf /etc/fail2ban/jail.local
```

**Editar archivo de configuración local**
```
sudo nano /etc/fail2ban/jail.local
```

> En el apartado [sshd] o servicio que queremos proteger podemos configurar de la siguiente manera

```
[sshd]
maxretry = 5
bantime=10800
```

> Donde:
> **maxretry** es el número de intentos andes de bloquear el acceso 
> 
> **bantime** el numero de segundos que durará bloqueada la dirección ip
> 
> En nuestro ejemplo 10800 segundos = 180 minutos = 3 horas
