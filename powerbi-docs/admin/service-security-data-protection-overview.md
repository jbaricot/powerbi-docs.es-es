---
title: Protección de datos en Power BI
description: Obtenga información sobre cómo funciona la protección de datos en Power BI
author: paulinbar
manager: rkarlin
ms.service: powerbi
ms.subservice: powerbi-eim
ms.topic: how-to
ms.date: 06/15/2020
ms.author: painbar
LocalizationGroup: Data from files
ms.openlocfilehash: 4575c80106329a00c959db73c2851c99959f41ec
ms.sourcegitcommit: 46a340937d9f01c6daba86a4ab178743858722ec
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/26/2020
ms.locfileid: "85393666"
---
# <a name="data-protection-in-power-bi"></a>Protección de datos en Power BI

Las empresas modernas tienen normas y requisitos empresariales estrictos sobre cómo administrar y proteger los datos confidenciales. Para proporcionar control y visibilidad sobre estos datos, Power BI se integra con Microsoft Information Protection y Microsoft Cloud App Security. Esto le permite:
* Usar las [etiquetas de confidencialidad](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels?view=o365-worldwide) de Microsoft Information Protection para clasificar y etiquetar el contenido (paneles, informes, conjuntos de datos y flujos de datos) en el servicio Power BI con la misma taxonomía usada para clasificar y proteger archivos en Office 365.
* Aplicar la protección y las etiquetas de confidencialidad de Microsoft Information Protection a los datos cuando se exportan a archivos de Excel, PowerPoint o PDF.
* Usar Microsoft Cloud App Security para supervisar las actividades de Power BI, investigar problemas de seguridad y proteger el contenido de Power BI con Control de aplicaciones de acceso condicional de Microsoft Cloud App Security.

