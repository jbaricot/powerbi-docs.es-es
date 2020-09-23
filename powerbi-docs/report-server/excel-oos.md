---
title: 'Hospedaje de libros de Excel mediante Office Online Server (OOS): Power BI Report Server'
description: Además de ver informes de Power BI en el portal web, Power BI Report Server puede hospedar libros de Excel mediante Office Online Server (OOS).
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: how-to
ms.date: 05/14/2020
ms.openlocfilehash: 90061cec87bae4b65d347617dacc2863052a07ce
ms.sourcegitcommit: 9350f994b7f18b0a52a2e9f8f8f8e472c342ea42
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/22/2020
ms.locfileid: "90861162"
---
# <a name="configure-your-report-server-to-host-excel-workbooks-using-office-online-server-oos"></a>Configuración de un servidor de informes para hospedar libros de Excel mediante Office Online Server (OOS)

Además de ver informes de Power BI en el portal web, Power BI Report Server puede hospedar libros de Excel mediante [Office Online Server (OOS)](/officeonlineserver/office-online-server-overview). El servidor de informes se convierte en una única ubicación para publicar y ver el contenido de autoservicio de Microsoft BI.

![Informes de Excel vistos desde el portal web del servidor de informes](media/excel-oos/excel-in-pbirs.png)

## <a name="prepare-server-to-run-office-online-server"></a>Preparación de un servidor para que ejecute Office Online Server

Realice estos procedimientos en el servidor que va a ejecutar Office Online Server. Este servidor debe ser Windows Server 2012 R2 o Windows Server 2016. Windows Server 2016 requiere la versión de abril de 2017 de Office Online Server, o cualquier versión posterior.

### <a name="install-prerequisite-software-for-office-online-server"></a>Instalación del software necesario para Office Online Server

1. Abra el símbolo del sistema de Windows PowerShell como administrador y ejecute este comando para instalar los roles y servicios necesarios.

    **Windows Server 2012 R2:**

    ```powershell
    Add-WindowsFeature Web-Server,Web-Mgmt-Tools,Web-Mgmt-Console,Web-WebServer,Web-Common-Http,Web-Default-Doc,Web-Static-Content,Web-Performance,Web-Stat-Compression,Web-Dyn-Compression,Web-Security,Web-Filtering,Web-Windows-Auth,Web-App-Dev,Web-Net-Ext45,Web-Asp-Net45,Web-ISAPI-Ext,Web-ISAPI-Filter,Web-Includes,InkandHandwritingServices,NET-Framework-Features,NET-Framework-Core,NET-HTTP-Activation,NET-Non-HTTP-Activ,NET-WCF-HTTP-Activation45,Windows-Identity-Foundation,Server-Media-Foundation
    ```

    **Windows Server 2016:**

    ```powershell
    Add-WindowsFeature Web-Server,Web-Mgmt-Tools,Web-Mgmt-Console,Web-WebServer,Web-Common-Http,Web-Default-Doc,Web-Static-Content,Web-Performance,Web-Stat-Compression,Web-Dyn-Compression,Web-Security,Web-Filtering,Web-Windows-Auth,Web-App-Dev,Web-Net-Ext45,Web-Asp-Net45,Web-ISAPI-Ext,Web-ISAPI-Filter,Web-Includes,NET-Framework-Features,NET-Framework-45-Features,NET-Framework-Core,NET-Framework-45-Core,NET-HTTP-Activation,NET-Non-HTTP-Activ,NET-WCF-HTTP-Activation45,Windows-Identity-Foundation,Server-Media-Foundation
    ```

    Si se le solicita, reinicie el servidor.
