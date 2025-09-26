---
lab:
  task: Case investigation with eDiscovery
  exercise: Exercise 3 - Case investigation with eDiscovery
---

## Inquilinos de WWL: términos de uso

Si se te proporciona un inquilino porque estás realizando un curso dirigido por un instructor, ten en cuenta que ese inquilino está disponible únicamente como apoyo para los laboratorios prácticos del curso.

Los inquilinos no deben compartirse ni usarse para otros fines que no sean los de los laboratorios prácticos. El inquilino usado en este curso es un inquilino de prueba y no se puede usar ni tener acceso a él después de que la clase haya terminado y no es apto para la extensión.

Los inquilinos no se deben convertir a suscripciones de pago. Los inquilinos obtenidos como parte de este curso siguen siendo propiedad de Microsoft Corporation y nos reservamos el derecho de acceso y recuperación en cualquier momento.

# Ejercicio 3: Tareas de aptitud

Contoso sospecha que los datos confidenciales de pago, incluidos los números de tarjeta de crédito y de cuenta, se han controlado o filtrado incorrectamente. Como investigador, su trabajo consiste en usar eDiscovery de Microsoft Purview para crear un caso, buscar en orígenes de datos, identificar contenido confidencial y aplicar acciones de redacción antes de generar los resultados para el cumplimiento o la revisión legal.

La tarea consistirá en crear y administrar casos de eDiscovery que cumplan los criterios de investigación:

- **Cree un nuevo caso de eDiscovery**: Configure un caso para administrar la investigación de datos de pago.
- **Ejecutar una búsqueda de eDiscovery**: Busque en orígenes de datos para identificar los archivos que pueden contener información de la tarjeta de pago o de la cuenta.
- **Agregue elementos a un conjunto de revisión**: Confirme los resultados de búsqueda en un conjunto de revisión para un análisis más profundo.
- **Etiquete los elementos para revisar**: Aplique etiquetas de relevancia y reacción para organizar documentos para el caso.
- **Aplicar difuminaciones**: Use herramientas de anotación para enmascarar detalles confidenciales, como números de tarjeta y cuenta.
- **Exportar resultados**: Exporte los elementos censurados y etiquetados, junto con un informe de elementos, para producción.

   > **Nota**: en este laboratorio se da por supuesto el acceso a un inquilino de M365 E5 con datos para explorar para realizar la investigación. Todavía puedes realizar este ejercicio sin datos, pero las recopilaciones y los conjuntos de revisión no producirán ningún resultado.

## Tarea 1: Concesión de permisos para eDiscovery

Para exportar archivos, necesitarás permisos específicos debido al acceso directo que esta opción concede a los archivos de usuario.

1. En Microsoft Edge, ve al Portal de Microsoft Purview, `https://purview.microsoft.com`, e inicia sesión.

1. Selecciona **Configuración** en el panel de navegación de la izquierda.

1. En el panel de navegación izquierdo, expande **Roles y ámbitos** y, después, selecciona **Grupos de roles**.

1. En la página **Grupos de roles para soluciones de Microsoft Purview**, selecciona **Administrador de eDiscovery**.

1. En la página flotante **Administrador de eDiscovery** de la derecha, selecciona **Editar**.

1. En la página **Administrar Administrador de eDiscovery**, selecciona **Elegir usuarios**.

1. En la página flotante **Elegir usuarios** de la derecha, selecciona el usuario que usarás para realizar esta investigación de eDiscovery en los pasos siguientes y, después, selecciona **Seleccionar**.

    >**Nota**: asegúrate de seleccionar el usuario que revisará los datos y exportará los resultados de la búsqueda.

1. De nuevo en la página **Administrar administrador de eDiscovery**, selecciona **Siguiente**.

1. En la página **Administrar Administrador de eDiscovery**, selecciona **Siguiente**.

1. En la página **Revisar el grupo de roles y finalizar**, selecciona **Guardar** para agregar el usuario al grupo de roles de administrador de eDiscovery.

1. Una vez que hayas agregado correctamente los usuarios, selecciona **Listo** en la página **El grupo de roles se actualizó correctamente**.

Has concedido correctamente el permiso de administrador de eDiscovery.

## Tarea 2: Crear un caso de eDiscovery

En esta tarea, creará un nuevo caso de eDiscovery para administrar la investigación de datos de pago.

1. En Microsoft Purview, selecciona **Soluciones** > **eDiscovery**.

1. En la página **Casos**, seleccione **Crear caso**.

1. En la ventana del cuadro de diálogo **Nuevo caso**, escriba:

   - **Nombre del caso**: `Payment Data Leak Investigation`
   - **Descripción del caso**: `Investigation into potential exposure of payment card and account data at Contoso.`

