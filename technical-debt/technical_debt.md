---
title: Le debo dinero al Banco de México: Negociando la deuda técnica.
published: false
description: ¿Cómo podemos afrontar la deuda técnica? Un ejemplo dentro de un equipo de infraestructura
tags: techicaldebt, softwareengineering, tooling, devops
//cover_image: https://direct_url_to_image.jpg
---

## Apenas llegué y ya estan lloviendo los ~~golpes~~ tickets

A todos nos ha pasado. Llegas a un nuevo equipo, una nueva empresa, startup o consultora y tu primer semana te asignan un bug.
¿Será mi novatada? ¿Por qué está pasando esto? Probablemente te harás miles de preguntas, pero hay algo común en ese comportamiento: _**la deuda técnica**_.

La _**deuda técnica**_ se define como el trabajo adicional (o retrabajo) a una tarea o funcionalidad definida, regularmente por alguno de estos motivos (pueden ser más):

* Un camino fácil (a veces hackish) [Duck tape programmer](https://jeffreypalermo.com/2009/09/debunking-the-duct-tape-programmer/)
* Optimización prematura
* Mala definición o diseño
* Acoplamiento con algún componente externo o interno
* Falta de visión durante el refinamiento de la tarea

Este concepto tiene una analogía directa con la deuda monetaria en cualquier sistema financiero, es decir, si dicha deuda no se paga, esta seguirá generando intereses y dificultará su pago futuro o reimplementación, lo cual suele ser muy costoso por la posible pérdida de conocimiento.

Cabe destacar, que como cualquier deuda o préstamo que se pide al banco, siempre se puede negociar y dependerá del uso que decidamos darle.

Por ejemplo, podemos pedir un préstamo para poner un negocio y conforme tengamos cierta liquidez comenzar a pagarlo; o bien, irnos a un bar con nuestros amigos a gastarnos el ingreso recién generado.

La situación en la industria del software es la misma. _**No es malo tener deuda técnica, es malo cuándo no decides pagarla o la ignoras**_.

## Hola, este software fue mio pero yo ya me fui

Todos hemos tocado ese punto donde tenemos _**sistemas legados**_, procesos completos de ingeniería que tienen áreas enormes de oportunidad pero por ser "viejos" son juzgados y vistos como el principal problema del mundo actual.

Un _**sistema legado**_ es aquel que podemos clasificar como obsoleto, poco actualizado o bien, con visión distinta a lo que requiere el negocio actualmente. **Muchos** factores pueden hacer que un sistema sea clasificado o no como legado. Por ejemplo:

* Falta de soporte de algún framework, biblioteca o lenguaje.
* Exceso de deuda técnica en el sistema.
* Actualización de los estándares bajo los que el sistema fue diseñado.
* Cambios en la estructura del negocio que impiden su actualización gradual.
* Las métricas sobre cambios o actualizaciones suelen ser muy costosas (relacionado al mismo tiempo a la deuda técnica).
* Acoplamiento del proceso con algún hardware en específico y qué este haya sido deprecado.

Estos solo son algunos de los *muchos* factores que pueden marcar como legado a un sistema.
Pero la pregunta del millón: ¿Debo reemplazar todo mi sistema  y crearlo desde cero? ¿Puedo evitar tener un sistema legado?

Las respuestas pueden ser: No y No. Sin embargo, puedes **negociar, visualizar y planear** el crecimiento de tu sistema.

## ¿Aceptan pagos a meses sin intereses?

La forma más sana (como hasta en la vida misma) de atender las deudas que uno tiene es tener visibilidad de las mismas. Dentro de la industria del software la situación es (o se recomienda) sea la misma. Para poder llevar un rastreo más eficaz de la deuda técnica se recomiendan los siguientes puntos:

* Mantener un registro de las funcionalidades que generaron nueva deuda (código duplicado, falta de pruebas, diseño acoplado a un componente en específico, problemas de seguridad, etc)
* Clasificar de forma quincenal (por medio del refinamiento, en caso de usar el framework Scrum) la urgencia, impacto y tiempo de cada tarea de deuda técnica.
* Asignar de ser posible del 20 al 25 % de la velocidad del equipo a pagar la deuda técnica que más dolencias les trae para avanzar de una forma más eficiente
* En caso de ser posible, alinear las nuevas funcionalidades para que la nueva arquitectura sea más mantenible, contando con alta cohesión y bajo acoplamiento
* Volver a negociar la deuda en caso de ser posible.

Existen muchas técnicas para el manejo y mantenimiento de código legado, a continuación se listan algunas (de las muchas) existentes:

* Faking Collaborators
* Wrap Methods/Classes
* Breaking Dependencies
* Database Refactoring techniques
* Dependency breaking techniques (Extract interface, Parametrize constructor/method, encapsulate global dependencies, etc)
* Replacing conditionals with Polymorphism
* Remove Middle Man
* Improving via design patterns
* etc

Muchas otras técnicas existen para poder lidiar con código legado o refactoring, algunas de estas las podemos encontrar en el libro de [Refactoring: Improving the design of existing code](https://www.amazon.com/Refactoring-Improving-Existing-Addison-Wesley-Signature/dp/0134757599/ref=sr_1_1?crid=3KUVIUUV0I376&dchild=1&keywords=refactoring+second+edition&qid=1593039494&s=books&sprefix=Refac%2Cstripbooks-intl-ship%2C338&sr=1-1), [Working Effectively with Legacy Code](https://www.amazon.com/Working-Effectively-Legacy-Michael-Feathers/dp/0131177052/ref=sr_1_1?crid=WD8QVMAS4BSP&dchild=1&keywords=working+effectively+with+legacy+code&qid=1593039457&s=books&sprefix=working+effec%2Cstripbooks-intl-ship%2C193&sr=1-1), [Effective Java](https://www.amazon.com/Effective-Java-Joshua-Bloch/dp/0134685997/ref=sr_1_1?dchild=1&keywords=effective+java&qid=1593039432&s=books&sr=1-1) y [Refactoring Databases: Evolutionary Database Design](https://www.amazon.com/gp/product/0321774515/ref=as_li_tl?ie=UTF8&camp=1789&creative=9325&creativeASIN=0321774515&linkCode=as2&tag=passionaboutd-20), por mencionar algunas fuentes.

Estas técnicas (o métodos) pueden formar parte de nuestro set de trucos de magia para poder resolver problemas, sin embargo, habrá veces que tendremos que reemplazar bloques completos, no por eso perdemos la funcionalidad y la retrocompatibilidad en caso de ser necesario.

## Un caso de estudio: El equipo de tooling en Kueski

Sin entrar en detalles, en [Kueski](https://kueski.com/) contamos con un equipo enfocado a la creación de herramientas e infraestructura para hacer más fácil la vida al los desarrolladores/ingenieros y así puedan entregar valor al negocio, consierando calidad y velocidad. Cuestiones de CI/CD, aprovisionamiento, regresiones automatizadas, infraestructura, DevSecOps, Manejo de licencias, son algunos de los puntos con los que nos toca lidiar.

Desde la creación de este equipo (a la par de la implementación de la cultura DevOps) hemos empujado el financiamiento sano de la deuda técnica. Siendo un equipo de cinco ingenieros, hemos logrado dar soporte a más de 150 pipelines, incluyendo lo antes mencionado hasta la fase de entrega. Por mucho podemos decir de forma muy humilde ... __Tenemos deuda técnica__ ...

Nadie del equipo era (aún no lo somos) experto en ésta área, comenzamos a notar el incremento en tiempo para cambios pequeños y eso nos levantó un foco rojo. Desde Agosto del 2019, comenzamos a llevar el tracking puntuap de bugs/technical debt que ibamos encontrando o eran reportados por nuestros usuarios finales.

Hemos adoptado una forma de trabajo que consiste en los siguientes procesos.

* Trunk based development
* Feature flags
* System monitoring and alerting via Slack
* Service Desk (para peticiones externas o soporte a ingeniería)
* Scrum (para planeación y manejo de nuevos features)
* Kanban board (registro de deuda técnica)
* Pair programming
  * Temas de soporte
  * Diseño y arquitectura de nuevos features
  * Refactoring de deuda técnica
* Behavior Driven Development (70 - 80% de Coverage)
* _Documentar la api pública_
* _Si se rompe algo, no te preocupes, es simplemente que lo debemos mejorar_
* _El pipeline es mi pastor, y nada me faltará_
* _Be aware of your team_
* _Be clear and concise_

Cada qué detectamos que necesitamos seguir algún camino poco mantenible o tomar algún atajo para resolver una incidencia, reportamos el ticket de deuda técnica en el Kanban board con el siguiente formato:

* Nombre del projecto
* Descripción de la deuda a pagar
* Propuesta o arquitectura de solución (opcional)
* Esfuerzo estimado inicial (low, medium, high, a coffee)
* Esfuerzo después de terminada
* Comentarios extra de la tarea

Las tareas son refinadas por la persona que la reporta (a veces éstas salen a través de una sesión de pair programming, por ejemplo); agregando diagramas o bien, bosquejos de la solución. Cada dos semanas (lo que dura un sprint), dedicamos el 20% de la fuerza (de ser posible) para atacar la deuda técnica generada, esto con la finalidad de contar con una base lo suficientemente mantenible para seguir avanzando.

Elegimos las tareas de deuda técnica que se encuentran relacionadas a un componente que requiere una mejora o bien, una funcionalidad nueva. Todo esto lo hacemos adoptando feature flags y monitoreo (con alertas en Slack), lo cual nos ha permitido actuar de forma proactiva en lugar de esperar a que nos llegue la petición por medio de un ticket o una incidencia.

Regularmente fomentamos la solución compartida a través de pair programming. Sin dudarlo hemos aprendido (o mejor dicho, re-aprendido) que varias mentes piensan mejor que una. También decidimos no contar con un coverage del 100%, ya que ante todo, nos gusta contar con cierta flexibilidad para poder innovar sin tener que lidiar con un monolíto de pruebas. [Hay una plática muy buena sobre ésto](https://www.youtube.com/watch?v=EZ05e7EMOLM).

## Finalmente: Salir del buró de crédito

El pago de deuda técnica es algo que se tendrá que hacer y es parte de nuestro rol como ingenieros. Es parte de un desarrollo integral el saber tratar con sistemas con deuda y legados (suelen ir relacionados pero no son dependientes), ya que *no siempre podremos crear todo desde cero*.

Ante todo, _se empático con el equipo y el sistema actual_, el objetivo es aprender e incrementar la funcionalidad, no sólo juzgar la situación.

_Se humilde y juega en equipo_, a veces nosotros mismos generamos esa deuda técnica (sí, no somos para nada perfectos), trabaja a la par con el equipo actual o equipos involucrados, para ellos es importante contar con la visibilidad y comprender el estado del arte en ese momento, así se logrará atacar de mejor forma la deuda, no sólo con un contexto sesgado.

En Tooling fomentamos la discución, siempre apoyando los puntos de vista y empujando que exista una mejora contínua.

Aprender a lidiar con sistemas legados y deuda técnica no te hace más o menos ingeniero (a veces queremos abusar de estar siempre a la vanguardia), recuerda que todo lo nuevo en unos años, será nuevamente código legado.

## Referencias

* https://medium.com/the-andela-way/what-technical-debt-is-and-how-its-measured-ff41603005e3
* https://itpeernetwork.intel.com/information-security-and-technical-debt-management/
* https://caylent.com/fight-technical-debt
* https://jeffreypalermo.com/2009/09/debunking-the-duct-tape-programmer/
* https://www.amazon.com/Refactoring-Improving-Existing-Addison-Wesley-Signature/dp/0134757599/ref=sr_1_1?crid=3KUVIUUV0I376&dchild=1&keywords=refactoring+second+edition&qid=1593039494&s=books&sprefix=Refac%2Cstripbooks-intl-ship%2C338&sr=1-1
* https://www.amazon.com/Working-Effectively-Legacy-Michael-Feathers/dp/0131177052/ref=sr_1_1?crid=WD8QVMAS4BSP&dchild=1&keywords=working+effectively+with+legacy+code&qid=1593039457&s=books&sprefix=working+effec%2Cstripbooks-intl-ship%2C193&sr=1-1
* https://www.youtube.com/watch?v=EZ05e7EMOLM
* https://www.youtube.com/watch?v=URSWYvyc42M