**Notas importantes**
* Las etiquetas de confidencialidad **no** afectan al acceso al contenido dentro de Power BI: se administra únicamente mediante los permisos de Power BI. Mientras las etiquetas son visibles, no se aplican las opciones de cifrado asociadas (configuradas en el [Centro de seguridad de Microsoft 365](https://security.microsoft.com/) o el [Centro de cumplimiento de Microsoft 365](https://compliance.microsoft.com/)). Solo se aplican a los datos que se exportan a archivos de Excel, PowerPoint y PDF.
* Las etiquetas de confidencialidad y el cifrado de archivos **no** se aplican en ninguna ruta de exportación que no sea a Excel, PowerPoint y PDF. El administrador del inquilino de Power BI puede deshabilitar cualquiera o todas las rutas de exportación que no admitan la aplicación de etiquetas de confidencialidad y su configuración de cifrado de archivos asociada.

## <a name="sensitivity-labels-in-power-bi"></a>Etiquetas de confidencialidad en Power BI

Las etiquetas de confidencialidad se crean y administran en el [Centro de seguridad de Microsoft 365](https://security.microsoft.com/) o el [Centro de cumplimiento de Microsoft 365](https://compliance.microsoft.com/).

Para acceder a las etiquetas de confidencialidad en cualquiera de estos centros, vaya a **Clasificación > Etiquetas de confidencialidad**. Estas etiquetas de confidencialidad se pueden usar en varios servicios de Microsoft, como Azure Information Protection, las aplicaciones de Office y los servicios de Office 365.

> [!Important]
> Si en la organización se usan etiquetas de confidencialidad de Azure Information Protection, tendrá que [migrarlas](https://docs.microsoft.com/azure/information-protection/configure-policy-migrate-labels) a uno de los servicios enumerados antes para que se puedan usar en Power BI.

> [!NOTE]
> Las etiquetas de confidencialidad solo se admiten para inquilinos de nubes públicas, no para los de nubes nacionales.

## <a name="how-sensitivity-labels-work-in-power-bi"></a>Cómo funcionan las etiquetas de confidencialidad en Power BI

Cuando se aplica una etiqueta de confidencialidad a un panel, informe, conjunto de datos o flujo de datos de Power BI, es similar a aplicar una etiqueta a ese recurso con las ventajas siguientes:
* **Personalizable**: puede crear categorías para diferentes niveles de contenido confidencial en su organización, como personal, público, general, confidencial y extremadamente confidencial.
* **Texto no cifrado**: como la etiqueta está en texto sin cifrar, es fácil que los usuarios sepan cómo tratar el contenido de acuerdo con las instrucciones de la etiqueta de confidencialidad.
* **Persistente**: después de aplicar una etiqueta de confidencialidad al contenido, le acompaña cuando se exporta a archivos de Excel, PowerPoint y PDF, y se convierte en la base de la aplicación de directivas.

Esto significa que la etiqueta de confidencialidad sigue al contenido cuando se exporta a archivos de Excel, PowerPoint y PDF, y se convierte en la base de la aplicación de directivas.

Los administradores de inquilinos de Power BI pueden controlar la [exportación a Excel](service-admin-portal.md#export-to-excel) y la [exportación a PowerPoint y PDF](service-admin-portal.md#export-reports-as-powerpoint-presentations-or-pdf-documents) en el [portal de administración de Power BI](service-admin-portal.md).

## <a name="sensitivity-label-example"></a>Ejemplo de etiqueta de confidencialidad

A continuación se muestra un ejemplo rápido de cómo funciona una etiqueta de confidencialidad en Power BI.
1. En el servicio Power BI, se aplica una etiqueta de confidencialidad **Extremadamente confidencial** a un informe.

   ![Etiquetas de confidencialidad en la vista de lista](media/service-security-data-protection-overview/sensitivity-labels-overview-01.png)
   
1. Cuando los datos se exportan a un archivo de Excel desde este informe, la etiqueta de confidencialidad y la protección se aplican al archivo de Excel exportado.

   ![La etiqueta de confidencialidad sigue al contenido](media/service-security-data-protection-overview/sensitivity-labels-overview-02.png)

En las aplicaciones de Microsoft Office, una etiqueta de confidencialidad aparece como una etiqueta en el correo electrónico o el documento, de forma similar a lo que se muestra en la imagen anterior. También puede asignar una clasificación al contenido (como un adhesivo) que se conserva y se mueve con el contenido a medida que se usa y se comparte en Power BI. Puede usar esta clasificación para generar informes de uso y ver los datos de actividad del contenido confidencial. En función de esta información, siempre puede elegir más adelante aplicar la configuración de protección.

## <a name="requirements-for-using-sensitivity-labels-in-power-bi"></a>Requisitos para el uso de etiquetas de confidencialidad en Power BI

Antes de poder habilitar las etiquetas de confidencialidad y usarlas en Power BI, primero debe completar los siguientes requisitos previos:
* Asegúrese de que las etiquetas de confidencialidad se han definido en el [Centro de seguridad de Microsoft 365](https://security.microsoft.com/) o el [Centro de cumplimiento de Microsoft 365](https://compliance.microsoft.com/).
* [Habilite las etiquetas de confidencialidad](service-security-enable-data-sensitivity-labels.md) en Power BI.
* Asegúrese de que los usuarios tienen las [licencias adecuadas](#licensing).
* Si usa Microsoft Cloud App Security con Power BI, asegúrese de tener las [licencias adecuadas](service-security-using-microsoft-cloud-app-security-controls.md#cloud-app-security-licensing).

## <a name="protect-content-using-microsoft-cloud-app-security"></a>Protección del contenido con Microsoft Cloud App Security

Puede proteger el contenido de Power BI contra fugas o infracciones imprevistas mediante el uso de Microsoft Cloud App Security. Una vez que se ha configurado Microsoft Cloud App Security, los administradores de seguridad pueden supervisar el acceso y la actividad de los usuarios, realizar análisis de riesgos en tiempo real y establecer controles específicos de la etiqueta.

Por ejemplo, las organizaciones pueden usar Microsoft Cloud App Security para configurar una directiva que impida a los usuarios descargar datos confidenciales de Power BI a dispositivos no administrados. Esta configuración permite a los usuarios seguir siendo productivos y conectarse a Power BI desde cualquier lugar, mientras se usa Microsoft Cloud App Security para evitar poner en peligro las acciones del usuario, todo en tiempo real.

**Requisitos**

Para que las etiquetas de confidencialidad puedan usar Microsoft Cloud App Security, se deben cumplir los siguientes requisitos previos:
* Cloud App Security y Azure Information Protection [deben estar habilitados para el inquilino](https://docs.microsoft.com/cloud-app-security/azip-integration).
* La aplicación [debe estar conectada a Microsoft Cloud App Security](https://docs.microsoft.com/cloud-app-security/enable-instant-visibility-protection-and-governance-actions-for-your-apps).

## <a name="licensing"></a>Licencias

* Para ver o aplicar las etiquetas de confidencialidad de Microsoft Information Protection en Power BI, es necesaria una licencia de Azure Information Protection Premium P1 o Premium P2. Microsoft Azure Information Protection se puede adquirir de forma independiente o mediante uno de los conjuntos de licencias de Microsoft. Consulte [Precios de Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection/) para más detalles.
* La visualización y la aplicación de etiquetas en las aplicaciones de Office tienen [requisitos de licencias](https://docs.microsoft.com/microsoft-365/compliance/get-started-with-sensitivity-labels#subscription-and-licensing-requirements-for-sensitivity-labels).
* Para aplicar etiquetas a contenido de Power BI, un usuario debe tener una licencia de Power BI Pro además de una de las licencias de Azure Information Protection mencionadas anteriormente.
* Debe disponer de las [licencias necesarias para Microsoft Cloud App Security](https://docs.microsoft.com/power-bi/admin/service-security-using-microsoft-cloud-app-security-controls#microsoft-cloud-app-security-licensing) si lo va a usar para proteger el contenido de Power BI contra pérdidas e infracciones imprevistas.

## <a name="considerations-and-limitations"></a>Consideraciones y limitaciones

En la lista siguiente se proporcionan algunas limitaciones de las etiquetas de confidencialidad en Power BI:

**General**
* Las etiquetas de confidencialidad solo se pueden aplicar en paneles, informes, conjuntos de datos y flujos de datos. En la actualidad no hay etiquetas de confidencialidad disponibles para [informes paginados](../paginated-reports/report-builder-power-bi.md) y libros.
* Las etiquetas de confidencialidad de los recursos de Power BI son visibles en la lista de áreas de trabajo y en las vistas de linaje, favoritos, recientes y aplicaciones; no son visibles actualmente en la vista "compartido conmigo". Tenga en cuenta, sin embargo, que una etiqueta aplicada a un recurso de Power BI, incluso si no está visible, siempre se conservará en los datos exportados a archivos de Excel, PowerPoint y PDF.
* Las etiquetas de confidencialidad solo se admiten para los inquilinos en la nube global (pública). No se admiten las etiquetas de confidencialidad para los inquilinos de otras nubes.
* No se admiten las etiquetas de confidencialidad para las aplicaciones de plantilla. Las etiquetas de confidencialidad establecidas por el creador de la aplicación de plantilla se quitan cuando se extrae la aplicación y se instala. Asimismo, al actualizar la aplicación, las etiquetas de confidencialidad agregadas a los artefactos de una aplicación de plantilla instalada por el consumidor de la aplicación se pierden (se restablecen vacías).
* Power BI no admite etiquetas de confidencialidad de los tipos de protección [No reenviar](https://docs.microsoft.com/microsoft-365/compliance/encryption-sensitivity-labels?view=o365-worldwide#let-users-assign-permissions), [definido por el usuario](https://docs.microsoft.com/microsoft-365/compliance/encryption-sensitivity-labels?view=o365-worldwide#let-users-assign-permissions) e [HYOK](https://docs.microsoft.com/azure/information-protection/configure-adrms-restrictions). Los tipos de protección No reenviar y definido por el usuario hacen referencia a las etiquetas definidas en el [Centro de seguridad de Microsoft 365](https://security.microsoft.com/) o el [Centro de cumplimiento de Microsoft 365](https://compliance.microsoft.com/).
* No se recomienda permitir que los usuarios apliquen etiquetas primarias en Power BI. Si se aplica una etiqueta primaria al contenido, se producirá un error al exportar los datos de ese contenido a un archivo (Excel, PowerPoint y PDF). Vea [Subetiquetas (etiquetas de agrupación)](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels?view=o365-worldwide#sublabels-grouping-labels).

**Exportarar**
* Los controles de etiqueta y protección solo se aplican cuando los datos se exportan a archivos de Excel, PowerPoint y PDF. La etiqueta y la protección no se aplican cuando los datos se exportan a archivos .csv o .pbix, Analizar en Excel o cualquier otra ruta de exportación.
* La aplicación de una etiqueta de confidencialidad y de protección a un archivo exportado no le agrega marcas de contenido. Pero si la etiqueta está configurada para aplicar marcas de contenido, el cliente de etiquetado unificado de Azure Information Protection las aplica de forma automática cuando el archivo se abre en las aplicaciones de escritorio de Office. Las marcas de contenido no se aplican de forma automática cuando se usa el etiquetado integrado para aplicaciones web, para dispositivos móviles o de escritorio. Vea [Cuando las aplicaciones de Office aplican marcas de contenido y cifrado](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels-office-apps?view=o365-worldwide#when-office-apps-apply-content-marking-and-encryption) para obtener más detalles.
* Un usuario que exporta un archivo de Power BI tiene permisos para acceder al archivo y editarlo según la configuración de la etiqueta de confidencialidad. El usuario que exporta los datos no obtiene permisos de propietario en el archivo.
* Se producirá un error en la exportación si no se puede aplicar una etiqueta al exportar los datos a un archivo. Para comprobar si se ha producido un error en la exportación porque no se ha podido aplicar la etiqueta, haga clic en el nombre del panel o informe en el centro de la barra de título y compruebe si en el cuadro desplegable de información que se abre se indica "No se puede cargar la etiqueta de confidencialidad". Esto puede suceder si el administrador de seguridad no ha publicado o ha eliminado la etiqueta aplicada, o bien es el resultado de un problema temporal del sistema.


## <a name="next-steps"></a>Pasos siguientes

En este artículo se proporciona una introducción a la protección de datos en Power BI. En los artículos siguientes se proporcionan más detalles acerca de la protección de datos en Power BI. 

* [Habilitación de etiquetas de confidencialidad de datos en Power BI](service-security-enable-data-sensitivity-labels.md)
* [Aplicación de etiquetas de confidencialidad de datos en Power BI](../collaborate-share/service-security-apply-data-sensitivity-labels.md)
* [Uso de controles de Microsoft Cloud App Security en Power BI](service-security-using-microsoft-cloud-app-security-controls.md)
* [Informe de métricas de protección de datos](service-security-data-protection-metrics-report.md)