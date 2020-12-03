---
title: Habilitación de la certificación de contenido
description: Obtenga información sobre cómo habilitar la certificación para conjuntos de datos, flujos de información, informes y aplicaciones.
author: paulinbar
ms.author: painbar
ms.service: powerbi
ms.subservice: powerbi-eim
ms.topic: how-to
ms.date: 10/26/2020
LocalizationGroup: Share your work
ms.openlocfilehash: 17fc02131f13fe7fe7d8fb17af4380f6a013b9e7
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/01/2020
ms.locfileid: "96413527"
---
# <a name="enable-content-certification"></a>Habilitación de la certificación de contenido

La organización puede certificar contenido seleccionado para identificarlo como un origen autoritativo de información crítica. Actualmente, se pueden certificar estos tipos de contenido:
* Conjuntos de datos
* Flujos de datos (versión preliminar)
* Informes (versión preliminar)
* Aplicaciones (versión preliminar)

Como administrador de Power BI, es el responsable de habilitar y configurar el proceso de certificación para su organización. Esto significa lo siguiente:
* Habilitar la certificación en el inquilino.
* Definir una lista de grupos de seguridad cuyos miembros estarán autorizados para certificar el contenido.
* Proporcionar una dirección URL que apunte a la documentación del proceso de certificación de contenido de la organización, si dicha documentación existe.

La certificación forma parte de la característica de *aprobación* de Power BI. Vea [Aprobación: promoción y certificación del contenido de Power BI](../collaborate-share/service-endorsement-overview.md) para obtener más información.

## <a name="set-up-certification"></a>Configuración de la certificación

1. En el portal de administración, vaya a Configuración de inquilinos.
1. En la sección Configuración de exportación y uso compartido, expanda la sección Certificación.

   ![Certificación para la configuración de conjuntos de datos y flujos de datos](media/service-admin-setup-certification/service-admin-certification-setup-dialog.png)

1. Establezca el control de alternancia en **Habilitado**.
1. Si la organización tiene una directiva de certificación publicada, proporcione aquí su dirección URL. Se convertirá en el vínculo **Más información** de la sección de certificación del [cuadro de diálogo de Configuración de aprobación](../collaborate-share/service-endorse-content.md#request-content-certification). Si no proporciona un vínculo, se aconsejará a los usuarios que quieran solicitar la certificación de su contenido que se pongan en contacto con su administrador de Power BI.
1. Especifique uno o más grupos de seguridad cuyos miembros estarán autorizados para certificar el contenido. Estos emisores de certificados autorizados podrán usar el botón Certificación que hay en la sección de certificación del [cuadro de diálogo de configuración de la aprobación](../collaborate-share/service-endorse-content.md#certify-content).
    
    Si un grupo de seguridad contiene subgrupos de seguridad a los que no quiere conceder derechos de certificación, puede activar la casilla **Excepto grupos de seguridad específicos** y escribir los nombres de esos grupos en un cuadro de texto que aparecerá.
1. Haga clic en **Aplicar**.

## <a name="next-steps"></a>Pasos siguientes
* [Promover o certificar contenido](../collaborate-share/service-endorse-content.md)
* [Más información sobre la aprobación en Power BI](../collaborate-share/service-endorsement-overview.md)
* ¿Tiene alguna pregunta? [Pruebe a preguntar a la comunidad de Power BI](https://community.powerbi.com/)
