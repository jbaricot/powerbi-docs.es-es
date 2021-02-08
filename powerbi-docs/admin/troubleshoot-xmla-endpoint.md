---
title: Solución de problemas de conectividad de los puntos de conexión XMLA en Power BI
description: En este artículo se describe cómo solucionar problemas de conectividad a través del punto de conexión XMLA en Power BI Premium.
author: Minewiskan
ms.author: kfollis
ms.reviewer: kayu
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: troubleshooting
ms.date: 02/02/2021
ms.custom: seodec18, css_fy20Q4
LocalizationGroup: Premium
ms.openlocfilehash: 98bc3da33f38974f3dfcb9e155111e7d16e6c069
ms.sourcegitcommit: f7330dabb9cd8bce90bb2efec3e3273a11578f10
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2021
ms.locfileid: "99494475"
---
# <a name="troubleshoot-xmla-endpoint-connectivity"></a>Solución de problemas de conectividad de los puntos de conexión XMLA

Los puntos de conexión XMLA en Power BI Premium se basan en el protocolo de comunicación de Analysis Services nativo para el acceso a los conjuntos de datos de Power BI. Debido a esto, solucionar los problemas de los puntos de conexión XMLA es muy similar a solucionar los problemas de una conexión de Analysis Services típica. Sin embargo, se aplican algunas diferencias con respecto a las dependencias específicas de Power BI.

## <a name="before-you-begin"></a>Antes de empezar

Antes de solucionar los problemas de un escenario de punto de conexión XMLA, asegúrese de revisar los conceptos básicos que se describen en [Conectividad del conjunto de datos con el punto de conexión de XMLA](service-premium-connect-tools.md). En ese artículo se describen los casos de uso más comunes del punto de conexión XMLA. También pueden resultarle útiles otras guías de solución de problemas de Power BI, como [Solución de problemas de puertas de enlace: Power BI](../connect-data/service-gateway-onprem-tshoot.md) y [Solución de problemas de Analizar en Excel](../collaborate-share/desktop-troubleshooting-analyze-in-excel.md).

## <a name="enabling-the-xmla-endpoint"></a>Habilitación del punto de conexión XMLA

El punto de conexión XMLA se puede habilitar tanto en las capacidades de Power BI Premium como en las de Power BI Embedded. En capacidades más pequeñas, como una capacidad A1 con solo 2,5 GB de memoria, puede encontrar un error en la configuración de la capacidad si intenta establecer el punto de conexión XMLA en **Lectura/Escritura** y, luego, seleccionar **Aplicar**. El error indica que hubo un problema con la configuración de la carga de trabajo y que debe volver a intentarlo más tarde.

Estas son algunas medidas que puede intentar:

- Limite el consumo de memoria de otros servicios de la capacidad, como los Flujos de datos, a 40 % o menos, o bien deshabilite por completo un servicio innecesario.  
- Actualice la capacidad a una SKU mayor. Por ejemplo, actualizar de una capacidad A1 a una capacidad A3 permite solucionar este problema de configuración sin tener que deshabilitar los Flujos de datos.

