# Usando PHP para acceder a JSON

## ¿Qué es PHP?

PHP es un lenguaje de programación del lado del servidor que se usa principalmente para crear páginas web dinámicas.
A diferencia del HTML, que solo muestra contenido, PHP piensa y decide qué mostrar antes de enviar el HTML al navegador.

## Utilización

PHP se escribe dentro de archivos con extensión `.phpp , y su código va entre estas etiquetas:

```
<?php
  // Código PHP aquí
?>
```

Puede integrarse dentro de HTML como esto:

```php
<h1>Bienvenido</h1>
<p>Hoy es <?php echo date("d/m/Y"); ?></p>
```

Este ejemplo muestra la fecha actual automáticamente. El navegador recibe solo HTML, pero PHP genera ese HTML de forma dinámica antes.

## Mostrando json simple

```php
<?php
// JSON de un solo nivel
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
