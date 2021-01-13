---
title: 'Power BI para clientes de la Administración Pública de Estados Unidos: información general'
description: Los clientes de la Administración Pública de Estados Unidos pueden agregar una suscripción de Power BI a su plan gubernamental de Microsoft 365. Obtenga información sobre cómo registrarse, conectarse y revisar la disponibilidad de características en esta descripción del servicio.
author: kfollis
ms.author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 01/05/2021
ms.custom: gcc
LocalizationGroup: Get started
ms.openlocfilehash: 9b52e0698f6b9c1ae779bf21738acee30db7447d
ms.sourcegitcommit: 932f6856849c39e34229dc9a49fb9379c56a888a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/06/2021
ms.locfileid: "97927092"
---
# <a name="power-bi-for-us-government-customers"></a>Power BI para clientes de la Administración Pública de Estados Unidos

Este artículo está destinado a los clientes de la Administración Pública de Estados Unidos que implementan Power BI como parte de un plan de Microsoft 365 Administración Pública. Los planes de la Administración Pública están diseñados para las necesidades únicas de las organizaciones que deben cumplir los estándares de cumplimiento y seguridad de Estados Unidos. El servicio Power BI diseñado para los clientes de la Administración Pública de Estados Unidos es distinto de la versión comercial del servicio Power BI. Las funcionalidades y diferencias en las características se describen en las siguientes secciones.

## <a name="add-power-bi-to-your-microsoft-365-government-plan"></a>Incorporación de Power BI a su plan de Microsoft 365 Administración Pública

