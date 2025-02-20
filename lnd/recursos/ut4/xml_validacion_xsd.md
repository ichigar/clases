# Validación mediante esquemas XSD

## Definición de esquema(schema)
Un **esquema** (schema) es una estructura o definición que **establece las reglas para validar** documentos XML. Consiste en un conjunto de reglas que especifica, para un documento XML:

- Los elementos y atributos que pueden aparecer
- En qué orden
- Con qué tipos de datos
- Con qué restricciones.

## Tipos de esquemas en XML

Existen varios lenguajes para definir esquemas en XML, los más comunes son:

- DTD (Document Type Definition)
- XSD (XML Schema Definition)
- Relax NG

## Introducción a XSD

XML Schema Definition (XSD) es un lenguaje basado en XML que se utiliza para definir la estructura y restricciones de un documento XML. XSD es una alternativa más potente y flexible que DTD (Document Type Definition), permitiendo definir tipos de datos, reglas de validación y estructuras complejas.

## Características de XSD
- Define la estructura de un documento XML.
- Permite la validación automática de datos.
- Soporta **tipos de datos** (numéricos, cadenas, fechas, booleanos, etc.).
- Permite **restricciones** (longitud, valores permitidos, patrones, etc.).
- Admite **herencia y reutilización** de elementos y atributos.
- Utiliza **espacios de nombres (namespaces)** para evitar conflictos.

## Sintaxis Básica de XSD
Un archivo XSD tiene apariencia similar a la siguiente:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema">
    <xs:element name="persona">
        <xs:complexType>
            <xs:sequence>
                <xs:element name="nombre" type="xs:string"/>
                <xs:element name="edad" type="xs:int"/>
            </xs:sequence>
        </xs:complexType>
    </xs:element>
</xs:schema>
```
La declaración que aparece en la segunda línea: `<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema">` es el inicio de una definición de esquema XML (XSD, *XML Schema Definition*), que se usa para definir la estructura y las reglas de un documento XML. 

Explicación del contenido:

- **`<xs:schema>`**  
   - Es el elemento raíz de un archivo XSD.
   - Define un esquema XML que establece la estructura, restricciones y tipos de datos para un documento XML.

- **`xmlns:xs="http://www.w3.org/2001/XMLSchema"`**  
  - **`xmlns`** significa "XML Namespace" (Espacio de Nombres en XML)
    es una declaración de espacio de nombres XML. Aquí, `xmlns:xs` define un prefijo (`xs`) que se asocia con el espacio de nombres http://www.w3.org/2001/XMLSchema. Este espacio de nombres es estándar y se utiliza para definir elementos y tipos de datos en un esquema XML.
  - **`xs`**: es un prefijo asociado a este espacio de nombres. Al utilizar `xmlns:xs="http://www.w3.org/2001/XMLSchema"`, indicamos que el prefijo **`xs`** es un alias.
  - **`http://www.w3.org/2001/XMLSchema`** es la URL del estándar XSD Es el espacio de nombres definido por el W3C para XML Schema. No es una URL que se vaya a descargar al validad, sino un identificador único del estándar.

Esta primera línea, básicamente establece que estamos definiendo un documento de validación XSD. El resto de líneas del documento especifican la estructura y restricciones que debe cumplir un documento XML para ser validado con este esquema. 

Para el ejemplo anterior, para que un documento XML sea válido según el esquema XSD debe cumplir con las siguientes características:

- Debe tener un elemento raíz `<persona>`. El documento XML debe comenzar con un único elemento `<persona>`.
- `<xs:complexType` indica que se va a definir un tipo de datos complejo. Un tipo de datos complejo es un tipo que puede contener otros elementos y atributos, a diferencia de los tipos de datos simples que solo contienen texto.
- Debe contener los elementos `<nombre>` y `<edad>` dentro de `<persona>`
- `<nombre>` debe ser de tipo **xs:string** (texto).
- `<edad>` debe ser de tipo **xs:int** (entero, sin decimales).
- Los elementos deben estar en el orden correcto. `<nombre>` debe aparecer antes de `<edad>` porque están definidos en una secuencia (`<xs:sequence>`).

## Validación de XML con XSD

