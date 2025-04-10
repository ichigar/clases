# Usando PHP para acceder a JSON

## ¿Qué es PHP?

PHP es un lenguaje de programación del lado del servidor que se usa principalmente para crear páginas web dinámicas.
A diferencia del HTML, que solo muestra contenido, PHP piensa y decide qué mostrar antes de enviar el HTML al navegador.

## Utilización

### Introducción

Podemos mezclar código PHP con HTML para ello hemos de tener en cuenta que hemos de cambiar la extensión del archivo de `.hmtl` a `.php` , y su código va entre estas etiquetas:

```php
<?php
  // Código PHP aquí
?>
```

### Mostrando PHP

Para mostrar información generada en PHP dentro del HTML utilizamos la instrucción `echo`

```php
<h1>Saludando con PHP</h1>
<?php
  echo "¡Hola mundo!";
?>
```

De forma más abreviada:

```php
<h1>Saludando con PHP</h1>
<?= "¡Hola mundo!" ?>
```

### PHP es dinámico

El resultado del PHP se genera en el momento de invocar la página en el navegador. El interprete de PHP en el servidor ejecuta el código, lo inserta en el HTML  en el punto en que es invocado y lo envía al cliente que lo visualiza en el navegador:

```php
<h1>Bienvenido</h1>
<p>Hoy es <?php echo date("d/m/Y"); ?></p>
```

Este ejemplo muestra la fecha actual automáticamente. El navegador recibe solo HTML, pero PHP genera ese HTML de forma dinámica antes.

## Las variables

Imagina que estás trabajando con una hoja de papel. En ella puedes **anotar cosas** para usarlas más tarde: un nombre, un número, una ciudad…

En programación, eso mismo se hace con algo llamado **variable**.

**Una variable es un lugar donde guardamos información temporalmente para poder usarla más adelante.**


### Ejemplo cotidiano

Piensa en una etiqueta que pones sobre un frasco:

- En la etiqueta escribes: **"nombre"**
- Dentro del frasco pones un papel en el que está escrito: **"Carlos"**

Más tarde, cuando necesites el nombre, **vas al frasco que dice "nombre"** y sacas lo que hay dentro: `"Carlos"`.


### variables en PHP

El ejemplo anterior, en PHP lo hacemos de la siguiente forma:
```php
<?php
$nombre = "Carlos";
echo "Hola, $nombre";
?>
```

- `$nombre` es la **variable**. El nombre de la cajita.
- `"Carlos"` es el valor que guardamos.
- `echo` es como decir: "muéstrame esto en pantalla".
- Al usar `echo "Hola, $nombre"`, PHP mostrará: `Hola, Carlos`

A tener en cuenta:

- `$` - Todas las variables empiezan con `$` en PHP.
- `=` - Se usa para **guardar un valor** en la variable. 
- `echo` - Se usa para **mostrar información** al usuario.



### Ejemplo completo con HTML

```php
<!DOCTYPE html>
<html>
<body>

<?php
$nombre = "Ana";
$edad = 28;
$ciudad = "Sevilla";

echo "<h1>Perfil</h1>";
echo "<p>Nombre: $nombre</p>";
echo "<p>Edad: $edad años</p>";
echo "<p>Ciudad: $ciudad</p>";
?>

</body>
</html>
```

PHP guarda la información y la usa para **rellenar la página automáticamente**.

## Las funciones

Una **función** es como una **herramienta ya hecha** que puedes usar para que el lenguaje de programación haga algo por ti. En lugar de escribir todas las instrucciones paso a paso, usas una palabra clave, y PHP ya sabe qué hacer.


### Parametros de las funciones

Un **parámetro** es la **información que le das a la función** para que pueda hacer su trabajo.

> Piensa en una función como una máquina de café, y el parámetro como el tipo de café que le pides:  
> **cafe("cortado")**, **cafe("solo")**, **cafe("con leche")**.

