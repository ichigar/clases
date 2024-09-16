# Cambiar el nombre del equipo en Ubuntu

Para cambiar el nombre del equipo (hostname) en Ubuntu Server debemos seguir los siguientes pasos

#### 1) Modificar el archivo `/etc/hostname`:
Este archivo contiene el nombre del equipo. Para cambiarlo, abre el archivo con un editor de texto como `nano`:

```bash
sudo nano /etc/hostname
```

En este archivo verás el nombre actual del equipo. Cámbialo por el nuevo nombre y guarda el archivo (`Ctrl+O` para guardar, `Ctrl+X` para salir).

#### 2) Actualizar el archivo `/etc/hosts`:
Este archivo mapea el hostname a la dirección `localhost` (127.0.0.1). Abre el archivo `/etc/hosts` con `nano`:

```bash
sudo nano /etc/hosts
```

Busca una línea similar a esta:

```
127.0.1.1   nombre-antiguo
```

Cambia `nombre-antiguo` por el nuevo nombre de tu equipo:

```
127.0.1.1   nuevo-nombre
```

Guarda y cierra el archivo.

### 3. Reiniciar el equipo:
Para aplicar los cambios de forma definitiva, reinicia el sistema:

```bash
sudo reboot
```

### Verificación:
Después de reiniciar, puedes verificar que el cambio fue exitoso ejecutando:

```bash
hostnamectl
```

El nuevo nombre debería aparecer reflejado en la salida. Además aparecerá también en el **prompt** del sistema
