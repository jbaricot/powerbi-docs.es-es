---
title: Uso de controles de Microsoft Cloud App Security en Power BI
description: Obtenga información sobre cómo usar Microsoft Cloud App Security con Power BI
author: paulinbar
ms.author: painbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-eim
ms.topic: how-to
ms.date: 06/15/2020
LocalizationGroup: Data from files
ms.openlocfilehash: f7bd3a59395e9f5f1ea167b7e7988aeb9882a72f
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/01/2020
ms.locfileid: "96413343"
---
# <a name="using-microsoft-cloud-app-security-controls-in-power-bi"></a>Uso de controles de Microsoft Cloud App Security en Power BI

Mediante Cloud App Security con Power BI, puede ayudar a proteger los informes, datos y servicios de Power BI de fugas o infracciones imprevistas. Con Cloud App Security, puede crear directivas de acceso condicional para los datos de la organización, mediante controles de sesión en tiempo real en Azure Active Directory (Azure AD), que le ayudarán a garantizar que los análisis de Power BI sean seguros. Una vez que se han establecido estas directivas, los administradores pueden supervisar el acceso y la actividad de los usuarios, realizar análisis de riesgos en tiempo real y establecer controles específicos de la etiqueta. 

![Uso del panel de controles de Cloud App Security](media/service-security-using-microsoft-cloud-app-security-controls/cloud-app-security-controls-01.png)

Puede configurar Cloud App Security para todo tipo de aplicaciones y servicios, no solo Power BI. Tendrá que configurar Cloud App Security para trabajar con Power BI para beneficiarse de las protecciones de Cloud App Security para los datos y análisis de Power BI. Para obtener más información sobre Cloud App Security, incluida una introducción a su funcionamiento, el panel y las puntuaciones de riesgo de la aplicación, vea la documentación [Cloud App Security](/cloud-app-security/).


## <a name="using-cloud-app-security-with-power-bi"></a>Uso de Cloud App Security con Power BI

Para usar Cloud App Security con Power BI, debe utilizar y configurar los servicios de seguridad de Microsoft pertinentes, algunos de los cuales se establecen fuera de Power BI.

### <a name="cloud-app-security-licensing"></a>Licencias de Cloud App Security

