# Introducción a JSON como Lenguaje de Marcas

## Definición

**JSON (JavaScript Object Notation)** es un **formato ligero de intercambio de datos** que se utiliza para transmitir información entre sistemas. Fue diseñado para ser fácil de leer y escribir tanto por humanos como por máquinas, lo que lo hace ideal para la comunicación web, configuraciones de software y almacenamiento de datos estructurados.

## Usos Comunes

**JSON** se usa en múltiples ámbitos, algunos de los más comunes son:

   - **APIs Web**: La comunicación entre clientes web (front-end) y servidores backend a través de peticiones HTTP.
   - **Configuraciones de Software**: Almacenamiento de configuraciones de aplicaciones en formatos JSON.
   - **Base de Datos NoSQL**: Representación y almacenamiento de datos estructurados en bases de datos no relacionales como MongoDB.
   - **Almacenamiento Local**: Guardado de datos en formato JSON para uso local, especialmente en aplicaciones web.

## Principales Características de JSON:

### Sintaxis Sencilla

- Todos los elementos de un documento **json** se definen dentro de 1 par de llaves `{}` y van separados por comas `,`.
```json
{
    elementos del documento json
}
```
- Los elementos de un documento **json** pueden ser **objetos** o **arrays**

- Los objetos se representan como pares **clave-valor** separados por comas, encerrados entre llaves `{}`.

**Ejemplo de objetos:**

```json
{
  "nombre": "John Doe",
  "edad": 30
}
```
- Los **arrays** se representan como listas ordenadas de valores separados por comas, encerrados entre corchetes `[]

**Ejemplo de arrays**

```json
{
    "materias": ["Matemáticas", "Historia"]
}
```

- JSON permite estructuras anidadas tanto en los objetos como en los arrays, lo que facilita el representación de datos complejos. Esto quiere decir, que los valores de un objeto o array pueden ser a su vez objetos o arrays.


**Ejemplo 1**:

   ```json
   {
     "nombre": "John Doe",
     "edad": 30,
     "isStudent": false,
     "materias": ["Matemáticas", "Historia"],
     "direccion": {
       "calle": "Avenida Principal",
       "numero": "1234"
     }
   }
   ```
**Ejemplo 2**

   ```json
   {
  "nombre": "John Doe",
  "edad": 30,
  "isStudent": false,
  "materias": [
    {
      "nombre": "Matemáticas",
      "profesor": "Juan Pérez"
    },
    {
      "nombre": "Historia",
      "profesor": "María López"
    }
  ],
  "dirección": {
    "calle": "Avenida Principal",
    "numero": "1234",
    "ciudad": {
      "nombre": "Madrid",
      "pais": "España"
    },
    "coordenadas": [40.7128, -74.0060]
  }
}
```

### Tipos de Datos Soportados para los valores:
   - **String**: Cadenas de texto encerrados en comillas dobles (`"string"`).
   - **Number**: Números enteros y decimales.
   - **Object**: Un objeto es una colección de pares clave-valor `{ "key1": value1, "key2": value2 }`.
   - **Array**: Una lista ordenada de valores `[value1, value2, value3]`.
   - **Boolean**: Valores booleanos `true` o `false`.
   - **Null**: El valor nulo `null`. Se utiliza para indicar que no tiene ningún valor o valor nulo.

| Tipo         | Ejemplo                        |
|--------------|--------------------------------|
| String       | `"Hola mundo"`                 |
| Number       | `123`, `3.14`                  |
| Boolean      | `true`, `false`                |
| Null         | `null`                         |
| Array        | `["a", "b", "c"]`              |
| Object       | `{"clave": "valor"}`           |

### Uso de comillas en cadenas de texto (string)

En JSON, los valores de tipo string deben ir siempre entre comillas dobles ("), y si dentro del texto también necesitas poner comillas dobles, debes escaparlas con una barra invertida (\).

**Ejemplo**

```json
{
  "frase": "Ella dijo: \"Hola, ¿cómo estás?\""
}
```

En este caso, el valor de "frase" contiene comillas dobles internas, y para que no rompan la estructura JSON, se escriben como `\"`.

**Ejemplo incorrecto (esto daría error al procesarlo)**

```json
{
  "frase": "Ella dijo: "Hola, ¿cómo estás?""
}
```

Esto es inválido porque el analizador JSON se confundiría al ver las comillas dobles sin escapar.

### Ventajas de JSON:

- **Simplicidad**: La sintaxis es sencilla y fácil de aprender.
- **Portabilidad**: Puede ser utilizado en prácticamente cualquier lenguaje de programación.
- **Legibilidad**: Es fácil de leer tanto por humanos como por máquinas.
- **Estandarizado**: Tiene un estándar globalmente aceptado.

### Desventajas de JSON:

- **Limitaciones Tipográficas**: Los valores de cadena deben ser encerrados en comillas dobles (`"`), lo que puede causar problemas con datos que contienen  a su vez comillas dobles.
- **No Soporta Tipos Especiales**: No hay soporte directo para tipos especiales como `Date`, `Blob`, o referencias a objetos.


### Comparativa con XML

**Ventajas de JSON sobre XML**

- Menor peso que XML.
- Sintaxis clara y concisa.
- Compatible con la mayoría de lenguajes de programación.
- Muy usado en APIs REST.

**Desventajas de JSON respecto a XML**

- No soporta comentarios.
- Menos flexible que XML en estructuras muy complejas.
- No permite definir esquemas tan formales como DTD o XSD en XML (aunque existen alternativas como JSON Schema).

| Característica       | JSON                    | XML                       |
|----------------------|-------------------------|---------------------------|
| Sintaxis             | Más simple              | Más compleja              |
| Tamaño               | Más ligero              | Más pesado                |
| Lectura humana       | Más fácil               | Menos intuitiva           |
| Estructura           | Clave-valor             | Basada en etiquetas       |
| Velocidad de análisis| Más rápida              | Más lenta                |

### Validación de json

Los editores de código suelen incluir herramientas o plugins para validar que un documento json esté bien construido.

También existen herramientas online como <https://jsonlint.com/> que nos permiten validar un documento json y mostrarnos los errores de sintaxis en caso de que no sea válido.




