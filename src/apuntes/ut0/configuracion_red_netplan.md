## Configuración de red con NETPLAN

### Configuración de la Red con Netplan en Ubuntu Server

Netplan es la herramienta de configuración de red utilizada en las versiones más recientes de Ubuntu Server (17.10 y posteriores). A continuación se describen los pasos básicos para configurar la red.

#### 1. **Ubicación de los Archivos de Configuración**

Los archivos de configuración de Netplan se encuentran en el directorio:

```
/etc/netplan/
```

Los archivos suelen tener una extensión `.yaml`. Puedes listar los archivos en este directorio con:

```bash
ls /etc/netplan/
```

#### 2. **Editar el Archivo de Configuración**

Abre el archivo de configuración con un editor de texto:

```bash
sudo nano /etc/netplan/50-cloud-init.yaml
```

#### 3. **Estructura del Archivo YAML**

La configuración de Netplan se define en formato YAML. A continuación se muestra un ejemplo básico de configuración para una interfaz de red estática:

```yaml
network:
  version: 2
  ethernets:
    ens33:
      dhcp4: no
      addresses:
        - 192.168.1.100/24
      gateway4: 192.168.1.1
      nameservers:
        addresses:
          - 8.8.8.8
          - 8.8.4.4
```

- **version**: Debe ser `2`.
- **ethernets**: Define las interfaces Ethernet.
- **ens33**: Es el nombre de la interfaz (puede variar, usa `ip a` para verificar el nombre).
- **dhcp4**: Establece si se debe usar DHCP (sí/no).
- **addresses**: Lista de direcciones IP estáticas.
- **gateway4**: Dirección IP del gateway.
- **nameservers**: Lista de servidores DNS.

#### 4. **Ejemplo de Configuración DHCP**

Si deseas configurar la interfaz para que obtenga su dirección IP automáticamente mediante DHCP, el archivo se vería así:

```yaml
network:
  version: 2
  ethernets:
    ens33:
      dhcp4: yes
```

#### 5. **Aplicar la Configuración**

Después de realizar los cambios, guarda el archivo y aplica la configuración con el siguiente comando:

```bash
sudo netplan apply
```

#### 6. **Verificar la Configuración**

Para verificar que la configuración se ha aplicado correctamente, puedes usar:

```bash
ip a
ip route
resolvectl status
```

Esto mostrará las direcciones IP asignadas a las interfaces de red, la puerta de enlace y los servidores de DNS.

#### 7. **Depuración de Problemas**

Si encuentras problemas, puedes usar el siguiente comando para obtener más información sobre la configuración de Netplan:

```bash
sudo netplan try
```

Este comando te permite probar la configuración antes de aplicarla permanentemente. Si hay un error, te dará la opción de revertir los cambios.

### Notas Adicionales

- Asegúrate de que la indentación en el archivo YAML sea correcta, ya que es sensible a espacios.
- Puedes tener múltiples archivos de configuración en `/etc/netplan/`, y Netplan los combinará.
- Para configuraciones más avanzadas, como VLANs o puentes, consulta la [documentación oficial de Netplan](https://netplan.io/).
