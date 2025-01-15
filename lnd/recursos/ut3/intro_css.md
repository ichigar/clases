# Introducción a CSS

## 1. ¿Qué es css?

**CSS** son las siglas de **Cascading Style Sheets**, que en español significa **Hojas de Estilo en Cascada**.

- **Cascading (Cascada):**

  - El término "cascada" hace referencia a cómo se aplican las **reglas de estilo** a un elemtnto cuando hay múltiples definiciones que entran en conflicto.

- **Style (Estilo):**
  - Hace alusión a la capacidad de definir cómo se presenta un documento HTML. Esto incluye colores, fuentes, tamaños, márgenes, posición de los elementos, animaciones, etc.

3. **Sheets (Hojas):**
   - Las "hojas" (sheets) en CSS se refiere a que los estilos que usas para diseñar una página web están organizados en hojas de estilo. Estas hojas son **archivos que contienen las reglas y las instrucciones** sobre cómo deben verse los elementos de tu página. Esto permite la reutilización y organización del diseño en grandes proyectos.

## 2. Utilidad de css

La importancia de CSS radica en que se encarga de dar estilo y apariencia a las páginas web. HTML organiza y estructura el contenido, CSS lo hace atractivo y funcional para los usuarios.

Entre las ventajas que aporta tenemos:

- **Personalización del diseño**: permite cambiar colores, tipos de letra, tamaños, márgenes, bordes, posiciones, animaciones... Sin CSS, las páginas serían texto plano y simples bloques.
- **Separación entre contenido y diseño**: al seperar contenido de apariencia es más sencillo el mantenimiento y la organización del código.
- **Compatibilidad con múltiples dispositivos**: CSS permite crear diseños **responsive**, adaptados a diferentes tamaños de pantalla como móviles, tablets y ordenadores, asegurando una buena experiencia de usuario para la misma página en diferentes dispositivos.
- **Control sobre el diseño global del sitio**:con una única hoja de estilo puedes controlar el diseño de todas las páginas de un sitio web, asegurando uniformidad y reduciendo la necesidad de repetir código.
- **Mejora la velocidad de carga**: al usar un archivo CSS externo, el navegador solo necesita descargarlo una vez y puede reutilizarlo para todas las páginas del sitio, reduciendo el tiempo de carga.
- **Diseños dinámicos y atractivos**: CSS permite incluir transiciones, transformaciones y animaciones para hacer las páginas más interactivas y visualmente agradables.

## 3. Tipos de hojas de estilo en css

CSS permite definir los estilos de una página web de tres formas diferentes: **inline (en línea)**, **interna (en el documento HTML)** y **externa (en un archivo separado)**. Cada método tiene sus propias características, ventajas y desventajas.

### 3.1. **Hojas de estilo en línea (inline)**

En este caso, los estilos se aplican directamente dentro del **atributo** `style` en la etiqueta del elemento HTML.

#### Características:
- Solo afecta al elemento en el que se aplica.
- Útil para realizar cambios rápidos o específicos.
- Puede hacer el código difícil de mantener si se abusa de él.

#### Ejemplo:

```html
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <title>Hojas de estilo en línea</title>
</head>
<body>
  <h1 style="color: blue; text-align: center;">Título en azul y centrado</h1>
  <p style="font-size: 16px; color: gray;">Este párrafo tiene un estilo en línea.</p>
</body>
</html>
```

### 3.2. **Hojas de estilo internas (en el documento HTML)**

Se colocan en la sección `<head>` del documento HTML dentro de la etiqueta `<style>`. Los estilos definidos aquí aplican a toda la página.

#### Características:
- Adecuado para páginas pequeñas o casos donde el estilo no se comparte entre múltiples páginas.
- Es más organizado que usar estilos en línea, pero menos eficiente que un archivo externo.

#### Ejemplo:
```html
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <title>Hojas de estilo internas</title>
  <style>
    body {
      background-color: #f9f9f9;
    }
    h1 {
      color: darkblue;
      text-align: center;
    }
    p {
      font-size: 18px;
      color: gray;
    }
  </style>
</head>
<body>
  <h1>Ejemplo de hoja de estilo interna</h1>
  <p>Este párrafo tiene un estilo definido dentro de la etiqueta `<style>`.</p>
</body>
</html>
```

### 3.3. **Hojas de estilo externas**

