---
title: Subinformes en informes paginados de Power BI
description: En este artículo, obtendrá información sobre los orígenes de datos admitidos para los informes paginados en el servicio Power BI y cómo conectarse a orígenes de datos de Azure SQL Database.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: how-to
ms.date: 04/29/2020
ms.openlocfilehash: 9ced88289b2170d503a8394d5b83175659178e85
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/23/2020
ms.locfileid: "85239588"
---
# <a name="subreports-in-power-bi-paginated-reports"></a>Subinformes en informes paginados de Power BI

Un *subinforme* es un elemento de informe paginado que muestra otro informe paginado dentro del cuerpo de un informe paginado principal. Como concepto, un subinforme de un informe es como un marco en una página web. Sirve para insertar un informe dentro de otro informe. Puede usarse cualquier informe como subinforme. El informe que se muestra como subinforme se almacena en la misma área de trabajo Premium que el informe primario. Es posible diseñar el informe primario para que pase sus parámetros al subinforme. Este tipo de informe puede repetirse dentro de las regiones de datos mediante un parámetro que filtre los datos de cada instancia del subinforme.  
  
 ![Subinforme en un informe paginado](media/subreports/paginated-report-subreport.png "Subinforme de informe paginado")  
  
 En esta ilustración, la información de contacto que se muestra en el informe de pedido de ventas procede en realidad de un subinforme de Contactos.  
  
