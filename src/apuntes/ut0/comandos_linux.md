# COMANDOS LINUX PARA LA GESTIÓN DE ARCHIVOS Y DIRECTORIOS

Todo buen administrador de sistemas debería saber cómo crear, borrar, editar, asignar permisos, visualizar, copiar, mover y determinar el tipo de ficheros y programas.

## Trucos para trabajar con archivos en Linux

Como la mayoría de usuarios viene de usar normalmente Windows, es bueno recordar algunas características de Linux que nos pueden servir de ayuda:

- **Los ficheros ocultos no son realmente ocultos**: simplemente empiezan por un punto ".", como los ficheros `.bashrc` y `.bash_profile`. No son visibles para los usuarios normales desde el explorador de archivos `nautilus` o con comandos y opciones convencionales.
- **Los nombres de ficheros pueden contener más de un punto**: los ficheros `este.es.un.nombre.largo.de.fichero` y `esteesunnombrelargodefichero` son posibles en Linux.
- **Los espacios en los nombres de ficheros son bonitos, pero es difícil teclearlos**: Usa un `_` o un punto `.` en lugar de espacios porque es mucho más fácil escribirlos en la línea de comandos que tener que poner `\` por cada espacio.
- **Los ficheros no están obligados a incluir una extensión**, pero son útiles para comandos de ordenar, seleccionar y copiar/mover/borrar. Además, permiten identificar rápidamente el tipo de contenido.

## Navegando por la jerarquía de directorios

Antes de poder movernos por la jerarquía de directorios, deberíamos saber cuál es la carpeta actual. Para ello, tenemos el comando `pwd`.

### pwd

**Propósito**: Mostrar la ruta del directorio de trabajo actual.

**Sintaxis**: 
```bash
pwd
```

**Opciones**: Ninguna

**Descripción**: El comando `pwd` imprime el directorio de trabajo (aquel en el que actualmente se está trabajando).

**Nota**: 
Cada vez que abrimos un terminal se nos muestra el prompt del sistema:

```bash
usuario@a1pc00:~/documentos/musica$
```

- El nombre a la izquierda de la `@`, `usuario` en este caso, es el nombre del usuario.
- El nombre entre la `@` y los dos puntos `:` es el nombre del equipo.
- Luego aparece el directorio actual: `~/documentos/musica`, que equivale a `/home/usuario/documentos/musica`.
- Por último, el símbolo `$` indica que es un usuario restringido. Si fuese `root`, aparecería `#`.

### cd

**Propósito**: El comando `cd` se usa para movernos por la jerarquía de directorios.

**Sintaxis**: 
```bash
cd [directorio]
```

`directorio` es la ruta absoluta o relativa al directorio al que queremos acceder.

**Nota**: Los corchetes `[ ]` no se escriben, indican que el parámetro es opcional.

**Opciones**: Ninguna

**Descripción**: Si escribimos `cd` sin argumentos, se cambiará al directorio `home` del usuario. En otro caso, se moverá al directorio indicado.

**Ejemplo**:
```bash
usuario@a1pc00:~/Descargas$ cd
usuario@a1pc00:~$ pwd
/home/usuario
```

Veamos algunos ejemplos:
```bash
usuario@a1pc00:~$ tree
.
├── Descargas
├── documentos
│   ├── apuntes
│   ├── examenes
│   ├── musica
│   └── videos
└── temp
usuario@a1pc00:~$ cd documentos/apuntes
usuario@a1pc00:~/documentos/apuntes$ cd ../musica
usuario@a1pc00:~/documentos/musica$ cd ../../temp
usuario@a1pc00:~/temp$ cd /home/usuario/Descargas/
usuario@a1pc00:~/Descargas$ cd ~
usuario@a1pc00:~$ cd documentos/musica
usuario@a1pc00:~/documentos/musica$ cd $HOME
```

- Las rutas pueden ser absolutas y relativas.
- `~` equivale a la ruta al directorio `home` del usuario.
- `$HOME` es una variable que guarda la carpeta `home`.

**Nota**: 
El comando `tree` muestra la jerarquía de directorios. Si no tiene parámetros, la muestra desde el directorio actual.