Para tener Cloud App Security en el inquilino, debe tener una de las [licencias](https://query.prod.cms.rt.microsoft.com/cms/api/am/binary/RE2NXYO) siguientes:
* Microsoft Cloud App Security: proporciona funciones de Cloud App Security para todas las aplicaciones compatibles, parte de los conjuntos de aplicaciones EMS E5 y Microsoft 365 E5.
* Office 365 Cloud App Security: proporciona funcionalidades de Cloud App Security solo para Office 365, parte del conjunto de aplicaciones Office 365 E5.
* Azure Active Directory Premium P1, para beneficiarse de las principales funcionalidades de Cloud App Security.

En las secciones siguientes se describen los pasos para usar Cloud App Security en Power BI.

### <a name="set-session-policies-in-azure-ad-required"></a>Establecimiento de directivas de sesión en Azure AD (obligatorio)
Los pasos necesarios para establecer los controles de sesión se completan en los portales de Azure AD y Cloud App Security. En el portal de Azure AD, cree una directiva de acceso condicional para Power BI y enrute las sesiones usadas en Power BI a través del servicio Cloud App Security. 

Cloud App Security funciona mediante una arquitectura de proxy inverso y se integra con el acceso condicional de Azure AD para supervisar la actividad del usuario de Power BI en tiempo real. Los siguientes pasos se proporcionan aquí para ayudarle a entender el proceso y se proporcionan instrucciones paso a paso detalladas en el contenido vinculado en cada uno de los pasos siguientes. También puede consultar este artículo de [Cloud App Security](/cloud-app-security/proxy-deployment-aad) que describe el proceso en su totalidad.

1.  [Cree una directiva de prueba del acceso condicional de Azure AD](/cloud-app-security/proxy-deployment-aad#add-azure-ad)
2.  [Inicie sesión en cada aplicación con un usuario en el ámbito de la directiva](/cloud-app-security/proxy-deployment-aad#sign-in-scoped)
3.  [Compruebe que las aplicaciones están configuradas para usar controles de acceso y de sesión](/cloud-app-security/proxy-deployment-aad#portal)
4.  [Pruebe la implementación](/cloud-app-security/proxy-deployment-aad#step-4-test-the-deployment)

El proceso para establecer directivas de sesión se describe en detalle en el artículo [Directivas de sesión](/cloud-app-security/session-policy-aad). 

### <a name="set-anomaly-detection-policies-to-monitor-power-bi-activities-recommended"></a>Establecimiento de directivas de detección de anomalías para supervisar las actividades de Power BI (recomendado)
Puede definir directivas de detección de anomalías de Power BI que pueden tener un ámbito independiente, de modo que solo se apliquen a los usuarios y grupos que desee incluir y excluir en la directiva. [Más información](/cloud-app-security/anomaly-detection-policy#scope-anomaly-detection-policies).

Cloud App Security también tiene dos detecciones integradas dedicadas para Power BI. [Consulte la sección más adelante en este documento para más información](#built-in-cloud-app-security-detections-for-power-bi).

### <a name="use-microsoft-information-protection-sensitivity-labels-recommended"></a>Uso de las etiquetas de confidencialidad de Microsoft Information Protection (recomendado)

Las etiquetas de confidencialidad le permiten clasificar y ayudar a proteger el contenido confidencial, de modo que los usuarios de la organización puedan colaborar con asociados ajenos a la organización y seguir siendo cuidadosos y conscientes del contenido y los datos confidenciales. 

Puede leer el artículo sobre [etiquetas de confidencialidad en Power BI](service-security-sensitivity-label-overview.md), que detalla el proceso de uso de etiquetas de confidencialidad para Power BI. A continuación se muestra un [ejemplo de una directiva de Power BI basada en etiquetas de confidencialidad](#example).

## <a name="built-in-cloud-app-security-detections-for-power-bi"></a>Detecciones integradas de Cloud App Security para Power BI

Las detecciones de Cloud App Security permiten a los administradores supervisar actividades específicas de una aplicación supervisada. Para Power BI, actualmente hay dos detecciones integradas dedicadas de Cloud App Security: 

* **Recurso compartido sospechoso**: detecta cuándo un usuario comparte un informe confidencial con un correo electrónico desconocido (externo a la organización). Un informe confidencial es un informe cuya etiqueta de confidencialidad se establece en **INTERNAL-ONLY** (solo interno) o superior. 

* **Compartición masiva de informes**: detecta cuándo un usuario comparte una gran cantidad de informes en una sola sesión.

La configuración de estas detecciones se realiza en el portal de Cloud App Security. [Más información](/cloud-app-security/anomaly-detection-policy#unusual-activities-by-user). 

## <a name="power-bi-admin-role-in-cloud-app-security"></a>Rol de administrador de Power BI en Cloud App Security

Cuando se usa Cloud App Security con Power BI, se crea un rol para los administradores de Power BI. Al iniciar sesión como administrador de Power BI en el [portal de Cloud App Security](https://portal.cloudappsecurity.com/), tiene acceso limitado a los datos pertinentes de Power BI, las alertas, los usuarios en riesgo, los registros de actividad y otra información.

## <a name="considerations-and-limitations"></a>Consideraciones y limitaciones 
El uso de Cloud App Security con Power BI se ha diseñado para ayudar a proteger el contenido y los datos de la organización, con detecciones que supervisan las sesiones de usuario y sus actividades. Al usar Cloud App Security con Power BI, hay algunas consideraciones y limitaciones que debe tener en cuenta:

* Cloud App Security solo puede funcionar con archivos de Excel, PowerPoint y PDF.
* Si desea utilizar las funcionalidades de las etiquetas de confidencialidad en las directivas de sesión para Power BI, debe tener una licencia de Azure Information Protection Premium P1 o Premium P2. Microsoft Azure Information Protection se puede adquirir de forma independiente o mediante uno de los conjuntos de licencias de Microsoft. Consulte [Precios de Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection/) para más detalles. Además, se deben haber aplicado las etiquetas de confidencialidad en los recursos de Power BI.
* El control de sesiones está disponible para cualquier explorador de cualquier plataforma principal en cualquier sistema operativo. Se recomienda usar Internet Explorer 11, o las versiones más recientes de Microsoft Edge, Google Chrome, Mozilla Firefox o Apple Safari. Las llamadas API públicas de Power BI y otras sesiones no basadas en el explorador no se admiten como parte del control de sesiones de Cloud App Security. [Vea más detalles](/cloud-app-security/proxy-intro-aad#supported-apps-and-clients).

> [!CAUTION]
> * En la directiva de sesión, en la parte "Acción", la funcionalidad "proteger" solo funcionará si no existe ninguna etiqueta en el elemento. Si ya existe una etiqueta, no se aplicará la acción "proteger"; no se puede invalidar una etiqueta existente que ya se haya aplicado a un elemento de Power BI.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo crear una directiva de sesión mediante Cloud App Security con Power BI.

En primer lugar, cree una nueva directiva de sesión. Seleccione **Directivas** en el menú de la izquierda en el portal de **Cloud App Security**.

![Creación de una nueva directiva de sesión](media/service-security-using-microsoft-cloud-app-security-controls/cloud-app-security-controls-02.png)

En la ventana que aparece, seleccione la lista desplegable **Crear directiva**.

![Selección de Crear directiva](media/service-security-using-microsoft-cloud-app-security-controls/cloud-app-security-controls-03.png)

En la lista de opciones del menú desplegable, seleccione **Directiva de sesión**.

![Selección de directiva de sesión](media/service-security-using-microsoft-cloud-app-security-controls/cloud-app-security-controls-04.png)

En la ventana que aparece, cree la directiva de sesión. En los pasos numerados se describe la configuración de la siguiente imagen.

  1. En la lista desplegable **Plantilla de directiva**, elija *Sin plantilla*.
  2. En el cuadro **Nombre de la directiva**, proporcione un nombre adecuado para la directiva de sesión.
  3. En **Tipo de control de sesión**, seleccione *Control de archivos descargados (con DLP)* .

      Para la sección **Origen de la actividad**, elija las directivas de bloqueo oportunas. Se recomienda bloquear los dispositivos no administrados y no compatibles. Elija bloquear las descargas cuando la sesión es de Power BI.

        ![Creación de la directiva de sesión: bloqueo de descargas.](media/service-security-using-microsoft-cloud-app-security-controls/cloud-app-security-controls-05.png)

        Al desplazarse hacia abajo verá más opciones. En la imagen siguiente se muestran esas opciones, con ejemplos adicionales. 

  4. Para *Etiqueta de confidencialidad*, elija *Extremadamente confidencial* o lo que mejor se adapte a su organización.
  5. Cambie **Método de inspección** a *ninguno*.
  6. Elija la opción **Bloquear** que se ajuste a sus necesidades.
  7. Asegúrese de crear una alerta para dicha acción.

        ![Seleccione la configuración de la directiva de sesión.](media/service-security-using-microsoft-cloud-app-security-controls/cloud-app-security-controls-06.png)

        

  8. Por último, asegúrese de seleccionar el botón **Crear** para crear la directiva de sesión.

        ![Cree la directiva de sesión.](media/service-security-using-microsoft-cloud-app-security-controls/cloud-app-security-controls-07.png)

## <a name="next-steps"></a>Pasos siguientes
En este artículo se describe cómo Cloud App Security puede proporcionar protecciones de datos y contenido para Power BI. También podrían interesarle los siguientes artículos, que describen la protección de datos para Power BI y el contenido de soporte técnico para los servicios de Azure que lo habilitan.

* [Información general sobre las etiquetas de confidencialidad en Power BI](service-security-sensitivity-label-overview.md)
* [Habilitación de etiquetas de confidencialidad en Power BI](service-security-enable-data-sensitivity-labels.md)
* [Aplicación de etiquetas de confidencialidad en Power BI](service-security-apply-data-sensitivity-labels.md)

También podrían interesarle los siguientes artículos de Azure y la seguridad:

* [Proteger aplicaciones con el Control de aplicaciones de acceso condicional de Microsoft Cloud App Security](/cloud-app-security/proxy-intro-aad)
* [Implementación de Control de aplicaciones de acceso condicional para aplicaciones destacadas](/cloud-app-security/proxy-deployment-aad)
* [Directivas de sesión](/cloud-app-security/session-policy-aad)
* [Introducción a las etiquetas de confidencialidad](/microsoft-365/compliance/sensitivity-labels)
* [Informe de métricas de protección de datos](service-security-data-protection-metrics-report.md)