Los estilos se colocan en un archivo separado con extensión `.css`. Este archivo se vincula al documento HTML mediante la etiqueta `<link>` en la sección `<head>`.

#### Características
- Es la forma más eficiente para proyectos grandes o cuando el estilo debe compartirse entre múltiples páginas.
- Permite separar completamente el contenido HTML del diseño.
- Facilita la reutilización y mantenimiento del código.

#### Ejemplo:

**Archivo CSS (`estilos.css`):**
```css
body {
  background-color: #e0f7fa;
}
h1 {
  color: teal;
  text-align: center;
}
p {
  font-size: 16px;
  color: darkgray;
}
```

**Archivo HTML:**

```html
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <title>Hojas de estilo externas</title>
  <link rel="stylesheet" href="estilos.css">
</head>
<body>
  <h1>Ejemplo de hoja de estilo externa</h1>
  <p>Este párrafo utiliza estilos definidos en un archivo CSS externo.</p>
</body>
</html>
```
#### Usar múltiples archivos CSS:

En proyectos más complejos, es común dividir el CSS en múltiples archivos para modularizar los estilos. Puedes enlazar múltiples archivos CSS incluyendo múltiples etiquetas <link>.

```HTML
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Mi Proyecto CSS</title>
    <link rel="stylesheet" href="css/reset.css">
    <link rel="stylesheet" href="css/layout.css">
    <link rel="stylesheet" href="css/styles.css">
</head>
<body>
    <h1>Hola, mundo!</h1>
</body>
</html>
```

### Comparación entre los tipos

| Tipo          | Ventajas                                                                 | Desventajas                                                             |
|---------------|--------------------------------------------------------------------------|--------------------------------------------------------------------------|
| **Inline**    | Fácil de usar para estilos rápidos o pruebas.                            | Dificultad para mantener y poco escalable.                              |
| **Interna**   | Buena para páginas pequeñas o donde los estilos no se reutilizan.        | No permite reutilización entre múltiples páginas.                       |
| **Externa**   | Reutilizable, fácil de mantener y separa diseño de contenido.            | Necesita una solicitud HTTP adicional para cargar el archivo (puede afectar la velocidad). |


### ¿Cuál elegir?

- **Inline:** Para ajustes rápidos y específicos o cuando no tienes acceso a los archivos CSS.
- **Interna:** Útil en páginas individuales o pequeños proyectos que no comparten estilos.
- **Externa:** La mejor opción para proyectos grandes o cuando deseas mantener estilos consistentes entre varias páginas.

## 4. Comentarios

Los comentarios en CSS son fragmentos de texto que los desarrolladores incluyen en el código para dar explicaciones o anotar ideas. Estos comentarios no son procesados ni ejecutados por el navegador, por lo que no afectan el diseño ni el comportamiento del sitio web.

Para escribir un comentario en CSS, se utiliza la siguiente sintaxis:

```css
/* Este es un comentario */
```
Empieza con `/*` y termina con `*/`.

El texto entre esos símbolos será ignorado por el navegador.

## 5. Reglas de declaración en css

Una **regla de declaración** en CSS es una unidad básica que **define** cómo se debe aplicar uno o varios estilos a un elemento HTML. La sintaxis de una declaración en CSS consta de los siguientes elementos:

* **Selector**: El selector identifica el(los) elemento(s) HTML al(los) que se aplicará la declaración de estilo. Entre **llaves** "{}" se incluirán las **declaraciones** que se aplicarán al selector:
* **Declaración**. Se compone, a su vez, de los elementos: 
  * **Propiedad**: La propiedad es el atributo de estilo que se desea modificar, como el color, el tamaño de fuente, el margen, etc
  * **": "** indica el final de la propiedad
  * **valor**: El valor es el ajuste que se le da a la propiedad, como por ejemplo, "red" para el color, "16px" para el tamaño de fuente, etc
  * **";"** indica el final de la declaración.

La sintaxis completa de una regla de declaración en CSS se ve de la siguiente manera:

```css
/* Regla de declaración */
selector {
  propiedad: valor;    /* declaración 1 */
  propiedad: valor;    /* declaración 2 */
  ...
}
```

Por ejemplo, la siguiente regla de declaración CSS establece el color de texto en rojo y el tamaño de fuente en 16 píxeles para todos los elementos `<p>`:

```css
p {
  color: red;
  font-size: 16px;
}
```

En este caso, p es el selector, color y font-size son las propiedades, y red y 16px son los valores asignados a esas propiedades.

