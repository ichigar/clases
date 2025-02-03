# XML

## Introducción

XML (eXtensible Markup Language) es un lenguaje de marcado que se utiliza para almacenar y transportar datos de forma estructurada y legible tanto por humanos como por máquinas. XML no define cómo se deben presentar los datos, sino cómo deben estructurarse. Fue desarrollado por el W3C (World Wide Web Consortium) y es ampliamente utilizado en aplicaciones y sistemas para el intercambio de información.

### Características más importantes de XML:

1. **Estructura jerárquica**:  
   XML organiza los datos en una estructura de árbol jerárquico, donde un documento XML comienza con un elemento raíz que puede contener múltiples elementos hijos, lo que facilita representar relaciones entre datos.

2. **Legible para humanos y máquinas**:  
   Los datos en XML están escritos en un formato que puede ser entendido por personas y procesado por software.

3. **Extensible**:  
   XML permite definir etiquetas personalizadas que se ajusten a las necesidades específicas de los datos, sin restricciones predefinidas.

4. **Independiente de la plataforma y el lenguaje**:  
   Al ser texto plano, los archivos XML pueden ser utilizados en diferentes plataformas, sistemas operativos y lenguajes de programación.

5. **Validación mediante DTD o XSD**:  
   XML permite la validación de la estructura y el contenido de los datos mediante DTD (Document Type Definition) o XSD (XML Schema Definition). Esto garantiza que los documentos sigan un formato predefinido.

6. **Separación entre contenido y presentación**:  
   XML no incluye información sobre cómo deben presentarse los datos; en su lugar, esta tarea suele delegarse en lenguajes como XSL (eXtensible Stylesheet Language).

7. **Compatibilidad con Unicode**:  
   XML admite el estándar Unicode, lo que permite manejar datos en casi cualquier idioma y alfabeto.

8. **Uso de etiquetas y atributos**:  
   XML utiliza **etiquetas** para definir elementos y atributos para agregar metadatos adicionales a esos elementos.

   Ejemplo:
   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <catalogo>
       <libro id="1">
           <titulo>Cien años de soledad</titulo>
           <autor>Gabriel García Márquez</autor>
           <añoPublicacion>1967</añoPublicacion>
           <editorial>Editorial Sudamericana</editorial>
           <precio moneda="USD">15.99</precio>
       </libro>
       <libro id="2">
           <titulo>Don Quijote de la Mancha</titulo>
           <autor>Miguel de Cervantes</autor>
           <añoPublicacion>1605</añoPublicacion>
           <editorial>Francisco de Robles</editorial>
           <precio moneda="EUR">12.50</precio>
       </libro>
   </catalogo>

   ```

9. **Bien formado**:  
   Un documento XML debe cumplir ciertas reglas básicas.

10. **Interoperabilidad**:  
    XML es ampliamente utilizado para facilitar la comunicación entre sistemas heterogéneos, como servicios web (SOAP, REST) y aplicaciones empresariales.

Estas características hacen que XML sea una herramienta poderosa para el manejo de datos estructurados en diversas industrias. Sin embargo, en ciertos casos, ha sido reemplazado o complementado por formatos más ligeros, como JSON, dependiendo de los requisitos del proyecto.

## Estructura y elementos de un documento XML

La estructura de un documento XML se organiza en niveles jerárquicos que consisten en elementos, atributos, texto y comentarios. A continuación, se describe su estructura y elementos clave.


### 1. Declaración XML
La declaración XML es opcional, pero se recomienda incluirla al inicio del documento para especificar la versión de XML y la codificación de caracteres.

**Ejemplo:**
```xml
<?xml version="1.0" encoding="UTF-8"?>
```

#### Importancia de especificar la codificación de caracteres

Especificar la codificación de caracteres en un documento XML es crucial porque garantiza que el contenido del documento sea interpretado correctamente por los sistemas que lo procesan. 

Cada carácter en un documento tiene un **código numérico** que depende de la codificación utilizada (por ejemplo, UTF-8, ISO-8859-1, etc.). Si un sistema interpreta un archivo con una codificación diferente a la utilizada al crearlo, algunos caracteres podrían aparecer como símbolos extraños o causar errores de lectura.

**Ejemplo:** Un carácter especial como ñ en UTF-8 se representa de forma diferente en ISO-8859-1.
Sin la codificación adecuada, un texto como "mañana" podría mostrarse incorrectamente como "maÃ±ana".

### 2. Elemento raíz
Todo documento XML debe tener un único **elemento raíz** que contenga todos los demás elementos.

**Ejemplo:**
```xml
<tienda>
    ...
</tienda>
```

En este caso, `<tienda>` es el elemento raíz que engloba todo el contenido del documento.

### 3. Elementos

Los elementos son las **etiquetas** que estructuran los datos. Los elementos pueden contener otros elementos, texto o ambos.

**Ejemplo:**
```xml
<producto>
    <nombre>Televisor</nombre>
    <precio>450.00</precio>
</producto>
```

- `<producto>` es el elemento que contiene otros elementos (`<nombre>` y `<precio>`).


### 4. Atributos

Los atributos proporcionan **información adicional** sobre un elemento y están definidos dentro de la **etiqueta de apertura**.

**Ejemplo:**
```xml
<producto id="101" categoria="electrodomestico">
    <nombre>Televisor</nombre>
    <precio moneda="USD">450.00</precio>
</producto>
```

- `id` y `categoria` son atributos del elemento `<producto>`.
- `moneda` es un atributo del elemento `<precio>`.


### 5. Contenido de texto
Los elementos pueden contener texto como contenido del mismo.

**Ejemplo:**
```xml
<descripcion>Un televisor de alta definición de 55 pulgadas.</descripcion>
```



### 6. Espacios en blanco y formato
XML es sensible a los espacios en blanco dentro del contenido de texto, pero ignora los espacios usados para dar formato al documento.

**Ejemplo (formato legible):**
```xml
<producto>
    <nombre>Televisor</nombre>
    <precio>450.00</precio>
