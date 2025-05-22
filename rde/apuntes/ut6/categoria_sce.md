# Categoría y clases del sistema de cableado estructurado de una LAN

En una **instalación de cableado estructurado** de una **red local (LAN)**, la **categoría** se refiere a una **clasificación técnica estandarizada** que indica el **rendimiento eléctrico y de transmisión** que debe tener **cada componente del sistema** (cables, conectores, patch panels, tomas RJ-45, latiguillos, etc.).


## Categoría en el cableado estructurado

La **categoría (o "Cat")** determina:

* La **frecuencia máxima de operación** (en MHz).
* La **velocidad máxima de transmisión de datos** (Mbps o Gbps).
* La **calidad y el nivel de interferencias** que puede soportar.
* La **compatibilidad** con estándares de red como Ethernet (10/100/1000/10G).


## Componentes afectados por la categoría

Para que un canal funcione correctamente, **todos los componentes deben ser de la misma categoría o superior**. Los elementos del SCE que determinan la categoría son:

- Cable UTP/FTP
- Patch panel
- Tomas de red RJ-45
- Latiguillos (patch cords)
- Conectores 

Si alguno de los elementos tiene una categoría inferior al resto, toda la instalación será de la categoría de dicho elemento.

Así, si todos los elementos de una instalalación de SCE son de categoría 6, pero los patch panels son de categoría 5e, dicha instalación se certificaría como de categoría **5e**.

## Categorías más comunes en instalaciones actuales**

| Categoría  | Frecuencia | Velocidad máxima                            | Uso típico en LANs               |
| ---------- | ---------- | ------------------------------------------- | -------------------------------- |
| **Cat 5e** | 100 MHz    | 1 Gbps (Gigabit Ethernet)                   | Instalaciones antiguas o básicas |
| **Cat 6**  | 250 MHz    | 1 Gbps (hasta 100 m) o 10 Gbps (hasta 55 m) | Estándar actual                  |
| **Cat 6A** | 500 MHz    | 10 Gbps (hasta 100 m)                       | Redes de alto rendimiento        |
| **Cat 7**  | 600 MHz    | 10 Gbps (mejor apantallado)                 | Uso específico, menos habitual   |
| **Cat 8**  | 2000 MHz   | Hasta 40 Gbps (≤30 m)                       | Centros de datos                 |


## Clases en un SCE

En la **normativa europea e internacional** (como **UNE-EN 50173** e **ISO/IEC 11801**), el sistema de cableado estructurado **no se clasifica por "categorías"**, sino por **clases de canal** (Clase C, D, E, EA, F, FA, I, II). Sin embargo, en la **práctica profesional**, ambas denominaciones se **usan de forma complementaria**.

### Diferencias entre clase y categoría

* **Categoría (Cat)** → Se refiere a **componentes individuales**: cables, conectores, tomas, etc.
* **Clase (Clase)** → Se refiere al **canal completo de transmisión**: desde el patch panel hasta la toma de usuario.

### Tabla de equivalencia entre Categorías y Clases (según ISO/IEC 11801 y UNE-EN 50173-1)

| **Clase (canal)** | **Categoría mínima de componentes** | **Frecuencia máx.** | **Velocidad**            | Uso práctico            |
| ----------------- | ----------------------------------- | ------------------- | ------------------------ | ----------------------- |
| **Clase C**       | Cat 3                               | 16 MHz              | 10 Mbps (Ethernet)       | Obsoleto                |
| **Clase D**       | Cat 5e                              | 100 MHz             | 100 Mbps – 1 Gbps        | Básico / aún en uso     |
| **Clase E**       | Cat 6                               | 250 MHz             | 1 Gbps – 10 Gbps (corto) | Estándar actual         |
| **Clase EA**      | Cat 6A                              | 500 MHz             | 10 Gbps (hasta 100 m)    | Muy común hoy           |
| **Clase F**       | Cat 7                               | 600 MHz             | 10 Gbps                  | Instalaciones exigentes |
| **Clase FA**      | Cat 7A                              | 1000 MHz            | ≥10 Gbps                 | Entornos especiales     |
| **Clase I**       | Cat 8.1                             | 2000 MHz            | 25/40 Gbps (≤30 m)       | Centros de datos        |
| **Clase II**      | Cat 8.2                             | 2000 MHz            | 25/40 Gbps (≤30 m)       | Muy alta velocidad      |

---

### Uso de clases

La clase de una instalación se usa **principalmente en documentación técnica, certificación y diseño de proyectos**. En obra, se habla más de "categorías" por simplicidad.

A la hora de certificar una instalación el informe indica la **clase del canal**.

Las **normas europeas como UNE-EN 50173 exigen especificar la clase**, no solo la categoría.


### Ejemplo práctico de uso combinado

* Un instalador compra **cables, conectores y tomas Cat 6A**.
* El canal completo es entonces de **Clase EA**.
* El certificador verifica si **todo el canal cumple Clase EA** según los requisitos normativos.

### Resumen

* **Clases = canal completo** (nivel normativo europeo).
* **Categorías = componentes** (nivel práctico en instalación).
* Se **complementan**, y **ambas deben coincidir** para garantizar el rendimiento de la red.



