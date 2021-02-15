---
title: Exportación de API de informes de análisis insertados de Power BI
description: Obtenga información sobre cómo exportar un informe insertado de Power BI.
author: KesemSharabi
ms.author: kesharab
ms.topic: how-to
ms.service: powerbi
ms.subservice: powerbi-developer
ms.date: 02/09/2021
ms.openlocfilehash: 68d4802ebb150827982a348bc67f6f46f60812be
ms.sourcegitcommit: de3b45cad5ae21c77692ce4490e21de01d21e6f3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/10/2021
ms.locfileid: "100013576"
---
# <a name="export-power-bi-report-to-file-preview"></a>Exportación de un informe de Power BI a un archivo (versión preliminar)

La API `exportToFile` permite exportar un informe de Power BI mediante una llamada REST. Se admiten los siguientes formatos de archivo:
* **.pptx** (PowerPoint)
* **.pdf**
* **.png**
    * Al exportar a un archivo .png, un informe de varias páginas se comprime en un archivo ZIP.
    * Cada archivo del archivo ZIP representa una página del informe
    * Los nombres de página son los mismos que los valores devueltos de las API [Obtener páginas](/rest/api/power-bi/reports/getpages) u [Obtener páginas en grupo](/rest/api/power-bi/reports/getpagesingroup)

## <a name="usage-examples"></a>Ejemplos de uso

Puede usar la característica de exportación de varias maneras. Estos son algunos ejemplos:

* **Botón Enviar para imprimir**: en la aplicación, cree un botón que, al hacer clic en él, desencadene un trabajo de exportación. El trabajo puede exportar el informe visto como archivo .pdf o .pptx, y cuando la operación se complete, el usuario puede recibir el archivo como una descarga. Mediante marcadores, puede exportar el informe en un estado específico, incluidos filtros configurados, segmentaciones y configuraciones adicionales. Como la API es asincrónica, el archivo puede tardar un tiempo en estar disponible.

* **Datos adjuntos de correo electrónico**: envíe un correo electrónico automatizado a intervalos establecidos, con un informe .pdf adjunto. Este escenario puede ser útil si desea automatizar el envío de un informe semanal a los ejecutivos. Para más información, consulte [Exportación y envío por correo electrónico de un informe de Power BI con Power Automate](../../collaborate-share/service-automate-power-bi-report-export.md)

## <a name="using-the-api"></a>Uso de la API