En Power BI Report Builder puede crear y modificar archivos de definición de informe paginados (.rdl). Puede cargar subinformes almacenados en SQL Server Reporting Services a un área de trabajo Premium en el servicio Power BI. Los informes principales y los subinformes deben publicarse en la misma área de trabajo. Instale [Power BI Report Builder](https://aka.ms/pbireportbuilder).
  
## <a name="work-with-report-builder-and-the-power-bi-service"></a>Trabajar con Report Builder y el servicio Power BI

Power BI Report Builder puede trabajar con informes paginados en el equipo (conocidos como informes locales) o con informes del servicio Power BI.  Al abrir Report Builder por primera vez, se le pedirá que inicie sesión en su cuenta de Power BI. Si no, seleccione **Iniciar sesión** en la esquina superior derecha.

:::image type="content" source="media/subreports/report-builder-sign-in.png" alt-text="Iniciar sesión en Power BI":::

Después de iniciar sesión, verá una opción **Servicio Power BI** en Power BI Report Builder para las opciones **Abrir** y **Guardar como** del menú **Archivo**. Al seleccionar la opción **Servicio Power BI** para guardar un informe, se crea una conexión dinámica entre Power BI Report Builder y el servicio Power BI. 

:::image type="content" source="media/subreports/report-builder-subreport-open-service.png" alt-text="Abrir desde el servicio Power BI":::

## <a name="save-a-local-report-to-the-power-bi-service"></a>Guardar un informe local en el servicio Power BI

Para poder agregar un subinforme a un informe principal, primero tiene que crear los dos informes y guardarlos en la misma área de trabajo de Power BI Premium. 

1. Para abrir un informe local existente, en el menú **Archivo**, seleccione **Abrir** > **Este equipo** y seleccione un archivo .rdl.  

2. En el menú **Archivo**, seleccione **Guardar como** > **Servicio Power BI**.  Para más detalles, vea [Publicación de un informe paginado en el servicio Power BI](paginated-reports-save-to-power-bi-service.md).

    > [!NOTE]
    > También puede cargar un informe empezando desde el servicio Power BI. Encontrará más información en el mismo artículo, [Publicación de un informe paginado en el servicio Power BI](paginated-reports-save-to-power-bi-service.md).

3. En el cuadro de diálogo **Guardar como**, seleccione un área de trabajo de Power BI Premium donde almacenar los informes paginados.  Las áreas de trabajo Premium tienen un icono de rombo ![icono de rombo Premium](media/subreports/report-builder-premium-diamond.png) junto a su nombre.

    :::image type="content" source="media/subreports/report-builder-subreport-save-as-service.png" alt-text="Guardar como en el servicio Power BI":::

4. Seleccione **Guardar**.

## <a name="add-a-subreport-to-a-report"></a>Agregar un subinforme a un informe

Ya ha guardado los dos informes en la misma área de trabajo Premium, así que ya puede agregar un informe dentro de otro como un subinforme. Hay dos maneras de agregar un subinforme. 

1. En la cinta **Insertar**, seleccione el botón **Subinforme**, o bien haga clic con el botón derecho en el lienzo del informe y seleccione **Insertar** > **Subinforme**.

    :::image type="content" source="media/subreports/report-builder-insert-subreport.png" alt-text="Insertar un subinforme en un informe":::

    Se abre el cuadro de diálogo **Propiedades del subinforme**.  

2. Seleccione el botón **Examinar**, vaya al informe que quiere usar como subinforme y especifique el nombre del subinforme en el cuadro de texto **Nombre**.

3. Configure las otras propiedades según sea necesario, incluidos los [parámetros](#use-parameters-in-subreports).

## <a name="use-parameters-in-subreports"></a>Usar parámetros en subinformes  
 Para pasar parámetros del informe primario al subinforme, defina un parámetro de informe en el informe que utiliza como subinforme. Cuando se coloca el subinforme en el informe primario, se puede seleccionar el parámetro de informe y el valor que se van a pasar desde el informe primario al parámetro de informe del subinforme.  
  
> [!NOTE]  
> El parámetro que se selecciona en el subinforme es un parámetro de *informe*, no un parámetro de *consulta*.  
  
 Se puede colocar un subinforme en el cuerpo principal del informe o en una región de datos. Si se coloca un subinforme en una región de datos, el subinforme se repite con cada instancia del grupo o de la fila de la región de datos. Puede pasar un valor del grupo o de la fila al subinforme. En la propiedad de valor del subinforme, use una expresión de campo para el campo que contiene el valor que quiere pasar al parámetro del subinforme.  
  
 Para más información sobre cómo trabajar con parámetros y subinformes, vea [Adición de un subinforme y parámetros](https://docs.microsoft.com/sql/reporting-services/report-design/add-a-subreport-and-parameters-report-builder-and-ssrs) en la documentación de SQL Server Reporting Services.  

## <a name="preview-paginated-reports-in-report-builder"></a>Vista previa de informes paginados en Report Builder

Puede obtener una vista previa de los informes en Report Builder.

- En la cinta **Inicio**, seleccione **Ejecutar**. 

Como Report Builder es una herramienta de diseño, la vista previa del informe puede tener un aspecto diferente de la representación del informe en el servicio Power BI.

### <a name="notes-about-previewing"></a>Notas sobre la vista previa

- Report Builder no almacena las credenciales de los orígenes de datos usados en los informes.  Report Builder le pide cada conjunto de credenciales durante la vista previa.  
- Si los orígenes de datos del informe son locales, debe configurar una puerta de enlace después de guardar el informe en el área de trabajo de Power BI.
- Si se produce un error en Report Builder durante la vista previa, devuelve un mensaje genérico.  Si el error es difícil de depurar, puede intentar representar el informe en el servicio Power BI.  

## <a name="considerations"></a>Consideraciones

### <a name="maintaining-the-connection"></a>Mantener la conexión

Report Builder no conserva la conexión a Power BI al cerrar el archivo.  Es posible trabajar con un informe principal local que tenga subinformes almacenados en el área de trabajo de Power BI. No olvide guardar el informe principal en el área de trabajo de Power BI antes de cerrar el informe.  Si no lo hace, es posible que se muestre el mensaje "no encontrado" durante la vista previa, ya que no hay conexión dinámica con el servicio Power BI.  En ese caso, vaya a un subinforme y seleccione sus propiedades.  Vuelva a abrir el subinforme desde el servicio Power BI.  Se restablecerá la conexión y el resto de los subinformes deberían mostrarse correctamente.

### <a name="renaming-a-subreport"></a>Cambiar el nombre de un subinforme

Si cambia el nombre de un subinforme en el área de trabajo, debe corregir la referencia de nombre en el informe principal. Si no lo hace, el subinforme no se representará. El informe principal se sigue representando con un mensaje de error dentro del elemento de subinforme.

## <a name="migrate-large-reports"></a>Migrar informes grandes

Si va a migrar informes de gran tamaño a Power BI, puede intentar usar la [herramienta RdlMigration](../guidance/migrate-ssrs-reports-to-power-bi.md).  La herramienta RdlMigration se ha actualizado para administrar los nombres de los subinformes duplicados.  Los nombres de subinformes pueden duplicarse cuando dos o más informes comparten el mismo nombre pero residen en subdirectorios diferentes.  Si los nombres no se resuelven de forma única, solo se reconoce el primer subinforme.

Si quiere usar Report Builder para migrar informes de gran tamaño, se recomienda trabajar primero con los subinformes. Guarde cada uno en el área de trabajo de Power BI para evitar que haya nombres de informe duplicados.

## <a name="share-reports-with-subreports"></a>Compartir informes con subinformes

Como hemos indicado, el informe principal y los subinformes deben estar en la misma área de trabajo. Si no, el subinforme no se representará. Al compartir el informe principal, puede que también tenga que compartir los subinformes. Si comparte el informe principal en una aplicación, incluya también los subinformes en esa aplicación. Si comparte el informe principal con usuarios o grupos de usuarios directamente, compruebe que también comparte cada subinforme con el mismo conjunto de usuarios o grupos de usuarios.
  
## <a name="next-steps"></a>Pasos siguientes

[Solución de problemas de subinformes en informes paginados de Power BI](subreports-troubleshoot.md)

[Visualización de un informe paginado en el servicio Power BI](../consumer/paginated-reports-view-power-bi-service.md)

¿Tiene más preguntas? [Pruebe la comunidad de Power BI](https://community.powerbi.com/)