A diferencia de la validación utilizando el esquema DTD, con XSD no podemos incluir la definición del mismo en el documento XML sino que debemos hacerlo de forma externa.

Para indicar en un fichero XML el archivo en el que se encuentra el XSD que lo valida lo hacemos de la siguiente forma:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<libro xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xsi:noNamespaceSchemaLocation="libro.xsd">
    <titulo>Aprendiendo XML</titulo>
    <autor>Juan Pérez</autor>
    <precio>25.50</precio>
</libro>
```

En un fichero de nombre "libro.xsd" incluimos el fichero con el esquema XSD que define la estructura esperada del XML:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema">
    <xs:element name="libro">
        <xs:complexType>
            <xs:sequence>
                <xs:element name="titulo" type="xs:string"/>
                <xs:element name="autor" type="xs:string"/>
                <xs:element name="precio" type="xs:decimal"/>
            </xs:sequence>
        </xs:complexType>
    </xs:element>
</xs:schema>
```

Con el mismo tipo de herramientas que utilizamos para el esquema DTD podemos validar el documento XML.

## Definiendo elementos en XSD

A la hora de definir elementos utilizando XSD debemos especificar su **nombre** y si es simple o complejo (Definidos mediante combinaciones de elementos y atributos). Para los tipos de datos simples debemos especificar que tipos de datos pueden almacenar. 

los tipos de datos definen qué valores pueden contener los elementos y atributos de un documento. XSD define una variedad de tipos de datos. Los más habituales son: `xs:string`, `xs:int`, `xs:decimal`, `xs:boolean`, `xs:date`, `xs:time`, etc.

Ejemplo:
```xml
<?xml version="1.0" encoding="UTF-8"?>
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema">
    <xs:element name="persona">
        <xs:complexType>
            <xs:sequence>
                <xs:element name="nombre" type="xs:string"/>
                <xs:element name="edad" type="xs:int"/>
                <xs:element name="altura" type="xs:decimal"/>
                <xs:element name="fechaNacimiento" type="xs:date"/>
            </xs:sequence>
        </xs:complexType>
    </xs:element>
</xs:schema>
```
Para que un documento XML sea válido según el esquema XSD dado, debe cumplir las siguientes características:

