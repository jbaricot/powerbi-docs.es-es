---
title: Notas del producto sobre la seguridad de Power BI
description: Notas del producto en las que se explican y describen la arquitectura de seguridad y la implementación de Power BI
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 05/14/2020
LocalizationGroup: Conceptual
ms.openlocfilehash: 5cee5dd701f7ac40b3f363e1bdcee039037fcde9
ms.sourcegitcommit: 1cad78595cca1175b82c04458803764ac36e5e37
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/19/2021
ms.locfileid: "98565120"
---
# <a name="power-bi-security-whitepaper"></a>Notas del producto sobre la seguridad de Power BI

**Resumen:** Power BI es una oferta de servicio de software en línea (*SaaS* o software como servicio) de Microsoft que le permite crear con facilidad y rapidez paneles, informes, conjuntos de información y visualizaciones de Business Intelligence de autoservicio. Con Power BI, se puede conectar a muchos orígenes de datos diferentes, combinar y dar forma a los datos de esas conexiones y, después, crear informes y paneles que se pueden compartir con otros usuarios.

**Escritor:** David Iseminger

**Revisores técnicos:** Pedram Rezaei, Cristian Petculescu, masiva Harinath, Tod Manning, Haydn Richardson, Adam Wilson, Ben Childs, Robert Bruckner, Sergei Gundorov, Kasper de Jonge

**Se aplica a:** Power BI SaaS, Power BI Desktop, Power BI Embedded Power BI Premium

> [!NOTE]
> Puede guardar o imprimir estas notas del producto si selecciona **Imprimir** desde el explorador y, a continuación, selecciona **Guardar como PDF**.

## <a name="introduction"></a>Introducción

**Power BI** es una oferta de servicio de software en línea (_SaaS_ o software como servicio) de Microsoft que le permite crear con facilidad y rapidez paneles, informes, conjuntos de información y visualizaciones de Business Intelligence de autoservicio. Con Power BI, se puede conectar a muchos orígenes de datos diferentes, combinar y dar forma a los datos de esas conexiones y, después, crear informes y paneles que se pueden compartir con otros usuarios.

