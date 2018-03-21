## Servicios Web HTTP

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




























### Status codes



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
