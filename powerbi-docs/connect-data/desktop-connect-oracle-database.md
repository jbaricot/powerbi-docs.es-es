---
title: Conexión a una base de datos de Oracle con Power BI Desktop
description: Pasos y descargas que se necesitan para conectar Oracle a Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: how-to
ms.date: 08/11/2020
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: f778b4f0c6572084598eb07df0e89b7a30aed7b1
ms.sourcegitcommit: d7145123133255d004b85ef8b20ca4977f0b843e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/11/2020
ms.locfileid: "88091604"
---
# <a name="connect-to-an-oracle-database-with-power-bi-desktop"></a>Conexión a una base de datos de Oracle con Power BI Desktop
Para conectarse a una base de datos de Oracle con Power BI Desktop, en el equipo donde se ejecute Power BI Desktop debe estar instalado el software cliente de Oracle correcto. El software cliente de Oracle que use depende de la versión que Power BI Desktop que haya instalado: 32 bits o 64 bits. También depende de la versión del servidor de Oracle.

Versiones de Oracle compatibles: 
- Oracle Server 9 y versiones posteriores
- Software de Oracle Data Access Client (ODAC) 11.2 y versiones posteriores

> [!NOTE]
> Si va a configurar una base de datos de Oracle para Power BI Desktop, una puerta de enlace de datos local o Power BI Report Server, consulte la información del artículo [Tipo de conexión de Oracle](https://docs.microsoft.com/sql/reporting-services/report-data/oracle-connection-type-ssrs?view=sql-server-ver15). 


## <a name="determining-which-version-of-power-bi-desktop-is-installed"></a>Determinación de versión instalada de Power BI Desktop
Para determinar la versión de Power BI Desktop instalada, seleccione **Archivo** > **Ayuda** > **Acerca de** y, luego, revise la línea **Versión**. En la siguiente imagen, hay instalada una versión de 64 bits de Power BI Desktop:

![Versión de Power BI Desktop](media/desktop-connect-oracle-database/connect-oracle-database_1.png)

## <a name="install-the-oracle-client"></a>Instalación del cliente de Oracle
- Para la versión de 32 bits de Power BI Desktop, [descargue e instale el cliente de Oracle de 32 bits](https://www.oracle.com/technetwork/topics/dotnet/utilsoft-086879.html).

- Para la versión de 64 bits de Power BI Desktop, [descargue e instale el cliente de Oracle de 64 bits](https://www.oracle.com/database/technologies/odac-downloads.html).

> [!NOTE]
> Elija una versión de Oracle Data Access Client (ODAC) que sea compatible con el servidor de Oracle. Por ejemplo, ODAC 12.x no siempre es compatible con la versión 9 de Oracle Server.
> Elija el instalador de Windows del cliente de Oracle.
> Durante la configuración del cliente de Oracle, asegúrese de habilitar *Configurar los proveedores de ODP.NET y/o Oracle para ASP.NET en el nivel de equipo* mediante la casilla correspondiente en el asistente para la instalación. Algunas versiones del asistente para clientes de Oracle activan la casilla de forma predeterminada y otras no. Asegúrese de que la casilla está activada para que Power BI pueda conectarse a la base de datos de Oracle.

## <a name="connect-to-an-oracle-database"></a>Conectarse a una base de datos de Oracle
Después de instalar el controlador cliente de Oracle que corresponda, puede conectarse a una base de datos de Oracle. Siga estos pasos para establecer la conexión:

1. Desde la pestaña **Inicio**, seleccione **Obtener datos**. 

2. En la ventana **Obtener datos** que aparece, seleccione **Más** (si es necesario), seleccione **Base de datos** > **Base de datos de Oracle** y después **Conectar**.
   
   ![Conexión a la base de datos Oracle](media/desktop-connect-oracle-database/connect-oracle-database_2.png)
3. En el cuadro de diálogo **Base de datos de Oracle** que aparece, proporcione el nombre del **servidor** y seleccione **Aceptar**. Si se requiere un SID, especifíquelo con el formato siguiente: *NombreDeServidor/SID*, donde *SID* es el nombre único de la base de datos. Si el formato *NombreDeServidor/SID* no funciona, use *NombreDeServidor/NombreDeServicio*, donde *NombreDeServicio* es el alias que se usa para conectarse.


   ![Escriba el nombre del servidor de Oracle](media/desktop-connect-oracle-database/connect-oracle-database_3.png)

   > [!NOTE]
   > Si está utilizando una base de datos local, o conexiones a bases de datos autónomas, es posible que deba colocar el nombre del servidor entre comillas para evitar errores de conexión. 
      
4. Si quiere importar datos con una consulta de base de datos nativa, incluya la consulta en el cuadro **Instrucción SQL**, que aparece al expandir la sección **Opciones avanzadas** del cuadro de diálogo **Base de datos de Oracle**.
   
   ![Expansión de Opciones avanzadas](media/desktop-connect-oracle-database/connect-oracle-database_4.png)


5. Una vez que haya escrito la información de la base de datos de Oracle en el cuadro de diálogo **Base de datos de Oracle** (incluida toda información opcional, como un SID o una consulta de base de datos nativa), seleccione **Aceptar** para conectarse.
5. Si la base de datos de Oracle necesita credenciales del usuario de la base de datos, ingréselas en el cuadro de diálogo cuando se le solicite hacerlo.


## <a name="troubleshooting"></a>Solución de problemas

Es posible que se produzcan varios errores en Oracle si la sintaxis de los nombres no es correcta o no está configurada correctamente:

* ORA-12154: TNS:no se ha podido resolver el identificador de conexión especificado.
* ORA-12514: TNS:el listener no conoce actualmente el servicio solicitado en el descriptor de conexión.
* ORA-12541: TNS:no hay ningún listener.
* ORA-12170: TNS:error de tiempo de espera de conexión.
* ORA-12504: TNS:el listener no ha recibido el SERVICE_NAME en CONNECT_DATA.

Estos errores podrían producirse si el cliente de Oracle no está instalado o no se ha configurado correctamente. Si está instalado, compruebe que el archivo tnsnames.ora esté configurado correctamente y que usa el parámetro net_service_name adecuado. También tendrá que asegurarse de que net_service_name sea el mismo en la máquina en donde se usa Power BI Desktop y la que ejecuta la puerta de enlace. Para obtener más información, vea [Instalación del cliente de Oracle](#install-the-oracle-client).

También es posible que encuentre un problema de compatibilidad entre la versión del servidor de Oracle y la de Oracle Data Access Client. Normalmente, le interesa que estas versiones coincidan, ya que algunas combinaciones son incompatibles. Por ejemplo, ODAC 12.x no es compatible con la versión 9 de Oracle Server.

Si ha descargado Power BI Desktop desde Microsoft Store, es posible que no pueda conectarse a bases de datos de Oracle debido a un problema con el controlador de Oracle. Si se produce este problema, el mensaje de error que se devuelve es: *Referencia a objeto no establecida*. Para solucionar el problema, siga uno de estos pasos:

* Descargue Power BI Desktop desde el [Centro de descarga](https://www.microsoft.com/download/details.aspx?id=58494) en lugar de Microsoft Store.

* Si quiere usar la versión disponible en Microsoft Store: en el equipo local, copie el archivo oraons.dll de _12.X.X\client_X_ en _12.X.X\client_X\bin_, donde _X_ representa los números de versión y directorio.

Si ve el mensaje de error *Referencia de objeto no establecida* en Power BI Gateway al conectarse a una base de datos de Oracle, siga las instrucciones de [Administración del origen de datos: Oracle](service-gateway-onprem-manage-oracle.md).

Si usa Power BI Report Server, consulte las instrucciones del artículo [Tipo de conexión de Oracle](https://docs.microsoft.com/sql/reporting-services/report-data/oracle-connection-type-ssrs?view=sql-server-ver15).