Antes de que pueda obtener una suscripción a Power BI para la Administración Pública de Estados Unidos y asignar licencias a los usuarios, debe inscribirse en un plan de Microsoft 365 Administración Pública. Si su organización ya tiene un plan de Microsoft 365 Administración Pública, vaya directamente a [Compra de una suscripción de Power BI Pro para los clientes de la Administración Pública](#buy-a-power-bi-pro-subscription-for-government-customers).

### <a name="enroll-in-a-microsoft-365-government-plan"></a>Inscripción en un plan de Microsoft 365 Administración Pública

Si es un cliente nuevo, debe validar la idoneidad de la organización antes de registrarse en un plan de Microsoft 365 Administración Pública.  Para comenzar, complete el [formulario de validación de idoneidad de Microsoft 365 para la Administración Pública](https://www.microsoft.com/microsoft-365/government/eligibility-validation). Para asegurarse de que selecciona el plan correcto para su organización, consulte las [descripciones del servicio Microsoft 365 Administración Pública de Estados Unidos](/office365/servicedescriptions/office-365-platform-service-description/office-365-us-government/office-365-us-government).

> [!NOTE]
> Si ya ha implementado Power BI en un entorno comercial y quiere migrar a la nube de la Administración Pública de Estados Unidos, tendrá que agregar una nueva suscripción de Power BI Pro al plan de Microsoft 365 Administración Pública. A continuación, replique los datos comerciales en el servicio Power BI para la Administración Pública de Estados Unidos, quite las asignaciones de licencias comerciales de las cuentas de usuario y, a continuación, asigne una licencia de Power BI Pro para la Administración Pública a las cuentas de usuario.
>
>
### <a name="buy-a-power-bi-pro-subscription-for-government-customers"></a>Compre una suscripción de Power BI Pro para clientes de la Administración Pública

Una vez que haya implementado Microsoft 365, puede agregar una suscripción a Power BI Pro. Siga las instrucciones paso a paso que se enumeran en el artículo [Inscripción de una organización de la Administración Pública de Estados Unidos](service-govus-signup.md) para comprar el servicio Power BI Pro para la Administración Pública. Compre licencias suficientes para todos los usuarios que necesiten usar Power BI y asígnelas a cuentas de usuario individuales.

> [!IMPORTANT]
> Power BI para la Administración Pública no está disponible como licencia *gratuita*. Para acceder a Government Community Cloud, se debe asignar una licencia de *Pro* a cada usuario. Si una cuenta de usuario tiene asignada una licencia gratuita, el usuario solo tiene autorización para acceder a la nube comercial y surgirán problemas de autenticación y acceso. Si ha comprado Power BI Premium, no tiene que asignar licencias Pro para permitir el acceso de los usuarios.  Los usuarios de la organización pueden acceder a los informes compartidos con ellos, siempre y cuando dichos informes se publique en una capacidad Premium. Para revisar las diferencias entre los tipos de licencia, consulte [Características del servicio Power BI por tipo de licencia](../fundamentals/service-features-license-type.md).
>

## <a name="government-cloud-instances"></a>Instancias en la nube de la Administración Pública

Microsoft 365 proporciona diversos entornos para que los organismos gubernamentales cumplan requisitos de cumplimiento variables. Para más información sobre cada entorno, vea:

* [Government Community Cloud (GCC) de Microsoft 365](/office365/servicedescriptions/office-365-platform-service-description/office-365-us-government/gcc) está diseñado para el gobierno federal, estatal y local.

* [Government Community Cloud High (GCC High) de Microsoft 365](/office365/servicedescriptions/office-365-platform-service-description/office-365-us-government/gcc-high-and-dod) está diseñado para las agencias federales, el sector de la defensa, la industria aeroespacial y otras organizaciones que contienen información sin clasificar controlada. Este entorno es idóneo para organizaciones de seguridad nacional y empresas con datos del reglamento internacional sobre el tráfico de armas (ITAR) o requisitos de Defense Federal Acquisition Regulations Supplement (DFARS).

* El [entorno DoD de Microsoft 365](/office365/servicedescriptions/office-365-platform-service-description/office-365-us-government/gcc-high-and-dod) está diseñado exclusivamente para el Departamento de Defensa de Estados Unidos.


## <a name="sign-in-to-power-bi-for-us-government"></a>Inicio de sesión en Power BI para la Administración Pública de Estados Unidos

La dirección URL para conectarse a Power BI es diferente para los usuarios de la Administración Pública y los usuarios comerciales. Para iniciar sesión en Power BI, use las direcciones URL siguientes:

| Versión comercial  | GCC  | GCC High | DoD |
| --- | --- | --- | --- |
| [https://app.powerbi.com/](https://app.powerbi.com) |[https://app.powerbigov.us](https://app.powerbigov.us) | [https://app.high.powerbigov.us](https://app.high.powerbigov.us) | [https://app.mil.powerbigov.us](https://app.mil.powerbigov.us) |

Es posible que la cuenta esté configurada en más de una nube. Si la cuenta está configurada de esa forma, al iniciar sesión en Power BI Desktop, puede elegir a qué nube conectarse.

## <a name="allow-connections-to-power-bi"></a>Concesión de permiso a conexiones a Power BI

Para usar el servicio Power BI, debe permitir las conexiones a los puntos de conexión necesarios en Internet. Estos destinos deben ser accesibles para permitir la comunicación entre su propia red, Power BI y otros servicios dependientes.

En la tabla siguiente, se enumeran los puntos de conexión necesarios que se deben agregar a la lista de permitidos para habilitar la conexión al servicio Power BI para el uso general del sitio. Estos puntos de conexión son exclusivos de la nube de la Administración Pública de Estados Unidos. El servicio Power BI solo requiere que el puerto TCP 443 esté abierto para los puntos de conexión enumerados. Los puntos de conexión para la obtención de datos, la integración del panel y los informes, los objetos visuales de Power BI y otros servicios opcionales no son exclusivos de la nube de la Administración Pública de Estados Unidos. Para agregar también estas direcciones URL a la lista de permitidos, consulte [Incorporación de direcciones URL de Power BI a la lista de permitidos](power-bi-whitelist-urls.md).

La autenticación, la identidad y la administración de Power BI dependen de la conectividad a los servicios de Microsoft 365. También tiene que conectarse a Microsoft 365 para ver los registros de auditoría. Para identificar los puntos de conexión para estos servicios, vea la integración de Microsoft 365 en la tabla siguiente.

### <a name="power-bi-urls-for-general-site-usage"></a>Direcciones URL de Power BI para el uso general del sitio

|  Propósito | Destination |
| ---- | ----- |
| API de back-end | **GCC**: api.powerbigov.us |
| | **GCC-High**: api.high.powerbigov.us |
| | **DoD**: api.mil.powerbi.gov.us |
| API de back-end | **GCC**: *analysis.usgovcloudapi.net |
| | **GCC High**: *.high.analysis.usgovcloudapi.net |
| | **DoD**: *.mil.analysis.usgovcloudapi.net |
| API de back-end | **All**: *.pbidedicated.usgovcloudapi.net |
| Content Delivery Network (CDN) | **GCC**: gov.content.powerapps.us |
| | **GCC High**: high.content.powerapps.us |
| | **DoD**: mil.content.powerapps.us |
| Integración de Microsoft 365 | **GCC**: [puntos de conexión mundiales](/microsoft-365/enterprise/urls-and-ip-address-ranges) |
| | **GCC High**: [puntos de conexión GCC High para la Administración Pública de Estados Unidos](/microsoft-365/enterprise/microsoft-365-u-s-government-gcc-high-endpoints) |
| | **DoD**: [puntos de conexión DOD para la Administración Pública de Estados Unidos](/microsoft-365/enterprise/microsoft-365-u-s-government-dod-endpoints) |
| Portal |**GCC**: *.powerbigov.us |
| | **GCC-High**: *.high.powerbigov.us |
| | **DoD**: *.mil.powerbigov.us |
| telemetría de servicio | **All**: dc.services.visualstudio.us |
| Mensajes informativos (opcional) | **All**: dynmsg.modpim.com |
| Encuestas NPS (opcional) | **All**: nps.onyx.azure.net |

## <a name="connect-government-and-global-azure-cloud-services"></a>Conexión con de la Administración Pública y los servicios globales en la nube de Azure

Azure se distribuye entre varias nubes. De forma predeterminada, puede habilitar las reglas de firewall para abrir una conexión a una instancia específica de la nube, pero las redes entre nubes son diferentes.  Para la comunicación entre servicios de la nube pública y servicios de Government Community Cloud, debe configurar reglas de firewall específicas. Por ejemplo, si desea acceder a instancias en la nube pública de una base de datos SQL a partir de su implementación de nube de la Administración Pública de Power BI, necesita una regla de firewall en esa base de datos. Configure reglas de firewall específicas para bases de datos SQL para permitir conexiones a la nube de Azure Government para los centros de datos siguientes:

* USGov Iowa
* USGov Virginia
* USGov Texas
* USGov Arizona
* US DoD (este)
* US DoD (centro)

Para obtener los intervalos IP en la nube de la Administración Pública de Estados Unidos, descargue el archivo de [intervalos IP y etiquetas de servicio de Azure: nube de la Administración Pública de Estados Unidos](https://www.microsoft.com/download/details.aspx?id=57063). Los intervalos se enumeran tanto para Power BI como para Power Query.

Para obtener más información sobre los servicios en la nube de Microsoft Azure Government, consulte la [documentación de Azure Government](/azure/azure-government/).

Para configurar firewalls para bases de datos SQL, consulte [Creación y administración de reglas de firewall de IP](/azure/sql-database/sql-database-firewall-configure#create-and-manage-ip-firewall-rules).

## <a name="power-bi-feature-availability"></a>Disponibilidad de características de Power BI

Para adaptarse a los requisitos de los clientes en la nube de la Administración Pública, existen algunas diferencias entre los planes de la Administración Pública y los planes comerciales. Nuestro objetivo es hacer que todas las características estén disponibles en las nubes de gobierno en un plazo de 30 días a partir de la disponibilidad general. En algunos casos, las dependencias subyacentes nos impiden que una característica esté disponible. En la siguiente lista figuran las características que aún no están disponibles en un entorno gubernamental determinado o que están disponibles con funcionalidad limitada. La lista usa la siguiente clave:

|Clave |Descripción|
|-----|------|
|![disponible](../media/yes.png)|La característica está disponible en el entorno, con las excepciones definidas en las notas a pie.|
|![no disponible](../media/no.png)| La característica no está disponible en el entorno, y no existe un período de tiempo estimado para que lo esté.|

Incluiremos el trimestre de disponibilidad estimada si hay una versión prevista para un entorno.

|Característica |GCC |GCC High |DoD|
|------|------|------|------|
|[Colaboración de Azure B2B entre la nube comercial y de gobierno](service-admin-azure-ad-b2b.md)<sup>1</sup>|![disponible](../media/yes.png)|![no disponible](../media/no.png)|![no disponible](../media/no.png)|
|[Inserción en SharePoint Online mediante el elemento web de Power BI](/sharepoint/dev/spfx/web-parts/overview-client-side-web-parts)|![disponible](../media/yes.png)|![Disponible](../media/yes.png)|![no disponible](../media/no.png)|
|[Conectividad de Power Automate para alertas orientadas a datos](../connect-data/power-bi-data-sources.md)|![disponible](../media/yes.png)|![disponible](../media/yes.png)|![no disponible](../media/no.png)|
|[Pestaña de Power BI en Teams](../collaborate-share/service-collaborate-microsoft-teams.md)<sup>2</sup>|![disponible](../media/yes.png)|![no disponible](../media/no.png)|![no disponible](../media/no.png)|
|[Modelos grandes](service-premium-large-models.md) | ![no disponible](../media/no.png) |![no disponible](../media/no.png)| ![no disponible](../media/no.png) |
|[Flujos de datos: optimización del motor de proceso de SQL](../transform-model/dataflows/dataflows-premium-features.md) | ![no disponible](../media/no.png) |![no disponible](../media/no.png)| ![no disponible](../media/no.png) |
|[Flujos de datos: consulta directa](../transform-model/dataflows/dataflows-configure-consume.md) | ![no disponible](../media/no.png) |![no disponible](../media/no.png)|![no disponible](../media/no.png)|
|[Protección de datos (etiquetas MIP)](service-security-sensitivity-label-overview.md)|![no disponible](../media/no.png)|![no disponible](../media/no.png) |![no disponible](../media/no.png)|
|[Aplicaciones plantilla](../connect-data/service-template-apps-overview.md)<sup>3</sup>|![no disponible](../media/no.png) |![no disponible](../media/no.png)| ![no disponible](../media/no.png)|
|[Objetos visuales personalizados](../developer/visuals/power-bi-custom-visuals.md)<sup>3</sup>|![no disponible](../media/no.png) |![no disponible](../media/no.png)| ![no disponible](../media/no.png)|
|[Azure Stream Analytics](/azure/stream-analytics/stream-analytics-power-bi-dashboard)| ![no disponible](../media/no.png)|![no disponible](../media/no.png)|![no disponible](../media/no.png)|
|[Conector de datos de calidad de las llamadas](/microsoftteams/cqd-power-bi-connector)|![no disponible](../media/no.png)|![no disponible](../media/no.png)|![no disponible](../media/no.png)|
|[Traiga su propio almacenamiento (Azure Data Lake Gen 2)](../transform-model/dataflows/dataflows-azure-data-lake-storage-integration.md)|![no disponible](../media/no.png)|![no disponible](../media/no.png)|![no disponible](../media/no.png)|
|[Generación de códigos QR](../create-reports/service-create-qr-code-for-tile.md)|![no disponible](../media/no.png)|![no disponible](../media/no.png)|![no disponible](../media/no.png)|

<sup>1</sup> Aunque la colaboración de B2B está disponible para GCC, se debe emitir al usuario externo una licencia en ese entorno. Las licencias de nubes comerciales no son válidas en GCC. Para obtener más información sobre las limitaciones conocidas de la colaboración de B2B con el Gobierno de EE. UU., [compare Azure Government y Azure global](/azure/azure-government/compare-azure-government-global-azure#azure-active-directory-premium-p1-and-p2).

<sup>2</sup> La experiencia de Power BI en Teams para GCC es limitada, solo funciona para áreas de trabajo clásicas y no incluye la funcionalidad mejorada que se describe en [Inserción de contenido de Power BI en Microsoft Teams](../collaborate-share/service-embed-report-microsoft-teams.md).

<sup>3</sup> La funcionalidad de las aplicaciones de plantilla y los objetos visuales personalizados en el lanzamiento se limitarán a las nubes de gobierno. En la versión se publicará más información sobre las limitaciones específicas.

## <a name="next-steps"></a>Pasos siguientes

* [Registro en Power BI para la Administración Pública de Estados Unidos](service-govus-signup.md)
* [Microsoft Power Apps para la Administración Pública de Estados Unidos](/power-platform/admin/powerapps-us-government)
* [Power Automate para la Administración Pública de Estados Unidos](/power-automate/us-govt)
* [Power BI US Government Demo](https://channel9.msdn.com/Blogs/Azure/Cognitive-Services-HDInsight-and-Power-BI-on-Azure-Government) (Demostración de Power BI para la Administración Pública de Estados Unidos)
