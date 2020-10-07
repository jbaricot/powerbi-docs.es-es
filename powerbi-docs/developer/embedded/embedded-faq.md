---
title: Preguntas más frecuentes acerca de Power BI Embedded
description: Examinar una lista de las preguntas más frecuentes, y sus respuestas, acerca de Power BI Embedded.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 02/11/2020
ms.openlocfilehash: 86ac6bebf6373f14ac343721a8594ee9f45b0e89
ms.sourcegitcommit: 6bc66f9c0fac132e004d096cfdcc191a04549683
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/06/2020
ms.locfileid: "91746203"
---
# <a name="frequently-asked-questions-about-power-bi-embedded"></a>Preguntas más frecuentes acerca de Power BI Embedded

* Si tiene otras preguntas, [pruebe a preguntar a la comunidad de Power BI](https://community.powerbi.com/).
* ¿Sigue teniendo problemas? Visite la [página de soporte técnico de Power BI](https://powerbi.microsoft.com/support/).

## <a name="general"></a>General

### <a name="what-is-power-bi-embedded"></a>¿Qué es Power BI Embedded?

[Microsoft Power BI Embedded (PBIE)](azure-pbie-what-is-power-bi-embedded.md) permite a los desarrolladores de aplicaciones insertar sorprendentes informes totalmente interactivos en sus aplicaciones sin tener que crear sus propias visualizaciones de datos y controles desde cero.

### <a name="who-is-the-target-audience-for-power-bi-embedded"></a>¿Quién es la público objetivo de Power BI Embedded?

Los desarrolladores y las empresas de software que crean sus aplicaciones, y a los que también se conoce como fabricantes de software independientes (ISV).

### <a name="how-is-power-bi-embedded-different-from-power-bi-the-service"></a>¿En qué se diferencian Power BI Embedded del servicio Power BI?

Power BI es una solución de análisis de software como servicio que proporciona a las organizaciones una única vista de sus datos empresariales más importantes.

Microsoft desarrolló Power BI Embedded para los ISV que desean insertar objetos visuales en sus aplicaciones para ayudar a sus clientes a tomar decisiones de análisis. Esto ahorra a los ISV tener que crear una solución de análisis propia. El [análisis integrado](embedding.md) permite a los usuarios empresariales acceder a los datos empresariales y ejecutar consultas para generar información desde la aplicación.


### <a name="what-is-the-difference-between-power-bi-premium-and-power-bi-embedded"></a>¿En qué se diferencian Power BI Premium y Power BI Embedded?

La capacidad de Power BI Premium está dirigida a empresas que quieran una solución de inteligencia empresarial completa que proporcione una vista única de su organización, asociados, clientes y proveedores. Power BI Premium ayuda a las organizaciones a tomar decisiones. Power BI Premium es un producto SaaS que permite que los usuarios consuman el contenido a través del portal de Power BI, una aplicación móvil y aplicaciones desarrolladas internamente.

Power BI Embedded es para aquellos ISV que desean insertar objetos visuales en sus aplicaciones. Power BI Embedded ayuda a los clientes tomar decisiones. Dado que Power BI Embedded es para desarrolladores de aplicaciones, los clientes de la aplicación pueden consumir contenido almacenado en la capacidad de Power BI Embedded, incluidos todos los usuarios de dentro o fuera de la organización. El contenido de la capacidad de Power BI Embedded no se puede compartir mediante la publicación Web o con un solo clic en SharePoint.

### <a name="what-is-the-microsoft-recommendation-for-when-a-customer-should-buy-power-bi-premium-vs-power-bi-embedded"></a>¿A quiénes recomienda Microsoft comprar Power BI Premium y a quiénes Power BI Embedded?

Microsoft recomienda que las empresas compren Power BI Premium, una solución de inteligencia empresarial en la nube y de autoservicio. Se recomienda que los ISV compren Power BI Embedded para sus componentes de análisis insertados con tecnología de nube. Sin embargo, los clientes pueden comprar el producto que deseen.

Puede haber algunos casos en los que un ISV (normalmente grande) desee utilizar una SKU P para lograr las ventajas adicionales del servicio Power BI preempaquetado en su organización, así como para insertarlo en sus aplicaciones. Es posible que algunas empresas decidan usar SKU A en Azure si solo les interesa la línea de creación de aplicaciones empresariales e inserción de análisis en ellas, pero no les interesa usar el servicio Power BI ya empaquetado.

### <a name="how-many-embed-tokens-can-i-create"></a>¿Cuántos tokens de inserción puedo crear?

Los tokens de inserción con licencia PRO están pensados para pruebas de desarrollo, de modo que el número de tokens de inserción que puede generar una cuenta maestra o una [entidad de servicio](embed-service-principal.md) de Power BI es limitado. Para realizar inserciones en un entorno de producción, [compre una capacidad](#technical). No hay ningún límite en la cantidad de tokens de inserción que se pueden generar cuando se compra una capacidad. Vaya a [Available Features](/rest/api/power-bi/availablefeatures) (Características disponibles) para comprobar el valor de uso que indica el porcentaje de uso actual de Power BI Embedded.

## <a name="technical"></a>Preguntas técnicas

### <a name="where-can-i-learn-more-about-capacity-and-skus-in-power-bi-embedded-analytics"></a>¿Dónde puedo obtener más información sobre la capacidad y los SKU relativos a los análisis incrustados de Power BI?

Consulte el artículo [Capacidad y SKU de los análisis incrustados de Power BI](embedded-capacity.md).

### <a name="what-are-the-prerequisites-for-creating-a-pbie-capacity-in-azure"></a>¿Cuáles son los requisitos previos para crear una capacidad PBIE en Azure?

* Inicie sesión en el directorio de la organización (no se admiten cuentas de Microsoft).
* Debe tener un inquilino de Power BI; es decir, al menos un usuario en su directorio debe estar registrado en Power BI. 
* Debe tener una suscripción a Azure en el directorio de su organización.

### <a name="how-can-i-monitor-power-bi-embedded-capacity-consumption"></a>¿Cómo puedo supervisar el uso de funcionalidad de Power BI Embedded?

* Con el [portal de administración de Power BI](../../admin/service-admin-portal.md#power-bi-embedded).

* Mediante la descarga de la [aplicación de métricas](../../admin/service-admin-premium-monitor-capacity.md) de Power BI.

* Con los [registros de diagnóstico de Azure](azure-pbie-diag-logs.md).

### <a name="can-my-capacity-scale-automatically-to-adjust-to-my-app-consumption"></a>¿Mi capacidad se puede escalar de forma automática para ajustarse al consumo de mi aplicación?

Aunque en la actualidad no hay escalado automático, todas las API están disponibles para escalarlas en cualquier momento.

### <a name="why-creatingscalingresuming-a-capacity-results-in-putting-the-capacity-into-a-suspended-state"></a>¿Por qué al crear, escalar o reanudar una capacidad, esta pasa a un estado suspendido?

El aprovisionamiento de una capacidad (escalado/reanudación/creación) puede generar errores. Puede usar la API de obtención de detalles para comprobar el estado de aprovisionamiento de una capacidad: [Capacities - Get Details](/rest/api/power-bi-embedded/capacities/getdetails) (Capacidades: Obtener detalles).

### <a name="can-i-only-create-power-bi-embedded-capacities-in-a-specific-region"></a>¿Puedo crear solo las capacidades de Power BI Embedded en una región específica?

Con la característica [Multi-Geo (versión preliminar)](embedded-multi-geo.md), puede adquirir una [capacidad de Power BI Embedded](azure-pbie-create-capacity.md) en una región distinta de la ubicación del inquilino principal de Power BI.

### <a name="why-cant-i-see-a-workspace-although-i-have-permissions"></a>¿Por qué no puedo ver un área de trabajo aunque tengo los permisos?

Cuando a un usuario se le conceden permisos en un área de trabajo, aplicación o artefacto, puede que no estén disponibles inmediatamente a través de llamadas de API.
El resultado puede ser un artefacto que faltan en una respuesta de la API 'GET' o un error al intentar usar el artefacto.
El usuario puede resolver este problema mediante una llamada a la [API refreshUserPermissions](/rest/api/power-bi/users/refreshuserpermissions), que actualiza los permisos de usuario.


### <a name="how-can-i-find-my-pbi-tenant-region"></a>¿Cómo puedo averiguar cuál es mi región de inquilino de PBI?

Puede usar el portal de PBI para saber cuál es la región de su inquilino de PBI.

`https://app.powerbi.com/` > ? > Acerca de Power BI

![Acerca de Power BI](media/embedded-faq/about-01.png)
![Región del inquilino](media/embedded-faq/tenant-location-01.png)

### <a name="what-does-the-cloud-solution-provider-csp-channel-support"></a>¿Qué admite el canal Proveedor de soluciones en la nube (CSP)?

* Puede crear PBIE en su inquilino con el tipo de suscripción de CSP.
* La cuenta de asociado puede iniciar sesión en el inquilino del cliente y adquirir PBIE para dicho inquilino especificando el usuario del inquilino de cliente como administrador de capacidad de Power BI.

### <a name="why-do-i-get-an-unsupported-account-message"></a>¿Por qué aparece un mensaje de cuenta no compatible?

Power BI requiere que se registre con una cuenta de la organización. No se admite el intento de registrarse en Power BI con una cuenta Microsoft.

### <a name="can-i-use-apis-to-create-and-manage-azure-capacities"></a>¿Puedo usar API para crear y administrar las capacidades de Azure?

Sí, hay cmdlets de Powershell y de las API REST de Azure Resource Manager que puede usar para crear y administrar recursos de PBIE.

* [API REST](/rest/api/power-bi-embedded/) 
* [Cmdlets de PowerShell](/powershell/module/azurerm.powerbiembedded/)

### <a name="what-is-the-pbi-embedded-dedicated-capacity-role-in-a-pbi-embedded-solution"></a>¿Qué es el rol de capacidad dedicada de PBI Embedded en una solución de PBI Embedded?

Para [promover la solución a producción](embed-sample-for-customers.md#move-to-production), es necesario asignar el contenido de Power BI (área de trabajo) que usa la aplicación a una capacidad de Power BI Embedded (SKU tipo A).

### <a name="in-what-azure-regions-is-pbi-embedded-available"></a>¿En qué regiones de Azure está disponible PBI Embedded?

[PAM](https://ecosystemmanager.azurewebsites.net/home) (EcoManager). Consulte el administrador de disponibilidad de productos.

16 regiones disponibles (las mismas que Power BI)

* EE. UU. (6): Este de EE. UU., Este de EE. UU. 2, Centro y norte de EE. UU., Centro y sur de EE. UU., Oeste de EE. UU., Oeste de EE. UU. 2
* Europa (2): Norte de Europa, Oeste de Europa
* Asia Pacífico (2): Sudeste de Asia, Este de Asia
* Brasil (1): Sur de Brasil
* Japón (1): Japón Oriental
* Australia (1): Sudeste de Australia
* India (1): Oeste de la India
* Canadá (1): Centro de Canadá
* Reino Unido (1): Sur de Reino Unido

### <a name="what-is-power-bi-embeddeds-authentication-model"></a>¿Qué es el modelo de autenticación de Power BI Embedded?

En Power BI Embedded se sigue usando Azure AD para la autenticación del usuario maestro (un usuario con licencia de Power BI Pro designado), o bien con la [entidad de servicio](embed-service-principal.md) para autenticar la aplicación dentro de Power BI.  

 Un ISV puede implementar su propia autenticación y autorización para sus aplicaciones.

Puede usar el directorio existente si ya tiene un inquilino de Azure AD. También puede crear un nuevo inquilino de Azure AD para la seguridad del contenido de aplicación insertado.

Para obtener un token de AAD, puede usar una de las [bibliotecas de autenticación de Azure Active Directory](/azure/active-directory/develop/active-directory-authentication-libraries). Existen bibliotecas de cliente para varias plataformas.

### <a name="my-application-already-uses-aad-for-user-authentication-how-can-we-use-this-identity-when-authenticating-to-power-bi-in-a-user-owns-data-scenario"></a>Mi aplicación ya usa AAD para la autenticación de usuario. ¿Cómo se puede usar esta identidad al autenticarse en Power BI en un escenario en el que el usuario posee los datos?

Es el flujo típico en nombre de otra persona de OAuth (<https://docs.microsoft.com/azure/active-directory/develop/web-api>). Debe configurar la aplicación para requerir permisos al servicio Power BI (con los ámbitos correspondientes). Una vez que tenga un token de usuario en la aplicación, solo tiene que llamar al método AcquireTokenAsync de API de ADAL usando ese token de acceso de usuario y especificar la dirección URL del recurso de Power BI como identificador de recurso:

```csharp
var context = new AD.AuthenticationContext(authorityUrl);
var userAssertion = new AD.UserAssertion(userAccessToken);
var clientAssertion = new AD.ClientAssertionCertificate(MyAppId, MyAppCertificate)
var authenticationResult = await context.AcquireTokenAsync(resourceId, clientAssertion, userAssertion);
```

### <a name="what-object-id-is-the-service-principal-object-id"></a>¿Cuál es el identificador de objeto de la entidad de servicio?

El *Id. de objeto* de la pantalla principal de una aplicación registrada es el identificador de objeto de la aplicación.

El identificador de objeto que se encuentra en la sección *Aplicación administrada en directorio local > Propiedades* es el identificador de objeto de entidad de servicio que debe usar. Este identificador de objeto se utiliza para hacer referencia a una entidad de servicio en las operaciones, o para realizar cambios en el identificador de objeto de la entidad de servicio, por ejemplo, aplicar una entidad de servicio como administrador a un área de trabajo

### <a name="how-is-power-bi-embedded-different-from-other-azure-services"></a>¿En qué se diferencia Power BI Embedded de otros servicios de Azure?

Debe tener una cuenta de Power BI para poder comprar Power BI Embedded en Azure. La región de implementación de Power BI Embedded determina la cuenta de Power BI. Administre su recurso de Power BI Embedded en Azure para:

* Escalar y reducir verticalmente
* Agregar administradores de capacidad
* Pausar y reanudar el servicio

Utilice PowerBI.com para asignar o desasignar áreas de trabajo a su capacidad de Power BI Embedded.

### <a name="what-content-pack-data-types-can-you-embed"></a>¿Qué tipos de datos de paquete de contenido puede insertar?

*No puede* insertar **paneles** ni **iconos** creados a partir de conjuntos de datos de paquete de contenido. Sin embargo, *puede* insertar **informes** creados a partir de un conjunto de datos de paquete de contenido.

### <a name="what-is-the-difference-between-using-row-level-security-rls-vs-javascript-filters"></a>¿Cuál es la diferencia entre usar la seguridad de nivel de fila RLS y filtros de JavaScript?

Suele haber confusión a la hora de usar RLS frente a los filtros de JavaScript, ya que un método trata sobre cómo controlar lo que puede ver un usuario específico y el otro sobre la optimización de la vista del usuario.

En RLS, el desarrollador de ISV controla el filtrado de datos como parte de la creación del modelo y la generación de tokens de inserción. El usuario final ve solo lo que el ISV permite que vea el usuario. En este caso, el usuario puede elegir ver menos de lo que se filtra, pero no podrá omitir la configuración de RLS y ver más de lo que se permite.

Para el filtrado en el lado cliente (JavaScript), el ISV puede decidir lo que ve el usuario final en la vista inicial, pero no puede controlar los cambios que el usuario final podría aplicar a la propia vista. Puesto que el código de cliente de Javascript del usuario puede desencadenar el filtrado de datos en el back-end, no puede considerarse seguro.

Para más información, consulte [RLS frente a los filtros de JavaScript](embedded-row-level-security.md#using-rls-vs-javascript-filters).

### <a name="how-do-i-manage-permissions-for-service-principals-with-power-bi"></a>¿Cómo se administran los permisos para las entidades de servicio con Power BI?

Después de habilitar la [entidad de servicio](embed-service-principal.md) para usarla con Power BI, los permisos de AD de la aplicación ya no tendrán efecto. Los permisos de la aplicación se administrarán desde el portal de administración de Power BI.

Las entidades de servicio heredan de su grupo de seguridad los permisos correspondientes a todas las opciones de configuración del inquilino de Power BI. Para limitar los permisos, cree un grupo de seguridad dedicado para las entidades de servicio y agréguelo a la lista **Excepto grupos de seguridad específicos** correspondiente a la configuración habilitada y pertinente de Power BI.

Esto es importante cuando se agrega la entidad de servicio como un **administrador** a la nueva área de trabajo. Puede administrar esta tarea a través de las [API](/rest/api/power-bi/groups/addgroupuser) o con el servicio Power BI.

### <a name="when-to-use-an-application-id-vs-a-service-principal-object-id"></a>¿Cuándo se usa un identificador de aplicación frente a un identificador de objeto de entidad de servicio?

El **[identificador de aplicación](embed-sample-for-customers.md#application-id)** se usa para crear el token de acceso cuando se pasa el identificador de aplicación para la autenticación.

Para hacer referencia a una entidad de servicio para operaciones o realizar cambios, use el **[identificador de objeto de entidad de servicio](embed-service-principal.md)** ; por ejemplo, para aplicar una entidad de servicio como un administrador a un área de trabajo.

### <a name="can-you-manage-an-on-premises-data-gateway-with-service-principal"></a>¿Se puede administrar una puerta de enlace de datos local con la entidad de servicio?

No se puede administrar una puerta de enlace de datos local (puerta de enlace de datos) mediante la [entidad de servicio](embed-service-principal.md) como se hace con una cuenta maestra.

Con una cuenta maestra, puede instalar una puerta de enlace de datos, agregarle usuarios, conectarse a orígenes de datos y realizar otras tareas administrativas.

Con la entidad de servicio, puede configurar la [seguridad de nivel de fila (RLS)](embedded-row-level-security.md#on-premises-data-gateway-with-service-principal) mediante un origen de datos de conexión dinámica local de SQL Server Analysis Services (SSAS). De este modo puede administrar usuarios y su acceso a los datos de SSAS cuando se realiza la integración con **Power BI Embedded** mediante una entidad de servicio.

### <a name="can-you-sign-into-the-power-bi-service-with-service-principal"></a>¿Se puede iniciar sesión en el servicio Power BI con la entidad de servicio?

No, no se puede iniciar sesión en Power BI con la entidad de servicio.

Además, tampoco se puede consumir contenido como un usuario en las aplicaciones externas (insertadas como SaaS), solo cuando se genera un token de inserción.

### <a name="what-are-the-best-practices-to-improve-performance"></a>¿Cuáles son los procedimientos recomendados para mejorar el rendimiento?

[Procedimientos recomendados de rendimiento de Power BI Embedded](embedded-performance-best-practices.md)

## <a name="licensing"></a>Licencias

### <a name="how-do-i-purchase-power-bi-embedded"></a>¿Cómo se adquiere Power BI Embedded?

Power BI Embedded está disponible a través de Azure.

### <a name="what-happens-if-i-already-purchased-power-bi-premium-and-now-i-want-some-power-bi-embedded-in-azure-benefits"></a>¿Qué ocurre si ya he adquirido Power BI Premium y ahora deseo algunas de las ventajas de Power BI Embedded en Azure?

Los clientes siguen pagando todas las compras de Power BI Premium que realicen hasta el final del plazo de su contrato actual y, luego, pueden cambiar sus compras de Power BI Premium si fuera necesario.

### <a name="do-i-still-have-to-buy-power-bi-premium-to-get-access-to-power-bi-embedded"></a>¿Hay que comprar Power BI Premium para obtener acceso a Power BI Embedded?

No, Power BI Embedded incluye la capacidad basada en Azure que necesita para implementar y distribuir su solución a los clientes.

### <a name="whats-the-purchase-commitment-for-power-bi-embedded"></a>¿Cuál es el compromiso de compra de Power BI Embedded?

Los clientes pueden cambiar su uso cada hora. No hay compromiso mensual o anual para el servicio Power BI Embedded.

### <a name="how-does-the-usage-of-power-bi-embedded-show-up-on-my-bill"></a>¿Cómo se muestra el uso de Power BI Embedded en mi factura?

Power BI Embedded factura a un precio por hora predecible en función del tipo de nodos. Mientras el recurso esté activo, se le factura aunque no se use. Debe pausar el recurso para detener la facturación.

### <a name="who-needs-a-power-bi-pro-license-for-power-bi-embedded-and-why"></a>¿Quién necesita una licencia de Power BI Pro para Power BI Embedded y por qué?

Necesita una licencia de Power BI Pro o [entidad de servicio](embed-service-principal.md) para usar las API REST. Los analistas que necesiten agregar informes a un área de trabajo de Power BI deben tener una licencia de Power BI Pro o usar una entidad de servicio. Para administrar el inquilino y la capacidad de Power BI, se necesita una licencia de Power BI Pro.

Dado que Power BI Embedded permite el uso del portal de Power BI para administrar y validar contenido insertado, la licencia de Power BI Pro es necesaria para autenticar la aplicación en PowerBI.com para obtener acceso a los informes de los repositorios correctos.

Pero para [crear o editar informes insertados](https://github.com/Microsoft/PowerBI-JavaScript/wiki/Create-Report-in-Embed-View) dentro de la aplicación, el usuario final no necesita una licencia Pro, porque no es imprescindible ser un usuario de Power BI.

### <a name="can-i-get-started-for-free"></a>¿Puedo empezar de forma gratuita?

Sí, puede usar sus [créditos de Azure](https://azure.microsoft.com/free/) para Power BI Embedded.

### <a name="can-i-get-a-trial-experience-for-power-bi-embedded-in-azure"></a>¿Puedo usar una versión de evaluación gratuita de Power BI Embedded en Azure?

Puesto que Power BI Embedded forma parte de Azure, se puede usar el servicio con el [crédito de 200 dólares que se recibe al suscribirse a Azure](https://azure.microsoft.com/free/).

### <a name="is-power-bi-embedded-available-for-national-clouds-us-government-germany-china"></a>¿Power BI Embedded está disponible para nubes nacionales (Gobierno de EE. UU., Alemania, China)?

Power BI Embedded también está disponible para las [nubes nacionales](embed-sample-for-customers-national-clouds.md).

### <a name="is-power-bi-embedded-available-for-non-profits-and-educational"></a>¿Está Power BI Embedded disponible para entidades educativas y sin ánimo de lucro?

No hay ningún precio especial de Azure para entidades sin ánimo de lucro y centros educativos.

## <a name="power-bi-workspace-collection"></a>Colección de áreas de trabajo de Power BI

### <a name="what-is-power-bi-workspace-collection"></a>¿Qué es la colección de áreas de trabajo de Power BI?

**Colección de áreas de trabajo de Power BI** (**Power BI Embedded**, versión 1) es una solución basada en el recurso de Azure **Colección de áreas de trabajo de Power BI**. Esta solución le permite crear aplicaciones de **Power BI Embedded** para sus clientes con contenido de Power BI en la solución **Colección de áreas de trabajo de Power BI**, API dedicadas y claves de colecciones de áreas de trabajo para autenticar la aplicación en Power BI.

### <a name="can-i-migrate-from-power-bi-workspace-collection-to-power-bi-embedded"></a>¿Puedo migrar de la colección de áreas de trabajo de Power BI a Power BI Embedded?

1. Puede usar la herramienta de migración para clonar el contenido de la **colección de áreas de trabajo de Power BI** en Power BI: https://docs.microsoft.com/power-bi/developer/migrate-from-powerbi-embedded#content-migration.

2. Comience con la prueba de concepto de la aplicación de **Power BI Embedded** que usa el contenido de Power BI.

3. Cuando esté listo para producción, adquiera una capacidad dedicada de **Power BI Embedded** y asigne el contenido de Power BI (área de trabajo) a dicha capacidad.

    > [!Note]
    > Puede seguir usando la **colección de áreas de trabajo de Power BI** al compilar en paralelo con una solución de **Power BI Embedded**. Cuando esté listo, puede mover el cliente a la nueva solución de **Power BI Embedded** y retirar la solución **Colección de áreas de trabajo de Power BI**.

Para más información, vea [Migración de contenido de la colección de áreas de trabajo de Power BI a Power BI Embedded](./migrate-from-powerbi-embedded.md).

### <a name="is-power-bi-workspace-collection-on-a-deprecation-path"></a>¿La colección de áreas de trabajo de Power BI se va a dejar de usar?

Sí, pero los clientes que ya usan la solución de la **colección de áreas de trabajo de Power BI** pueden seguir usándola hasta que esté en desuso. Los clientes también pueden crear colecciones de áreas de trabajo y cualquier aplicación de **Power BI Embedded** en las que todavía se use la solución **Colección de áreas de trabajo de Power BI**.

Sin embargo, esto también significa que no se agregan nuevas características a una ninguna solución de **colección de áreas de trabajo de Power BI**. Recomendamos a los clientes que planeen su migración a la nueva solución de **Power BI Embedded**.

### <a name="when-is-power-bi-workspace-collection-support-discontinued"></a>¿Cuándo se interrumpe el soporte para la colección de áreas de trabajo de Power BI?

Los clientes que ya usan la solución de las **colecciones de áreas de trabajo de Power BI** pueden seguir usándola hasta el final de junio de 2018 o hasta que finalice su contrato de soporte técnico.

### <a name="in-what-regions-can-i-create-a-pbi-workspace-collection"></a>¿En qué regiones se pueden crear colecciones de áreas de trabajo de Power BI?

Las regiones disponibles son Sudeste de Australia, Sur de Brasil, Centro de Canadá, Este de EE. UU. 2, Este de Japón, Centro y norte de EE. UU., Europa del Norte, Centro y Sur de EE. UU., Sudeste de Asia, Sur de Reino Unido, Oeste de Europa, Oeste de la India y Oeste de EE. UU.

### <a name="why-should-i-migrate-from-pbi-workspace-collection-to-power-bi-embedded"></a>¿Por qué debo migrar de la Colección de áreas de trabajo de Power BI a Power BI Embedded?

Algunas características y funcionalidades nuevas de la solución **Power BI Embedded** no se pueden usar con la **Colección de áreas de trabajo de Power BI**.

Algunas de las características son:
* Se admiten todos los orígenes de datos de PBI. Solo se admiten dos orígenes de datos de la **colección de áreas de trabajo de Power BI**. 
* Las nuevas características como Preguntas y respuestas, actualizaciones, marcadores, inserción de paneles e iconos y menús personalizados solo se admiten en la solución **Power BI Embedded**.
* Modelo de facturación de capacidad.

## <a name="embedding-setup-tool"></a>Herramienta de configuración de inserción

### <a name="what-is-the-embedding-setup-tool"></a>¿Qué es la herramienta de configuración de inserción?

La [herramienta de configuración de inserción](https://aka.ms/embedsetup) permite empezar a trabajar rápidamente y descargar una aplicación de ejemplo para empezar con la inserción con Power BI.

### <a name="which-solution-should-i-choose"></a>¿Qué solución debería elegir?

* La [inserción para los clientes](embedding.md#embedding-for-your-customers) permite insertar paneles e informes para los usuarios que no tienen una cuenta de Power BI. Ejecute la solución de [inserción para los clientes](https://aka.ms/embedsetup/AppOwnsData).
* La [inserción para la organización](embedding.md#embedding-for-your-organization) permite ampliar el servicio Power BI. Ejecute la solución de [inserción para la organización](https://aka.ms/embedsetup/UserOwnsData).

### <a name="ive-downloaded-the-sample-app-which-solution-do-i-choose"></a>He descargado la aplicación de ejemplo, ¿qué solución debo elegir?

Si está trabajando con la experiencia de **inserción para los clientes**, guarde el archivo *PowerBI-Developer-Samples.zip* y descomprímalo. Después, abra la carpeta *PowerBI-Developer-Samples-master\App Owns Data* y ejecute el archivo *PowerBIEmbedded_AppOwnsData.sln*.

Si está trabajando con la experiencia de **inserción para la organización**, guarde el archivo *PowerBI-Developer-Samples.zip* y descomprímalo. Después, abra la carpeta *PowerBI-Developer-Samples-master\User Owns Data\integrate-report-web-app* y ejecute el archivo *pbi-saas-embed-report.sln*.

### <a name="how-can-i-edit-my-registered-application"></a>¿Cómo puedo editar mi aplicación registrada?

Para obtener información sobre cómo editar aplicaciones registradas en Azure AD, consulte [Inicio rápido: Actualización de una aplicación en Azure Active Directory](/azure/active-directory/develop/quickstart-v1-update-azure-ad-app).

### <a name="how-can-i-edit-my-power-bi-user-profile-or-data"></a>¿Cómo puedo editar los datos o el perfil de usuario de Power BI?

[Aquí](../../fundamentals/service-basic-concepts.md) encontrará información sobre cómo editar los datos de Power BI.

Para obtener más información, vea [Solución de problemas de una aplicación insertada](embedded-troubleshoot.md).

¿Tiene más preguntas? [Pruebe la comunidad de Power BI](https://community.powerbi.com/)