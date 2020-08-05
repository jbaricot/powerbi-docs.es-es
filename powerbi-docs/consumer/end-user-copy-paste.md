---
title: Copia y pegado de una visualización en el servicio Power BI
description: Copia y pegado de una visualización en el servicio Power BI
author: mihart
ms.reviewer: maggie.tsang
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: how-to
ms.date: 06/25/2020
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: dc5cba8953a527e87768815759a14dd8f2cf7ee1
ms.sourcegitcommit: 2131f7b075390c12659c76df94a8108226db084c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/03/2020
ms.locfileid: "87537858"
---
# <a name="copy-a-visual-as-an-image-to-your-clipboard"></a>Copia de un objeto visual como imagen en el portapapeles

[!INCLUDE[consumer-appliesto-yyyn](../includes/consumer-appliesto-yyyn.md)]

¿Alguna vez ha querido compartir una imagen de un informe o de un panel de Power BI? Ahora puede copiar el objeto visual y pegarlo en cualquier otra aplicación que admita el pegado. 

Cuando se copia una imagen estática de un objeto visual, se obtiene una copia del mismo junto con los metadatos. Esto incluye:
* Vínculo al informe o al panel de Power BI
* Título del informe o del panel
* Aviso si la imagen contiene información confidencial
* Hora de la última actualización
* Filtros aplicados al objeto visual

### <a name="copy-from-a-dashboard-tile"></a>Copia desde un icono de panel

1. Navegue al panel desde el que quiera copiar.

2. En la esquina superior derecha del objeto visual, seleccione **Más acciones (…)** y elija **Copiar objeto visual como imagen**. 

    ![Icono "Copiar objeto visual como imagen" resaltado](media/end-user-copy-paste/power-bi-copy-dashboard.png)

3. Cuando aparezca el cuadro de diálogo **El objeto visual ya se puede copiar**, seleccione **Copiar al portapapeles**.

    ![Cuadro de diálogo con la opción "Copiar al portapapeles"](media//end-user-copy-paste/power-bi-copied.png)

4. Una vez copiado el objeto visual, péguelo en otra aplicación mediante **Ctrl+V** o haga clic con el botón derecho y seleccione Pegar. En la siguiente captura de pantalla, hemos pegado el objeto visual en Microsoft Word. 

    ![Objeto visual pegado en Word](media//end-user-copy-paste/power-bi-paste-word.png)

### <a name="copy-from-a-report-visual"></a>Copia desde el objeto visual de un informe 

1. Navegue al informe desde el que quiera copiar.

2. En la esquina superior derecha del objeto visual, seleccione el icono **Copiar objeto visual como imagen**. 

    ![Icono "Copiar objeto visual como imagen" resaltado](media/end-user-copy-paste/power-bi-copy-icon.png)

3. Cuando aparezca el cuadro de diálogo **El objeto visual ya se puede copiar**, seleccione **Copiar al portapapeles**.

    ![Cuadro de diálogo con la opción "Copiar al portapapeles"](media//end-user-copy-paste/power-bi-copied.png)


4. Una vez copiado el objeto visual, péguelo en otra aplicación mediante **Ctrl+V** o haga clic con el botón derecho y seleccione Pegar. En la siguiente captura de pantalla, hemos pegado el objeto visual en un correo electrónico.

    ![Objeto visual pegado en Outlook](media//end-user-copy-paste/power-bi-copy-email.png)

5. Si hay una etiqueta de confidencialidad de datos aplicada al informe, recibirá una advertencia al seleccionar el icono de copia.  

    ![Advertencia de datos confidenciales](media//end-user-copy-paste/power-bi-sensitive.png)

    Además, se agregará una etiqueta de confidencialidad a los metadatos que se encuentran debajo del objeto visual pegado. 

    ![Objeto visual con una etiqueta de información confidencial](media//end-user-copy-paste/power-bi-confidential.png)



## <a name="considerations-and-troubleshooting"></a>Consideraciones y solución de problemas

   ![Copia no disponible](media//end-user-copy-paste/power-bi-copy-grey.png)


P: ¿Por qué está deshabilitado el icono de copia en un objeto visual?    
R: Actualmente se admiten objetos visuales nativos de Power BI y objetos visuales personalizados certificados. Hay compatibilidad limitada con ciertos objetos visuales, entre los que se incluyen: 
- ESRI y otros objetos visuales de mapa 
- Objetos visuales de Python 
- Objetos visuales de R 
- PowerApps    

R: El departamento de TI o el administrador de Power BI pueden desactivar la opción para copiar un objeto visual.


P: ¿Por qué mi objeto visual no se pega correctamente?    
R: Existen limitaciones para los objetos visuales personalizados y los objetos visuales animados. 



## <a name="next-steps"></a>Pasos siguientes
Obtenga más información sobre [Visualizaciones en informes de Power BI](end-user-visual-type.md)

¿Tiene más preguntas? [Pruebe la comunidad de Power BI](https://community.powerbi.com/)

