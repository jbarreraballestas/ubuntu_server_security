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
