# Configuración de Ubuntu como Router con NAT

Este tutorial describe cómo configurar un equipo Ubuntu con dos tarjetas de red (NICs) para que funcione como un router con NAT activado, permitiendo que los dispositivos en la red interna accedan a Internet a través de la interfaz externa.

## Requisitos previos

1. **Equipo Ubuntu** con dos tarjetas de red:
   - **NIC1**: Conectada a la red externa (por ejemplo, a un módem o router que accede a Internet).
   - **NIC2**: Conectada a la red interna (para proporcionar conectividad a los dispositivos locales).
   - Tarjetas de red configuradas correctamente con netplan.
   
2. **Privilegios de superusuario (root)** o capacidad para ejecutar comandos con `sudo`.


## 1. Habilitar el reenvío de paquetes IP

Debes habilitar el reenvío de paquetes para que Ubuntu pueda actuar como router. Edita el archivo `sysctl.conf`:

```bash
sudo nano /etc/sysctl.conf
```

Descomenta o añade la siguiente línea:

```bash
net.ipv4.ip_forward = 1
```

Aplica los cambios:

```bash
sudo sysctl -p
```

## 2. Configurar NAT usando `iptables`

Configura `iptables` para realizar la traducción de direcciones de red (NAT) en la interfaz externa (`enp3s0`):

```bash
sudo iptables -t nat -A POSTROUTING -o enp0s3 -j MASQUERADE
```

Permitir el reenvío de tráfico desde la red interna hacia la externa:

```bash
sudo iptables -A FORWARD -i enp0s8 -o enp0s3 -j ACCEPT
sudo iptables -A FORWARD -i enp0s8 -o enp0s3 -m state --state RELATED,ESTABLISHED -j ACCEPT
```

## 3. Guardar las reglas de `iptables`

Para que las reglas de `iptables` se apliquen tras reiniciar el sistema, instala el paquete `iptables-persistent`:

```bash
sudo apt install iptables-persistent
```

Durante la instalación, selecciona "Sí" para guardar las reglas actuales.

Si ya tienes instalado el paquete, puedes guardar las reglas manualmente ejecutando:

```bash
sudo netfilter-persistent save
```

Si nos hemos equivocado o queremos modificar las reglas podemos hacerlo editando el fichero en el que se almacenan:

```bash
sudo nano /etc/iptables/rules.v4
```
Para que se apliquen las reglas del fichero ejecutamos:

```bash
sudo iptables-restore < /etc/iptables/rules.v4
```

## 4. Verificar la conectividad

Una vez completada la configuración, conecta dispositivos a la interfaz interna (`enp0s8`) y asegúrate de que pueden acceder a Internet:

```bash
$ ping -c 4 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=110 time=40.7 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=110 time=40.8 ms
64 bytes from 8.8.8.8: icmp_seq=3 ttl=110 time=40.0 ms
64 bytes from 8.8.8.8: icmp_seq=4 ttl=110 time=40.7 ms

--- 8.8.8.8 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 2997ms
rtt min/avg/max/mdev = 40.007/40.558/40.824/0.322 ms

$ ping -c 4 rediris.es
PING rediris.es (130.206.13.20) 56(84) bytes of data.
64 bytes from www.rediris.es (130.206.13.20): icmp_seq=1 ttl=51 time=37.1 ms
64 bytes from www.rediris.es (130.206.13.20): icmp_seq=2 ttl=51 time=37.3 ms
64 bytes from www.rediris.es (130.206.13.20): icmp_seq=3 ttl=51 time=38.1 ms
64 bytes from www.rediris.es (130.206.13.20): icmp_seq=4 ttl=51 time=37.8 ms

--- rediris.es ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 2997ms
rtt min/avg/max/mdev = 37.141/37.586/38.093/0.381 ms
```


## 8. Solución de problemas

Si los dispositivos internos no pueden acceder a Internet, verifica los siguientes aspectos:

1. Asegúrate de que el reenvío de IP esté activado:
   ```bash
   sudo sysctl net.ipv4.ip_forward
   ```
Deberías obtener:

```
net.ipv4.ip_forward = 1
```

2. Revisa las reglas de `iptables`:
```bash
sudo iptables -L -t nat
sudo iptables -L -v
```
Si queremos empezar desde cero y eliminar todas las reglas que hemos creado ejecutamos:
```bash
sudo iptables -F -t nat
sudo iptables -F
```

3. Verifica que las interfaces de red estén configuradas correctamente usando el comando `ip a`.