2. Instale el software siguiente:

   * [.NET Framework 4.5.2](https://go.microsoft.com/fwlink/p/?LinkId=510096)
   * [Paquetes redistribuibles de Visual C++ para Visual Studio 2013](https://www.microsoft.com/download/details.aspx?id=40784)
   * [Visual C++ Redistributable para Visual Studio 2015](https://go.microsoft.com/fwlink/p/?LinkId=620071)
   * [Microsoft.IdentityModel.Extention.dll](https://go.microsoft.com/fwlink/p/?LinkId=620072)

### <a name="install-office-online-server"></a>Instalación de Office Online Server

Si planea usar las características de Excel Online que utilizan el acceso a datos externos (por ejemplo, Power Pivot), tenga en cuenta que Office Online Server debe residir en el mismo bosque de Active Directory que sus usuarios, así como los orígenes de datos externos a los que planea acceder mediante la autenticación basada en Windows.

1. Descargue Office Online Server del [Centro de servicios de licencias por volumen (VLSC)](https://go.microsoft.com/fwlink/p/?LinkId=256561). La descarga se encuentra en los productos de Office en el portal de VLSC. Para fines de desarrollo, puede descargar OOS de las descargas de suscriptor de MSDN.
2. Ejecute Setup.exe.
3. En la página **Lea los Términos de licencia del software de Microsoft**, seleccione **Acepto los términos de este contrato** y seleccione **Continuar**.
4. En la página **Elegir una ubicación de archivos**, seleccione la carpeta donde quiera que se instalen los archivos de Office Online Server (por ejemplo, C:\Archivos de programa\Microsoft Office Web Apps\*) y haga clic en **Instalar ahora**. Si la carpeta que ha especificado no existe, el programa de instalación la crea automáticamente.

    Se recomienda instalar Office Online Server en la unidad del sistema.

5. Cuando el programa de instalación finalice la instalación de Office Online Server, seleccione **Cerrar**.

### <a name="install-language-packs-for-office-web-apps-server-optional"></a>Instalación de los paquetes de idioma de Office Web Apps Server (opcional)

Los paquetes de idioma de Office Online Server permiten a los usuarios ver archivos de Office basados en web en varios idiomas.

Para instalar los paquetes de idioma, siga estos pasos.

1. Descargue los paquetes de idioma de Office Online Server del [Centro de descarga de Microsoft](https://go.microsoft.com/fwlink/p/?LinkId=798136).
2. Ejecute **wacserverlanguagepack.exe**.
3. En el Asistente del paquete de idioma de Office Online Server, en la página **Lea los Términos de licencia del software de Microsoft**, seleccione **Acepto los términos de este contrato** y seleccione **Continuar**.
4. Cuando el programa de instalación finalice la instalación de Office Online Server, seleccione **Cerrar**.

## <a name="deploy-office-online-server"></a>Implementación de Office Online Server

### <a name="create-the-office-online-server-farm-https"></a>Creación de la granja de Office Online Server (HTTPS)

Use el comando New-OfficeWebAppsFarm para crear una nueva granja de Office Online Server que consta de un solo servidor, como se muestra en el ejemplo siguiente.

```powershell
New-OfficeWebAppsFarm -InternalUrl "https://server.contoso.com" -ExternalUrl "https://wacweb01.contoso.com" -CertificateName "OfficeWebApps Certificate"
```

**Parámetros**

* **–InternalURL** es el nombre de dominio completo (FQDN) del servidor que ejecuta Office Online Server, como `https://servername.contoso.com`.
* **– ExternalURL** es el FQDN al que se puede acceder en Internet.
* **– CertificateName** es el nombre descriptivo del certificado.

### <a name="create-the-office-online-server-farm-http"></a>Creación de la granja de Office Online Server (HTTP)

Use el comando New-OfficeWebAppsFarm para crear una nueva granja de Office Online Server que consta de un solo servidor, como se muestra en el ejemplo siguiente.

```powershell
New-OfficeWebAppsFarm -InternalURL "https://servername" -AllowHttp
```

**Parámetros**

* **– InternalURL** es el nombre del servidor que ejecuta Office Online Server, como `https://servername`.
* **– AllowHttp** configura la granja para que use HTTP.

### <a name="verify-that-the-office-online-server-farm-was-created-successfully"></a>Comprobación de que la granja de Office Online Server se ha creado correctamente

Una vez que se ha creado la granja, sus detalles se muestran en el símbolo del sistema de Windows PowerShell. Para comprobar que Office Online Server se ha instalado y configurado correctamente, use un explorador web para acceder a la dirección URL de detección de Office Online Server, como se muestra en el ejemplo siguiente. La dirección URL de detección es el parámetro de *InternalUrl* que especificó al configurar la granja de Office Online Server, seguido de */hospedaje/detección*, por ejemplo:

```
<InternalUrl>/hosting/discovery
```

Si Office Online Server funciona según lo previsto, debería ver un XML de detección del Protocolo de interfaz de plataforma abierta de aplicación web (WOPI)-XML en el explorador web. Las primeras líneas de dicho archivo deben ser similares a estas:

```xml
<?xml version="1.0" encoding="utf-8" ?> 
<wopi-discovery>
<net-zone name="internal-http">
<app name="Excel" favIconUrl="<InternalUrl>/x/_layouts/images/FavIcon_Excel.ico" checkLicense="true">
<action name="view" ext="ods" default="true" urlsrc="<InternalUrl>/x/_layouts/xlviewerinternal.aspx?<ui=UI_LLCC&><rs=DC_LLCC&>" /> 
<action name="view" ext="xls" default="true" urlsrc="<InternalUrl>/x/_layouts/xlviewerinternal.aspx?<ui=UI_LLCC&><rs=DC_LLCC&>" /> 
<action name="view" ext="xlsb" default="true" urlsrc="<InternalUrl>/x/_layouts/xlviewerinternal.aspx?<ui=UI_LLCC&><rs=DC_LLCC&>" /> 
<action name="view" ext="xlsm" default="true" urlsrc="<InternalUrl>/x/_layouts/xlviewerinternal.aspx?<ui=UI_LLCC&><rs=DC_LLCC&>" /> 
```

### <a name="configure-excel-workbook-maximum-size"></a>Configuración del tamaño máximo del libro de Excel

El tamaño máximo de todos los archivos de Power BI Report Server es 100 MB. Para no superarlo, es preciso establecerlo manualmente en OOS.

```powershell
Set-OfficeWebAppsFarm -ExcelWorkbookSizeMax 100
```

## <a name="using-effectiveusername-with-analysis-services"></a>Uso de EffectiveUserName con Analysis Services

Para permitir dinámicas a Analysis Services en el caso de las conexiones de un libro de Excel que hacen uso de EffectiveUserName. Para que OOS use EffectiveUserName, tendrá que agregar la cuenta de equipo del servidor de OOS como administrador para la instancia de Analysis Services. Para ello, se necesita Management Studio para SQL Server 2016, o cualquier versión posterior.

Actualmente, en los libros de Excel solo se admiten conexiones de Analysis Services incrustadas. Será preciso que la cuenta del usuario tenga permiso para conectarse a Analysis Services, ya que la capacidad de que el usuario haga de proxy no está disponible.

Ejecute los siguientes comandos de PowerShell en el servidor de OOS.

```powershell
Set-OfficeWebAppsFarm -ExcelUseEffectiveUserName:$true
Set-OfficeWebAppsFarm -ExcelAllowExternalData:$true
Set-OfficeWebAppsFarm -ExcelWarnOnDataRefresh:$false
```

## <a name="configure-a-power-pivot-instance-for-data-models"></a>Configuración de una instancia de Power Pivot en los modelos de datos

La instalación de una instancia del modo Power Pivot de Analysis Services le permite trabajar con libros de Excel que usan Power Pivot. Asegúrese de que el nombre de la instancia es *POWERPIVOT*. Agregue la cuenta de equipo del servidor OOS como administrador, para la instancia del modo Power Pivot de Analysis Services. Para ello, se necesita Management Studio para SQL Server 2016, o cualquier versión posterior.

Para que OOS use la instancia del modo Power Pivot, ejecute el siguiente comando.

```powershell
New-OfficeWebAppsExcelBIServer -ServerId <server_name>\POWERPIVOT
```

Si no admitía datos externos, desde el paso de Analysis Services anterior, ejecute el siguiente comando.

```powershell
Set-OfficeWebAppsFarm -ExcelAllowExternalData:$true
```

### <a name="firewall-considerations"></a>Consideraciones del firewall

Para evitar problemas de firewall, es posible que tenga que abrir los puertos 2382 y 2383. También puede agregar el archivo *msmdsrv.exe*, para la instancia de PowerPivot, como una directiva del firewall de aplicaciones.

## <a name="configure-power-bi-report-server-to-use-the-oos-server"></a>Configuración de Power BI Report Server para que use el servidor de OOS

En la página **General** de **Configuración del sitio**, escriba la dirección URL de detección de OOS. La dirección URL de detección de OOS es *InternalUrl*, que se usa al implementar el servidor de OOS, seguido de */hospedaje/detección*. Por ejemplo, `https://servername/hosting/discovery`, para HTTP. Y `https://server.contoso.com/hosting/discovery` para HTTPS.

Para llegar a **Configuración del sitio**, seleccione el **icono del engranaje** en la parte superior derecha y seleccione **Configuración del sitio**.

Los usuarios con el rol de **administrador del sistema** son los únicos que ven la configuración de la dirección URL de detección de Office Online Server.

![Configuración del sitio para Power BI Report Server.](media/excel-oos/reportserver-site-settings.png)

Después de escribir la dirección URL de detección y seleccionar **Aplicar**, al seleccionar un libro de Excel en el portal web, este debería mostrarse en dicho portal.

## <a name="limitations-and-considerations"></a>Limitaciones y consideraciones

- Tendrá la funcionalidad de solo lectura en los libros.
- La actualización programada no se admite para los libros de Excel en Power BI Report Server.

## <a name="next-steps"></a>Pasos siguientes

[Información general de administrador](admin-handbook-overview.md)  
[Instalar un servidor de informes de Power BI](install-report-server.md)  
[Descarga del Generador de informes](https://www.microsoft.com/download/details.aspx?id=53613)  
[Descargar SQL Server Data Tools (SSDT)](/sql/ssdt/download-sql-server-data-tools-ssdt)

¿Tiene más preguntas? [Pruebe a preguntar a la comunidad de Power BI](https://community.powerbi.com/)