\newpage
## Apéndice B: Glosario {#glossary .list-paragraph}

[]{#AgenteDeAmenaza .anchor}**Agente de Amenaza:** Cualquier entidad que
puede poseer un impacto negativo en el sistema. Puede ser desde un
usuario malicioso que desea comprometer los controles de seguridad del
sistema; sin embargo, también puede referirse al mal uso accidental del
sistema o a una amenaza física como fuego o inundación.

**Autenticación:** Conjunto de Controles utilizados para verificar la
identidad de un usuario o entidad que interactúa con el software

[]{#AutenticaciónMultiFactor .anchor}**Autenticación Multi-Factor:**
Proceso de autenticación que le requiere al usuario producir múltiples y
distintos tipos de credenciales. Típicamente son basados en:

> -   algo que el usuario tiene, por ejemplo: una tarjeta inteligente
> -   algo que conoce, por ejemplo: un pin
> -   o algo que es, por ejemplo: datos provenientes de un lector biométrico

[]{#AutenticaciónSecuencial .anchor}**Autenticación secuencial:** Cuando
los datos de autenticación son solicitados en páginas sucesivas e vez de
ser solicitados todos de una sola vez en una única página.

[]{#Canonicalizar .anchor}**Canonicalizar:** Convertir distintas
codificaciones y representaciones de datos a una forma estándar
predefinida.

[]{#CaracteresConsideradosPeligrosos .anchor}**Caracteres considerados
peligrosos:** Cualquier carácter o representación codificada de un
carácter que puede afectar la operación intencionada de la aplicación o
sistema asociado por ser interpretado de una manera especial, fuera del
uso intencionado del carácter. Estos caracteres pueden ser utilizados
para:

> -   Alterar la estructura de las sentencias o código existente
>
> -   Insertar código inintencionado
>
> -   Alterar caminos
>
> -   Causar salidas inesperadas de rutinas o funciones
>
> -   Causar condiciones de error
>
> -   Obtener cualquiera de los efectos anteriores sobre el flujo de
>     aplicaciones o sistemas

[]{#CasosDeAbuso .anchor}**Caso de Abuso:** Especificación de un tipo de
interacción completa entre un sistema y uno o más actores, donde los
resultados de la interacción son perjudiciales para el sistema, uno de
los actores o uno de los interesados en el sistema

[]{#CodificaciónDeEntidadesHTML .anchor}**Codificación de Entidades
HTML:** Proceso por el cual se reemplazan ciertos caracteres ASCII por
sus entidades equivalentes en HTML. Por ejemplo: este proceso
reemplazaría el carácter de menor \"\<\" con su equivalente en HTML
\"&lt;\". Las entidades HTML son \'inertes\' en la mayoría de los
intérpretes, especialmente en los navegadores, pudiendo mitigar ciertos
tipos de ataque en los clientes.

**Codificación de Salida:** Conjunto de controles que apuntan al uso de
una codificación para asegurar que los datos producidos por la
aplicación son seguros.

[]{#CodificaciónDeSalidaContextualizada .anchor}**Codificación de Salida
Contextualizada:** Basar la codificación de salida en el uso que le dará
la aplicación. El método específico varía dependiendo en la forma que
será utilizado.

[]{#confidencialidad .anchor}**Confidencialidad:** Propiedad de la
información por la que se garantiza que está accesible únicamente a
entidades autorizadas.

**Configuración del sistema:** Conjunto de controles que ayuda a
asegurar que los componentes de infraestructura que brindan soporte al
software fueron desplegados de manera segura.

[]{#ConsultasParametrizadas .anchor}**Consultas parametrizadas (prepared
statements):** Mantiene la consulta y los datos separados a través del
uso de marcadores. La estructura de la consulta es definida utilizando
marcadores, la consulta SQL es enviada a la base de datos y preparada,
para luego ser combinada con los valores de los parámetros. Esto
previene a las consultas de ser alteradas debido a que los valores de
los parámetros son combinados con la consulta compilada y con el string
de SQL.

**Control de Acceso:** Un conjunto de controles que permiten o niegan el
acceso a un recurso de un usuario o entidad dado.

[]{#ControlDeSeguridad .anchor}**Control de seguridad:** Acción que
mitiga una vulnerabilidad potencial y ayuda a asegurar que el software
se comporta únicamente de la forma esperada.

[]{#DatosDeEstado .anchor}**Datos de estado:** Cuando datos o parámetros
son utilizados, ya sea por la aplicación o el servidor, emulando una
conexión persiste o realizando el seguimiento del estado de un cliente a
través de un proceso multi-pedido o transacción.

[]{#DatosDelRegistroDeLog .anchor}**Datos del registro de log:** Debe
incluir lo siguiente:

> -   Time stamp obtenida de un componente confiable del sistema
>
> -   Nivel de severidad para cada evento
>
> -   Marcado de eventos relevantes a la seguridad, si se encuentran
>     mezclados con otras entradas de la bitácora
>
> -   Identidad de la cuenta/usuario que ha causado el evento
>
> -   Dirección IP del origen asociado con el pedido
>
> -   Resultado del evento (suceso o falla)
>
> -   Descripción del evento

[]{#disponibilidad .anchor}**Disponibilidad:** Medida de Accesibilidad y
Usabilidad del sistema.

[]{#Exploit .anchor}**Exploit:** Forma de tomar ventaja de una
vulnerabilidad. Tipicamente se trata de una acción intencional diseñada
para comprometer los controles de seguridad del software utilizando una
vulnerabilidad.

[]{#CSRF .anchor}**Falsificación de petición en sitios cruzados
(CSRF):** Una aplicación externa o sitio web fuerza a un cliente a
realizar un pedido a otra aplicación en la que el cliente posee una
sesión activa. Las Aplicaciones son vulnerables cuando utilizan
parámetros o URLs predecibles o conocidas y cuando el navegador
transmite automáticamente toda la información de sesión con cada pedido
a la aplicación vulnerable. (Este ataque es discutido específicamente en
este documento por ser extremadamente común y poco comprendido).

[]{#FronteraDeConfianza .anchor}**Frontera de Confianza:** Una frontera
de confianza típicamente constituye los componentes del sistema bajo
control directo. Todas las conexiones y datos prevenientes de sistemas
fuera del control directo, incluyendo todos los clientes y sistemas
gestionados por terceros, deben ser considerados no confiables y ser
validados en la frontera, antes de permitir cualquier futura interacción
con el sistema.

**Gestión de Archivos:** Conjunto de controles que cubren la interacción
entre el código y otro sistema de archivos.

**Gestión de memoria:** Conjunto de controles de direccionamiento de
memoria y uso de buffers.

**Gestión de sesión:** Conjunto de controles que ayudan a asegurar que
la aplicación web maneja las sesiones HTTP de forma segura.

[]{#impacto .anchor}**Impacto:** Medida del efecto negativo en el
negocio que resulta de la ocurrencia de un evento indeseado; pudiendo
ser el resultado la explotación de una vulnerabilidad.

[]{#integridad .anchor}**Integridad:** La seguridad de que la
información es precisa, completa y válida, y no ha sido alterada por una
acción no autorizada.

**Manejo de Errores y Registro en bitácora:** Conjunto de prácticas que
aseguran que las operaciones de manejo de errores y registro en bitácora
se manejan correctamente.

[]{#mitigar .anchor}**Mitigar:** Pasos tomados para reducir la severidad
de una vulnerabilidad. Estos pueden incluir remover una vulnerabilidad,
hacer una vulnerabilidad más difícil de explotar, o reducir el impacto
negativo de una explotación exitosa.

**Prácticas Criptográficas:** Conjunto de controles que aseguran que las
operaciones de criptografía dentro de la aplicación son manejadas de
manera segura.

**Prácticas de Codificación Generales:** Conjunto de controles que
cubren las prácticas de codificación que no son parte otras categorías.

**Protección de datos:** Conjunto de controles que ayudan a asegurar que
el software maneja de forma segura el almacenamiento de la información.

[]{#RequerimientoDeSeguridad .anchor}**Requerimiento de Seguridad:**
Conjunto de requerimientos funcionales y de diseño que ayudan a asegurar
que el software se construye y despliega de forma segura.

[]{#Sanitizar .anchor}**Sanitizar:** El proceso de hacer seguros datos
potencialmente peligrosos a través de la utilización de remoción,
reemplazo, codificación o \"escaping\" de los caracteres que lo
componen.

**Seguridad de Base de Datos:** Conjunto de controles que aseguran la
interacción del software con la base de datos de una forma segura y que
la base de datos se encuentra configurada de forma segura.

**Seguridad de Comunicaciones:** Conjunto de controles que ayudan a
asegurar que el software maneja de forma segura el envío y la recepción
de datos.

[]{#sistema .anchor}**Sistema:** Término genérico que cubre sistemas
operativos, servidores web, frameworks de aplicaciones e infraestructura
relacionada.

**Validación de entrada:** Conjunto de controles que verifican que las
propiedades de los datos ingresados coinciden con las esperadas por la
aplicación, incluyendo tipos, largos, rangos, conjuntos de caracteres
aceptados excluyendo caracteres peligrosos conocidos.

[]{#Vulnerabilidad .anchor}**Vulnerabilidad:** Debilidad en un sistema
que lo hace susceptible a ataque o daño.