- Debe tener un único elemento raíz llamado `<persona>`
- Debe contener los elementos obligatorios en el orden correcto:
  - `<nombre>` (tipo `xs:string`): Debe contener solo texto.
  - `<edad>` (tipo `xs:int`): Debe ser un número entero (sin decimales.
  - `<altura>` (tipo `xs:decimal`): Debe ser un número decimal, permitiendo decimales opcionales.
  - `<fechaNacimiento>` (tipo `xs:date`): Debe seguir el formato `YYYY-MM-DD`.
- No puede omitir ninguno de los elementos definidos en la secuencia y deben estar en el orden en que se definen (`<xs:sequence>`)

Ejemplo de un XML válido según este esquema

```xml
<?xml version="1.0" encoding="UTF-8"?>
<persona>
    <nombre>Ana López</nombre>
    <edad>28</edad>
    <altura>1.68</altura>
    <fechaNacimiento>1995-07-15</fechaNacimiento>
</persona>
```

Si queremos definir que los elementos contenidos en un tipo complejo pueden aparecer en cualquier orden se utiliza `xs:all` en lugar de `xs:sequence`. Para el ejemplo anterior, si queremos indicar que los elementos contenidos en `<persona>` pueden aparecer en cualquier orden lo hacemos de la forma:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema" elementFormDefault="qualified">

    <xs:element name="persona">
        <xs:complexType>
            <xs:all>
                <xs:element name="nombre" type="xs:string"/>
                <xs:element name="edad" type="xs:int"/>
                <xs:element name="altura" type="xs:decimal"/>
                <xs:element name="fechaNacimiento" type="xs:date"/>
            </xs:all>
        </xs:complexType>
    </xs:element>

</xs:schema>
```
Para la definición anterior, el siguiente documento sería válido:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<persona>
    <edad>30</edad>
    <nombre>Juan Pérez</nombre>
    <fechaNacimiento>1993-05-12</fechaNacimiento>
    <altura>1.75</altura>
</persona>
```

### Repetición de elementos

Podemos indicar el número de veces que puede aparecer un elemento dentro de una secuencia utilizando los atributos `minOccurs` y `maxOccurs` en su definición.

- `minOccurs="0"` → Hace que el elemento sea opcional.
- `maxOccurs="1"` → El elemento puede aparecer una sola vez como máximo.
- `minOccurs="1"` → El elemento debe aparecer al menos una vez.
- `maxOccurs="unbounded"` → El elemento puede repetirse un número ilimitado de veces.

#### Elementos opcionales

Indicamos que un elemento puede o no aparecer con `minOccurs="0"` y `maxOccurs="1"`.

```xml
<xs:element name="telefono" type="xs:string" minOccurs="0" maxOccurs="1"/>
```

Significa que el elemento `telefono` es opcional y puede aparecer como máximo 1 vez. Equivale al uso de `?` en el esquema de validación **DTD**.


Ejemplo XML válido:

```xml
<telefono>123456789</telefono>
```


#### Permitir que un elemento se repita varias veces

Podemos especificar un rango de ocurrencias.

Ejemplo: minOccurs="1" y maxOccurs="5" (Debe aparecer al menos una vez, pero no más de cinco)

```xml
<xs:element name="telefono" type="xs:string" minOccurs="1" maxOccurs="5"/>
```
Ejemplos XML válidos:

```xml
<telefono>123456789</telefono>
```

```xml
<telefono>123456789</telefono>
<telefono>987654321</telefono>
<telefono>555555555</telefono>
```

Ejemplo XML no válido (más de 5 elementos):

```xml
<telefono>123456789</telefono>
<telefono>987654321</telefono>
<telefono>555555555</telefono>
<telefono>666666666</telefono>
<telefono>777777777</telefono>
<telefono>888888888</telefono>  <!-- Error: Se permite un máximo de 5 -->
```

#### Permitir un número ilimitado de repeticiones

Si queremos permitir cualquier número de elementos, usamos `maxOccurs="unbounded"`.

Ejemplo: `minOccurs="0"` y `maxOccurs="unbounded"` (Cero o más veces)

```xml
<xs:element name="telefono" type="xs:string" minOccurs="0" maxOccurs="unbounded"/>
```

### Nombres alternativos de elementos en XSD. `xs:choice`

En **XSD (XML Schema Definition)**, podemos indicar que un elemento puede tener un **nombre alternativo** usando `xs:choice` (Múltiples nombres para un mismo tipo)

Ejemplo: Un elemento que puede llamarse `telefono` o `movil`:


```xml
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema">
    <xs:element name="contacto">
        <xs:complexType>
            <xs:sequence>
                <xs:choice>
                    <xs:element name="telefono" type="xs:string"/>
                    <xs:element name="movil" type="xs:string"/>
                </xs:choice>
            </xs:sequence>
        </xs:complexType>
    </xs:element>
</xs:schema>
```

Ejemplo XML válido:

```xml
<contacto>
    <telefono>123456789</telefono>
</contacto>
```
```xml
<contacto>
    <movil>987654321</movil>
</contacto>
```
## Restringiendo el valor de los elementos

### **Especificación de Restricciones a Elementos Simples en XSD**
En **XML Schema Definition (XSD)**, se pueden agregar **restricciones (facetas)** a los elementos simples utilizando el elemento `<xs:restriction>`. Esto permite definir reglas sobre **valores permitidos, longitudes, patrones, rangos numéricos**, etc.

### Uso de `<xs:restriction>` dentro de `<xs:simpleType>`**
El patrón general para restringir un tipo de dato en XSD se aplica sustituyendo la declaración de un elemento simple de la forma:

```xml
<xs:element name="nombre_elemento" type="xs:tipo"/>
```
Por: 

```xml
<xs:simpleType name="nombre_elemento">
    <xs:restriction base="xs:tipo">
        <!-- Restricciones aquí -->
    </xs:restriction>
</xs:simpleType>
```
Donde:
- `base="xs:tipo"` indica el **tipo de dato original** del cual se parte.
- Dentro de `<xs:restriction>`, se agregan las **restricciones específicas**.

### Tipos de Restricciones Comunes
Las restricciones más usadas en XSD incluyen:

| Restricción | Descripción | Ejemplo |
|-------------|------------|---------|
| `xs:minLength` | Longitud mínima del valor (para `string`) | `minLength="3"` |
| `xs:maxLength` | Longitud máxima del valor (para `string`) | `maxLength="10"` |
| `xs:pattern` | Define un patrón mediante una **expresión regular** | `pattern="[A-Za-z]+"` |
| `xs:enumeration` | Define una lista de **valores permitidos** | `enumeration="Hombre"` |
| `xs:minInclusive` | Valor mínimo permitido (para números) | `minInclusive="18"` |
| `xs:maxInclusive` | Valor máximo permitido (para números) | `maxInclusive="99"` |
| `xs:minExclusive` | Debe ser **mayor** que el valor dado | `minExclusive="0"` |
| `xs:maxExclusive` | Debe ser **menor** que el valor dado | `maxExclusive="100"` |


### Ejemplos de Restricciones de valores de elementos en XSD

```xml
<?xml version="1.0" encoding="UTF-8"?>
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema" elementFormDefault="qualified">

    <xs:element name="persona">
        <xs:complexType>
            <xs:sequence>
                <xs:element name="nombre">
                    <xs:simpleType>
                        <xs:restriction base="xs:string">
                            <xs:minLength value="3"/>
                            <xs:maxLength value="20"/>
                        </xs:restriction>
                    </xs:simpleType>
                </xs:element>

                <xs:element name="edad">
                    <xs:simpleType>
                        <xs:restriction base="xs:int">
                            <xs:minInclusive value="18"/>
                            <xs:maxInclusive value="65"/>
                        </xs:restriction>
                    </xs:simpleType>
                </xs:element>

                <xs:element name="codigoPostal">
                    <xs:simpleType>
                        <xs:restriction base="xs:string">
                            <xs:pattern value="\d{5}"/>
                        </xs:restriction>
                    </xs:simpleType>
                </xs:element>

                <xs:element name="genero">
                    <xs:simpleType>
                        <xs:restriction base="xs:string">
                            <xs:enumeration value="Masculino"/>
                            <xs:enumeration value="Femenino"/>
                            <xs:enumeration value="Otro"/>
                        </xs:restriction>
                    </xs:simpleType>
                </xs:element>
            </xs:sequence>
        </xs:complexType>
    </xs:element>

</xs:schema>
```

### Ejemplo de XML Válido según el Esquema
```xml
<?xml version="1.0" encoding="UTF-8"?>
<persona>
    <nombre>Juan</nombre>
    <edad>25</edad>
    <codigoPostal>28001</codigoPostal>
    <genero>Masculino</genero>
</persona>
```

**Es válido porque:**
- `nombre`: Tiene entre 3 y 20 caracteres.
- `edad`: Está entre 18 y 65 años.
- `codigoPostal`: Tiene 5 dígitos.
- `genero`: Es uno de los valores permitidos.

## Definición de atributos con XSD

Los atributos se definen con `xs:attribute` dentro de un `xs:complexType`, pero fuera de `xs:sequence`.

Ejemplo de definición atributos dentro de un elemento

```xml
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema">
    <xs:element name="persona">
        <xs:complexType>
            <xs:sequence>
                <xs:element name="nombre" type="xs:string"/>
            </xs:sequence>
            <xs:attribute name="id" type="xs:int" use="required"/>
        </xs:complexType>
    </xs:element>
</xs:schema>
```

Ejemplo XML válido:

```xml
<persona id="123">
    <nombre>Juan Pérez</nombre>
</persona>
```
Explicación:
- El atributo `id` es de tipo `xs:int` y es obligatorio (`use="required"`).
- El elemento `nombre` es un subelemento dentro de persona.

### Definición de atributos opcionales

Si el atributo no es obligatorio, se usa `use="optional"` (que es el valor por defecto si no se especifica).

Ejemplo de definición de atributo opcional:

```xml
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema">
    <xs:element name="producto">
        <xs:complexType>
            <xs:sequence>
                <xs:element name="nombre" type="xs:string"/>
            </xs:sequence>
            <xs:attribute name="codigo" type="xs:string" use="optional"/>
        </xs:complexType>
    </xs:element>
</xs:schema>
```

Ejemplo XML válido:

```xml
<producto>
    <nombre>Televisor</nombre>
</producto>
```

También sería válido:

```
<producto codigo="ABC123">
    <nombre>Computadora</nombre>
</producto>
```

### Definición de atributos con valores predeterminados

Se puede asignar un valor por defecto usando `default`.

Ejemplo de definición de atributo con valor por defecto

```xml
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema">
    <xs:element name="usuario">
        <xs:complexType>
            <xs:sequence>
                <xs:element name="nombre" type="xs:string"/>
            </xs:sequence>
            <xs:attribute name="tipo" type="xs:string" default="invitado"/>
        </xs:complexType>
    </xs:element>
</xs:schema>
```

Ejemplos de XML válido:

```xml
<usuario>
    <nombre>Ana</nombre>
</usuario>
```

```xml
<usuario tipo="admin">
    <nombre>Pedro</nombre>
</usuario>
```

Explicación: Si no se especifica el atributo tipo, su valor por defecto será `"invitado"`.

### Restricciones en el valor de los atributos

En **XSD**, los atributos pueden tener restricciones para limitar sus valores. Estas restricciones se aplican mediante **tipos de datos simples** y `xs:restriction`. 

#### 1. Restricción a valores específicos (`xs:enumeration`)

Se usa `xs:enumeration` para definir un conjunto de valores permitidos.

Ejemplo: Atributo `tipoUsuario` con valores específicos:

```xml
<xs:attribute name="tipoUsuario">
    <xs:simpleType>
        <xs:restriction base="xs:string">
            <xs:enumeration value="admin"/>
            <xs:enumeration value="editor"/>
            <xs:enumeration value="visitante"/>
        </xs:restriction>
    </xs:simpleType>
</xs:attribute>
```

Ejemplo XML válido:
```xml
<usuario tipoUsuario="admin"/>
<usuario tipoUsuario="visitante"/>
```

Ejemplo XML inválido:
```xml
<usuario tipoUsuario="superadmin"/> 
<!-- Error: "superadmin" no está en la lista de valores permitidos -->
```

#### 2. Restricción de longitud (`xs:minLength`, `xs:maxLength`)

Se usa cuando un atributo debe tener una cantidad mínima y/o máxima de caracteres.

Ejemplo: Atributo `codigo` con longitud entre 5 y 10 caracteres:
```xml
<xs:attribute name="codigo">
    <xs:simpleType>
        <xs:restriction base="xs:string">
            <xs:minLength value="5"/>
            <xs:maxLength value="10"/>
        </xs:restriction>
    </xs:simpleType>
</xs:attribute>
```
Ejemplo XML válido:

```xml
<producto codigo="ABC123"/>
```
Ejemplo XML inválido**

```xml
<producto codigo="AB"/>  
<!-- Error: Solo tiene 2 caracteres, el mínimo es 5 -->
```

#### 3. Restricción de valores numéricos (`xs:minInclusive`, `xs:maxInclusive`)
Se usa para definir un rango de valores numéricos.

Ejemplo: Atributo `edad` entre 18 y 65 años

```xml
<xs:attribute name="edad">
    <xs:simpleType>
        <xs:restriction base="xs:int">
            <xs:minInclusive value="18"/>
            <xs:maxInclusive value="65"/>
        </xs:restriction>
    </xs:simpleType>
</xs:attribute>
```
Ejemplo XML válido

```xml
<persona edad="30"/>
```
Ejemplo XML inválido
```xml
<persona edad="16"/>  
<!-- Error: 16 está fuera del rango permitido (18-65) -->
```

#### 4. Restricción de valores mediante patrones (`xs:pattern`)

Se usa para validar el formato de un atributo mediante **expresiones regulares**.

Ejemplo: Atributo `codigoPostal` con formato de 5 dígitos:
```xml
<xs:attribute name="codigoPostal">
    <xs:simpleType>
        <xs:restriction base="xs:string">
            <xs:pattern value="\d{5}"/>
        </xs:restriction>
    </xs:simpleType>
</xs:attribute>
```

Ejemplo XML válido
```xml
<direccion codigoPostal="28001"/>
```

Ejemplo XML inválido**
```xml
<direccion codigoPostal="A1234"/>  
<!-- Error: No cumple con el patrón de solo números -->
```
