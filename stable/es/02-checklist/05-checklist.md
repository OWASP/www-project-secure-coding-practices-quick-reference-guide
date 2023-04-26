\newpage
# Lista de Verificación de Prácticas de Codificación Segura {#secure-coding-practices-checklist .list-paragraph}

## Validación de entradas

- [ ]   Realizar todas las validaciones de datos en un sistema confiable.
    Por ejemplo: el servidor.

- [ ]   Identificar todas las fuentes de datos y clasificarlos como
    confiables o no. Validar todos los datos provenientes de
    fuentes no confiables. Por ejemplo: bases de datos, archivo, etc.

- [ ]   Debería existir una rutina de validación de datos de entrada
    centralizada para la aplicación.

- [ ]   Para todas las entradas de datos, especificar el juego de
    caracteres apropiado, tal como UTF-8.

- [ ]   Codificar los datos a un juego de caracteres común antes de su 
    validación ([*Canonicalización*](#Canonicalize)).

- [ ]   Todas las fallas en la validación deber terminar en el rechazo del
    dato de entrada.

- [ ]   Determinar si el sistema soportará juegps de caracteres UTF-8
    extendidos y de ser así, validarlos luego de terminada la
    decodificación del UTF-8.

- [ ]   Validar todos los datos brindados por el cliente antes de
    procesarlos, incluyendo todos los parámetros, URLs y contenidos de
    encabezados HTTP (por ejemplo nombres de Cookies y valores).
    Asegurarse de incluir los pedidos automáticos generados por JavaScript,
    Flash u otro código embebido.

- [ ]   Verificar que los valores de los encabezados, tanto en solicitudes como
 en respuestas contengan sólo caracteres ASCII.

- [ ]   Validar los datos provenientes de redirecciones. Un atacante puede
    enviar contenido malicioso directamente en el destino de la redirección,
    evitando la lógica de la aplicación y cualquier otra validación realizada antes de la redirección.

- [ ]   Validar que los tipos de datos sean los esperados.

- [ ]   Validar rangos de datos.

- [ ]   Validar largos de datos.

- [ ]   Validar toda entrada con una "lista permitida" que contenga los caracteres
 aceptados, siempre que sea posible.

- [ ]   Si es necesario permitir el ingreso de [*carácteres 
    peligrosos*](#Hazardous_Character), implementar controles adicionales
    tales como la codificación de la salida, utilizar una API de seguridad
    y el registrar del uso de estos datos a través de la aplicación.
    Algunos ejemplos de caracteres peligrosos:

> \< \> \" \' % ( ) & + \\ \\\' \\\"

- [ ]   Si su rutina estándar de validación no contempla el ingreso de los
    ejemplos de datos anteriormente indicados, esta rutina debería de ser revisada puntualmente.

- [ ]   Compruebe si hay bytes nulos (%00).

- [ ]   Compruebe si hay caracteres de nueva línea (%0d, %0a, \\r, \\n).

- [ ]   Compruebe si hay caracteres de alteraciones de ruta "punto, punto,
    barra" (../ o ..\\). En los casos en que se soportan sets de
    caracteres UTF-8 extendidos, implemente representaciones
    alternativas tales como: %c0%ae%c0%ae/ (utilice la
    [*canonicalización*](#Canonicalize) como forma de mitigar la
    doble codificación u otras formas de ofuscar ataques).

## Codificación de salidas {#output-encoding .list-paragraph}

- [ ]   Realice toda codificación en una zona de confianza (Por ejemplo, en el
    servidor).

- [ ]   Utilice una rutina probada y estándar para cada tipo de codificación
    de salida.

- [ ]   [*Codifique las salidas tomando en cuenta el contexto*]
(#Contextual_Output_Encoding) de todos los datos
    devueltos al cliente que se encuentre fuera de la [*frontera de confianza*]
    (#Trust_Boundaries) de la aplicación. La [*codificación de entidades HTML*]
    (#HTML_Entity_Encode) es un ejemplo, aunque no sea suficiente en todos los casos.

- [ ]   Codifique todos los caracteres salvo que sean reconocidos como
    seguros por el intérprete al que están destinados.

- [ ]   [*Sanitice*](#Sanitize_Data) según el contexto todas las
 salidas de datos no confiables hacia consultas SQL, XML y LDAP.

- [ ]   [*Sanitice*](#Sanitize_Data) todas las salidas de datos no confiables
    hacia comandos del sistema operativo.

## Autenticación y gestión de contraseñas {#authentication-and-password-management .list-paragraph}

- [ ]   Requerir autenticación para todos los recursos y páginas excepto
    aquellas específicamente clasificadas como públicas.

- [ ]   Todos los controles de autenticación deben ser efectuados dentro de la
frontera de confianza, por ejemplo: el servidor.

- [ ]   Establecer y utilizar servicios de autenticación estándares y
    probados cuando sea posible.

- [ ]   Utilizar una implementación centralizada para todos los controles de
    autenticación, incluyendo bibliotecas que invoquen a servicios externos
    de autenticación.

- [ ]   Segregar la lógica de autenticación, de la del recurso solicitado y
    utilizar redirecciones desde y hacia el control centralizado de
    autenticación.

- [ ]   Todos los controles de autenticación deben fallar de una forma
    segura.

- [ ]   Todas las funciones administrativas y de gestión de cuentas
    deben ser al menos tan seguras como el mecanismo primario de
    autenticación.

- [ ]   Si la aplicación gestiona un almacén de credenciales, se
    debe asegurar que únicamente se almacena el hash con sal de las contraseñas
    y que el archivo/tabla que guarda las contraseñas y claves solo puede ser
    escrito por la aplicación (si es posible, no utilizar el algoritmo de hash MD5).

- [ ]   El hash de las contraseñas debe ser implementado en dentro de la
frontera de confianza. (por ejemplo: el servidor).

- [ ]   Validar los datos de autenticación únicamente luego haber completado
    todos los datos de entrada, especialmente en implementaciones de
    [*autenticación secuencial*](#Sequential_Authentication).

- [ ]   Las respuestas a los fallos en la autenticación no deben indicar
    cuál parte de la autenticación fue incorrecta. A modo de ejemplo, en
    lugar de \"usuario invalido\" o \"contraseña invalida\", utilizar
    \"usuario y/o contraseña inválidos\" en ambos casos. Las repuestas a
    los errores deben ser idénticas tanto a nivel de lo desplegado como
    a nivel del código fuente.

- [ ]   Utilizar autenticación para conexiones a sistemas externos que
    involucren información o funciones sensibles.

- [ ]   Las credenciales de autenticación para acceder a servicios externos
    a la aplicación deben ser cifrados y almacenados en ubicaciones
    protegidas dentro de la frontera de confianza (por ejemplo: el
    servidor). El código fuente NO es una ubicación segura.

- [ ]   Utilizar únicamente pedidos del tipo HTTP POST para la transmisión
    de credenciales de autenticación.

- [ ]   Utilizar únicamente conexiones cifradas o cifrar los datos
    para el envío de contraseñas que no sean temporales, por ejemplo: correo
    cifrados. Contraseñas temporales (como aquellas asociadas con
    reseteos por correo electrónico), pueden ser una excepción.

- [ ]   Aplicar por medio de una política o regulación los
    requerimientos de complejidad de la contraseña. Las credenciales de
    autenticación deben ser suficientes como para resistir aquellos
    ataques típicos de las amenazas en el entorno del sistema, por ejemplo:
    obligar el uso de combinaciones de caracteres
    numéricos/alfanuméricos y/o caracteres especiales.

- [ ]   Aplicar por medio de una política o regulación los
    requerimientos de longitud de la contraseña. Comúnmente se utilizan
    ocho caracteres, pero dieciséis es mejor, adicionalmente considerar
    el uso de frases de varias palabras.

- [ ]   No se debe desplegar en la pantalla la contraseña ingresada. A modo
    de ejemplo, en formularios web, utilizar el tipo de entrada
    \"password\" (input type=\"password\").

- [ ]   Deshabilitar las cuentas luego de un número establecido de intentos
    inválidos de inicio de sesión(por ejemplo, cinco intentos).
    La cuenta debe ser dehabilitada por un periodo de tiempo suficiente como
    para desalentar una inferencia de credenciales por fuerza bruta, pero no
    tanto como para provocar un ataque de denegación de servicio.

- [ ]   El cambio y reseteo de contraseñas requieren los mismos niveles de
    control asociados a la creación y autenticación de cuentas.

- [ ]   Las preguntas para el reseteo de contraseñas deben contemplar un
    amplio rango de respuestas aleatorias, por ejemplo: \"libro
    favorito\" es una mala pregunta dado que \"la biblia\" es una
    respuesta muy común.

- [ ]   Si se utiliza la recuperación de contraseña a través del correo
    electrónico, se debe enviar únicamente un link o contraseña temporal a una
    casillas previamente registrada en el sistema.

- [ ]   Las contraseñas y links temporales deben tener un corto periodo de
    validez.

- [ ]   Obligar el cambio de contraseñas temporales luego de su utilización.

- [ ]   Notificar a los usuarios cada vez que se produce un reseteo de
    contraseña.

- [ ]   Prevenir la reutilización de contraseñas.

- [ ]   Las contraseñas deben tener al menos un día de antigüedad antes de
    poder ser cambiadas, de forma de evitar ataques de reutilización de
    contraseñas.

- [ ]   Hacer cumplir por medio de una política o regulación los
    requerimientos de cambio de contraseña. Los sistemas críticos pueden
    requerir cambios más frecuentes que otros sistemas. El tiempo entre
    cada reseteo debe ser controlado administrativamente.

- [ ]   Deshabilitar la funcionalidad de \"auto completar\" campos de contraseñas.

- [ ]   El último acceso (fallido o exitoso) debe ser reportado al usuario
    en su siguiente acceso exitoso.

- [ ]   Implementar un monitoreo para identificar ataques a múltiples
    cuentas utilizando la misma contraseña. Este patrón de ataque es
    utilizado parar superar bloqueos estándar cuando los nombres de
    usuario pueden ser recopilados o adivinados.

- [ ]   Cambiar todos los usuarios y contraseñas por defecto o deshabilitar
    las cuentas asociadas.

- [ ]   Re autenticar usuarios antes de la realización de operaciones
    críticas.

- [ ]   Utilizar [*autenticación multi-factor*](#Multi_Factor_Authentication)
    para las cuentas más sensibles o de mayor valor.

- [ ]   Si se utiliza un código de una tercera parte para la autenticación,
    inspeccionarlo minuciosamente para asegurar que no se encuentre
    afectado por cualquier código malicioso.

## Administración de sesiones: {#session-management .list-paragraph}

- [ ]   Utilizar las funciones para la gestión de sesiones propias del framework
 de desarrollo o del servidor de aplicaciones. Sólo se deben reconocer estos
 identificadores como válidos.

- [ ]   La creación de identificadores de sesión solo debe ser realizada dentro
    de una frontera de confianza (el servidor, por ejemplo).

- [ ]   Los controles de gestión de sesiones deben utilizar
    algoritmos que generen identificadores suficientemente aleatorios.

- [ ]   Definir el dominio y ruta para las cookies que contienen
    identificadores de sesión autenticados con un valor suficientemente
    estricto para el sitio.

- [ ]   La función de fin de sesión (logout) debe terminar completamente con
la sesión o conexión asociada.

- [ ]   La función de fin de sesión (logout) debe estar disponible en todas las
páginas protegidas por autenticación.

- [ ]   Establecer un tiempo de inactividad de la sesión lo más corto posible,
    balanceando los riesgos con los requerimientos del negocio. En la
    mayoría de los casos, nunca debería ser superior a algunas horas.

- [ ]   Deshabilitar logeos persistentes y efectuar finalizaciones
    periódicas de sesiones, incluso cuando la sesión se encuentra
    activa.Esto aplica especialmente en aplicaciones ricas en conexiones de red
    o que se conectan a sistemas críticos. El período de tiempo para finalizar
    la sesión debe de ser compatible con las necesidades del negocio. 
    Además, el usuario debe recibir las notificaciones suficientes para poder mitigar impactos negativos.

- [ ]   Si una sesión fue establecida antes del inicio de sesión, cerrar dicha
sesión y establecer una nueva luego de un login exitoso.

- [ ]   Generar un nuevo identificador de sesión luego de cada re
    autenticación.

- [ ]   No permitir logeos concurrentes con el mismo identificador de usuario.

- [ ]   No exponer identificadores de sesión en URLs, mensajes de error ni
    logs. Los identificadores de sesión solo deben ser ubicados en la cookie
    HTTP. A modo de ejemplo, no transmitir el identificador de sesión como un parámetro GET.

- [ ]   Proteger de accesos no autorizados los datos de las sesiones, por
    parte de otros usuarios del servidor, implementando los controles de acceso acordes.

- [ ]   Generar un nuevo identificador de sesión y desactivar el anterior de
    forma periódica.Esto puede mitigar algunos escenarios
    de robo de sesiones donde el identificador es comprometido.

- [ ]   Generar un nuevo identificador de sesión si la conexión cambia de HTTP
    a HTTPS, como puede suceder durante la autenticación. Dentro de
    la aplicación es recomendable utilizar siempre HTTPS en lugar de cambiar
    entre HTTP y HTTPS.

- [ ]   Uso de complementos de gestión de sesión para operaciones sensibles del
    lado del servidor para operaciones sensibles (como la gestión de cuentas de
    usuarios). Algunos ejemplos son el uso de tokens o parámetros generados
    aleatoramente para la sesión. Este método puede ser utilizado para prevenir
    ataques de ([*Falsificación de petición en sitios cruzados (Cross Site 
    Request Forgery Attacks, o CSRF)*](#CSRF).

- [ ]   Uso de complementos de gestión de sesión para operaciones sensibles o
    críticas utilizando tokens o parámetros por cada pedido (per request) en
    lugar de por sesión.

- [ ]   Configurar el atributo \"seguro\" (secure) para las cookies
    transmitidas sobre una conexión TLS.

- [ ]   Configurar las cookies con el atributo HttpOnly, salvo que se
    requiera específicamente acceso desde los scripts del lado del cliente,
    para leer o configurar una cookie.

## Control de Acceso {#access-control .list-paragraph}

- [ ]  Para el flujo decisiones de autorización, utilizar únicamente
    objetos confiables del sistema. Por ejemplo, objetos de sesión del lado del
    servidor.

- [ ]   Utilizar un único componente para el chequeo de autorizaciones para
    todo el sitio. Esto incluye bibliotecas que invoquen a servicios de
    autorización externos.

- [ ]   Los controles de acceso deben fallar de forma segura.

- [ ]   Denegar todos los accesos en caso que la aplicación no pueda
    acceder a la información de configuración de seguridad.

- [ ]   Requerir controles de autorización en cada solicitud,
    incluyendo aquellos creados por scripts en el servidor, \"includes\" y
    pedidos AJAX o Flash desde el lado del cliente.

- [ ]   Separar lógica privilegiada del restp del código de la aplicación.

- [ ]   Restringir acceso a archivos u otros recursos, incluyendo aquellos
    fuera del control directo de la aplicación, únicamente a usuarios
    autorizados.

- [ ]   Restringir el acceso a las URL protegidas sólo a los usuarios autorizados.

- [ ]   Restringir el acceso a las funciones protegidas únicamente a los usuarios autorizados.

- [ ]   Restringir las referencias directas a objetos únicamente a los usuarios
    autorizados.

- [ ]   Restringir el acceso a los servicios sólo a los usuarios autorizados.

- [ ]   Restringir el acceso a información de la aplicación, solo a usuarios
    autorizados.

- [ ]   Restringir el acceso a los atributos de usuario y datos y a la
    información sobre políticas utilizados por los controles de acceso.

- [ ]   Restringir el acceso a la información de configuración relevante para
    la seguridad sólo a usuarios autorizados.

- [ ]   Las reglas de control de acceso implementadas del lado del servidor
    y en la capa de presentación, deben coincidir.

- [ ]   Si los [*datos de estado*](#State_Data) deben almacenarse en el 
    cliente, deben ser cifrados y comprobada su integridad en el servidor para
    detectar manipulaciones.

- [ ]   Hacer que flujos de aplicación que cumplan con las reglas del
    negocio.

- [ ]   Limitar el número de transacciones que un usuario común o un
    dispositivo puede ejecutar en un período de tiempo dado. La tasa de transacciones/tiempo debe ser mayor a la necesidad del negocio, pero suficientemente bajo para detectar ataques automatizados.

- [ ]   Utilizar el header \"referer\" sólo como un chequeo complementario.
    Nunca debe ser utilizado como chequeo de autorización, ya que puede ser
    suplantado.

- [ ]   Si se permiten sesiones autenticadas largas, revalide periódicamente
    la autorización de un usuario para asegurarse de que sus privilegios no han
    cambiado y, si es así, cerrar la sesión del usuario y obligarle a
    volver a autenticarse.

- [ ]   Implemente la auditoría de cuentas y aplique la desactivación de
    cuentas no utilizadas (por ejemplo, después de no más de 30 días de la
    expiración de la contraseña de una cuenta).

- [ ]   La aplicación debe permitir deshabilitar y terminar cuentas una vez
    que se termina la autorización. Por ejemplo ante un cambio de rol, estatus
    de empleo, etc.

- [ ]   Cuentas de servicio o cuentas de soporte a la conectividad deben
    poseer los mínimos privilegios.

- [ ]   Crear una política de control de acceso para documentar las reglas
    de negocio de la aplicación, los tipos de datos, criterios para
    autorización de acceso y los controles asociados para otorgarlos y
    controlarlos. Esto incluye la identificación de accesos requeridos
    tanto para los datos como para los sistemas.

## Prácticas Critpográficas {#cryptographic-practices .list-paragraph}

- [ ]   Todas las funciones de criptografía de la aplicación deben ser
    implementadas en sistemas de confiables (el servidor, por ejemplo).

- [ ]   Proteger secretos maestros de accesos no autorizados.

- [ ]   Los módulos criptográficos deben fallar en forma segura.

- [ ]   Todos los números aleatorios, nombres aleatorios de archivos, GUIDs, y
    cadenas de caracteres aleatorios, deben generarse utilizando el módulos
    aprobado para tal fin, tendiendo a que los valores generados no sean
    predecibles.

- [ ]   Los módulos criptrográficos utilizados por la aplicación deben cumplir
    con FIPS 140-2 o con su estándar equivalente. (Ver
    <http://csrc.nist.gov/groups/STM/cmvp/validation.html>).

- [ ]   Establecer y utilizar una política y procesos de cómo gestionar las
    claves criptográficas.

## Manejo de errores y Logs {#error-handling-and-logging .list-paragraph}

- [ ]   No divulgar información sensible en respuestas de error, incluyendo
    detalles del sistema, identificadores de sesión o información de la
    cuenta.

- [ ]   Utilizar manejadores de errores que no muestren información de
    depuración o de memoria.

- [ ]   Implementar mensajes de error genéricos y utilizar páginas de error 
    personalizadas.

- [ ]   La aplicación debe manejar los errores de la aplicación y no basarse
    en la configuración del servidor.

- [ ]   Liberar correctamente la memoria asignada cuando se producen
    condiciones de error.

- [ ]   La lógica de tratamiento de errores asociada a los controles de
    seguridad debe denegar el acceso por defecto.

- [ ]   Todos los controles de registro deben estar implementados en sistemas
    confiables (por ejemplo, el servidor).

- [ ]   El registro de los controles de acceso debe incluir tanto los casos de
    éxito como de falla.

- [ ]   Asegurar que los [*datos de registros 
    (logs)*](#Log_Event_Data) contengan información importante.

- [ ]   Asegurar que los registros de bitácora (logs) de entrada que incluyen
    información no confiable, no serán interpretado o ejecutado como código
    en interfaces de visualización o aplicativos.

- [ ]   Restringir el acceso a los registros de bitácora (logs), sólo a
    personal autorizado.

- [ ]   Utilizar una rutina centralizada para todas las operaciones de
    registro (logging).

- [ ]   No guardar información sensible en registros de bitácora (logs),
    incluyendo detalles innecesarios del sistema.

- [ ]   Asegurar que existen mecanismos para conducir un análisis de los
    registros de bitácora (logs).

- [ ]   Registrar todas las fallas de validación.

- [ ]   Registrar todos los intentos de autenticación, en
    particular los fallidos.

- [ ]   Registrartodas las fallas en los controles de acceso.

- [ ]   Registrar todos los eventos de intento de evasión de
    controles, incluyendo cambios en el estado de la información no
    esperados.

- [ ]   Registrar todos los intentos de conexión con tokens
    inválidos o vencidos.

- [ ]   Registrar todas las excepciones del sistema.

- [ ]   Registrar todas las funciones administrativas, incluyendo
    cambios en la configuración de seguridad.

- [ ]   Registrar todas las fallas de conexión de TLS.

- [ ]   Registrar las fallas de los módulos criptográficos.

- [ ]   Utilizar una función de hash para validar la integridad de los
    registros (logs).

## Protección de datos: {#data-protection .list-paragraph}

- [ ]   Implementar el principio de mínimo privilegio, restringir el acceso de
    los usuarios solamente a la funcionalidad, datos y sistemas de
    información que son necesarias para realizar sus tareas.

- [ ]   Proteja todas las copias temporales o en caché de datos sensibles
    almacenados en el servidor frente a accesos no autorizados y elimine los
    archivos temporales de trabajo en cuanto dejen de ser necesarios.

- [ ]   Cifrar toda información altamente sensible almacenada, como por
    ejemplo: datos para la verificación de la autenticación, incluso en el
    servidor. Siempre utilice algoritmos de cifrado que hayan sido ampliamente
    analizados y con buenos antecedentes. Por mayor información, vea
    \"Prácticas Criptográficas\".

- [ ]   Proteja el código fuente del servidor de forma de que no pueda ser
    descargado por un usuario.

- [ ]   No almacene contraseñas, cadenas de conexión u otra información
    sensible sensible en texto claro o de cualquier otra forma no criptográfica
    en el lado del cliente. Esto incluye embeber la información en  formatos
    inseguros como: MS viewstate, Adobe flash o código compilado.

- [ ]   Remueva los comentarios en el código de producción que sea accesible
    al usuario que puedan revelar detalles sobre los servidores o información
    sensible.

- [ ]   Elimine cualquier aplicación que no sea necesaria, así como la
    documentación de los sistemas que puedan revelar información útil para los
    atacantes.

- [ ]   No incluya información sensible en los parámetros de la consulta HTTP
    GET.

- [ ]   Deshabilite las funcionalidades de autocompletar en aquellos
    formularios que contengan información sensible, incluyendo la autenticación.

- [ ]   Deshabilite el caché en el cliente para las páginas que contengan
    información sensible. Los encabezados HTTP \"Cache-Control: no-store\" y \"Pragma: no-cache\" pueden ser utilizados en conjunto,aunque el segundo sea utilizado como compatibilidad con HTTP/1.0 principalmente.

- [ ]   La aplicación debe de soportar la eliminación de datos sensibles
    cuando ya no son requeridos, como por ejemplo: información
    personal o ciertos datos financieros.

- [ ]   Implemente controles de acceso adecuados para los datos sensibles
    almacenados en el servidor. Esto incluye datos en caché, archivos temporales
    y datos que sólo deben ser accesibles por usuarios específicos del sistema.

## Seguridad en las comunicaciones: {#communication-security .list-paragraph}

- [ ]   Implemente cifrado para todas las transmisiones de información
    sensible. Esto debe incluir TLS para proteger la conexión y se
    puede combinar con cifrado discreto de archivos sensibles
    en conexiones que no estén basadas en HTTP.

- [ ]   Los certificados TLS deben de ser válidos y poseer el nombre de
    dominio correcto, no deben estar expirados y deben ser instalados
    con los certificados intermedios si son requeridos.

- [ ]   Las conexiones TLS que fallen no deben de transformarse en una
    conexión insegura.

- [ ]   Utilizar conexiones TLS para todo el contenido que requiera acceso
    autenticado y para todo otro tipo de información sensible.

- [ ]   Utilizar TLS para las conexione a sistemas externos que involucren
    funciones o información sensible.

- [ ]   Utilizar una única implementación estándar de TLS que se encuentre
    configurada correctamente.

- [ ]   Especificar los caracteres de codificación para todas las
    conexiones.

- [ ]   Filtrar los parámetros que contengan información sensible en el cabezal
    HTTP referer, cuando existan vínculos a sitios externos.

## Configuración de los sistemas: {#system-configuration .list-paragraph}

- [ ]   Asegurarse de que los servidores, los frameworks y los componentes
    del sistema están utilizando la última versión aprobada.

- [ ]   Asegurar que los servidores, los frameworks y los componentes del
    sistema están actualizados con todos los parches emitidos para las
    versiones en uso.

- [ ]   Deshabilitar el listado de directorio.

- [ ]   Restringir el servidor web, los procesos y las cuentas de servicios
    con el mínimos privilegios posibles.

- [ ]   Cuando ocurra una excepción, se debe de fallar de forma segura.

- [ ]   Elimine todas las funcionalidades y archivos que no sean necesarios.

- [ ]   Eliminar código de pruebas o cualquier funcionalidad que no sea
    necesaria en producción, previo al despliegue.

- [ ]   Evite la divulgación de la estructura de directorios a través del
    archivo robots.txt colocando directorios que estén disponibles para el
    índice público. Luego "Deshabilitar" el directorio raíz en el archivo
    robots.txt, en vez de "Deshabilitar" cada directorio individualmente.

- [ ]   Definir cuáles de los métodos HTTP, GET o POST, la aplicación va a
    soportar y si deben de ser manejados de forma diferente en las
    distintas páginas de la aplicación.

- [ ]   Desactive los métodos HTTP innecesarios, como las extensiones WebDAV.
    Si se requiere un método HTTP extendido, utilice un mecanismo de
    autenticación bien probado.

- [ ]   Si el servidor web acepta tanto HTTP 1.0 como 1.1, asegúrese de que
    ambos están configurados de forma similar o asegúrese de que entiende
    cualquier diferencia que pueda existir (por ejemplo, el manejo de métodos
    HTTP extendidos).

- [ ]   Eliminar información innecesaria en los encabezados HTTP de
    respuesta referidas al SO, versión del servidor web y frameworks de
    aplicación.

- [ ]   El almacén de la configuración de seguridad debe de ser en un formato
    legible para un humano, con el fin de permitir su auditoría.

- [ ]   Implementar un Sistema de gestión de activos y registrar los
    componentes del sistema en éste.

- [ ]   Aislar los ambientes de desarrollo de la red de producción y
    permitir el acceso solamente a los grupos de desarrollo y testeo
    específicamente autorizados. Los ambientes de desarrollo a menudo
    son configurados de forma menos segura que los ambientes de
    producción y los atacantes pueden utilizar estas diferencias para
    descubrir vulnerabilidades o una forma para explotarlas.

- [ ]   Implementar un Sistema de Control de Cambios del Software para
    gestionar y registrar los cambios al código tanto para los ambientes
    de desarrollo como para los de producción.

## Seguridad de Base de Datos {#database-security .list-paragraph}

- [ ]   Utilice [*consultas parametrizadas*](#Parameterized_Queries) con
    tipos de datos fuertemente tipados.

- [ ]   Valide las entradas y codifique las salidas y
    asegúrese de manejar los meta caracteres. Si esto falla, no ejecute
    el comando de la base de datos.

- [ ]   Asegúrese de que todas las variables posean tipos de datos
    asociados.

- [ ]   La aplicación debe de utilizar el mínimo nivel de privilegios cuando
    accede a la base de datos.

- [ ]   Utilice credenciales seguras para acceder a la base de datos.

- [ ]   Las cadenas de conexión a la base de datos no deben de estar
    incluidas en el código de la aplicación. Pueden estar en un archivo de
    configuración separado en un sistema confiable y debería de estar cifrado.

- [ ]   Utilice procedimientos almacenados para abstraer el acceso a los
    datos y elimine los permisos de las tablas en la base de datos.

- [ ]   Cierre la conexión a la base de datos tan pronto como sea posible.

- [ ]   Elimine o cambie todas las contraseñas administrativas por defecto.
    Utilice contraseñas fuertes o frases o implemente autenticación de
    múltiples factores.

- [ ]   Deshabilite todas las funcionalidades innecesarias de la base de
    datos (por ejemplo: procedimientos almacenados innecesarios,
    servicios no utilizados, paquetes de utilidades). Instale sólo el
    conjunto mínimo de funcionalidades y opciones requeridas (reducción de la superficie de ataque).

- [ ]   Eliminar el contenido innecesario incluido por defecto (por
    ejemplo: esquemas de ejemplo).

- [ ]   Deshabilitar las cuentas por defecto que no son necesarias para la
    operativa.

- [ ]   La aplicación debería conectarse a la base de datos con credenciales
    diferentes para cada nivel de confianza, por ejemplo: usuarios,
    usuarios solo lectura, invitados, administrador.

## Manejo de Archivos {#file-management .list-paragraph}

- [ ]   No utilizar directamente información provista por el usuario en
    ninguna operación dinámica de inclusión (include).

- [ ]   Requerir autenticación antes de permitir la transferencia de un
    archivo al servidor.

- [ ]   Limite los tipos de archivos que pueden ser cargados al servidor
    únicamente a aquellos requeridos por la operativa del negocio (por
    ejemplo: pdf, doc, xls, etc.).

- [ ]   Validar los tipos de archivo transferidos verificando la estructura
    de sus encabezados. La validación del tipo de archivo únicamente por
    la extensión no es suficiente.

- [ ]   No almacenar archivos cargados en el contexto de la
    aplicación web. Los archivos deben almacenarse en un repositorio
    específico o en una base de datos.

- [ ]   Evite o restrinja la transferencia de archivos que puedan ser
    interpretados por el servidor web, por ejemplo: asp, php, jsp, etc.

- [ ]   Eliminar los permisos de ejecución a las carpetas en las que se cargan
    archivos por parte de usuarios.

- [ ]   Implemente una transferencia de archivos seguro en UNIX mediante el
    uso de discos lógicos y el uso de las rutas (path) correspondientes
    o mediante la utilización de un entorno chroot.

- [ ]   Cuando se referencie a un archivo existente en el servidor, utilice
    una lista de permitidos de nombres y extensiones válidas. Validar el
    contenido del parámetro pasado contra esta lista de permitidas y si se
    encuentra una coincidencia, denegar la operación o utilizar
    transferir un archivo pre-definido.

- [ ]   No utilizar información provista por el usuario para la generación
    de redirecciones dinámicas. Si se debe proveer esta funcionalidad,
    la redirección debe aceptar únicamente caminos relativos dentro de
    la URL previamente establecidos (lista de directorios
    relativos permitidos).

- [ ]   No incluir en parámetros nombres de directorios o rutas de archivos,
    en su lugar utilizar índices que internamente se asocien a
    directorios o rutas pre definidas.

- [ ]   Nunca envíe la ruta absoluta de un archivo al cliente.

- [ ]   Asegúrese que los archivos y recursos de la aplicación sean de solo
    lectura.

- [ ]   Analizar los archivos transferidos por los clientes en busca de virus
    y malware.

## Manejo de Memoria: {#memory-management .list-paragraph}

- [ ]   Utilice controles en las entrada y salidas de datos no
    confiables.

- [ ]   Verifique de dos formas que el largo de los buffers sean los requeridos.

- [ ]   Cuando utilice primitivas que requieran el número de bytes a copiar,
    como ser strncpy(), sea consciente que si el tamaño del buffer
    destino es igual al tamaño del buffer origen, el destino podría
    quedar sin el NULL-byte requerido del final.

- [ ]   Verifique los límites de los buffers si se llama a las funciones
    dentro de un loop y asegúrese de no correr riesgo de escribir fuera
    del espacio reservado.

- [ ]   Truncar el largo de todos los strings de entrada a un tamaño
    razonable antes de pasarlos a una función de copia o concatenación.

- [ ]   Específicamente libere los recursos, no confíe en el garbage
    collector(por ejemplo: objetos de conexión, handlers de archivos,
    etc.).

- [ ]   Utilice stacks no ejecutables cuando sea posible (NX bit).

- [ ]   Evite el uso de primitivas con vulnerabilidades conocidas (por
    ejemplo: printf, strcat, strcpy, etc.).

- [ ]   Libere adecuadamente la memoria previa a la salida de una función y
    de todos los puntos de finalización de la aplicación.

## Practicas Generales para la Codificación: {#general-coding-practices .list-paragraph}

- [ ]   Utilizar código gestionado probado y aprobado en lugar de crear nuevo
    código no gestionado para tareas comunes.

- [ ]   Utilice las APIs ya incluídas (build-in) para el acceso a funciones
    específicas del sistema operativo. No permita que la aplicación ejecute
    comandos directamente en el sistema operativo, especialmente mediante la
    invocación de una shell.

- [ ]   Utilice sumas de comprobación o hashes para verificar la integridad
    del código interpretado, bibliotecas, ejecutables y archivos de configuración.

- [ ]   Utilice locks para evitar múltiples pedidos simultáneos o utilice
    mecanismos de sincronización para evitar condiciones de carrera

- [ ]   Proteja las variables y recursos compartidos de accesos concurrentes
    inadecuados.

- [ ]   Inicialice explícitamente todas sus variables y almacenes de datos, ya sea durante la declaración o antes del primer uso.

- [ ]   Las aplicaciones que requieran para su ejecución privilegios elevados,
    deberán solicitarlos tan tarde como sea posible, y liberarlos lo antes
    posible.

- [ ]   Evitar errores de cálculo comprendiendo la forma en que el lenguaje
    de programación maneja las operaciones matemáticas y las
    representaciones numéricas. Prestar especial atención a las
    discrepancias en la cantidad de bytes utilizados para la
    representación, la precisión, diferencias entre valores con y sin
    signo, truncamiento, conversiones y casting entre tipos de
    variables, cálculos \"no-numéricos\" y como el lenguaje maneja los
    números demasiado grandes o demasiado pequeños para su
    representación.

- [ ]   No utilizar datos provistos por el usuario para ejecutar funciones
    dinámicamente.

- [ ]   Evite que los usuarios introduzcan o modifiquen código de la
    aplicación.

- [ ]   Revisar todas las aplicaciones secundarias, código provisto por
    terceros y bibliotecas para determinar la necesidad del negocio para
    su utilización y validar el funcionamiento seguro, ya que estos
    pueden introducir nuevas vulnerabilidades.

- [ ]   Implementar mecanismos seguros para las actualizaciones. Si la
    aplicación realiza actualizaciones automáticas, utilizar firmas
    criptográficas para el código y asegurarse que el cliente que
    descarga la aplicación verifique dichas firma. Utilizar canales
    cifrados para las transferencias de código desde el servidor de
    actualización.
