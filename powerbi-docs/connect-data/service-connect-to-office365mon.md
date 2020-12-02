---
title: Conexión a Office365Mon con Power BI
description: Office365Mon para Power BI
author: paulinbar
ms.author: painbar
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: how-to
ms.date: 11/26/2019
LocalizationGroup: Connect to services
ms.openlocfilehash: c7433bcc75da316e2e705a63dbcc2f17745ad573
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/01/2020
ms.locfileid: "96403062"
---
# <a name="connect-to-office365mon-with-power-bi"></a>Conexión a Office365Mon con Power BI
Analizar los datos de rendimiento de estado e interrupciones de Office 365 es fácil con Power BI y la plantilla de aplicación Office365Mon. Power BI recupera los datos (incluidos los de sondeo de estado e interrupciones) y, a continuación, crea un panel integrado e informes basados en esos datos.

Conéctese a la [aplicación de plantilla Office365Mon](https://msit.powerbi.com/groups/me/getapps/services/office365mon.office365mon_powerbi_v3) para Power BI.

>[!NOTE]
>Se necesita una cuenta de administrador de Office365Mon para conectarse a la aplicación de plantilla de Power BI y cargarla.

## <a name="how-to-connect"></a>Cómo conectarse
1. Seleccione **Obtener datos** en la parte inferior del panel de navegación.
   
   ![Captura de pantalla del botón Obtener datos, mostrado en el panel de navegación.](media/service-connect-to-office365mon/pbi_getdata.png)
2. En el cuadro **Servicios** , seleccione **Obtener**.
   
   ![Captura de pantalla del cuadro de diálogo Servicios, en el que se muestra el botón Obtener.](media/service-connect-to-office365mon/pbi_getservices.png) 
3. Seleccione **Office365Mon** \> **Obtener**.
   
   ![Captura de pantalla del cuadro de diálogo Office365Mon, en el que se muestra el botón Obtener vínculo.](media/service-connect-to-office365mon/o365mon.png)
4. En Método de autenticación, seleccione **oAuth2** \> **Iniciar sesión**.
   
   Cuando se le solicite, escriba sus credenciales de administrador de Office365Mon y siga el proceso de autenticación.
   
   ![Captura de pantalla del cuadro de diálogo Conectar con Office365Mon, en el que se muestra oAuth2 en el campo Método de autenticación.](media/service-connect-to-office365mon/creds.png)
   
   ![Captura de pantalla del inicio de sesión de Office365Mon, en el que se solicitan las credenciales.](media/service-connect-to-office365mon/creds2.png)
5. Una vez que Power BI haya importado los datos, verá un panel, un informe y un conjunto de datos nuevos en el panel de navegación. Los nuevos elementos están marcados con un asterisco amarillo \*. Seleccione la entrada de Office365Mon.
   
   ![Captura de pantalla del panel de navegación de Power BI, en la que muestran el panel, el informe y el conjunto de datos.](media/service-connect-to-office365mon/dashboard4.png)

**¿Qué más?**

* Pruebe a [hacer una pregunta en el cuadro de preguntas y respuestas](../consumer/end-user-q-and-a.md), en la parte superior del panel.
* [Cambie los iconos](../create-reports/service-dashboard-edit-tile.md) en el panel.
* [Seleccione un icono](../consumer/end-user-tiles.md) para abrir el informe subyacente.
* Aunque el conjunto de datos se programará para actualizarse diariamente, puede cambiar la programación de actualización o intentar actualizar a petición mediante **Actualizar ahora**

## <a name="troubleshooting"></a>Solución de problemas
Si recibe el mensaje **"Error de inicio de sesión"** después de usar las credenciales de la suscripción a Office365Mon para iniciar sesión, la cuenta que está usando no tiene permisos para recuperar los datos de Office365Mon de su cuenta. Compruebe que se trata de una cuenta de administrador y vuelva a intentarlo.

## <a name="next-steps"></a>Pasos siguientes
[¿Qué es Power BI?](../fundamentals/power-bi-overview.md)

[Obtener datos para Power BI](service-get-data.md)
