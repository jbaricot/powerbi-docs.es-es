---
title: Análisis en Excel para Power BI
description: Análisis de conjuntos de datos de Power BI en Microsoft Excel
author: davidiseminger
ms.reviewer: ''
ms.custom: contperfq4
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
ms.date: 05/26/2020
ms.author: davidi
LocalizationGroup: Reports
ms.openlocfilehash: 1605e6108b990c95a995eadd9a6b3d03260001f5
ms.sourcegitcommit: 13c4bec679313f2951f1833033316cb8176da8a1
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/26/2020
ms.locfileid: "88937502"
---
# <a name="analyze-in-excel"></a>Analizar en Excel
Con **Analizar en Excel**, puede traer conjuntos de datos de Power BI a Excel y luego verlos e interactuar con ellos a través de tablas dinámicas, gráficos, segmentaciones y otras características de Excel. Para usar **Analizar en Excel**, primero debe descargar la característica desde Power BI, instalarla y, luego, seleccionar uno o varios conjuntos de datos para usarlos en Excel. 

![Analizar en Excel](media/service-analyze-in-excel/analyze-excel-00a.png)

En este artículo se muestra cómo instalar y usar Analizar en Excel, se describen sus limitaciones y se proporcionan algunos pasos siguientes. Aprenderá lo siguiente:

