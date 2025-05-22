# Etiquetado cableado estructurado de red local

En una **red local que solo incluye cableado horizontal**, el **etiquetado de todos sus elementos** es esencial para la **gestión, mantenimiento, resolución de incidencias y ampliaciones futuras**. 

La **normativa principal** que regula el **etiquetado de infraestructuras de red** es la:

## TIA/EIA-606-B – Administración de infraestructuras de telecomunicaciones

Esta norma es la más completa y ampliamente aceptada para el **etiquetado de elementos de redes de telecomunicaciones**, incluyendo redes con solo cableado horizontal.



## Elementos que deben etiquetarse y su normativa

| Elemento                                   | Norma aplicable               | Requisitos de etiquetado principales                                     |
| ------------------------------------------ | ----------------------------- | ------------------------------------------------------------------------ |
| **Tomas de red (RJ-45)**                   | TIA/EIA-606-B, UNE-EN 50174-2 | Etiqueta visible, única, permanente. Ej: A01, B02…                       |
| **Paneles de parcheo**                     | TIA/EIA-606-B, UNE-EN 50173-1 | Cada puerto etiquetado con el código de la toma correspondiente          |
| **Cables (horizontal)**                    | TIA/EIA-606-B                 | Etiquetados en ambos extremos con el mismo código que la toma            |
| **Latiguillos**                            | TIA/EIA-606-B (recomendado)   | Etiqueta opcional, útil para trazabilidad en racks                       |
| **Puntos de consolidación (si hay)**       | TIA/EIA-606-B                 | Identificador único, documentado y referenciado                          |
| **Armario mural o punto de concentración** | TIA/EIA-606-B                 | Etiquetado general (Ej: Rack-01, Mural-02), visible y vinculado al plano |
| **Canalizaciones**                         | UNE-EN 50174-2                | Etiquetadas según uso: datos, eléctrica, voz, etc.                       |


## Requisitos generales del etiquetado según TIA/EIA-606-B

1. **Identificación única**

   * Cada elemento debe tener un **código irrepetible** dentro de la instalación.

2. **Ubicación visible y permanente**

   * Las etiquetas deben estar colocadas en un lugar **fácilmente legible** y **resistentes al desgaste**.

3. **Formato estandarizado**

   * Se recomienda un sistema estructurado como:

     * `TXX-RYY-PZZ` donde:

       * T = tipo de elemento (Toma, Patch, Cable...)
       * R = ubicación o rack
       * P = puerto o posición

4. **Documentación obligatoria**

   * El sistema de etiquetado debe ir acompañado de:

     * **Plano de red**
     * **Tabla de correspondencias**
     * **Registro de conexiones**



## Resumen de normativa para etiquetado en red con solo cableado horizontal

| Norma              | Ámbito                            | Aplicación práctica                                           |
| ------------------ | --------------------------------- | ------------------------------------------------------------- |
| **TIA/EIA-606-B**  | Etiquetado y administración       | Identificación única, visible, documentada, trazable          |
| **UNE-EN 50174-2** | Instalación y señalización física | Identificación en canalizaciones, registros y puntos visibles |
| **UNE-EN 50173-1** | Diseño de cableado                | Correspondencia entre panel, toma y cableado documentada      |


## Buenas prácticas complementarias

* Usa etiquetas de **impresión térmica o láser**, resistentes al calor y al roce.
* Aplica etiquetas también en la **parte posterior del patch panel**.
* Mantén un **registro digital (Excel, PDF o software de gestión)** de toda la infraestructura.

Perfecto. A continuación te presento una **plantilla de etiquetado estandarizado** para una instalación de red **con solo cableado horizontal**, siguiendo la norma **TIA/EIA-606-B** y buenas prácticas de la **UNE-EN 50174-2**. Puedes adaptarla según tus zonas, racks y número de tomas.



## Plantilla de Etiquetado para Red con Cableado Horizontal

### Convención de nombres sugerida

* `TXX` = Toma de red
* `PXX` = Puerto del patch panel
* `CXX` = Cable horizontal
* `ZXX` = Zona o habitación
* Ejemplo completo: **T-Z01-01**, **P-Z01-01**, **C-Z01-01**



### Ejemplo de tabla de correspondencias

