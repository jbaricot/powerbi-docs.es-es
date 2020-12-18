---
title: 'Tutorial: Consumo de un modelo de Azure Machine Learning en Power BI'
titleSuffix: Azure Machine Learning
description: Obtenga información sobre cómo consumir modelos de Azure Machine Learning en Power BI.
services: machine-learning
ms.service: machine-learning
ms.subservice: core
ms.topic: tutorial
ms.author: samkemp
author: samuel100
ms.reviewer: sdgilley, maggies
ms.date: 12/10/2020
ms.openlocfilehash: 6c68fff575e4da0c9126904df2de5292747c209c
ms.sourcegitcommit: 46cf62d9bb33ac7b7eae7910fbba6756f626c65f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/15/2020
ms.locfileid: "97491791"
---
# <a name="tutorial-consume-azure-machine-learning-models-in-power-bi"></a>Tutorial: Consumo de modelos de Azure Machine Learning en Power BI

Este tutorial le guía a través de la creación de un informe de Power BI basado en un modelo de Machine Learning. Al final de este tutorial podrá realizar lo siguiente:

> [!div class="checklist"]
> * Puntuar modelos de Machine Learning (implementados mediante Azure Machine Learning) en Power BI.
> * Conectarse a un modelo de Azure Machine Learning en el Editor de Power Query.
> * Crear un informe con una visualización basada en ese modelo.
> * Publicar ese informe en el servicio Power BI.
> * Configurar una actualización programada para el informe.

## <a name="prerequisites"></a>Requisitos previos

Antes de comenzar este tutorial, debe:

- Entrenar e implementar un modelo de Machine Learning en Azure Machine Learning. Usar uno de estos tres tutoriales de Azure Machine Learning: 

    - [Opción A: Código](/azure/machine-learning/tutorial-power-bi-custom-model)
    - [Opción B: Diseñador](/azure/machine-learning/tutorial-power-bi-designer-model)
    - [Opción C: ML automatizado](/azure/machine-learning/tutorial-power-bi-automated-model)

