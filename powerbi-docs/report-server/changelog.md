---
title: Registro de cambios de Power BI Report Server
description: Este registro de cambios es para el servidor de informes de Power BI y enumera los elementos nuevos junto con las correcciones de errores de cada versión publicada.
ms.author: jaimeta
author: jtarquino
ms.reviewer: maggies
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 10/29/2020
ms.openlocfilehash: 3173108abe6082c199cbf6ff1229ca57fde31064
ms.sourcegitcommit: a5fa368abad54feb44a267fe26c383a731c7ec0d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93044774"
---
# <a name="change-log-for-power-bi-report-server"></a>Registro de cambios de Power BI Report Server

Este registro de cambios es para el servidor de informes de Power BI y enumera los elementos nuevos junto con las correcciones de errores de cada versión publicada.

Para obtener más información sobre las nuevas características, vea [Novedades de Power BI Report Server](whats-new.md). 

## <a name="october-2020"></a>Octubre de 2020
- **Servidor de informes de Power BI**
    - *Versión: 1.9.7604.41261 (compilación 15.0.1104.239), fecha de publicación: 27 de octubre de 2020*
         - Características
            - Se ha habilitado la compatibilidad con los metadatos de los conjuntos de datos mejorados en Power BI Report Server.
            - Se ha habilitado la capacidad de actualizar conexiones para informes de Power BI para DirectQuery y actualización; vea [Cambio de cadenas de conexión de origen de datos](./connect-data-source-apis.md) para obtener más información.
        - Actualizaciones de seguridad
        - Correcciones de errores
            - Se ha corregido una incidencia que impide que los usuarios cambien las programaciones de actualizaciones de informes de Power BI.
            - Se han corregido los mensajes de error confusos que los usuarios reciben al administrar informes cuando las credenciales han expirado.
            - Se ha corregido una incidencia con la exportación de informes con puntos en el nombre.
            - Se han corregido incidencias del lector de pantalla en una región de datos Tablix.
            - Se ha corregido una incidencia que causaba que los archivos de registro estuvieran en blanco en algunas circunstancias.
            - Se ha corregido una incidencia con el cuadro de diálogo "Conectarse a Power BI", que no se cierra.
            - Se ha actualizado el representador MHTML para usar el DOCTYPE HTML más reciente.

- **Power BI Desktop (optimizado para Power BI Report Server)**
   - *Versión: 2.86.961.0 (octubre de 2020), fecha de publicación: 27 de octubre de 2020* (nueva compilación y versión)
        - Contiene los cambios necesarios para la conexión con Power BI Report Server (octubre de 2020).        
   
