### Tutorial Paso a Paso: Cómo Agregar Contenido a un Sitio Web Usando HTML

#### Paso 1: Crea la Estructura HTML Básica
Para comenzar, crea un archivo HTML y define la estructura básica:

```html
<!DOCTYPE html>
<html>
<head>
    <title>PC Gaming de Alto Rendimiento</title>
</head>
<body>
    <!-- Todo el contenido de la página se coloca dentro del body -->
</body>
</html>
```
Donde:

* **`<html>`**:
   - **Descripción**: Esta etiqueta define el contenedor raíz de un documento HTML. Todo el contenido de la página debe estar dentro de esta etiqueta.
* **`<head>`**:
   - **Descripción**: Esta etiqueta contiene metadatos sobre el documento, como el título, enlaces a estilos externos, scripts, o meta información como la codificación de caracteres o la descripción de la página.
* **`<body>`**:
   - **Descripción**: Contiene todo el contenido visible de la página web (texto, imágenes, enlaces, etc.).
* **`<title>`** es parte del elemento `<head>` en un documento HTML y define el título de la página web. Este título es lo que aparece en la pestaña del navegador y también es el texto que los motores de búsqueda (como Google) muestran como título en los resultados de búsqueda
* **`<!-- -->` (Comentarios en HTML)**:
   - **Descripción**: Los comentarios son invisibles para los usuarios y no afectan el contenido de la página. Son útiles para anotar el código o desactivar partes de código sin eliminarlas.

#### Paso 2: Añade Títulos y Párrafos
Los títulos y párrafos son fundamentales para organizar el contenido.
- **Título Principal**: Agrega un título principal utilizando la etiqueta `<h1>`:
  ```html
  <h1>Componentes Clave de un PC Gaming</h1>
  ```
- **Párrafo**: Añade un párrafo de texto con la etiqueta `<p>`:
  ```html
  <p>Un PC gaming de alto rendimiento requiere componentes potentes como una tarjeta gráfica dedicada, un procesador rápido y suficiente memoria RAM.</p>
  ```
  Donde:

* **`<h1>`**:
   - **Descripción**: Define el encabezado más importante en una página. Este es el título principal del documento o de una sección y se recomienda que haya solo uno por página para mantener la accesibilidad.

* **`<h2>`**:
   - **Descripción**: Define un encabezado de segundo nivel. Se utiliza para sub-secciones dentro del contenido definido por el encabezado `<h1>`.
* **`<p>`**:
   - **Descripción**: Esta etiqueta se usa para definir un párrafo de texto.
   - **Atributos comunes**:
     - **align**: Define la alineación del texto dentro del párrafo. Los valores posibles son `left`, `right`, `center`, `justify`. Ejemplo: `<p align="center">Texto centrado</p>`.
     
**HTML hasta este punto:**
```html
<!DOCTYPE html>
<html>
<head>
    <title>PC Gaming de Alto Rendimiento</title>
</head>
<body>
    <h1>Componentes Clave de un PC Gaming</h1>
    <p>Un PC gaming de alto rendimiento requiere componentes potentes como una tarjeta gráfica dedicada, un procesador rápido y suficiente memoria RAM.</p>
</body>
</html>
```

#### Paso 3: Añadir Enlaces
Para enlazar otras páginas o sitios web, utiliza la etiqueta `<a>`.
- **Ejemplo de Enlace**:
  ```html
  <a href="https://www.example.com">Más información sobre tarjetas gráficas</a>
  ```
Donde:

* **`<a>`**:
   - **Descripción**: Crea un enlace a otra página web o recurso.
   - **Atributos comunes**:
     - **href**: Define la URL de destino del enlace. Ejemplo: `<a href="https://www.ejemplo.com">Texto del enlace</a>`.
     - **target**: Define dónde abrir el enlace. Ejemplo: `_blank` para abrir en una nueva pestaña o ventana. Ejemplo: `<a href="https://www.ejemplo.com" target="_blank">Abrir en nueva pestaña</a>`.
     - **title**: Muestra un texto adicional cuando el usuario pasa el cursor sobre el enlace.