## 6. Selectores

Como acabamos de ver, los **selectores** en CSS son la parte de las reglas css en la que indicamos a **qué elementos HTML queremos aplicar un estilo determinado**. Identifica uno o varios elementos en la página web para aplicarles un conjunto de estilos. Existen varios tipos de selectores.

Los tipos de selectores más comunes son:

### 6.1. Selector de tipo (Type Selector)

* Selecciona elementos según la etiqueta HTML.
* Ejemplo:

```HTML
<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<title>Selector de tipo</title>
<style>
  h1 {
    color: red; /*Todos los títulos <h1> serán rojos */
}
  p {
    font-size: 16px; /* Todos los párrafos <p> tendrán tamaño de 16px */
}
</style>
</head>
<body>
  <h1>Este es un título</h1>
  <p>Este es un párrafo con tamaño de texto 16px.</p>
  <p>Otro párrafo con el mismo tamaño de texto.</p>
</body>
</html>
```


### 6.2. Selector de clase (Class Selector)

#### El atributo class

El atributo class en HTML se utiliza para asignar una o más clases a un elemento. Estas clases permiten identificar y agrupar elementos de la página, facilitando aplicar estilos al mismo con CSS.

La sintaxis básica es:

```HTML
<tag class="nombre-clase">Contenido</tag>
```

* `tag`: Es la etiqueta HTML donde se aplica la clase (como div, p, h1, etc.).
* `class`: Es el nombre del atributo.
* `nombre-clase`: Es el nombre que defines para la clase. Puedes asignar más de una clase separándolas por espacios.

#### Selector class

El selector de clase especifica elementos con una clase específica (definida con el atributo `class` en una etiqueta HTML):

*  Usa el punto `.` antes del nombre de la clase.
*  Ejemplo:

```HTML
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <title>Selector de clase</title>
  <style>
      .destacado {
        background-color: yellow; /* Los elementos con la clase 'destacado' tendrán fondo amarillo */
      }
  </style>
</head>
<body>
  <p class="destacado">Este párrafo está destacado.</p>
  <p>Este párrafo no tiene clase aplicada.</p>
</body>
</html>
```

### 6.4. Selector de ID (ID Selector)

- Selecciona un único elemento con un identificador único (`id`) en HTML.
- Usa el símbolo `#` antes del nombre del ID.
- Ejemplo:
```HTML
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <title>Selector de ID</title>
  <style>  
    #encabezado {
    text-align: center; /* El elemento con id 'encabezado' estará centrado */
  }
<body>
  <h1 id="encabezado">Este es el título principal</h1>
  <h2>Este título no tiene estilos aplicados</h2>
</body>
</html>
```

### 6.5. Selector universal (Universal Selector)

- Selecciona **todos los elementos** de la página.
- Usa el símbolo `*`.
- Ejemplo:

```HTML
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <title>Selector universal</title>
  <style>    
    * {
      margin: 0; /* Elimina los márgenes de todos los elementos */
      padding: 0; /* Elimina el relleno de todos los elementos */
    }
  </style>
</head>
<body>
  <h1>Título sin márgenes</h1>
  <p>Este párrafo también carece de márgenes y rellenos.</p>
</body>
</html>
```

### 6.6. Selector de atributo (Attribute Selector)

- Selecciona elementos según un atributo HTML específico.
- Ejemplo:
```HTML
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <title>Selector de atributo</title>
  <style>
    input[type="text"] {
      border: 1px solid gray; /* Aplica a todos los campos <input> con tipo 'text' */
      padding: 5px;  /* Espaciado interno */
    }
  </style>
</head>
<body>
  <form>
    <label for="nombre">Nombre:</label>
    <input type="text" id="nombre" name="nombre">
    <br>
    <label for="edad">Edad:</label>
    <input type="number" id="edad" name="edad">
  </form>
</body>
</html>
```

### 6.7 Selectores combinados (Combinators)
- Permiten seleccionar elementos basados en su **relación** con otros elementos.
- Ejemplos:
  - **Selector descendente (` `):** Selecciona elementos dentro de otro. Los elementos se especifican separados por espacios.

```HTML
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <title>Selector descendente</title>
  <style>
    div p {
      color: blue; /* Selecciona todos los <p> dentro de un <div> */
    }
  </style>
</head>
<body>
  <div>
    <p>Este párrafo está dentro de un div y será azul.</p>
  </div>
  <p>Este párrafo no está en un div, no será afectado.</p>
</body>
</html>
```
- **Selector hijo directo (`>`):**
  Selecciona solo los hijos inmediatos.

