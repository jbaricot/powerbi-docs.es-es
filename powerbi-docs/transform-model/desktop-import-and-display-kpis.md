---
title: Importar y mostrar KPI en Power BI
description: Importar y mostrar los KPI
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: how-to
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Model your data
ms.openlocfilehash: b12cc24c7ddddd0bc866a3bbeb23e0c7097711db
ms.sourcegitcommit: c83146ad008ce13bf3289de9b76c507be2c330aa
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/10/2020
ms.locfileid: "86215249"
---
# <a name="import-and-display-kpis-in-power-bi"></a>Importar y mostrar KPI en Power BI
Con **Power BI Desktop**, puede importar y mostrar los KPI en tablas, matrices y tarjetas.

Siga estos pasos para importar y mostrar los KPI.

1. Comience con un libro de Excel que tenga un modelo de Power Pivot y KPI. En este ejercicio se usa un libro denominado *KPI*.

1. Importe el libro de Excel en Power BI, mediante **Archivo -> Importar -> Contenido de libro de Excel**. También puede [obtener información sobre cómo importar libros](../connect-data/desktop-import-excel-workbooks.md). 

1. Después de la importación en Power BI, aparecerá el KPI en el panel **Campos**, marcado con el icono de ![semáforo](media/desktop-import-and-display-kpis/traffic.png). Para usar un KPI en el informe, asegúrese de expandir su contenido, exponiendo los campos **Valor**, **Objetivo** y **Estado**.

    ![Captura de pantalla de Power BI Desktop, en la que se muestra Delta KPI expandido en el panel Campos.](media/desktop-import-and-display-kpis/desktoppreviewfeatureon2.png)
 
1. Los KPI importados son útiles en los tipos de visualización estándar, como el tipo **Tabla**. Power BI también incluye el tipo de visualización **KPI**, que solo se debe usar para crear nuevos KPI.
   
    ![Captura de pantalla de Power BI Desktop en la que se muestran los campos de Table1 seleccionados en el panel Campo.](media/desktop-import-and-display-kpis/desktoppreviewfeatureon3.png)

Y eso es todo. Puede usar los KPI para resaltar tendencias, el progreso u otros indicadores importantes.
