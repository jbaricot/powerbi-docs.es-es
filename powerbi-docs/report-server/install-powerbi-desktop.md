---
title: Instalación de Power BI Desktop para Power BI Report Server
description: Más información sobre cómo instalar Power BI Desktop para Power BI Report Server
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: how-to
ms.date: 10/16/2020
ms.openlocfilehash: 068d4a025bda878899e2d54f93bc56eaea336f3e
ms.sourcegitcommit: 7ed995eed0fd6e718748accf87bae384211cd95d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/29/2021
ms.locfileid: "99044089"
---
# <a name="install-power-bi-desktop-for-power-bi-report-server"></a>Instalación de Power BI Desktop para Power BI Report Server

Para crear informes de Power BI para Power BI Report Server, tendrá que descargar e instalar la versión de Power BI Desktop optimizada para Power BI Report Server. Esta es una versión de Power BI Desktop distinta de la que se usa con el servicio Power BI. Por ejemplo, en la versión de Power BI Desktop para el servicio Power BI se incluyen características en vista previa. Estas características no se incluyen en la versión de Power BI Report Server hasta que estén disponibles con carácter general. Es necesario usar esta versión para asegurarse de que el servidor de informes puede interactuar con una versión conocida de los informes y el modelo. 

No se preocupe. Puede instalar Power BI Desktop y Power BI Desktop para Power BI Report Server en paralelo en el mismo equipo.

## <a name="download-and-install-power-bi-desktop"></a>Descarga e instalación de Power BI Desktop

La mejor manera de asegurarse de que tiene la versión más actualizada de Power BI Desktop para Power BI Report Server es iniciarla en el portal web de su servidor de informes.

