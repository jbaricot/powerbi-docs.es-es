---
title: Vista de modelo en Power BI Desktop
description: Vista de modelo en Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: how-to
ms.date: 01/17/2020
ms.author: davidi
LocalizationGroup: Model your data
ms.openlocfilehash: 1c580d403ef33f1c61d5fcd0707d78b4b331da5d
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/23/2020
ms.locfileid: "85239851"
---
# <a name="work-with-model-view-in-power-bi-desktop"></a>Trabajo con la vista Modelo en Power BI Desktop

La *vista Modelo* muestra todas las tablas, columnas y relaciones en el modelo. Esta vista puede resultar especialmente útil cuando el modelo tiene relaciones complejas entre muchas tablas.

Seleccione el icono **Modelo** cerca del lateral de la ventana para ver una vista del modelo existente. Mantenga el cursor sobre una línea de relación para mostrar las columnas que se han usado.

![Vista Modelo en Power BI Desktop](media/desktop-relationship-view/model-view-full-screen.png)

En la ilustración, puede ver que la tabla *Stores* tiene una columna *StoreKey* que está relacionada con la tabla *Sales*, que también tiene una columna *StoreKey*. Las dos tablas tienen una relación del tipo *varios a uno* (\*:1). Una flecha en el centro de la línea muestra la dirección del flujo de contexto del filtro. Las flechas dobles significan que la dirección del filtro cruzado se establece en *Ambos*.

Se puede hacer doble clic en una relación para abrirla en el cuadro de diálogo **Editar relación**. Para obtener más información acerca de las relaciones, vea [Creación y administración de relaciones en Power BI Desktop](desktop-create-and-manage-relationships.md).
