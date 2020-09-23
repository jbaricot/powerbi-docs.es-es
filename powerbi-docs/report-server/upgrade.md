---
title: Actualización de Power BI Report Server
description: Aprenda a actualizar un servidor de informes de Power BI.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: how-to
ms.custom: ''
ms.date: 09/05/2017
ms.openlocfilehash: cb2a5ede49acb218450174bbf77388be5c504617
ms.sourcegitcommit: 9350f994b7f18b0a52a2e9f8f8f8e472c342ea42
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/22/2020
ms.locfileid: "90861737"
---
# <a name="upgrade-power-bi-report-server"></a>Actualización de Power BI Report Server

Aprenda a actualizar un servidor de informes de Power BI.

 **Descarga** ![descarga](media/upgrade/download.png "descarga")

Para descargar el servidor de informes de Power BI y Power BI Desktop optimizado para el servidor de informes de Power BI, vaya a [Publicar informes en almacenamiento local con el servidor de informes de Power BI](https://powerbi.microsoft.com/report-server/).

## <a name="before-you-begin"></a>Antes de empezar

Antes de actualizar un servidor de informes, se recomienda que realice los pasos siguientes para hacer copia de seguridad del servidor de informes.

### <a name="backing-up-the-encryption-keys"></a>Copia de seguridad de las claves de cifrado

Debe realizar una copia de seguridad de las claves de cifrado cuando configura la instalación de un servidor de informes por primera vez. También debe realizar una copia de seguridad de las claves cada vez que cambie la identidad de las cuentas de servicio o cambie el nombre del equipo. Para obtener más información, vea [Hacer copia de seguridad y restaurar claves de cifrado de Reporting Services](/sql/reporting-services/install-windows/ssrs-encryption-keys-back-up-and-restore-encryption-keys).

### <a name="backing-up-the-report-server-databases"></a>Copia de seguridad de las bases de datos del servidor de informes

Dado que un servidor de informes es un servidor sin estado, todos los datos de aplicación se almacenan en las bases de datos **reportserver** y **reportservertempdb** que se ejecutan en una instancia del Motor de base de datos de SQL Server. Puede hacer una copia de seguridad de las bases de datos **reportserver** y **reportservertempdb** con alguno de los métodos admitidos para copias de seguridad de bases de datos de SQL Server. Éstas son algunas de las recomendaciones específicas de las bases de datos del servidor de informes:

* Use el modelo de recuperación completa para realizar la copia de seguridad de la base de datos **reportserver**.
* Use el modelo de recuperación simple para realizar la copia de seguridad de la base de datos **reportservertempdb**.
* Puede utilizar distintas programaciones de copia de seguridad para cada base de datos. La copia de seguridad de **reportservertempdb** solo se realiza para evitar tener que volver a crearla en caso de un error de hardware. Si se produce un error de hardware, no es necesario recuperar los datos de **reportservertempdb**, pero sí se requiere la estructura de la tabla. Si se pierde **reportservertempdb**, la única forma de recuperarla es volver a crear la base de datos del servidor de informes. Si se vuelve a crear **reportservertempdb**, es importante que su nombre sea el mismo que el de la base de datos primaria del servidor de informes.

Para obtener más información sobre copia de seguridad y recuperación de bases de datos relacionales de SQL Server, vea [Realizar copias de seguridad y restaurar bases de datos de SQL Server](/sql/relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases).

### <a name="backing-up-the-configuration-files"></a>Copia de seguridad de los archivos de configuración

El servidor de informes de Power BI usa archivos de configuración para almacenar la configuración de la aplicación. Se debe realizar una copia de seguridad de estos archivos la primera vez que se configura el servidor y después de implementar extensiones personalizadas. Debe realizar una copia de seguridad de los siguientes archivos:

* config.json
* RSHostingService.exe.config
* RSReportServer.config
* Rssvrpolicy.config
* Reportingservicesservice.exe.config
* Web.config para las aplicaciones ASP.NET del servidor de informes
* Machine.config para ASP.NET

## <a name="upgrade-the-report-server"></a>Actualización del servidor de informes

Es sencillo actualizar el servidor de informes de Power BI. Solo se necesitan unos cuantos pasos para instalar los archivos.

1. Busque la ubicación de PowerBIReportServer.exe e inicie el instalador.

2. Seleccione **Upgrade Power BI Report Server** (Actualizar servidor de informes de Power BI).

    ![Actualización de Power BI Report Server](media/upgrade/reportserver-upgrade1.png "Actualización de Power BI Report Server")

3. Lea y acepte los términos y condiciones de la licencia y después seleccione **Actualizar**.

    ![Contrato de licencia](media/upgrade/reportserver-upgrade-eula.png "Contrato de licencia")

4. Después de una actualización correcta, seleccione **Configure Report Server** (Configurar servidor de informes) para iniciar el Administrador de configuración de Reporting Services o seleccione **Cerrar** para salir del instalador.

    ![Actualizar configuración](media/upgrade/reportserver-upgrade-configure.png)

## <a name="upgrade-power-bi-desktop"></a>Actualización de Power BI Desktop

Después de actualizar el servidor de informes, deseará asegurarse de que los autores de informes de Power BI actualicen a la versión de Power BI Desktop optimizado para el servidor de informes de Power BI que coincida con el servidor.

## <a name="next-steps"></a>Pasos siguientes

* [Información general de administrador](admin-handbook-overview.md)  
* [Instalar Power BI Desktop optimizado para el servidor de informes de Power BI](install-powerbi-desktop.md)  
* [Verify a Reporting Services Installation](/sql/reporting-services/install-windows/verify-a-reporting-services-installation) (Comprobar una instalación de Reporting Services)  
* [Configure the report server service account](/sql/reporting-services/install-windows/configure-the-report-server-service-account-ssrs-configuration-manager) (Configurar la cuenta de servicio del servidor de informes)  
* [Configure report server URLs](/sql/reporting-services/install-windows/configure-report-server-urls-ssrs-configuration-manager) (Configurar direcciones URL del servidor de informes)  
* [Configure a report server database connection](/sql/reporting-services/install-windows/configure-a-report-server-database-connection-ssrs-configuration-manager) (Configurar una conexión de base de datos del servidor de informes)  
* [Inicializar un servidor de informes](/sql/reporting-services/install-windows/ssrs-encryption-keys-initialize-a-report-server)  
* [Configurar conexiones SSL en un servidor de informes](/sql/reporting-services/security/configure-ssl-connections-on-a-native-mode-report-server)  
* [Configure windows service accounts and permissions](/sql/database-engine/configure-windows/configure-windows-service-accounts-and-permissions) (Configurar permisos y cuentas del servicio de Windows)  
* [Compatibilidad del explorador con el servidor de informes de Power BI](browser-support.md)

¿Tiene más preguntas? [Pruebe a preguntar a la comunidad de Power BI](https://community.powerbi.com/)