### Utilización

1. Escribes el **nombre de la función**.
2. Le pasas **entre paréntesis** el valor o valores que quieres que use.
3. PHP hace el trabajo y te devuelve el resultado.

### Ejemplos de funciones de PHP

### `strlen()`  
Te dice cuántas letras (caracteres) tiene un texto.

```php
echo strlen("Hola"); // Resultado: 4
```

- `"Hola"` es el parámetro que le pasas a `strlen()`  
- PHP cuenta los caracteres y te devuelve el número.


### `strtoupper()`  
Convierte un texto en mayúsculas.

```php
echo strtoupper("bienvenido"); // Resultado: BIENVENIDO
```

- `"bienvenido"` es el parámetro.  
- La función lo convierte todo a mayúsculas.

### 🧮 `rand()`  
Genera un número aleatorio.

```php
echo rand(1, 10); // Resultado: un número entre 1 y 10
```

## Usando PHP para mostrar json simple

```php
<?php

$json = '{
  "nombre": "Lecturas del Atlántico",
  "ciudad": "Las Palmas",
  "telefono": "928123456",
  "email": "info@lecturasatlantico.com",
  "fundada": 1998
}';

// Decodificar como objeto
$data = json_decode($json);
?>

<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <title><?= $data->nombre ?></title>
</head>
<body>
  <!-- Mostrar el objeto JSON formateado -->
  <h2>Contenido del JSON:</h2>
  <pre><?= json_encode($data, JSON_PRETTY_PRINT | JSON_UNESCAPED_UNICODE) ?></pre>
  
  <h1><?= $data->nombre ?></h1>
  <p><strong>Ciudad:</strong> <?= $data->ciudad ?></p>
  <p><strong>Teléfono:</strong> <?= $data->telefono ?></p>
  <p><strong>Email:</strong> <?= $data->email ?></p>
  <p><strong>Año de fundación:</strong> <?= $data->fundada ?></p>
</body>
</html>
```

## Mostrando json con arrays

```php
<?php
$json = '{
  "nombre": "Lecturas del Atlántico",
  "ciudad": "Las Palmas",
  "telefono": "928123456",
  "email": "info@lecturasatlantico.com",
  "fundada": 1998,
  "categorias": ["Ficción", "Tecnología", "Cómics", "Infantil"]
}';

// Decodificar a objeto
$data = json_decode($json);

// Modificar el email
$data->email = "contacto@nuevodominio.com";
?>

<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <title><?= $data->nombre ?></title>
</head>
<body>

  <h2>Contenido completo del objeto JSON:</h2>
  <pre><?= json_encode($data, JSON_PRETTY_PRINT | JSON_UNESCAPED_UNICODE) ?></pre>

  <h1><?= $data->nombre ?></h1>
  <p><strong>Ciudad:</strong> <?= $data->ciudad ?></p>
  <p><strong>Teléfono:</strong> <?= $data->telefono ?></p>
  <p><strong>Email:</strong> <?= $data->email ?></p>
  <p><strong>Fundada en:</strong> <?= $data->fundada ?></p>

  <h3>Categorías:</h3>
  <ul>
    <?php foreach ($data->categorias as $categoria): ?>
      <li><?= $categoria ?></li>
    <?php endforeach; ?>
  </ul>

</body>
</html>

```

## Modificando elementos

```php
<?php
$json = '{
  "nombre": "Lecturas del Atlántico",
  "ciudad": "Las Palmas",
  "telefono": "928123456",
  "email": "info@lecturasatlantico.com",
  "fundada": 1998,
  "categorias": ["Ficción", "Tecnología", "Cómics", "Infantil"]
}';

// Decodificar a objeto
$data = json_decode($json);

// Modificar el email
$data->email = "contacto@nuevodominio.com";
$data->categorias[] = "Juvenil";
$data->categorias[1] = "Arte";

$json = json_encode($data)
?>
```