## <a name="may-2020"></a>Mayo de 2020
- **Servidor de informes de Power BI**
    - *Versión: 1.8.7485.35104 (compilación 15.0.1103.234), fecha de publicación: 30 de junio de 2020*
        - Correcciones de errores
            - Se corrigió un error en escenarios de escalabilidad horizontal en que los informes no estaban reflejando las ediciones de manera inmediata en el servidor después de la carga.
    - *Versión: 1.8.7468.41510 (compilación 15.0.1103.232), fecha de publicación: 15 de junio de 2020*
        - Correcciones de errores
            - Se corrigió un error en el que los informes no estaban reflejando las ediciones de manera inmediata en el servidor después de la carga.
            - Se corrigió un error en el que no se completaba la actualización cuando se usaba la coincidencia aproximada para combinar consultas.
    - *Versión: 1.8.7450.37410 (compilación 15.0.1103.227), fecha de publicación: 27 de mayo de 2020*
         - Características
            -  Se ha agregado compatibilidad para el tamaño de grupo de conexiones de catálogo personalizable (vea [Configuración de MaxCatalogConnectionPoolSizePerProcess](/sql/reporting-services/report-server/rsreportserver-config-configuration-file#bkmk_service) para obtener más detalles).
            -  Se ha mejorado el comportamiento al ver un informe durante una operación de actualización.
        - Actualizaciones de seguridad
        - Correcciones de errores
            - Se han corregido dos incidencias relacionadas con las comillas simples en los nombres de carpeta e informe.
            - Se ha corregido una incidencia relacionada con el desplazamiento horizontal con determinados exploradores y la característica Ver registros.
            - Se ha corregido una incidencia que hacía que la actualización programada con el informe abierto a veces provocara errores de esquema en el modelo subyacente.
            - Se ha corregido una incidencia que hacía que el texto alternativo para la exportación a PDF no se codificara correctamente para los caracteres de varios bytes.
            - Se ha corregido una incidencia que hacía que las aplicaciones personalizadas que ejecutaban LoadReport recibieran incorrectamente un error TrustedHeader.
            - Se ha corregido una incidencia que hacía que la carga pesada de la actualización programada pudiera provocar errores en las actualizaciones.
            - Se ha corregido una incidencia que hacía que los informes se guardaran en una ubicación incorrecta si el nombre del informe coincidía con el de la carpeta.
            - Se han corregido incidencias de tabulación en el mapa del documento.
            - Se ha corregido una incidencia con las suscripciones controladas por datos que generan errores al usar consultas DAX.
            - Se ha corregido una incidencia en el acceso de URL que hacía que FindString no buscara coincidencias.
            - Se ha corregido una incidencia que interrumpía los orígenes de datos insertados al mover informes.
            - Se ha corregido una incidencia que hacía que se produjera un error en la actualización programada para determinados orígenes de datos.
            - Se ha agregado validación a la programación de informes para reducir la posibilidad de solicitudes no válidas.


- **Power BI Desktop (optimizado para Power BI Report Server)**
   - *Versión: 2.81.5831.1181 (mayo de 2020), fecha de publicación: 9 de junio de 2020*
        - Corrección de errores
           -  Corrección para objetos visuales de Marketplace
   - *Versión: 2.81.5831.941 (mayo de 2020), fecha de publicación: 27 de mayo de 2020* (nueva compilación y nueva versión)
        - Contiene los cambios necesarios para la conexión con Power BI Report Server (mayo de 2020)        
   
## <a name="january-2020"></a>Enero de 2020
- **Servidor de informes de Power BI**
    - *Versión: 1.6.7364.4075 (compilación 15.0.1102.777), fecha de publicación: 2 de marzo de 2020*
         - Correcciones de errores
           -  Corrección para informes de Power BI que no se pueden cargar para determinados orígenes de datos
           -  Corrección para la ubicación de descarga del vínculo de Power BI Report Server Desktop desde el portal
           -  Corrección para DynamicImageDPI para la representación en Excel
           -  Corrección para las conexiones de Oracle que usan una referencia cultural de subprocesos incorrecta en ciertos escenarios de varios usuarios (vea la [documentación de UseInstalledUICulture](./connect-data-sources.md) para obtener más detalles).
           -  Corrección para el valor predeterminado de CustomHeaders que produce errores en la inserción de informes
           -  Corrección para los nombres de parámetros de SQL que se general incorrectamente en determinados casos
    - *Versión: 1.6.7327.3007 (compilación 15.0.1102.759), fecha de publicación: 23 de enero de 2020*
         - Características
            -  Exportación de informes de Power BI a Excel.
           -  Compatibilidad de los conjuntos de datos de Power BI Premium con los informes paginados.
           -  Compatibilidad de AltText (texto alternativo) con los elementos de informe paginados.
           -  Compatibilidad con encabezados personalizados.
           -  Compatibilidad con Instancia administrada de Azure SQL como catálogo.
           -  Cifrado de base de datos transparente para el catálogo.
        - Actualizaciones de seguridad
        - Correcciones de errores
            - Correcciones de accesibilidad para lectores de pantalla, representación de informes y navegación mediante teclado.
            - Corrección para guardar títulos de informe de varios bytes.
            - Corrección para el registro detallado que afecta a la confiabilidad del servidor de informes.
          - Corrección para garantizar datos activos en informes de Power BI en dispositivos móviles.
          - Corrección para aplicar resaltado cruzado a los objetos visuales de la exportación filtrada de informes de Power BI.
          - Corrección para escribir un pie de página al realizarla exportación a Word con la expresión de visibilidad de informes paginados. 
     
- **Power BI Desktop (optimizado para Power BI Report Server)**
    - *Versión: 2.76.5678.1521 (enero de 2020), fecha de publicación: 23 de enero de 2020* (nueva compilación y nueva versión)
        - Contiene los cambios necesarios para la conexión con Power BI Report Server (enero de 2020).        


## <a name="september-2019"></a>Septiembre de 2019
- **Servidor de informes de Power BI**
    - *Versión: 1.6.7236.4246 (compilación 15.0.1102.646), fecha de publicación: 25 de octubre de 2019*
        - Actualizaciones de seguridad
        - Correcciones de errores
            - Corrección para .NET Framework 4.7 no instalada.
            - Corrección para los informes paginados para Teradata con parámetros de varios valores con el error 110083.
            - La corrección para el valor de URLRoot no funciona si hay varios enlaces de URL de servicio web y uno de ellos es https://+80/reportserver.
          - Corrección para los parámetros con varios valores en los informes paginados que se muestran fuera del área de informe.
          
    - *Versión: 1.6.7221.30698 (compilación 15.0.1102.620), fecha de publicación: 9 de octubre de 2019*
        - Correcciones de errores
            - Corrección del objeto visual personalizado Filtro de texto.
            - Se ha corregido el rendimiento de las segmentaciones desplegables.
            - Corrección de la eliminación de información de identificación personal de telemetría.
          - Corrección para las direcciones URL que no distinguen mayúsculas de minúsculas.
          
    - *Versión 1.6.7206.38019 (Compilación 15.0.1102.597), publicada el: 26 de septiembre de 2019*
        - Actualizaciones de seguridad
        - Correcciones de errores
           - Informes paginados
             - Corrección de incidencias de accesibilidad detectadas al usar Internet Explorer y Microsoft Edge.
             - Corrección de incidencias de SAP HANA al probar la conexión.
             - Corrección de incidencias encontradas al proporcionar una lista de direcciones de correo electrónico.
             - Corrección de los informes de Power BI que usan un origen de datos de DirectQuery y la autenticación integrada.
             - Corrección de los informes paginados para que se representen con parámetros de filtro cuando la instantánea está habilitada.
             - Corrección de la ejecución doble de procedimientos almacenados durante la ejecución del informe.
             - Corrección de la cuenta de servicio predeterminada a la que se le conceden permisos de inicio de sesión de SQL Server cuando la cuenta de servicio personalizada está configurada para ejecutar Power BI Report Server.
             - Corrección de la obtención de acceso a los modelos que se actualizan en la zona horaria japonesa.
             - Corrección de los modelos obsoletos cuando se carga una nueva versión del informe durante la actualización.
             - Corrección de los valores de parámetro que contienen el carácter "&".
         - Programación
             - API web actualizada: /PowerBIReports({Id})/DataSources (PATCH) para permitir las actualizaciones de la cadena de conexión.
         
- **Power BI Desktop (optimizado para Power BI Report Server)**
    - *Versión: 2.73.5586.1501 (septiembre de 2019), fecha de publicación: 25 de octubre de 2019*
        - Correcciones de errores
            - Corrección para la telemetría.
            
    - *Versión: 2.73.5586.1241 (septiembre de 2019), fecha de publicación: 9 de octubre de 2019*
        - Correcciones de errores
            - Corrección del objeto visual personalizado Filtro de texto.
            - Corrección del rendimiento de las segmentaciones desplegables.
            - Corrección de la eliminación de información de identificación personal de telemetría.
            
    - *Versión: 2.73.5586.821 (septiembre de 2019), publicada: 26 de septiembre de 2019* (nueva compilación y versión)
        - Contiene los cambios necesarios para la conexión con Power BI Report Server (septiembre de 2019)

    
## <a name="may-2019"></a>Mayo de 2019

- **Servidor de informes de Power BI**          
    - *Versión 1.5.7074.36177 (compilación 15.0.1102.371), fecha de publicación: 21 de mayo de 2019*
        - Correcciones de errores
            - Informes paginados
                - Corrección para habilitar siempre la inserción de fuentes de PDF.
                - Corrección para establecer las cookies enviadas sobre HTTPS como seguras.
                - Corrección de incidencias con los elementos emergentes debido a errores de script.
                - Corrección de incidencias de visualización con la aplicación móvil en teléfonos con Android.
                - Corrección del navegador de tiempo del informe móvil para mostrar los números de semana correctos, independientemente del inicio del año fiscal.
                - Se ha agregado la propiedad configurable "RestrictedResourceMimeTypeForUpload" para que los administradores puedan especificar los tipos mime prohibidos.
         - Características
            - Se ha agregado compatibilidad con los objetos visuales de confianza a PBIRS.

- **Power BI Desktop (optimizado para Power BI Report Server)**
    - *Versión: 2.69.5467.1801 (mayo de 2019), publicada el: 21 de mayo de 2019*
        - Correcciones de errores
            - Corrección para evitar la reentrada de credenciales durante la carga de PBIX a PBIRS.
            - Correcciones en la apertura de documentos con # en el nombre de archivo.
            - Se ha agregado un vínculo más sencillo para la navegación hacia atrás en la ventana de selección de PBIRS.
            - Corrección para el modo de Alto contraste en PBIRS para mostrar el botón Atrás, que muestra mensajes visuales de advertencia.
            - Correcciones de la interfaz de usuario en el panel de selección, escalado del lienzo.

    - *Versión: 2.69.5467.5201 (mayo de 2019), publicada el: 30 de julio de 2019*
        - Correcciones de errores
            - Corrección del registro de telemetría incorrecta

## <a name="january-2019"></a>Enero de 2019

- **Servidor de informes de Power BI**          
    - *Version 1.4.7024.16477 (Compilación 15.0.1102.299), publicada el: 28 de marzo de 2019*
        - Correcciones de errores
            - Informes de Power BI
                - Corrección del problema con las credenciales básicas al usar una consulta directa en SAP Hana y SAP BW
                - Error en la corrección de actualización de datos de fuente OData con "No se pudo cargar el archivo o ensamblado Microsoft.OData.Core.NetFX35.V7"

- **Servidor de informes de Power BI**            
    - *Versión 1.4.6969.7395 (compilación 15.0.1102.235), fecha de publicación: 30 de enero de 2019*
        - Correcciones de errores
            - Informes de Power BI
                - Corrección del problema con las credenciales básicas al usar una consulta directa
                - Corrección de las relaciones bidireccionales con los filtros de seguridad de nivel de fila aplicados
                - Corrección de datos obsoletos después de una actualización de modelo en un entorno de escalabilidad horizontal
                - Corrección de la barra de desplazamiento doble de tabla o matriz en Firefox 63 o posterior
                - Corrección del tamaño del icono de +/- de Internet Explorer
            - Informes paginados
                - Corrección del problema de actualización del uso de un origen de datos compartido de un informe

    - *Versión 1.4.6960.38798 (compilación 15.0.1102.222), fecha de publicación: 22 de enero de 2019*
        - Características
            - Informes de Power BI 
                - Compatibilidad con Seguridad de nivel de fila
                - Expandir y contraer encabezados de fila de matriz
                - Copiar y pegar entre archivos .pbix
                - Guías de alineación inteligente
                - Compatibilidad con el conector SAP BW 2.0
            - Administradores
                - Capacidad para definir qué extensiones de recursos se pueden cargar en el servidor de informes
                - Capacidad para restringir los esquemas de hipervínculos admitidos
            - Programación
                - Nueva API web: /PowerBIReports({Id})/DataModelRoles (GET)
                - Nueva API web: /PowerBIReports({Id})/DataModelRoleAssignments (GET y PUT)
                - Consulte el artículo sobre la [API de REST de Power BI Report Server](https://app.swaggerhub.com/apis/microsoft-rs/PBIRS/2.0) para obtener más detalles.
        - Correcciones de errores
            - Vulnerabilidad por inyección de HTML
            - Símbolo del Euro no visible al exportar a PDF
            - Guardar una contraseña con varios orígenes de datos en informes de Power BI invalida las contraseñas no modificadas.
            - Los objetos visuales muestran problemas en la aplicación de Power BI Mobile tras un tiempo de inactividad.

- **Power BI Desktop (optimizado para Power BI Report Server)**
    - *Versión: 2.65.5313.1562 (enero de 2019), fecha de publicación: 30 de enero de 2019*
        - Los iconos de acceso directo y los anclados siguen estando después de desinstalar Power BI Report Server
        - Corrección para anclar Power BI Report Server en el menú de inicio proporcionando texto en negro sobre un icono negro

    - *Versión: 2.65.5313.1421 (enero de 2019), fecha de publicación: 22 de enero de 2019* (nueva compilación y nueva versión)
        - Contiene los cambios necesarios para la conexión con Power BI Report Server (enero de 2019). 
    - *Versión: 2.65.5313.5141 (enero de 2019), fecha de publicación: 31 de julio de 2019* (nueva compilación y nueva versión)
        - Correcciones de errores
            - Corrección del registro de telemetría incorrecta

## <a name="august-2018"></a>Agosto de 2018

- **Servidor de informes de Power BI**
    - *Versión 1.3.6816.37243 (compilación 15.0.2.557), fecha de publicación: 30 de agosto de 2018*
        - Correcciones de errores
            - Se ha corregido una incidencia que causaba que el servidor se actualizara a partir de versiones anteriores de PBI Report Server, pero no de un redireccionamiento de enlace, y los clientes veían este mensaje:      
            *`
            Failed to load expression host assembly. Details: Could not load file or assembly 'Microsoft.ReportingServices.ProcessingObjectModel, Version=2018.7.0.0, Culture=neutral, PublicKeyToken=89845dcd8080cc91' or one of its dependencies. The located assembly's manifest definition does not match the assembly reference. (Exception from HRESULT: 0x80131040) (rsErrorLoadingExprHostAssembly)
             `*
             
            - El error de transferencia de la etiqueta de datos ya está corregido.
            
    - *Versión 1.3.6801.38816 (compilación 15.0.2.540), fecha de publicación: 15 de agosto de 2018*
        - Características
            - Compatibilidad de Direct Query de SSO de SAP HANA con Kerberos ya disponible para informes de Power BI
            - API de objeto visual personalizada incluida con la versión: versión 1.13.0
            - Los objetos visuales de Power BI se revierten a una versión anterior compatible con la versión actual de la API de servidor (si está disponible)

- **Power BI Desktop (optimizado para Power BI Report Server)**
    - *Versión: 2.61.5192.641 (agosto de 2018), fecha de publicación: 15 de agosto de 2018*
        - Contiene los cambios necesarios para la conexión con Power BI Report Server (agosto de 2018)         
    - *Versión: 2.61.5192.7701 (agosto de 2018), fecha de publicación: 8 de agosto de 2019* (nueva compilación y versión)
        - Correcciones de errores
            - Corrección del registro de telemetría incorrecta
            
## <a name="march-2018"></a>Marzo de 2018

- **Servidor de informes de Power BI**
    - *Versión 1.2.6690.34729 (compilación 15.0.2.402), fecha de publicación: 27 de abril de 2018*
        - Correcciones de errores
            - Habilitar la migración de catálogos de SQL Server Reporting Services 2017
            - Para informes de Power BI (PBIX)
                - Los informes se pueden actualizar cuando un servidor está configurado para usar la autenticación personalizada
                - La modificación de las propiedades de un informe no restablece las credenciales del origen de datos
            - Para informes paginados (RDL)
                - El uso de `Lookup()` o de funciones derivadas, como `LookupSet()` y `MultiLookup()` en expresiones RDL ya no da como resultado `#Error`
                - Los informes vinculados respetan el tamaño de página del informe de destino al imprimir
                - Se pueden crear suscripciones para informes vinculados que usan parámetros en cascada
                - Los valores predeterminados de parámetros de varios valores pueden modificarse cuando se usa IE11
                - Se pueden editar las opciones de entrega de las suscripciones controladas por datos
                - Las suscripciones se pueden ver y editar mientras la suscripción se encuentra en ejecución
                - La definición de las credenciales del origen de datos no elimina las cadenas de conexión basadas en expresiones
            - Para los KPI
                - Las líneas de tendencia se actualizan cuando se actualizan los datos
            - Mejoras generales de la estabilidad

    - *Versión 1.2.6660.39920 (compilación 15.0.2.389), fecha de publicación: 28 de marzo de 2018*
        - Correcciones de errores
            - Para los informes de Power BI (PBIX), corrección para Exportar datos que no funcionan desde los objetos visuales de Power BI
            - Para los informes de Power BI (PBIX), corrección para los filtros de URL que no funcionan
            - Para los informes paginados (RDL), corrección para las imágenes que no se muestran correctamente en IE11 después de actualizar a la versión de marzo de Power BI Report Server

    - *Versión 1.2.6648.38132 (compilación 15.0.2.378), fecha de publicación: 19 de marzo de 2018*
        - Actualizaciones de seguridad
        - Mejoras de accesibilidad
        - Correcciones de errores
            - Para informes paginados (RDL), corrección de la visibilidad de los parámetros en un informe vinculado que se revierte después de editar sus propiedades
            - Corrección del portal web con autenticación de formularios personalizada que omite la cookie de expiración deslizante
            - Corrección para las exportaciones a Word que crean un alto de filas desigual si el contenido de la fila está vacío
            - Para los informes paginados (RDL), se ha incluido una corrección de la cadena de conexión basada en expresiones que se elimina cuando se cambia la credencial para el origen de datos.
            - Corrección de la capacidad de usar KPI con valores de texto
            - Para informes paginados (RDL), corrección de la capacidad de asignar un nuevo conjunto de datos a un informe paginado existente (RDL)
            - Otras correcciones de estabilidad y facilidad de uso

- **Power BI Desktop (optimizado para Power BI Report Server)**
    - Versión: 2.56.5023.1043 (marzo de 2018), fecha de publicación: 19 de marzo de 2018
        - Contiene los cambios necesarios para la conexión con Power BI Report Server (marzo de 2018)

## <a name="october-2017"></a>Octubre de 2017

- **Servidor de informes de Power BI**
    - *Versión 1.1.6582.41691 (compilación 14.0.600.442), fecha de publicación: 10 de enero de 2018*
        - Actualizaciones de seguridad
        - Correcciones de errores
            - Corrección del error que provocaba que GetParameters devolviese 400.
            - Corrección de la configuración de conjuntos de datos compartidos en informes paginados existentes (RDL).
            - Corrección de la excepción ExecutionNotFoundException al exportar informes con valores de parámetros distintos a PDF.

    - *Versión 1.1.6551.5155 (compilación 14.0.600.438), fecha de publicación: 11 de diciembre de 2017*
        - Correcciones de errores
            - Error al guardar los datos después de la actualización para determinados informes de Power BI Desktop.

    - *Versión 1.1.6530.30789 (compilación 14.0.600.437), fecha de publicación: 17 de noviembre de 2017*
        - Correcciones de errores
            - Corrección de los escenarios de autenticación básica 
            - Corrección del error por el que los días laborables no se podían seleccionar en la página de Suscripciones, Planes de actualización de caché e Instantáneas del historial en el Portal
            - En el caso de los informes paginados (RDL), corrección del error por el que, al tener expresiones en el cuadro de texto con la propiedad CanGrow establecida en false, los valores no muestran colores y las fuentes no son correctas
            - Para los informes de Power BI (PBIX), corrección del error por el que, al agregar leyendas al gráfico de líneas, se representa un objeto visual vacío

    - *Versión 1.1.6514.9163 (compilación 14.0.600.434), fecha de publicación: 1 de noviembre de 2017*
        - Correcciones de errores
            - Se han corregido problemas de confiabilidad de carga de los informes .pbix de más de 500 MB.
            - Se ha corregido un problema de carga de datos de los informes .pbix de más de 1 GB.

    - *Versión 1.1.6513.3500 (compilación 14.0.600.433), fecha de publicación: 31 de octubre de 2017*
        - Características
            - Compatibilidad con el modelo de datos insertados
            - Visualización de libros de Excel (con la integración de Office Online Server habilitada)
            - Actualización de datos programada (PBIX)
            - Compatibilidad con Direct Query
            - Compatibilidad con archivos de gran tamaño (hasta 2 GB)
            - API de REST pública
            - Compatibilidad con conjuntos de datos compartidos en Power BI Desktop (a través de oData)
            - Compatibilidad con parámetros de dirección URL para archivos PBIX
            - Mejoras de accesibilidad

- **Power BI Desktop (optimizado para Power BI Report Server)**
    - *Versión: 2.51.4885.3981 (octubre de 2017), fecha de publicación: 10 de abril de 2018*
        - Actualizaciones de seguridad

    - *Versión: 2.51.4885.2501 (octubre de 2017), fecha de publicación: 10 de enero de 2018*
        - Actualizaciones de seguridad

    - *Versión: 2.51.4885.1423 (octubre de 2017), fecha de publicación: 17 de noviembre de 2017*
        - Correcciones de errores
            - Corrección del error por el que Power BI Desktop de 32 bits no se puede ejecutar en sistemas operativos x86
            - Para los informes de Power BI (PBIX), corrección para mostrar las líneas de cuadrícula del eje X
            - Otras correcciones de errores menores

    - *Versión: 2.51.4885.1041 (octubre de 2017), fecha de publicación: 31 de octubre de 2017*
        - Características
            - Contiene los cambios necesarios para la conexión con Power BI Report Server (octubre de 2017)

## <a name="june-2017"></a>Junio de 2017

- **Servidor de informes de Power BI**
    - *Compilación 14.0.600.309, fecha de publicación: 10 de enero de 2018*
        - Actualizaciones de seguridad

    - *Compilación 14.0.600.305, fecha de publicación: 19 de septiembre de 2017*  
        - Correcciones de errores
            - Actualización a la versión más reciente del [control Web de mapas de Bing](/bingmaps/v8-web-control/)

    - *Compilación 14.0.600.301, fecha de publicación: 11 de julio de 2017*
        - Correcciones de errores
            - La etiqueta `{{UserId}}` se resuelve en las credenciales almacenadas en lugar de ser el usuario el que ejecute el informe en los informes de Power BI
            - Algunas imágenes no se pueden representar en los informes del servidor de informes de Power BI
            - No se puede cambiar el nombre de un informe de Power BI en el servidor de informes de Power BI
            - No se pueden cargar objetos visuales de Power BI en la aplicación móvil de Power BI (es necesario volver a instalarla para borrar la caché local)

    - *Compilación 14.0.600.271, fecha de publicación: 12 de junio de 2017*
        - Versión inicial del servidor de informes de Power BI

- **Power BI Desktop (optimizado para Power BI Report Server)**
    - *Versión: 2.47.4766.4901 (junio de 2017), fecha de publicación: 10 de enero de 2018*
        - Actualizaciones de seguridad

## <a name="next-steps"></a>Pasos siguientes

[¿Qué es Power BI Report Server?](get-started.md)
[Información general de administrador](admin-handbook-overview.md)  
[Instalar un servidor de informes de Power BI](install-report-server.md)  
[Descarga del Generador de informes](https://www.microsoft.com/download/details.aspx?id=53613)  
[Descargar SQL Server Data Tools (SSDT)](/sql/ssdt/download-sql-server-data-tools-ssdt)

¿Tiene más preguntas? [Pruebe a preguntar a la comunidad de Power BI](https://community.powerbi.com/)
