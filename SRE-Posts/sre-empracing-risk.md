---
title: Site Reliability Engineering: Embracing Risk and Disaster Management
published: true
description: ¿Cómo manejamos los riesgos en el Software? 
tags: sre, techical debt, software design, software architecture
cover_image: https://jresendiz27-public-assets.s3.us-east-2.amazonaws.com/SRE-Posts/EmbracingRisk/image.jpg
---

> _"Conflict isn't an inevitable part of offering a software service"_ - [Google Site Reliability Engineering](https://landing.google.com/sre/sre-book/chapters/introduction/).

## ¿Qué es Site Reliability Engineering?

Dentro del área del desarrollo de software, es parte de nuestro día a día resolver problemas de cualquier tipo, incluyendo el conciliar una entrega de alguna funcionalidad, la reparación de algún defecto o mejora al sistema actual.

Site Reliability Engineering, es un concepto que Google ha hecho famoso desde hace varios años, cuyo principal objetivo es unificar la parte de diseño de software con la parte operativa de un producto/servicio, tomando en cuenta factores cómo la resiliencia, seguridad, entrega, manejo de riesgos del ciclo del desarrollo de un sistema informático.

Los equipos de SRE se encuentran enfocados a procesos de ingeniería y entrega de valor al producto. Sin un proceso constante de análisis,diseño e implementación, [la carga operativa suele incrementar](https://landing.google.com/sre/sre-book/chapters/eliminating-toil/) y eso implica contar con más personal para ejecutar la carga de trabajo.

Uno de los enfoques principales de SRE, es reducir esa carga operacional manteniendo una razón, ahdoc a las necesidades del producto sin comprometer la calidad del mismo (la propuesta de Google es 50%/50%. 

Es decir, mantener la carga operativa y el proceso de innovación/automatización de forma que los equipos de trabajo no sólo se enfoquen en atender problemas operacionales, si no también realizar mejoras, [resolver deuda técnica](https://www.toptal.com/finance/part-time-cfos/technical-debt), innovar sobre el producto en cuestión.

En esta serie de 3 publicaciones, estaremos hablando de temas relacionados a SRE y cómo estos conceptos nos pueden ayudar a mejorar nuestro ritmo de trabajo, trabajando a la par con las áreas involucradas para que nuestros sistemas cumplan con los requisitos de calidad, disponibilidad, seguridad propuestos por el equipo o la competencia en sí.

## Disponibilidad: Manejando el riesgo y los desastres en el software

**Todos los sistemas son propensos a fallos**. Si un sistema aparenta no tener fallos, es probable que los tenga, simplemente aún no se han presentado.

Cuándo existe algún tipo de fallo o riesgo en algún sistema, éste desgasta la relación con los usuarios (sean internos o externos), uno de los objetivos de SRE es fomentar la reducción o acotación de éste riesgo.

Existen varios factores que determinan el costo de los factores de disponibilidad, los dos principales son:

* **Redundancia**: Ya sea en equipo físico, recurso humano o espacio para lograr ejecutar un plan de acción ante un fallo (o responder ante alguna anomalía)
* **Costo de oportunidad**: Los recursos que una organización desea considerar para el diseño de funcionalidades minimizando el riesgo. Estos recursos no sólo se enfocan a la disponibilidad/seguridad; si no también pueden representar nuevas funcionalidades o mejoras al sistema/producto.

Es importante mencionar que no todos los recursos deben ser enfocados a la disponibilidad, ni tampoco al desarrollo de nuevas funcionalidades; ya que este balance puede ir cambiando con el paso del tiempo.

Factores como el diseño del sistema, el cliente final, criticidad del servicio, cantidad de deuda técnica, por mencionar algunos, son pilares a considerar para definir cuál debe ser la disponibilidad de un servicio.

La mejor forma de poder tomar una decisión es teniendo métricas dentro de los sistemas, sin embargo, si tomamos un sistema nuevo, se puede conciliar contar con algún tipo de holgura y conforme pasa el tiempo (un trimestre, por ejemplo) determinar el peso de cada uno de los factores y así mejorar la propuesta.

Dentro del libro de SRE, se mencionan las siguientes dos propuestas de medición de disponibilidad de un sistema:

![Disponibilidad](https://jresendiz27-public-assets.s3.us-east-2.amazonaws.com/SRE-Posts/EmbracingRisk/disponibilidad_1.png)

![Disponibilidad](https://jresendiz27-public-assets.s3.us-east-2.amazonaws.com/SRE-Posts/EmbracingRisk/disponibilidad_2.png)

Para poder afrontar el riesgo dentro de nuestros sistemas es necesario tomar en cuenta las siguientes preguntas:

* Disponibilidad
  * ¿Cuál es el nivel requerido de disponibilidad?
  * ¿Cómo es el manejo de las integraciones con terceros en caso de que éstas fallen?
  * ¿Cómo podemos aprovechar el costo de oportunidad para ayudar a reducir los riesgos?
* Negocio
  * ¿Cuál es el nivel de disponibilidad que provee la competencia?
  * ¿El servicio impacta directamente en las ganancias?
  * ¿El servicio es gratuito o de paga? (Considerando un [SLA](https://en.wikipedia.org/wiki/Service-level_agreement))
  * ¿Actualmente cuál es el proceso de control de calidad con el que se cuenta? (El balance en la [pirámide de pruebas](https://martinfowler.com/articles/practical-test-pyramid.html))
* Diseño y Arquitectura
  * ¿Las métricas actuales fueron diseñadas considerando la deuda técnica?
  * ¿Cuál es la frecuencia de actualización del servicio? ¿Se intenta encontrar un nicho en el mercado o es un servicio ya establecido?
  * ¿Cómo es el proceso de monitoreo actual? (logs, red, consultas, tiempos de respuesta, consumo de memoria, etc)
  * ¿Es necesario contar con algún requisito de seguridad? ¿El servicio se encuentra dentro de una [Trusted Computer Base (TBC)](https://blog.finjan.com/trusted-computing-base/)?

Estas preguntas pueden formar parte del diseño y creación de cualquier sistema que desee contar con [alta disponibilidad](https://www.atlassian.com/blog/statuspage/high-availability), y ser consideradas no sólo a nivel sistema, también a nivel funcionalidad y adecuarse a cómo sea necesario.

Usualmente la disponibilidad es calculada por el número de 9s que el proveedor del servicio puede garantizar.  *Una disponibilidad de 99.9% habla de un porcentaje de baja disponibilidad de apróximadamente 8.76 horas al año.* Cada número nueve agregado a ese valor, implica un análisis profundo de la arquitectura actual, infraestructura y costos: en horas hombre, contratos con proveedores y mantenimiento.

Siempre existe la alternativa de contar con distintos niveles de disponibilidad dependiendo el servicio, con base en la cantidad de subscriptores/funcionalidades, así los clientes pueden elegir el plan que más les convenga (cambiando los beneficios y el esquema de cobro).

## Trabajando para ser seguros y resilientes

Un sistema que sólo se encuentra orientado a cuestiones de seguridad y resiliencia, sin contemplar los requerimientos de funcionalidad de negocio, tiende a ser un sistema rígido y poco usable. Es importante tener en cuenta lo antes mencionado para conciliar estos requerimientos y saber que siempre existirá un riesgo que debemos considerar cómo aceptable para no dificultar el flujo de trabajo.

Durante la creación de un proyecto, la etapa de toma de requerimientos y diseño es indispensable para poder delimitar las fronteras del sistema, es decir, el acoplamiento con otros módulos, bases de datos, bibliotecas, sistemas de archivos, interfaces de red y servicios externos.

Existen patrones de diseño y de arquitectura que pueden ayudar a disminuir el riesgo de acoplamiento con algún sistema o biblioteca; sin embargo, el riesgo siempre estará y no por estar aislado dejará de existir.

Dentro del flujo de trabajo de cualquier equipo, es indispensable contar con ciertas etapas durante el desarrollo para garantizar la integridad y calidad del producto que entregamos. A continuación se mencionan algunas fases a considerar:

* Análisis de dependencias
* Análisis de licencias
* Análisis de vulnerabilidades
* Cobertura de código
* [Code smells](https://blog.codinghorror.com/code-smells/)/Linting
* Pruebas unitarias, de integración, de sistema

Estas fases son algunas que pueden ser tomadas como parte de cualquier flujo de trabajo, siempre de forma automatizada por medio de algún servicio de integración continua como [Jenkins](https://www.jenkins.io/), [CircleCI](https://circleci.com/), [TravisCI](https://travis-ci.org/), [Github Actions](https://github.com/features/actions), etc. Estas fases de desarrollo pueden fungir como un integrante más al equipo de trabajo; un integrante imparcial con una visión y procesos automatizados.

El contar con procesos automátizados y replicables, es parte de la cultura Devops. Debemos ver éste proceso de automatización como una inversión a largo plazo para mejorar la calidad, más allá de un bloqueante durante las etapas tempranas del desarrollo.

![This is how we fail](https://jresendiz27-public-assets.s3.us-east-2.amazonaws.com/SRE-Posts/EmbracingRisk/software_security.jpg)

Tocando temas de seguridad, al igual que al hablar de temas de resiliencia, entre más seguro sea un sistema, tiende a ser menos usable, ya que cada capa de seguridad puede llegar a entorpecer la usabilidad y tiempos de respuesta de un servicio; y entre más componentes llegue a tener un sistema, mayor es su superficie de ataque.

Muchos de los factores de seguridad y disponibilidad suelen ser no tangibles y en general abstractos respecto a temas de negocio, por lo mismo no son tomados como prioridad durante las fases de desarrollo; también suelen ser emergentes conforme pasa el tiempo.

A nivel seguridad, esta puede ser una lista de referencia de factores a tomar en cuenta:

* ¿Cómo el servicio se encuentra estructurado (módulos, monolito, microservicios)?
* ¿Cuáles son los mecanismos de comunicación entre servicios (Rest, RPC, Sockets)?
* ¿Cómo se encuentran estructuradas las pruebas para realizar validaciones de seguridad o sanitización?
* ¿Se debe contar con algún tipo de restricción por cuestiones de * legislación o manejo de datos?
¿Qué información con la que tratamos debe ser cifrada o sanitizada?
* ¿Cuáles son las técnicas de autenticación mínimas requeridas para garantizar la auditabilidad de accesos?
* ¿Se cuenta actualmente con un proceso de aplicación de parches de seguridad en el sistema actual?
* ¿El sistema cuenta con los roles necesarios para garantizar [el principio del menor privilegio](https://heimdalsecurity.com/blog/what-is-the-principle-of-least-privilege/)?
* ¿Dentro del diseño se consideró contar con CIA [(Confidentiality, Integrity, Availability)](https://developer.mozilla.org/en-US/docs/Archive/Security/Confidentiality,_Integrity,_and_Availability)?

Una estrategia que puede ayudar al SRE, Product Owners y equipos de ingeniería en general, es seguir un template de requerimiento/diseño con las preguntas que se consideran relevantes, por ejemplo:

```markdown
Feature #1

Description:
    A description about the feature.

External/Internal Dependencies:
    A list of all the possible dependencies that might be used by the system itself
    and how they will be managed.

SLA:
    Service Level Agreements that needs to be achieved for this feature.
    If they don't exists; at least SLO should be managed for the service

Security and Data considerations:
    If there is any consideration about how the service's data has to be handled
    (obfuscating or anonymizing data). This point it's suitable to describe the
    minimum security levels for the feature/system, at least the service
    should live in a TCB. If the managed data needs to be encrypted, this needs
    to be handled here, like the used algorithm or provider.

Do the service creates new technical debt?
    It's important to keep in track all the technical debt created/paid by the team,
    so it doesn't overwhelm the deliver velocity.

Service/Feature technical requirements:
    Database versions, languages, dependencies, coverage levels.

Architecture diagrams:
    If required, the service diagrams are suitable for a quick review.
```

Como punto indispensable, [se recomienda que todos los sistemas diseñados puedan contar con un proceso de auditabilidad](https://blog.pythian.com/building-mature-devops-practice-implementing-devops-best-practices-throughout-application-lifecycle/), con la finalidad de poder afrontar las incidencias que puedan llegar a presentarse; brindando la visibilidad y permisos mínimos para resolver el problema.

[El manejo de logs es una parte indispensable para el monitoreo de un sistema](https://dzone.com/articles/best-practices-for-efficient-log-management-and-mo), y no sólo es contar con éstos, también que deben proveer información importante sobre los procesos que un sistema ejecuta, sin exponer información sensible sobre clientes, por ejemplo.

Existen muchas alternativas para manejar el monitoreo dentro de tus aplicaciones, servicios como [Prometheus](https://prometheus.io/), [Datadog](https://www.datadoghq.com/), [ELK](https://www.elastic.co/what-is/elk-stack), [AWS Cloudwatch](https://aws.amazon.com/cloudwatch/), etc; pueden ser integrados a tu sistema. Muchos de estos servicios te permiten generar dashboards para poder realizar un análisis de lo que pasa actualmente.

La inclusión de alertas (con base en ciertos errores o umbrales de las métricas) nos permite reaccionar ante algún tipo de incidencia, ya sea de forma manual o programática; además de mantener a los equipos de trabajo en sincronía de lo que pasa en los ambientes productivos.

Dentro de las métricas que pueden formar parte de un sistema, estas son las que se recomienda mantener monitoreadas:

* Uso de memoria
* Logs de procesos críticos de sistema operativo (journalctl)
Logs del proceso productivo (Se recomienda que sean mostrados directamente en el STDOUT, así será más fácil su integración con  contenedores)
* Tráfico de red
* Métricas de CPU
* Uso de disco

La periodicidad de recolección de las métricas, dependerá de la razón de ser del componente; por ejemplo: Imaginemos un servicio con con una interacción constante a una API externa y  un proceso matemático complejo. Dado esa breve (y muy vaga) descripción, probablemente el uso de disco no sea una métrica que debamos obtener minuto a minuto, sin embargo, el uso de CPU y el tráfico de red se convierten en válidas opciones para tener con una mayor frecuencia.

## Todo explotó: Un plan ante el desastre (DRP)

![This is how we fail](https://jresendiz27-public-assets.s3.us-east-2.amazonaws.com/SRE-Posts/EmbracingRisk/disaster_fail.jpeg)

Por más intentos materiales y humanos invertidos en cualquier proceso de ingeniería, estos tendrán defectos y existirán errores; cómo SREs, es nuestra misión inculcar una cultura orientada a evitar desastres, al mismo tiempo contar con planes de contingencia para mitigar posibles errores humanos, ventanas de mantenimiento, incidentes de seguridad, etc.

Un DRP (Disaster Recovery Plan) consta del conjunto de procedimientos, acciones y puntos de contacto mínimos para mantener el negocio funcional mientras se trabaja en recuperar el estado más reciente del sistema.

Este tipo de plan se debe realizar a la par con todas las áreas de negocio, no sólo desde ingeniería;  para poder garantizar la mayor cobertura operativa en caso de algún incidente. Los DRP se deben encontrar actualizados y adecuados al giro actual de la empresa.

Dentro del desarrollo de un plan de recuperación, [existen algunos conceptos base que deben ser tomados en cuenta](https://www.gocloudwave.com/disaster-recovery-101-update-review/):

* RTO: Recovery Time Objective. Se define cómo el tiempo que necesita la empresa para poner sus sistemas nuevamente en línea y funcionales después de que un evento fue declarado.
* DT: Decision Time. Muchos lo consideran el tiempo más crítico dentro de un plan de contingencia; este tiempo involucrado desde que se conoce la incidencia hasta que se inicia con el plan de recuperación. Este tiempo es crucial, ya que depende de los managers, leads, CTO, SREs el tomar la elección de ejecutar. A veces el tiempo invertido en soluciones por parte del equipo de ingeniería puede verse reflejado en minutos u horas con pérdidas de información. No existe una fórmula perfecta para esta métrica y depende de la criticidad del incidente, servicios afectados, horas del día o las personas involucradas.
* RPO: Recovery Point Objective. Es el tiempo entre tu último respaldo y cuándo se decidió ejecutar el plan de recuperación. Estos respaldos se pueden dejar en otras cuentas o medios físicos, de cualquier forma, es importante recordar que la consistencia de la información es la más importante.
* WRT: Working Recovery Time. Es el tiempo estimado en ejecutar el plan de recuperación desde que inicia hasta que éste mismo es culminado. Este tiempo puede ser tan crítico como la información involucrada en el sistema mismo.
* MTD: Maximum Tolerable Downtime. El tiempo máximo permitido en el que los sistemas pueden estar como no disponibles, es decir, el tiempo que la empresa puede tolerar no contar con un sistema funcional.

![DRP Concepts](https://jresendiz27-public-assets.s3.us-east-2.amazonaws.com/SRE-Posts/EmbracingRisk/concepts.png)

El DRP debe estar documentado y ser conocido por todas las áreas involucradas, además de contar con un proceso de revisión (dependiendo el servicio y la tasa de cambio del mismo) que puede ir de un trimestre, hasta un par de años.

## Conclusión

SRE es un tema integral dentro del desarrollo de una aplicación o sistema, forma parte integral de los procesos operativos y de ingeniería. Es importante tener en cuenta que **no existe una fórmula para solucionar todos nuestros problemas de riesgo y disponibilidad**, la baraja de opciones es infinita, agregando también la gran velocidad con la que la industria de software suele moverse.

Sin embargo, este tipo de cuestionamientos y lineamientos son algo que no ha cambiado a lo largo de los años en la industria del software. Deben ser considerados como guías para un trabajo contínuo y de calidad, más allá de normas por seguir.

**Los desastres siempre ocurrirán sea cual sea su magnitud.** SRE fomenta una cultura para afrontar este tipo de retos de forma ordenada, segura y eficiente; sin dejar detrás la importancia que tiene el negocio y los clientes en el proceso.

La flexibilidad y la aceptación de éstos horizontes desconocidos nos permiten siempre tener un campo fértil para la innovación, siempre y cuando se tenga un diseño flexible y estructurado de lo que deseamos alcanzar.

### Recursos

* <https://landing.google.com/sre/sre-book/chapters/introduction/>
* <https://landing.google.com/sre/sre-book/chapters/eliminating-toil/>
* <https://www.toptal.com/finance/part-time-cfos/technical-debt>
* <https://en.wikipedia.org/wiki/Service-level_agreement>
* <https://martinfowler.com/articles/practical-test-pyramid.html>
* <https://blog.finjan.com/trusted-computing-base/>
* <https://www.atlassian.com/blog/statuspage/high-availability>
* <https://blog.codinghorror.com/code-smells/>
* <https://heimdalsecurity.com/blog/what-is-the-principle-of-least-privilege/>
* <https://developer.mozilla.org/en-US/docs/Archive/Security/Confidentiality,_Integrity,_and_Availabilityc>
* <https://dzone.com/articles/best-practices-for-efficient-log-management-and-mo>
* <https://www.gocloudwave.com/disaster-recovery-101-update-review/>
* <https://blog.pythian.com/building-mature-devops-practice-implementing-devops-best-practices-throughout-application-lifecycle/>
