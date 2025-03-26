# RSS (Really Simple Syndication)

## Estructura de un feed RSS

Como hemos visto, un feed RSS es un archivo en formato XML con una estructura jerárquica. La versión más usada es RSS 2.0. A continuación, se muestra un ejemplo básico de un documento RSS:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<rss version="2.0">
  <channel>
    <title>Noticias Tecnológicas</title>
    <link>https://www.tecnonoticias.com/feed/rss.xml</link>
    <description>Últimas noticias sobre tecnología</description>
    <atom:link href="https://www.tecnonoticias.com/feed/rss.xml" rel="self" type="application/rss+xml" />
    <language>es</language>

    <item>
      <title>Nuevo iPhone lanzado</title>
      <link>https://www.tecnonoticias.com/iphone-nuevo</link>
      <description>Apple ha presentado su nuevo modelo de iPhone con increíbles novedades.</description>
      <pubDate>Fri, 28 Feb 2025 12:00:00 GMT</pubDate>
      <guid>https://www.tecnonoticias.com/iphone-nuevo</guid>
    </item>

    <item>
      <title>Microsoft lanza Windows 12</title>
      <link>https://www.tecnonoticias.com/windows-12</link>
      <description>Microsoft ha lanzado la nueva versión de su sistema operativo.</description>
      <pubDate>Fri, 28 Feb 2025 14:00:00 GMT</pubDate>
      <guid>https://www.tecnonoticias.com/windows-12</guid>
    </item>

  </channel>
</rss>
```

### Explicación de la estructura

- `<rss version="2.0">`: Indica la versión del estándar RSS utilizada.
- `<channel>`: Contenedor principal del feed que agrupa toda la información.
- `<title>`: Nombre del canal RSS.
- `<link>`: URL del fichero xml del RSS del canal.
- `<description>`: Descripción del contenido del canal.
- `<atom:link/>: se utiliza comúnmente para proporcionar un enlace al feed RSS en sí mismo. Esto es útil para que los lectores de feeds o las aplicaciones puedan identificar y acceder fácilmente al feed.
  - `href`: Especifica la URL del feed.
  - `rel="self"`: Indica que este enlace es una referencia al propio feed.
  - `type="application/rss+xml"`: Especifica el tipo MIME del feed.
- `<language>`: Código de idioma del feed.
- `<item>`: Cada entrada o actualización en el feed.
  - `<title>`: Título de la publicación.
  - `<link>`: Enlace al contenido completo.
  - `<description>`: Resumen o introducción del contenido.
  - `<pubDate>`: Fecha de publicación en formato RFC 822.
  - `<guid>`: Identificador único de la entrada. Para que el RSS sea válido se debe incluir este elemento. El contenido debe ser un identificador único que no se repita en ningún otro de los items del canal. Puede ser, por ejemplo, el título del elemento o el enlace al mismo.


## Suscribirse a un feed RSS
Para recibir actualizaciones mediante RSS, se necesita un lector RSS, también llamado agregador.

### Herramientas populares para leer RSS
🔹 Online: Feedly, Inoreader  
🔹 Extensiones de navegador: RSS Feed Reader, Feedbro  
🔹 Software de escritorio: QuiteRSS, RSSOwl  
🔹 Móviles: Flipboard, Podcast Addict  

### Pasos para suscribirse
1. Identificar la URL del feed RSS (normalmente indicada con un ícono naranja). Ejemplo: `https://www.tecnonoticias.com/rss.xml`
2. Copiar y pegar la URL en un lector RSS.
3. El lector mostrará las últimas publicaciones del sitio.
4. Cada vez que haya contenido nuevo, se actualizará automáticamente.

## Creación de un sitio web con un canal RSS
Para ofrecer un feed RSS en un sitio web, se debe generar un archivo XML que se actualice con cada nueva publicación.

Los pasos genéricos son:

1. Crear el archivo `rss.xml` con la estructura básica (como el ejemplo anterior).
2. Subirlo al servidor web en una ubicación accesible (`https://www.tusitio.com/feed/rss.xml`).
3. Agregar un enlace al feed en alguna de las secciones de la página web. Insertamos algo como:

```html
<body>

...
  <a href="https://www.tusitio.com/feed/rss.xml">
    <img src="rss-icon.png" alt="RSS Feed"> Suscribirse al RSS
  </a>

...
</body>
```

4. También se puede añadir un enlace en la cabecera del HTML para que los navegadores detecten automáticamente el feed:

```html
<head>

...  
  <link rel="alternate" type="application/rss+xml" title="Noticias Tecnológicas" href="https://www.tecnonoticias.com/feed/rss.xml">

...
</body>
```
## Elementos de los items de un canal RSS

### Incluyendo pistas de audio en el canal de un podcast

El XML de un canal RSS puede incluir elementos multimedia entre los contenidos de cada item. Esto permite que algunos lectores puedan reproducir dichos elementos desde el lector sin tener que abrirlos desde el navegador.

Si queremos incluir el fichero de audio de un podcast, añadimos algo como los siguiente al item:

```xml
<enclosure url="https://www.ejemplo.com/audio/episodio2.mp3" length="9876543" type="audio/mpeg"/>
```
Donde:
- `enclosure` es el elemento que utilizamos para indicar que estamos insertando el acceso a un elemento multimedia relacionado con el item.
- `url` este atributo permite def