```HTML
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <title>Selector hijo directo</title>
  <style>
    div > p {
      font-size: 18px;  /* Afecta solo a los <p> que son hijos directos de <div> */
    }
  </style>
</head>
<body>
  <div>
    <p>Este párrafo es hijo directo de un div y será afectado.</p>
    <section>
      <p>Este párrafo no es hijo directo del div, no será afectado.</p>
    </section>
  </div>
</body>
</html>
```

## 7. Especificidad

La **especificidad** en CSS es una regla que determina qué estilo se aplica a un elemento cuando hay **conflictos** entre múltiples reglas que lo afectan. En otras palabras, es una forma de decidir **cuál estilo tiene prioridad** sobre otro.

La especificidad depende de los **selectores utilizados** en las reglas de CSS. Mientras más específico sea un selector, mayor será su peso, y por lo tanto, tendrá prioridad sobre los estilos menos específicos.

### Cálculo de la especificidad

La especificidad se calcula como una **puntación numérica**, representada como tres valores separados (A-B-C), que dependen del tipo de selectores usados:

1. **A**: Número de selectores de ID (`#id`).
2. **B**: Número de selectores de clase (`.clase`) y atributos (`[atributo]`).
3. **C**: Número de selectores de tipo (`div`, `h1`, `p`) .

### Reglas de cálculo de especificidad

1. Si hay conflictos, se aplica la regla con mayor especificidad.
2. Si tienen la misma especificidad, se aplica la que aparece más al final en el código CSS.
3. Las reglas **inline** (en línea) tienen la mayor prioridad.
4. La regla `!important` tiene prioridad sobre cualquier otra regla (aunque debe usarse con cuidado).

### Ejemplos de cálculo de especificidad

1. **Selector de tipo** (C):
   ```css
   p {
     color: red;
   }
   ```
   Especificidad: **0-0-1**

2. **Selector de clase** (B):
   ```css
   .texto {
     color: blue;
   }
   ```
   Especificidad: **0-1-0**

3. **Selector de ID** (A):
   ```css
   #principal {
     color: green;
   }
   ```
   Especificidad: **1-0-0**

4. **Combinar selectores**:
   ```css
   div#principal .texto {
     color: orange;
   }
   ```
   Especificidad:
   - `#principal`: **1-0-0**
   - `.texto`:     **0-1-0**
   - `div`:        **0-0-1**
   **Total:**      **1-1-1**


### Ejemplo práctico

```html
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <title>Especificidad en CSS</title>
  <style>
    p {
      color: red; /* Especificidad: 0-0-1 */
    }
    .texto {
      color: blue; /* Especificidad: 0-1-0 */
    }
    #especial {
      color: green; /* Especificidad: 1-0-0 */
    }
    p.texto {
      color: purple; /* Especificidad: 0-1-1 */
    }
  </style>
</head>
<body>
  <p>Este texto será rojo (regla más general).</p>
  <p class="texto">Este texto será azul (clase tiene prioridad sobre tipo).</p>
  <p id="especial" class="texto">Este texto será verde (ID tiene la mayor prioridad).</p>
  <p id="especial" class="texto" style="color: orange;">Este texto será naranja (estilo inline tiene prioridad).</p>
</body>
</html>
```

### Especificidad con `!important`

La declaración `!important` se usa para forzar que una regla tenga prioridad sobre cualquier otra, independientemente de la especificidad.

**Ejemplo:**
```css
p {
  color: red !important; /* Prioridad absoluta */
}
```

Incluso si hay una regla con mayor especificidad o un estilo en línea, `!important` prevalecerá.

#### **Nota:** 
Usar `!important` puede dificultar el mantenimiento del código, por lo que debe emplearse con moderación.


### Consejos para gestionar la especificidad

1. **Usa selectores simples** siempre que sea posible.
2. **Evita el uso excesivo de selectores ID.** Prefiere las clases para mantener el código más flexible.
3. **Minimiza el uso de `!important`**, ya que puede complicar la depuración de estilos.
4. **Ordena las reglas en CSS de manera lógica**, desde lo más general a lo más específico.

## 8. Propiedades