</producto>
```



### 7. Comentarios
Los comentarios se utilizan para agregar notas en el documento que no serán procesadas por los programas.

**Ejemplo:**
```xml
<!-- Este es un catálogo de productos -->
<tienda>
    <producto>
        <nombre>Televisor</nombre>
        <precio>450.00</precio>
    </producto>
</tienda>
```



### 8. Estructura completa de un documento XML
**Ejemplo:**
```xml
<?xml version="1.0" encoding="UTF-8"?>
<tienda>
    <!-- Lista de productos disponibles -->
    <producto id="101" categoria="electrodomestico">
        <nombre>Televisor</nombre>
        <descripcion>Un televisor de alta definición de 55 pulgadas.</descripcion>
        <precio moneda="USD">450.00</precio>
    </producto>
    <producto id="102" categoria="electrodomestico">
        <nombre>Licuadora</nombre>
        <descripcion>Licuadora de 10 velocidades.</descripcion>
        <precio moneda="USD">35.99</precio>
    </producto>
</tienda>
```

## Reglas documento XML bien formado

Un documento XML se considera **bien formado** cuando cumple con las reglas sintácticas definidas por la especificación de XML. Estas reglas garantizan que el documento sea legible y procesable por cualquier parser XML compatible. A continuación, se describen las principales características que debe cumplir un documento XML bien formado:

### 1. Una única etiqueta raíz
- Todo el contenido del documento debe estar contenido dentro de un único elemento raíz.
- **Ejemplo correcto:**
  ```xml
  <catalogo>
      <producto>
          <nombre>Televisor</nombre>
      </producto>
  </catalogo>
  ```
- **Ejemplo incorrecto (sin única raíz):**
  ```xml
  <producto>
      <nombre>Televisor</nombre>
  </producto>
  <producto>
      <nombre>Licuadora</nombre>
  </producto>
  ```


### 2. Todas las etiquetas deben estar correctamente cerradas
- Cada etiqueta de apertura debe tener una etiqueta de cierre correspondiente.
- **Ejemplo correcto:**
  ```xml
  <nombre>Televisor</nombre>
  ```
- **Ejemplo incorrecto (etiqueta sin cerrar):**
  ```xml
  <nombre>Televisor
  ```


### 3. Las etiquetas deben estar correctamente anidadas
- Las etiquetas deben abrirse y cerrarse en el orden correcto, respetando la jerarquía.
- **Ejemplo correcto:**
  ```xml
  <producto>
      <nombre>Televisor</nombre>
      <precio>450.00</precio>
  </producto>
  ```
- **Ejemplo incorrecto (etiquetas mal anidadas):**
  ```xml
  <producto>
      <nombre>Televisor</precio>
      <precio>450.00</nombre>
  </producto>
  ```


### 4. Diferenciación entre mayúsculas y minúsculas
- XML es sensible a las mayúsculas y minúsculas. Las etiquetas deben coincidir exactamente en su apertura y cierre.
- **Ejemplo correcto:**
  ```xml
  <Nombre>Televisor</Nombre>
  ```
- **Ejemplo incorrecto (diferencia en mayúsculas/minúsculas):**
  ```xml
  <Nombre>Televisor</nombre>
  ```


### 5. Los atributos deben estar correctamente formateados
- Los atributos de los elementos deben:
  - Usar comillas (`"` o `'`) para delimitar los valores.
  - No repetirse dentro de un mismo elemento.
- **Ejemplo correcto:**
  ```xml
  <producto id="101" categoria="electrodomestico" />
  ```
- **Ejemplo incorrecto (falta de comillas):**
  ```xml
  <producto id=101 categoria=electrodomestico />
  ```


### 6. Caracteres especiales deben ser escapados
- Algunos caracteres tienen un significado especial en XML y deben ser escapados si se utilizan como texto.
- **Ejemplo correcto:**
  ```xml
  <descripcion>Televisor de 55 pulgadas &amp; alta definición.</descripcion>
  ```
- **Ejemplo incorrecto (sin escapar):**
  ```xml
  <descripcion>Televisor de 55 pulgadas & alta definición.</descripcion>
  ```


### 7. Declaración XML (opcional pero recomendada)
- Aunque no es estrictamente necesaria, incluir la declaración XML al inicio del documento es una buena práctica.
- **Ejemplo:**
  ```xml
  <?xml version="1.0" encoding="UTF-8"?>
  ```

---

### 8. Prohibido el contenido fuera de la raíz
- No debe haber texto o contenido fuera del elemento raíz.
- **Ejemplo incorrecto:**
  ```xml
  Texto fuera de la raíz.
  <catalogo>
      <producto>
          <nombre>Televisor</nombre>
      </producto>
  </catalogo>
  ```



### Actividad 1

El siguiente documento no cumple con las reglas de un documento XML bien formado.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<catalogo>
    <producto id=201>
        <Nombre>Televisor</nombre>
        <precio moneda="USD">450.00</precio>
        <descripcion>Televisor de alta definición de 55 pulgadas</descripcion>
    <producto>
    <producto id=202>
        <nombre>Licuadora</nombre>
        <precio moneda="USD">35.99</precio
        <descripcion>Licuadora de 10 velocidades.</descripcion>
    </producto>
    <producto id=203>
        <nombre>Refrigerador</nombre>
        <descripcion>Refrigerador de dos puertas.
    </producto>
```

a) Localiza los errores y descríbelos:

b) Inserta a continuación el documento corregido:

```xml
```