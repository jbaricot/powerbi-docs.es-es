---
title: Línea de base de seguridad de Azure para Power BI
description: La línea de base de seguridad de Power BI proporciona instrucciones de procedimientos y recursos para implementar las recomendaciones de seguridad especificadas en Azure Security Benchmark.
author: msmbaldwin
ms.service: security
ms.topic: conceptual
ms.date: 11/20/2020
ms.author: mbaldwin
ms.custom: subject-security-benchmark
ms.openlocfilehash: b0eb2906463efa95615fa76f3f7dda2a91ef126a
ms.sourcegitcommit: 9d033abd9c01a01bba132972497dda428d7d5c12
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/24/2020
ms.locfileid: "95550574"
---
# <a name="azure-security-baseline-for-power-bi"></a>Línea de base de seguridad de Azure para Power BI

Esta línea de base de seguridad aplica las instrucciones de la [versión 2.0 de Azure Security Benchmark](https://docs.microsoft.com/azure/security/benchmarks/overview) a Power BI. Azure Security Benchmark proporciona recomendaciones sobre cómo puede proteger sus soluciones de nube en Azure. El contenido se agrupa mediante los **controles de seguridad** definidos por Azure Security Benchmark y las instrucciones relacionadas aplicables a Power BI. Se han excluido los **controles** que no se aplican a Power BI.

Para ver cómo Power BI coincide por completo con Azure Security Benchmark, vea el [archivo de asignación de línea de base de seguridad completo de Power BI](https://github.com/MicrosoftDocs/SecurityBenchmarks/tree/master/Azure%20Offer%20Security%20Baselines).

## <a name="network-security"></a>Seguridad de redes

*Para más información, consulte [Azure Security Benchmark: seguridad de red](/azure/security/benchmarks/security-controls-v2-network-security).*

### <a name="ns-3-establish-private-network-access-to-azure-services"></a>NS-3: establecimiento del acceso de red privada a los servicios de Azure

**Instrucciones**: Power BI admite la conexión del inquilino de Power BI a un punto de conexión de vínculo privado y la deshabilitación del acceso público a Internet.

- [Vínculos privados para acceder a Power BI](https://docs.microsoft.com/power-bi/admin/service-security-private-links)

**Supervisión de Azure Security Center**: No aplicable

**Responsabilidad**: Compartido

## <a name="identity-management"></a>Administración de identidades

*Para más información, consulte [Azure Security Benchmark: Administración de identidades](/azure/security/benchmarks/security-controls-v2-identity-management).*

### <a name="im-1-standardize-azure-active-directory-as-the-central-identity-and-authentication-system"></a>IM-1: Unificación en Azure Active Directory como sistema central de identidad y autenticación

**Instrucciones**: Power BI se integra con Azure Active Directory (Azure AD), que es el servicio de administración de identidades y acceso predeterminado de Azure. Debe usar Azure AD como estándar para controlar la administración de identidades y el acceso de la organización.

La protección de Azure AD debe tener máxima prioridad en la práctica de seguridad en la nube de su organización. Azure AD proporciona una puntuación de seguridad de la identidad para ayudarle a evaluar el estado de seguridad de la identidad en relación con los procedimientos recomendados de Microsoft. Use la puntuación para medir el grado de coincidencia de la configuración con los procedimientos recomendados y para hacer mejoras en la posición de seguridad.

Nota: Azure AD admite identidades externas que permiten a los usuarios que no tienen un cuenta de Microsoft iniciar sesión en sus aplicaciones y recursos con su identidad externa.

- [Inquilinos en Azure Active Directory](https://docs.microsoft.com/azure/active-directory/develop/single-and-multi-tenant-apps)

- [Procedimiento para crear y configurar una instancia de Azure AD](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-access-create-new-tenant)

- [Uso de proveedores de identidades externos para una aplicación](https://docs.microsoft.com/azure/active-directory/b2b/identity-providers)

- [¿Qué es la puntuación de seguridad de la identidad en Azure Active Directory?](https://docs.microsoft.com/azure/active-directory/fundamentals/identity-secure-score)

**Supervisión de Azure Security Center**: No aplicable

**Responsabilidad**: Customer

### <a name="im-2-manage-application-identities-securely-and-automatically"></a>IM-2: Administración de identidades de aplicaciones de forma segura y automática

**Instrucciones**: Power BI y Power BI Embedded admiten el uso de entidades de servicio. Almacene las credenciales de entidad de servicio que se usan para cifrar o acceder a Power BI en un almacén de claves, asigne directivas de acceso adecuadas al almacén y revise los permisos de acceso de forma periódica.

Automatización de tareas de área de trabajo y conjunto de datos de Premium con entidades de servicio https://docs.microsoft.com/power-bi/admin/service-premium-service-principal

**Supervisión de Azure Security Center**: No aplicable

**Responsabilidad**: Customer

### <a name="im-3-use-azure-ad-single-sign-on-sso-for-application-access"></a>IM-3: Uso del inicio de sesión único de Azure AD para acceder a las aplicaciones

**Instrucciones**: Power BI usa Azure Active Directory para proporcionar administración de identidad y acceso a los recursos de Azure, las aplicaciones en la nube y las aplicaciones locales. Esto incluye identidades empresariales, como empleados, así como identidades externas, como asociados y proveedores. Esto permite que el inicio de sesión único (SSO) administre y proteja el acceso a los datos y recursos de la organización locales y en la nube. Conecte todos los usuarios, las aplicaciones y los dispositivos a Azure AD para obtener un acceso seguro y sin problemas, además de mayor visibilidad y control.

- [Descripción del SSO de aplicación con Azure AD](https://docs.microsoft.com/azure/active-directory/manage-apps/what-is-single-sign-on)

**Supervisión de Azure Security Center**: No aplicable

**Responsabilidad**: Customer

### <a name="im-4-use-strong-authentication-controls-for-all-azure-active-directory-based-access"></a>IM-4: Uso de controles con autenticación multifactor sólida para todo el acceso basado en Azure Active Directory

**Instrucciones**: Power BI se integra con Azure AD que admite controles de autenticación segura mediante la autenticación multifactor (MFA) y métodos sin contraseñas seguros.
- Autenticación multifactor: habilite MFA de Azure AD y siga las recomendaciones de administración de identidades y acceso de Azure Security Center para obtener algunos procedimientos recomendados para la configuración de MFA. MFA se puede aplicar en todos los usuarios, en usuarios concretos o por usuario en función de las condiciones de inicio de sesión y los factores de riesgo.
- Autenticación sin contraseña: existen tres opciones de autenticación sin contraseña disponibles: Windows Hello para empresas, la aplicación Microsoft Authenticator y métodos de autenticación locales como las tarjetas inteligentes.

Para los administradores y usuarios con privilegios, asegúrese de que se usa el nivel más alto de autenticación segura, seguido de la implementación de la directiva de autenticación segura adecuada para otros usuarios.

Nota: MFA solo se puede aplicar a las cuentas de usuario habilitadas en Azure AD. Las entidades de servicio de Power BI no admiten el uso de MFA.

- [Procedimiento para habilitar la MFA en Azure](https://docs.microsoft.com/azure/active-directory/authentication/howto-mfa-getstarted)

- [Introducción a las opciones de autenticación sin contraseña de Azure Active Directory](https://docs.microsoft.com/azure/active-directory/authentication/concept-authentication-passwordless)

**Supervisión de Azure Security Center**: No aplicable

**Responsabilidad**: Customer

### <a name="im-5-monitor-and-alert-on-account-anomalies"></a>IM-5: Supervisión y alerta de anomalías de cuenta

**Instrucciones**: Defina directivas de detección de anomalías en Microsoft Cloud App Security que pueden tener un ámbito independiente, de modo que solo se apliquen a los usuarios y grupos que quiera incluir. Estas directivas de detección de anomalías pueden ayudar a detectar y supervisar las anomalías de comportamiento relacionadas con los usuarios que acceden a Power BI y lo utilizan.

- [Uso de controles de Microsoft Cloud App Security en Power BI](https://docs.microsoft.com/power-bi/admin/service-security-using-microsoft-cloud-app-security-controls)

**Supervisión de Azure Security Center**: No aplicable

**Responsabilidad**: Customer

### <a name="im-6-restrict-azure-resource-access-based-on-conditions"></a>IM-6: Restricción del acceso a recursos de Azure en función de las condiciones

**Instrucciones**: Power BI admite el acceso condicional de Azure AD para un control de acceso más pormenorizado en función de condiciones definidas por el usuario; por ejemplo, los inicios de sesión de usuario desde determinados intervalos IP tendrán que usar MFA para el inicio de sesión. También se puede usar la directiva de administración de sesión de autenticación granular para distintos casos de uso.

- [Información general sobre el acceso condicional de Azure](https://docs.microsoft.com/azure/active-directory/conditional-access/overview)

- [Directivas de acceso condicional habituales](https://docs.microsoft.com/azure/active-directory/conditional-access/concept-conditional-access-policy-common)

- [Configuración de la administración de las sesiones de autenticación con el acceso condicional](https://docs.microsoft.com/azure/active-directory/conditional-access/howto-conditional-access-session-lifetime)

- [Uso de controles de Microsoft Cloud App Security en Power BI](https://docs.microsoft.com/power-bi/admin/service-security-using-microsoft-cloud-app-security-controls)

**Supervisión de Azure Security Center**: No aplicable

**Responsabilidad**: Customer

### <a name="im-7-eliminate-unintended-credential-exposure"></a>IM-7: Elimine la exposición de credenciales no intencionada

**Instrucciones**: Para las aplicaciones insertadas de Power BI, se recomienda implementar el escáner de credenciales para identificar las credenciales en el código. El escáner de credenciales también fomenta el traslado de credenciales detectadas a ubicaciones más seguras, como Azure Key Vault.

Almacene las claves de cifrado o credenciales de entidad de servicio que se usan para cifrar o acceder a Power BI en un almacén de claves, asigne directivas de acceso adecuadas al almacén y revise los permisos de acceso de forma periódica.
 
En GitHub, puede usar la característica de escaneo de secretos nativos para identificar credenciales u otro tipo de secretos en el código.

- [Sus propias claves de cifrado para Power BI](https://docs.microsoft.com/power-bi/admin/service-encryption-byok)

 
Configuración de credenciales
- [Escáner](https://secdevtools.azurewebsites.net/helpcredscan.html) 

- [Escaneo de secretos de GitHub](https://docs.github.com/github/administering-a-repository/about-secret-scanning)

**Supervisión de Azure Security Center**: No aplicable

**Responsabilidad**: Compartido

## <a name="privileged-access"></a>Acceso con privilegios

*Para más información, consulte [Azure Security Benchmark: Acceso con privilegios](/azure/security/benchmarks/security-controls-v2-privileged-access).*

### <a name="pa-1-protect-and-limit-highly-privileged-users"></a>PA-1: Protección y limitación de usuarios con privilegios elevados

**Instrucciones**: Para reducir el riesgo y seguir el principio de privilegios mínimos, se recomienda mantener la pertenencia de los administradores de Power BI a un número reducido de usuarios. Los usuarios con estos permisos con privilegios podrían acceder a todas las características de administración de la organización y modificarlas. Los administradores globales, a través de Microsoft 365 o Azure Active Directory, poseen implícitamente derechos de administrador en el servicio Power BI.

Power BI tiene cuentas con privilegios elevados:
- Administrador global
- Administrador de facturación
- Administrador de licencias
- Administrador de usuarios
- Administrador de Power BI
- Administrador de Capacidad de Power BI Premium
- Administrador de capacidad de Power BI Embedded

Power BI admite directivas de sesión en Azure AD para habilitar directivas de acceso condicional y enrutar las sesiones que se usan en Power BI a través del servicio Cloud App Security.

Habilite el acceso con privilegios Just-in-Time (JIT) para las cuentas de administrador de Power BI mediante Privileged Access Management de M365.

- [Roles de administrador relacionados con Power BI](https://docs.microsoft.com/power-bi/admin/service-admin-administering-power-bi-in-your-organization#administrator-roles-related-to-power-bi)

- [Privileged Access Management de M365](https://docs.microsoft.com/microsoft-365/compliance/privileged-access-management-overview?view=o365-worldwide&amp;preserve-view=true)

- [Controles de Cloud App Security en Power BI](https://docs.microsoft.com/power-bi/admin/service-security-using-microsoft-cloud-app-security-controls)

**Supervisión de Azure Security Center**: No aplicable

**Responsabilidad**: Customer

### <a name="pa-2-restrict-administrative-access-to-business-critical-systems"></a>PA-2: Restricción del acceso administrativo a los sistemas críticos para la empresa

**Instrucciones**: Limite el número de roles o cuentas con privilegios elevados con acceso elevado a Power BI.

Puede habilitar el acceso con privilegios Just-in-Time (JIT) mediante [estas](https://docs.microsoft.com/microsoft-365/compliance/privileged-access-management-overview?view=o365-worldwide&amp;preserve-view=true) instrucciones de Privileged Access Management de M365.

Puede encontrar más detalles en la página 183 de [este](https://aka.ms/PBIEnterpriseDeploymentWP) documento de implementación de Power BI Enterprise.

**Supervisión de Azure Security Center**: No aplicable

**Responsabilidad**: Customer

### <a name="pa-3-review-and-reconcile-user-access-regularly"></a>PA-3: Revisión y conciliación de manera periódica del acceso de los usuarios

**Instrucciones**: Como administrador del servicio Power BI, puede analizar el uso de todos los recursos de Power BI en el nivel de inquilino mediante informes personalizados basados en el registro de actividad de Power BI. Puede descargar las actividades mediante una API REST o un cmdlet de PowerShell. También puede filtrar los datos de actividad por intervalo de fechas, usuario y tipo de actividad.

Debe cumplir estos requisitos para acceder al registro de actividad de Power BI:
- Debe ser un administrador global o un administrador del servicio Power BI.
- Ha instalado los [cmdlets de administración de Power BI](https://www.powershellgallery.com/packages/MicrosoftPowerBIMgmt) localmente o usa los cmdlets de administración de Power BI en Azure Cloud Shell.

Una vez que se han cumplido estos requisitos, puede seguir las instrucciones siguientes para realizar el seguimiento de la actividad del usuario en Power BI:

- [Seguimiento de la actividad de los usuarios en Power BI](https://docs.microsoft.com/power-bi/admin/service-admin-auditing)

**Supervisión de Azure Security Center**: No aplicable

**Responsabilidad**: Customer

### <a name="pa-4-set-up-emergency-access-in-azure-ad"></a>PA-4: Configuración del acceso de emergencia en Azure AD

**Instrucciones**: Power BI se integra con Azure Active Directory y M365 para administrar sus recursos. Para evitar el bloqueo accidental del inquilino de M365 o la organización de Azure AD, configure una cuenta de acceso de emergencia para el acceso cuando no se puedan usar cuentas administrativas normales. Las cuentas de acceso de emergencia tienen normalmente privilegios elevados y no se asignan a usuarios específicos. Las cuentas de acceso de emergencia se limitan a situaciones "excepcionales" o de emergencia en las que no se pueden usar las cuentas administrativas normales.

Debe asegurarse de que las credenciales (como contraseña, certificado o tarjeta inteligente) de las cuentas de acceso de emergencia estén protegidas y solo las conozcan aquellas personas que estén autorizadas a usarlas solo en caso de emergencia.

- [Administración de cuentas de acceso de emergencia en Azure AD](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-emergency-access)

- [Protección de las cuentas de M365](https://docs.microsoft.com/microsoft-365/campaigns/m365-campaigns-protect-admin-accounts)

**Supervisión de Azure Security Center**: No aplicable

**Responsabilidad**: Customer

### <a name="pa-6-use-privileged-access-workstations"></a>PA-6: Uso de estaciones de trabajo con privilegios de acceso

**Guía**: Las estaciones de trabajo seguras y aisladas son de una importancia vital para la seguridad de los roles con acceso a información confidencial como administradores, desarrolladores y operadores de servicios críticos. Use estaciones de trabajo de usuario de alta seguridad o Azure Bastion para las tareas administrativas relacionadas con la administración de Power BI. Use Azure Active Directory, Protección contra amenazas avanzada de Microsoft Defender (ATP) o Microsoft Intune para implementar una estación de trabajo de usuario segura y administrada para las tareas administrativas. Las estaciones de trabajo protegidas se pueden administrar de forma centralizada para aplicar una configuración segura, como autenticación sólida, líneas de base de software y hardware y acceso lógico y de red restringido.

Descripción del acceso con privilegios
- [estaciones de trabajo](https://docs.microsoft.com/azure/active-directory/devices/concept-azure-managed-workstation)

- [Implementación de una estación de trabajo con privilegios de acceso](https://docs.microsoft.com/azure/active-directory/devices/howto-azure-managed-workstation)

**Supervisión de Azure Security Center**: No aplicable

**Responsabilidad**: Customer

## <a name="data-protection"></a>Protección de datos

*Para más información, consulte [Azure Security Benchmark: protección de datos](/azure/security/benchmarks/security-controls-v2-data-protection).*

### <a name="dp-1-discovery-classify-and-label-sensitive-data"></a>DP-1: Detección, clasificación y etiquetado de datos confidenciales

**Instrucciones**: Use etiquetas de confidencialidad de Microsoft Information Protection en los informes, paneles, conjuntos de datos y flujos de datos para proteger el contenido confidencial contra pérdidas y el acceso no autorizado a los datos.

Use etiquetas de confidencialidad de Microsoft Information Protection para clasificar y etiquetar los informes, paneles, conjuntos de datos y flujos de datos del servicio Power BI y para proteger el contenido confidencial del acceso a datos no autorizado y la pérdida de datos cuando se exporta desde el servicio Power BI a archivos de Excel, PowerPoint y PDF.

- [Aplicación de etiquetas de confidencialidad en Power BI](https://docs.microsoft.com/power-bi/admin/service-security-apply-data-sensitivity-labels)

**Supervisión de Azure Security Center**: No aplicable

**Responsabilidad**: Customer

### <a name="dp-2-protect-sensitive-data"></a>DP-2: Protección de datos confidenciales

**Instrucciones**: Power BI se integra con las etiquetas de confidencialidad de Microsoft Information Protection para la protección de datos confidenciales. Para obtener más información, vea [Etiquetas de confidencialidad de Microsoft Information Protection en Power BI](https://docs.microsoft.com/power-bi/admin/service-security-sensitivity-label-overview)

Power BI permite a los usuarios del servicio aportar su propia clave para proteger los datos en reposo. Para obtener más información, vea [Sus propias claves de cifrado para Power BI](https://docs.microsoft.com/power-bi/admin/service-encryption-byok).

Los clientes tienen la opción de mantener los orígenes de datos locales y aprovechar Direct Query o Live Connect con una puerta de enlace de datos local para minimizar la exposición de los datos al servicio en la nube. Para obtener más información, vea [¿Qué es una puerta de enlace de datos local?](https://docs.microsoft.com/data-integration/gateway/service-gateway-onprem).

Power BI admite la seguridad de nivel de fila. Para obtener más información, vea [Seguridad de nivel de fila (RLS) con Power BI](https://docs.microsoft.com/power-bi/admin/service-admin-rls). Tenga en cuenta que RLS se puede aplicar incluso a orígenes de datos de Direct Query, en cuyo caso el archivo PBIX actúa como un proxy de habilitación de seguridad.

**Supervisión de Azure Security Center**: No aplicable

**Responsabilidad**: Customer

### <a name="dp-3-monitor-for-unauthorized-transfer-of-sensitive-data"></a>DP-3: Supervisión de la transferencia no autorizada de datos confidenciales

**Instrucciones**: Este control se puede lograr parcialmente mediante la compatibilidad de Microsoft Cloud App Security con Power BI.

Mediante Cloud App Security con Power BI, puede ayudar a proteger los informes, datos y servicios de Power BI de fugas o infracciones imprevistas. Con Cloud App Security, puede crear directivas de acceso condicional para los datos de la organización, mediante controles de sesión en tiempo real en Azure Active Directory (Azure AD), que le ayudarán a garantizar que los análisis de Power BI sean seguros. Una vez que se han establecido estas directivas, los administradores pueden supervisar el acceso y la actividad de los usuarios, realizar análisis de riesgos en tiempo real y establecer controles específicos de la etiqueta.

Uso
- [Controles de Microsoft Cloud App Security en Power BI](https://docs.microsoft.com/power-bi/admin/service-security-using-microsoft-cloud-app-security-controls)

**Supervisión de Azure Security Center**: No aplicable

**Responsabilidad**: Customer

### <a name="dp-4-encrypt-sensitive-information-in-transit"></a>DP-4: Cifrado de la información confidencial en tránsito

**Instrucciones**: Asegúrese de que, para el tráfico HTTP, los clientes y los orígenes de datos que se conectan a los recursos de Power BI pueden negociar TLS v1.2 o superior.

- [Aplicación del uso de la versión TLS](https://docs.microsoft.com/power-bi/admin/service-admin-power-bi-security#enforcing-tls-version-usage)

- [Información sobre la seguridad de TLS](https://docs.microsoft.com/security/engineering/solving-tls1-problem)

**Supervisión de Azure Security Center**: No aplicable

**Responsabilidad**: Customer

### <a name="dp-5-encrypt-sensitive-data-at-rest"></a>DP-5: Cifrado de datos confidenciales en reposo

**Instrucciones**: Power BI cifra los datos en reposo y en proceso. De forma predeterminada, Power BI usa claves administradas por Microsoft para cifrar los datos. Las organizaciones pueden optar por usar sus propias claves para el cifrado del contenido del usuario en reposo en Power BI, desde imágenes de informe hasta conjuntos de datos importados en capacidades Premium.

- [Uso de claves propias en Power BI](https://docs.microsoft.com/power-bi/admin/service-encryption-byok)

**Supervisión de Azure Security Center**: No aplicable

**Responsabilidad**: Compartido

## <a name="asset-management"></a>Administración de recursos

*Para más información, consulte [Azure Security Benchmark: Administración de recursos](/azure/security/benchmarks/security-controls-v2-asset-management).*

### <a name="am-1-ensure-security-team-has-visibility-into-risks-for-assets"></a>AM-1: Asegurarse de que el equipo de seguridad tiene visibilidad sobre los riesgos para los recursos

**Instrucciones**: Use Azure Sentinel con los registros de auditoría de Office de Power BI para asegurarse de que el equipo de seguridad tiene visibilidad sobre los riesgos para los recursos de Power BI.

- [Conexión de registros de Office 365 a Azure Sentinel](https://docs.microsoft.com/azure/sentinel/connect-office-365)

**Supervisión de Azure Security Center**: No aplicable

**Responsabilidad**: Customer

### <a name="am-2-ensure-security-team-has-access-to-asset-inventory-and-metadata"></a>AM-2: Asegurarse de que el equipo de seguridad tiene acceso a los metadatos y al inventario de recursos

**Instrucciones**: Asegúrese de que los equipos de seguridad tengan acceso a un inventario actualizado continuamente de recursos de Power BI Embedded. Los equipos de seguridad suelen necesitar este inventario para evaluar la exposición potencial de su organización a los riesgos emergentes y como una entrada para mejoras de seguridad continuas. 

Azure Resource Graph puede consultar y detectar todos los recursos de Power BI Embedded de las suscripciones.  

Organice de forma lógica los recursos según la taxonomía de su organización mediante etiquetas y otros metadatos en Azure (nombre, descripción y categoría).  

- [Creación de consultas con Azure Resource Graph Explorer](https://docs.microsoft.com/azure/governance/resource-graph/first-query-portal)

- [Guía de decisiones de nomenclatura y etiquetado de recursos](https://docs.microsoft.com/azure/cloud-adoption-framework/decision-guides/resource-tagging/?toc=/azure/azure-resource-manager/management/toc.json)

**Supervisión de Azure Security Center**: No aplicable

**Responsabilidad**: Customer

### <a name="am-3-use-only-approved-azure-services"></a>AM-3: Uso exclusivo de servicios de Azure aprobados

**Instrucciones**: Power BI admite implementaciones basadas en Azure Resource Manager para Power BI Embedded y puede restringir la implementación de sus recursos a través de Azure Policy mediante una definición de directiva personalizada.

Use Azure Policy para auditar y restringir qué servicios pueden aprovisionar los usuarios en su entorno. Use Azure Resource Graph para consultar y detectar recursos dentro de sus suscripciones. También puede usar Azure Monitor para crear reglas para desencadenar alertas cuando se detecta un servicio no aprobado.

- [Configuración y administración de Azure Policy](https://docs.microsoft.com/azure/governance/policy/tutorials/create-and-manage)

Procedimiento para denegar un tipo de recurso específico con
- [Azure Policy](https://docs.microsoft.com/azure/governance/policy/samples/built-in-policies#general)

Procedimiento para crear consultas con Azure
- [Resource Graph Explorer](https://docs.microsoft.com/azure/governance/resource-graph/first-query-portal)

**Supervisión de Azure Security Center**: No aplicable

**Responsabilidad**: Customer

## <a name="logging-and-threat-detection"></a>registro y detección de amenazas

*Para más información, consulte [Azure Security Benchmark: registro y detección de amenazas](/azure/security/benchmarks/security-controls-v2-logging-threat-protection).*

### <a name="lt-2-enable-threat-detection-for-azure-identity-and-access-management"></a>LT-2: Habilitación de la detección de amenazas para la administración de identidades y acceso de Azure

**Instrucciones**: Reenvíe cualquier registro desde Power BI a la Administración de eventos e información de seguridad, que se puede usar para configurar detecciones de amenazas personalizadas. Además, use los controles de Microsoft Cloud App Security (MCAS) en Power BI para habilitar la detección de anomalías mediante [esta](https://docs.microsoft.com/power-bi/admin/service-security-using-microsoft-cloud-app-security-controls) guía.

- [Seguimiento de actividades de usuario en Power BI](https://docs.microsoft.com/power-bi/admin/service-admin-auditing)

**Supervisión de Azure Security Center**: No aplicable

**Responsabilidad**: Customer

### <a name="lt-3-enable-logging-for-azure-network-activities"></a>LT-3: Habilitación del registro para las actividades de red de Azure

**Instrucciones**: Power BI es una oferta de SaaS totalmente administrada y la configuración de red subyacente y el registro son responsabilidad de Microsoft. Para los clientes que usan vínculos privados, se pueden configurar algunos registros y parte de la supervisión.

- [Registro y supervisión de Private Link](https://docs.microsoft.com/azure/private-link/private-link-overview#logging-and-monitoring)

**Supervisión de Azure Security Center**: No aplicable

**Responsabilidad**: Compartido

### <a name="lt-4-enable-logging-for-azure-resources"></a>LT-4: Habilitación del registro para recursos de Azure

**Instrucciones**: Con Power BI, tiene dos opciones para realizar el seguimiento de la actividad del usuario: El registro de actividad de Power BI y el registro de auditoría unificado. Estos registros contienen una copia completa de los datos de auditoría de Power BI, pero hay varias diferencias clave, como se resume a continuación.
 
Registro de auditoría unificado:

 
- Incluye eventos de SharePoint Online, Exchange Online, Dynamics 365 y otros servicios además de los eventos de auditoría de Power BI.

 
- Solo tienen acceso, como administradores globales y auditores, los usuarios con permisos Registros de auditoría o Registros de auditoría de solo lectura.

 
- Los administradores y auditores globales pueden buscar en el registro de auditoría unificado mediante el Centro de seguridad de Microsoft 365 y el Centro de cumplimiento de Microsoft 365.

 
- Los administradores y auditores globales pueden descargar entradas del registro de auditoría mediante los cmdlets y las API de administración de Microsoft 365.

 
- Mantiene los datos de auditoría durante 90 días.

 
- Conserva los datos de auditoría, incluso si el inquilino se mueve a otra región de Azure.
 
Registro de actividad de Power BI:

 
- Solo incluye los eventos de auditoría de Power BI.

 
 
- Los administradores globales y los administradores del servicio Power BI tienen acceso.

 
- Todavía no hay ninguna interfaz de usuario para buscar en el registro de actividad.

 
- Los administradores globales y los administradores del servicio Power BI pueden descargar entradas del registro de actividad mediante una API REST de Power BI y un cmdlet de administración.

 
- Conserva los datos de actividad durante 30 días.

 
- No conserva los datos de actividad cuando el inquilino se mueve a otra región de Azure.

- [Datos de auditoría de Power BI](https://docs.microsoft.com/power-bi/admin/service-admin-auditing#operations-available-in-the-audit-and-activity-logs)

- [Registro de actividad de Power BI](https://docs.microsoft.com/power-bi/admin/service-admin-auditing#use-the-activity-log)

- [Registro de auditoría de Power BI](https://docs.microsoft.com/power-bi/admin/service-admin-auditing#use-the-audit-log)

**Supervisión de Azure Security Center**: No aplicable

**Responsabilidad**: Compartido

### <a name="lt-5-centralize-security-log-management-and-analysis"></a>LT-5: Centralizar la administración y el análisis de los registros de seguridad

**Instrucciones**: Power BI centraliza los registros en dos lugares: el registro de actividad de Power BI y el registro de auditoría unificado. Estos registros contienen una copia completa de los datos de auditoría de Power BI, pero hay varias diferencias clave, como se resume a continuación.
 

Registro de auditoría unificado:

- Incluye eventos de SharePoint Online, Exchange Online, Dynamics 365 y otros servicios además de los eventos de auditoría de Power BI.

- Solo tienen acceso, como administradores globales y auditores, los usuarios con permisos Registros de auditoría o Registros de auditoría de solo lectura.

- Los administradores y auditores globales pueden buscar en el registro de auditoría unificado mediante el Centro de seguridad de Microsoft 365 y el Centro de cumplimiento de Microsoft 365.

- Los administradores y auditores globales pueden descargar entradas del registro de auditoría mediante los cmdlets y las API de administración de Microsoft 365.

- Mantiene los datos de auditoría durante 90 días.

- Conserva los datos de auditoría, incluso si el inquilino se mueve a otra región de Azure.

 

Registro de actividad de Power BI:

- Solo incluye los eventos de auditoría de Power BI.

- Los administradores globales y los administradores del servicio Power BI tienen acceso.

- Todavía no hay ninguna interfaz de usuario para buscar en el registro de actividad.

- Los administradores globales y los administradores del servicio Power BI pueden descargar entradas del registro de actividad mediante una API REST de Power BI y un cmdlet de administración.

- Mantiene los datos de actividad durante 30 días.

- No conserva los datos de actividad cuando el inquilino se mueve a otra región de Azure.

- [Datos de auditoría de Power BI](https://docs.microsoft.com/power-bi/admin/service-admin-auditing#operations-available-in-the-audit-and-activity-logs)

- [Registro de actividad de Power BI](https://docs.microsoft.com/power-bi/admin/service-admin-auditing#use-the-activity-log)

- [Registro de auditoría de Power BI](https://docs.microsoft.com/power-bi/admin/service-admin-auditing#use-the-audit-log)

**Supervisión de Azure Security Center**: No aplicable

**Responsabilidad**: Customer

### <a name="lt-6-configure-log-storage-retention"></a>LT-6: Configuración de la retención del almacenamiento de registros

**Instrucciones**: Configure las directivas de retención de almacenamiento para los registros de auditoría de Office según los requisitos empresariales y de cumplimiento normativo.

- [Directivas de retención del registro de auditoría de Office](https://docs.microsoft.com/microsoft-365/compliance/audit-log-retention-policies)

**Supervisión de Azure Security Center**: No aplicable

**Responsabilidad**: Customer

## <a name="incident-response"></a>Respuesta a los incidentes

*Para más información, consulte [Azure Security Benchmark: respuesta ante incidentes](/azure/security/benchmarks/security-controls-v2-incident-response).*

### <a name="ir-1-preparation--update-incident-response-process-for-azure"></a>IR-1: Preparación: actualización del proceso de respuesta a incidentes para Azure

**Guía**: Asegúrese de que la organización tenga procesos para responder a incidentes de seguridad, que haya actualizado estos procesos para Azure y que los ejercite regularmente para garantizar su disponibilidad.

- [Implementación de la seguridad en todo el entorno empresarial](https://docs.microsoft.com/azure/cloud-adoption-framework/security/security-top-10#4-process-update-incident-response-ir-processes-for-cloud)

- [Guía de referencia de respuesta a incidentes](https://docs.microsoft.com/microsoft-365/downloads/IR-Reference-Guide.pdf)

**Supervisión de Azure Security Center**: No aplicable

**Responsabilidad**: Customer

### <a name="ir-2-preparation--setup-incident-notification"></a>IR-2: Preparación: notificación de incidentes de configuración

**Guía**: Configure la información de contacto en caso de incidentes de seguridad en Azure Security Center. Microsoft utilizará esta información para ponerse en contacto con usted si el Centro de respuestas de seguridad de Microsoft (MSRC) detecta que un tercero no autorizado o ilegal ha accedido a sus datos. También hay opciones para personalizar la alerta y notificación de incidentes en diferentes servicios de Azure en función de sus necesidades de respuesta a incidentes. 

- [Establecimiento del contacto de seguridad de Azure Security Center](https://docs.microsoft.com/azure/security-center/security-center-provide-security-contact-details)

**Supervisión de Azure Security Center**: No aplicable

**Responsabilidad**: Customer

### <a name="ir-3-detection-and-analysis--create-incidents-based-on-high-quality-alerts"></a>IR-3: Detección y análisis: creación de incidentes en función de alertas de alta calidad

**Instrucciones**: Asegúrese de que tiene un proceso para crear alertas de alta calidad y medir la calidad de las alertas. Esto le permite aprender de incidentes anteriores y clasificar las alertas para los analistas, de modo que no pierdan tiempo con falsos positivos.

Supervise las alertas relacionadas con Power BI en Microsoft Cloud App Security. Las alertas de alta calidad se pueden crear en función de la experiencia de incidentes anteriores, orígenes de la comunidad validados y herramientas diseñadas para generar y limpiar las alertas mediante la fusión y la correlación de diversos orígenes de la señal.

- [Supervisión de alertas en Cloud App Security](https://docs.microsoft.com/cloud-app-security/monitor-alerts)

**Supervisión de Azure Security Center**: No aplicable

**Responsabilidad**: Customer

### <a name="ir-4-detection-and-analysis--investigate-an-incident"></a>IR-4: Detección y análisis: investigación de incidentes

**Instrucciones**: Cree una guía de respuesta a incidentes para su organización. Realice ejercicios para probar las capacidades de respuesta a los incidentes de los sistemas con regularidad. Identifique puntos débiles y brechas y revise el plan según sea necesario.

Asegúrese de que haya planes de respuesta a incidentes escritos que definan todos los roles del personal, así como las fases de administración y gestión de los incidentes, desde la detección hasta la revisión posterior a la incidencia.

- [Información general sobre incidentes en Protección contra amenazas de Microsoft](https://docs.microsoft.com/microsoft-365/security/mtp/incidents-overview)

**Supervisión de Azure Security Center**: No aplicable

**Responsabilidad**: Customer

### <a name="ir-5-detection-and-analysis--prioritize-incidents"></a>IR-5: Detección y análisis: clasificar incidentes

**Guía**: Proporcione contexto a los analistas sobre los incidentes en los que deberán centrarse en primer lugar en función de la gravedad de la alerta y la confidencialidad de los recursos. 

 
Protección contra amenazas de Microsoft aplica el análisis de correlación y agrega todas las alertas y las investigaciones relacionadas de distintos productos a un solo incidente. Protección contra amenazas de Microsoft también desencadena alertas únicas sobre actividades que solo se pueden identificar como malintencionadas dada la visibilidad de un extremo a otro de Protección contra amenazas de Microsoft sobre todo el conjunto de productos. De esta forma, Protección contra amenazas de Microsoft narra una historia de ataques más amplia, lo que permite a un analista de operaciones de seguridad comprender y solucionar amenazas complejas en toda la organización.

- [Prioridad de los incidentes en Protección contra amenazas de Microsoft](https://docs.microsoft.com/microsoft-365/security/mtp/incident-queue?view=o365-worldwide&amp;preserve-view=true)

**Supervisión de Azure Security Center**: No aplicable

**Responsabilidad**: Customer

### <a name="ir-6-containment-eradication-and-recovery--automate-the-incident-handling"></a>IR-6: Contención, erradicación y recuperación: automatización del control de incidentes

**Guía**: Automatice las tareas repetitivas manuales para acelerar el tiempo de respuesta y reducir la carga de los analistas. Las tareas manuales tardan más tiempo en ejecutarse, lo que ralentiza cada incidente y reduce el número de incidentes que un analista puede manejar. Las tareas manuales también aumentan la fatiga del analista, lo que aumenta el riesgo del error humano que produce retrasos y reduce la capacidad de los analistas de centrarse de manera efectiva en tareas complejas.  
 
Use las características de automatización de flujos de trabajo de Protección contra amenazas de Microsoft para desencadenar automáticamente investigaciones y correcciones en respuesta a las alertas de seguridad entrantes. 
 
- [Investigación y respuesta automatizadas en Protección contra amenazas de Microsoft](https://docs.microsoft.com/microsoft-365/security/mtp/mtp-autoir)

**Supervisión de Azure Security Center**: No aplicable

**Responsabilidad**: Customer

## <a name="posture-and-vulnerability-management"></a>administración de posturas y vulnerabilidades

*Para más información, consulte [Azure Security Benchmark: administración de posturas y vulnerabilidades](/azure/security/benchmarks/security-controls-v2-vulnerability-management).*

### <a name="pv-1-establish-secure-configurations-for-azure-services"></a>PV-1: establecimiento de configuraciones seguras para servicios de Azure 

**Instrucciones**: Configure el servicio Power BI con los valores adecuados para la organización y el estado de seguridad. Se deben tener en cuenta detenidamente las opciones de acceso para el servicio y el contenido, así como la seguridad de la aplicación y el área de trabajo. Vea Seguridad y protección de datos de Power BI en las notas del producto sobre la implementación de Power BI Enterprise.

- [Notas del producto sobre la implementación de Enterprise](https://aka.ms/PBIEnterpriseDeploymentWP)

**Supervisión de Azure Security Center**: No aplicable

**Responsabilidad**: Customer

### <a name="pv-2-sustain-secure-configurations-for-azure-services"></a>PV-2: sostenimiento de configuraciones seguras para servicios de Azure

**Instrucciones**: Supervise la instancia de Power BI mediante las API REST de administración de Power BI.

- [API REST de administración de Power BI](https://docs.microsoft.com/rest/api/power-bi/admin)

- [Notas del producto sobre la implementación de Power BI Enterprise](https://aka.ms/PBIEnterpriseDeploymentWP)

**Supervisión de Azure Security Center**: No aplicable

**Responsabilidad**: Customer

### <a name="pv-8-conduct-regular-attack-simulation"></a>PV-8: realización de una simulaciones de ataques periódicas

**Guía**: Según sea necesario, realice pruebas de penetración o actividades de equipo rojo en los recursos de Azure y asegúrese de corregir todos los resultados de seguridad críticos.

siga las reglas de compromiso de la prueba de penetración de Microsoft Cloud para asegurarse de que las pruebas de penetración no infrinjan las directivas de Microsoft. Use la estrategia de Microsoft y la ejecución de las pruebas de penetración del equipo rojo y sitios activos en la infraestructura de nube, los servicios y las aplicaciones administradas por Microsoft.

- [Pruebas de penetración en Azure](https://docs.microsoft.com/azure/security/fundamentals/pen-testing)

- [Reglas de interacción de las pruebas de penetración](https://www.microsoft.com/msrc/pentest-rules-of-engagement?rtc=1)

- [Equipo rojo de Microsoft Cloud](https://gallery.technet.microsoft.com/Cloud-Red-Teaming-b837392e)

**Supervisión de Azure Security Center**: No aplicable

**Responsabilidad**: Compartido

## <a name="backup-and-recovery"></a>Copia de seguridad y recuperación

*Para obtener más información, vea [Azure Security Benchmark: Copia de seguridad y recuperación](/azure/security/benchmarks/security-controls-v2-backup-recovery).*

### <a name="br-3-validate-all-backups-including-customer-managed-keys"></a>BR-3: Validación de todas las copias de seguridad, incluidas las claves administradas por el cliente

**Instrucciones**: Si usa la característica Bring Your Own Key (BYOK) en Power BI, tendrá que validar periódicamente que puede acceder a las claves administradas por el cliente y restaurarlas.

- [BYOK en Power BI](https://docs.microsoft.com/power-bi/admin/service-encryption-byok)

**Supervisión de Azure Security Center**: No aplicable

**Responsabilidad**: Customer

### <a name="br-4-mitigate-risk-of-lost-keys"></a>BR-4: Mitigación del riesgo de pérdida de claves

**Instrucciones**: Si usa la característica Bring Your Own Key (BYOK) en Power BI, debe asegurarse de que el almacén de claves que controla las claves administradas por el cliente está configurado con las instrucciones de BYOK en la documentación de Power BI siguiente. Habilite la eliminación temporal y la protección de purga de Azure Key Vault para proteger las claves frente a una eliminación accidental o malintencionada.

- [BYOK en Power BI](https://docs.microsoft.com/power-bi/admin/service-encryption-byok)

- [Procedimiento para habilitar la eliminación temporal y la protección de purga en Key Vault](https://docs.microsoft.com/azure/storage/blobs/storage-blob-soft-delete?tabs=azure-portal)

Para los recursos de clave de puerta de enlace, asegúrese de seguir las instrucciones de la siguiente documentación sobre claves de recuperación de puerta de enlace.

- [Clave de recuperación de puerta de enlace de datos local](https://docs.microsoft.com/data-integration/gateway/service-gateway-recovery-key)

**Supervisión de Azure Security Center**: No aplicable

**Responsabilidad**: Customer

## <a name="governance-and-strategy"></a>Gobernanza y estrategia

*Para más información, consulte [Azure Security Benchmark: gobernanza y estrategia](/azure/security/benchmarks/security-controls-v2-governance-strategy).*

### <a name="gs-1-define-asset-management-and-data-protection-strategy"></a>GS-1: Definición de la estrategia de protección de datos y administración de recursos 

**Guía**: Asegúrese de documentar y comunicar una estrategia clara para la protección y supervisión continua de sistemas y datos. Dé prioridad a la detección, evaluación, protección y supervisión de los sistemas y datos críticos para la empresa. 

Esta estrategia debe incluir instrucciones, directivas y estándares documentados para los siguientes elementos: 

-   Norma de clasificación de datos de acuerdo con los riesgos empresariales

-   Visibilidad en la organización de seguridad de los riesgos y el inventario de recursos 

-   Aprobación de la organización de seguridad de los servicios de Azure para su uso 

-   Seguridad de los recursos durante su ciclo de vida

-   Estrategia de control de acceso necesaria según la clasificación de datos de la organización

-   Uso de funciones de protección de datos nativa de Azure y de terceros

-   Requisitos de cifrado de datos para casos de uso en tránsito y en reposo

-   Normas criptográficas adecuadas

Para más información, consulte las siguientes referencias:
- [Recomendación para la arquitectura de seguridad de Azure: almacenamiento, datos y cifrado](https://docs.microsoft.com/azure/architecture/framework/security/storage-data-encryption?toc=/security/compass/toc.json&amp;bc=/security/compass/breadcrumb/toc.json)

- [Aspectos básicos de la seguridad de Azure: seguridad, cifrado y almacenamiento de datos de Azure](https://docs.microsoft.com/azure/security/fundamentals/encryption-overview)

- [Cloud Adoption Framework: procedimientos recomendados de cifrado y seguridad de los datos de Azure](https://docs.microsoft.com/azure/security/fundamentals/data-encryption-best-practices?toc=/azure/cloud-adoption-framework/toc.json&amp;bc=/azure/cloud-adoption-framework/_bread/toc.json)

- [Azure Security Benchmark: administración de recursos](https://docs.microsoft.com/azure/security/benchmarks/security-benchmark-v2-asset-management)

- [Azure Security Benchmark: protección de datos](https://docs.microsoft.com/azure/security/benchmarks/security-benchmark-v2-data-protection)

**Supervisión de Azure Security Center**: No aplicable

**Responsabilidad**: Customer

### <a name="gs-2-define-enterprise-segmentation-strategy"></a>GS-2: Definición de una estrategia de segmentación empresarial 

**Guía**: Establezca en toda la empresa una estrategia para segmentar el acceso a los recursos mediante una combinación de identidad, red, aplicación, suscripción, grupo de administración y otros controles.

Equilibre concienzudamente la necesidad de separación de seguridad con la necesidad de habilitar el funcionamiento diario de los sistemas que necesitan comunicarse entre sí y acceder a los datos.

Asegúrese de que la estrategia de segmentación se implementa de forma coherente en todos los tipos de control, como la seguridad de red, los modelos de identidad y acceso, y los modelos de acceso y permisos de las aplicaciones, y los controles de los procesos humanos.

- [Guía de la estrategia de segmentación en Azure (vídeo)](https://docs.microsoft.com/security/compass/microsoft-security-compass-introduction#azure-components-and-reference-model-2151)

- [Guía de la estrategia de segmentación en Azure (documento)](https://docs.microsoft.com/security/compass/governance#enterprise-segmentation-strategy)

- [Alineación de la segmentación de red con la estrategia de segmentación empresarial](https://docs.microsoft.com/security/compass/network-security-containment#align-network-segmentation-with-enterprise-segmentation-strategy)

**Supervisión de Azure Security Center**: No aplicable

**Responsabilidad**: Customer

### <a name="gs-3-define-security-posture-management-strategy"></a>GS-3: Definición de la estrategia de administración de la posición de seguridad

**Guía**: Mida y mitigue continuamente los riesgos de los recursos individuales y el entorno en el que se hospedan. Dé prioridad a los recursos de gran valor y a las superficies de ataque muy expuestas, como las aplicaciones publicadas, los puntos de entrada y salida de red, los puntos de conexión de usuario y administrador, etc.

- [Azure Security Benchmark: administración de posturas y vulnerabilidades](https://docs.microsoft.com/azure/security/benchmarks/security-benchmark-v2-posture-vulnerability-management)

**Supervisión de Azure Security Center**: No aplicable

**Responsabilidad**: Customer

### <a name="gs-4-align-organization-roles-responsibilities-and-accountabilities"></a>GS-4: Alineación de los roles y responsabilidades de la organización

**Guía**: Asegúrese de documentar y comunicar una estrategia clara para los roles y las responsabilidades de la organización de seguridad. Dé prioridad a ofrecer una responsabilidad clara en las decisiones de seguridad, a proporcionar a todos los usuarios formación sobre el modelo de responsabilidad compartida y a los equipos técnicos sobre la tecnología para proteger la nube.

- [Procedimiento recomendado de seguridad de Azure 1. Personas: Formación del equipo sobre el recorrido de seguridad de la nube](https://docs.microsoft.com/azure/cloud-adoption-framework/security/security-top-10#1-people-educate-teams-about-the-cloud-security-journey)

- [Procedimiento recomendado de seguridad de Azure 2. Personas: Formación del equipo en tecnología de seguridad de la nube](https://docs.microsoft.com/azure/cloud-adoption-framework/security/security-top-10#2-people-educate-teams-on-cloud-security-technology)

- [Procedimiento recomendado de seguridad de Azure 3. Proceso: Asignación de responsabilidades por las decisiones de seguridad en la nube](https://docs.microsoft.com/azure/cloud-adoption-framework/security/security-top-10#4-process-update-incident-response-ir-processes-for-cloud)

**Supervisión de Azure Security Center**: No aplicable

**Responsabilidad**: Customer

### <a name="gs-5-define-network-security-strategy"></a>GS-5: Definición de la estrategia de seguridad de red

**Guía**: Establezca un enfoque de seguridad de red de Azure como parte de la estrategia de control de acceso de seguridad general de su organización.  

Esta estrategia debe incluir instrucciones, directivas y estándares documentados para los siguientes elementos: 

-   Centralización de la responsabilidad de seguridad y la administración de redes

-   Modelo de segmentación de la red virtual alineado con la estrategia de segmentación empresarial

-   Estrategia de corrección en diferentes escenarios de amenazas y ataques

-   Estrategia de entrada y salida y perimetral de Internet

-   Estrategia de interconectividad entre el entorno local y la nube híbrida

-   Artefactos de seguridad de red actualizados (por ejemplo, diagramas de red y arquitectura de red de referencia)

Para más información, consulte las siguientes referencias:
- [Procedimiento recomendado de seguridad de Azure 11. Arquitectura: Establecimiento de una estrategia de seguridad unificada](https://docs.microsoft.com/azure/cloud-adoption-framework/security/security-top-10#11-architecture-establish-a-single-unified-security-strategy)

- [Azure Security Benchmark: seguridad de red](https://docs.microsoft.com/azure/security/benchmarks/security-benchmark-v2-network-security)

- [Azure Network Security Overview (Información general sobre Azure Network Security)](https://docs.microsoft.com/azure/security/fundamentals/network-overview)

- [Estrategia para la arquitectura de red empresarial](https://docs.microsoft.com/azure/cloud-adoption-framework/ready/enterprise-scale/architecture)

**Supervisión de Azure Security Center**: No aplicable

**Responsabilidad**: Customer

### <a name="gs-6-define-identity-and-privileged-access-strategy"></a>GS-6: Definición de la estrategia de acceso con privilegios e identidades

**Guía**: Establezca una identidad de Azure y enfoques de acceso con privilegios como parte de la estrategia de control de acceso de seguridad general de su organización.  

Esta estrategia debe incluir instrucciones, directivas y estándares documentados para los siguientes elementos: 

-   Un sistema de identidad y autenticación centralizado y su interconectividad con otros sistemas de identidad internos y externos

-   Métodos de autenticación sólida en diferentes casos de uso y condiciones

-   Protección de usuarios con privilegios elevados

-   Supervisión y control de anomalías en las actividades de los usuarios  

-   Proceso de revisión y conciliación del acceso y la identidad de los usuarios

Para más información, consulte las siguientes referencias:

- [Azure Security Benchmark: administración de identidades](https://docs.microsoft.com/azure/security/benchmarks/security-benchmark-v2-identity-management)

- [Azure Security Benchmark: acceso con privilegios](https://docs.microsoft.com/azure/security/benchmarks/security-benchmark-v2-privileged-access)

- [Procedimiento recomendado de seguridad de Azure 11. Arquitectura: Establecimiento de una estrategia de seguridad unificada](https://docs.microsoft.com/azure/cloud-adoption-framework/security/security-top-10#11-architecture-establish-a-single-unified-security-strategy)

- [Información general sobre seguridad de administración de identidades de Azure](https://docs.microsoft.com/azure/security/fundamentals/identity-management-overview)

**Supervisión de Azure Security Center**: No aplicable

**Responsabilidad**: Customer

### <a name="gs-7-define-logging-and-threat-response-strategy"></a>GS-7: Definición de la estrategia de registro y respuesta a amenazas

**Guía**: Establezca una estrategia de registro y respuesta a amenazas para detectar y corregir rápidamente las amenazas mientras cumple los requisitos de cumplimiento. Para dar prioridad, proporcione a los analistas alertas de alta calidad y experiencias sin problemas para que puedan centrarse en las amenazas en lugar de los pasos manuales y de integración. 

Esta estrategia debe incluir instrucciones, directivas y estándares documentados para los siguientes elementos: 

-   Las responsabilidades y el rol de la organización en las operaciones de seguridad (SecOps) 

-   Un proceso de respuesta a incidentes bien definido que esté alineado con NIST u otro marco del sector. 

-   Captura y retención de registros para admitir la detección de amenazas, la respuesta ante incidentes y las necesidades de cumplimiento

-   Visibilidad y correlación centralizada de la información sobre amenazas, mediante SIEM, funcionalidades nativas de Azure y otros orígenes 

-   Plan de comunicación y notificación con sus clientes, proveedores y entidades públicas de interés

-   Uso de plataformas nativas de Azure y de terceros para el tratamiento de incidentes, como el registro y la detección de amenazas, los análisis forenses y la corrección y erradicación de ataques

-   Procesos para controlar incidentes y actividades posteriores a incidentes, como las lecciones aprendidas y la retención de pruebas

Para más información, consulte las siguientes referencias:

- [Azure Security Benchmark: registro y detección de amenazas](https://docs.microsoft.com/azure/security/benchmarks/security-benchmark-v2-logging-threat-detection)

- [Azure Security Benchmark: respuesta a incidentes](https://docs.microsoft.com/azure/security/benchmarks/security-benchmark-v2-incident-response)

- [Procedimiento recomendado de seguridad de Azure 4. Proceso: Actualización de los procesos de respuesta a incidentes para la nube](https://docs.microsoft.com/azure/cloud-adoption-framework/security/security-top-10#4-process-update-incident-response-ir-processes-for-cloud)

- [Guía de decisiones sobre registros e informes en Azure Adoption Framework](https://docs.microsoft.com/azure/cloud-adoption-framework/decision-guides/logging-and-reporting/)

- [Escala, administración y supervisión empresarial de Azure](https://docs.microsoft.com/azure/cloud-adoption-framework/ready/enterprise-scale/management-and-monitoring)

**Supervisión de Azure Security Center**: No aplicable

**Responsabilidad**: Customer

## <a name="next-steps"></a>Pasos siguientes

- Consulte la [Información general sobre Azure Security Benchmark V2](/azure/security/benchmarks/overview).
- Obtenga más información sobre las [líneas de base de seguridad de Azure](/azure/security/benchmarks/security-baselines-overview).
