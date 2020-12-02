---
title: Conexión a la Microsoft Graph Security API en Power BI Desktop
description: Conexión fácil a la Microsoft Graph Security API en Power BI Desktop
author: paulinbar
ms.author: painbar
ms.reviewer: ''
ms.custom: seojan19
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: conceptual
ms.date: 01/29/2019
LocalizationGroup: Connect to data
ms.openlocfilehash: b3aa9be7be6e2769367cd3337b78030d52bde0c7
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/01/2020
ms.locfileid: "96411434"
---
# <a name="connect-to-the-microsoft-graph-security-api-in-power-bi-desktop"></a>Conexión a la Microsoft Graph Security API en Power BI Desktop

Puede usar el conector Microsoft Graph Security de Power BI Desktop para conectarse a la [Microsoft Graph Security API](/graph/security-concept-overview). Luego, puede compilar paneles e informes para obtener conclusiones de las [alertas](/graph/api/resources/alert) relacionadas con la seguridad y las [puntuaciones de seguridad](/graph/api/resources/securescores).

Microsoft Graph Security API se conecta a [varias soluciones de seguridad](/graph/api/resources/security-api-overview#alerts) de Microsoft y sus partners para facilitar la correlación de las alertas. Esta combinación proporciona acceso a completa información contextual y simplifica la automatización. Permite a las organizaciones obtener conclusiones rápidamente y actuar en varios productos de seguridad, al tiempo que reduce los costos y la complejidad.

## <a name="prerequisites-to-use-the-microsoft-graph-security-connector"></a>Requisitos previos para usar el conector Microsoft Graph Security

Para usar el conector Microsoft Graph Security, debe obtener el consentimiento *explícito* del administrador de global de Azure Active Directory (Azure AD). Vea los [requisitos de autenticación de Microsoft Graph Security](/graph/security-authorization).
Para el consentimiento se necesitan el identificador y el nombre de aplicación del conector, que se mencionan aquí y están disponibles en [Azure Portal](https://portal.azure.com):

| Propiedad | Valor |
|----------|-------|
| **Nombre de la aplicación** | `MicrosoftGraphSecurityPowerBIConnector` |
| **Identificador de la aplicación** | `cab163b7-247d-4cb9-be32-39b6056d4189` |
| **URI de redirección** | `https://oauth.powerbi.com/views/oauthredirect.html` |
|||

Para conceder el consentimiento para el conector, el administrador global de Azure AD puede usar uno de estos métodos:

* [Concesión de consentimiento para aplicaciones de Azure AD](/azure/active-directory/develop/v2-permissions-and-consent)

* Respuesta a una solicitud que envía la aplicación lógica durante su primera ejecución mediante la [experiencia de consentimiento de la aplicación](/azure/active-directory/develop/application-consent-experience)
   
La cuenta de usuario que inicia sesión en el conector de Microsoft Graph Security debe tener asignado el rol Lector de seguridad de Azure AD, **si** el usuario no es miembro del rol *Administrador de seguridad*. Vea [Asignar roles de Azure AD a usuarios](/graph/security-authorization#assign-azure-ad-roles-to-users).

## <a name="using-the-microsoft-graph-security-connector"></a>Uso del conector Microsoft Graph Security

Siga estos pasos para usar el conector:

1. Seleccione **Obtener datos** > **Más** en la cinta **Inicio** de Power BI Desktop.
2. Seleccione **Servicios en línea** en la lista de categorías del lado izquierdo de la ventana.
3. Seleccione **Microsoft Graph Security (Beta)** .

    ![Cuadro de diálogo Obtener datos](media/desktop-connect-graph-security/GetData.PNG)
    
4. En la ventana **Microsoft Graph Security**, seleccione la versión de la Microsoft Graph API que va a consultar: **v1.0** o **beta**.

    ![Cuadro de diálogo de selección de versión](media/desktop-connect-graph-security/selectVersion.PNG)
    
5. Cuando se le pida, inicie sesión en la cuenta de Azure Active Directory. Esta cuenta debe tener el rol *Lector de seguridad* o *Administrador de seguridad*, como se ha mencionado en la sección anterior.

    ![Iniciar sesión](media/desktop-connect-graph-security/SignIn.PNG) 
    
6. Si es el administrador *y* todavía no tiene el consentimiento para el conector (aplicación) Microsoft Graph Security de Power BI, verá el cuadro de diálogo siguiente. Seleccione **Consentimiento en nombre de la organización**.

    ![Cuadro de diálogo de consentimiento del administrador](media/desktop-connect-graph-security/AdminConsent.PNG)
    
7. Una vez iniciada la sesión, aparece el cuadro de diálogo siguiente, que indica que se ha autenticado. Seleccione **Conectar**.

    ![Cuadro de diálogo "Ha iniciado sesión"](media/desktop-connect-graph-security/SignedIn.PNG)
    
8. Después de conectarse, la ventana **Navegador** muestra las alertas, las puntuaciones de seguridad y otras entidades que están disponibles en la [Microsoft Graph Security API](/graph/security-concept-overview) para la versión seleccionada en el paso 4. Seleccione una o varias entidades para importarlas y usarlas en Power BI Desktop. Luego, seleccione **Cargar** para obtener la vista de resultados que se muestra tras el paso 9.

    ![Cuadro de diálogo Navegador](media/desktop-connect-graph-security/NavTable.PNG)
    
9. Si quiere usar una consulta avanzada con la Microsoft Graph Security API, seleccione **Especificar URL de Microsoft Graph Security personalizada para filtrar resultados**. Use esta función para emitir una consulta [OData.Feed](./desktop-connect-odata.md) a la Microsoft Graph Security API con los permisos necesarios.

   En el ejemplo siguiente se usa el elemento *serviceUri* `https://graph.microsoft.com/v1.0/security/alerts?$filter=Severity eq 'High'`. Para ver cómo compilar consultas para filtrar, ordenar o recuperar los resultados más recientes, vea [Opciones de consulta de sistema de OData](/graph/query-parameters).

   ![Ejemplo de OdataFeed](media/desktop-connect-graph-security/ODataFeed.PNG)
    
   Al seleccionar **Invoke**, la función **OData.Feed** realiza una llamada a la API, que abre el Editor de consultas. Se filtra y se refina el conjunto de datos que se quiere usar. Luego, se cargan esos datos en Power BI Desktop.

Esta es la ventana de resultados de las entidades de Microsoft Graph Security que se han consultado:

   ![Ejemplo de ventana de resultados](media/desktop-connect-graph-security/Result.PNG)
    

Ahora está listo para usar los datos importados del conector Microsoft Graph Security en Power BI Desktop. Puede crear gráficos o informes. O bien, puede interactuar con otros datos que se importan de libros de Excel, bases de datos u otros orígenes de datos.

## <a name="next-steps"></a>Pasos siguientes
* Vea plantillas y ejemplos de Power BI que usan este conector en [Microsoft Graph Security GitHub Power BI samples](https://aka.ms/graphsecuritypowerbiconnectorsamples) (Ejemplos de GitHub de Microsoft Graph Security de Power BI).

* Para obtener escenarios de uso e información adicional, vea [esta entrada de blog del conector Microsoft Graph Security de Power BI](https://aka.ms/graphsecuritypowerbiconnectorblogpost).

* Puede conectarse a todo tipo de datos con Power BI Desktop. Para más información, consulte los siguientes recursos:

    * [¿Qué es Power BI Desktop?](../fundamentals/desktop-what-is-desktop.md)
    * [Orígenes de datos en Power BI Desktop](desktop-data-sources.md)
    * [Combinar datos y darles forma con Power BI Desktop](desktop-shape-and-combine-data.md)
    * [Connect to Excel workbooks in Power BI Desktop (Conectarse a libros de Excel en Power BI Desktop)](desktop-connect-excel.md)
    * [Especificar datos directamente en Power BI Desktop](desktop-enter-data-directly-into-desktop.md)