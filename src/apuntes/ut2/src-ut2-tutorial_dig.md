# La herramienta dig

La herramienta dig nos permite hacer consultas consultas para obtener cualquier registro que nos interese. Resulta muy útil para comprobar el correcto funcionamiento del servicio de . En su uso más simple solicitamos un registro de tipo A a nuestros resolvers que tenemos la configuración de red de nuestro equipo

```
$ dig rediris.es                      

; <<>> DiG 9.18.28-0ubuntu0.24.04.1-Ubuntu <<>> rediris.es
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 64220
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 65494
;; QUESTION SECTION:
;rediris.es.			IN	A

;; ANSWER SECTION:
rediris.es.		5120	IN	A	130.206.13.20

;; Query time: 0 msec
;; SERVER: 127.0.0.53#53(127.0.0.53) (UDP)
;; WHEN: Sat Oct 19 22:46:33 WEST 2024
;; MSG SIZE  rcvd: 55
```

Obtenemos el **registro A** del nombre de dominio que hemos solicitado, o sea, la dirección IP del nombre de dominio proporcionado. 

Además se muestra otra información de forma detallada entre la que podemos destacar: 

- La petición que hemos realizado.
- Tiempo empleado en obtener la respuesta.
- Servidor de al que se le realiza la consulta

Si queremos que el resultado se muestre en formato corto y sólo nos muestre el resultado de la consulta realizada sin más detalle, añadimos a la petición la opción **+short** 

```bash
dig rediris.es +short
130.206.13.20
```

En el que caso de que queramos obtener un registro que no sea un registro A podemos especificarlo a continuación o mediante la opción **-t** 

Para obtener los registros MX de un dominio ejecutamos: 

```bash
$ dig rediris.es mx
```

o 

```bash
$ dig -t mx rediris.es
```

Para obtener los servidores de de un dominios 

```bash
$ dig rediris.es ns
```

Para obtener de quien es alias un nombre de dominio: 

```bash
$ dig www.elpais.com cname
```

Para obtener, en caso de que exista, la dirección IPv6 de un dominio ejecutamos: 

```bash
$ dig google.es aaaa
```

Si queremos realizar una resolución inversa, esto es, averiguar a que nombre de dominio apunta una determinada dirección IP utilizamos la opción **-x** 

```bash
$ dig -x 8.8.8.8
```

En el caso de que queramos preguntar a un determinado servidor de en lugar de a los que tenemos configurados como resolvers en el sistema operativo debemos usar la **@** para indicar el servidor. 

```bash
	$ dig lanzarote.com @8.8.4.4
```

Y por ultimo, si lo que queremos es que se nos muestre la información completa del registro  lo hacemos añadiendo las opciones +answer +noall

```bash
$ dig wikipedia.org A +noall +answer
wikipedia.org.		600	IN	A	91.198.174.192
```