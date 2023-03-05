\newpage
# Apéndice A: Visión General de la Seguridad en el Software y sus Principales Riesgos {#software-security-and-risk-principles-overview .list-paragraph}

La construcción de software seguro requiere una comprensión básica de
los principios de seguridad. Si bien escapa al objetivo de esta guía una
revisión exhaustiva de estos principios, se proporciona una visión general y
 rápida de los mismos.

El objetivo de la seguridad en el software es el de mantener la
[*confidencialidad*](#Confidentiality), [*integridad*](#Integrity) y
[*disponibilidad*](#Availability) de los avtivos de información de
modo de permitir el desarrollo exitoso de las operaciones del negocios. Este
 objetivo se consigue con la implementación de [*controles de seguridad*](#Security_Controls).
La presente guía pone foco en los controles técnicos específicos para
 [*mitigar*](#Mitigate) la presencia de [*vulnerabilidades*](#Vulnerability)
 de ocurrencia frecuentes en el software. Si bien el foco principal está en
 las aplicaciones web y la infraestructura que las soporta, la mayoría de los
 lineamientos pueden aplicarse en cualquier plataforma de desarrollo de software.

Es de gran utilidad comprender qué se entiende por un riesgo, con el fin
de proteger al negocio de riesgos inaceptables derivados de su
dependencia con el software. Un riesgo es una combinación de factores que
amenazan el correcto funcionamiento del negocio.
Puede ser definido conceptualmente como: un [*agente amenazante*](#Threat_Agent)
 que interactúa con el [*sistema*](#System), que puede tener una
 [*vulnerabilidad*](#Vulnerability) a ser [*explotada*](#Exploit) de
 forma de generar un [*impacto*](#Impact). Si bien este puede resultar
 un concepto abstracto, se lo puede pensar de esta forma: un ladrón
 de autos (agente amenazante) recorre un estacionamiento verificando
 los vehículos (el sistema) en busca de una
 puerta sin trabar (la vulnerabilidad) y, cuando encuentra una, la abre
 (situación a ser explotada) y toma algo de dentro del mismo (el impacto).
 Todos estos factores juegan un rol en el desarrollo de software seguro.

Existe una diferencia fundamental entre el enfoque que adopta un equipo
de desarrollo y el que toma alguien que está atacando la aplicación. Un equipo
 de desarrollo adopta un enfoque basado en lo que tiene intenciones de realizar.
 En otras palabras, están diseñando una aplicación para que realice tareas
 específicas basándose en los requerimientos funcionales y casos de uso que han
 sido documentados. Un atacante, por otra parte, está más interesado en lo que
 puede llegar a hacerse con la aplicación en cuestión y opera bajo el principio
 de \"cualquier acción que no haya sido denegada de forma expresa, está permitida\".
Para hacer frente a esto, se deben integrar algunos elementos adicionales en
 las etapas tempranas del ciclo de desarrollo de software. Estos nuevos elementos
 son los [*requerimientos de seguridad*](#Security_Requirements) y los
 [*casos de abuso*](#Abuse_Case). Esta guía fue creada para ayudar a identificar
 requerimientos de seguridad de alto nivel y hacer frente a muchos escenarios de
 abuso comunes.

Es importante que los equipos de desarrollo web entiendan que los
controles implementados en el cliente, tales como la validación de entrada de
 datos, campos ocultos y controles en la interfaz (por ejemplo: menús desplegables
 y botones de opción) brindan poco o nulo beneficio desde el punto de vista de
 la seguridad. Un atacante puede utilizar herramientas tales como proxies del
 lado del cliente (por ejemplo: OWASP ZAP o Burp) o herramientas de capturas de
 paquetes de red (como WireShark) para analizar el tráfico de la aplicación y
 enviar solitudes hechas a medida, sin siquiera pasar por la interfaz. Además,
 Applets de Java, programas Flash y otros objetos de ejecución del lado del
 cliente pueden ser descompilados y analizados en busca de fallas.

Las fallas de seguridad en el software pueden introducirse en cualquiera
de las etapas del ciclo de desarrollo del software, pudiendo:

- No identificar requerimientos de seguridad desde el inicio.

- Crear diseños conceptuales que contengan errores en la lógica.

- Utilizar prácticas débiles de codificación que introduzcan vulnerabilidades
técnicas.

- Implantación del software de forma inapropiada.

- Introducción de fallas durante el mantenimiento o actualización del producto.

Es importante además entender que las vulnerabilidades del software
 pueden escapar los límites del software mismo. Dependiendo de la naturaleza del
 software, la vulnerabilidad y la infraestructura que le da soporte, el impacto
 del éxito en la explotación puede comprometer a una o todas las siguientes:

- El software y su información asociada.

- Los sistemas operativos de los servidores asociados.

- La base de datos del backend.

- Otras aplicaciones en el entorno compartido.

- El sistema del usuario final.

- Otro software con el que interactúe el usuario.
