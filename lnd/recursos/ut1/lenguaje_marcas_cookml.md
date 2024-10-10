# Ejmplo de lenguaje de marcas de recetario de cocina
## Especificaciones del lenguaje de marcas:
* Nombre: **RecetarioML**
* Extensión que tendrán los ficheros de este lenguaje de marcas: **.rml**
* Tipo de lenguaje de marcas: intercambio de informacion

## Descripción

Este lenguaje de marcas se utilizará para codificar un recetario de cocina. 
* El recetario consiste en una serie de recetas individuales
* Cada receta debe tener
  * título
  * metadatos (descripción general de la misma)
    * Los metadatos deben incluir: el autor, el número de porciones/raciones de la receta, el tiempo total de preparación y la dificultad.
  * ingredientes
    * Los ingredientes se incluyen en una secuencia de ingredientes individuales, cada uno de ellos tiene un atributo con la cantidad y dentro de la etiqueta aparece el nombre del ingrediente.
  * utensilios para prepararla
    * Los utensilios son las herramientas de cocina necesarias para elaborar la receta
  * instrucciones. Las instrucciones son opcionales, el resto de elementos son obligatorios.
    * Las instrucciones incluyen de forma ordenada los pasos necesarios para elaborar la receta. Las instrucciones son opcionales. Cada paso incluye en la etiqueta su descripción y un atributo tiempo con los minutos necesarios. El tiempo de cada paso es opcional.


## Estructura de etiquetas del lenguaje de marcas y valores permitidos
```
recetario/
│
├── receta/
│   ├── titulo - Cadena de texto
│   ├── metadatos/
│   │   ├── autor - Cadena de texto
│   │   ├── porciones - Número entero
│   │   ├── tiempoPreparacion - Número entero
│   │   └── dificultad - valores("Fácil", "Medio", "Difícil")
│   ├── ingredientes/
│   │   ├── ingrediente (cantidad="") - ingrediente cadena de texto, atributo cantidad cadena de texto
│   │   ├── ingrediente (cantidad="")
│   │   └── ... 
│   ├── utensilios/
│   │   ├── utensilio - cadena de texto
│   │   ├── utensilio
│   │   └── ...
│   └── instrucciones/ (opcional)
│       ├── paso (tiempo="") - paso cadena de texto, atributo número entero de minutos entre comillas
│       │   └── descripcion
│       ├── paso (tiempo="") 
│       │   └── descripcion
│       └── ... 
│
├── receta/  (Segunda receta)
│   ├── titulo
│   ├── metadatos/
│   │   ├── autor
│   │   ├── porciones
│   │   ├── tiempoPreparacion
│   │   └── cocina
│   ├── ingredientes/
│   │   ├── ingrediente (cantidad="")
│   │   ├── ingrediente (cantidad="")
│   │   └── ... 
│   ├── utensilios/
│   │   ├── utensilio
│   │   ├── utensilio
│   │   └── ...
│   └── instrucciones/
│       ├── paso (tiempo="") 
│       │   └── descripcion
│       ├── paso (tiempo="") 
│       │   └── descripcion
│       └── ... 
│
└── ... (Se pueden añadir más recetas aquí)

```
## Ejemplo de documento

```
<recetario>
    <receta>
        <titulo>Spaghetti a la Boloñesa</titulo>        
        <metadatos>
            <autor>Juan Pérez</autor>
            <porciones>4</porciones>
            <tiempoPreparacion>15</tiempoPreparacion>
            <dificultad>Fácil</dificultad>
        </metadatos>

        <ingredientes>
            <ingrediente cantidad="500g">Spaghetti</ingrediente>
            <ingrediente cantidad="400g">Carne molida</ingrediente>
            <ingrediente cantidad="2">Tomates</ingrediente>
            <ingrediente cantidad="1">Cebolla</ingrediente>
            <ingrediente cantidad="100ml">Aceite de oliva</ingrediente>
            <ingrediente cantidad="Al gusto">Sal</ingrediente>
            <ingrediente cantidad="Al gusto">Pimienta</ingrediente>
        </ingredientes>

        <utensilios>
            <utensilio>Sartén</utensilio>
            <utensilio>Olla</utensilio>
            <utensilio>Cuchillo</utensilio>
            <utensilio>Tabla de cortar</utensilio>
        </utensilios>

        <instrucciones>
            <paso tiempo="5 min">
                <descripcion>Calentar el aceite en una sartén a fuego medio.</descripcion>
            </paso>
            <paso tiempo="10 min">
                <descripcion>Agregar la cebolla cocinar hasta que estén dorados.</descripcion>
            </paso>
            <paso tiempo="15 min">
                <descripcion>Incorporar la carne molida y cocinar hasta que se dore completamente.</descripcion>
            </paso>
            <paso tiempo="10 min">
                <descripcion>Añadir los tomates picados, la sal y la pimienta. Cocinar a fuego lento.</descripcion>
            </paso>
            <paso tiempo="8 min">
                <descripcion>Hervir el spaghetti en una olla con agua y sal.</descripcion>
            </paso>
            <paso>
                <descripcion>Mezclar la salsa boloñesa con el spaghetti cocido. Servir caliente.</descripcion>
            </paso>
        </instrucciones>

    </receta>

    <receta>
        <titulo>Ensalada César</titulo>

        <metadatos>
            <autor>María López</autor>
            <porciones>2</porciones>
            <tiempoPreparacion>10</tiempoPreparacion>
            <dificultad>Fácil</dificultad>
        </metadatos>

        <ingredientes>
            <ingrediente cantidad="1">Lechuga romana</ingrediente>
            <ingrediente cantidad="100g">Pechuga de pollo</ingrediente>
            <ingrediente cantidad="50g">Queso parmesano</ingrediente>
            <ingrediente cantidad="50ml">Aderezo César</ingrediente>
            <ingrediente cantidad="Al gusto">Sal</ingrediente>
            <ingrediente cantidad="Al gusto">Pimienta</ingrediente>
        </ingredientes>

        <utensilios>
            <utensilio>Ensaladera</utensilio>
            <utensilio>Cuchillo</utensilio>
            <utensilio>Sartén</utensilio>
        </utensilios>

        <instrucciones>
            <paso tiempo="5 min">
                <descripcion>Cortar la lechuga y el pollo en tiras.</descripcion>
            </paso>
            <paso tiempo="5 min">
                <descripcion>Saltear el pollo en una sartén con un poco de sal y pimienta.</descripcion>
            </paso>
            <paso>
                <descripcion>Mezclar la lechuga, el pollo y el queso en la ensaladera.</descripcion>
            </paso>
            <paso>
                <descripcion>Agregar el aderezo César y mezclar bien. Servir frío.</descripcion>
            </paso>
        </instrucciones>
    </receta>
</recetario>

```

Etiquetas permitidas y su descripción
Valores permitidos para dichas etiquetas (Ejemplo enteros del 1 al 10, números realies, cadena de 5 a 100 caracteres de longitud, ...)