Para instalar `tree` ejecutamos:
```bash
$ sudo apt-get install tree
```

## Listando ficheros y directorios

### ls

**Propósito**: Listar directorios, archivos o ambos.

**Sintaxis**: 
```bash
ls [Opciones] [nombre_directorio o archivo]
```

**Opciones**: 
- `-a` muestra todos los archivos, incluyendo ocultos.
- `-c` ordena por fecha de creación.
- `-d` muestra directorios como archivos.
- `-i` muestra información de i-node.
- `-l` lista en formato largo con detalles.
- `-lh` lista en formato largo con tamaños legibles.

**Descripción**: El comando `ls` muestra el contenido de un directorio. Si se omite el nombre, muestra el contenido del directorio actual.

**Ejemplo**:
```bash
usuario@a1pc00:~/temp$ ls
00063821.pdf capturas CMS.jpg Deuda.pdf dist dokuwiki-logo.jpeg drupal.jpeg ejemplo01.html EL_CIELO_DESDE_LA_PALMA.pps esquema_web_dinamico.png
```

Listando en formato largo:
```bash
usuario@a1pc00:~$ ls -lha temp/
total 60M
drwxr-xr-x  7 usuario usuario 4,0K 2011-10-26 23:10 .
-rw-r--r--  1 usuario usuario  11K 2011-10-26 23:01 00063821.pdf
```

## Creando ficheros

### touch

**Propósito**: Crea un fichero vacío o actualiza su fecha si existe.

**Sintaxis**: 
```bash
touch [archivo]
```

**Ejemplo**:
```bash
usuario@a1pc00:~$ touch documentos/apuntes/tema1.txt
usuario@a1pc00:~$ ls -lh documentos/apuntes/
total 0
-rw-r--r-- 1 usuario usuario 0 2011-10-26 23:23 tema1.txt
```

Ejecutamos `touch` en un archivo existente:
```bash
usuario@a1pc00:~/prueba$ touch examples.desktop
usuario@a1pc00:~$ ls -la
-rw-r--r-- 1 usuario usuario  179 2011-10-26 23:15 examples.desktop
```

## Copiando ficheros y directorios

### cp

**Propósito**: Copiar archivos y directorios.

**Sintaxis**: 
```bash
cp [Opciones] archivo_fuente archivo_destino
```

**Opciones**:
- `-a` conserva todos los atributos.
- `-r` copia archivos y subdirectorios.

**Ejemplo**:
```bash
usuario@a1pc00:~$ cp -r documentos prueba
usuario@a1pc00:~$ tree prueba
prueba └── documentos ├── apuntes └── tema1.txt
```

**Nota**: 
```bash
cp documentos/apuntes/tema1.txt .
```
En lugar de la ruta absoluta, usamos `.` para indicar el directorio actual.

## Moviendo objetos

### mv

**Propósito**: Mueve o renombra archivos y directorios.

**Sintaxis**: 
```bash
mv [Opciones] fuente destino
```

**Ejemplo**: 
```bash
usuario@a1pc00:~/documentos/apuntes$ mv tema2.txt apuntes_tema2.txt
```

## Creando y borrando directorios

### mkdir

**Propósito**: Crear directorios.

**Sintaxis**: 
```bash
mkdir [Opciones] directorio
```

**Ejemplo**:
```bash
usuario@a1pc00:~/temp$ mkdir dirx
usuario@a1pc00:~/temp$ ls
dirx
```

Crear jerarquía de directorios:
```bash
usuario@a1pc00:~/temp$ mkdir -p dir1/dir2/dir3
usuario@a1pc00:~/temp$ tree
.
├── dir1
│   └── dir2
│       └── dir3
└── dirx
```

### rmdir

**Propósito**: Borrar directorios.

**Sintaxis**: 
```bash
rmdir [Opciones] directorio
```

**Ejemplo**: 
```bash
usuario@a1pc00:~/temp$ rmdir dirx
```

## Eliminando objetos

### rm

**Propósito**: Elimina archivos y directorios.

**Sintaxis**: 
```bash
rm [Opciones] archivos
```

**Ejemplo**: 
```bash
usuario@a1pc00:~$ rm examples.desktop
```