El servicio Power BI se rige por los [términos de Microsoft Online Services](https://www.microsoftvolumelicensing.com/DocumentSearch.aspx?Mode=3&amp;DocumentTypeId=31) y la [Declaración de privacidad de Microsoft Enterprise](https://www.microsoft.com/privacystatement/OnlineServices/Default.aspx). Para conocer la ubicación de procesamiento de datos, vea los términos de ubicación de procesamiento de datos de los Términos de Microsoft Online Services. Para obtener información de cumplimiento, el [Centro de confianza de Microsoft](https://www.microsoft.com/trust-center/product-overview) es el principal recurso para Power BI. El equipo de Power BI se esfuerza para brindar a sus clientes las innovaciones y la productividad más recientes. Power BI está actualmente en el nivel D del marco de cumplimiento de Microsoft 365. Obtenga más información sobre el cumplimiento en el [centro de confianza de Microsoft](/compliance/regulatory/offering-home).

En este artículo se describe la seguridad de Power BI a través de una explicación de su arquitectura; después se explica cómo se autenticarán los usuarios en Power BI y cómo se establecen las conexiones de datos y, luego, cómo se almacenan y mueven los datos a través del servicio en Power BI. La última sección está dedicada a preguntas relacionadas con la seguridad, con las respuestas correspondientes.

## <a name="power-bi-architecture"></a>Arquitectura de Power BI

El servicio **Power BI** se basa en **Azure**, que es la [plataforma de informática en la nube](https://azure.microsoft.com/overview/what-is-azure/) de Microsoft. En la actualidad, Power BI se implementa en muchos centros de datos en todo el mundo: hay muchas implementaciones activas a disposición de los clientes en las regiones a las que sirven esos centros de datos y un número equivalente de implementaciones pasivas que actúan como copias de seguridad para cada implementación activa.

Cada implementación de Power BI consta de dos clústeres: un front-end web (**WFE**) y un **back-end**. Estos dos clústeres se muestran en la imagen siguiente y constituyen el fondo del resto de este artículo. 

![WFE y back-end](media/whitepaper-powerbi-security/powerbi-security-whitepaper_01.png)

Power BI usa Azure Active Directory (**AAD**) para la autenticación y administración de cuentas. Power BI también usa el **Traffic Manager de Azure (ATM)** para dirigir el tráfico de usuario al centro de recursos más cercano, determinado por el registro DNS del cliente que intenta conectarse, durante el proceso de autenticación y para descargar archivos y contenido estático. Power BI usa el WFE más cercano geográficamente para distribuir de forma eficaz el contenido estático y los archivos necesarios a los usuarios, con la excepción de Power BI objetos visuales que se entregan mediante la **Content Delivery Network de Azure (CDN)**.

### <a name="the-wfe-cluster"></a>El clúster WFE

El clúster **WFE** administra el proceso de autenticación y conexión inicial para Power BI, con AAD para autenticar clientes y proporcionar tokens para conexiones de clientes siguientes al servicio de Power BI.

![El clúster WEF](media/whitepaper-powerbi-security/powerbi-security-whitepaper_02.png)

Cuando los usuarios se intentan conectar al servicio Power BI, el servicio DNS del cliente se puede comunicar con **Azure Traffic Manager** para buscar el centro de datos más cercano con una implementación de Power BI. Para más información sobre este proceso, vea [Métodos de enrutamiento del tráfico de Azure Traffic Manager](/azure/traffic-manager/traffic-manager-routing-methods#performance-traffic-routing-method).

El clúster WFE más cercano al usuario administra la secuencia de inicio de sesión y autenticación (descrita más adelante en este artículo) y proporciona un token de AAD al usuario una vez que la autenticación es correcta. El componente ASP.NET dentro del clúster WFE analiza la solicitud para determinar a qué organización pertenece el usuario y, después, consulta el **Servicio global** de Power BI. El Servicio global es una sola tabla de Azure que se comparte entre todos los clústeres WFE y de back-end del mundo, y que asigna usuarios y organizaciones de clientes al centro de datos en el que se hospeda su inquilino de Power BI. El WFE especifica al explorador en qué clúster de back-end se hospeda el inquilino de la organización. Una vez que se ha autenticado a un usuario, las posteriores interacciones del cliente se producen directamente con el clúster de back-end, sin que WFE intermedie para dichas solicitudes.

### <a name="the-power-bi-back-end-cluster"></a>Clúster de back-end de Power BI

El clúster **back-end** informa de cómo interactúan los clientes autenticados con el servicio de Power BI. El clúster **back-end** administra visualizaciones, paneles para el usuario, conjuntos de datos, informes, almacenamiento de datos, conexiones de datos, actualización de datos y otros aspectos de la interacción con el servicio de Power BI.

![Clúster de back-end](media/whitepaper-powerbi-security/powerbi-security-whitepaper_03.png)

El rol **Puerta de enlace** actúa como una puerta de enlace entre las solicitudes del usuario y el servicio de Power BI. Los usuarios no interactúan directamente con roles que no sean el Rol de puerta de enlace.

**Importante:** Es imperativo tener en cuenta que _solo_ los roles de Azure API Management (**APIM**) y puerta de enlace (**GW**) son accesibles a través de la red pública de Internet. Proporcionan autenticación, autorización, protección DDoS, limitación, equilibrio de carga, enrutamiento y otras capacidades.

La línea de puntos en la imagen del clúster de **back-end** anterior aclara el límite entre los dos únicos roles accesibles para los usuarios (a la izquierda de la línea de puntos) y los roles a los que únicamente puede acceder el sistema. Cuando un usuario autenticado se conecta al servicio Power BI, la conexión y cualquier solicitud del cliente se acepta y administra mediante el rol de **Puerta de enlace** y **Azure API Management**, que después interactúa en nombre del usuario con el resto del servicio Power BI. Por ejemplo, cuando un cliente intenta ver un panel, el rol **Puerta de enlace** acepta la solicitud y, a continuación, envía de forma independiente una solicitud al rol **Presentación** para recuperar los datos necesarios para que el explorador muestre el panel.

![El rol de puerta de enlace](media/whitepaper-powerbi-security/powerbi-security-whitepaper_04.png)

### <a name="power-bi-premium"></a>Power BI Premium

**Power BI Premium** ofrece un área de trabajo de servicio dedicada, aprovisionada y con particiones para los suscriptores que necesitan recursos dedicados para sus actividades de Power BI. Cuando un cliente se registra para una suscripción de Power BI Premium, se crea la capacidad Premium mediante **Azure Resource Manager**. El lanzamiento de esa suscripción asigna un conjunto de máquinas virtuales acordes con el nivel de suscripción, en el centro de datos donde se hospeda su inquilino de Power BI (a excepción de los entornos Multi-Geo, como se describe más adelante en este documento), iniciado como una implementación de **Azure Service Fabric**.

![Power BI Premium](media/whitepaper-powerbi-security/powerbi-security-whitepaper_05.png)

Una vez creada, toda la comunicación con el clúster Premium se enruta a través del clúster de back-end de Power BI, donde se establece una conexión a las máquinas virtuales de la suscripción de **Power BI Premium** dedicada del cliente.

### <a name="data-storage-architecture"></a>Arquitectura de almacenamiento de datos

Power BI usa dos repositorios principales para almacenar y administrar datos: los datos cargados por los usuarios se envían normalmente a **Azure Blob Storage**, y todos los metadatos, así como los artefactos para el propio sistema, se almacenan detrás de un firewall en **Azure SQL Database**.

![Almacenamiento de datos](media/whitepaper-powerbi-security/powerbi-security-whitepaper_06.png)

Por ejemplo, cuando un usuario importa un libro de Excel al servicio Power BI, se crea una base de datos tabular de Analysis Services en memoria, y los datos se almacenan en memoria hasta un máximo de una hora (o hasta que en el sistema se produzca presión de memoria). Los datos también se envían a **Azure Blob Storage**.

Los metadatos sobre la suscripción de Power BI de un usuario, como paneles, informes, orígenes de datos recientes, áreas de trabajo, información de la organización y del inquilino, y otros metadatos sobre el sistema, se almacenan y actualizan en **Azure SQL Database**. Toda la información almacenada en Azure SQL Database está totalmente cifrada mediante la tecnología [Cifrado de datos transparente (TDE) de Azure SQL](/azure/sql-database/transparent-data-encryption-azure-sql). También se cifran todos los datos que se almacenan en Azure Blob Storage. En la sección **Almacenamiento y movimiento de datos** se describe más información sobre el proceso de carga, almacenamiento y movimiento de los datos.

## <a name="tenant-creation"></a>Creación de inquilinos

Un inquilino es una instancia dedicada del servicio Azure AD que una organización recibe y posee cuando se suscribe a un servicio en la nube de Microsoft, como Azure, Microsoft Intune, Power BI o Microsoft 365. Cada inquilino de Azure AD es distinto e independiente de otros inquilinos de Azure AD.

Un inquilino aloja los usuarios de una empresa y la información sobre ellos: sus contraseñas, datos de perfil de usuario, permisos, etc. También contiene grupos, aplicaciones y otra información relativa a una organización y su seguridad. Para obtener más información, consulte [¿Qué es un inquilino de Azure ad](/office365/enterprise/subscriptions-licenses-accounts-and-tenants-for-microsoft-cloud-offerings).

Se crea un inquilino de Power BI en el centro de datos que se considera más cercano al país (o región) y la información de estado proporcionada para el inquilino en Azure Active Directory, que se proporcionó cuando se aprovisionó inicialmente el Microsoft 365 o el servicio Power BI. El inquilino de Power BI no se mueve de esa ubicación de centro de datos hoy.

### <a name="multiple-geographies-multi-geo"></a>Varias zonas geográficas (Multi-Geo)

Algunas organizaciones requieren una presencia de Power BI en varias zonas geográficas, o regiones, según las necesidades empresariales. Por ejemplo, una empresa puede tener su Power BI inquilino en el Estados Unidos pero también puede hacer negocios en otras áreas geográficas, como Australia, y necesitar ciertos Power BI datos que permanecen en reposo en esa región remota para cumplir con las normativas locales. A partir de la segunda mitad de 2018, las organizaciones con su inquilino de inicio en una geografía también pueden aprovisionar y acceder a Power BI recursos ubicados en otra geografía. Por comodidad, a lo largo de este documento se hará referencia a esta característica como **Multi-Geo**.

El artículo más actual y el principal para obtener información multigeográfica es el artículo [de configuración de la compatibilidad con múltiples geografías para Power BI Premium](../admin/service-admin-premium-multi-geo.md) . 

Hay varios detalles técnicos que deben evaluarse en el contexto de las leyes y regulaciones locales cuando se trabaja en zonas geográficas diferentes. Estos detalles incluyen los siguientes:

- Un nivel de ejecución de consultas remotas se hospeda en la región de capacidad remota para asegurarse de que el modelo de datos, las cachés y la mayoría del procesamiento de datos permanecen en la región de capacidad remota. Hay algunas excepciones, como se detalla en el artículo sobre la [Power BI Premium multigeográfica](../admin/service-admin-premium-multi-geo.md) .
- Un texto de consulta en caché y el resultado correspondiente almacenado en una región remota permanecerán en esa región en reposo. sin embargo, otros datos en tránsito pueden ir entre varias zonas geográficas.
- Los archivos PBIX o XLSX que se publican (se cargan) en una capacidad multigeográfica del servicio Power BI pueden dar lugar a que se almacene temporalmente una copia en el almacenamiento de blobs de Azure en la región de inquilino de Power BI. En tales circunstancias, los datos se cifran mediante el cifrado de servicio de Azure Storage (SSE) y la copia está programada para la recolección de elementos no utilizados en cuanto se completa el procesamiento y la transferencia del contenido del archivo a la región remota. 
- Cuando se mueven datos entre regiones en un entorno multigeográfico, la instancia de los datos de la región de origen se eliminará en un plazo de 7-30 días. 

### <a name="datacenters-and-locales"></a>Centros de datos y configuraciones regionales

Power BI está disponible en regiones concretas, en función de dónde se implementen los clústeres de Power BI en los centros de datos regionales. Microsoft tiene previsto ampliar su infraestructura de Power BI a centros de datos adicionales.

Los vínculos siguientes proporcionan información adicional sobre los centros de datos de Azure.

- [Regiones de Azure](https://azure.microsoft.com/regions/): información sobre la presencia global y las ubicaciones de Azure.
- [Servicios de Azure, por región](https://azure.microsoft.com/regions/#services): una lista completa de los servicios de Azure (tanto de infraestructura como de plataforma) disponibles de Microsoft en cada región.

Actualmente, el servicio Power BI está disponible en regiones específicas, con servicio de centros de recursos como se describe en el [centro de confianza de Microsoft](https://www.microsoft.com/trust-center/product-overview). El siguiente vínculo muestra un mapa de centros de datos de Power BI; puede mantener el puntero sobre una región para ver los centros de datos que se encuentran allí:

* [Centros de datos de Power BI](https://www.microsoft.com/TrustCenter/CloudServices/business-application-platform/data-location)

Microsoft también proporciona centros de datos para nubes soberanas. Para obtener más información sobre la disponibilidad del servicio Power BI para nubes nacionales, vea [Nubes nacionales de Power BI](https://powerbi.microsoft.com/clouds/).

Para obtener más información sobre dónde se almacenan los datos y cómo se usan, vea [Microsoft Trust Center](https://www.microsoft.com/trust-center/product-overview). Los compromisos sobre la ubicación de los datos de cliente en reposo se especifican en los **Términos de procesamiento de datos** de los [Términos de Microsoft Online Services](https://www.microsoftvolumelicensing.com/DocumentSearch.aspx?Mode=3&amp;DocumentTypeId=31).

## <a name="user-authentication"></a>Autenticación de usuario

La autenticación de usuarios en el servicio Power BI consta de una serie de solicitudes, respuestas y redireccionamientos entre el explorador del usuario y el servicio Power BI o los servicios de Azure que se usan en Power BI. Esa secuencia describe el proceso de autenticación de usuarios en Power BI. Para obtener más información sobre las opciones de los modelos de autenticación de usuario (modelos de inicio de sesión) de una organización, consulte [elección de un modelo de inicio de sesión para Microsoft 365](https://blogs.office.com/2014/05/13/choosing-a-sign-in-model-for-office-365/).

### <a name="authentication-sequence"></a>Secuencia de autenticación

La secuencia de autenticación del usuario para el servicio Power BI se produce como se describe en los pasos siguientes, que se ilustran en las imágenes siguientes.

1. Un usuario inicia una conexión al servicio Power BI desde un explorador, ya sea escribiendo la dirección del Power BI en la barra de direcciones (como `https://app.powerbi.com` ) o seleccionando _iniciar sesión_ desde la página de aterrizaje de Power BI ( https://powerbi.microsoft.com) . La conexión se establece mediante TLS 1.2 y HTTPS, y toda la comunicación posterior entre el explorador y el servicio Power BI usa HTTPS. La solicitud se envía a **Azure Traffic Manager**.

2. **Azure Traffic Manager** comprueba el registro DNS del usuario para determinar el centro de datos más cercano donde se ha implementado Power BI, y responde al DNS con la dirección IP del clúster WFE al que se debe enviar al usuario.

3. Después, WFE redirige al usuario a la página de inicio de sesión de Microsoft Online Services.

    ![Secuencia de autenticación](media/whitepaper-powerbi-security/powerbi-security-whitepaper_08.png)

1. Una vez que se ha autenticado al usuario, la página de inicio de sesión le redirige al **clúster WFE** del servicio Power BI más cercano que se haya determinado anteriormente.

2. El explorador envía una cookie obtenida del inicio de sesión correcto a Microsoft Online Services, que es inspeccionada por el **servicio ASP.NET** dentro del **clúster WFE**.

3. El clúster WFE consulta con el servicio **Azure Active Directory** (**AAD**) para autenticar la suscripción del usuario al servicio Power BI y para obtener un token de seguridad de AAD. Cuando AAD devuelve la autenticación correcta del usuario y un token de seguridad de AAD, el clúster WFE consulta el **Servicio global de Power BI**, en el que se mantiene una lista de los inquilinos y sus ubicaciones de clúster de back-end de Power BI, y determina qué clúster del servicio Power BI contiene el inquilino del usuario. Después, el clúster WFE dirige al usuario al clúster de Power BI donde reside su inquilino y devuelve una colección de elementos al explorador del usuario:

      - El **token de seguridad de AAD**.
      - **Información de la sesión**
      - La dirección web del clúster de **back-end** con el que el usuario se puede comunicar e interactuar.

1. Después, el explorador del usuario contacta con la instancia de Azure CDN especificada, o para algunos archivos el WFE, con el fin de descargar la colección de archivos comunes especificados que se necesitan para habilitar la interacción del explorador con el servicio Power BI. Luego, la página del explorador incluye el token de AAD, la información de la sesión, la ubicación del clúster de back-end asociado y la colección de archivos descargados desde Azure CDN y el clúster WFE, para la duración de la sesión de explorador del servicio Power BI.

![Interacción de Azure CDN](media/whitepaper-powerbi-security/powerbi-security-whitepaper_09.png)

Una vez completados esos elementos, el explorador inicia el contacto con el clúster de back-end especificado y comienza la interacción del usuario con el servicio Power BI. A partir de ese punto, todas las llamadas al servicio Power BI se realizan con el clúster de back-end especificado, y en todas se incluye el token de AAD del usuario. El token de AAD tiene un tiempo de espera de una hora; WFE lo actualiza periódicamente si una sesión de usuario permanece abierta, con el fin de conservar el acceso.

## <a name="data-storage-and-movement"></a>Almacenamiento y movimiento de datos

En el servicio Power BI, los datos están _en reposo_ (datos disponibles para un usuario de Power BI sobre el que actualmente no se actúa), o bien _en curso_ (por ejemplo: consultas que se ejecutan, conexiones y modelos de datos sobre los que se actúa, datos o modelos que se cargan en el servicio Power BI y otras acciones que los usuarios o el servicio Power BI pueden emprender sobre los datos a los que se está accediendo o que se están actualizando). Los datos que están en proceso se conocen como _datos en curso_. En Power BI, los datos en reposo se cifran. Los datos que están en tránsito, lo que significa que se envían al servicio Power BI o que este los recibe, también se cifran.

El servicio Power BI también administra los datos de otra forma en función de si se accede a ellos mediante **DirectQuery** o importación. Por tanto, hay dos categorías de datos de usuario para Power BI: los datos a los que se accede con DirectQuery y los datos a los que no se accede con DirectQuery.

**DirectQuery** es una consulta para la que se ha traducido la consulta de un usuario de Power BI del lenguaje Expresiones de análisis de datos (DAX) de Microsoft (que es el que se usa en Power BI y otros productos de Microsoft para crear consultas) al lenguaje de datos nativo del origen de datos (por ejemplo, T-SQL u otros lenguajes de base de datos nativos). Los datos asociados con DirectQuery se almacenan solo por referencia, lo que significa que los datos de origen no se almacenan en Power BI cuando DirectQuery no está activa (excepto los datos de visualización que se usan para mostrar paneles e informes, como se describe en la sección _Datos en curso (movimiento de datos)_, a continuación). En su lugar, se almacenan referencias a los datos de DirectQuery, que permiten acceder a esos datos cuando se ejecuta DirectQuery. Una instancia de DirectQuery contiene toda la información necesaria para ejecutar la consulta, incluida la cadena de conexión y las credenciales que se usan para acceder a los orígenes de datos, lo que permite a DirectQuery conectarse a los orígenes de datos incluidos para la actualización automática. Con DirectQuery, la información del modelo de datos subyacente se incorpora a DirectQuery.

Una consulta de un conjunto de datos de importación consta de una colección de consultas DAX que _no_ se traducen directamente al lenguaje nativo de ningún origen de datos subyacente. Las consultas de importación no incluyen credenciales para los datos subyacentes, y estos se cargan en el servicio Power BI a menos que sean datos locales a los que se accede a través de una instancia de [Power BI Gateway](../connect-data/service-gateway-onprem.md), en cuyo caso la consulta solo almacena referencias a datos locales.

En la tabla siguiente se describen los datos de Power BI en función del tipo de consulta que se usa. Una **X** indica la presencia de datos de Power BI al usar el tipo de consulta asociado.

|                         | Importar   | DirectQuery | Live Connect  |
|-------------------------|----------|-------------|---------------|
|**Esquema**               | X        | X           |               |
|**Datos de fila**             | X        |             |               |
|**Almacenamiento en caché de datos de objetos visuales** | X        | X           | X             |

La distinción entre DirectQuery y otras consultas determina cómo controla el servicio Power BI los datos en reposo, y si se cifra la propia consulta. En las secciones siguientes se describen los datos en reposo y en movimiento, y se explica el cifrado, la ubicación y el proceso para controlar los datos.

### <a name="data-at-rest"></a>Datos en reposo

Cuando los datos están en reposo, el servicio Power BI almacena conjuntos de datos, informes e iconos de panel de la manera descrita en las subsecciones siguientes. Como se ha mencionado antes, en Power BI se cifran los datos en reposo. En las secciones siguientes, ETL es el acrónimo de Extracción, Transformación y Carga.

#### <a name="encryption-keys"></a>Claves de cifrado

- Las claves de cifrado para las claves de Azure Blob se almacenan, cifradas, en Azure Key Vault.
- El propio Azure SQL administra las claves de cifrado para la tecnología TDE de Azure SQL Database.
- La clave de cifrado para el servicio de movimiento de datos y la puerta de enlace de datos local se almacena:
  - En la puerta de enlace de datos local en la infraestructura del cliente, para los orígenes de datos locales.
  - En el rol de movimiento de datos, para los orígenes de datos basados en la nube.

La clave de cifrado de contenido (CEK) usada para cifrar el Blob Storage Microsoft Azure es una clave de bits 256 generada de forma aleatoria. El algoritmo que usa la CEK para cifrar el contenido es AES\_CBC\_256.

La clave de cifrado de claves (KEK) que se usa para cifrar la CEK es una clave predefinida de 256 bits. El algoritmo que usa la KEK para cifrar la CEK es A256KW.

Las claves de cifrado de puerta de enlace basadas en la clave de recuperación nunca abandonan una infraestructura local. Power BI no puede acceder a los valores de las credenciales cifradas en el entorno local y no puede interceptarlas; los clientes web cifran la credencial con una clave pública que está asociada con la puerta de enlace con la que se comunica.

Para los orígenes de datos basados en la nube, el rol de movimiento de datos cifra las claves de cifrado con métodos de [Always Encrypted](/sql/relational-databases/security/encryption/always-encrypted-database-engine). Obtenga más información sobre la [característica de base de datos Always Encrypted](/sql/relational-databases/security/encryption/always-encrypted-database-engine).

#### <a name="datasets"></a>Conjuntos de datos

1. Metadatos (tablas, columnas, medidas, cálculos, cadenas de conexión, etc.)

    a. Para la instancia local de Analysis Services no se almacena nada en el servicio, excepto una referencia a esa base de datos almacenada cifrada en Azure SQL.

    b. Todos los demás metadatos para ETL, DirectQuery e inserción de datos se cifran y almacenan en Azure Blob Storage.

1. Credenciales para los orígenes de datos originales
  
      a. Instancia local de Analysis Services: no se necesitan credenciales y, por tanto, no se almacena ninguna.

      b. DirectQuery: depende de si el modelo se ha creado directamente en el servicio, en cuyo caso se almacena en la cadena de conexión y se cifra en Azure Blob, o bien si el modelo se ha importado desde Power BI Desktop, en cuyo caso se almacenan las credenciales cifradas en Azure SQL Database de movimiento de datos. La clave de cifrado se almacena en el equipo que ejecuta la puerta de enlace en la infraestructura del cliente.

      c. Datos insertados: no aplicable.

      d. ETL

      - Para **Salesforce** o **OneDrive**: los tokens de actualización se almacenan cifrados en la instancia de Azure SQL Database del servicio Power BI.
      - De lo contrario:
        - Si se establece el conjunto de datos para la actualización, las credenciales se almacenan cifradas en la instancia de Azure SQL Database de Movimiento de datos. La clave de cifrado se almacena en el equipo que ejecuta la puerta de enlace en la infraestructura del cliente.
        - Si el conjunto de datos no se establece para la actualización, no se almacena ninguna credencial para los orígenes de datos

1. Datos

    a. Instancia local de Analysis Services y DirectQuery: no se almacena nada en el servicio Power BI.

    b. ETL: se cifra en Azure Blob Storage, pero todos los datos actualmente en la instancia de Azure Blob Storage del servicio Power BI usan [Storage Service Encryption (SSE) de Azure](/azure/storage/common/storage-service-encryption), también conocido como cifrado del lado servidor. Multi-Geo también usa SSE.

    c. Datos de inserción v1: se cifran en Azure Blob Storage, pero todos los datos actualmente en la instancia de Azure Blob Storage del servicio Power BI usan [Storage Service Encryption (SSE) de Azure](/azure/storage/common/storage-service-encryption), también conocido como cifrado del lado servidor. Multi-Geo también usa SSE. Los datos de inserciones v1 se han suspendido a partir del 2016. 

    d. Datos de inserción v2: se almacenan en Azure SQL, cifrados.

Para cifrar su instancia de Azure Blob Storage, Power BI usa el enfoque de cifrado del lado cliente, mediante el modo de encadenamiento de bloques de cifrado (CBC) con el Estándar de cifrado avanzado (AES). Obtenga [más información sobre el cifrado del lado cliente](/azure/storage/common/storage-client-side-encryption).

Power BI proporciona supervisión de integridad de datos de las maneras siguientes:

* Para los datos en reposo en Azure SQL, Power BI usa dbcc, TDE y la suma de comprobación de página constante como parte de las ofertas de SQL nativas.

* Para los datos en reposo en Azure Blob Storage, Power BI usa el cifrado del lado cliente y HTTPS para transferir datos al almacenamiento, lo que incluye comprobaciones de integridad durante la recuperación de los datos. Obtenga [más información sobre la seguridad de Azure Blob Storage](/azure/storage/blobs/security-recommendations).

#### <a name="reports"></a>Informes

1. Metadatos (definición de informe)

   a. Los informes pueden ser Excel para informes de Microsoft 365 o informes de Power BI. Lo siguiente se aplica a los metadatos en función del tipo de informe:
        
    &ensp;&ensp;un. Los metadatos de informe de Excel se almacenan cifrados en SQL Azure. Los metadatos también se almacenan en Microsoft 365.

    &ensp;&ensp;b. Power BI informes se almacenan cifrados en Azure SQL Database.

2. Datos estáticos

   Los datos estáticos incluyen artefactos como imágenes de fondo y objetos visuales de Power BI.

    &ensp;&ensp;un. En el caso de los informes creados con Excel para Microsoft 365, no se almacena nada.

    &ensp;&ensp;b. Para los informes de Power BI, los datos estáticos se almacenan y se cifran en Azure Blob Storage.

3. Cachés

    &ensp;&ensp;un. En el caso de los informes creados con Excel para Microsoft 365, no se almacena nada en la memoria caché.

    &ensp;&ensp;b. En el caso de Power BI informes, los datos de los objetos visuales de los informes mostrados se almacenan en caché y se almacenan en la memoria caché de datos visual que se describe en la sección siguiente.
 

4. Archivos originales de Power BI Desktop (.pbix) o Excel (.xlsx) publicados en Power BI.

    En ocasiones, se almacenan una copia o una instantánea de los archivos .xlsx o .pbix en la instancia de Azure Blob Storage de Power BI y, en ese caso, los datos se cifran. Todos estos informes almacenados en el servicio Power BI, en Azure Blob Storage, usan [Storage Service Encryption (SSE) de Azure](/azure/storage/common/storage-service-encryption), también conocido como cifrado del lado servidor. Multi-Geo también usa SSE.

#### <a name="dashboards-and-dashboard-tiles"></a>Paneles e iconos de paneles

1. Memorias caché: los datos necesarios para los objetos visuales en el panel normalmente se almacenan en caché y se almacenan en la memoria caché de datos visual que se describe en la sección siguiente. Otros iconos como los objetos visuales anclados desde Excel o SQL Server Reporting Services (SSRS) se almacenan en Azure Blob como imágenes y también se cifran.

2. Datos estáticos: que incluyen artefactos como imágenes de fondo y Power BI objetos visuales que se almacenan, cifran, en Azure BLOB Storage.

Independientemente del método de cifrado usado, Microsoft administra el cifrado de claves en nombre de los clientes.

#### <a name="visual-data-cache"></a>Caché de datos visual

Los datos visuales se almacenan en caché en ubicaciones diferentes, en función de si el conjunto de datos está hospedado en una capacidad de Power BI Premium. En el caso de los conjuntos de datos que no se hospedan en una capacidad, los datos visuales se almacenan en caché y se almacenan cifrados en un Azure SQL Database. En el caso de los conjuntos de datos que se hospedan en una capacidad, los datos visuales se pueden almacenar en caché en cualquiera de las siguientes ubicaciones:

* Azure Blob Storage
* Archivos Premium de Azure
* Nodo capacidad de Power BI Premium


### <a name="data-transiently-stored-on-non-volatile-devices"></a>Datos almacenados de forma transitoria en dispositivos no volátiles

Los dispositivos no volátiles son dispositivos que tienen memoria que persiste sin energía constante. A continuación se describen los datos que se almacenan de forma transitoria en dispositivos que no son volátiles. 

#### <a name="datasets"></a>Conjuntos de datos

1. Metadatos (tablas, columnas, medidas, cálculos, cadenas de conexión, etc.)

2. Algunos artefactos relacionados con los esquemas se pueden almacenar en el disco de los nodos de proceso durante un período de tiempo limitado. También se pueden almacenar algunos artefactos no cifrados en Azure REDIS Cache durante un período de tiempo limitado.

3. Credenciales para los orígenes de datos originales

    a. Instancia local de Analysis Services: no se almacena nada.

    b. DirectQuery: depende de si el modelo se ha creado directamente en el servicio, en cuyo caso se almacena en la cadena de conexión, en formato cifrado con la clave de cifrado almacenada en texto sin cifrar en el mismo sitio (junto con la información cifrada), o bien si el modelo se ha importado desde Power BI Desktop, en cuyo caso las credenciales no se almacenan en dispositivos que no son volátiles.

    > [!NOTE]
    > La característica de creación del modelo de servicio se ha suspendido a partir de 2017.

    c. Datos insertados: ninguno (no aplicable).

    d. ETL: ninguno (no se almacenada nada en el nodo de proceso diferente a lo que se ha explicado en la sección **Datos en reposo** anterior)
4. Datos

    Algunos artefactos de datos se pueden almacenar en el disco de los nodos de proceso durante un período de tiempo limitado.

### <a name="data-in-process"></a>Datos en curso

Los datos están en curso cuando un usuario los usa o accede a ellos de forma activa. Por ejemplo, los datos están en curso cuando un usuario accede a un conjunto de datos, revisa o modifica un panel o informe, cuando se realiza la actualización u otras actividades de acceso de datos que se puedan producir. Cuando se produce cualquiera de esos eventos y los datos están en curso, el **Rol de datos** del servicio Power BI crea una base de datos de Analysis Services (AS) en memoria y el conjunto de datos se carga en ella. Con independencia de que el conjunto de datos se base en DirectQuery o no, los datos cargados en la base de datos de AS no se cifran para permitir el acceso por parte del **Rol de datos**, y se mantienen en memoria para posteriores accesos hasta que el servicio Power BI ya no necesita el conjunto de datos. Para los clientes con una suscripción de Power BI Premium, Power BI crea una base de datos de Analysis Services (AS) en memoria en la colección del cliente aprovisionada por separado de máquinas virtuales de Power BI.

Una vez que se actúa sobre los datos, lo que inicialmente incluye su carga en Power BI, el servicio Power BI puede almacenar en caché los datos de visualización en una instancia cifrada de **Azure SQL Database**, independientemente de si el conjunto de datos se basa en DirectQuery.

Para supervisar la integridad de los datos para los datos en curso, Power BI usa HTTPS, TCP/IP y TLS para asegurarse de que los datos se cifran y se mantiene la integridad durante el transporte.

## <a name="user-authentication-to-data-sources"></a>Autenticación de usuarios en orígenes de datos

Con cada origen de datos, un usuario establece una conexión basada en su inicio de sesión y obtiene acceso a los datos con esas credenciales. Después, los usuarios pueden crear consultas, paneles e informes basados en los datos subyacentes.

Cuando un usuario comparte consultas, paneles, informes o cualquier visualización, el acceso a esos datos y visualizaciones depende de si los orígenes de datos subyacentes admiten la seguridad de nivel de rol (RLS).

Si un origen de datos subyacente admite la **seguridad de nivel de rol (RLS) de Power BI**, el servicio Power BI la aplicará y los usuarios que no tengan credenciales suficientes para acceder a los datos subyacentes (por ejemplo una consulta que se usa en un panel, informe u otro artefacto de datos) no verán los datos para los que no tengan privilegios suficientes. Si el acceso de un usuario a los datos subyacentes es distinto del usuario que ha creado el panel o el informe, las visualizaciones y otros artefactos solo mostrarán datos en función del nivel de acceso a los datos que tenga el usuario.

Si un origen de datos **no** aplica RLS, las credenciales de inicio de sesión de Power BI se aplican al origen de datos subyacente, o si se proporcionan otras credenciales durante la conexión, se aplican esas credenciales proporcionadas. Cuando un usuario carga datos en el servicio Power BI desde orígenes de datos que no sean RLS, los datos se almacenan en Power BI, como se describe en la sección **Almacenamiento y movimiento de datos** de este documento. Para los orígenes de datos que no son RLS, cuando los datos se comparten con otros usuarios (por ejemplo, a través de un panel o informe) o se produce una actualización de los datos, se usan las credenciales originales para acceder a los datos o mostrarlos.

![Seguridad de nivel de rol (RLS)](media/whitepaper-powerbi-security/powerbi-security-whitepaper_10.png)

Para obtener un ejemplo rápido y contrastar los orígenes de datos RLS y no RLS, imagine que Sam crea un informe y un panel y, después, los comparte con Abby y Ralph. Si los orígenes de datos que se usan en el informe y el panel proceden de orígenes de datos que **no** admiten RLS, Abby y Ralph podrán ver los datos que Sam ha incluido en el panel (que se ha cargado en el servicio Power BI), y tanto Abby como Ralph pueden interactuar con los datos. En cambio, si Sam crea un informe y un panel a partir de orígenes de datos que son compatibles con RLS y después lo comparte con Abby y Ralph, cuando Abby intente ver el panel se producirá lo siguiente:

1. Como el panel es de un origen de datos RLS, las visualizaciones de panel mostrarán brevemente un mensaje &quot;cargando&quot; mientras el servicio Power BI consulta el origen de datos para recuperar el conjunto de datos actual especificado en la cadena de conexión asociada con la consulta del panel subyacente.

2. A los datos se accede y se recuperan en función de las credenciales y el rol del Abby, y solo se cargan en el panel y el informe los datos para los que Abby tenga autorización suficiente.

3. Las visualizaciones en el panel y el informe se muestran según el nivel de rol de Abby.

Si Ralph accediera al panel o informe compartido, se produciría la misma secuencia en función de su nivel de rol.

## <a name="power-bi-mobile"></a>Power BI Mobile

Power BI Mobile es una colección de aplicaciones diseñadas para las tres plataformas móviles principales: Android, iOS y Windows Mobile. Las consideraciones de seguridad para las aplicaciones de Power BI Mobile se dividen en dos categorías:

* Comunicación de dispositivos
* La aplicación y los datos en el dispositivo

Para la **comunicación de dispositivos**, todas las aplicaciones de Power BI Mobile se comunican con el servicio Power BI y usan las mismas secuencias de conexión y autenticación que los exploradores, que se describen en detalle anteriormente en estas notas del producto. Las aplicaciones para dispositivos móviles iOS y Android de Power BI abren una sesión de explorador en la propia aplicación, y la aplicación móvil de Windows abre un agente para establecer el canal de comunicación con Power BI.

En la tabla siguiente se muestra la compatibilidad de autenticación basada en certificados (CBA) para Power BI Mobile en función de la plataforma de dispositivos móviles:

| **Compatibilidad con CBA** | **iOS** | **Android** | **Windows** |
| --- | --- | --- | --- |
| **Power BI** (inicio de sesión en el servicio) | admitido | admitido | No compatible |
| **SSRS ADFS** (conectarse al servidor SSRS) | No compatible | Compatible | No compatible |

Las aplicaciones Power BI Mobile se comunican activamente con el servicio Power BI. Se usan datos de telemetría para recopilar estadísticas de uso y datos similares de las aplicaciones móviles, que se transmiten a los servicios que se usan para supervisar el uso y la actividad; no se envían datos personales con los datos de telemetría.

La **aplicación de Power BI en el dispositivo** almacena datos en el dispositivo que facilitan el uso de la aplicación:

* Los tokens de Azure Active Directory y actualización se almacenan en un mecanismo seguro en el dispositivo, con medidas de seguridad estándar del sector.

* Los datos se almacenan en caché en el dispositivo, y la propia aplicación no los cifra directamente.

* La configuración también se almacena en el dispositivo sin cifrar, pero no se almacena ningún dato real del usuario.

La caché de datos de Power BI Mobile permanece en el dispositivo durante dos semanas, o bien hasta que: se quita la aplicación, el usuario cierra sesión en Power BI Mobile o el usuario no puede iniciar sesión (por ejemplo, en caso de expiración del token o cambio de contraseña). La caché de datos incluye los paneles e informes a los que se ha accedido anteriormente desde la aplicación de Power BI Mobile.

Las aplicaciones de Power BI Mobile no examinan las carpetas del dispositivo. 

Las tres plataformas para las que está disponible Power BI Mobile admiten Microsoft Intune, un servicio de software que proporciona administración de aplicaciones y dispositivos móviles. Con Intune habilitado y configurado, se cifran los datos en el dispositivo móvil y la propia aplicación de Power BI no se puede instalar en una tarjeta SD. Obtenga [más información sobre Microsoft Intune](https://www.microsoft.com/cloud-platform/microsoft-intune).

## <a name="power-bi-security-questions-and-answers"></a>Preguntas y respuestas sobre la seguridad de Power BI

Las preguntas siguientes son preguntas y respuestas comunes sobre seguridad para Power BI. Se organizan en función de cuándo se han agregado a este documento, para facilitar la capacidad de encontrar rápidamente nuevas preguntas y respuestas cuando se actualice este documento. Las preguntas más recientes se han agregado al final de esta lista.

**¿Cómo se conectan los usuarios y obtienen acceso a los orígenes de datos mientras usan Power BI?**

* **Credenciales de Power BI y credenciales de dominio:** Los usuarios inician sesión en Power BI mediante una dirección de correo electrónico; Cuando un usuario intenta conectarse a un recurso de datos, Power BI pasa la dirección de correo electrónico de inicio de sesión de Power BI como credenciales. Para los recursos conectados a un dominio (ya sea local o basado en la nube), el servicio de directorio compara el correo electrónico de inicio de sesión con un _Nombre principal de usuario_ ([UPN](/windows/win32/secauthn/user-name-formats)) para determinar si existen credenciales suficientes para permitir el acceso. En el caso de las organizaciones que usan direcciones de correo electrónico basadas en el trabajo para iniciar sesión en Power BI (el mismo correo electrónico que usan para iniciar sesión en los recursos de trabajo, como _david@contoso.com_ ), la asignación puede producirse sin problemas; en el caso de las organizaciones que no usan direcciones de correo electrónico basadas en el trabajo (como _david@contoso.onmicrosoft.com_ ), se debe establecer la asignación de directorios para permitir el Power BI acceso

* **SQL Server Analysis Services y Power BI:** En el caso de las organizaciones que usan SQL Server Analysis Services locales, Power BI ofrece la Power BI puerta de enlace de datos local (que es una **puerta de enlace**, como se hace referencia en las secciones anteriores).  La puerta de enlace de datos local de Power BI puede exigir la seguridad de nivel de rol (RLS) en los orígenes de datos. Para más información sobre RLS, vea **Autenticación de usuarios en orígenes de datos** anteriormente en este documento. Para obtener más información acerca de las puertas de enlace, consulte [puerta de enlace de datos local](../connect-data/service-gateway-onprem.md).

  Además, las organizaciones pueden usar Kerberos para el **inicio de sesión único** (SSO) y conectarse sin problemas desde Power BI a orígenes de datos locales como SQL Server, SAP HANA y Teradata. Para obtener más información y los requisitos de configuración específicos, vea [**Uso de Kerberos para el inicio de sesión único desde Power BI en orígenes de datos locales**](../connect-data/service-gateway-sso-overview.md).

* Conexiones que no son **de dominio**: para las conexiones de datos que no están unidas a un dominio y no son compatibles con la seguridad de nivel de rol (RLS), el usuario debe proporcionar las credenciales durante la secuencia de conexión, que Power BI pasa al origen de datos para establecer la conexión. Si los permisos son suficientes, los datos se cargan desde el origen de datos al servicio Power BI.

**¿Cómo se transfieren los datos a Power BI?**

* Todos los datos solicitados y transmitidos por Power BI se cifran en tránsito mediante HTTPS para establecer la conexión desde el origen de datos al servicio Power BI. Se establece una conexión segura con el proveedor de datos, y los datos se desplazan por la red solo cuando se haya establecido esa conexión.

**En Power BI, ¿cómo se almacena en caché un modelo, panel o informe? ¿Es seguro?**

* Cuando se accede a un origen de datos, el servicio Power BI sigue el proceso descrito en la sección **Almacenamiento y movimiento de datos** anteriormente en este documento.

**¿Los clientes almacenan en caché los datos de la página web localmente?**

* Cuando los clientes de explorador acceden a Power BI, los servidores web de Power BI establecen la directiva _Cache-Control_ en _no-store_. La directiva _no-store_ indica a los exploradores que no almacenen en caché la página web que está viendo el usuario, y que tampoco almacenen la página web en la carpeta de caché del cliente.

**¿Qué ocurre con la seguridad basada en roles, el uso compartido de informes, paneles y conexiones de datos? ¿Cómo funciona en cuanto al acceso a datos, la visualización del panel, el acceso a informes o la actualización?**

* Para los orígenes de datos habilitados que **no admiten la seguridad de nivel de rol (RLS)**, si un panel, informe o modelo de datos se comparte con otros usuarios a través de Power BI, los datos estarán disponibles para verlos e interactuar con ellos para los usuarios con los que se hayan compartido. Power BI *no* vuelve a autenticar a los usuarios en el origen inicial de los datos; una vez que los datos se cargan en Power BI, el usuario que se ha autenticado en el origen de datos es responsable de administrar qué usuarios y grupos pueden ver los datos.

  Cuando se realizan conexiones de datos a un origen de datos compatible con **RLS**, como un origen de datos de Analysis Services, solo se almacenan en caché en Power BI los datos de paneles. Cada vez que se ve o se accede a un informe o conjunto de datos en Power BI en el que se usan datos procedentes del origen de datos compatible con RLS, el servicio Power BI accede al origen de datos para obtener datos en función de las credenciales del usuario, y si existen permisos suficientes, los datos se cargan en el modelo de datos o informe para ese usuario. Si se produce un error de autenticación, el usuario verá un error.

  Para más información vea la sección **Autenticación de usuarios en orígenes de datos** anteriormente en este documento.

**Nuestros usuarios se conectan a los mismos orígenes de datos todo el tiempo, algunos de los cuales requieren credenciales que difieren de sus credenciales de dominio. ¿Cómo pueden evitar tener que escribir estas credenciales cada vez que realicen una conexión de datos?**

* Power BI ofrece [Power BI Personal Gateway](https://support.powerbi.com/knowledgebase/articles/649846), una característica que permite a los usuarios crear credenciales para varios orígenes de datos diferentes y luego usarlas de forma automática cuando accedan a cada uno de esos orígenes de datos. Para más información, vea [Power BI Personal Gateway](https://support.powerbi.com/knowledgebase/articles/649846).

**¿Cómo funcionan los grupos de Power BI?**

* Los grupos de Power BI permiten a los usuarios colaborar de forma rápida y sencilla en la creación de paneles, informes y modelos de datos dentro de equipos establecidos. Por ejemplo, si tiene un grupo de Power BI que incluye a todos los usuarios del equipo inmediato, puede colaborar fácilmente con todos los integrantes del equipo si selecciona el grupo desde Power BI. Los grupos de Power BI son equivalentes a los grupos universales de Office 365 (que puede [crear](https://support.office.com/Article/View-create-and-delete-Groups-in-the-Office-365-admin-center-a6360120-2fc4-46af-b105-6a04dc5461c7) y [administrar](https://support.office.com/Article/Manage-Group-membership-in-the-Office-365-admin-center-e186d224-a324-4afa-8300-0e4fc0c3000a), y de los que puede [obtener más información](https://support.office.com/Article/Find-help-about-Groups-in-Office-365-7a9b321f-b76a-4d53-b98b-a2b0b7946de1)) y usan los mismos mecanismos de autenticación que se utilizan en Azure Active Directory para proteger los datos. Puede [crear grupos en Power BI](https://support.powerbi.com/knowledgebase/articles/654250) o crear un grupo universal en el Centro de administración de Microsoft 365; en ambos casos, el resultado es el mismo para la creación de grupos en Power BI.

  Tenga en cuenta que los datos compartidos con grupos de Power BI siguen la misma consideración de seguridad que cualquier dato compartido en Power BI. Para los orígenes de datos que no son **RLS**, Power BI **no** vuelve a autenticar a los usuarios en los datos originales, y una vez que los datos se cargan en Power BI, el usuario que se ha autenticado en el origen de datos es responsable de administrar qué usuarios y grupos pueden ver los datos. Para más información vea la sección **Autenticación de usuarios en orígenes de datos** anteriormente en este documento.

  Obtenga más información sobre los [grupos en Power BI](https://support.powerbi.com/knowledgebase/articles/654247).

**¿Qué puertos usa la puerta de enlace de datos local y la puerta de enlace personal? ¿Hay algún nombre de dominio que deba permitirse con fines de conectividad?**

* La respuesta detallada a esta pregunta está disponible en el siguiente vínculo: [puertos de puerta de enlace](/data-integration/gateway/service-gateway-communication#ports)

**Cuando se trabaja con la puerta de enlace de datos local, ¿cómo se usan las claves de recuperación y dónde se almacenan? ¿Qué ocurre con la administración segura de credenciales?**

* Durante la instalación y configuración de puertas de enlace, el administrador escribe una **clave de recuperación** de puerta de enlace. Esa **clave de recuperación** se usa para generar una clave simétrica **AES** segura. También se crea una clave asimétrica de **RSA** al mismo tiempo.

    Esas claves generadas (**RSA** y **AES**) se almacenan en un archivo que se encuentra en el equipo local. Ese archivo también se cifra. El contenido del archivo solo lo puede descifrar ese equipo Windows concreto, y solo mediante esa cuenta de servicio de puerta de enlace concreta.

    Cuando un usuario escribe las credenciales del origen de datos en la interfaz de usuario del servicio Power BI, las credenciales se cifran con la clave pública en el explorador. La puerta de enlace descifra las credenciales mediante la clave privada RSA y las vuelve a cifrar con una clave simétrica AES antes de que los datos se almacenen en el servicio Power BI. Con este proceso, el servicio Power BI nunca tiene acceso a los datos sin cifrar.

**¿Qué protocolos de comunicación usa la puerta de enlace de datos local y cómo se protegen?**

* La puerta de enlace admite los dos siguientes protocolos de comunicaciones:

  - **AMQP 1,0 – TCP + TLS**: este protocolo requiere que los puertos 443, 5671-5672 y 9350-9354 estén abiertos para la comunicación saliente. Es el protocolo preferido, porque tiene una menor sobrecarga de comunicación.

  - **Https: WebSockets sobre https + TLS**: este protocolo solo usa el puerto 443. WebSocket se inicia con un único mensaje HTTP CONNECT. Una vez que se ha establecido el canal, la comunicación es esencialmente TCP+TLS. Puede forzar que la puerta de enlace use este protocolo modificando una configuración que se describe en el [artículo sobre la puerta de enlace local](/data-integration/gateway/service-gateway-communication#force-https-communication-with-azure-service-bus).

**¿Cuál es el rol de Azure CDN en Power BI?**

* Como se ha mencionado antes, Power BI usa **Azure Content Delivery Network (CDN)** para distribuir de forma eficaz el contenido estático y los archivos necesarios a los usuarios en función de la configuración regional geográfica. Para entrar en más detalle, el servicio Power BI usa varias **CDN** para distribuir de forma eficaz el contenido estático y los archivos necesarios a los usuarios a través de la red Internet pública. Estos archivos estáticos incluyen descargas de productos (como **Power BI Desktop**, la **puerta de enlace de datos local** o aplicaciones de Power BI de distintos proveedores de servicios independientes), archivos de configuración del explorador que se usan para iniciar y establecer las sucesivas conexiones con Power BI, así como la página de inicio de sesión seguro inicial de Power BI.

  En función de la información proporcionada durante la conexión inicial al servicio Power BI, el explorador del usuario contacta con la instancia de Azure **CDN** especificada (o para algunos archivos, el **WFE**) para descargar la colección de archivos comunes especificados que se necesitan para habilitar la interacción del explorador con el servicio Power BI. Luego, la página del explorador incluye el token de AAD, la información de la sesión, la ubicación del clúster de **back-end** asociado y la colección de archivos descargados desde Azure **CDN** y el clúster **WFE**, para la duración de la sesión de explorador del servicio Power BI.

**En el caso de los objetos visuales de Power BI, ¿Microsoft realiza alguna evaluación de seguridad o privacidad del código Visual personalizado antes de publicar elementos en la galería?**

* No. Es responsabilidad del cliente revisar y determinar si se debe confiar en el código del objeto visual personalizado. El código de todos los objetos visuales personalizados funciona en un entorno de espacio aislado, por lo que cualquier código incorrecto en un objeto visual personalizado no afecta de forma negativa al resto del servicio Power BI.

**¿Hay otros objetos visuales de Power BI que envían información fuera de la red del cliente?**

* Sí. Los objetos visuales Bing Maps y ESRI transmiten datos fuera del servicio Power BI para los objetos visuales que usan esos servicios.

**En el caso de las aplicaciones de plantilla, ¿Microsoft realiza alguna evaluación de seguridad o privacidad de la aplicación de plantilla antes de publicar elementos en la galería?**
* No. El publicador de la aplicación es responsable del contenido, mientras que la responsabilidad del cliente es revisar y determinar si debe confiar en el publicador de la aplicación de plantilla. 

**¿Hay aplicaciones de plantilla que pueden enviar información fuera de la red del cliente?**
* Sí. Es responsabilidad del cliente revisar la Directiva de privacidad del editor y determinar si se debe instalar la aplicación de plantilla en el inquilino. Además, el publicador es responsable de notificar el comportamiento y las capacidades de la aplicación.

**¿Qué ocurre con la soberanía de datos? ¿Podemos aprovisionar inquilinos en centros de datos ubicados en zonas geográficas específicas para asegurarse de que los datos no salen de los límites del país?**

* Algunos clientes de zonas geográficas concretas tienen la opción de crear un inquilino en una nube nacional, donde el almacenamiento y el procesamiento de datos son independientes de otros centros de datos. Las nubes nacionales tienen un tipo de seguridad ligeramente diferente, puesto que un administrador de datos independiente controla el servicio Power BI de la nube nacional en nombre de Microsoft.

  Como alternativa, los clientes también pueden configurar un inquilino en una región específica, pero estos inquilinos no tienen un administrador de datos independiente de Microsoft. Los precios de las nubes nacionales son diferentes del servicio Power BI comercial disponible con carácter general. Para obtener más información sobre la disponibilidad del servicio Power BI para nubes nacionales, vea [Nubes nacionales de Power BI](https://powerbi.microsoft.com/clouds/).

**¿Cómo trata Microsoft las conexiones de los clientes que tienen Power BI Premium suscripciones? ¿Son las conexiones distintas de las establecidas para el servicio Power BI no Premium?**

* Las conexiones que se establecen para los clientes con suscripciones de Power BI Premium implementan un proceso de autorización [de negocio a negocio (B2B) de Azure](/azure/active-directory/active-directory-b2b-what-is-azure-ad-b2b), mediante Azure Active Directory (AD) para habilitar el control de acceso y la autorización. Power BI controla las conexiones de los suscriptores de Power BI Premium a los recursos de Power BI Premium como haría con cualquier otro usuario de Azure AD.

## <a name="conclusion"></a>Conclusión

La arquitectura del servicio Power BI se basa en dos clústeres: el front-end web (WFE) y el back-end. El clúster WFE es responsable de la conexión inicial y la autenticación en el servicio de Power BI y, una vez realizada la autenticación, el back-end controla todas las interacciones de usuario siguientes. Power BI usa Azure Active Directory (AAD) para almacenar y administrar identidades de usuario, y administra el almacenamiento de datos y metadatos con Azure Blob y Azure SQL Database, respectivamente.

El almacenamiento y procesamiento de los datos en Power BI difiere en función de si se accede a los datos con DirectQuery, y también depende de si se trata de orígenes de datos locales o en la nube. Power BI también es capaz de aplicar la seguridad de nivel de rol (RLS) e interactúa con las puertas de enlace que proporcionan acceso a los datos locales.

## <a name="feedback-and-suggestions"></a>Comentarios y sugerencias

Agradecemos sus comentarios. Nos interesa conocer cualquier sugerencia de mejora, adiciones o aclaraciones de estas notas del producto u otro contenido relacionado con Power BI. Envíe sus sugerencias a [pbidocfeedback@microsoft.com](mailto:pbidocfeedback@microsoft.com) .

## <a name="additional-resources"></a>Recursos adicionales

Para obtener más información sobre Power BI, vea los recursos siguientes.

- [Grupos en Power BI](https://support.powerbi.com/knowledgebase/articles/654247)
- [Introducción a Power BI Desktop](https://support.powerbi.com/knowledgebase/articles/471664)
- [Información general sobre la API REST de Power BI](/rest/api/power-bi/)
- [Referencia de la API de Power BI](/rest/api/power-bi/)
- [Puerta de enlace de datos local](../connect-data/service-gateway-onprem.md)
- [Nubes nacionales de Power BI](https://powerbi.microsoft.com/clouds/)
- [Power BI Premium](https://aka.ms/pbipremiumwhitepaper)
- [Uso de Kerberos para el inicio de sesión único (SSO) de Power BI a orígenes de datos locales](../connect-data/service-gateway-sso-overview.md)