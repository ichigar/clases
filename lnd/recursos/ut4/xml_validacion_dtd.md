# Validación de Documentos XML utilizando DTD

## Introducción

Un **DTD (Document Type Definition)** es un conjunto de reglas que define la estructura, los elementos, los atributos y las entidades de un documento XML. Ayuda a asegurar que un documento XML sea válido y cumpla con una estructura predefinida. Los DTD se pueden usar para definir qué elementos están permitidos, en qué orden deben aparecer, qué atributos deben tener, y si los elementos pueden repetirse o no.

## Definición de un DTD

Un DTD se puede definir de dos maneras:
- **Interna**: Dentro del propio documento XML.
- **Externa**: En un archivo DTD separado que hace referencia al documento XML.

### DTD Interno

Un DTD interno se declara dentro de un documento XML. La declaración `DOCTYPE` está ubicada al inicio del archivo XML, antes de la raíz del documento.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE nota [
  <!ELEMENT nota (destinatario, asunto, mensaje)>
  <!ELEMENT destinatario (#PCDATA)>
  <!ELEMENT asunto (#PCDATA)>
  <!ELEMENT mensaje (#PCDATA)>
]>
<nota>
  <destinatario>Juan Pérez</destinatario>
  <asunto>Reunión de trabajo</asunto>
  <mensaje>El informe está listo para la revisión.</mensaje>
</nota>
```

En este ejemplo:
- `<!DOCTYPE nota [ ... ]>` declara que el documento XML está validado por un DTD que describe la estructura.
- `<!ELEMENT ...>` define los elementos y su contenido.

#### DTD Externo

Un DTD externo se declara con la palabra clave `DOCTYPE` y hace referencia a un archivo DTD separado, que contiene las reglas para validar el documento.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE nota SYSTEM "nota.dtd">
<nota>
  <destinatario>Juan Pérez</destinatario>
  <asunto>Reunión de trabajo</asunto>
  <mensaje>El informe está listo para la revisión.</mensaje>
</nota>
```

Archivo `nota.dtd`:

```xml
<!ELEMENT nota (destinatario, asunto, mensaje)>
<!ELEMENT destinatario (#PCDATA)>
<!ELEMENT asunto (#PCDATA)>
<!ELEMENT mensaje (#PCDATA)>
```

En este caso, el archivo `nota.dtd` define la estructura de `nota.xml`.

## Proceso de validación

Una vez definido el DTD que debe cumplir un determinado documento XML debemos poder realizar el proceso de validación. Para ello existen múltiples tipos de herramientas como:

- Utilizando la herramienta de línea de comandos `xmllint`
- Con el plugin **XML by Red Hat** en VSCode u otros complementos para diferentes IDE.
- Herrramientas online, como por ejemplo <https://www.truugo.com/xml_validator/>
- Con programas que usen **librerias** específicas de XML en diferentes lenguajes de programación como **Python**, **PHP** o **Java**

## Elementos en un DTD

Un DTD describe qué elementos son permitidos y cómo deben organizarse dentro del documento. La declaración de un elemento tiene la siguiente forma:

```xml
<!ELEMENT nombre_del_elemento contenido>
```

### Tipos de Contenido

* **PCDATA** (Parsed Character Data): Contenido textual.

   ```xml
   <!ELEMENT nombre (#PCDATA)>
   ```

   Este ejemplo indica que el elemento `nombre` debe contener texto.

* **Elementos vacíos** (EMPTY): Para elementos sin contenido (autocerrados en XML). Son útiles si queremos que el elemento únicamente tenga atributos, pero no contenido:

```xml
<!ELEMENT imagen EMPTY>
```

  Este ejemplo indica que el elemento no debería tener contenido. Debería ser de la forma: `<imagen/>`.


* **Elementos con otros elementos**: Se pueden definir elementos dentro de otros elementos. Sirven para definir la estructura que debe tener el documento. Además, los elementos deben aparecer en el orden especificado en el documento XML:

Ejemplo en DTD:

  ```xml
  <!ELEMENT direccion (calle, ciudad, codigoPostal)>
  <!ELEMENT calle (#PCDATA)>
  <!ELEMENT ciudad (#PCDATA)>
  <!ELEMENT codigoPostal (#PCDATA)>
  ````

Ejemplo de XML válido:

  ```xml
  <direccion>
    <calle>Av. Reforma 100</calle>
    <ciudad>Ciudad de México</ciudad>
    <codigoPostal>01000</codigoPostal>
  </direccion>
  ```

Ejemplo de XML inválido. El orden es incorrecto:

  ```xml
  <direccion>
    <codigoPostal>01000</codigoPostal>
    <calle>Av. Reforma 100</calle>
    <ciudad>Ciudad de México</ciudad>
  </direccion>
  ```

* **Elección de elementos**: Se puede usar el operador `|` para indicar elementos alternativos.

  ```xml
  <!ELEMENT transporte (auto | bicicleta | avion)>
  <!ELEMENT auto (#PCDATA)>
  <!ELEMENT bicicleta (#PCDATA)>
  <!ELEMENT avion (#PCDATA)>
  ```

Ejemplo XML válido:

```xml
<transporte>
    <bicicleta>Mountain Bike</bicicleta>
</transporte>
```
Ejemplo inválido. Hay más de una opción dentro de `<transporte>`:

```xml
<transporte>
    <auto>Ford</auto>
    <avion>Boeing</avion>
</transporte>
```

* **Repitición de elementos**: Se puede usar el operador `*` (cero o más) o `+` (uno o más) para definir la cantidad de repeticiones de un elemento.

   ```xml
   <!ELEMENT lista_de_compras (item+)>
   ```

   Aquí, `lista_de_compras` debe contener uno o más elementos `item`.

* **Elementos opcionales**: Se usa `?` para indicar que un elemento es opcional.

```xml
<!ELEMENT persona (nombre, telefono?)>
```
  Esto indica que el elemento <telefono> puede aparecer 0 o 1 vez (es opcional), mientras que nombre debe aparecer obligatoriamente.


### Ejemplo Completo con los Diferentes Operadores:

```xml
<!ELEMENT persona (nombre, apellido, direccion?, telefono*)>
```

- El elemento `persona` debe contener:
  - Un `nombre` (obligatorio),
  - Un `apellido` (obligatorio),
  - Una `direccion` (opcional),
  - Uno o más elementos `email` (pueden repetirse, debe haber uno al menos)
  - Cero o más elementos `telefono` (opcionales, pueden repetirse).

Ejemplo de documento XML válido:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE persona [
  <!ELEMENT persona (nombre, apellido, direccion?, email+, telefono*)>
  <!ELEMENT nombre (#PCDATA)>
  <!ELEMENT apellido (#PCDATA)>
  <!ELEMENT direccion (#PCDATA)>
  <!ELEMENT email (#PCDATA)>
  <!ELEMENT telefono (#PCDATA)>
]>
<persona>
  <nombre>Juan</nombre>
  <apellido>Pérez</apellido>
  <direccion>Calle Falsa 123</direccion>
  <email>jhondoe@example.com</email>
  <telefono>123456789</telefono>
  <telefono>987654321</telefono>
</persona>
```

## Atributos de los Elementos

Los atributos permiten describir información adicional sobre los elementos. Los atributos se definen en el DTD con la siguiente sintaxis:

```xml
<!ATTLIST nombre_del_elemento atributo tipo_de_atributo valor>
```

Ejemplo:

```xml
<!ATTLIST libro isbn CDATA #REQUIRED>
```

Esto indica que el elemento `libro` debe tener un atributo `isbn` que debe ser de tipo `CDATA` (texto normal) y es **requerido**. 

### Tipos de Atributos

- **`CDATA`**: El atributo puede contener cualquier texto. puede ser obligatorio(#REQUIRED) o tener un valor por defecto (los veremos más adelante)

```xml
<!DOCTYPE biblioteca [
    <!ELEMENT biblioteca (libro)>
    <!ELEMENT libro (#PCDATA)>
    <!ATTLIST libro titulo CDATA #REQUIRED>
]>
<biblioteca>
    <libro titulo="El Quijote"/>
</biblioteca>
```

- **`ID`**: Identificador único dentro del documento. No puede haber otra etiqueta que tenga el mismo valor en dicho atributo. Solo puede contener letras, números y algunos caracteres especiales (-, _, .).

```xml
<!DOCTYPE biblioteca [
    <!ELEMENT biblioteca (libro)>
    <!ELEMENT libro (#PCDATA)>
    <!ATTLIST libro id ID #REQUIRED>
]>
<biblioteca>
    <libro id="L001"/>
    <libro id="L002"/>
</biblioteca>
```

Otros atributos que podemos utilizar son:

- `IDREF`: Referencia a un identificador.
- `NMTOKEN`: Cadena de texto que puede contener letras, números y guiones.

### Valor por defecto de un atributo

En **DTD**, se puede definir un **valor por defecto** para un atributo en la declaración `<!ATTLIST>` utilizando la siguiente sintaxis:

```xml
<!ATTLIST nombre_del_elemento nombre_atributo tipo_de_dato "valor_por_defecto">
```

**Ejemplo de uso de valores por defecto**

Si tienes un elemento `<libro>` con un atributo `disponible` que, por defecto, es `"sí"`, puedes definirlo así en el **DTD**:

```xml
<!DOCTYPE biblioteca [
    <!ELEMENT biblioteca (libro)>
    <!ELEMENT libro (#PCDATA)>
    <!ATTLIST libro disponible CDATA "sí">
]>
<biblioteca>
    <libro>Cien años de soledad</libro>
</biblioteca>
```

El atributo `disponible="sí"` se **asume automáticamente** si no se especifica en el XML.

Si el usuario especifica el atributo en el XML, **se usa el valor proporcionado** y no se aplica el valor por defecto:

```xml
<biblioteca>
    <libro disponible="no">Don Quijote</libro>
</biblioteca>
```

En este caso el valor `"no"` sobrescribe el valor por defecto `"sí"`.


### Tipos de valores de atributos en DTD

| **Tipo de Valor** | **Significado** |
|-------------------|----------------|
| `"valor"`        | Valor por defecto si no se proporciona en el XML. |
| `#REQUIRED`      | **Obligatorio**: El XML será inválido si falta el atributo. |
| `#IMPLIED`       | **Opcional sin valor por defecto**: Puede omitirse sin problemas. |
| `#FIXED "valor"` | **Valor fijo**: No se puede cambiar en el XML. |


**Ejemplo de cada caso**

```xml
<!DOCTYPE biblioteca [
    <!ELEMENT biblioteca (libro)>
    <!ELEMENT libro (#PCDATA)>
    <!ATTLIST libro disponible CDATA "sí">   <!-- Valor por defecto -->
    <!ATTLIST libro isbn CDATA #REQUIRED>    <!-- Obligatorio -->
    <!ATTLIST libro editorial CDATA #IMPLIED>  <!-- Opcional sin valor por defecto -->
    <!ATTLIST libro formato CDATA #FIXED "digital"> <!-- Fijo, no se puede cambiar -->
]>
```

Ejemplo XML válido con esta definición:

```xml
<biblioteca>
    <libro isbn="978-3-16-148410-0">Cien años de soledad</libro>
    <libro isbn="978-84-376-0494-7" disponible="no" editorial="Alfaguara">Don Quijote</libro>
</biblioteca>
```

**Explicación:**
- **`isbn` es obligatorio**, por lo que **debe** estar presente.
- **`disponible` se asume `"sí"`** si no se especifica.
- **`editorial` es opcional**, así que puede faltar sin errores.
- **`formato="digital"` no puede cambiarse**, aunque no se escriba en el XML.

