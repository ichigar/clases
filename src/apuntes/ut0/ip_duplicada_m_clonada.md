## Tutorial para solicionar problema Ip duplicada en MV clonadas
AL obtener IP por DHCP en MV de linux clonadas se suele dar el caso de que la máquina obtenga la misma IP que otras máquinas de la red.

Para solucionarlo debemos seguir los siguientes pasos:

1) Primero cambiamos el nombre al equipo. Las instrucciones las tenemos en el [siguiente tutorial](cambiar_nombre_equipo_ubuntu.md)
2) Eliminar o regenerar el archivo de cliente DHCP:

En Ubuntu, el archivo `/etc/machine-id` puede estar contribuyendo a este comportamiento. Para regenerarlo ejecuta:
```bash
sudo rm /etc/machine-id
sudo systemd-machine-id-setup
sudo reboot
```

Esto generará un nuevo identificador de máquina, lo que debería ayudar a que el servidor DHCP asigne una IP diferente.
