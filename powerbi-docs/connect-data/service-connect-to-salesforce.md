---
title: Conexión a Salesforce con Power BI
description: Salesforce para Power BI
author: paulinbar
ms.author: painbar
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: how-to
ms.date: 05/30/2019
LocalizationGroup: Connect to services
ms.openlocfilehash: f43d60a22d436cc0be5aa57bc9b383d535dbfc0d
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/01/2020
ms.locfileid: "96392896"
---
# <a name="connect-to-salesforce-with-power-bi"></a>Conexión a Salesforce con Power BI
Power BI le permite conectarse fácilmente a su cuenta de Salesforce.com. Con esta conexión, puede recuperar los datos de Salesforce y disponer de un panel e informes proporcionados automáticamente.

Más información sobre la [Integración de Salesforce](https://powerbi.microsoft.com/integrations/salesforce) con Power BI.

## <a name="how-to-connect"></a>Cómo conectarse
1. En Power BI, seleccione **Obtener datos** en la parte inferior del panel de navegación.
   
   ![Captura de pantalla del botón Obtener datos, mostrado en el panel de navegación.](media/service-connect-to-salesforce/pbi_getdata.png) 
2. En el cuadro **Servicios** , seleccione **Obtener**.
   
   ![Captura de pantalla del cuadro de diálogo Servicios, en el que se muestra el botón Obtener.](media/service-connect-to-salesforce/pbi_getservices.png) 
3. Seleccione **Datos de análisis para Salesforce** y seleccione **Obtener**.  
   
   ![Captura de pantalla del cuadro de diálogo Analytics for Salesforce, donde se muestra el vínculo Obtener ahora.](media/service-connect-to-salesforce/salesforce.png)
4. Seleccione **Iniciar sesión** para iniciar el flujo de inicio de sesión.
   
    ![Captura de pantalla del cuadro de diálogo Conectar con Salesforce, en la que se muestra el botón Iniciar sesión.](media/service-connect-to-salesforce/dialog.png)
5. Cuando se le solicite, escriba sus credenciales de Salesforce. Seleccione **Permitir** para que Power BI pueda tener acceso a la información básica y los datos de Salesforce.
   
   ![Captura de pantalla de las credenciales de Salesforce, en la que se muestra que Power BI solicita permiso para acceder a la información.](media/service-connect-to-salesforce/sf_authorize.png)
6. Configure lo que quiere importar en Power BI mediante la opción de lista desplegable:
   
   * **Panel**
     
     Seleccione un panel predefinido basado en un rol (como, por ejemplo **Jefe de ventas**). Estos paneles recuperan un conjunto específico de datos estándar de Salesforce que no incluyen los campos personalizados.
     
     ![Captura de pantalla del panel de Salesforce, en el que se muestra la opción para seleccionar un panel predefinido basado en un rol.](media/service-connect-to-salesforce/pbi_salesforcechooserole.png)
   * **Informes**
     
     Seleccione uno o más informes personalizados de su cuenta de Salesforce. Estos informes coincidirán con sus vistas en Salesforce y pueden incluir datos de campos personalizados y objetos.
     
     ![Captura de pantalla de los informes de Salesforce, en la que se muestra una lista de informes personalizados.](media/service-connect-to-salesforce/pbi_salesforcereports.png)
     
     Si no ve ningún informe, agréguelos o créelos en su cuenta de Salesforce y vuelva a intentarlo.

7. Seleccione **Conectar** para comenzar el proceso de importación. Durante la importación verá una notificación que muestra que la importación está en curso. Una vez finalizada la importación, en el panel de navegación verá un panel, un informe y un conjunto de datos para los datos de Salesforce.
   
   ![Captura de pantalla del panel Sales Manager, en el que se muestran el panel, el informe y los conjuntos de datos.](media/service-connect-to-salesforce/pbi_getdatasalesforcedash.png)

Puede cambiar este panel para mostrar los datos de la forma que desee. Puede realizar preguntas con Preguntas y respuestas o [seleccionar un icono](../consumer/end-user-tiles.md) para abrir el informe subyacente y [editar o eliminar los iconos del panel](../create-reports/service-dashboard-edit-tile.md).

**¿Qué más?**

* Pruebe a [hacer una pregunta en el cuadro de preguntas y respuestas](../consumer/end-user-q-and-a.md), en la parte superior del panel.
* [Editar o eliminar un icono](../create-reports/service-dashboard-edit-tile.md) en el panel
* [Seleccione un icono](../create-reports/service-dashboard-tiles.md) para abrir el informe subyacente
* Aunque el conjunto de datos se programará para actualizarse diariamente, puede cambiar la programación de actualización o intentar actualizar bajo petición mediante **Actualizar ahora**.

## <a name="system-requirements-and-considerations"></a>Consideraciones y requisitos del sistema

- Estar conectado con una cuenta de Salesforce de producción que tenga habilitado el acceso de API.

- Permiso concedido a la aplicación de Power BI durante el inicio de sesión

- La cuenta debe tener disponibles llamadas de API suficientes para extraer y actualizar los datos.

- La actualización requiere un token de autenticación válido. Asegúrese de tener importados cinco conjuntos de datos de Salesforce o menos, ya que Salesforce tiene un límite de cinco tokens de autenticación por aplicación.

- La API de informes de Salesforce tiene una restricción que admite hasta 2000 filas de datos.


## <a name="troubleshooting"></a>Solución de problemas

Si se producen errores, revise los requisitos anteriores. 

Actualmente no se admite el inicio de sesión en un dominio personalizado o de espacio aislado.

### <a name="unable-to-connect-to-the-remote-server-message"></a>Mensaje "Unable to connect to the remote server" (No se puede conectar al servidor remoto)

Si recibe un mensaje "No se puede conectar al servidor remoto" al intentar conectarse a su cuenta de Salesforce, eche un vistazo a esta solución en el foro siguiente: [Mensaje de error de inicio de sesión del conector de Salesforce: Unable to connect to the remote server](https://www.outsystems.com/forums/Forum_TopicView.aspx?TopicId=17674&TopicName=log-in-error-message-unable-to-connect-to-the-remote-server&) (Mensaje de error de inicio de sesión del conector de Salesforce: no se puede conectar al servidor remoto).


## <a name="next-steps"></a>Pasos siguientes
[¿Qué es Power BI?](../fundamentals/power-bi-overview.md)

[Orígenes de datos del servicio Power BI](service-get-data.md)
