En UX (y en metodologías ágiles en general), una **user story** o **historia de usuario** es una descripción breve, escrita en lenguaje sencillo, de una funcionalidad contada desde la perspectiva de la persona que la va a usar. Su objetivo es que el equipo no pierda de vista _quién_ necesita algo, _qué_ necesita y _por qué_, en lugar de centrarse solo en especificaciones técnicas.

El formato clásico es:

> **Como** [tipo de usuario], **quiero** [acción u objetivo], **para** [beneficio o motivación].

Por ejemplo: _"Como cliente frecuente de una tienda online, quiero guardar mis métodos de pago, para no tener que introducirlos cada vez que compro."_

La parte del "para" es la más valiosa desde el punto de vista de UX, porque expresa la necesidad real detrás de la petición. Eso permite al diseñador explorar distintas soluciones: quizá el problema de fondo es que el checkout es lento, y hay más formas de resolverlo que guardar tarjetas.

Las historias suelen acompañarse de **criterios de aceptación**, que definen cuándo se considera cumplida. Siguiendo el ejemplo, podrían ser que el usuario pueda guardar varias tarjetas, elegir una como predeterminada y eliminarlas cuando quiera.

En el trabajo de UX cumplen varias funciones: traducen la investigación con usuarios (entrevistas, personas, journey maps) en requisitos concretos, sirven de lenguaje común entre diseño, desarrollo y producto, y ayudan a priorizar el trabajo en un backlog. Un criterio muy usado para escribir buenas historias es **INVEST**: que sean independientes, negociables, valiosas, estimables, pequeñas (_small_) y verificables (_testable_).

Conviene distinguirlas de conceptos cercanos: las **personas** describen _quién_ es el usuario, los **casos de uso** detallan paso a paso la interacción con el sistema, y los **job stories** (una alternativa) se centran en la situación en vez del rol, con el formato _"Cuando [situación], quiero [motivación], para [resultado]"_.


Ejemplo:
```mermaid
flowchart LR
    EPIC["<b>ÉPICA</b><br>Checkout de la tienda online"]

    US1["<b>US-01 · Guardar métodos de pago</b><br>Como cliente frecuente,<br>quiero guardar mis tarjetas,<br>para no introducirlas en cada compra."]
    US2["<b>US-02 · Compra como invitado</b><br>Como cliente nuevo,<br>quiero comprar sin crear una cuenta,<br>para terminar la compra rápidamente."]
    US3["<b>US-03 · Coste total visible</b><br>Como comprador,<br>quiero ver envío e impuestos antes de pagar,<br>para evitar sorpresas en el precio final."]
    US4["<b>US-04 · Editar el carrito</b><br>Como comprador,<br>quiero cambiar cantidades desde el carrito,<br>para no volver a la ficha del producto."]
    US5["<b>US-05 · Seguimiento del pedido</b><br>Como cliente que ya compró,<br>quiero recibir avisos del estado del envío,<br>para saber cuándo llegará mi pedido."]

    AC1["✅ Guardar varias tarjetas<br>✅ Marcar una como predeterminada<br>✅ Eliminar tarjetas en cualquier momento"]
    AC2["✅ Solo se pide email y dirección<br>✅ Opción de crear cuenta al final<br>✅ Recibe confirmación por email"]
    AC3["✅ Desglose visible desde el carrito<br>✅ Se recalcula al cambiar dirección<br>✅ El total no cambia en el último paso"]
    AC4["✅ Botones + / − por producto<br>✅ Eliminar producto con opción de deshacer<br>✅ El total se actualiza al instante"]
    AC5["✅ Aviso al enviar y al entregar<br>✅ Enlace al seguimiento del transportista<br>✅ Elegir email o notificación push"]

    EPIC --> US1 & US2 & US3 & US4 & US5
    US1 -.-> AC1
    US2 -.-> AC2
    US3 -.-> AC3
    US4 -.-> AC4
    US5 -.-> AC5

    classDef epic fill:#6c4ee3,stroke:#4b32b8,color:#ffffff
    classDef story fill:#e8f0fe,stroke:#4a7bd1,color:#1a1a1a
    classDef criteria fill:#eaf7ee,stroke:#3f9a5c,color:#1a1a1a

    class EPIC epic
    class US1,US2,US3,US4,US5 story
    class AC1,AC2,AC3,AC4,AC5 criteria
```