1. Seleccione **Crear**.

   Una vez creado el caso, se le llevará directamente al nuevo caso.

Ha creado correctamente un nuevo caso de eDiscovery denominado _Investigación de filtraciones de datos de pago_.

## Tarea 3: Creación de una búsqueda de eDiscovery

En esta tarea, creará una búsqueda para buscar correos electrónicos y documentos que hacen referencia a datos confidenciales de pago.

1. Seleccione **Crear una búsqueda**.

1. En la ventana del cuadro de diálogo **Nueva búsqueda**, escriba:

   - **Nombre de búsqueda**: `Payment Data Exposure Search`
   - **Descripción de la búsqueda**: `Find emails and documents that reference credit cards, debit cards, or account numbers.`

1. Seleccione **Crear**.

1. En la página **Búsqueda de exposición de datos de pago**, seleccione **Agregar orígenes**.

1. En la página **Buscar origen**, **filtre** los orígenes para **Solo grupos**.

1. Seleccione **Agregar orígenes para todo el inquilino** y deje las casillas seleccionadas para **Todas las personas y grupos** y **Todas las carpetas públicas**.

1. Seleccione **Guardar**.

1. De nuevo en la página **Búsqueda de exposición de datos de pago**, en el **Generador de condiciones**, agregue condiciones:

   - En el primer cuadro, establezca **Palabras clave igual** y, a continuación, escriba `credit card`.
   - En el segundo cuadro, escriba `debit card`.
   - En el tercer cuadro, escriba `account number`.

   > **Nota**: Las condiciones se tratan como OR, por lo que la búsqueda devuelve elementos que incluyen tarjeta de crédito, tarjeta de débito o número de cuenta.

1. Seleccione **Ejecutar consulta**.

1. En la página **Elegir resultados** de búsqueda, seleccione **Estadísticas** y, después, seleccione **Incluir informe de palabras clave de consulta**.

1. Seleccione **Ejecutar consulta** para iniciar la búsqueda.

   > **Nota**: Este proceso puede tardar unos 5 minutos en generar resultados.

1. Cuando finalice la búsqueda, revise los resultados en la pestaña **Estadísticas**. Examine los recuentos de elementos, el volumen de datos y los aciertos de palabras clave.

1. Cambie a la pestaña **Ejemplo**. Seleccione **Generar resultados de ejemplo**.

1. En la página **Generar vista de ejemplo**, deje los valores predeterminados seleccionados y, a continuación, seleccione **Ejecutar consulta**.

   > **Nota**: Este proceso puede tardar unos 5 minutos en generar resultados.

1. Una vez completada la consulta, revise los resultados.

Ejecutó correctamente la búsqueda y revisó los resultados mediante las vistas Estadísticas y Ejemplo.

## Tarea 4: Agregar la búsqueda a un conjunto de revisión

En esta tarea, confirma los resultados de búsqueda en un conjunto de revisión para que se puedan analizar más.

1. En la página **Búsqueda de exposición de datos de pago**, seleccione **Agregar al conjunto de revisión**.

1. En el control flotante **Agregar al conjunto de revisión**, seleccione **Agregar al nuevo conjunto de revisión**.

   - Escriba un nombre: `Payment Data Review Set`.

1. En **Seleccionar elementos que se van a incluir**, mantenga los **elementos indexados que coincidan con la consulta de búsqueda seleccionada**.

1. En **Seleccionar elementos de listas y datos adjuntos**, seleccione **Enumerar datos adjuntos** para que los archivos adjuntos se incluyan en el conjunto de revisión.

1. Deje todas las demás opciones en sus valores predeterminados y, a continuación, seleccione **Agregar al conjunto de revisión**.

   > **Nota**: Este proceso puede tardar unos 5 minutos en generar resultados.

Ha creado correctamente el **conjunto de revisión de datos de pago** y ha agregado los resultados de búsqueda a él.

## Tarea 5: Revisar y etiquetar elementos

En esta tarea, filtrará los elementos establecidos y aplicará etiquetas para organizarlos para la investigación.

1. En la página **Conjunto de revisión de datos de pago**, seleccione **Consulta** y, a continuación, configure:

   - Primera lista desplegable: **Palabras clave**
   - Operador: **Es igual a cualquiera de**
   - Escriba palabras clave:

     - `Visa`
     - `Master Card`
   - Seleccione **+ Agregar condiciones**.
   - Agregar condición:

     - Campo: **Clase File**
     - Operador: **Es igual a cualquiera de**
     - Valor: `Document`
   - Seleccione **Ejecutar consulta**.

1. Seleccione **Guardar** para guardar esta consulta de búsqueda. En el campo Nombre de filtro, escriba `Payment data docs`.

1. En la barra de comandos, seleccione **Etiquetar archivos**.

