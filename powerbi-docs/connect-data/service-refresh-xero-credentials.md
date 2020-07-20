---
title: Actualización de las credenciales del paquete de contenido de Xero
description: Si usa el paquete de contenido de Xero Power BI, quizás haya experimentado un problema con la actualización diaria del paquete de contenido debido a un incidente reciente con el servicio de Power BI.
author: SarinaJoan
ms.reviewer: kayu
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
ms.date: 08/10/2017
ms.author: sarinas
LocalizationGroup: Troubleshooting
ms.openlocfilehash: a1697bfce1db1ca92d50bfb83210d21b2820fdae
ms.sourcegitcommit: e8ed3d120699911b0f2e508dc20bd6a9b5f00580
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/11/2020
ms.locfileid: "86263705"
---
# <a name="how-to-refresh-your-xero-content-pack-credentials-if-refresh-failed"></a>Actualización de las credenciales del paquete de contenido de Xero después de un error de actualización
Si usa el paquete de contenido de Xero Power BI, quizás haya experimentado algunos problemas con la actualización diaria del paquete de contenido debido a un incidente reciente con el servicio de Power BI.

Puede ver si el paquete de contenido se actualiza correctamente comprobando el estado de la última actualización para el conjunto de datos Xero como se muestra en la captura de pantalla que aparece a continuación.

![Captura de pantalla del cuadro de diálogo Xero, en la que se muestra el estado de actualización del conjunto de datos Xero.](media/service-refresh-xero-credentials/powerbi-xero-refresh-failed.png)

Si ve que se produce el error de actualización indicado anteriormente, siga estos pasos para renovar sus credenciales del paquete de contenido.

1. Haga clic en **Más opciones** (...) junto a su conjunto de datos Xero y, después, haga clic en **Programar actualización**. Se abre la página de configuración para el paquete de contenido de Xero.
   
    ![Captura de pantalla del cuadro de diálogo Xero con la selección de Programar actualización.](media/service-refresh-xero-credentials/powerbi-xero-schedule-refresh.png)
2. En la página **Configuración de Xero**, seleccione **Credenciales del origen de datos** > **Editar credenciales**.
   
    ![Captura de pantalla del cuadro de diálogo Configuración de Xero, en el que se muestran los valores de Xero con Editar credenciales seleccionado.](media/service-refresh-xero-credentials/powerbi-xero-settings-page.png)
3. Escriba el nombre de su organización > **Siguiente**.
   
    ![Captura de pantalla del cuadro de diálogo Configurar Xero, en el que se muestra el nombre de la organización.](media/service-refresh-xero-credentials/powerbi-xero-configure.png)
4. Inicie sesión con su cuenta de Xero.
   
    ![Captura de pantalla del cuadro de diálogo de inicio de sesión de Xero, en la que se muestra cómo iniciar sesión en la cuenta de Xero.](media/service-refresh-xero-credentials/powerbi-xero-welcome.png)
5. Ahora que sus credenciales están actualizadas, asegurémonos de que se establece la ejecución diaria de la programación de actualización. Para ello, haga clic en **Más opciones** (...) junto a su conjunto de datos Xero y, después, haga clic en **Programar actualización** de nuevo.
   
    ![Captura de pantalla del cuadro de diálogo Programar actualización, en el que muestra la frecuencia de actualización y la zona horaria.](media/service-refresh-xero-credentials/powerbi-xero-refresh-schedule.png)
6. También puede actualizar el conjunto de datos inmediatamente. Haga clic en **Más opciones** (...) junto a su conjunto de datos Xero y, después, haga clic en **Actualizar ahora**.
   
    ![Captura de pantalla del cuadro de diálogo Xero con la selección de Actualizar ahora.](media/service-refresh-xero-credentials/powerbi-xero-refresh-now.png)

Si sigue teniendo problemas de actualización, no dude en ponerse en contacto con nosotros en [https://support.powerbi.com](https://support.powerbi.com) 

Para obtener más información sobre el paquete de contenido de Xero para Power BI, consulte la [página de ayuda del paquete de contenido de Xero](service-connect-to-xero.md).

### <a name="next-steps"></a>Pasos siguientes
* ¿Tiene más preguntas? [Pruebe la comunidad de Power BI](https://community.powerbi.com/)

