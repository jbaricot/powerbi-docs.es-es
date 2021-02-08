---
title: Creación de un informe de Power BI para Power BI Report Server
description: Aprenda a crear un informe de Power BI para el servidor de informes de Power BI en sencillos pasos.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: how-to
ms.date: 07/24/2020
ms.openlocfilehash: e3c4d97ba6d5ba43e05feecca6a1f0d0c27c89aa
ms.sourcegitcommit: 7ed995eed0fd6e718748accf87bae384211cd95d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/29/2021
ms.locfileid: "99043812"
---
# <a name="create-a-power-bi-report-for-power-bi-report-server"></a>Creación de un informe de Power BI para Power BI Report Server
Puede almacenar y administrar informes de Power BI en el portal web de Power BI Report Server, así como también puede almacenarlos en la nube del servicio Power BI (https://powerbi.com) ). Cree y edite informes en Power BI Desktop y publíquelos en el portal web. Luego, los lectores de informes de su organización pueden verlos en un explorador o en una aplicación móvil de Power BI de un dispositivo móvil.

![Informe de Power BI en el portal web](media/quickstart-create-powerbi-report/report-server-powerbi-report.png)

Aquí tiene cuatro pasos para ayudarle a comenzar.

## <a name="step-1-install-power-bi-desktop-for-power-bi-report-server"></a>Paso 1: Instalar Power BI Desktop para Power BI Report Server

Si ya ha creado informes de Power BI en Power BI Desktop, estará casi listo para crearlos en Power BI Report Server. Se recomienda instalar la versión de Power BI Desktop para Power BI Report Server, ya que así tendrá la certeza de que el servidor y la aplicación siempre están sincronizados. Ambas versiones de Power BI Desktop pueden estar en el mismo equipo.

1. En el portal web de Report Server, seleccione la flecha **Descargar** > **Power BI Desktop**.

    ![Descarga de Power BI Desktop desde el portal web](media/install-powerbi-desktop/report-server-download-web-portal.png)

    O bien, vaya a la página principal de [Power BI Report Server](https://powerbi.microsoft.com/report-server/) y seleccione **Opciones avanzadas de descarga**.

2. En la página del Centro de descarga, seleccione **Descargar**.

3. En función de su equipo, seleccione:

    - **PBIDesktopRS.msi** (versión de 32 bits).

    - **PBIDesktopRS_x64.msi** (versión de 64 bits).

4. Después de descargar el instalador, ejecute el Asistente para instalación de Power BI Desktop.

2. Al final del proceso de instalación, seleccione **Iniciar Power BI Desktop ahora**.
   
    Se inicia automáticamente y está listo para funcionar. Sabrá que tiene la versión correcta porque en la barra de título aparece **Power BI Desktop (enero de 2021)** .

    ![Power BI Desktop, enero de 2021](media/install-powerbi-desktop/power-bi-report-server-desktop.png)

3. Si no conoce Power BI Desktop, considere la posibilidad de ver los vídeos de la pantalla de inicio de sesión.
   
    ![Pantalla de inicio de Power BI Desktop](media/quickstart-create-powerbi-report/report-server-powerbi-desktop-start.png)

## <a name="step-2-select-a-data-source"></a>Paso 2: Seleccionar origen de datos
Puede conectarse a una gran variedad de orígenes de datos. Más información acerca de cómo [conectarse a orígenes de datos](connect-data-sources.md).

1. En la pantalla de inicio de sesión, seleccione **Obtener datos**.
   
    En la pestaña **Inicio**, seleccione **Obtener datos**.
2. Seleccione el origen de datos: en este ejemplo, **Analysis Services**.
   
    ![Seleccionar origen de datos](media/quickstart-create-powerbi-report/power-bi-report-server-get-data-ssas.png)
3. Rellene el campo **Servidor** y, opcionalmente, **Base de datos**. Asegúrese de que **Conectar en directo** está seleccionado > **Aceptar**.
   
    ![Nombre del servidor](media/quickstart-create-powerbi-report/report-server-ssas-server-name.png)
4. Elija el servidor de informes en el que guardará los informes.
   
    ![Selección del servidor de informes](media/quickstart-create-powerbi-report/report-server-select-server.png)

## <a name="step-3-design-your-report"></a>Paso 3: Diseño del informe
Esta es la parte divertida: va a crear los objetos visuales que ilustran los datos.

Por ejemplo, puede crear un gráfico de embudo de clientes y los valores de grupo por ingresos anuales.

![Diseñar un informe](media/quickstart-create-powerbi-report/report-server-create-funnel.png)

1. En **Visualizaciones**, seleccione **Gráfico de embudo**.
2. Arrastre el campo de recuento a **Valores**. Si no es un campo numérico, Power BI Desktop lo convierte automáticamente en un *recuento* del valor.
3. Arrastre el campo al grupo de **Grupo**.

Más información acerca del [diseño de un informe de Power BI](../create-reports/desktop-report-view.md).

## <a name="step-4-save-your-report-to-the-report-server"></a>Paso 4: Guardado del informe en el servidor de informes
Cuando el informe esté listo, guárdelo en la instancia de Power BI Report Server que eligió en el paso 2.

1. En el menú **Archivo**, seleccione **Guardar como** > **servidor de informes de Power BI**.
   
    ![Guardar en el servidor de informes](media/quickstart-create-powerbi-report/report-server-save-as-powerbi-report-server.png)
2. Ahora puede verlo en el portal web.
   
    ![Ver informe en el portal web](media/quickstart-create-powerbi-report/report-server-powerbi-report.png)
    
> [!NOTE]
> Si más adelante decide editar el informe, los datos que verá en el escritorio serán siempre los que estén almacenados en caché del momento en el que se creó el informe por primera vez.  Para ver los datos más recientes al editar el informe, debe actualizarlos en la aplicación Power BI Desktop.

## <a name="next-steps"></a>Pasos siguientes
### <a name="power-bi-desktop"></a>Power BI Desktop
Hay muchos recursos excelentes para crear informes en Power BI Desktop. Este vínculo es un buen punto de partida.

* [Introducción a Power BI Desktop](../fundamentals/desktop-getting-started.md)
* Aprendizaje guiado: [Exploración de Power BI Desktop](/learn/modules/get-data-power-bi/2-getting-started-power-bi-desktop)

### <a name="power-bi-report-server"></a>Power BI Report Server
* [Instalación de Power BI Desktop para Power BI Report Server](install-powerbi-desktop.md)  
* [¿Qué es Power BI Report Server?](get-started.md)  

¿Tiene más preguntas? [Pruebe a preguntar a la comunidad de Power BI](https://community.powerbi.com/)
