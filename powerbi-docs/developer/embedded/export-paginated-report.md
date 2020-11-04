---
title: Exportación de la API de informes paginados de Power BI
description: Obtenga información sobre cómo exportar un informe paginado de Power BI insertado
author: KesemSharabi
ms.author: kesharab
ms.topic: how-to
ms.service: powerbi
ms.subservice: powerbi-developer
ms.date: 04/05/2020
ms.openlocfilehash: d0d9472ef767a67b3b75be4c9eb5d6922d9cdf81
ms.sourcegitcommit: a5fa368abad54feb44a267fe26c383a731c7ec0d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93045149"
---
# <a name="export-paginated-report-to-file-preview"></a>Exportación de un informe paginado a un archivo (versión preliminar)

La API `exportToFile` permite exportar un informe paginado de Power BI mediante una llamada REST. Se admiten los siguientes formatos de archivo:
* **.pptx** (PowerPoint)
* **.pdf**
* **.xlsx** (Excel)
* **.dox** (Word)
* **.csv**
* **.xml**
* **.mhtml**
* **Imagen**
    * Al exportar a una imagen, establezca el formato de la imagen mediante la configuración de formato `OutputFormat`
    * Los valores de OutputFormat admitidos son: .bmp, .emf, .gif, .jpeg, .png o .tiff (el predeterminado)

## <a name="usage-examples"></a>Ejemplos de uso

Puede usar la característica de exportación de varias maneras. Estos son algunos ejemplos:

* **Botón Enviar para imprimir** : en la aplicación, cree un botón que, al hacer clic en él, desencadene un trabajo de exportación. El trabajo puede exportar el informe visto como archivo .pdf o .pptx, y cuando la operación se complete, el usuario puede recibir el archivo como una descarga. Con los parámetros de informe y la configuración de formato, puede exportar el informe en un estado específico, incluidos los datos filtrados, los tamaños de página personalizados y otros valores de formato específicos. Como la API es asincrónica, el archivo puede tardar un tiempo en estar disponible.

* **Datos adjuntos de correo electrónico** : envíe un correo electrónico automatizado a intervalos establecidos, con un informe .pdf adjunto. Este escenario puede ser útil si desea automatizar el envío de un informe semanal a los ejecutivos.

## <a name="using-the-api"></a>Uso de la API

La API es asincrónica. Cuando se llama a la API [exportToFile](/rest/api/power-bi/reports/exporttofile), se desencadena un trabajo de exportación. Después de activar un trabajo de exportación, use el [sondeo](/rest/api/power-bi/reports/getexporttofilestatus) para realizar un seguimiento del trabajo, hasta que se complete.

Cuando se completa la exportación, la llamada API de sondeo devuelve una [dirección URL de Power BI](/rest/api/power-bi/reports/getfileofexporttofile) para obtener el archivo. La dirección URL estará disponible durante veinticuatro horas.

## <a name="supported-features"></a>Características admitidas

### <a name="format-settings"></a>Configuración de formato