- Registrarse para obtener una [evaluación gratuita de Power BI](https://app.powerbi.com/signupredirect?pbi_source=web).
- [Instale Power BI Desktop](https://powerbi.microsoft.com/desktop/) en un equipo local.

## <a name="create-the-data-model"></a>Crear el modelo de datos

Abra Power BI Desktop y seleccione **Obtener datos**. En el cuadro de diálogo **Obtener datos**, busque **web**. Seleccione el origen **Web** > **Conectar**.

:::image type="content" source="media/service-aml-integrate/pbi-get-data.png" alt-text="Captura de pantalla que muestra datos web.":::

En el cuadro de diálogo **De web**, copie y pegue la siguiente dirección URL en el cuadro:

```txt 
https://www4.stat.ncsu.edu/~boos/var.select/diabetes.tab.txt
```

:::image type="content" source="media/service-aml-integrate/pbi-data.png" alt-text="Captura de pantalla que muestra la dirección URL web.":::

Seleccione **Aceptar**.

Seleccione **Transformar datos** para abrir la ventana **Editor de Power Query**.

En la cinta de opciones Inicio del Editor de Power Query, seleccione el botón **Azure Machine Learning**.

:::image type="content" source="media/service-aml-integrate/aml-button.png" alt-text="Captura de pantalla que muestra Editor de Power Query.":::

Después de iniciar sesión en su cuenta de Azure mediante el inicio de sesión único, verá una lista de servicios disponibles. Seleccione el servicio **my-sklearn-service** que creó en el tutorial Entrenamiento e implementación de un modelo de Machine Learning. 

Power Query rellena automáticamente las columnas. Recuerde que en nuestro esquema para el servicio, teníamos un decorador de Python que especificaba las entradas. Seleccione **Aceptar**.

:::image type="content" source="media/service-aml-integrate/aml-pbi-run.png" alt-text="Captura de pantalla que muestra modelos de Azure Machine Learning.":::

Al seleccionar **Aceptar** se llama a Azure Machine Learning Service. Desencadena una advertencia sobre la privacidad de los datos para los datos y el punto de conexión.

:::image type="content" source="media/service-aml-integrate/data_privacy_warning.png" alt-text="Captura de pantalla que muestra la advertencia de privacidad.":::

Seleccione **Continuar**. En la siguiente pantalla, seleccione **Ignorar las comprobaciones de los niveles de privacidad de este archivo.**  > **Guardar**.

Una vez que se puntúan los datos, Power Query crea una columna adicional denominada **AzureML.my-diabetes-model**.

:::image type="content" source="media/service-aml-integrate/scored-data.png" alt-text="Captura de pantalla que muestra la columna puntuada agregada.":::

Los datos que devuelve el servicio son una **lista**. 

> [!NOTE]
> Si implementó un modelo de diseñador, verá un **registro**.

Para obtener las predicciones, en la cinta de opciones **Transformar**, seleccione el botón **Expandir columna** > **Expandir en nuevas filas**.

Después de la expansión, verá las predicciones en la columna AzureML.my-diabetes-model.

:::image type="content" source="media/service-aml-integrate/after-expand.png" alt-text="Captura de pantalla que muestra la expansión.":::

Siga estos pasos siguientes para finalizar la limpieza del modelo de datos.

1. Cambie el nombre de la columna **AzureML.my-diabetes-model** a **predicted**.
1. Cambie el nombre de la columna **Y** a **actual**.
1. Cambiar el tipo de la columna **actual**: Seleccione la columna y, en la cinta de opciones **Transformar** seleccione **Tipo de datos** > **Número decimal**.
1. Cambiar el tipo de la columna **predicted**: Seleccione esa columna y, en la cinta de opciones **Transformar** seleccione **Tipo de datos** > **Número decimal**.
1. En la cinta **Inicio**, seleccione **Cerrar y aplicar**.

## <a name="create-a-report-with-visualizations"></a>Creación de un informe con visualizaciones

Ahora puede crear algunas visualizaciones para mostrar los datos.

1. En el panel **Visualizaciones**, seleccione la opción **Gráfico de líneas**. 
1. Con el objeto visual del gráfico de líneas seleccionado:
1. Arrastre el campo **AGE** a **Eje**.
1. Arrastre el campo **actual** a **Valores**.
1. Arrastre el campo **predicted** a **Valores**.

Cambie el tamaño del gráfico de líneas para rellenar la página. El informe ahora tiene un solo gráfico de líneas con dos líneas, una para los valores predichos y otra para los valores reales, distribuidos por edad.

:::image type="content" source="media/service-aml-integrate/report-viz.png" alt-text="Captura de pantalla que muestra la visualización del informe.":::

## <a name="publish-the-report"></a>Publicación del informe

Si lo desea, puede agregar más visualizaciones. En aras de la brevedad, en este tutorial publicaremos el informe.

1. Guarde el informe.
1. Seleccione **Archivo** > **Publicar** > **Publicar en Power BI**.
1. Inicie sesión en el servicio Power BI.
1. Seleccione **Mi área de trabajo**.
1. Cuando el informe se publique correctamente, seleccione el vínculo **Abrir <MI_ARCHIVO_PBIX.pbix> en Power BI**. El informe se abre en Power BI en el explorador.

     :::image type="content" source="media/service-aml-integrate/publish-success.png" alt-text="Captura de pantalla que muestra la publicación correcta.":::

## <a name="enable-datasets-to-refresh"></a>Habilitación de conjuntos de valores para actualizar

En un escenario en el que el origen de datos se actualiza con nuevos datos para puntuar. Debe actualizar las credenciales para que se puedan puntuar los datos. 

En Mi área de trabajo en el servicio Power BI, en la barra de encabezado negro, seleccione **más opciones (...)**  > **Configuración** > **Configuración**.

:::image type="content" source="media/service-aml-integrate/settings-pbi.png" alt-text="Captura de pantalla que muestra la configuración.":::

Seleccione **Conjuntos de datos**, expanda **Credenciales de origen de datos** y luego seleccione **Editar credenciales**.

:::image type="content" source="media/service-aml-integrate/data-refresh.png" alt-text="Captura de pantalla que muestra la actualización de credenciales.":::

Siga las instrucciones para **azureMLFunctions** y **Web**. Asegúrese de seleccionar un nivel de privacidad. Ahora puede establecer opciones en **Actualización programada** para los datos. Seleccione un valor en **Frecuencia de actualización** y **Zona horaria**. También puede seleccionar una dirección de correo electrónico en la que Power BI pueda enviar notificaciones de error de actualización.

:::image type="content" source="media/service-aml-integrate/schedule-refresh.png" alt-text="Captura de pantalla que muestra el conjunto de datos y la actualización de puntuación.":::

Seleccione **Aplicar**.

>[!NOTE]
> Cuando los datos se actualizan, los datos también se envían al punto de conexión de Azure Machine Learning para su puntuación.

## <a name="clean-up-resources"></a>Limpieza de recursos

>[!IMPORTANT]
>Los recursos que creó pueden usarse como requisitos previos de otros tutoriales y artículos de procedimientos de Azure Machine Learning.

Si no tiene previsto usar los recursos que ha creado, elimínelos para no incurrir en gastos.

1. En Azure Portal, seleccione **Grupos de recursos** a la izquierda del todo.
 
1. En la lista, seleccione el grupo de recursos que creó.

1. Seleccione **Eliminar grupo de recursos**.

   ![Captura de pantalla de las selecciones para eliminar un grupo de recursos en Azure Portal.](./media/service-aml-integrate/delete-resources.png)

1. Escriba el nombre del grupo de recursos. A continuación, seleccione **Eliminar**.
1. En Mi área de trabajo del servicio Power BI, elimine el informe y el conjunto de datos relacionados. No es necesario eliminar Power BI Desktop ni el informe del equipo. Power BI Desktop es gratuito.

## <a name="next-steps"></a>Pasos siguientes

En esta serie de tutoriales, aprenderá a configurar una programación en Power BI para que el punto de conexión de puntuación pueda puntuar los nuevos datos en Azure Machine Learning.