| Nº | Zona / Ubicación     | Toma de red (RJ-45) | Puerto en patch panel | Código de cable horizontal | Observaciones     |
| -- | -------------------- | ------------------- | --------------------- | -------------------------- | ----------------- |
| 1  | Oficina A – Puesto 1 | **T-Z01-01**        | **P-Z01-01**          | **C-Z01-01**               | PC Administración |
| 2  | Oficina A – Puesto 2 | **T-Z01-02**        | **P-Z01-02**          | **C-Z01-02**               | Teléfono IP       |
| 3  | Sala Reunión         | **T-Z02-01**        | **P-Z02-01**          | **C-Z02-01**               | Videoconferencia  |
| 4  | Aula TIC – Puesto 1  | **T-Z03-01**        | **P-Z03-01**          | **C-Z03-01**               | Estudiante A      |
| …  | …                    | …                   | …                     | …                          | …                 |


### Etiquetado físico

| Elemento              | Ubicación de etiqueta               | Formato sugerido     |
| --------------------- | ----------------------------------- | -------------------- |
| Toma de red (RJ-45)   | Placa frontal                       | `T-ZXX-YY`           |
| Puerto en patch panel | Frontal del panel debajo del puerto | `P-ZXX-YY`           |
| Cable horizontal      | En ambos extremos (panel y toma)    | `C-ZXX-YY`           |
| Canaleta (opcional)   | Inicio/final del tramo              | “Canaleta Datos Z01” |


### Documentación complementaria (recomendada)

* Plano de red con la **ubicación física de todas las tomas**.
* Lista completa de correspondencias.
* Etiquetas impresas térmicamente o con impresora de etiquetas.
* Archivo digital (Excel/PDF) para mantenimiento y auditoría.

Aquí tienes un **ejemplo de tabla en formato Markdown** con el **etiquetado de todos los elementos** de una red local pequeña (solo cableado horizontal), siguiendo la normativa UNE-EN 50174 y la estructura de TIA/EIA-606-B.



## Supuesto: Red local de un local comercial con 3 zonas

* **Z01** – Oficina principal (2 puestos)
* **Z02** – Sala de reuniones (1 puesto)
* **Z03** – Recepción (1 puesto)

Se instalan 2 tomas por puesto (voz y datos), conectadas a un **panel de parcheo de 12 puertos** en un **armario mural** (Rack-01).



### Tabla de etiquetas


| Nº | Zona       | Código de Toma | Código de Panel | Código de Cable | Ubicación Física              | Observaciones           |
|----|------------|----------------|------------------|------------------|-------------------------------|--------------------------|
| 1  | Z01        | T-Z01-01        | P-Z01-01         | C-Z01-01         | Oficina Principal - Puesto 1A | Datos PC                 |
| 2  | Z01        | T-Z01-02        | P-Z01-02         | C-Z01-02         | Oficina Principal - Puesto 1A | Voz Teléfono IP          |
| 3  | Z01        | T-Z01-03        | P-Z01-03         | C-Z01-03         | Oficina Principal - Puesto 1B | Datos PC                 |
| 4  | Z01        | T-Z01-04        | P-Z01-04         | C-Z01-04         | Oficina Principal - Puesto 1B | Voz Teléfono IP          |
| 5  | Z02        | T-Z02-01        | P-Z02-01         | C-Z02-01         | Sala de Reuniones - Mesa      | Datos portátil           |
| 6  | Z02        | T-Z02-02        | P-Z02-02         | C-Z02-02         | Sala de Reuniones - Mesa      | Teléfono IP              |
| 7  | Z03        | T-Z03-01        | P-Z03-01         | C-Z03-01         | Recepción - Mostrador         | Datos PC recepción       |
| 8  | Z03        | T-Z03-02        | P-Z03-02         | C-Z03-02         | Recepción - Mostrador         | Teléfono IP              |




### Codificación usada

* `T-ZXX-YY` = **Toma** en la zona ZXX, número correlativo.
* `P-ZXX-YY` = **Puerto de panel** que corresponde a esa toma.
* `C-ZXX-YY` = **Cable horizontal** que conecta esa toma al panel.
* La codificación es **única, clara y rastreable**, como exige la norma.