En CSS, una **propiedad** es el aspecto del estilo que deseas modificar de un elemento HTML. Como hemos visto, cada propiedad se acompaña de un **valor** que define el ajuste específico para ese aspecto. Las propiedades pueden afectar diversos aspectos de los elementos, como el **color**, **tamaño**, **espaciado**, **fuentes**, **alineación**, etc.


### 8.1. Propiedades comunes en CSS

1. **`color`**: Define el color del texto.
   ```css
   p {
     color: blue; /* El texto será azul */
   }
   ```

2. **`font-size`**: Establece el tamaño de la fuente.
   ```css
   h1 {
     font-size: 24px; /* El tamaño de la fuente será de 24 píxeles */
   }
   ```

3. **`background-color`**: Establece el color de fondo de un elemento.
   ```css
   div {
     background-color: yellow; /* El fondo será amarillo */
   }
   ```

4. **`margin`**: Controla el espacio exterior alrededor de un elemento.
   ```css
   div {
     margin: 20px; /* Hay un espacio de 20 píxeles alrededor del div */
   }
   ```

5. **`padding`**: Controla el espacio interior dentro de un elemento.
   ```css
   div {
     padding: 10px; /* Hay un espacio de 10 píxeles dentro del div */
   }
   ```

6. **`border`**: Define un borde alrededor de un elemento.
   ```css
   div {
     border: 2px solid black; /* Borde de 2 píxeles, estilo de línea continuo y color negro */
   }
   ```

7. **`width`** y **`height`**: Establecen el tamaño de un elemento.
   ```css
   div {
     width: 300px; /* El ancho será de 300 píxeles */
     height: 200px; /* La altura será de 200 píxeles */
   }
   ```

8. **`text-align`**: Controla la alineación del texto dentro de un elemento.
   ```css
   h1 {
     text-align: center; /* El texto será centrado */
   }
   ```

9. **`font-family`**: Define la fuente que se utilizará en un elemento.
   ```css
   p {
     font-family: Arial, sans-serif; /* La fuente será Arial, o sans-serif si no está disponible */
   }
   ```

10. **`display`**: Controla cómo se muestra un elemento en la página.
    ```css
    div {
      display: block; /* El elemento se comporta como un bloque */
    }
    ```


### 8.2. Propiedades de estilo de texto y fuente

1. **`font-weight`**: Establece el grosor de la fuente.
   ```css
   p {
     font-weight: bold; /* El texto será en negrita */
   }
   ```

2. **`font-style`**: Define el estilo de la fuente (normal, cursiva, etc.).
   ```css
   p {
     font-style: italic; /* El texto será en cursiva */
   }
   ```

3. **`line-height`**: Define la altura de las líneas de texto.
   ```css
   p {
     line-height: 1.5; /* La altura de las líneas será 1.5 veces el tamaño de la fuente */
   }
   ```

4. **`text-decoration`**: Añade decoraciones al texto, como subrayado, tachado, etc.
   ```css
   a {
     text-decoration: underline; /* El enlace tendrá subrayado */
   }
   ```


### 8.3. Propiedades relacionadas con los colores y fondos

1. **`color`**: Define el color del texto.
   ```css
   p {
     color: #333333; /* El texto será de color gris oscuro */
   }
   ```

2. **`background-image`**: Define una imagen de fondo.
   ```css
   body {
     background-image: url('fondo.jpg'); /* Se establece una imagen de fondo */
   }
   ```

3. **`opacity`**: Controla la opacidad de un elemento (transparencia).
   ```css
   div {
     opacity: 0.5; /* El elemento será semi-transparente */
   }
   ```


### Ejemplo práctico con varias propiedades

```html
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <title>Propiedades en CSS</title>
  <style>
    body {
      background-color: #f0f0f0;
      font-family: Arial, sans-serif;
    }
    h1 {
      color: #003366;
      text-align: center;
    }
    p {
      font-size: 18px;
      color: #555555;
      line-height: 1.6;
      margin: 20px;
    }
    .caja {
      background-color: #ffffff;
      border: 1px solid #ccc;
      padding: 20px;
      width: 300px;
      height: 200px;
      margin: auto;
    }
  </style>
</head>
<body>
  <h1>Estilos con propiedades CSS</h1>
  <div class="caja">
    <p>Este es un párrafo dentro de una caja con estilo. El texto tiene un tamaño de 18px y un interlineado de 1.6.</p>
  </div>
</body>
</html>
```