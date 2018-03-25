## Servicios Web HTTP

#### Contexto

La web es un sistema masivo de información cliente / servidor distribuido como se muestra en el siguiente diagrama.


![alt text](https://github.com/pumanzor/linuxadmin/blob/master/imgs/TheWeb.png)

-----

Muchas aplicaciones se ejecutan de forma simultánea en la Web, como navegación web, correo electrónico, transferencia de archivos, transmisión de audio y video, etc. 

Para que se produzca una comunicación adecuada entre el cliente y el servidor, estas aplicaciones deben acordar un protocolo específico de nivel de aplicación, como HTTP, FTP, SMTP, POP, etc.

------

HTTP (Protocolo de transferencia de hipertexto) es quizás el protocolo de aplicación más popular utilizado en Internet (o The WEB).

HTTP es un protocolo de solicitud-respuesta cliente-servidor asimétrico como se ilustra en la imagen siguiente. Un cliente HTTP envía un mensaje de solicitud a un servidor HTTP. El servidor, a su vez, devuelve un mensaje de respuesta. En otras palabras, HTTP es un protocolo de extracción, el cliente extrae información del servidor (en lugar de que el servidor envíe información al cliente).

![alt text](https://github.com/pumanzor/linuxadmin/blob/master/imgs/HTTP.png)


> HTTP es un protocolo sin estado stateless. En otras palabras, la solicitud actual no sabe qué se ha hecho en las solicitudes anteriores.

> HTTP permite negociar el tipo de datos y la representación, para permitir que los sistemas se construyan independientemente de los datos que se transfieren.

> Citando del RFC 2616: "El protocolo de transferencia de hipertexto (HTTP) es un protocolo de nivel de aplicación para sistemas de información hipermedia distribuidos, colaborativos. Es un protocolo genérico, sin estado, que puede usarse para muchas tareas más allá de su uso para el hipertexto, tales como servidores de nombres y sistemas de administración de objetos distribuidos, a través de la extensión de sus métodos de solicitud, códigos de error y encabezados".

---------------

Cada vez que se escribre una URL desde su navegador para obtener un recurso web usando HTTP, p. http://www.nowhere123.com/index.html, el navegador convierte la URL en un mensaje de solicitud y lo envía al servidor HTTP. El servidor HTTP interpreta el mensaje de solicitud y le devuelve un mensaje de respuesta apropiado, que es el recurso que solicitó o un mensaje de error. Este proceso se ilustra a continuación:

![alt text](https://github.com/pumanzor/linuxadmin/blob/master/imgs/HTTP_Steps.png)

--------------

Uniform Resource Locator (URL)

Una URL (Localizador Uniforme de Recursos) se utiliza para identificar un recurso de manera única en la web. La URL tiene la siguiente sintaxis:

protocolo://nombre de host:puerto/ruta-y-nombre-archivo

Hay 4 partes en una URL:

* Protocolo: el protocolo de nivel de aplicación utilizado por el cliente y el servidor, por ejemplo, HTTP, FTP y telnet.
* Nombre de host: el nombre de dominio DNS (por ejemplo, www.nowhere123.com) o la dirección IP (por ejemplo, 192.128.1.2) del servidor.
* Puerto: el número de puerto TCP que el servidor está escuchando para las solicitudes entrantes de los clientes.
* Ruta de acceso y nombre de archivo: el nombre y la ubicación del recurso solicitado, en el directorio base del documento del servidor.

Por ejemplo, en la URL http://www.nowhere123.com/docs/index.html, el protocolo de comunicación es HTTP; el nombre de host es www.nowhere123.com. El número de puerto no se especificó en la URL y toma el número predeterminado, que es el puerto TCP 80 para HTTP. La ruta y el nombre del archivo para el recurso que se ubicará es "/docs/index.html".

Otros ejemplos de URL son:

    ftp://www.ftp.org/docs/test.txt
    mailto: user@test101.com
    noticias: soc.culture.Singapore
    telnet://www.nowhere123.com/




### que es Apache web server

#### The Apache HTTP Server

- is a powerful, flexible, HTTP/1.1 compliant web server
- implements the latest protocols, including HTTP/1.1 (RFC2616)
- is highly configurable and extensible with third-party modules
- can be customised by writing 'modules' using the Apache module API
- provides full source code and comes with an unrestrictive license
- runs on Windows 2000, Netware 5.x and above, OS/2, and most versions of Unix, as well as several other operating systems
- is actively being developed
- encourages user feedback through new ideas, bug reports and patches
- implements many frequently requested features, including:
  - DBM databases as well, as relational databases and LDAP for authentication
  - allows you to easily set up password-protected pages with enormous numbers of authorized users, without bogging down the server.
  - Customized responses to errors and problems
  - Allows you to set up files, or even CGI scripts, which are returned by the server in response to errors and problems, e.g.    setup a script to intercept 500 Server Errors and perform on-the-fly diagnostics for both users and yourself.
  - Multiple DirectoryIndex directives - Allows you to say DirectoryIndex index.html index.cgi, which instructs the server to either send back index.html or run index.cgi when a directory URL is requested, whichever it finds in the directory.

  - Unlimited flexible URL rewriting and aliasing - Apache has no fixed limit on the numbers of Aliases and Redirects which may be declared in the config files. In addition, a powerful rewriting engine can be used to solve most URL manipulation problems.
  - Content negotiation - i.e. the ability to automatically serve clients of varying sophistication and HTML level compliance, with documents which offer the best representation of information that the client is capable of accepting.
  - Virtual Hosts - Allows the server to distinguish between requests made to different IP addresses or names (mapped to the same machine). Apache also offers dynamically configurable mass-virtual hosting.
  - Configurable Reliable Piped Logs - You can configure Apache to generate logs in the format that you want. In addition, on most Unix architectures, Apache can send log files to a pipe, allowing for log rotation, hit filtering, real-time splitting of     - multiple vhosts into separate logs, and asynchronous DNS resolving on the fly.

### como funciona Apache2

Las direcciones en la web se encuentran expresadas con URL - Uniform Resource Locators - quien especifican el protocolo (e.g. http), un nombre de servidor (e.g. www.apache.org), y una URL-path (e.g. /docs/current/getting-started.html) y posiblemente una query string (e.g. ?arg=value) utilizada para pasar argumento adicionales al server.

Un cliente (browser, cliente modo texto, etc) conecta a un servidor con el protocolo especificado y hace un request por un recurso utilizando el URL-path.

El URL-path puede representar cualquier numero de cosas en el servidor. Puede ser un archivo (ej. como index.html) un handler (como  server-status) o algun tipo de programa (como index.php).

El servidor enviara una respuesta consistente en el codigo de status (status code) y opcionalmente un response body. El status code indica si el request tuvo exito y si no que tipo de condicion de error que hubo. Este le dice al cliente que deberia hacer con la respuesta.

El detalle de las transacciones y de los error de condicion son escritas en los log files.


Para conectarse a un servidor, el cliente primero tendrá que resolver el nombre del servidor en una dirección IP: la ubicación en Internet donde reside el servidor. Por lo tanto, para que su servidor web sea accesible, es necesario que el nombre del servidor esté en DNS.

Más de un nombre de host puede apuntar a la misma dirección IP y más de una dirección IP se puede conectar al mismo servidor físico. Por lo tanto, puede ejecutar más de un sitio web en el mismo servidor físico o maquina virtual, utilizando una función llamada hosts virtuales.

Si está probando un servidor que no es accesible por Internet, puede poner nombres de host en su archivo de hosts para hacer una resolución local. Por ejemplo, es posible que desee colocar un registro en su archivo de hosts para asignar una solicitud de www.example.com a su sistema local, con fines de prueba. Esta entrada se vería así:

    127.0.0.1 www.example.com


El archivo de hosts probablemente en linux se encuentre en /etc/hosts o en windows en  C:\Windows\system32\drivers\etc\hosts


El Servidor HTTP Apache se configura a través de archivos de texto simples. Estos archivos pueden ubicarse en una variedad de lugares, dependiendo de cómo instaló exactamente el servidor o de la distribucion de Linux que utiliza. Si instaló httpd desde las fuentes, la ubicación predeterminada de los archivos de configuración es /usr/local/apache2/conf. 

El archivo de configuración predeterminado generalmente se llama httpd.conf. Esto también puede variar en las distribuciones de terceros.

La configuración se divide frecuentemente en varios archivos más pequeños, para facilitar la administración. Estos archivos se cargan a través de la directiva "Include". Los nombres o ubicaciones de estos subarchivos no son mágicos y pueden variar mucho de una instalación a otra. Organice y subdivida estos archivos para que tenga más sentido para usted. Si la disposición de archivos que tiene de forma predeterminada no tiene sentido para usted, puede reorganizarla a su gusto.

El servidor se configura colocando directivas de configuración en estos archivos de configuración. Una directiva es una palabra clave seguida de uno o más argumentos que establecen su valor.

La pregunta "¿Dónde debería poner esa directiva?" generalmente se responde al considerar dónde desea que una directiva sea efectiva. Si se trata de una configuración global, debe aparecer en el archivo de configuración, fuera de cualquier <Directory>, <location>, <VirtualHost> u otra sección. 
    
Si se va a aplicar solo a un directorio particular, debe ir dentro de una sección <Directory> que hace referencia a ese directorio, y así sucesivamente.

Además de los archivos de configuración principal, ciertas directivas pueden ir en archivos .htaccess ubicados en los directorios de contenido. Los archivos .htaccess son principalmente para personas que no tienen acceso a los archivos de configuración del servidor principal.


### Instalacion

#### en Debian / Ubuntu / Kali

    apt-get install apache2
    

### Configuraciones.

Los archivos de configuracion de apache2 en DEbian se encuentran en el directorio

/etc/apache2

dentro de este directorio se pueden apreciar varios archvos de configuracion del servidor web

* apache2.conf: This is the main configuration file for the server. Almost all configuration can be done from within this file, although it is recommended to use separate, designated files for simplicity. This file will configure defaults and be the central point of access for the server to read configuration details.

* ports.conf: This file is used to specify the ports that virtual hosts should listen on. Be sure to check that this file is correct if you are configuring SSL.

* conf.d/: This directory is used for controlling specific aspects of the Apache configuration. For example, it is often used to define SSL configuration and default security choices.

* sites-available/: This directory contains all of the virtual host files that define different web sites. These will establish which content gets served for which requests. These are available configurations, not active configurations.

* sites-enabled/: This directory establishes which virtual host definitions are actually being used. Usually, this directory consists of symbolic links to files defined in the "sites-available" directory.

* mods-[enabled,available]/: These directories are similar in function to the sites directories, but they define modules that can be optionally loaded instead.



























### Status codes

* Códigos con formato 1xx: Respuestas informativas. Indica que la petición ha sido recibida y se está procesando.
* Códigos con formato 2xx: Respuestas correctas. Indica que la petición ha sido procesada correctamente.
* Códigos con formato 3xx: Respuestas de redirección. Indica que el cliente necesita realizar más acciones para finalizar la petición.
* Códigos con formato 4xx: Errores causados por el cliente. Indica que ha habido un error en el procesado de la petición a causa de que el cliente ha hecho algo mal.
* Códigos con formato 5xx: Errores causados por el servidor. Indica que ha habido un error en el procesado de la petición a causa de un fallo en el servidor.

------

    1×× Informational
    100 Continue
    101 Switching Protocols
    102 Processing

    2×× Success
    200 OK
    201 Created
    202 Accepted
    203 Non-authoritative Information
    204 No Content
    205 Reset Content
    206 Partial Content  
    207 Multi-Status
    208 Already Reported
    226 IM Used

    3×× Redirection
    300 Multiple Choices
    301 Moved Permanently
    302 Found
    303 See Other
    304 Not Modified
    305 Use Proxy
    307 Temporary Redirect
    308 Permanent Redirect

    4×× Client Error
    400 Bad Request
    401 Unauthorized
    402 Payment Required
    403 Forbidden
    404 Not Found
    405 Method Not Allowed
    406 Not Acceptable
    407 Proxy Authentication Required
    408 Request Timeout
    409 Conflict
    410 Gone
    411 Length Required
    412 Precondition Failed
    413 Payload Too Large
    414 Request-URI Too Long
    415 Unsupported Media Type
    416 Requested Range Not Satisfiable
    417 Expectation Failed
    418 I'm a teapot
    421 Misdirected Request
    422 Unprocessable Entity
    423 Locked
    424 Failed Dependency
    426 Upgrade Required
    428 Precondition Required
    429 Too Many Requests
    431 Request Header Fields Too Large
    444 Connection Closed Without Response
    451 Unavailable For Legal Reasons
    499 Client Closed Request

    5×× Server Error
    500 Internal Server Error
    501 Not Implemented
    502 Bad Gateway
    503 Service Unavailable
    504 Gateway Timeout
    505 HTTP Version Not Supported
    506 Variant Also Negotiates
    507 Insufficient Storage
    508 Loop Detected
    510 Not Extended
    511 Network Authentication Required
    599 Network Connect Timeout Error
