# Espacios de Nombres en XML (XML Namespaces)

## Introducción
Los espacios de nombres en XML proporcionan un método para evitar conflictos en los nombres de los elementos cuando se combinan documentos XML de diferentes aplicaciones.

## Conflictos de Nombres
En XML, los nombres de los elementos son definidos por el desarrollador, lo que puede provocar conflictos cuando se mezclan documentos XML de distintas aplicaciones.

Ejemplo de XML con información de una tabla HTML:
```xml
<table>
  <tr>
    <td>Manzanas</td>
    <td>Bananas</td>
  </tr>
</table>
```

Ejemplo de XML con información sobre una mesa (mueble):
```xml
<table>
  <name>Mesa de Café Africana</name>
  <width>80</width>
  <length>120</length>
</table>
```
Si estos fragmentos XML se combinaran, existiría un conflicto de nombres ya que ambos contienen el elemento `<table>`, pero con significados y contenidos diferentes.

## Solución al Conflicto con Prefijos
Para evitar estos conflictos, se pueden utilizar prefijos en los nombres de los elementos:
```xml
<h:table>
  <h:tr>
    <h:td>Manzanas</h:td>
    <h:td>Bananas</h:td>
  </h:tr>
</h:table>

<f:table>
  <f:name>Mesa de Café Africana</f:name>
  <f:width>80</f:width>
  <f:length>120</f:length>
</f:table>
```
En este caso, los prefijos `h:` y `f:` diferencian ambos elementos `<table>`, evitando conflictos.

## Espacios de Nombres en XML - Atributo `xmlns`
Cuando se usan prefijos en XML, es necesario definir un espacio de nombres para cada prefijo mediante el atributo `xmlns` en la etiqueta de inicio del elemento.

Ejemplo:
```xml
<root>
  <h:table xmlns:h="http://www.w3.org/TR/html4/">
    <h:tr>
      <h:td>Manzanas</h:td>
      <h:td>Bananas</h:td>
    </h:tr>
  </h:table>
  
  <f:table xmlns:f="https://www.w3schools.com/furniture">
    <f:name>Mesa de Café Africana</f:name>
    <f:width>80</f:width>
    <f:length>120</f:length>
  </f:table>
</root>
```

- `xmlns:h="http://www.w3.org/TR/html4/"` asigna el prefijo `h:` a este espacio de nombres.
- `xmlns:f="https://www.w3schools.com/furniture"` asigna el prefijo `f:` a otro espacio de nombres.

Cuando un espacio de nombres se define para un elemento, todos los elementos secundarios con el mismo prefijo quedan asociados a dicho espacio.

## Declaración de Espacios de Nombres en el Elemento Raíz
Otra opción es definir los espacios de nombres en el elemento raíz:
```xml
<root xmlns:h="http://www.w3.org/TR/html4/"
      xmlns:f="https://www.w3schools.com/furniture">
  <h:table>
    <h:tr>
      <h:td>Manzanas</h:td>
      <h:td>Bananas</h:td>
    </h:tr>
  </h:table>
  
  <f:table>
    <f:name>Mesa de Café Africana</f:name>
    <f:width>80</f:width>
    <f:length>120</f:length>
  </f:table>
</root>
```
**Nota:** La URI del espacio de nombres no se usa para buscar información; solo sirve para asignar un identificador único.

## Identificador de Recursos Uniforme (URI)
Un **Uniform Resource Identifier (URI)** es una cadena de caracteres que identifica un recurso en Internet.
- Un tipo común de URI es la **URL** (Uniform Resource Locator), que identifica una dirección web.
- Otro tipo menos común es el **URN** (Uniform Resource Name).

## Espacios de Nombres Predeterminados
Para evitar el uso de prefijos en todos los elementos secundarios, se puede definir un espacio de nombres predeterminado:
```xml
<table xmlns="http://www.w3.org/TR/html4/">
  <tr>
    <td>Manzanas</td>
    <td>Bananas</td>
  </tr>
</table>
```
En este caso, todos los elementos dentro de `<table>` heredan el espacio de nombres sin necesidad de un prefijo.

Otro ejemplo con información sobre un mueble:
```xml
<table xmlns="https://www.w3schools.com/furniture">
  <name>Mesa de Café Africana</name>
  <width>80</width>
  <length>120</length>
</table>
```

## Conclusión
- Los **espacios de nombres en XML** ayudan a evitar conflictos de nombres al combinar documentos de distintas fuentes.
- Se definen mediante el atributo `xmlns`, con o sin prefijos.
- Los **URI** sirven como identificadores únicos, pero no necesariamente apuntan a una página web.
- Son esenciales en el procesamiento de XML.

Con estas técnicas, los desarrolladores pueden estructurar documentos XML de manera clara y evitar ambigüedades. 