1. En el control flotante **Etiquetar archivos**, seleccione **Crear o editar etiquetas**.

1. En la página **Administrar etiquetas**, configure:

   - **Nombre de grupo de etiqueta**: `Relevance`

     - **Nombre de etiqueta**: `Relevant`
     - Seleccione **Agregar etiqueta** y, a continuación, agregue `Not relevant`
   - Seleccione **Agregar grupo de etiquetas**.
   - **Nombre de grupo de etiqueta**: `Review status`
     - **Nombre de etiqueta**: `Needs redaction`

1. Seleccione **Guardar** y luego **Cerrar**.

1. En el control flotante **Etiquetar archivos**, etiquete el primer elemento como **Relevante** y el segundo elemento como **No relevante**.

1. En el conjunto de revisión, busque **Contoso Purchasing Permissions - Q1.docx** de **Irvin S** con fecha del **2 de agosto de 2019**.

1. Seleccione el elemento y etiquete que **necesita censura**.

1. Seleccione **Cerrar** para cerrar el control flotante **Etiquetar archivos**.

Ha etiquetado correctamente los documentos pertinentes, no relevantes y necesarios para la censura.

## Tarea 6: Aplicar censura

En esta tarea, se censura información confidencial de un documento del conjunto de revisión.

1. En el **conjunto de revisión de datos de pago**, seleccione el elemento **Contoso Purchasing Permissions - Q1.docx** de **Irvin S** con fecha del **2 de agosto de 2019** para abrir el visor de documentos.

1. En la barra de herramientas del visor, seleccione **Anotar**.

1. En las herramientas de anotación, seleccione la lista desplegable de **Dibujo** y, a continuación, seleccione **Censura del área**.

    >![Captura de pantalla que muestra dónde seleccionar Censura de área.](./Media/area-redaction.png)

1. Con el cursor, dibuje un cuadro alrededor de la información confidencial del archivo, como:

   - Número de tarjeta Visa
   - Número de tarjeta MasterCard
   - Número de cuenta bancaria

1. Repita lo necesario hasta que se cubran todos los datos confidenciales.

1. Cierre el visor de documentos.

1. De nuevo en la página **Conjunto de revisión de datos de pago**, con el archivo **Contoso Purchasing Permissions - Q1.docx** seleccionado, seleccione **Acciones** > **Confirmar censuras en PDF**.

   > **Nota**: Confirmar las censuras guarda un PDF censurado en el conjunto de revisión mientras mantiene el archivo original sin cambios.

Ha aplicado correctamente las censuras y las ha confirmado en una copia de PDF censurada.

## Tarea 7: Exportar resultados

En esta tarea, exportará los elementos censurados y etiquetados del conjunto de revisión para producción.

1. En el **conjunto de revisión de datos de pago**, active las casillas situadas junto a los elementos que desea exportar.

   > Asegúrese de incluir el documento **Contoso Purchasing Permissions - Q1.docx** que censuró.

1. En la barra de comandos, seleccione **Acciones** > **Exportar**.

1. En el control flotante **Exportar**, configure:

   - **Nombre de exportación**: `PaymentData_Export_2025`
   - **Descripción**: `Export of review set items with redacted versions for Payment Data Leak Investigation.`

1. En **Seleccionar elementos que se van a incluir en la exportación**:

   - Elija **Solo documentos seleccionados**.
   - Deje **Expandir los documentos seleccionados para incluir > Elementos familiares asociados** activados (esto garantiza que se incluyan los datos adjuntos).

1. En **Tipo de exportación**, seleccione **Exportar elementos con informe de elementos**.

   - Active la casilla **Exportar censura** para incluir los archivos PDF censurados y la casilla **Exportar etiquetas** para incluir información de etiquetas.

1. En **Formato de exportación**, seleccione **Crear archivos .msg para los mensajes** y deje los demás valores predeterminados seleccionados.

1. Seleccione **Exportar**.

1. Seleccione el **Administrador de procesos** para ver el estado de la exportación.

1. Seleccione **Actualizar** en el administrador de procesos hasta que el estado de exportación sea **Completado**.

1. Cuando el estado sea **Completado**, seleccione la fila de la exportación.

1. En el control flotante **Exportar**, seleccione todos los archivos en **Exportar paquetes** y, a continuación, **Descargar**.

1. Seleccione una ubicación para descargar las exportaciones y vaya a la ubicación de las exportaciones descargadas.

1. Explore los elementos del archivo ZIP.

Ha creado un caso, ha buscado datos confidenciales, ha agregado elementos a un conjunto de revisión, ha aplicado etiquetas y censuras y exportó los resultados censurados. Estos son los pasos clave para realizar una investigación con Microsoft Purview eDiscovery.