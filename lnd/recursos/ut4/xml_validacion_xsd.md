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
La declaración que aparece en la primera línea: `<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema">` es el inicio de una definición de esquema XML (XSD, *XML Schema Definition*), que se usa para definir la estructura y las reglas de un documento XML. Explicación del contenido:

- **`<xs:schema>`**  
   - Es el elemento raíz de un archivo XSD.
   - Define un esquema XML que establece la estructura, restricciones y tipos de datos para un documento XML.

- **`xmlns:xs="http://www.w3.org/2001/XMLSchema"`**  
  - **`xmlns`** significa "XML Namespace" (Espacio de Nombres en XML)
    Se usa para evitar conflictos de nombres cuando se combinan diferentes vocabularios XML en un mismo documento. Define a qué esquema pertenecen los elementos y atributos en el documento.
  - **`xs`**: es un prefijo asociado a este espacio de nombres. Al utilizar `xmlns:xs="http://www.w3.org/2001/XMLSchema"`, indicamos que el prefijo `**xs**` es un alias.
  - **`http://www.w3.org/2001/XMLSchema`** es la URL del estándar XSD Es el espacio de nombres definido por el W3C para XML Schema. No es una URL que se vaya a descargar al validad, sino un identificador único del estándar.

El resto de líneas del documento especifican la estructura y restricciones que debe cumplir un documento XML para ser validado con este esquema. Iremos viendo como crear las reglas. Para el ejemplo anterior, para que un documento XML sea válido según el esquema XSD debe cumplir con las siguientes características:

- Debe tener un elemento raíz `<persona>`. El documento XML debe comenzar con un único elemento <persona>.
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

A la hora de definir elementos utilizando XSD debemos especificar su nombre y si es simple o complejo (Definidos mediante combinaciones de elementos y atributos). Para los tipos de datos simples debemos especificar que tipos de datos pueden almacenar. 

los tipos de datos definen qué valores pueden contener los elementos y atributos de un documento. XSD define una variedad de tipos de datos. Los más habituales son: `xs:string`, `xs:int`, `xs:decimal`, `xs:boolean`, `xs:date`, `xs:time`, etc.

Ejemplo:
```xml
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

#### Sin completar a partir de aquí

## Estructuras en XSD
- **Elementos Simples:** No contienen subelementos.
- **Elementos Complejos:** Pueden contener otros elementos y atributos.
- **Atributos:** Definen propiedades adicionales para los elementos.

Ejemplo de un **elemento con atributos**:

En este caso, el elemento `usuario` tiene un atributo `id`. Los atributos en XSD proporcionan información adicional sobre un elemento y pueden definirse con distintos tipos de datos y restricciones. En este ejemplo, el atributo `id` es de tipo `xs:int` y es obligatorio (`use="required"`). Esto significa que cualquier elemento `usuario` en el documento XML deberá incluir un identificador numérico para ser válido.
```xml
<xs:element name="usuario">
    <xs:complexType>
        <xs:attribute name="id" type="xs:int" use="required"/>
    </xs:complexType>
</xs:element>
```

## Ejemplos de XML y XSD

A continuación, se presentan varios ejemplos de XML junto con sus correspondientes esquemas XSD.

### Ejemplo 1: Información de una Persona
**XML:**
```xml
<persona>
    <nombre>Juan Pérez</nombre>
    <edad>30</edad>
    <correo>juan.perez@example.com</correo>
</persona>
```

**XSD:**
```xml
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema">
    <xs:element name="persona">
        <xs:complexType>
            <xs:sequence>
                <xs:element name="nombre" type="xs:string"/>
                <xs:element name="edad" type="xs:int"/>
                <xs:element name="correo" type="xs:string"/>
            </xs:sequence>
        </xs:complexType>
    </xs:element>
</xs:schema>
```

**Explicación:**
Este esquema define un elemento `persona` que contiene tres subelementos: `nombre` (cadena de texto), `edad` (entero) y `correo` (cadena de texto). Cada elemento debe aparecer exactamente una vez y seguir los tipos de datos especificados.

### Ejemplo 2: Lista de Productos
**XML:**
```xml
<productos>
    <producto id="101">
        <nombre>Smartphone</nombre>
        <precio>699.99</precio>
    </producto>
    <producto id="102">
        <nombre>Tablet</nombre>
        <precio>499.99</precio>
    </producto>
</productos>
```

**XSD:**
```xml
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema">
    <xs:element name="productos">
        <xs:complexType>
            <xs:sequence>
                <xs:element name="producto" maxOccurs="unbounded">
                    <xs:complexType>
                        <xs:sequence>
                            <xs:element name="nombre" type="xs:string"/>
                            <xs:element name="precio" type="xs:decimal"/>
                        </xs:sequence>
                        <xs:attribute name="id" type="xs:int" use="required"/>
                    </xs:complexType>
                </xs:element>
            </xs:sequence>
        </xs:complexType>
    </xs:element>
</xs:schema>
```

**Explicación:**
Este esquema define una lista de productos donde cada `producto` tiene un atributo `id` obligatorio, un `nombre` como cadena de texto y un `precio` en formato decimal. El uso de `maxOccurs="unbounded"` permite incluir múltiples productos dentro del elemento `productos`.