Especifique una variedad de valores de formato para cada formato de archivo. Las propiedades y los valores admitidos son equivalentes a los [parámetros de información del dispositivo](../../paginated-reports/report-builder-url-parameters.md#report-commands-rdl) para los parámetros de dirección URL del informe paginado.

A continuación se muestran dos ejemplos, uno para exportar las cuatro primeras páginas de un informe con el tamaño de página del informe a un archivo .pptx, y otro para exportar la tercera página de un informe a un archivo .jpeg.

**Exportación de las cuatro primeras páginas a un archivo .pptx**

```json
{
      "format": "PPTX",
      "paginatedReportConfiguration":{
            "formatSettings":{
                  "UseReportPageSize": "true",
                  "StartPage": "1",
                  "EndPage": "4"
            }
      }
}
```

**Exportar de la tercera página a un archivo .jpeg**

```json
{
      "format": "IMAGE",
      "paginatedReportConfiguration":{
            "formatSettings":{
                  "OutputFormat": "JPEG",
                  "StartPage": "3",
                  "EndPage": "3"
            }
      }
}
```

### <a name="report-parameters"></a>Parámetros de informe

Puede usar la API `exportToFile` para exportar mediante programación un informe con un conjunto de parámetros de informe. Esto se realiza mediante funciones de [parámetro de informe](../../paginated-reports/paginated-reports-parameters.md).

Este es un ejemplo para establecer los valores de los parámetros de informe.

```json
{
      "format": "PDF",
      "paginatedReportConfiguration":{
            "parameterValues":[
                  {"name": "State", "value": "WA"},
                  {"name": "City", "value": "Seattle"},
                  {"name": "City", "value": "Bellevue"},
                  {"name": "City", "value": "Redmond"}
            ]
      }
}
```

### <a name="authentication"></a>Authentication

Se puede autenticar mediante un usuario (o usuario maestro), o bien una [entidad de servicio](embed-service-principal.md).

### <a name="row-level-security-rls"></a>Seguridad de nivel de fila (RLS)

Al usar un conjunto de datos de Power BI en el que se ha definido la Seguridad de nivel de fila (RLS) como origen de datos, puede exportar un informe que muestre los datos que solo son visibles para usuarios concretos. Por ejemplo, si exporta un informe de ventas que está definido con roles regionales, puede filtrar dicho informe mediante programación para que solo se muestre una determinada región.

Para exportar mediante RLS, debe tener permiso de lectura para el conjunto de datos de Power BI que el informe use como origen de datos.

Este es un ejemplo para proporcionar un nombre de usuario efectivo para RLS.

```json
{
      "format": "PDF",
      "paginatedReportConfiguration":{
            "identities": [
                  {"username": "john@contoso.com"}
            ]
      }
}
```

## <a name="code-examples"></a>Ejemplos de código

El SDK de API de Power BI que se usa en los ejemplos de código se puede descargar [aquí](https://www.nuget.org/packages/Microsoft.PowerBI.Api).

Cuando crea un trabajo de exportación, hay tres pasos que se deben seguir:

1. Envío de una solicitud de exportación.
2. Sondeo.
3. Obtención del archivo.

En esta sección se proporcionan ejemplos para cada paso.

### <a name="step-1---sending-an-export-request"></a>Paso 1: Envío de una solicitud de exportación

El primer paso es enviar una solicitud de exportación. En este ejemplo, se envía una solicitud de exportación para un intervalo de páginas concreto, un tamaño y valores de parámetro de informe.

```csharp
private async Task<string> PostExportRequest(
    Guid reportId,
    Guid groupId)
{
    // For documentation purposes the export configuration is created in this method
    // Ordinarily, it would be created outside and passed in
    var paginatedReportExportConfiguration = new PaginatedReportExportConfiguration()
    {
        FormatSettings = new Dictionary<string, string>()
        {
            {"PageHeight", "14in"},
            {"PageWidth", "8.5in" },
            {"StartPage", "1"},
            {"EndPage", "4"},
        },
        ParameterValues = new List<ParameterValue>()
        {
            { new ParameterValue() {Name = "State", Value = "WA"} },
            { new ParameterValue() {Name = "City", Value = "Redmond"} },
        },
    };

    var exportRequest = new ExportReportRequest
    {
        Format = FileFormat.PDF,
        PaginatedReportExportConfiguration = paginatedReportExportConfiguration,
    };

    var export = await Client.Reports.ExportToFileInGroupAsync(groupId, reportId, exportRequest);

    // Save the export ID, you'll need it for polling and getting the exported file
    return export.Id;
}
```

### <a name="step-2---polling"></a>Paso 2: Sondeo

Después de enviar una solicitud de exportación, use el sondeo para identificar cuándo está listo el archivo de exportación que está esperando.

```csharp
private async Task<Export> PollExportRequest(
    Guid reportId,
    Guid groupId,
    string exportId /* Get from the ExportToAsync response */,
    int timeOutInMinutes,
    CancellationToken token)
{
    Export exportStatus = null;
    DateTime startTime = DateTime.UtcNow;
    const int secToMillisec = 1000;
    do
    {
        if (DateTime.UtcNow.Subtract(startTime).TotalMinutes > timeOutInMinutes || token.IsCancellationRequested)
        {
            // Error handling for timeout and cancellations
            return null;
        }

        var httpMessage = 
            await Client.Reports.GetExportToFileStatusInGroupWithHttpMessagesAsync(groupId, reportId, exportId);
            
        exportStatus = httpMessage.Body;
        if (exportStatus.Status == ExportState.Running || exportStatus.Status == ExportState.NotStarted)
        {
            // The recommended waiting time between polling requests can be found in the RetryAfter header
            // Note that this header is only populated when the status is either Running or NotStarted
            var retryAfter = httpMessage.Response.Headers.RetryAfter;
            var retryAfterInSec = retryAfter.Delta.Value.Seconds;

            await Task.Delay(retryAfterInSec * secToMillisec);
        }
    }
    // While not in a terminal state, keep polling
    while (exportStatus.Status != ExportState.Succeeded && exportStatus.Status != ExportState.Failed);

    return exportStatus;
}
```

### <a name="step-3---getting-the-file"></a>Paso 3: Obtención del archivo

Una vez que el sondeo devuelve una dirección URL, use este ejemplo para obtener el archivo recibido.

```csharp
private async Task<ExportedFile> GetExportedFile(
    Guid reportId,
    Guid groupId,
    Export export /* Get from the GetExportStatusAsync response */)
{
    if (export.Status == ExportState.Succeeded)
    {
        var httpMessage = 
            await Client.Reports.GetFileOfExportToFileInGroupWithHttpMessagesAsync(groupId, reportId, export.Id);

        return new ExportedFile
        {
            FileStream = httpMessage.Body,
            ReportName = export.ReportName,
            FileExtension = export.ResourceFileExtension,
        };
    }

    return null;
}

public class ExportedFile
{
    public Stream FileStream;
    public string ReportName;
    public string FileExtension;
}
```

### <a name="end-to-end-example"></a>Ejemplo de un extremo a otro

Este es un ejemplo de un extremo a extremo para exportar un informe. Este ejemplo incluye las siguientes etapas:
1. [Envío de la solicitud de exportación](#step-1---sending-an-export-request).
2. [Sondeo](#step-2---polling).
3. [Obtención del archivo](#step-3---getting-the-file).

```csharp
private async Task<ExportedFile> ExportPaginatedReport(
    Guid reportId,
    Guid groupId,
    int pollingtimeOutInMinutes,
    CancellationToken token)
{
    try
    {
        var exportId = await PostExportRequest(reportId, groupId);

        var export = await PollExportRequest(reportId, groupId, exportId, pollingtimeOutInMinutes, token);
        if (export == null || export.Status != ExportState.Succeeded)
        {
           // Error, failure in exporting the report
            return null;
        }

        return await GetExportedFile(reportId, groupId, export);
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
>[Exportar informe a archivo](export-to.md)

> [!div class="nextstepaction"]
>[Insertar para los clientes](embed-sample-for-customers.md)

> [!div class="nextstepaction"]
>[Insertar para la organización](embed-sample-for-your-organization.md)