1. En el portal web de Report Server, seleccione la flecha **Descargar** > **Power BI Desktop**.

    ![Descarga de Power BI Desktop desde el portal web](media/install-powerbi-desktop/report-server-download-web-portal.png)

    O bien, vaya a la página principal de [Power BI Report Server](https://powerbi.microsoft.com/report-server/) y seleccione **Opciones avanzadas de descarga**.

2. En la página del Centro de descarga, seleccione un idioma y después **Descargar**.

3. En función de su equipo, seleccione: 

    - **PBIDesktopRS.msi** (versión de 32 bits).
    - **PBIDesktopRS_x64.msi** (versión de 64 bits).

1. Después de descargar el instalador, ejecute el Asistente para instalación de Power BI Desktop.

2. Al final del proceso de instalación, seleccione **Iniciar Power BI Desktop**.

    Se inicia automáticamente y está listo para funcionar.

## <a name="verify-youre-using-the-correct-version"></a>Comprobación relativa al uso de una versión correcta
Comprobar que esté usando la versión correcta de Power BI Desktop es muy sencillo: solo tiene que echar un vistazo a la pantalla de inicio o a la barra de título de Power BI Desktop. Puede ver que tiene la versión correcta porque aparece **Power BI Desktop (enero de 2021)** o posterior en la barra de título. Además, los colores del logotipo de Power BI aparecen invertidos, es decir, amarillo sobre negro en lugar de negro sobre amarillo.

![Power BI Desktop, enero de 2021](media/install-powerbi-desktop/power-bi-report-server-desktop.png)

La versión de Power BI Desktop para el servicio Power BI no indica el mes ni el año en la barra de título.

## <a name="file-extension-association"></a>Asociación de extensión de archivo
Imagine que ha instalado Power BI Desktop y Power BI Desktop para Power BI Report Server en el mismo equipo. La instalación más reciente de Power BI Desktop tiene la asociación de archivos con los archivos .pbix. Así pues, al hacer doble clic en un archivo .pbix, se iniciará la versión de Power BI Desktop que haya instalado más recientemente.

Si tiene Power BI Desktop e instala Power BI Desktop para Power BI Report Server, todos los archivos .pbix se abrirán en esta última versión de forma predeterminada. Si quiere que Power BI Desktop sea la opción predeterminada para abrir un archivo .pbix, reinstale [Power BI Desktop desde Microsoft Store](https://aka.ms/pbidesktopstore).

Siempre puede abrir la versión de Power BI Desktop que desea usar en primer lugar. Y, después, abra el archivo desde Power BI Desktop.

Esta es la manera más segura de abrir siempre la versión correcta de Power BI Desktop. Empiece a editar un informe de Power BI desde Power BI Report Server, o bien puede crearlo desde el servicio Power BI.

## <a name="considerations-and-limitations"></a>Consideraciones y limitaciones

Los informes de Power BI de Power BI Report Server del servicio Power BI (`https://app.powerbi.com`) y de las aplicaciones móviles de Power BI actúan prácticamente igual, pero hay algunas características diferentes.

### <a name="selecting-a-language"></a>Selección de un idioma

En el caso de Power BI Desktop para Power BI Report Server, el idioma se selecciona al instalar la aplicación. Después no se puede cambiar, pero se puede instalar una versión en otro idioma.

### <a name="report-visuals-in-a-browser"></a>Objetos visuales de informe en un explorador

Los informes de Power BI Report Server admiten casi todas las visualizaciones, incluidos los objetos visuales de Power BI. Los informes del servidor de informes de Power BI no admiten:

* Objetos visuales de R
* Rutas de navegación
* Características de la versión preliminar de Power BI Desktop

### <a name="reports-in-the-power-bi-mobile-apps"></a>Informes en las aplicaciones móviles de Power BI

Los informes del servidor de informes de Power BI admiten toda la funcionalidad básica en las [aplicaciones móviles de Power BI](../consumer/mobile/mobile-apps-for-mobile-devices.md), lo que incluye:

* [Diseño del informe en el teléfono](../create-reports/desktop-create-phone-report.md): puede optimizar un informe para las aplicaciones móviles de Power BI. En teléfonos móviles, los informes optimizados presentan una disposición especial y el icono ![Icono de diseño de informes en el teléfono](media/install-powerbi-desktop/power-bi-rs-mobile-optimized-icon.png).
  
    ![Informe optimizado para teléfonos](media/install-powerbi-desktop/power-bi-rs-mobile-optimized-report.png)

Los informes del servidor de informes de Power BI no admiten estas características en las aplicaciones móviles de Power BI:

* Objetos visuales de R
* Objetos visuales de Power BI
* Rutas de navegación
* Filtrado geográfico o códigos de barras

### <a name="custom-security"></a>Seguridad personalizada

Power BI Desktop para Power BI Report Server no admite la seguridad personalizada. Si la instancia de Power BI Report Server se configura con una extensión de seguridad personalizada, no puede guardar un informe de Power BI desde Power BI Desktop (optimizado para Power BI Report Server) en la instancia de Power BI Report Server. Tendrá que guardar el archivo de informe .pbix de Power BI Desktop y cargarlo al sitio del portal de Power BI Report Server.

### <a name="saving-reports-to-a-power-bi-report-server-in-a-different-domain"></a>Guardado de informes en una instancia de Power BI Report Server en otro dominio

Cuando se guarda un informe de Power BI en Power BI Report Server, se usan las credenciales de Windows. No se puede guardar directamente en un servidor de informes de otro dominio con las credenciales de Windows. Puede usar un explorador web para ver el servidor de informes y, en su lugar, cargar manualmente el archivo desde el equipo.

## <a name="next-steps"></a>Pasos siguientes

Una vez que Power BI Desktop se ha instalado, puede empezar a crear informes de Power BI.

[Creación de un informe de Power BI para Power BI Report Server](quickstart-create-powerbi-report.md)  
[¿Qué es Power BI Report Server?](get-started.md)

¿Tiene más preguntas? [Pruebe a preguntar a la comunidad de Power BI](https://community.powerbi.com/)

