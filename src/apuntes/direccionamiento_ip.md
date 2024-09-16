# Direcciones IP

## Conceptos básicos

Todo ordenador conectado a una red necesita estar perfectamente identificado a nivel de **capa 3**. Esta es la misión de las direcciones IP.

Una dirección IP es un número que identifica a una interfaz de un dispositivo dentro de una red que utilice el protocolo IP.

Una dirección IP se representa y se almacena internamente mediante un número binario de 32 bits (IPv4). Las direcciones IP se expresan nomalmente con una notación decimal con puntos: se dividen los 32 bits de la dirección en cuatro octetos de 8 bits cada uno separados por puntos. Esto se hace así porque a a nosotros, los humanos, nos resulta
más fácil entender la notación decimal con puntos que la binaria a base de unos y ceros. Estructura de una direccion IP

En la capa 3 se forman lo que se denomina redes IP o redes lógicas.
Estas redes se superponen a las redes físicas.

Una red física da lugar siempre a, al menos, una red lógica. No obstante, dentro de una red física puede haber más de una red lógica.

Dos ordenadores necesitan estar en la misma red lógica si quieren comunicarse directamente. En caso de estar en redes lógicas diferentes, su comunicación pasa a ser indirecta y sus mensajes han de pasar por, al menos, un **router**.

En consecuencia, cada direccion IP tiene dos partes. Una parte **identifica la red** a la que el sistema está conectado (parte de red) y una segunda parte identifica el sistema en particular dentro de dicha red (**parte de host**).

Al nombrar una dirección indicando la parte de red y rellenando con ceros la parte de host estaremos realmente refiriendonos a esa red por completo.

## Clases de direcciones IP

De este modo, los diseñadores del protocolo IP dividieron las
direcciones IP disponibles en varias clases.

Conocer la clase a la que pertenece una dirección IP es el primer paso para determinar qué parte de la dirección  identifica la red y qué parte identifica el host.

En una dirección IP un bit o una secuencia bits al principio de cada dirección permite identificar la clase a la que pertenece la misma. Hay 5 clases de direcciones IP.

### Direcciones de clase A

Las direcciones de clase A se diseñaron para ser utilizadas en redes extremadamente grandes. Todas las direcciones IP Clase A utilizan solamente los primeros 8 bits para identificar la parte de red de la dirección. Los tres octetos restantes se pueden utilizar para la parte de host de la dirección.

Cuando está escrito en formato binario, el primer bit (el bit que está ubicado más a la izquierda) de la dirección Clase A siempre es 0.

### Direcciones de clase B

Todas las direcciones IP Clase B utilizan los primeros 16 bits para identificar la parte de red de la dirección. Los dos octetos restantes de la dirección IP se encuentran reservados para la porción del host de la dirección.

Los primeros 2 bits de una dirección Clase B siempre son 10 (uno y cero).

### Direcciones de clase C

Todas las direcciones IP Clase C utilizan los primeros 24 bits para identificar la porción de red de la dirección. Sólo se puede utilizar el último octeto de una dirección IP Clase C para la parte de la dirección que corresponde al host.

Los 3 primeros bits de una dirección Clase C siempre son 110 (uno, uno y cero).

### Direcciones de clase D

Las direcciones de clase D se utilizan para direcciones especiales denominadas grupos de difusión. Los 4 primeros bits de una dirección de Clase D siempre son 1110 (uno, uno, uno y cero).

### Direcciones de clase E

Se han definido direcciones de clase E reservadas para investigación. 

Por tanto, las direcciones de clase E no pueden utilizarse en Internet.

Los primeros 4 bits de una dirección de Clase E siempre están
establecidos a 1.

## Direcciones IP reservadas

No todas las direcciones comprendidas entre la 0.0.0.0 y la
223.255.255.255 son válidas para ser asignadas a un host: algunas de ellas tienen significados especiales. Las principales direcciones especiales se resumen aqui:

-   **Todos los bits a 0**: no se le puede asignar a un host ya que se
    utilizada en circunstancias especiales por ciertos protocolos de
    red. Ejemplo: **0.0.0.0**
-   **Todos los bits a 1**: no se le puede asignar a un host ya que está
    reservada para usar como IP de destino en paquetes que se desea sean
    de **difusión o de broadcast** para todos los equipos de la LAN
    actual. Ejemplo: **255.255.255.255**
-   **Todos los bits de host a 0**: no se puede asignar a un host ya que
    es la dirección de la red correspondiente (digamos que es el nombre
    que se le asigna a la red correspondiente). Ejemplo: **176.10.0.0**
-   **Todos los bits de host a 1**: no se puede asignar a un host ya que
    está reservada para usar como IP de destino en paquetes que se
    desean sean de de difusión o de broadcast sobre la red especificada.
    Ejemplo: **172.10.255.255**
-   **Primer octeto a 01111111 (127 en decimal)**: no se puede asignar a
    un host ya que ciertas direcciones de esta red se usan para referise
    al propio host (dirección loopback). Ejemplo: **127.0.0.1**


**Nota: Difusión o broadcasting**, como ya hemos visto, es el envío de un mensaje a todos los ordenadores que se encuentran en una red.

**Nota: La dirección de loopback** (normalmente 127.0.0.1) es una dirección asignada por defecto a una tarjeta de red virtual que está presente en todos los ordenadores y que actúa como un circuito cerrado.
Cualquier paquete IP enviado por el ordenador por esta interfaz le será devuelto a esta.

## Direcciones IP públicas y privadas

Las **direcciones IP públicas** son únicas. No hay dos máquinas conectadas a Internet que tengan la misma dirección IP. No hay problemas de ordenadores con la misma IP porque las direcciones IP públicas las asigna la **ICANN**, un organismo internacional neutral.

Hay ciertas direcciones en cada clase de dirección IP que no están asignadas y que se denominan **direcciones privadas**. Las direcciones privadas pueden ser utilizadas por los hosts de aquellas redes de área local que usan traducción de dirección de red (**NAT**) o un **servidor proxy** para conectarse a Internet, o por los hosts de una red que no se
va a conectar a Internet.

Los diseñadores de IP apartaron 3 bloques de direcciones IP como direcciones privadas:

* Rango 1: todas las direcciones dentro de la red 10.0.0.0
* Rango 2: todas las direcciones dentro de las redes 172.16.0.0 - 172.31.0.0 ambas inclusive.
* Rango 3: todas las direcciones dentro de las redes 192.168.0.0 - 192.168.255.0 ambas inclusive.

## Mascaras de subred

Para que una computadora sepa más fácilmente cómo dividir una dirección IP de 32 bits en parte de red y parte de host se utiliza un segundo número de 32 bits denominado máscara de subred. Una máscara de subred tiene unos en los bits correspondientes a la parte de red y ceros en los bits correspondientes a la parte de host.

Las máscaras de red se expresan de dos formas: en **notación decimal** o en **notación de prefijo de red** (indicando tras la dirección mediante una barra el número de unos que tiene la máscara).

Las siguientes son las máscaras para las direcciones clase A, B. y C:

* Máscara para direcciones de clase A: 255.0.0.0 /8
* Máscara para direcciones de clase B: 255.255.0.0 /16
* Máscara para direcciones de clase C: 255.255.255.0 /24
