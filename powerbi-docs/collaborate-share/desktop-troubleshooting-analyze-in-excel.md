---
title: Solución de problemas de análisis en Excel en Power BI Desktop
description: Soluciones a problemas comunes en Analizar en Excel
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-collaborate-share
ms.topic: troubleshooting
ms.date: 05/27/2020
LocalizationGroup: Troubleshooting
ms.openlocfilehash: ae152a99557f86ef82718efdbe3ee767893d15b8
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/01/2020
ms.locfileid: "96412078"
---
# <a name="troubleshooting-analyze-in-excel"></a>Solución de problemas de Analizar en Excel

Puede haber ocasiones en las que al usar Analizar en Excel obtenga un resultado inesperado o que la característica no funcione según lo esperado. Esta página proporciona soluciones para problemas comunes al utilizar Analizar en Excel.

> [!NOTE]
> Hay una página independiente dedicada a describir y habilitar [Analizar en Excel](service-analyze-in-excel.md).
> 
> Si se encuentra con un caso que no se menciona a continuación y está causando problemas, puede pedir ayuda adicional en el [sitio de la comunidad](https://community.powerbi.com/) o crear una [incidencia de soporte técnico](https://powerbi.microsoft.com/support/).
> 
> 

Este artículo contiene las siguientes secciones de solución de problemas:

* Actualización de las bibliotecas de Excel para el proveedor OLE DB
* Determinación de si necesita actualizar las bibliotecas de Excel
* Error de tipo "no se puede realizar la conexión"
* Error Prohibido
* No hay modelos de datos
* Error de token expirado
* No se puede obtener acceso a Analysis Services local
* No se puede arrastrar nada al área de valores de tabla dinámica (no hay medidas)

## <a name="update-excel-libraries-for-the-ole-db-provider"></a>Actualización de las bibliotecas de Excel para el proveedor OLE DB
Para usar **Analizar en Excel**, el equipo debe tener instalado un proveedor AS OLE DB actual. Esta [entrada de la Comunidad](https://community.powerbi.com/t5/Service/Analyze-in-Excel-Initialization-of-the-data-source-failed/m-p/30837#M8081) es una excelente fuente para comprobar la instalación del proveedor OLE DB o para descargar una versión actualizada.

Las bibliotecas de Excel tienen que coincidir con su versión de Windows en términos de número de bits. Si cuenta con Windows de 64 bits, debe instalar el proveedor OLE DB de 64 bits.

Para descargar las bibliotecas más recientes de Excel, visite Power BI y seleccione la **flecha hacia abajo** en la esquina superior derecha del servicio Power BI. A continuación, seleccione **Analizar en actualizaciones de Excel**.

![Captura de pantalla de la opción de menú de flecha abajo en la esquina superior derecha para seleccionar Analizar en actualizaciones de Excel.](media/desktop-troubleshooting-analyze-in-excel/tshoot-analyze-excel_1.png)

En el cuadro de diálogo que aparece, seleccione **Descargar (versión preliminar)** .

![Captura de pantalla del cuadro de diálogo Analizar en actualizaciones de Excel para seleccionar el botón Descargar u obtener vista previa.](media/desktop-troubleshooting-analyze-in-excel/tshoot-analyze-excel_2.png)

## <a name="determining-whether-you-need-to-update-your-excel-libraries"></a>Determinación de si necesita actualizar las bibliotecas de Excel
Puede descargar la versión más reciente de las bibliotecas del proveedor OLE DB de Excel a partir de los vínculos de la sección anterior. Una vez que descargue la biblioteca del proveedor OLD DB apropiada y comience la instalación, se realizarán las comprobaciones en la versión instalada actualmente.

Si las bibliotecas de cliente de proveedor OLE DB de Excel están actualizadas, verá un cuadro de diálogo similar al siguiente:

![Captura de pantalla del cuadro de diálogo en el que se pide que se actualice si hay disponible una versión más reciente de la biblioteca cliente del proveedor de OLE DB de Excel.](media/desktop-troubleshooting-analyze-in-excel/troubleshoot-analyze-excel_3.png)

Como alternativa, si la nueva versión que está instalando es más reciente que la versión en el equipo, aparecerá el cuadro de diálogo siguiente:

![Captura de pantalla del cuadro de diálogo para confirmar una actualización durante la instalación de las bibliotecas cliente del proveedor OLE DB de Excel.](media/desktop-troubleshooting-analyze-in-excel/troubleshoot-analyze-excel_2.png)

Si ve un cuadro de diálogo que le solicita que actualice, debe continuar con la instalación para obtener la versión más reciente del proveedor OLE DB instalado en el equipo.

## <a name="connection-cannot-be-made-error"></a>Error de tipo "no se puede realizar la conexión"
La causa principal de un error de tipo *no se puede realizar la conexión* es que las bibliotecas de cliente del proveedor OLE DB de su equipo no están actualizadas. Para obtener información sobre cómo determinar la actualización correcta, y para los vínculos de descarga, consulte la sección anterior **Actualización de las bibliotecas de Excel para el proveedor OLE DB** de este artículo.

## <a name="forbidden-error"></a>Error Prohibido
Algunos usuarios tienen más de una cuenta de Power BI y cuando Excel intenta conectarse a Power BI mediante las credenciales existentes, puede usar las credenciales que no tienen acceso al conjunto de datos o al informe al que desea obtener acceso.

Cuando esto ocurre, puede recibir un error llamado **Prohibido**, que significa que puede que haya iniciado sesión en Power BI con credenciales que no tienen permisos en el conjunto de datos. Después de que aparezca el error **Prohibido**, cuando se le pida que escriba las credenciales, utilice las credenciales que tengan permiso para obtener acceso al conjunto de datos que está intentando utilizar.

Si sigue experimentando errores, inicie sesión en Power BI con la cuenta que tiene permiso y compruebe que puede ver el conjunto de datos y obtener acceso al conjunto de datos en Power BI al que está intentando tener acceso en Excel.

## <a name="no-data-models"></a>No hay modelos de datos
Si se produce un error que indica **Can't find OLAP cube model** (No se puede encontrar el modelo del cubo OLAP), el conjunto de datos al que está intentando obtener acceso no tiene ningún modelo de datos y, por tanto, no se puede analizar en Excel.

## <a name="token-expired-error"></a>Error de token expirado
Si recibe un error de **token expirado** significa que no ha utilizado recientemente la característica **Analizar en Excel** en el equipo que está utilizando. Simplemente vuelva a escribir sus credenciales o vuelva a abrir el archivo, y el error deberían desaparecer.

## <a name="unable-to-access-on-premises-analysis-services"></a>No se puede obtener acceso a Analysis Services local
Si está intentando obtener acceso a un conjunto de datos que tiene conexiones a datos de Analysis Services locales, puede que reciba un mensaje de error. **Analizar en Excel** admite la conexión a informes y conjuntos de datos en **Analysis Services** local con una cadena de conexión, siempre y cuando el equipo está en el mismo dominio que el servidor de **Analysis Services** y la cuenta tiene acceso a ese servidor de **Analysis Services**.

## <a name="cant-drag-anything-to-the-pivottable-values-area-no-measures"></a>No se puede arrastrar nada al área de valores de tabla dinámica (no hay medidas)
Cuando **Analizar en Excel** se conecta a un modelo OLAP externo (que es la forma en que Excel se conecta a Power BI), la *tabla dinámica* requiere que se definan **medidas** en el modelo externo, ya que todos los cálculos se realizan en el servidor. Esto es diferente a cuando se trabaja con un origen de datos local (como tablas de Excel, o bien cuando se trabaja con conjuntos de datos en **Power BI Desktop** o en el **servicio Power BI**), en cuyo caso el modelo tabular está disponible localmente y [se pueden usar medidas implícitas](https://support.microsoft.com/en-us/office/measures-in-power-pivot-86484821-a324-4da3-803b-82fd2e5033f4), que son medidas que se generan dinámicamente y no se almacenan en el modelo de datos. En estos casos, el comportamiento de Excel difiere del comportamiento en **Power BI Desktop** o en el **servicio Power BI**: podría haber columnas en los datos que se pueden tratar como medidas en Power BI, pero no es posible usarlas como valores (medidas) en Excel.

Para solucionar este problema, tiene varias opciones:

1. Cree [medidas en el modelo de datos en **Power BI Desktop**](../transform-model/desktop-tutorial-create-measures.md); después publique el modelo de datos en el **servicio Power BI** y acceda desde Excel a ese conjunto de datos publicado.
2. Cree [medidas en el modelo de datos desde PowerPivot para Excel](https://support.office.com/article/Create-a-Measure-in-Power-Pivot-d3cc1495-b4e5-48e7-ba98-163022a71198).
3. Si ha importado los datos de un libro de Excel que solo tenía tablas (y ningún modelo de datos), puede [agregar las tablas al modelo de datos](https://support.office.com/article/Add-worksheet-data-to-a-Data-Model-using-a-linked-table-d3665fc3-99b0-479d-ba09-a37640f5be42) y, después, seguir los pasos de la opción 2 anterior para crear medidas en el modelo de datos.

Una vez que las medidas se hayan definido en el modelo en el servicio Power BI, podrá usarlas en el área **Valores** de las tablas dinámicas de Excel.

## <a name="next-steps"></a>Pasos siguientes
[Analizar en Excel](service-analyze-in-excel.md)

[Tutorial: Creación de medidas propias en Power BI Desktop](../transform-model/desktop-tutorial-create-measures.md)

[Medidas en PowerPivot](https://support.microsoft.com/en-us/office/measures-in-power-pivot-86484821-a324-4da3-803b-82fd2e5033f4)

[Crear una medida en PowerPivot](https://support.office.com/article/Create-a-Measure-in-Power-Pivot-d3cc1495-b4e5-48e7-ba98-163022a71198)

[Agregar datos de hoja de cálculo a un modelo de datos mediante tablas vinculadas](https://support.office.com/article/Add-worksheet-data-to-a-Data-Model-using-a-linked-table-d3665fc3-99b0-479d-ba09-a37640f5be42)