* [Instalar Analizar en Excel](#install-analyze-in-excel)
* [Conectarse a datos de Power BI](#connect-to-power-bi-data)
* [Usar Excel para analizar los datos](#use-excel-to-analyze-the-data)
* [Guardar y compartir un libro](#saving-and-sharing-your-new-workbook)
* [Requisitos](#requirements)

Empecemos con el proceso de instalación.

## <a name="install-analyze-in-excel"></a>Instalar Analizar en Excel

Debe instalar **Analizar en Excel** desde los vínculos proporcionados en el servicio Power BI. Power BI detecta la versión de Excel que tiene en el equipo y descarga automáticamente la versión adecuada (de 32 bits o 64 bits). El servicio Power BI se ejecuta en un explorador. Puede iniciar sesión en Power BI con el vínculo siguiente:

* [Iniciar sesión en Power BI](https://app.powerbi.com)

Una vez que inicie sesión y el servicio Power BI se ejecute en el explorador, seleccione el elemento **Más opciones** (los puntos suspensivos) que aparecen en la esquina superior derecha y seleccione **Descargar > Actualizaciones de Analizar en Excel**. Este elemento de menú se aplica a las instalaciones nuevas de actualizaciones de Analizar en Excel.

![Descarga de Analizar en Excel en el Inicio de Power BI](media/service-analyze-in-excel/analyze-excel-02.png)

También puede navegar en el servicio Power BI a un conjunto de datos que quiera analizar y seleccionar el elemento **Más opciones** para un conjunto de datos, un informe u otro elemento de Power BI. En el menú que aparece, seleccione la opción **Analizar en Excel**, tal como se muestra en la imagen siguiente.

![Analizar en Excel desde un conjunto de datos](media/service-analyze-in-excel/analyze-excel-01.png)

En cualquier caso, Power BI detecta si tiene instalado Analizar en Excel y, si no es así, se le pedirá que lo descargue. 

![Actualizaciones necesarias](media/service-analyze-in-excel/analyze-excel-03.png)

Cuando selecciona Descargar, Power BI detecta la versión de Excel que tiene instalada y descarga la versión correspondiente del instalador de Analizar en Excel. Verá un estado de descarga en la parte inferior del explorador o en cualquier lugar en el que el explorador muestre el progreso de la descarga. 

![Descarga de actualizaciones](media/service-analyze-in-excel/analyze-excel-04.png)

Una vez finalizada la descarga, ejecute el instalador (.msi) para instalar Analizar en Excel. El nombre del proceso de instalación no es Analizar en Excel, sino que será **Proveedor OLE DB de Microsoft Analysis Services**, tal como se muestra en la imagen siguiente, o un nombre similar.

![Actualizaciones que instalan el proveedor OLE DB de Analysis Services](media/service-analyze-in-excel/analyze-excel-05.png)

Una vez que se complete el proceso, estará listo para seleccionar un informe en el servicio Power BI (u otro elemento de datos de Power BI, como un conjunto de datos) y, luego, analizarlo en Excel.

## <a name="connect-to-power-bi-data"></a>Conectarse a datos de Power BI

En el servicio Power BI, navegue hasta el conjunto de datos o el informe que quiera analizar en Excel y, después:

1. Seleccione el menú **Más opciones**.

1. Seleccione **Analizar en Excel** en los elementos de menú que aparecen.

    En la imagen siguiente se muestra la selección de un informe.

    ![Instalación de actualizaciones](media/service-analyze-in-excel/analyze-excel-06.png)
    
    >[!NOTE]
    >Recuerde que, si selecciona Analizar en Excel desde el menú de un informe, lo que se abre en Excel es el conjunto de datos subyacente del informe.

    Después, el servicio Power BI crea un archivo de Excel del conjunto de datos que está diseñado (y estructurado) para su uso con **Analizar en Excel** e inicia un proceso de descarga en el explorador.
    
    ![Descarga del archivo de Excel](media/service-analyze-in-excel/analyze-in-excel-download-xlsx.png)

    El nombre de archivo coincide con el conjunto de datos (o informe u otro origen de datos) del que se deriva. Por tanto, si el nombre del informe es *Informe trimestral*, el archivo descargado será **Informe trimestral.xlsx**.

    >[!Note]
    >Analizar en Excel ahora descarga un archivo de Excel en lugar de un archivo ODC. De esta forma, se protegen los datos exportados desde Power BI. El archivo de Excel descargado hereda la etiqueta de confidencialidad del conjunto de archivos elegido para Analizar en Excel.

3. Abra el archivo de Excel.

    >[!NOTE]
    >La primera vez que abra el archivo, es posible que tenga que **Habilitar la edición** y, después, **Habilitar el contenido**, en función de la configuración de [Vista protegida](https://support.microsoft.com/en-gb/office/what-is-protected-view-d6f09ac7-e6b9-4495-8e43-2bbcdbcb6653?ui=en-us&rs=en-gb&ad=gb) y [Documento de confianza](https://support.microsoft.com/en-us/office/trusted-documents-cf872bd8-47ec-4c02-baa5-1fdba1a11b53).
    >
    >![Captura de pantalla del banner Habilitar edición de la vista protegida](media/service-analyze-in-excel/protected-view-enable-editing-banner.png)
    >
    >![Captura de pantalla del banner Habilitar contenido de Documento de confianza](media/service-analyze-in-excel/trusted-document-enable-content-banner.png)

## <a name="use-excel-to-analyze-the-data"></a>Usar Excel para analizar los datos

Una vez que haya habilitado la edición y el contenido, Excel le presentará una **tabla dinámica** vacía y una lista de **campos** del conjunto de datos de Power BI listos para su análisis.

![Excel con datos conectados](media/service-analyze-in-excel/analyze-in-excel-connected.png)

El archivo de Excel tiene una cadena de conexión de MSOLAP que se conecta al conjunto de datos en Power BI. Al analizar o trabajar con los datos, Excel consulta ese conjunto de datos en Power BI y devuelve los resultados a Excel. Si ese conjunto de datos se conecta a un origen de datos activo mediante DirectQuery, Power BI consulta el origen de datos y devuelve el resultado a Excel.

Una vez establecida la conexión con los datos de Power BI, puede crear tablas dinámicas, gráficos y analizar ese conjunto de datos tal como lo haría con un conjunto de datos local en Excel.

**Analizar en Excel** es especialmente útil para los conjuntos de datos e informes que se conectan a los orígenes de datos siguientes:

* Base de datos *tabular de Analysis Services* o base de datos *multidimensional*
* Archivos de Power BI Desktop o libros de Excel con modelos de datos que tienen medidas de modelo creadas con expresiones de análisis de datos (DAX).

> [!IMPORTANT]
> El uso de **Analizar en Excel** expone todos los datos de nivel de detalle a cualquier usuario con permiso para el conjunto de datos.

Hay algunos aspectos que se deben tener en cuenta al empezar a usar Analizar en Excel, lo que podría requerir conciliar uno o dos pasos adicionales. Estas posibilidades se describen en las secciones siguientes. 


### <a name="sign-in-to-power-bi"></a>Iniciar sesión en Power BI
Aunque haya iniciado sesión en Power BI en el explorador, la primera vez que abra un nuevo archivo de Excel en Excel, es posible que se le pida que inicie sesión en Power BI con la cuenta de Power BI. Esto autentica la conexión de Excel a Power BI.

### <a name="users-with-multiple-power-bi-accounts"></a>Usuarios con varias cuentas de Power BI
Algunos usuarios tienen varias cuentas de Power BI. Si es así, es posible que haya iniciado sesión en Power BI con una cuenta, pero que sea otra cuenta la que tenga acceso al conjunto de datos que se está usando en Analizar en Excel. En ese caso, es posible que obtenga un error **Prohibido** o de inicio de sesión al intentar acceder a un conjunto de datos usado en un libro de Analizar en Excel.

Si eso sucede, tendrá la oportunidad de iniciar sesión de nuevo, momento en el cual puede hacerlo con la cuenta de Power BI que tiene acceso a dicho conjunto de datos. También puede seleccionar su nombre en la cinta de opciones superior de Excel, que identifica con qué cuenta inició sesión actualmente. Cierre la sesión y vuelva a iniciarla con la otra cuenta.


## <a name="saving-and-sharing-your-new-workbook"></a>Guardar y compartir un libro

Puede **guardar** el libro de Excel que crea con el conjunto de Power BI como lo haría con cualquier otro libro. Sin embargo, no puede volver a publicar o importar el libro en Power BI porque solo puede publicar o importar libros en Power BI que tengan datos en tablas, o que tengan un modelo de datos. Dado que el nuevo libro simplemente tiene una conexión con el conjunto de datos en Power BI, publicarlo o importarlo en Power BI sería repetir una y otra vez lo mismo.

Una vez guardado el libro, puede compartirlo con otros usuarios de Power BI en su organización. 

Cuando un usuario con el que ha compartido el libro lo abre, verá las tablas dinámicas y los datos tal como estaban cuando se guardó el libro por última vez, lo que no significa que sea la versión más reciente de los datos. Para obtener los datos más recientes, los usuarios deben utilizar el botón **Actualizar** situado en la cinta de opciones **Datos**. Y dado que el libro se conecta a un conjunto de datos en Power BI, los usuarios que intenten actualizarlo deberán iniciar sesión en Power BI e instalar las actualizaciones de Excel la primera vez que lo hagan con este método.

Dado que los usuarios tienen que actualizar el conjunto de datos y no se permite la actualización de conexiones externas en Excel Online, se recomienda que los usuarios abran el libro en la versión de escritorio de Excel de su equipo.

> [!NOTE]
> Los administradores de los inquilinos de Power BI pueden usar el *Portal de administración de Power BI* para deshabilitar el uso de **Analizar en Excel** con conjuntos de datos locales ubicados en bases de datos de Analysis Services (AS). Cuando esta opción está deshabilitada, **Analizar en Excel** está deshabilitado para las bases de datos de AS, pero disponible para su uso con otros conjuntos de datos.


## <a name="other-ways-to-access-power-bi-datasets-from-excel"></a>Otras formas de acceder a los conjuntos de datos de Power BI desde Excel
Los usuarios con SKU de Office específicas también pueden conectarse a los conjuntos de datos de Power BI desde Excel a través de la característica **Obtener datos** de Excel. Si la SKU no es compatible con esta característica, la opción de menú **Obtener datos** no aparece.

En el menú de la cinta de opciones **Datos**, seleccione **Obtener datos > Desde conjunto de datos de Power BI**, tal como se muestra en la imagen siguiente.

![Uso del menú Obtener datos](media/service-analyze-in-excel/analyze-excel-10.png)

Aparece un panel en el que puede examinar los conjuntos de datos a los que tiene acceso, ver si los conjuntos de datos están certificados o promocionados y determinar si se han aplicado etiquetas de protección de datos a esos conjuntos de datos. 

Para más información sobre cómo obtener datos en Excel de esta manera, consulte [Crear una tabla dinámica a partir de conjuntos de valores de Power BI](https://support.office.com/article/31444a04-9c38-4dd7-9a45-22848c666884) en la documentación de Excel.

También puede acceder a las **tablas destacadas** de Excel en la galería **Tipos de datos**. Para más información sobre las tablas destacadas y cómo obtener acceso a ellas, consulte [Acceso a tablas destacadas de Power BI en Excel (versión preliminar)](service-excel-featured-tables.md).

## <a name="requirements"></a>Requisitos
Hay algunos requisitos para usar **Analizar en Excel**:

* **Analizar en Excel** es compatible con Microsoft Excel 2010 SP1 y versiones posteriores.

* Las tablas dinámicas de Excel no admiten la agregación de campos numéricos mediante arrastrar y colocar. El conjunto de datos en Power BI *debe tener medidas definidas previamente*. Obtenga información sobre cómo [crear medidas](../transform-model/desktop-measures.md).
* Algunas organizaciones podrían tener reglas de directiva de grupo que impiden la instalación de las actualizaciones necesarias de **Analizar en Excel** en Excel. Si no puede instalar las actualizaciones, consulte con su administrador.
* **Analizar en Excel** requiere que el conjunto de datos se encuentre en Power BI Premium o que el usuario tenga una licencia de Power BI Pro. Para más información sobre las diferencias de funcionalidad entre los distintos tipos de licencias, eche un vistazo a la sección _Comparación de características de Power BI_ de [Precios de Power BI](https://powerbi.microsoft.com/pricing/).
* Los usuarios pueden conectarse a conjuntos de datos a través de Analizar en Excel si disponen de permiso en el conjunto de datos subyacente.  Un usuario puede disponer de ese permiso de varias maneras; por ejemplo, si tiene el rol Miembro en el área de trabajo que contiene el conjunto de datos, si tiene un informe o panel compartido con él que usa el conjunto de datos o si tiene permiso de compilación en el conjunto de datos ya sea en el área de trabajo o en una aplicación que contiene ese conjunto de datos. Obtenga más información sobre el [permiso de compilación](../connect-data/service-datasets-build-permissions.md) en conjuntos de datos.
* Los usuarios invitados no pueden usar **Analizar en Excel** para los conjuntos de datos enviados desde (que se originen en) otro inquilino. 
* **Analizar en Excel** es una característica del servicio Power BI que no está disponible en Power BI Report Server ni en Power BI Embedded. 
* **Analizar en Excel** solo se admite en equipos donde se ejecuta Microsoft Windows.


En el caso de los usuarios que tengan que desinstalar la característica **Analizar en Excel**, puede hacerlo con la opción de sistema **Agregar o quitar programas**.

## <a name="troubleshooting"></a>Solución de problemas
Puede haber ocasiones en las que al usar Analizar en Excel obtenga un resultado inesperado o que la característica no funcione según lo esperado. [En esta página se ofrecen soluciones a problemas comunes al utilizar Analizar en Excel](desktop-troubleshooting-analyze-in-excel.md).

## <a name="next-steps"></a>Pasos siguientes

Puede que también esté interesado en los siguientes artículos:

* [Uso de la obtención de detalles de varios informes en Power BI Desktop](../create-reports/desktop-cross-report-drill-through.md)
* [Uso de segmentaciones de datos en Power BI Desktop](../visuals/power-bi-visualization-slicers.md)
* [Solución de problemas de Analizar en Excel](desktop-troubleshooting-analyze-in-excel.md)
* [Acceso a tablas destacadas de Power BI en Excel (versión preliminar)](service-excel-featured-tables.md).

