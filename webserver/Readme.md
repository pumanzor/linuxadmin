### Servicios Web

Modelo cliente servidor, 

Las direcciones en la web se encuentran expresadas con URL - Uniform Resource Locators - quien especifican el protocolo (e.g. http), un nombre de servidor (e.g. www.apache.org), y una URL-path (e.g. /docs/current/getting-started.html) y posiblemente una query string (e.g. ?arg=value) utilizada para pasar argumento adicionales al server.

Un cliente (browser, cliente modo texto, etc) conecta a un servidor con el protocolo especificado y hace un request por un recurso utilizando el URL-path.

El URL-path puede representar cualquier numero de cosas en el servidor. Puede ser un archivo (ej. como index.html) un handler (como  server-status) o algun tipo de programa (como index.php).

El servidor enviara una respuesta consistente en el codigo de status (status code) y opcionalmente un response body. El status code indica si el request tuvo exito y si no que tipo de condicion de error que hubo. Este le dice al cliente que deberia hacer con la respuesta.

El detalle de las transacciones y de los error de condicion son escritas en los log files.


Para conectarse a un servidor, el cliente primero tendrá que resolver el nombre del servidor en una dirección IP: la ubicación en Internet donde reside el servidor. Por lo tanto, para que su servidor web sea accesible, es necesario que el nombre del servidor esté en DNS.

Más de un nombre de host puede apuntar a la misma dirección IP y más de una dirección IP se puede conectar al mismo servidor físico. Por lo tanto, puede ejecutar más de un sitio web en el mismo servidor físico o maquina virtual, utilizando una función llamada hosts virtuales.

Si está probando un servidor que no es accesible por Internet, puede poner nombres de host en su archivo de hosts para hacer una resolución local. Por ejemplo, es posible que desee colocar un registro en su archivo de hosts para asignar una solicitud de www.example.com a su sistema local, con fines de prueba. Esta entrada se vería así:

    127.0.0.1 www.example.com



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
