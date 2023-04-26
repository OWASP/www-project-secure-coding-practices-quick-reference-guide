\newpage
## Apéndice B: Glosario {#glossary .list-paragraph}

[]{##Threat_Agenta .anchor}**Agente de Amenaza:** Cualquier entidad que
puede poseer un impacto negativo en el sistema. Puede ser desde un
usuario malicioso que desea comprometer los controles de seguridad del
sistema; sin embargo, también puede referirse al mal uso accidental del
sistema o a una amenaza física como fuego o inundación.

**Autenticación:** Conjunto de Controles utilizados para verificar la
identidad de un usuario o entidad que interactúa con el software.

[]{#Multi_Factor_Authentication .anchor}**Autenticación Multi-Factor:**
Proceso de autenticación que le requiere al usuario producir múltiples y
distintos tipos de credenciales. Típicamente son basados en:

> • algo que el usuario tiene, por ejemplo: una tarjeta inteligente
> • algo que conoce, por ejemplo: un pin
> • o algo que es, por ejemplo: datos provenientes de un lector biométrico

[]{#Sequential_Authentication .anchor}**Autenticación secuencial:** Cuando
los datos de autenticación son solicitados en páginas sucesivas en vez de
ser solicitados todos de una sola vez en una única página.

[]{#Canonicalize .anchor}**Canonicalizar:** Reducir las distintas
    codificaciones y representaciones de datos a una única forma simple.

[]{#Hazardous_Character .anchor}**Caracteres considerados peligrosos:**
    Cualquier carácter o representación codificada que pueda afectar al
    funcionamiento de la aplicación o del sistema asociado al ser interpretado
    (comportamiento  ajeno al uso previsto del carácter). Estos caracteres pueden
    utilizarse para:

> • Alterar la estructura de las sentencias o código existente.
>
> • Insertar nuevo código no deseado. >
> • Alterar rutas.
>
> • Causar salidas inesperadas de rutinas o funciones.
>
> • Causar condiciones de error.
>
> • Obtener cualquiera de los efectos anteriores sobre el flujo de aplicaciones
> o sistemas

[]{#Abuse_Case .anchor}**Caso de Abuso:** Describe los usos indebidos
    intencionados o no del software. Los casos de abuso deben cuestionar los
    supuestos del diseño del sistema.

[]{#HTML_Entity_Encode .anchor}**Codificación de Entidades HTML:** Proceso de
    sustitución de determinados caracteres ASCII por sus equivalentes en
    entidades HTML. Por ejemplo, la codificación sustituiría el carácter menor
    \"\<\" por su equivalente en HTML \"&lt;\". Las entidades HTML son \"inertes\" en la mayoría de los intérpretes, especialmente en navegadores, por lo que puede mitigar ciertos ataques del lado del cliente.

**Codificación de Salida:** Conjunto de controles que apuntan al uso de una
    codificación para asegurar que los datos producidos por la aplicación son
    seguros.

[]{#Contextual_Output_Encoding .anchor} **Codificación de Salida Contextualizada:**
    Codificación de los datos de salida en función de cómo serán utilizados
    por la aplicación. Los métodos específicos varían en función de la forma en
    que se utilizan los datos de salida. Si los datos se van a incluir en la
    respuesta al cliente, tenga en cuenta escenarios de inclusión como: el
    cuerpo de un documento HTML, un atributo HTML, dentro de JavaScript, dentro
    de CSS o en una URL. También debe tener en cuenta otros casos de uso como
    consultas SQL, XML y LDAP.

[]{#Confidentiality .anchor}**Confidencialidad:** Propiedad de la información
    por la que se garantiza que está accesible únicamente a entidades
    autorizadas.

**Configuración del sistema:** Conjunto de controles que ayuda a asegurar que
    los componentes de infraestructura que brindan soporte al software fueron
    desplegados de manera segura.

[]{#Parameterized_Queries .anchor}
    **Consultas parametrizadas (prepared statements):** Mantiene la consulta
    y los datos separados a través del uso de marcadores. La estructura de la
    consulta es definida utilizando marcadores, la consulta SQL es enviada a la
    base de datos y preparada, para luego ser combinada con los valores de los
    parámetros. Esto previene a las consultas de ser alteradas debido a que los
    valores de los parámetros son combinados con la consulta compilada, no con
    la cadena de caracteres que representa al SQL.

**Control de Acceso:** Conjunto de controles que permiten o deniegan a un
    usuario, u otra entidad, el acceso a un recurso del sistema. Suele basarse
    en roles jerárquicos y privilegios individuales dentro de un rol, pero
    también incluye las interacciones entre sistemas.

[]{#Security_Controls .anchor} **Control de seguridad:** Acción que mitiga una
    vulnerabilidad potencial y ayuda a asegurar que el software se comporta
    únicamente de la forma esperada.

[]{#State_Data .anchor} **Datos de estado:** Cuando son utilizados datos o
    parámetros, ya sea por la aplicación o el servidor, emulando una conexión
    persiste o realizando el seguimiento del estado de un cliente a través de
    un proceso multi-pedido o transacción.

[]{#Log_Event_Data .anchor}**Datos de registros (log):** Debe incluir lo siguiente:

> 1\. Fecha-Hora obtenida de un componente confiable del sistema.
>
> 2\. Nivel de severidad para cada evento
>
> 3\. Etiquetado de eventos relevantes a la seguridad, si se encuentran
> mezclados con otras entradas de la bitácora.
>
> 4\. Identidad de la cuenta/usuario que ha causado el evento.
>
> 5\. Dirección IP del origen asociado con el pedido.
>
> 6\. Resultado del evento (éxito o falla).
>
> 7\. Descripción del evento.

[]{#Availability .anchor} **Disponibilidad:** Medida de Accesibilidad y
    Usabilidad del sistema.

[]{#Exploit .anchor} **Exploit:** Forma de tomar ventaja de una vulnerabilidad.
    Tipicamente se trata de una acción intencional diseñada para comprometer
    los controles de seguridad del software utilizando una vulnerabilidad.

[]{#Cross_Site_Request_Forgery .anchor}
    **Falsificación de petición en sitios cruzados (CSRF):** Una aplicación
    externa o sitio web fuerza a un cliente a realizar un pedido a otra
    aplicación en la que el cliente posee una sesión activa. Las Aplicaciones
    son vulnerables cuando utilizan parámetros o URLs predecibles o conocidas y
    cuando el navegador transmite automáticamente toda la información de sesión
    con cada pedido a la aplicación vulnerable. (Este ataque es discutido
    específicamente en este documento por ser extremadamente común y poco
    comprendido).

[]{#Trust_Boundaries .anchor} **Frontera de Confianza:** Una frontera de
    confianza típicamente constituye los componentes del sistema bajo control
    directo. Todas las conexiones y datos prevenientes de sistemas fuera del
    control directo, incluyendo todos los clientes y sistemas gestionados por
    terceros, deben ser considerados no confiables y los datos provenientes de
    éstos deben ser validados en la frontera, antes de permitir cualquier
    futura interacción con el sistema.

**Gestión de Archivos:** Conjunto de controles que cubren la interacción
    entre el código y otro sistema de archivos.

**Gestión de memoria:** Conjunto de controles que cubren el uso de buffers y el
    direccionamiento de memoria.

**Gestión de sesión:** Conjunto de controles que ayudan a asegurar que la
    aplicación web maneja las sesiones HTTP de forma segura.

[]{#Impact .anchor}**Impacto:** Medida del efecto negativo en el negocio que
    resulta de la ocurrencia de un evento indeseado; pudiendo ser el resultado
    la explotación de una vulnerabilidad.

[]{#Integrity .anchor}**Integridad:** La garantía de que la información es
    precisa, completa y válida, y no ha sido alterada por una acción no
    autorizada.

**Manejo de Errores y Registro en bitácora:** Conjunto de prácticas que
    aseguran que las operaciones de manejo de errores y registro de eventos se
    gestionan correctamente.

[]{#Mitigate .anchor}**Mitigar:** Pasos tomados para reducir la severidad de
    una vulnerabilidad. Estos pueden incluir remover una vulnerabilidad, hacer
    una vulnerabilidad más difícil de explotar, o reducir el impacto negativo
    de una explotación exitosa.

**Prácticas Criptográficas:** Conjunto de controles que aseguran que las
    operaciones de criptografía dentro de la aplicación son manejadas de manera
    segura.

**Prácticas de Codificación Generales:** Conjunto de controles que cubren las
    prácticas de codificación que no son parte otras categorías.

**Protección de datos:** Conjunto de controles que asegurar que el software
    interactúa con la base de datos de forma segura, además de que la base de
    datos se encuentre configurada de forma segura.

[]{#Security_Requirements .anchor} **Requerimiento de Seguridad:** Conjunto de
    requerimientos funcionales y de diseño que ayudan a asegurar que el
    software se construye y despliega de forma segura.

[]{#Sanitize_Data .anchor} **Sanitizar:** El proceso de hacer seguros datos
    potencialmente peligrosos a través de la utilización de eliminación,
    reemplazo, codificación o \"escapeo\" de los caracteres que lo componen.

**Seguridad de Base de Datos:** Conjunto de controles que aseguran la
    interacción del software con la base de datos de una forma segura y que la
    base de datos se encuentra configurada de forma segura.

**Seguridad en las Comunicaciones:** Conjunto de controles que ayudan a
    asegurar que el software maneja de forma segura el envío y la recepción de
    datos.

[]{#System .anchor}**Sistema:** Término genérico que cubre sistemas operativos,
    servidores web, frameworks de aplicaciones y la infraestructura
    relacionada.

**Validación de entrada:** Conjunto de controles que verifican que las
    propiedades de los datos ingresados coinciden con las esperadas por la
    aplicación, incluyendo tipos, largos, rangos, conjuntos de caracteres
    aceptados y no se incluyen caracteres peligrosos conocidos.

[]{#Vulnerabilidad .anchor}**Vulnerabilidad:** Debilidad en un sistema que lo
    hace susceptible a ataque o daño.
