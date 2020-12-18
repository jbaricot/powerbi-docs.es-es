---
title: Conexión a los datos de Azure Cost Management en Power BI Desktop
description: Conéctese fácilmente a Azure y consiga información sobre el costo y el uso de Azure con Power BI Desktop
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.custom: ''
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: how-to
ms.date: 12/10/2020
LocalizationGroup: Connect to data
ms.openlocfilehash: 6d99e91657d0c5f0bbd1e9c665f00d16c34ba24f
ms.sourcegitcommit: 772c65b7b440ab082510bf3f64b871d19139d451
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/12/2020
ms.locfileid: "97353252"
---
# <a name="create-visuals-and-reports-with-the-azure-cost-management-connector-in-power-bi-desktop"></a>Creación de objetos visuales e informes con el conector Azure Cost Management de Power BI Desktop

El conector de Azure Cost Management para Power BI Desktop se puede usar para crear informes y visualizaciones eficaces y personalizados que ayuden a comprender mejor su gasto con Azure. En la actualidad, el conector de Azure Cost Management admite clientes con un [Contrato de cliente de Microsoft](https://azure.microsoft.com/pricing/purchase-options/microsoft-customer-agreement/) o un [Contrato Enterprise](https://azure.microsoft.com/pricing/enterprise-agreement/).  

El conector de Azure Cost Management utiliza OAuth 2.0 para la autenticación con Azure e identifica a los usuarios que van a usar el conector. Los tokens generados en este proceso son válidos durante un período específico. Power BI conserva el token para el siguiente inicio de sesión. OAuth 2.0 es un estándar para este proceso que se ejecuta en segundo plano y garantiza que estos permisos se administran de forma segura. Para conectarse, debe usar una cuenta de [Administrador de organización](/azure/billing/billing-understand-ea-roles) para contratos Enterprise o una [Cuenta de propietario de facturación](/azure/billing/billing-understand-mca-roles) para los contratos de cliente de Microsoft. 

> [!NOTE]
> Este conector reemplaza a los conectores de [Azure Consumption Insights (beta) y Azure Cost Management (beta)](desktop-connect-azure-consumption-insights.md) que antes estaban disponibles. Los informes creados con el conector anterior deben volver a crearse con este.

> [!NOTE]
> El conector de Azure Cost Management para Power BI Desktop no admite la conexión a nubes gubernamentales. 


## <a name="connect-using-azure-cost-management"></a>Conectar mediante Azure Cost Management

Haga lo siguiente para usar el **conector de Azure Cost Management**:

1.  En la cinta **Inicio**, seleccione **Obtener datos**.
2.  Seleccione **Azure** en la lista de categorías de datos.
3.  Seleccione **Azure Cost Management**.

    ![Obtener datos](media/desktop-connect-azure-cost-management/azure-cost-management-00b.png)

4. En el cuadro de diálogo que se abre, escriba el **Id. del perfil de facturación** de **Contratos de cliente de Microsoft** o el número de **inscripción** de **Contratos de Enterprise (EA)**. 


## <a name="connect-to-a-microsoft-customer-agreement-account"></a>Conectarse a una cuenta de Contrato de cliente de Microsoft 

Para conectarse con una cuenta de **Contrato de cliente de Microsoft**, puede obtener el **identificador de perfil de facturación** de Azure Portal:

1.  En [Azure Portal](https://portal.azure.com/), vaya a **Administración de costos + facturación**.
2.  Seleccione su perfil de facturación. 
3.  En **Configuración** en el menú, seleccione **Propiedades** en la barra lateral.
4.  En el **perfil de Facturación**, copie el **id**. 
5.  En **Elegir ámbito**, seleccione **Id. del perfil de facturación** y pegue el identificador de perfil de facturación del paso anterior. 
6.  Escriba el número de meses y seleccione **Aceptar**.

    ![En la captura de pantalla se muestran las propiedades de Azure Cost Management con un ámbito de identificador del perfil de facturación.](media/desktop-connect-azure-cost-management/azure-cost-management-01a.png)

7.  Cuando se le solicite, inicie sesión con su cuenta de usuario y contraseña de Azure. Debe usar un propietario de la cuenta de facturación para acceder correctamente. 


## <a name="connect-to-an-enterprise-agreement-account"></a>Conectar a una cuenta de Contrato Enterprise

Si necesita conectarse a una cuenta de Contrato Enterprise (EA), puede obtener el identificador de inscripción en Azure Portal:

1.  En [Azure Portal](https://portal.azure.com/), vaya a **Administración de costos + facturación**.
2.  Seleccione la cuenta de facturación.
3.  En el menú **Información general**, copie el valor de **Id. de cuenta de facturación**.
4.  En **Elegir ámbito**, seleccione **Número de inscripción** y pegue el identificador de cuenta de facturación del paso anterior. 
5.  Escriba el número de meses y seleccione **Aceptar**.

    ![En la captura de pantalla se muestran las propiedades de Azure Cost Management con un ámbito de número de inscripción.](media/desktop-connect-azure-cost-management/azure-cost-management-01b.png)

6.  Cuando se le solicite, inicie sesión con su cuenta de usuario y contraseña de Azure. Debe usar una cuenta de administrador Enterprise para los Contratos Enterprise.

## <a name="data-available-through-the-connector"></a>Datos disponibles a través del conector

Una vez que se haya autenticado correctamente, aparecerá una ventana **Navegador** con las siguientes tablas de datos disponibles:

| **Table** | **Descripción** |
| --- | --- |
| **Balance summary** (Resumen del saldo) | Resumen del saldo de los Contratos Enterprise (EA). |
| **Billing events** (Eventos de facturación) | Registro de eventos de nuevas facturas, compras de crédito, etc. Solo en Contratos de cliente de Microsoft. |
| **Budgets** | Detalles de presupuesto para ver los costos o el uso reales frente a los objetivos de presupuesto existentes. |
| **Charges** | Resumen mensual del uso de Azure, los cargos de Marketplace y los cargos facturados por separado. Solo en Contratos de cliente de Microsoft. |
| **Credit lots** (Lotes de crédito) | Detalles de la compra de lotes de crédito de Azure para el perfil de facturación suministrado. Solo en Contratos de cliente de Microsoft. |
| **Pricesheets** (Hojas de precios) | Tasas de los medidores aplicables para el perfil de facturación proporcionado o la inscripción a Contrato Enterprise. |
| **RI charges** (Cargos de RI) | Cargos asociados a las instancias reservadas en los últimos 24 meses. |
| **RI recommendations (shared)**  [Recomendaciones de RI (compartidas)] | Recomendaciones de compra de instancias reservadas según las tendencias de uso de todas las suscripciones para los últimos 7, 30 o 60 días. |
| **RI recommendations (single)**  [Recomendaciones de RI (únicas)] | Recomendaciones de compra de instancias reservadas según las tendencias de uso en una única suscripción para los últimos 7, 30 o 60 días. |
| **RI usage details** (Detalles de uso de RI) | Detalles de consumo de las instancias reservadas existentes en el último mes. |
| **RI usage summary** (Resumen de uso de RI) | Porcentaje diario de uso de reservas de Azure. |
| **Usage details** (Detalles de uso) | Desglose de las cantidades consumidas y los gastos estimados del perfil de facturación facilitado en la inscripción del Contrato Enterprise. |
| **Usage details amortized** (Detalles de uso amortizados) | Desglose de las cantidades consumidas y los gastos estimados amortizados del perfil de facturación facilitado en la inscripción del Contrato Enterprise. |

Puede seleccionar una tabla para ver un diálogo de vista previa. Para seleccionar una o más tablas, active las casillas situadas junto a los nombres correspondientes y, después, seleccione **Cargar**.

![En la captura de pantalla se muestra el cuadro de diálogo Navegador.](media/desktop-connect-azure-cost-management/azure-cost-management-01c.png)

Al seleccionar **Cargar**, los datos se cargan en Power BI Desktop. 

Una vez cargados los datos seleccionados, los campos y las tablas de datos que haya seleccionado se muestran en el panel **Campos**.


## <a name="next-steps"></a>Pasos siguientes

Se puede conectar a muchos orígenes de datos distintos mediante Power BI Desktop. Para más información, consulte los siguientes artículos:

* [¿Qué es Power BI Desktop?](../fundamentals/desktop-what-is-desktop.md)
* [Orígenes de datos en Power BI Desktop](desktop-data-sources.md)
* [Combinar datos y darles forma con Power BI Desktop](desktop-shape-and-combine-data.md)
* [Connect to Excel workbooks in Power BI Desktop (Conectarse a libros de Excel en Power BI Desktop)](desktop-connect-excel.md)   
* [Especificar datos directamente en Power BI Desktop](desktop-enter-data-directly-into-desktop.md)