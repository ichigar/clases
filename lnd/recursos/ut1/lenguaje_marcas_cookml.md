# Ejmplo de lenguaje de marcas de recetas de cocina
## Características del lenguaje de marcas:
* Nombre: **CookML**
* Extensión que tendrán los ficheros de este lenguaje de marcas: **.cml**
* Tipo de lenguaje de marcas: intercambio de informacion

## Estructura de etiquetas del lenguaje de marcas
```
recetario/
│
├── receta/
│   ├── titulo
│   ├── metadatos/
│   │   ├── autor
│   │   ├── porciones
│   │   ├── tiempoPreparacion
│   │   └── dificultad
│   ├── ingredientes/
│   │   ├── ingrediente (cantidad="")
│   │   ├── ingrediente (cantidad="")
│   │   └── ... 
│   ├── utensilios/
│   │   ├── utensilio
│   │   ├── utensilio
│   │   └── ...
│   └── instrucciones/
│       ├── paso (tiempo="") (opcional)
│       │   └── descripcion
│       ├── paso (tiempo="") (opcional)
│       │   └── descripcion
│       └── ... 
│
├── receta/  (Segunda receta)
│   ├── titulo
│   ├── metadatos/
│   │   ├── autor
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
│       ├── paso (tiempo="") (opcional)
│       │   └── descripcion
│       ├── paso (tiempo="") (opcional)
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
            <tiempoPreparacion>15 min</tiempoPreparacion>
            <dificultad>Fácil</dificultad>
        </metadatos>

        <ingredientes>
            <ingrediente cantidad="500g">Spaghetti</ingrediente>
            <ingrediente cantidad="400g">Carne molida</ingrediente>
            <ingrediente cantidad="2">Tomates</ingrediente>
            <ingrediente cantidad="1">Cebolla</ingrediente>
            <ingrediente cantidad="2 dientes">Ajo</ingrediente>
            <ingrediente cantidad="100ml">Aceite de oliva</ingrediente>
            <ingrediente cantidad="Sal">Al gusto</ingrediente>
            <ingrediente cantidad="Pimienta">Al gusto</ingrediente>
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
                <descripcion>Agregar la cebolla y el ajo picados, cocinar hasta que estén dorados.</descripcion>
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

        <informacionNutricional>
            <calorias>650 kcal</calorias>
            <proteinas>30g</proteinas>
            <carbohidratos>80g</carbohidratos>
            <grasas>20g</grasas>
        </informacionNutricional>
    </receta>

    <receta>
        <titulo>Ensalada César</titulo>

        <metadatos>
            <autor>María López</autor>
            <tiempoPreparacion>10 min</tiempoPreparacion>
            <dificultad>Fácil</dificultad>
        </metadatos>

        <ingredientes>
            <ingrediente cantidad="1">Lechuga romana</ingrediente>
            <ingrediente cantidad="100g">Pechuga de pollo</ingrediente>
            <ingrediente cantidad="50g">Queso parmesano</ingrediente>
            <ingrediente cantidad="100g">Crutones</ingrediente>
            <ingrediente cantidad="50ml">Aderezo César</ingrediente>
            <ingrediente cantidad="Sal">Al gusto</ingrediente>
            <ingrediente cantidad="Pimienta">Al gusto</ingrediente>
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
                <descripcion>Mezclar la lechuga, el pollo, los crutones y el queso en la ensaladera.</descripcion>
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
