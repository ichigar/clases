# Formularios en HTML

## Formulario de ejemplo

```html
<form action="https://webhook.site/723ffee6-5e54-434f-afdc-2fc4f4c1efc9" method="post">
    
    <fieldset>
        <legend>Información Básica</legend>
        <label for="nombreEquipo">Nombre del equipo:</label>
        <input type="text" id="nombreEquipo" name="nombreEquipo" required maxlength="100" placeholder="Nombre del equipo de gaming">
        <br><br>

        <label for="fechaRegistro">Fecha de registro:</label>
        <input type="date" id="fechaRegistro" name="fechaRegistro" required>
        <br><br>

        <label for="categoria">Categoría:</label>
        <select id="categoria" name="categoria" required>
            <option value="">Seleccione</option>
            <option value="FPS">FPS</option>
            <option value="MOBA">MOBA</option>
            <option value="RPG">RPG</option>
            <option value="Estrategia">Estrategia</option>
        </select>
        <br><br>

        <label for="emailContacto">Correo electrónico de contacto:</label>
        <input type="email" id="emailContacto" name="emailContacto" required placeholder="ejemplo@correo.com">
        <br><br>

        <label for="website">Sitio web del equipo:</label>
        <input type="url" id="website" name="website" placeholder="https://www.sitiodelteam.com">
    </fieldset>

    <fieldset>
        <legend>Integrantes</legend>
        <label for="numJugadores">Número de jugadores:</label>
        <input type="number" id="numJugadores" name="numJugadores" min="1" max="10" step="1" required>
        <br><br>

        <label for="capitan">¿Es capitán del equipo?</label>
        <input type="checkbox" id="capitan" name="capitan">
    </fieldset>


    <fieldset>
        <legend>Preferencias de Hardware</legend>
        <label for="procesador">Procesador preferido:</label>
        <input type="text" id="procesador" name="procesador" placeholder="Modelo del procesador">
        <br><br>

        <label for="teclado">Tipo de teclado:</label>
        <input type="radio" id="mecanico" name="teclado" value="Mecánico">
        <label for="mecanico">Mecánico</label>
        <input type="radio" id="membrana" name="teclado" value="Membrana">
        <label for="membrana">Membrana</label>
        <br><br>

        <label for="presupuesto">Presupuesto:</label>
        <input type="range" id="presupuesto" name="presupuesto" min="500" max="5000" step="100">
        <output id="presupuestoOutput">2750</output>
    </fieldset>

    <fieldset>
        <legend>Comentarios Adicionales</legend>
        <label for="comentarios">Comentarios:</label><br>
        <textarea id="comentarios" name="comentarios" rows="4" cols="50" placeholder="Escribe tus comentarios aquí..."></textarea>
    </fieldset>

    <br>
    <button type="submit">Registrar equipo</button>
    <button type="reset">Restablecer formulario</button>
</form>
```
### Explicación de las etiquetas y atributos relacionados con los formularios

#### `<form action="https://webhook.site/723ffee6-5e54-434f-afdc-2fc4f4c1efc9" method="post">`
Define un formulario HTML. Los atributos son:
- `action="https://webhook.site/723ffee6-5e54-434f-afdc-2fc4f4c1efc9"`: URL a la que se enviarán los datos del formulario.
- `method="post"`: Método HTTP usado para enviar los datos. En este caso, `post` se usa para enviar datos de forma segura.

#### `<fieldset>`
Etiqueta semámtica que Agrupa elementos relacionados dentro de un formulario para mejorar la legibilidad y organización.

#### `<legend>`

Proporciona un título para los elementos agrupados dentro del `<fieldset>`, describiendo el propósito del grupo de campos.

#### `<label for="nombreEquipo">Nombre del equipo:</label>`
Define un rótulo para el elemento con `id="nombreEquipo"`. El atributo `for` asocia el rótulo con el campo de entrada correspondiente. Esto permite que, al hacer clic en el rótulo, el cursor se posicione automáticamente en el campo de entrada asociado, mejorando así la accesibilidad y la experiencia del usuario.

#### `<input type="text" id="nombreEquipo" name="nombreEquipo" required maxlength="100" placeholder="Nombre del equipo de gaming">`
Define un campo de entrada de texto. Atributos:
- `type="text"`: Especifica que el campo es para ingresar texto.
- `id="nombreEquipo"`: Identificador único para este campo.
- `name="nombreEquipo"`: Nombre del campo, usado al enviar los datos del formulario.
- `required`: Indica que este campo es obligatorio.
- `maxlength="100"`: Longitud máxima del texto permitido.
- `placeholder="Nombre del equipo de gaming"`: Texto sugerido que aparece en el campo antes de que el usuario ingrese datos.

#### `<input type="date" id="fechaRegistro" name="fechaRegistro" required>`
Campo de entrada para fechas. `type="date"` crea un selector de fechas. `required` indica que el campo es obligatorio.

#### `<select id="categoria" name="categoria" required>`
Elemento para seleccionar una opción de una lista predefinida. Atributos:
- `id` y `name` funcionan igual que en los campos `<input>`.
- `required`: Indica que este campo es obligatorio.

#### `<option value="...">`
Define las opciones dentro del `<select>`. El atributo `value` especifica el valor que se enviará si se selecciona esa opción.

#### `<input type="email" id="emailContacto" name="emailContacto" required placeholder="ejemplo@correo.com">`
Campo para ingresar un correo electrónico. `type="email"` requiere un formato válido de correo electrónico. `placeholder` proporciona un ejemplo de entrada.

#### `<input type="url" id="website" name="website" placeholder="https://www.sitiodelteam.com">`
Campo de entrada para una URL. `type="url"` requiere un formato válido de URL.

#### `<input type="number" id="numJugadores" name="numJugadores" min="1" max="10" step="1" required>`
Campo para ingresar un número. Atributos:
- `min="1"`: Valor mínimo permitido.
- `max="10"`: Valor máximo permitido.
- `step="1"`: Incremento o decremento permitido.
- `required`: Campo obligatorio.

#### `<input type="checkbox" id="capitan" name="capitan">`
Define una casilla de verificación. `type="checkbox"` permite al usuario marcar o desmarcar el campo.

#### `<input type="radio" id="mecanico" name="teclado" value="Mecánico">`
Campo de opción única. `type="radio"` permite al usuario elegir una opción dentro de un grupo de opciones con el mismo `name`. El atributo `value` indica el valor que se enviará al seleccionar la opción.

#### `<input type="range" id="presupuesto" name="presupuesto" min="500" max="5000" step="100">`
Campo para seleccionar un valor dentro de un rango. Atributos:
- `min` y `max` definen el rango de valores permitidos.
- `step` define los incrementos del rango.

#### `<textarea id="comentarios" name="comentarios" rows="4" cols="50" placeholder="Escribe tus comentarios aquí..."></textarea>`
Área de texto para ingresar varias líneas. Atributos:
- `rows` y `cols` definen el tamaño del área de texto.
- `placeholder` muestra un texto sugerido antes de que el usuario ingrese datos.

#### `<button type="submit">Registrar equipo</button>`
Botón para enviar el formulario. `type="submit"` hace que los datos del formulario se envíen a la URL especificada en `action`.

#### `<button type="reset">Restablecer formulario</button>`
Botón para restablecer todos los campos del formulario a sus valores iniciales. `type="reset"` permite limpiar todos los campos del formulario.