Antes de usar la API, compruebe que las siguientes [configuraciones de inquilinos del administrador](../../admin/service-admin-portal.md#tenant-settings) estén habilitadas:
* **Exportación de informes como presentaciones de PowerPoint o documentos PDF**: habilitada de forma predeterminada.
* **Exportación de informes como archivos de imagen**: se requiere solo para *.png* y está deshabilitada de forma predeterminada.

La API es asincrónica. Cuando se llama a la API [exportToFile](/rest/api/power-bi/reports/exporttofile), se desencadena un trabajo de exportación. Después de activar un trabajo de exportación, use el [sondeo](/rest/api/power-bi/reports/getexporttofilestatus) para realizar un seguimiento del trabajo, hasta que se complete.

Durante el sondeo, la API devuelve un número que representa la cantidad de trabajo completado. El progreso de cada trabajo de exportación se calcula en función del número total de exportaciones que tenga ese trabajo. Un trabajo de exportación incluye la exportación de un solo objeto visual, o una página con o sin marcadores. Todas las exportaciones tienen el mismo peso. Si, por ejemplo, el trabajo de exportación incluye la exportación de un informe con 10 páginas, y el sondeo devuelve 70, significa que la API ha procesado 7 de las 10 páginas en el trabajo de exportación.

Cuando se completa la exportación, la llamada API de sondeo devuelve una [dirección URL de Power BI](/rest/api/power-bi/reports/getfileofexporttofile) para obtener el archivo. La dirección URL estará disponible durante veinticuatro horas.

## <a name="supported-features"></a>Características admitidas

En esta sección se describe el funcionamiento de las siguientes características admitidas:

* [Selección de páginas para imprimir](#selecting-which-pages-to-print)
* [Exportación de una página o un solo objeto visual](#exporting-a-page-or-a-single-visual)
* [Marcadores](#bookmarks)
* [Filtros](#filters)
* [Autenticación](#authentication)
* [Seguridad de nivel de fila (RLS)](#row-level-security-rls)
* [Protección de datos](#data-protection)
* [Localización](#localization)

### <a name="selecting-which-pages-to-print"></a>Selección de páginas para imprimir

Especifique las páginas que desea imprimir conforme al valor devuelto de [Obtener páginas](/rest/api/power-bi/reports/getpages) u [Obtener páginas en grupo](/rest/api/power-bi/reports/getpagesingroup). También puede especificar el orden de las páginas que está exportando.

### <a name="exporting-a-page-or-a-single-visual"></a>Exportación de una página o un solo objeto visual

Puede especificar una página o un solo objeto visual para que se exporte. Las páginas se pueden exportar con o sin marcadores.

Dependiendo del tipo de exportación, deberá pasar atributos diferentes al objeto [ExportReportPage](/rest/api/power-bi/reports/exporttofile#exportreportpage). En la tabla siguiente se especifican los atributos necesarios para cada trabajo de exportación.  

>[!NOTE]
>Exportar un solo objeto visual tiene el mismo peso que exportar una página (con o sin marcadores). Esto significa que, en cuanto a los cálculos del sistema, ambas operaciones tienen el mismo valor.

|Atributo   |Página     |Un solo objeto visual  |Comentarios|
|------------|---------|---------|---|
|`bookmark`  |Opcional |![No se aplica.](../../media/no.png)|Úselo para exportar una página con un estado específico.|
|`pageName`  |![Se aplica a.](../../media/yes.png)|![Se aplica a.](../../media/yes.png)|Use la API REST [GetPages](/rest/api/power-bi/reports/getpage) o la API de cliente `getPages`. Para obtener más información, vea [Obtención de páginas y objetos visuales](/javascript/api/overview/powerbi/get-visuals).   |
|`visualName`|![No se aplica.](../../media/no.png)|![Se aplica a.](../../media/yes.png)|Hay dos maneras de obtener el nombre del objeto visual:<li>Usar la API de cliente `getVisuals`. Para obtener más información, vea [Obtención de páginas y objetos visuales](/javascript/api/overview/powerbi/get-visuals).</li><li>Escuchar y registrar el evento *visualClicked*, que se desencadena cuando se selecciona un objeto visual. Para obtener más información, consulte [Procedimiento para controlar eventos](/javascript/api/overview/powerbi/handle-events).</li>. |

### <a name="bookmarks"></a>Marcadores

Los [marcadores](../../consumer/end-user-bookmarks.md) pueden usarse para guardar un informe en una configuración específica, incluidos los filtros aplicados y el estado de los objetos visuales del informe. Puede usar la API [exportToFile](/rest/api/power-bi/reports/exporttofile) para exportar mediante programación el marcador de un informe de dos maneras:

* **Exportar un marcador existente**

    Para exportar un [marcador de informe](../../consumer/end-user-bookmarks.md#report-bookmarks) existente, use la propiedad `name`, un identificador único (con distinción entre mayúsculas y minúsculas) que puede obtener mediante la [API de JavaScript de los marcadores](https://github.com/Microsoft/PowerBI-JavaScript/wiki/Bookmarks).

* **Exportar el estado del informe**

    Para exportar el estado actual del informe, use la propiedad `state`. Por ejemplo, puede usar el método `bookmarksManager.capture` del marcador para capturar los cambios que un usuario específico realizó en un informe y luego exportarlo en su estado actual mediante `capturedBookmark.state`.

>[!NOTE]
>Los [marcadores personales](../../consumer/end-user-bookmarks.md#personal-bookmarks) y los [filtros persistentes](https://powerbi.microsoft.com/blog/announcing-persistent-filters-in-the-service/) no se admiten.

### <a name="filters"></a>Filtros

Con `reportLevelFilters` en [PowerBIReportExportConfiguration](/rest/api/power-bi/reports/exporttofile#powerbireportexportconfiguration), puede exportar un informe con un condición filtrada.

Para exportar un informe filtrado, inserte los [parámetros de cadena de consulta de URL](../../collaborate-share/service-url-filters.md) que quiere usar como filtro en [ExportFilter](/rest/api/power-bi/reports/exporttofile#exportfilter). Cuando escriba la cadena, debe quitar la parte `?filter=` del parámetro de consulta de URL.

En la tabla siguiente se incluyen algunos ejemplos de sintaxis de cadenas que puede pasar a `ExportFilter`.

|Filter    |Sintaxis    |Ejemplo    |
|---|----|----|----|
|Un valor en un campo    |Table/Field eq 'value'    |Store/Territory eq 'NC'    |
|Varios valores en un campo    |Table/Field in ('value1', 'value2')     |Store/Territory in ('NC', 'TN')    |
|Un valor distinto en un campo y un valor distinto diferente en otro campo    |Table/Field1 eq 'value1' y Table/Field2 eq 'value2'    |Store/Territory eq 'NC' y Store/Chain eq 'Fashions Direct'    |

>[!NOTE]
>`ReportLevelFilters` solo puede contener un [ExportFilter](/rest/api/power-bi/reports/exporttofile#exportfilter) único.

### <a name="authentication"></a>Authentication

Se puede autenticar mediante un usuario (o usuario maestro), o bien una [entidad de servicio](embed-service-principal.md).

### <a name="row-level-security-rls"></a>Seguridad de nivel de fila (RLS)

Con la [seguridad de nivel de fila (RLS)](embedded-row-level-security.md), puede exportar un informe que muestra datos que solo son visibles para ciertos usuarios. Por ejemplo, si exporta un informe de ventas que está definido con roles regionales, puede filtrar dicho informe mediante programación para que solo se muestre una determinada región.

Para realizar la exportación mediante la seguridad de nivel de fila, debe tener los siguientes permisos:
* Permisos para escribir y volver a compartir para el conjunto de datos al que está conectado el informe
* Si el informe reside en un área de trabajo v1, debe ser el administrador de dicho espacio de trabajo.
* Si el informe reside en un área de trabajo v2, debe ser un miembro o administrador del área de trabajo

### <a name="data-protection"></a>Protección de datos

Los formatos .pdf y .pptx admiten [etiquetas de confidencialidad](../../admin/service-security-sensitivity-label-overview.md). Si exporta un informe con una etiqueta de confidencialidad a un archivo .pdf o .pptx, el archivo exportado mostrará el informe con su etiqueta de confidencialidad.

Un informe con una etiqueta de confidencialidad no se puede exportar a un archivo .pdf o .pptx mediante una [entidad de servicio](embed-service-principal.md).

### <a name="localization"></a>Localización

Al usar la API `exportToFile`, puede pasar su localización deseada. La configuración de localización afecta a la forma en que se muestra el informe, por ejemplo, cambiando el formato conforme a la localización seleccionada.

## <a name="concurrent-requests"></a>Solicitudes simultáneas

`exportToFile` admite solicitudes simultáneas de trabajos de exportación. En la tabla siguiente se muestra la cantidad de trabajos que puede ejecutar al mismo tiempo, dependiendo de la SKU en la que reside el informe. Las solicitudes concurrentes se refieren a páginas de informes. Por ejemplo, veinte páginas en una solicitud de exportación en una SKU A6 se procesarán simultáneamente. Esto llevará aproximadamente el mismo tiempo que enviar veinte solicitudes de exportación con una página cada una.

Un trabajo que supere su número de solicitudes simultáneas no se termina. Por ejemplo, si exporta tres páginas en una SKU A1, se ejecutará el primer trabajo y los dos últimos esperarán a los dos próximos ciclos de ejecución.

>[!NOTE]
>La exportación de un informe de Power BI a un archivo mediante la API `exporToFile` no es compatible con la licencia [Premium por usuario (PPU)](../../admin/service-premium-per-user-faq.md). 

|SKU de Azure  |SKU de Office  |Número máximo de páginas de informe simultáneas  |
|-----------|------------|-----------|
|A1         |EM1         |1          |
|A2         |EM2         |2          |
|A3         |EM3         |3          |
|A4         |P1          |6          |
|A5         |P2          |12         |
|A6         |P3          |24         |

## <a name="limitations"></a>Limitaciones

* El informe que va a exportar debe estar en una capacidad Premium o Embedded.
* El conjunto de datos del informe que va a exportar debe estar en una capacidad Premium o Embedded.
* En la versión preliminar pública, el número de exportaciones de Power BI por hora está limitado a 50 por capacidad. El término "exportación" se refiere a exportar un solo objeto visual o una página de informe con o sin marcadores (no se incluye la exportación de informes paginados).
* Los informes exportados no pueden tener un tamaño superior a 250 MB.
* Al exportar a .png, no se admiten las etiquetas de confidencialidad.
* El número de exportaciones (objetos visuales individuales o páginas de informe) que se pueden incluir en un informe exportado es de 50 (no se incluye la exportación de informes paginados). Si la solicitud incluye más exportaciones, la API devuelve un error y el trabajo de exportación se cancela.
* Los [marcadores personales](../../consumer/end-user-bookmarks.md#personal-bookmarks) y los [filtros persistentes](https://powerbi.microsoft.com/blog/announcing-persistent-filters-in-the-service/) no se admiten.
* Los objetos visuales de Power BI que se enumeran a continuación no se admiten. Cuando se exporta un informe que contiene estos objetos visuales, las partes del informe que contienen dichos objetos visuales no se representarán y mostrarán un símbolo de error.
    * Objetos visuales de Power BI sin certificar
    * Objetos visuales de R
    * PowerApps
    * Objetos visuales de Python
    * Visio

## <a name="code-examples"></a>Ejemplos de código

Cuando crea un trabajo de exportación, hay tres pasos que se deben seguir:

1. [Envío de una solicitud de exportación](#step-1---sending-an-export-request).
2. [Sondeo](#step-2---polling).
3. [Obtención del archivo](#step-3---getting-the-file).
4. [Uso de la secuencia de archivo](#step-4---using-the-file-stream).

En esta sección se proporcionan ejemplos para cada paso.

### <a name="step-1---sending-an-export-request"></a>Paso 1: Envío de una solicitud de exportación

El primer paso es enviar una solicitud de exportación. En este ejemplo, se envía una solicitud de exportación para una página específica.

```csharp
private async Task<string> PostExportRequest(
    Guid reportId,
    Guid groupId,
    FileFormat format,
    IList<string> pageNames = null, /* Get the page names from the GetPages REST API */
    string urlFilter = null)
{
    var powerBIReportExportConfiguration = new PowerBIReportExportConfiguration
    {
        Settings = new ExportReportSettings
        {
            Locale = "en-us",
        },
        // Note that page names differ from the page display names
        // To get the page names use the GetPages REST API
        Pages = pageNames?.Select(pn => new ExportReportPage(Name = pn)).ToList(),
        // ReportLevelFilters collection needs to be instantiated explicitly
        ReportLevelFilters = !string.IsNullOrEmpty(urlFilter) ? new List<ExportFilter>() { new ExportFilter(urlFilter) } : null,

    };

    var exportRequest = new ExportReportRequest
    {
        Format = format,
        PowerBIReportConfiguration = powerBIReportExportConfiguration,
    };

    // The 'Client' object is an instance of the Power BI .NET SDK
    var export = await Client.Reports.ExportToFileInGroupAsync(groupId, reportId, exportRequest);

    // Save the export ID, you'll need it for polling and getting the exported file
    return export.Id;
}
```

### <a name="step-2---polling"></a>Paso 2: Sondeo

Después de enviar una solicitud de exportación, use el sondeo para identificar cuándo está listo el archivo de exportación que está esperando.

```csharp
private async Task<HttpOperationResponse<Export>> PollExportRequest(
    Guid reportId,
    Guid groupId,
    string exportId /* Get from the PostExportRequest response */,
    int timeOutInMinutes,
    CancellationToken token)
{
    HttpOperationResponse<Export> httpMessage = null;
    Export exportStatus = null;
    DateTime startTime = DateTime.UtcNow;
    const int c_secToMillisec = 1000;
    do
    {
        if (DateTime.UtcNow.Subtract(startTime).TotalMinutes > timeOutInMinutes || token.IsCancellationRequested)
        {
            // Error handling for timeout and cancellations 
            return null;
        }

        // The 'Client' object is an instance of the Power BI .NET SDK
        httpMessage = await Client.Reports.GetExportToFileStatusInGroupWithHttpMessagesAsync(groupId, reportId, exportId);
        exportStatus = httpMessage.Body;

        // You can track the export progress using the PercentComplete that's part of the response
        SomeTextBox.Text = string.Format("{0} (Percent Complete : {1}%)", exportStatus.Status.ToString(), exportStatus.PercentComplete);
        if (exportStatus.Status == ExportState.Running || exportStatus.Status == ExportState.NotStarted)
        {
            // The recommended waiting time between polling requests can be found in the RetryAfter header
            // Note that this header is not always populated
            var retryAfter = httpMessage.Response.Headers.RetryAfter;
            var retryAfterInSec = retryAfter.Delta.Value.Seconds;
            await Task.Delay(retryAfterInSec * c_secToMillisec);
        }
    }
    // While not in a terminal state, keep polling
    while (exportStatus.Status != ExportState.Succeeded && exportStatus.Status != ExportState.Failed);

    return httpMessage;
}
```

### <a name="step-3---getting-the-file"></a>Paso 3: Obtención del archivo

Una vez que el sondeo devuelve una dirección URL, use este ejemplo para obtener el archivo recibido.

```csharp
private async Task<ExportedFile> GetExportedFile(
    Guid reportId,
    Guid groupId,
    Export export /* Get from the PollExportRequest response */)
{
    if (export.Status == ExportState.Succeeded)
    {
        // The 'Client' object is an instance of the Power BI .NET SDK
        var fileStream = await Client.Reports.GetFileOfExportToFileAsync(groupId, reportId, export.Id);
        return new ExportedFile
        {
            FileStream = fileStream,
            FileSuffix = export.ResourceFileExtension,
        };
    }
    return null;
}

public class ExportedFile
{
    public Stream FileStream;
    public string FileSuffix;
}
```

### <a name="step-4---using-the-file-stream"></a>Paso 4: uso de la secuencia de archivo

Cuando tenga la secuencia de archivo, puede administrarla de la manera que mejor se adapte a sus necesidades. Por ejemplo, puede enviarla por correo electrónico o usarla para descargar los informes exportados.

### <a name="end-to-end-example"></a>Ejemplo de un extremo a otro

Este es un ejemplo de un extremo a extremo para exportar un informe. Este ejemplo incluye las siguientes etapas:
1. [Envío de la solicitud de exportación](#step-1---sending-an-export-request).
2. [Sondeo](#step-2---polling).
3. [Obtención del archivo](#step-3---getting-the-file).

```csharp
private async Task<ExportedFile> ExportPowerBIReport(
    Guid reportId,
    Guid groupId,
    FileFormat format,
    int pollingtimeOutInMinutes,
    CancellationToken token,
    IList<string> pageNames = null,  /* Get the page names from the GetPages REST API */
    string urlFilter = null)
{
    const int c_maxNumberOfRetries = 3; /* Can be set to any desired number */
    const int c_secToMillisec = 1000;
    try
    {
        Export export = null;
        int retryAttempt = 1;
        do
        {
            var exportId = await PostExportRequest(reportId, groupId, format, pageNames, urlFilter);
            var httpMessage = await PollExportRequest(reportId, groupId, exportId, pollingtimeOutInMinutes, token);
            export = httpMessage.Body;
            if (export == null)
            {
                // Error, failure in exporting the report
                return null;
            }
            if (export.Status == ExportState.Failed)
            {
                // Some failure cases indicate that the system is currently busy. The entire export operation can be retried after a certain delay
                // In such cases the recommended waiting time before retrying the entire export operation can be found in the RetryAfter header
                var retryAfter = httpMessage.Response.Headers.RetryAfter;
                if(retryAfter == null)
                {
                    // Failed state with no RetryAfter header indicates that the export failed permanently
                    return null;
                }

                var retryAfterInSec = retryAfter.Delta.Value.Seconds;
                await Task.Delay(retryAfterInSec * c_secToMillisec);
            }
        }
        while (export.Status != ExportState.Succeeded && retryAttempt++ < c_maxNumberOfRetries);

        if (export.Status != ExportState.Succeeded)
        {
            // Error, failure in exporting the report
            return null;
        }

        var exportedFile = await GetExportedFile(reportId, groupId, export);

        // Now you have the exported file stream ready to be used according to your specific needs
        // For example, saving the file can be done as follows:
        /*
            var pathOnDisk = @"C:\temp\" + export.ReportName + exportedFile.FileSuffix;

            using (var fileStream = File.Create(pathOnDisk))
            {
                exportedFile.FileStream.CopyTo(fileStream);
            }
        */

        return exportedFile;
    }
    catch
    {
        // Error handling
        throw;
    }
}
```

## <a name="next-steps"></a>Pasos siguientes

Revise cómo insertar contenido para sus clientes y su organización:

> [!div class="nextstepaction"]
>[Exportación de un informe paginado a un archivo](export-paginated-report.md)

> [!div class="nextstepaction"]
>[Insertar para los clientes](embed-sample-for-customers.md)

> [!div class="nextstepaction"]
>[Insertar para la organización](embed-sample-for-your-organization.md)

> [!div class="nextstepaction"]
>[Exportación y envío por correo electrónico de un informe de Power BI con Power Automate](../../collaborate-share/service-automate-power-bi-report-export.md)
