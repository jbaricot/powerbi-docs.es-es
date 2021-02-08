---
title: Etiquetado de los campos de códigos de barras en Power BI Desktop para habilitar el filtrado de digitalización de códigos de barras en aplicaciones móviles
description: Cuando etiquete un campo de código de barras en su modelo de Power BI Desktop, los usuarios de aplicaciones móviles podrán digitalizar códigos de barras para obtener datos filtrados en sus teléfonos y tabletas iOS y Android.
author: paulinbar
ms.author: painbar
ms.service: powerbi
ms.subservice: pbi-transform-model
ms.topic: how-to
ms.date: 01/20/2021
LocalizationGroup: Model your data
ms.openlocfilehash: 4674347d3acd6520d7d156a7d1634a13df611afe
ms.sourcegitcommit: f7330dabb9cd8bce90bb2efec3e3273a11578f10
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2021
ms.locfileid: "99494425"
---
# <a name="tag-barcode-fields-in-power-bi-desktop-to-enable-barcode-scan-filtering-in-the-mobile-apps"></a>Etiquetado de los campos de códigos de barras en Power BI Desktop para habilitar el filtrado de digitalización de códigos de barras en aplicaciones móviles

En Power BI Desktop, puede [clasificar datos](desktop-data-categorization.md) en una columna, de modo que Power BI Desktop sepa cómo tratar los valores en objetos visuales en un informe. También puede clasificar una columna como **Código de barras**. Después, cuando alguien de su compañía u organización [digitalice un código de barras](../consumer/mobile/mobile-apps-scan-barcode-iphone.md) de un producto usando la aplicación móvil de Power BI con su teléfono o tableta iOS o Android, se le mostrará cualquier informe que contenga dicho código de barras. Cuando abra el informe, se filtrará automáticamente con los datos relacionados con el código de barras en cuestión.

## <a name="categorize-barcode-data"></a>Clasificación de datos de códigos de barras

Supongamos que dispone de un informe que contiene códigos de barras: 

1. En Power BI Desktop, cambie a la vista Datos.
2. Seleccione la columna que contiene los datos de código de barras. Vea la lista de [formatos de código de barras admitidos](#supported-barcode-formats) a continuación.
3. En la pestaña **Herramientas de columnas**, seleccione **Categoría de datos** > **Código de barras**.
   
    ![Lista Categoría de datos](media/desktop-mobile-barcodes/power-bi-desktop-barcode.png)

    >[!WARNING]
    >No clasifique más de una columna en todas las tablas de datos de un informe como **Código de barras**. Las aplicaciones móviles solo admiten el filtrado de códigos de barras en informes que únicamente tienen una columna de código de barras en todas las tablas de datos del informe. Si un informe tiene más de una columna de código de barras, no se realiza ningún filtrado.

4. En la vista Informes, agregue el código de barras a los objetos visuales que quiera filtrar por dicho código.
5. Guarde el informe y publíquelo en el servicio Power BI.

Ahora, cuando abra el escáner en las aplicaciones de Power BI para teléfonos y tabletas iOS y Android, y digitalice un código de barras, verá este informe en la lista de informes que tienen códigos de barras. Al abrir el informe, los objetos visuales se filtrarán por el código de barras del producto que ha digitalizado.

## <a name="supported-barcode-formats"></a>Formatos de código de barras admitidos
Estos son los formatos de código de barras que Power BI reconoce si los puede etiquetar en un informe de Power BI: 

* UPCECode 
* Code39Code  
* A39Mod43Code 
* EAN13Code 
* EAN8Code  
* 93Code  
* 128Code 
* PDF417Code 
* Interleaved2of5Code 
* ITF14Code 

## <a name="next-steps"></a>Pasos siguientes
* [Digitalización de un código de barras mediante la aplicación de Power BI en un teléfono o tableta iOS o Android](../consumer/mobile/mobile-apps-scan-barcode-iphone.md)
* [Problemas con la digitalización de códigos de barras](../consumer/mobile/mobile-apps-scan-barcode-iphone.md#issues-with-scanning-a-barcode)
* [Categorización de datos en Power BI Desktop](desktop-data-categorization.md)  
* ¿Tiene alguna pregunta? [Pruebe a preguntar a la comunidad de Power BI](https://community.powerbi.com/)
