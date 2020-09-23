---
title: 'Power BI para clientes de la Administración Pública de Estados Unidos: información general'
description: Los clientes de la Administración Pública de Estados Unidos pueden agregar una suscripción de Power BI Pro a su plan gubernamental de Microsoft 365. Obtenga información sobre cómo registrarse y revisar la disponibilidad de características en esta descripción del servicio.
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 09/02/2020
ms.author: kfollis
ms.custom: licensing support
LocalizationGroup: Get started
ms.openlocfilehash: 948e0260f13aa243a45ba5bdf6fe59c9699d47a0
ms.sourcegitcommit: 9350f994b7f18b0a52a2e9f8f8f8e472c342ea42
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/22/2020
ms.locfileid: "90855113"
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

## <a name="connect-to-power-bi-for-us-government"></a>Conexión a Power BI para la Administración Pública de Estados Unidos

La dirección URL para conectarse a Power BI es diferente para los usuarios de la Administración Pública y los usuarios comerciales. Para iniciar sesión en Power BI, use las direcciones URL siguientes:

| Versión comercial  | GCC  | GCC High | DoD |
| --- | --- | --- | --- |
| [https://app.powerbi.com/](https://app.powerbi.com) |[https://app.powerbigov.us](https://app.powerbigov.us) | [https://app.high.powerbigov.us](https://app.high.powerbigov.us) | [https://app.mil.powerbigov.us](https://app.mil.powerbigov.us) |

Es posible que la cuenta esté configurada en más de una nube. Si la cuenta está configurada de esa forma, al iniciar sesión en Power BI Desktop, puede elegir a qué nube conectarse.

## <a name="connect-government-and-global-azure-cloud-services"></a>Conexión con de la Administración Pública y los servicios globales en la nube de Azure

Azure se distribuye entre varias nubes. De forma predeterminada, puede habilitar las reglas de firewall para abrir una conexión a una instancia específica de la nube, pero las redes entre nubes son diferentes.  Para la comunicación entre servicios de la nube pública y servicios de Government Community Cloud, debe configurar reglas de firewall específicas. Por ejemplo, si desea acceder a instancias en la nube pública de una base de datos SQL a partir de su implementación de nube de la Administración Pública de Power BI, necesita una regla de firewall en esa base de datos. Configure reglas de firewall específicas para bases de datos SQL para permitir conexiones a la nube de Azure Government para los centros de datos siguientes:

* USGov Iowa
* USGov Virginia
* USGov Texas
* USGov Arizona

En la nube pública, hay disponibles intervalos IP. Para obtener los intervalos IP en la nube de la Administración Pública de Estados Unidos, descargue el archivo de [intervalos IP y etiquetas de servicio de Azure: nube de la Administración Pública de Estados Unidos](https://www.microsoft.com/download/details.aspx?id=57063).

Para configurar firewalls para bases de datos SQL, consulte [Creación y administración de reglas de firewall de IP](/azure/sql-database/sql-database-firewall-configure#create-and-manage-ip-firewall-rules).

## <a name="power-bi-feature-availability"></a>Disponibilidad de características de Power BI

Para adaptarse a los requisitos de los clientes en la nube de la Administración Pública, existen algunas diferencias entre los planes de la Administración Pública y los planes comerciales. Nuestro objetivo es hacer que todas las características estén disponibles en las nubes de gobierno en un plazo de 30 días a partir de la disponibilidad general. En algunos casos, las dependencias subyacentes nos impiden que una característica esté disponible.

En la siguiente tabla se enumeran las características que no están disponibles en un entorno de gobierno determinado y la disponibilidad estimada si la versión está planeada:

|Característica |GCC |GCC High |DoD|
|------|------|------|------|
|[Colaboración de Azure B2B entre la nube comercial y de gobierno](service-admin-azure-ad-b2b.md)<sup>1</sup>|![disponible](../media/yes.png)|![no disponible](../media/no.png)|![no disponible](../media/no.png)|
|[Inserción en SharePoint Online mediante el elemento web de Power BI](/esharepoint/dev/spfx/web-parts/overview-client-side-web-parts)|![disponible](../media/yes.png)|![Disponible](../media/yes.png)|![no disponible](../media/no.png)|
|[Conectividad de Power Automate para alertas orientadas a datos](../connect-data/power-bi-data-sources.md)|![disponible](../media/yes.png)|![disponible](../media/yes.png)|![no disponible](../media/no.png)|
|[Pestaña de Power BI en Teams](../collaborate-share/service-collaborate-microsoft-teams.md)<sup>2</sup>|![disponible](../media/yes.png)|![no disponible](../media/no.png)|![no disponible](../media/no.png)|
|[Métricas de capacidad](../admin/service-admin-premium-monitor-portal.md)|T3 2020 |T3 2020|T3 2020|
|[Modelos grandes](service-premium-large-models.md) | T4 2020 |T4 2020| ![no disponible](../media/no.png) |
|[Flujos de datos: optimización del motor de proceso de SQL](../transform-model/service-dataflows-enhanced-compute-engine.md) | T4 2020 |T4 2020| ![no disponible](../media/no.png) |
|[Flujos de datos: consulta directa](../transform-model/service-dataflows-directquery.md) | T4 2020 |T4 2020|![no disponible](../media/no.png)|
|[Notificaciones de interrupción del servicio](service-premium-large-models.md)|T4 2020 |T4 2020|T4 2020|
|[Protección de datos (etiquetas MIP)](service-security-sensitivity-label-overview.md)|T4 2020|T4 2020 |T4 2020|
|[Aplicaciones plantilla](../connect-data/service-template-apps-overview.md)<sup>3</sup>|T4 2020 |T4 2020| T4 2020|
|[Objetos visuales personalizados](../developer/visuals/power-bi-custom-visuals.md)<sup>3</sup>|T4 2020 |T4 2020| T4 2020|
|[Generación de códigos QR](../create-reports/service-create-qr-code-for-tile.md)|![no disponible](../media/no.png)|![no disponible](../media/no.png)|![no disponible](../media/no.png)|

<sup>1</sup> Aunque la colaboración de B2B está disponible para GCC, se debe emitir al usuario externo una licencia en ese entorno. Las licencias de nubes comerciales no son válidas en GCC. Para obtener más información sobre las limitaciones conocidas de la colaboración de B2B con el Gobierno de EE. UU., [compare Azure Government y Azure global](/azure/azure-government/compare-azure-government-global-azure#azure-active-directory-premium-p1-and-p2)

<sup>2</sup> La experiencia de Power BI en Teams para GCC es limitada, solo funciona para áreas de trabajo clásicas y no incluye la funcionalidad mejorada que se describe en [Inserción de contenido de Power BI en Microsoft Teams](../collaborate-share/service-embed-report-microsoft-teams.md).

<sup>3</sup> La funcionalidad de las aplicaciones de plantilla y los objetos visuales personalizados en el lanzamiento se limitarán a las nubes de gobierno. En la versión se publicará más información sobre las limitaciones específicas.

## <a name="next-steps"></a>Pasos siguientes

* [Registro en Power BI para la Administración Pública de Estados Unidos](service-govus-signup.md)
* [Microsoft Power Apps para la Administración Pública de Estados Unidos](/power-platform/admin/powerapps-us-government)
* [Power Automate para la Administración Pública de Estados Unidos](/power-automate/us-govt)
* [Power BI US Government Demo](https://channel9.msdn.com/Blogs/Azure/Cognitive-Services-HDInsight-and-Power-BI-on-Azure-Government) (Demostración de Power BI para la Administración Pública de Estados Unidos)