**HTML hasta este punto:**
```html
<!DOCTYPE html>
<html>
<head>
    <title>PC Gaming de Alto Rendimiento</title>
</head>
<body>
    <h1>Componentes Clave de un PC Gaming</h1>
    <p>Un PC gaming de alto rendimiento requiere componentes potentes como una tarjeta gráfica dedicada, un procesador rápido y suficiente memoria RAM.</p>
    <a href="https://www.example.com">Más información sobre tarjetas gráficas</a>
</body>
</html>
```

#### Paso 4: Crear Listas
Las listas ayudan a organizar elementos de manera clara.
##### **Lista Ordenada (Numerada)**:
  ```html
  <ol>
      <li>Tarjeta gráfica potente</li>
      <li>Procesador de alto rendimiento</li>
      <li>Mínimo 16 GB de RAM</li>
  </ol>
  ```
Donde:

* **`<ol>`**:
    - **Descripción**: Define una lista ordenada, donde los elementos se enumeran con números o letras.
    - **Atributos comunes**:
      - **type**: Define el tipo de numeración, como `1` (números), `A` (letras mayúsculas), `a` (letras minúsculas), o `I` (números romanos). Ejemplo: `<ol type="A">`.
      - **start**: Define el número inicial de la lista. Ejemplo: `<ol start="5">` comienza la lista desde el número 5.

##### **Lista No Ordenada (Con Viñetas)**:
  ```html
  <ul>
      <li>Almacenamiento SSD</li>
      <li>Fuente de alimentación confiable</li>
      <li>Refrigeración adecuada</li>
  </ul>
  ```

Donde:

* **`<ul>`**:
    - **Descripción**: Define una lista no ordenada. Los elementos de la lista se muestran con viñetas o puntos.
    - **Atributos comunes**:
      - **type**: Define el tipo de viñeta. Puede ser `circle`, `disc`, o `square`. Ejemplo: `<ul type="square">`. 
* **`<li>`** 
  * **Descripción:** representa un elemento dentro de una lista, y su apariencia varía según el tipo de lista donde esté contenido:
En una lista no ordenada (`<ul>`), los elementos `<li>` aparecen con viñetas o puntos (o cualquier símbolo especificado con el atributo type en `<ul>`). En una lista ordenada (`<ol>`), los elementos `<li>` aparecen con números o letras, dependiendo del tipo de lista.

**HTML hasta este punto:**
```html
<!DOCTYPE html>
<html>
<head>
    <title>PC Gaming de Alto Rendimiento</title>
</head>
<body>
    <h1>Componentes Clave de un PC Gaming</h1>
    <p>Un PC gaming de alto rendimiento requiere componentes potentes como una tarjeta gráfica dedicada, un procesador rápido y suficiente memoria RAM.</p>
    <a href="https://www.example.com">Más información sobre tarjetas gráficas</a>
    <ol>
        <li>Tarjeta gráfica potente</li>
        <li>Procesador de alto rendimiento</li>
        <li>Mínimo 16 GB de RAM</li>
    </ol>
    <ul>
        <li>Almacenamiento SSD</li>
        <li>Fuente de alimentación confiable</li>
        <li>Refrigeración adecuada</li>
    </ul>
</body>
</html>
```

#### Paso 5: Añadir Imágenes
Para insertar imágenes en tu página web, utiliza la etiqueta `<img>`.
- **Ejemplo de Imagen Local**:
  ```html
  <img src="tarjeta-grafica.jpg" alt="Imagen de una tarjeta gráfica para gaming">
  ```

Donde:

* **`<img>`**:
   - **Descripción**: Se utiliza para insertar imágenes en una página web.
   - **Atributos comunes**:
     - **src**: Define la ubicación de la imagen. Ejemplo: `<img src="imagen.jpg" alt="Descripción de la imagen">`.
     - **alt**: Proporciona un texto alternativo que se muestra si la imagen no se puede cargar, o para accesibilidad.
     - **width** y **height**: Definen el ancho y alto de la imagen en píxeles. Ejemplo: `<img src="imagen.jpg" width="300" height="200">`.
     - **title**: Texto que aparece cuando el usuario pasa el cursor sobre la imagen.