Tenga en cuenta que también debe habilitar la [Opción de exportación de datos](service-premium-connect-tools.md#security) de nivel de inquilino en el Portal de administración de Power BI. Esta opción también es necesaria para la característica Analizar en Excel.

## <a name="establishing-a-client-connection"></a>Establecimiento de una conexión de cliente

Después de habilitar el punto de conexión XMLA, se recomienda probar la conectividad a un área de trabajo en la capacidad. Para más información, consulte [Conexión a un área de trabajo Premium](service-premium-connect-tools.md#connecting-to-a-premium-workspace). No olvide leer la sección [Requisitos de la conexión](service-premium-connect-tools.md#connection-requirements) para ver sugerencias útiles e información sobre las limitaciones de conectividad XMLA actuales.

### <a name="connecting-with-a-service-principal"></a>Conexión con una entidad de servicio

Si habilitó la opción de inquilino para permitir que las entidades de servicio usen las API de Power BI, tal como se describe en [Habilitación de entidades de servicio](service-premium-service-principal.md#enable-service-principals), puede conectarse a un punto de conexión XMLA mediante una entidad de servicio. Tenga en cuenta que la entidad de servicio requiere el mismo nivel de permisos de acceso en el nivel de área de trabajo o de conjunto de datos que los usuarios normales.

Para usar una entidad de servicio, asegúrese de especificar la información de identidad de la aplicación en la cadena de conexión de la manera siguiente:

- `User ID=<app:appid@tenantid>`
- `Password=<application secret>`

Por ejemplo:

`Data Source=powerbi://api.powerbi.com/v1.0/myorg/Contoso;Initial Catalog=PowerBI_Dataset;User ID=app:91ab91bb-6b32-4f6d-8bbc-97a0f9f8906b@19373176-316e-4dc7-834c-328902628ad4;Password=6drX...;`

Si aparece el siguiente mensaje de error:

"No es posible establecer una conexión con el conjunto de datos debido a que la información de la cuenta no está completa. En el caso de las entidades de servicio, asegúrese de especificar el id. del inquilino junto con el id. de la aplicación con la aplicación de formato:\<appId>@\<tenantId> y vuelva a intentarlo".

Asegúrese de especificar el id. del inquilino junto con el id. de la aplicación con el formato correcto.

También es válido especificar el id. de la aplicación sin el id. del inquilino. Sin embargo, en este caos debe reemplazar el alias `myorg` de la dirección URL del origen de datos por el id. del inquilino real. Power BI puede entonces ubicar la entidad de servicio en el inquilino correcto. Pero, como procedimiento recomendado, use el alias `myorg` y especifique el id. del inquilino en conjunto con el id. de la aplicación en el parámetro Id. de usuario.

### <a name="connecting-with-azure-active-directory-b2b"></a>Conexión con Azure Active Directory B2B

Gracias a la compatibilidad con negocio a negocio (B2B) de Azure Active Directory (Azure AD) en Power BI, puede proporcionar a usuarios invitados externos acceso a los conjuntos de datos a través del punto de conexión XMLA. Asegúrese de que la opción [Compartir contenido con usuarios externos](service-admin-portal.md#export-and-sharing-settings) esté habilitada en el Portal de administración de Power BI. Para más información, consulte [Distribuir contenido de Power BI a usuarios externos invitados con Azure AD B2B](service-admin-azure-ad-b2b.md).

## <a name="deploying-a-dataset"></a>Implementación de un conjunto de datos

Puede implementar un proyecto de modelo tabular en Visual Studio (SSDT) en un área de trabajo de Power BI Premium de forma muy parecida a hacerlo en Azure Analysis Services. Sin embargo, cuando la implementación se hace en un área de trabajo de Power BI Premium, hay algunas consideraciones adicionales. Asegúrese de revisar la sección [Implementación de proyectos de modelo desde Visual Studio (SSDT)](service-premium-connect-tools.md#deploy-model-projects-from-visual-studio-ssdt) del artículo Conectividad del conjunto de datos con el punto de conexión XMLA.

### <a name="deploying-a-new-model"></a>Implementación de un modelo nuevo

En la configuración predeterminada, Visual Studio intenta procesar el modelo como parte de la operación de implementación para cargar datos en el conjunto de datos desde los orígenes de datos. Tal como se describe en [Implementación de proyectos de modelo desde Visual Studio (SSDT)](service-premium-connect-tools.md#deploy-model-projects-from-visual-studio-ssdt), esta operación puede presentar un error porque las credenciales de origen de datos no se pueden especificar como parte de la operación de implementación. En su lugar, si las credenciales del origen de datos no están definidas todavía para ninguno de los conjuntos de datos existentes, debe especificar las credenciales del origen de datos en la configuración del conjunto de datos con la interfaz de usuario de Power BI (**Conjuntos de datos** > **Configuración** > **Credenciales del origen de datos** > **Editar credenciales**). Una vez que se definen las credenciales del origen de datos, Power BI puede aplicarlas a este origen de datos de manera automática para cualquier conjunto de datos nuevo, una vez que la implementación de los metadatos se ha realizado correctamente y se ha creado el conjunto de datos.

Si Power BI no puede enlazar el conjunto de datos nuevo a las credenciales del origen de datos, recibirá un error que indica "No se puede procesar la base de datos. Motivo: No se han podido guardar las modificaciones en el servidor", con el código de error "DMTS_DatasourceHasNoCredentialError", tal como se muestra a continuación:

:::image type="content" source="media/troubleshoot-xmla-endpoint/deploy-refresh-error.png" alt-text="Error de implementación de modelo":::

Para evitar que haya errores en el procesamiento, establezca las **Opciones de implementación** > **Opciones de procesamiento** en **No procesar**, tal como se muestra en la imagen siguiente. A continuación, Visual Studio solo implementa metadatos. Después, puede configurar las credenciales del origen de datos y hacer clic en **Actualizar ahora** para el conjunto de datos en la interfaz de usuario de Power BI. Para información sobre cómo solucionar los problemas de procesamiento, consulte la sección [Actualización de un conjunto de datos](#refreshing-a-dataset) más adelante en este artículo.

:::image type="content" source="media/troubleshoot-xmla-endpoint/do-not-process.png" alt-text="Opción No procesar":::

### <a name="new-project-from-an-existing-dataset"></a>Proyecto nuevo a partir de un conjunto de datos existente

No se admite la creación de un proyecto tabular nuevo en Visual Studio mediante la importación los metadatos de un conjunto de datos existente en un área de trabajo de Power BI Premium. Sin embargo, puede conectarse al conjunto de datos mediante SQL Server Management Studio, crear scripts para los metadatos y volver a usarlos en otros proyectos tabulares.

## <a name="migrating-a-dataset-to-power-bi"></a>Migración de un conjunto de datos a Power BI

Se recomienda especificar el nivel de compatibilidad 1500 (o superior) para los modelos tabulares. Este nivel de compatibilidad admite la mayoría de las funcionalidades y los tipos de orígenes de datos. Los niveles de compatibilidad posteriores son compatibles con las versiones anteriores de los niveles.

### <a name="supported-data-providers"></a>Proveedores de datos admitidos

En el nivel de compatibilidad 1500, Power BI admite estos tipos de orígenes de datos:

- Orígenes de datos del proveedor (heredados con una cadena de conexión en los metadatos del modelo).
- Orígenes de datos estructurados (introducidos con el nivel de compatibilidad 1400).
- Declaraciones de M insertadas de orígenes de datos (como Power BI Desktop los declara).

Se recomienda usar orígenes de datos estructurados, los que Visual Studio crea de forma predeterminada al pasar por el flujo de datos de importación. Sin embargo, si planea migrar un modelo existente a Power BI que usa un origen de datos del proveedor, asegúrese de que el origen de datos del proveedor se basa en un proveedor de datos compatible. En concreto, Microsoft OLE DB Driver for SQL Server y cualquier controlador ODBC de terceros. Para OLE DB Driver for SQL Server, debe cambiar la definición del origen de datos al proveedor de datos de .NET Framework para SQL Server. En el caso de los controladores ODBC de terceros que puedan no estar disponibles en el servicio Power BI, debe cambiar a una definición de origen de datos estructurados.

También se recomienda reemplazar la versión obsoleta de Microsoft OLE DB Driver for SQL Server (SQLNCLI11) en las definiciones del origen de datos de SQL Server por el proveedor de datos de .NET Framework para SQL Server.

En la tabla siguiente se proporciona un ejemplo de una cadena de conexión de proveedor de datos de .NET Framework para SQL Server que reemplaza una cadena de conexión correspondiente para OLE DB Driver for SQL Server.

|Controlador OLE DB para SQL Server  |Proveedor de datos .NET Framework para SQL Server   |
|---------|---------|
|`Provider=SQLNCLI11;Data Source=sqldb.database.windows.net;Initial Catalog=AdventureWorksDW;Trusted_Connection=yes;`    |   `Data Source=sqldb.database.windows.net;Initial Catalog=AdventureWorksDW2016;Integrated Security=SSPI;Encrypt=true;TrustServerCertificate=false`       |

### <a name="cross-referencing-partition-sources"></a>Referencias cruzadas de orígenes de particiones

Del mismo modo que hay varios tipos de orígenes de datos, también hay varios tipos de orígenes de particiones que un modelo tabular puede incluir para importar datos a una tabla. En concreto, una partición puede usar un origen de partición de consulta o un origen de partición de M. A su vez, estos tipos de orígenes de particiones pueden hacer referencia a orígenes de datos de proveedor o a orígenes de datos estructurados. Si bien los modelos tabulares de Azure Analysis Services admiten la referencia cruzada de estos diversos tipos de particiones y orígenes de datos, Power BI exige una relación más estricta. Los orígenes de la partición de consulta deben hacer referencia a orígenes de datos del proveedor y los orígenes de particiones de M deben hacer referencia a orígenes de datos estructurados. No se admiten otras combinaciones en Power BI. Si desea migrar un conjunto de datos de referencia cruzada, en la tabla siguiente se describen las configuraciones admitidas:  

|Origen de datos   |Origen de la partición   |Comentarios   |Se admite en Power BI Premium con el punto de conexión XMLA   |
|---------|---------|---------|---------|
|Origen de datos del proveedor      |   Origen de partición de consulta      |   El motor de AS usa la pila de conectividad basada en cartuchos para acceder al origen de datos.       |     Sí     |
|Origen de datos del proveedor      |   Origen de partición de M       |   El motor de AS traduce el origen de datos del proveedor en un origen de datos estructurados genérico y, a continuación, usa el motor de mashup para importar los datos.       |    No     |
|Sincronización del origen de datos      |     Origen de partición de consulta     |    El motor de AS encapsula la consulta nativa del origen de la partición en una expresión M y, a continuación, usa el motor de mashup para importar los datos.      |    No     |
|Sincronización del origen de datos      |    Origen de partición de M      |     El motor de AS usa el motor de mashup para importar los datos.     |   Sí      |

## <a name="refreshing-a-dataset"></a>Actualización de un conjunto de datos

Los puntos de conexión XMLA permiten realizar operaciones de actualización en los modelos tabulares, así como en los conjuntos de datos creados en Power BI Desktop. Para admitir lo último, asegúrese de especificar la configuración de formato de almacenamiento mejorado. Esta opción es necesaria si quiere realizar el procesamiento u otras operaciones de lectura/escritura mediante el punto de conexión XMLA. Puede encontrar la configuración en Power BI Desktop en Característica en vista previa (GB). Una vez que realice la configuración, vuelva a publicar la solución PBIX en el área de trabajo de Power BI Premium.  

Power BI devuelve el error siguiente si realiza una actualización a través del punto de conexión XMLA en un modelo sin metadatos mejorados: "La operación solo se admite en el modelo con la propiedad "DefaultPowerBIDataSourceVersion" establecida en "PowerBI_V3" en Power BI Premium".

### <a name="data-sources-and-impersonation"></a>Orígenes de datos y suplantación

La configuración de suplantación que se puede definir para los orígenes de datos del proveedor no es pertinente para Power BI. Power BI usa un mecanismo distinto en función de la configuración del conjunto de datos para administrar las credenciales del origen de datos. Por este motivo, asegúrese de seleccionar **Cuenta de servicio** si está creando un origen de datos del proveedor.

:::image type="content" source="media/troubleshoot-xmla-endpoint/impersonate-services-account.png" alt-text="Suplantación de una cuenta de servicio":::

### <a name="fine-grained-processing"></a>Procesamiento detallado

Al desencadenar una actualización programada o una actualización a petición en Power BI, Power BI habitualmente actualiza todo el conjunto de datos. En muchos casos, resulta más eficaz hacer actualizaciones de manera más selectiva. Puede realizar tareas de procesamiento detallado en SQL Server Management Studio (SSMS) tal como se muestra a continuación, o bien mediante el uso de scripts o herramientas de terceros.

:::image type="content" source="media/troubleshoot-xmla-endpoint/process-tables.png" alt-text="Proceso de tablas en SSMS":::

### <a name="overrides-in-refresh-tmsl-command"></a>Invalidaciones en el comando Refresh de TMSL

Las invalidaciones en el [comando Refresh (TMSL)](/analysis-services/tmsl/refresh-command-tmsl) permiten a los usuarios elegir otra definición de consulta de partición o de origen de datos para la operación de actualización. Actualmente, en Power BI Premium **no se admiten las invalidaciones**. Se devuelve un error que indica que el enlace fuera de línea no se permite en Power BI Premium. Para obtener más información, vea "Compatibilidad con la lectura y escritura de XMLA" en la documentación del producto" .

## <a name="errors-in-ssms---premium-gen-2"></a>Errores en SSMS: Premium Gen2

### <a name="query-execution"></a>Ejecución de consultas

Cuando se conecta a un área de trabajo en una capacidad [Premium Gen2](service-premium-what-is.md#power-bi-premium-generation-2-preview), SQL Server Management Studio puede mostrar el siguiente error:

```
Executing the query ...
Error -1052311437:
```

Esto se debe a que las bibliotecas cliente instaladas con SSMS v18.7.1 no admiten el seguimiento de la sesión. Esto se resuelve en SSMS 18.8 y versiones posteriores. [Descargar la última versión de SSMS](/sql/ssms/download-sql-server-management-studio-ssms).

### <a name="refresh-operations"></a>Operaciones de actualización

Cuando se usa SSMS v18.7.1 o una versión anterior para realizar una operación de actualización de larga duración (> 1 min) de un conjunto de datos en una capacidad Premium Gen2, SSMS puede mostrar un error similar al siguiente aunque la operación de actualización se realice correctamente:

```
Executing the query ...
Error -1052311437:
The remote server returned an error: (400) Bad Request.

Technical Details:
RootActivityId: 3716c0f7-3d01-4595-8061-e6b2bd9f3428
Date (UTC): 11/13/2020 7:57:16 PM
Run complete
```

Esto se debe a un problema conocido en las bibliotecas cliente en el que se realiza un seguimiento incorrecto del estado de la solicitud de actualización. Esto se resuelve en SSMS 18.8 y versiones posteriores. [Descargar la última versión de SSMS](/sql/ssms/download-sql-server-management-studio-ssms).

## <a name="editing-role-memberships-in-ssms"></a>Edición de las pertenencias a roles en SSMS

Si se usa la versión 18.8 de SQL Server Management Studio (SSMS) para editar una pertenencia a roles en un conjunto de datos, SSMS puede mostrar el siguiente error:

```
Failed to save modifications to the server. 
Error returned: ‘Metadata change of current operation cannot be resolved, please check the command or try again later.’ 
```

Esto se debe a un problema conocido de la API REST de App Services. Esto se resolverá en una próxima versión. Mientras tanto, para soslayar este error, en **Propiedades del rol**, haga clic en **Script** y, después, escriba y ejecute el siguiente comando de TMSL:

```json
{ 
  "createOrReplace": { 
    "object": { 
      "database": "AdventureWorks", 
      "role": "Role" 
    }, 
    "role": { 
      "name": "Role", 
      "modelPermission": "read", 
      "members": [ 
        { 
          "memberName": "xxxx", 
          "identityProvider": "AzureAD" 
        }, 
        { 
          "memberName": “xxxx” 
          "identityProvider": "AzureAD" 
        } 
      ] 
    } 
  } 
} 
```

## <a name="publish-error---live-connected-dataset"></a>Error de publicación: Conjunto de datos conectado activo

Al volver a publicar un conjunto de datos conectado activo mediante el conector de Analysis Services, puede aparecer el siguiente error:

:::image type="content" source="media/troubleshoot-xmla-endpoint/couldnt-publish-to-power-bi.png" alt-text="Error &quot;No se pudo publicar en Power BI&quot;":::

Como se indica en el mensaje de error, elimine o cambie el nombre del conjunto de datos existente para resolver este problema. Asegúrese también de volver a publicar cualquier aplicación que dependa del informe. Si así lo cree conveniente, avise también a los usuarios de niveles inferiores para que actualicen los marcadores con la nueva dirección de informe, así podrán acceder al informe más reciente sin problemas.  

## <a name="workspaceserver-alias"></a>Alias del servidor o el área de trabajo

A diferencia de Azure Analysis Services, los [alias](/azure/analysis-services/analysis-services-server-alias) de nombre de servidor **no se admiten** para las áreas de trabajo de Power BI Premium. 

## <a name="dataset-refresh-through-the-xmla-endpoint"></a>Actualización de un conjunto de datos por medio del punto de conexión de XMLA

La fecha y la hora de la última actualización se muestran en una serie de ubicaciones de Power BI, como las columnas actualizadas de los informes y las listas, los detalles del conjunto de datos, la configuración del conjunto de datos y el historial de actualización del conjuntos de datos. Actualmente, la fecha y la hora de actualización que se muestran en Power BI **no** incluyen las operaciones de actualización realizadas por medio del punto de conexión de XMLA mediante TMSL/TOM, SSMS o herramientas de terceros.

## <a name="discover_m_expressions"></a>DISCOVER_M_EXPRESSIONS 

En estos momentos, la vista de administración de datos DMV DISCOVER_M_EXPRESSIONS (DMV) no es compatible con Power BI al usar el punto de conexión de XMLA. Las aplicaciones pueden usar el Modelo de objetos tabulares (TOM) para obtener las expresiones M usadas por el modelo de datos.

## <a name="see-also"></a>Vea también

[Conectividad del conjunto de datos con el punto de conexión de XMLA](service-premium-connect-tools.md)  
[Automatización de tareas de área de trabajo y conjunto de datos de Premium con entidades de servicio](service-premium-service-principal.md)  
[Solución de problemas de Analizar en Excel](../collaborate-share/desktop-troubleshooting-analyze-in-excel.md)  
[Implementación de la solución de modelo tabular](/analysis-services/deployment/tabular-model-solution-deployment?view=power-bi-premium-current&preserve-view=true).
