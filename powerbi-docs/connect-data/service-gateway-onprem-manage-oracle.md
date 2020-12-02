---
title: 'Administrar el origen de datos: Oracle'
description: Cómo administrar la puerta de enlace de datos local y los orígenes de datos de Oracle que pertenecen a esa puerta de enlace.
author: arthiriyer
ms.author: arthii
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: how-to
ms.date: 07/15/2019
LocalizationGroup: Gateways
ms.openlocfilehash: 0fdf34841b06fcbb4ad2eab8af5945214ac45932
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/01/2020
ms.locfileid: "96402326"
---
# <a name="manage-your-data-source---oracle"></a>Administrar el origen de datos: Oracle

[!INCLUDE [gateway-rewrite](../includes/gateway-rewrite.md)]

Después de [instalar la puerta de enlace de datos local](/data-integration/gateway/service-gateway-install), tendrá que [agregar orígenes de datos](service-gateway-data-sources.md#add-a-data-source) que se puedan usar con ella. En este artículo se describe cómo trabajar con puertas de enlace y orígenes de datos de Oracle para la actualización programada o para DirectQuery.

## <a name="connect-to-an-oracle-database"></a>Conectarse a una base de datos de Oracle
Para conectarse a una base de datos de Oracle con la puerta de enlace de datos local, en el equipo donde se ejecute la puerta de enlace debe estar instalado el software cliente de Oracle correcto. El software cliente de Oracle que use dependerá de la versión del servidor de Oracle, pero siempre coincidirá con la puerta de enlace de 64 bits.

Versiones de Oracle compatibles: 
- Oracle Server 9 y versiones posteriores
- Software de Oracle Data Access Client (ODAC) 11.2 y versiones posteriores

## <a name="install-the-oracle-client"></a>Instalación del cliente de Oracle
- [Descargue e instale el cliente de Oracle de 64 bits](https://www.oracle.com/database/technologies/odac-downloads.html).

> [!NOTE]
> Elija una versión de Oracle Data Access Client (ODAC) que sea compatible con el servidor de Oracle. Por ejemplo, ODAC 12.x no siempre es compatible con la versión 9 de Oracle Server.
> Elija el instalador de Windows del cliente de Oracle.
> Durante la configuración del cliente de Oracle, asegúrese de habilitar *Configurar los proveedores de ODP.NET y/o Oracle para ASP.NET en el nivel de equipo* mediante la casilla correspondiente en el asistente para la instalación. Algunas versiones del asistente para clientes de Oracle activan la casilla de forma predeterminada y otras no. Asegúrese de que la casilla está activada para que Power BI pueda conectarse a la base de datos de Oracle.
 
Una vez que se ha instalado el cliente y después de configurar ODAC correctamente, se recomienda usar Power BI Desktop u otro cliente de prueba para comprobar la instalación y configuración correctas en la puerta de enlace.

## <a name="add-a-data-source"></a>Elegir un origen de datos

Para más información sobre cómo agregar un origen de datos, consulte [Adición de un origen de datos](service-gateway-data-sources.md#add-a-data-source). Como **Tipo de origen de datos**, seleccione **Oracle**.

![Adición del origen de datos de Oracle](media/service-gateway-onprem-manage-oracle/data-source-oracle.png)

Cuando haya seleccionado el tipo de origen de datos Oracle, rellene su información, que incluye **Servidor** y **Base de datos**. 

Como **Método de autenticación** puede elegir **Windows** o **Básico**. Si va a usar una cuenta creada en Oracle, elija **Básico** en lugar de Windows. A continuación, escriba las credenciales que se van a usar con este origen de datos.

> [!NOTE]
> Todas las consultas que se realicen al origen de datos se ejecutarán con estas credenciales. Para más información sobre cómo se almacenan las credenciales, vea [Almacenamiento de credenciales cifradas en la nube](service-gateway-data-sources.md#store-encrypted-credentials-in-the-cloud).

![Rellene la configuración del origen de datos](media/service-gateway-onprem-manage-oracle/data-source-oracle2.png)

Después de rellenar todo, seleccione **Agregar**. Ahora puede usar este origen de datos para la actualización programada o para DirectQuery en un servidor de Oracle local. Si se realiza correctamente, verá el mensaje *Se conectó correctamente*.

![Representación del estado de conexión](media/service-gateway-onprem-manage-oracle/datasourcesettings4.png)

### <a name="advanced-settings"></a>Configuración avanzada

Opcionalmente, puede configurar el nivel de privacidad del origen de datos. Esta configuración controla cómo se pueden combinar los datos. Solo se usa para la actualización programada. La configuración del nivel de privacidad no se aplica a DirectQuery. Para más información sobre los niveles de privacidad del origen de datos, vea [Niveles de privacidad (Power Query)](https://support.office.com/article/Privacy-levels-Power-Query-CC3EDE4D-359E-4B28-BC72-9BEE7900B540).

![Establecimiento del nivel de privacidad](media/service-gateway-onprem-manage-oracle/datasourcesettings9.png)

## <a name="use-the-data-source"></a>Uso del origen de datos

Después de haber creado el origen de datos, estará disponible para usarse con conexiones DirectQuery, o bien a través de una actualización programada.

> [!WARNING]
> El nombre del servidor y de la base de datos deben coincidir entre Power BI Desktop y el origen de datos dentro de la puerta de enlace de datos local.

El vínculo entre el conjunto de datos y el origen de datos dentro de la puerta de enlace se basa en el nombre del servidor y en el nombre de la base de datos. Estos nombres deben coincidir. Por ejemplo, si proporciona una dirección IP para el nombre del servidor, dentro de Power BI Desktop, tendrá que usar la dirección IP del origen de datos dentro de la configuración de la puerta de enlace. Este nombre también tiene que coincidir con un alias definido en el archivo tnsnames.ora. Para obtener más información sobre el archivo tnsnames.ora, vea [Instalación del cliente de Oracle](#install-the-oracle-client).

Este requisito se aplica tanto a DirectQuery como a la actualización programada.

### <a name="use-the-data-source-with-directquery-connections"></a>Uso del origen de datos con conexiones de DirectQuery

Asegúrese de que el nombre del servidor y de la base de datos coinciden entre Power BI Desktop y el origen de datos configurado para la puerta de enlace. También tiene que asegurarse de que el usuario aparece en la pestaña **Usuarios** del origen de datos para publicar conjuntos de datos de DirectQuery. La selección para DirectQuery se produce dentro de Power BI Desktop al importar los datos por primera vez. Para obtener más información sobre cómo usar DirectQuery, vea el artículo sobre el [uso de DirectQuery en Power BI Desktop](desktop-use-directquery.md).

Después de publicar, ya sea desde Power BI Desktop o desde **Obtener datos**, los informes deben empezar a funcionar. La conexión puede tardar varios minutos en poderse usar después de crear el origen de datos dentro de la puerta de enlace.

### <a name="use-the-data-source-with-scheduled-refresh"></a>Uso del origen de datos con la actualización programada

Si aparece en la pestaña **Usuarios** del origen de datos configurado dentro de la puerta de enlace y los nombres del servidor y de la base de datos coinciden, verá la puerta de enlace como una opción para usar con la actualización programada.

![Representación de los usuarios](media/service-gateway-onprem-manage-oracle/powerbi-gateway-enterprise-schedule-refresh.png)

## <a name="troubleshooting"></a>Solución de problemas

Es posible que se produzcan varios errores en Oracle si la sintaxis de los nombres no es correcta o no está configurada correctamente:

* ORA-12154: TNS:no se ha podido resolver el identificador de conexión especificado.
* ORA-12514: TNS:el listener no conoce actualmente el servicio solicitado en el descriptor de conexión.
* ORA-12541: TNS:no hay ningún listener.
* ORA-12170: TNS:error de tiempo de espera de conexión.
* ORA-12504: TNS:el listener no ha recibido el SERVICE_NAME en CONNECT_DATA.

Estos errores podrían producirse si el cliente de Oracle no está instalado o no se ha configurado correctamente. Si está instalado, compruebe que el archivo tnsnames.ora esté configurado correctamente y que usa el parámetro net_service_name adecuado. También tendrá que asegurarse de que net_service_name sea el mismo en la máquina en donde se usa Power BI Desktop y la que ejecuta la puerta de enlace. Para obtener más información, vea [Instalación del cliente de Oracle](#install-the-oracle-client).

También es posible que encuentre un problema de compatibilidad entre la versión del servidor de Oracle y la de Oracle Data Access Client. Normalmente, le interesa que estas versiones coincidan, ya que algunas combinaciones son incompatibles. Por ejemplo, ODAC 12.x no es compatible con la versión 9 de Oracle Server.

Para diagnosticar problemas de conectividad entre el servidor de origen de datos y el equipo de puerta de enlace, se recomienda instalar un cliente (como Power BI Desktop u Oracle ODBC Test) en el equipo de puerta de enlace. Puede usar el cliente para comprobar la conectividad con el servidor de origen de datos.

Para obtener más información sobre la solución de problemas relacionados con la puerta de enlace, vea [Solución de problemas con la puerta de enlace de datos local](/data-integration/gateway/service-gateway-tshoot).

## <a name="next-steps"></a>Pasos siguientes

* [Solución de problemas de puertas de enlace: Power BI](service-gateway-onprem-tshoot.md)
* [Power BI Premium](../admin/service-premium-what-is.md)

¿Tiene más preguntas? Pruebe a preguntar a la [comunidad de Power BI](https://community.powerbi.com/).