**HTML hasta este punto:**

```html
<!DOCTYPE html>
<html>
<head>
    <title>PC Gaming de Alto Rendimiento</title>
</head>
<body>
    <h1>Componentes Clave de un PC Gaming</h1>
    <p>Un PC gaming de alto rendimiento requiere componentes potentes como una tarjeta gráfica dedicada, un procesador rápido y suficiente memoria RAM.</p>
    <a href="https://www.example.com">Más información sobre tarjetas gráficas</a>
    <ol>
        <li>Tarjeta gráfica potente</li>
        <li>Procesador de alto rendimiento</li>
        <li>Mínimo 16 GB de RAM</li>
    </ol>
    <ul>
        <li>Almacenamiento SSD</li>
        <li>Fuente de alimentación confiable</li>
        <li>Refrigeración adecuada</li>
    </ul>
    <img src="tarjeta-grafica.jpg" alt="Imagen de una tarjeta gráfica para gaming">
</body>
</html>
```

#### Paso 6: Configura la Codificación UTF-8
Para asegurarte de que los caracteres especiales se muestren correctamente, añade la configuración de codificación UTF-8 en la sección `<head>` de tu archivo HTML.
- **Ejemplo de Configuración UTF-8**:
  ```html
  <head>
      <meta charset="UTF-8">
      <title>PC Gaming de Alto Rendimiento</title>
  </head>
  ```

  Donde:

  * **`<meta charset="UTF-8">`**:
    * **meta**: La etiqueta `<meta>` se utiliza para proporcionar **metadatos** sobre el documento HTML, como la descripción, palabras clave, o, en este caso, la codificación de caracteres.
    * **charset**: Este atributo de la etiqueta `<meta>` define el **conjunto de caracteres** que se utilizará para interpretar el contenido de la página. Especifica cómo los caracteres del texto deben ser representados.
    * **UTF-8**: Es un estándar de codificación de caracteres ampliamente utilizado. UTF-8 puede representar todos los caracteres en el conjunto de caracteres Unicode, lo que lo convierte en una opción ideal para garantizar que se muestren correctamente todos los caracteres, incluidos los caracteres especiales, símbolos, y letras de diferentes idiomas.

Es importante usar `UTF-8` por:

- **Compatibilidad Internacional**: UTF-8 es capaz de manejar casi cualquier idioma, incluidos caracteres latinos, cirílicos, chinos, árabes, y más, lo que lo hace esencial para páginas web con contenido multilingüe.
- **Evitar errores de codificación**: Sin una declaración de codificación clara, los navegadores podrían interpretar incorrectamente los caracteres especiales (como acentos, ñ, o caracteres no latinos), lo que llevaría a la aparición de símbolos incorrectos o de codificación.
- **Estándar moderno**: UTF-8 es el estándar más común en la web hoy en día. Garantiza que tu sitio funcione correctamente en una variedad de navegadores y plataformas.

**HTML final:**
```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <title>PC Gaming de Alto Rendimiento</title>
</head>
<body>
    <h1>Componentes Clave de un PC Gaming</h1>
    <p>Un PC gaming de alto rendimiento requiere componentes potentes como una tarjeta gráfica dedicada, un procesador rápido y suficiente memoria RAM.</p>
    <a href="https://www.example.com">Más información sobre tarjetas gráficas</a>
    <ol>
        <li>Tarjeta gráfica potente</li>
        <li>Procesador de alto rendimiento</li>
        <li>Mínimo 16 GB de RAM</li>
    </ol>
    <ul>
        <li>Almacenamiento SSD</li>
        <li>Fuente de alimentación confiable</li>
        <li>Refrigeración adecuada</li>
    </ul>
    <img src="tarjeta-grafica.jpg" alt="Imagen de una tarjeta gráfica para gaming">
</body>
</html>
```


