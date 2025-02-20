---
lab:
  task: Configure Communication Compliance
  exercise: Exercise 4 - Configure Communication Compliance
---
## Inquilinos de WWL: términos de uso

Si se te proporciona un inquilino porque estás realizando un curso dirigido por un instructor, ten en cuenta que ese inquilino está disponible únicamente como apoyo para los laboratorios prácticos del curso.

Los inquilinos no deben compartirse ni usarse para otros fines que no sean los de los laboratorios prácticos. El inquilino usado en este curso es un inquilino de prueba y no se puede usar ni tener acceso a él después de que la clase haya terminado y no es apto para la extensión.

Los inquilinos no se deben convertir a suscripciones de pago. Los inquilinos obtenidos como parte de este curso siguen siendo propiedad de Microsoft Corporation y nos reservamos el derecho de acceso y recuperación en cualquier momento.

# Ejercicio 4: Tareas de aptitud

- **Directiva de plantilla predefinida**: crea una directiva de cumplimiento de comunicación con una plantilla predefinida.
- **Directiva de plantilla personalizada**: crea una directiva de cumplimiento de comunicación modificando una plantilla predefinida.
- **Directiva de comunicación personalizada**: crea una directiva de cumplimiento de comunicación única adaptada a necesidades organizativas específicas.

## Tarea 1: Creación de una directiva de cumplimiento de comunicación a partir de una plantilla

En esta tarea, crearás una directiva con una plantilla predefinida para abordar rápidamente escenarios comunes de cumplimiento.

1. En Microsoft Edge, ve al Portal de Microsoft Purview, `https://purview.microsoft.com`, e inicia sesión.
1. Selecciona **Soluciones** > **Cumplimiento de comunicaciones**.
1. En el panel de navegación izquierdo, selecciona **Directivas**.
1. Selecciona **Crear directiva** y revisa las plantillas de directiva disponibles:

   - **Interacciones de Microsoft Copilot**: supervisa todas las interacciones con Copilot para Microsoft 365.
   - **Contenido inapropiado**: detecta el contenido de odio, violencia, sexual y de autolesiones en Microsoft Teams.
   - **Texto inapropiado**: marca amenazas, discriminación y acoso en Exchange Online, Microsoft Teams y Viva Engage.
   - **Imágenes inapropiadas**: identifica imágenes adultas y subidas de tono en Exchange Online y Microsoft Teams.
   - **Información confidencial**: supervisa la información confidencial en Exchange Online, Microsoft Teams y Viva Engage con un porcentaje de revisión inferior.
   - **Cumplimiento normativo financiero**: asegura el cumplimiento normativo financiero en Exchange Online, Microsoft Teams y Viva Engage.
   - **Conflicto de interés**: detecta posibles conflictos de interés en Exchange Online, Microsoft Teams y Viva Engage.

1. Selecciona la plantilla de directiva para **Detectar texto inapropiado**.
1. En la página flotante **Detectar comunicaciones para texto inapropiado** de la derecha, escribe el usuario que revisará las alertas de cumplimiento de comunicación en el campo **Revisores**.
1. Selecciona **Crear directiva** en la parte inferior de la página flotante y, después, selecciona **Cerrar** en la página **La directiva se ha creado**.

Has creado correctamente una directiva de cumplimiento de comunicaciones con la plantilla **Detectar texto inapropiado**.

## Tarea 2: Creación de una directiva de cumplimiento de comunicación a partir de una plantilla personalizada

Aquí modificarás una plantilla de directiva para adaptarla a necesidades organizativas específicas.

1. Todavía deberías estar en la página **Directivas** en **Cumplimiento de comunicaciones** en el Portal de Microsoft Purview.
1. Selecciona **Crear directiva** > **Detectar imágenes inapropiadas**.
1. En la página flotante **Detectar comunicaciones para imágenes inapropiadas** de la derecha, selecciona **Personalizar directiva** en la parte inferior de la página flotante.
1. Selecciona **Personalizar directiva** en la parte inferior de la página flotante.
1. En **Nombre y descripción de la directiva**, selecciona **Siguiente**.
1. En la página **Elegir usuarios y revisores**, escribe el usuario que revisará las alertas de cumplimiento de comunicaciones en el campo **Revisores** y, después, selecciona **Siguiente**.
1. En la página **Elegir ubicaciones para detectar comunicaciones**, habilita las ubicaciones para:

   - Exchange.
   - Teams.
   - Viva Engage.

1. Selecciona **Siguiente**.
1. En choose **Elegir condiciones y porcentaje de revisión**, revisa las acciones predeterminadas de la plantilla de imágenes inapropiadas y selecciona **Siguiente**.
1. En la página **Revisar y finalizar**, selecciona **Crear directiva** y, después, selecciona **Listo** en la página **La directiva se actualizó**.

Has personalizado correctamente una directiva de cumplimiento de comunicaciones con la plantilla **Detectar imágenes inapropiadas**.

## Tarea 3: Creación de una directiva de cumplimiento de comunicaciones personalizada

En esta tarea, crearás una directiva de cumplimiento de comunicación desde cero para cumplir los requisitos de cumplimiento únicos.

1. Todavía deberías estar en la página **Directivas** en **Cumplimiento de comunicaciones** en el Portal de Microsoft Purview.
1. Selecciona **Crear directiva** > **Directiva personalizada**.
1. En la página **Nombre y descripción de la directiva** escribe:

   - **Nombre**: `Global Communication Compliance Policy`
   - **Descripción**: `Monitors emails and Teams messages for policy violations.`

1. Selecciona **Siguiente**.
1. En la página **Elegir usuarios y revisores**:

   - En **Elegir usuarios y grupos**, selecciona **Todos los usuarios**.
   - Deja en blanco el campo para **Usuarios y grupos excluidos**.
   - En el campo **Revisores**, escribe los revisores que supervisarán las alertas de cumplimiento.

1. Selecciona **Siguiente**.
1. En **Elegir ubicaciones para detectar comunicaciones**, habilita solamente:

   - Exchange
   - Teams

   Asegúrate de que no se seleccionan todas las demás ubicaciones.

1. Selecciona **Siguiente**.
1. En la página **Elegir condiciones y porcentaje de revisión**, deja los valores predeterminados seleccionados para **Dirección de comunicación**.
1. En **Condiciones**, selecciona **+ Agregar condición** > **Contenido coincide con clasificador entrenable**.
1. En **Contenido coincide con clasificadores entrenables**, selecciona **Agregar** > **Clasificadores entrenables**.
1. En la página flotante **Clasificadores entrenables** de la derecha, selecciona clasificadores para **Colusión normativa**, **Manipulación de existencias**, **Divulgación no autorizada** y **Sabotaje corporativo**.
1. Selecciona **Agregar** en la parte inferior de la página flotante **Clasificadores entrenables** de la derecha.
1. De nuevo en la página **Elegir condiciones y porcentaje de revisión**, ajusta el control deslizante **Porcentaje de revisión** al **25 %**.
1. Selecciona **Siguiente** en la parte inferior de la página **Elegir condiciones y porcentaje de revisión**.
1. En la página **Revisar y finalizar**, selecciona **Crear directiva** y, después, selecciona **Listo** en la página **La directiva se ha creado** .

Has creado correctamente una directiva de cumplimiento de comunicaciones personalizada denominada _Directiva global de cumplimiento de comunicaciones_.
