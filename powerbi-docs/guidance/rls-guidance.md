---
title: Instrucciones de seguridad de nivel de fila (RLS) en Power BI Desktop
description: Instrucciones para aplicar seguridad de nivel de fila (RLS) en los modelos de datos con Power BI Desktop.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 06/18/2020
ms.author: v-pemyer
ms.openlocfilehash: 60bb1ef7421d4ebcedd49d2e973cf245edec0381
ms.sourcegitcommit: cff93e604e2c5f24e0f03d6dbdcd10c2332aa487
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/22/2020
ms.locfileid: "90965036"
---
# <a name="row-level-security-rls-guidance-in-power-bi-desktop"></a>Instrucciones de seguridad de nivel de fila (RLS) en Power BI Desktop

Este artículo está dirigido a modeladores de datos como usted que trabajan con Power BI Desktop. Describe las prácticas de diseño adecuadas para aplicar seguridad de nivel de fila (RLS) en los modelos de datos.

Es importante comprender las _filas de tabla_ de los filtros de RLS. No se pueden configurar para restringir el acceso a los objetos de modelo, como tablas, columnas o medidas.

> [!NOTE]
> En este artículo no se describe RLS ni cómo configurarlo. Para obtener más información, consulte [Restricción del acceso a datos con seguridad de nivel de fila (RLS) en Power BI Desktop](../create-reports/desktop-rls.md).
>
> Además, no se trata la aplicación de RLS en conexiones dinámicas a modelos hospedados externamente con Azure Analysis Services o SQL Server Analysis Services. En estos casos, es Analysis Services quien aplica RLS. Cuando Power BI se conecta mediante inicio de sesión único (SSO), Analysis Services aplicará RLS (a menos que la cuenta tenga privilegios de administrador).

## <a name="create-roles"></a>Crear roles

Es posible crear varios roles. Cuando piense en las necesidades de permisos que requiere un único usuario de informes, procure crear un único rol que conceda todos esos permisos, en lugar de optar por un diseño en el que un usuario de informes sea miembro de varios roles. El motivo es que un usuario de informes podría asignarse a varios roles, ya sea directamente mediante su cuenta de usuario o indirectamente mediante la pertenencia a grupos de seguridad. Las asignaciones de roles múltiples pueden producir resultados inesperados.

Cuando se asigna un usuario de informes a varios roles, los filtros RLS se vuelven aditivos. Esto significa que los usuarios de informes pueden ver filas de tabla que representan la unión de esos filtros. Pero aún hay más: en algunos escenarios no es posible garantizar que un usuario de informes no vea las filas de una tabla. Por lo tanto, a diferencia de los permisos aplicados a objetos de base de datos de SQL Server (y otros modelos de permisos), no se aplica el principio "una vez denegado, denegado siempre".

Considere un modelo con dos roles: El primer rol, llamado **Workers** (Trabajadores), restringe el acceso a todas las filas de la tabla **Payroll** (Nómina) mediante la siguiente expresión de regla:

```dax
FALSE()
```

> [!NOTE]
> Una regla no devolverá ninguna fila de la tabla cuando su expresión se evalúe como **false**.

Aún así, un segundo rol, denominado **Managers** (Directivos), permite el acceso a todas las filas de la taba **Payroll** (Nómina) mediante la siguiente expresión de regla:

```dax
TRUE()
```

Atención: Si un usuario de informe se asigna a ambos roles, verá todas las filas de la tabla **Salary** (Salario).

## <a name="optimize-rls"></a>Optimización de RLS

RLS funciona aplicando filtros automáticamente a cada consulta DAX, y estos filtros pueden tener un impacto negativo en el rendimiento de las consultas. Por lo tanto, la eficacia de RLS se reduce a un buen diseño del modelo. Es importante seguir las instrucciones para el diseño de modelos, como se describe en los siguientes artículos:

- [Descripción de un esquema de estrella e importancia para Power BI](star-schema.md)
- Todos los artículos de la guía de instrucciones de la relación se encuentran en la [documentación de orientación de Power BI](./index.yml).

En general, suele ser más eficaz aplicar filtros RLS en tablas de tipo de dimensión y no tablas de tipo de hechos. Y basarse en relaciones bien diseñadas para garantizar que los filtros RLS se propaguen a otras tablas de modelos. Por lo tanto, evite usar la función DAX [LOOKUPVALUE](/dax/lookupvalue-function-dax) cuando las relaciones de modelo puedan lograr el mismo resultado.

Siempre que se apliquen filtros RLS en las tablas de DirectQuery y existan relaciones con otras tablas de DirectQuery, asegúrese de optimizar la base de datos de origen. Puede implicar el diseño de índices adecuados o el uso de columnas calculadas persistentes. Para obtener más información, vea [Instrucciones del modelo de DirectQuery en Power BI Desktop](directquery-model-guidance.md).

### <a name="measure-rls-impact"></a>Medición del impacto de RLS

Es posible medir el impacto en el rendimiento de los filtros de RLS en Power BI Desktop mediante el [Analizador de rendimiento](../create-reports/desktop-performance-analyzer.md). En primer lugar, determine la duración de las consultas visuales de informes cuando no se aplique RLS. A continuación, use el comando **Ver como** en la pestaña **Modelado** de la cinta de opciones para aplicar RLS y determinar y comparar las duraciones de la consulta.

## <a name="configure-role-mappings"></a>Configuración de las asignaciones de roles

Una vez publicados en Power BI, debe asignar miembros a los roles del conjunto de datos. Solo los propietarios del conjunto de datos o los administradores del área de trabajo pueden agregar miembros a los roles. Para más información, consulte [Seguridad de nivel de fila (RLS) con Power BI (Administración de la seguridad en el modelo)](../admin/service-admin-rls.md#manage-security-on-your-model).

Los miembros pueden ser cuentas de usuario o grupos de seguridad. Siempre que sea posible, se recomienda asignar grupos de seguridad a los roles de los conjuntos de seguridad. Implica la administración de pertenencias a grupos de seguridad en Azure Active Directory. Posiblemente, delega la tarea a los administradores de red.

## <a name="validate-roles"></a>Validación de roles

Pruebe cada rol para asegurarse de que filtra el modelo correctamente. Se realiza fácilmente mediante el uso del comando **Ver como** en la pestaña de la cinta **Modelado**.

Cuando el modelo tenga reglas dinámicas que usen la función DAX [USERNAME](/dax/username-function-dax), asegúrese de comprobar los valores esperados _e inesperados_. Al incrustar contenido de Power BI —específicamente con el escenario [la aplicación posee los datos](../developer/embedded/embedding.md#embedding-for-your-customers)—, la lógica de la aplicación puede pasar cualquier valor como un nombre de usuario de identidad efectivo. Siempre que sea posible, asegúrese de que los valores accidentales o malintencionados den como resultado filtros que no devuelven ninguna fila.

Considere un ejemplo que use Power BI insertado, donde la aplicación pasa el rol de trabajo del usuario como el nombre de usuario efectivo: Es "Manager"(Directivo) o "Worker" (Trabajador). Los administradores pueden ver todas las filas, pero los trabajadores solo pueden ver las filas en las que el valor de la columna **Tipo** es "Interno".

Se define la siguiente expresión de regla:

```dax
IF(
    USERNAME() = "Worker",
    [Type] = "Internal",
    TRUE()
)
```

El problema con esta expresión de regla es que todos los valores, excepto "Worker" (Trabajador), devuelven _todas las filas de la tabla_. Por lo tanto, un valor accidental, como "Wrker", devuelve involuntariamente todas las filas de la tabla. Así pues, es más seguro escribir una expresión que pruebe cada valor esperado. En la expresión de regla mejorada siguiente, un valor inesperado hará que la tabla no devuelva ninguna fila.

```dax
IF(
    USERNAME() = "Worker",
    [Type] = "Internal",
    IF(
        USERNAME() = "Manager",
        TRUE(),
        FALSE()
    )
)
```

## <a name="design-partial-rls"></a>RLS de diseño parcial

A veces, los cálculos necesitan valores que no están restringidos por filtros de RLS. Por ejemplo, es posible que en un informe se tenga que mostrar la relación entre los ingresos obtenidos para la región de ventas del usuario del informe y _todos los ingresos obtenidos_.

Aunque no es posible que una expresión DAX invalide RLS —de hecho, no puede determinar ni siquiera que se aplique RLS—, puede usar una tabla de modelo de resumen. La tabla del modelo de resumen se consulta para recuperar los ingresos de "todas las regiones" y no está restringida por ningún filtro de RLS.

Veamos cómo podría implementar este requisito de diseño. En primer lugar, tenga en cuenta el siguiente diseño de modelo:

:::image type="content" source="media/rls-guidance/mixed-rls-model.png" alt-text="Se muestra una imagen de un diagrama de modelo. En los párrafos siguientes se describe el diseño":::.

El modelo consta de cuatro tablas:

- La tabla **Salesperson** (Comercial) almacena una fila por comercial. Incluye la columna **EmailAddress** (Dirección de correo electrónico), que almacena la dirección de correo electrónico de cada vendedor. Esta tabla está oculta.
- La tabla **Sales** (Ventas) almacena una fila por pedido. Incluye la medida **Revenue % All Region** (% ingresos toda la región), que está diseñada para devolver una relación de los ingresos obtenidos por la región del usuario del informe con respecto a los ingresos obtenidos por todas las regiones.
- La tabla **Date** (Fecha) almacena una fila por fecha y permite filtrar y agrupar el año y el mes.
- **SalesRevenueSummary** (Resumen de los ingresos por ventas) es una tabla calculada. Almacena los ingresos totales para cada fecha de pedido. Esta tabla está oculta.

La siguiente expresión define la tabla calculada **SalesRevenueSummary** (Resumen de los ingresos por ventas):

```dax
SalesRevenueSummary =
SUMMARIZECOLUMNS(
    Sales[OrderDate],
    "RevenueAllRegion", SUM(Sales[Revenue])
)
```

> [!NOTE]
> Una [tabla de agregación](../transform-model/desktop-aggregations.md) podría lograr el mismo requisito de diseño.

La siguiente regla de RLS se aplica a la tabla **Salesperson** (Comercial):

```dax
[EmailAddress] = USERNAME()
```

En la tabla siguiente se describe cada una de las tres relaciones del modelo:

|Relación|Descripción|
|---------|---------|
|![Terminador de diagrama de flujo 1.](media/common/icon-01-red-30x30.png)|Hay una relación de varios a varios entre las tablas **Salesperson** (Comercial) y **Sales** (Ventas). La regla de RLS filtra la columna **EmailAddress** (Dirección de correo electrónico) de la tabla oculta **Salesperson** (Comercial) mediante la función de DAX [USERNAME](/dax/username-function-dax). El valor de la columna **Region** (Región) (para el usuario del informe) se propaga a la tabla **Sales** (Ventas).|
|![Terminador de diagrama de flujo 2.](media/common/icon-02-red-30x30.png)|Hay una relación de uno a varios entre las tablas **Date** (Fecha) y **Sales** (Ventas).|
|![Terminador de diagrama de flujo 3.](media/common/icon-03-red-30x30.png)|Hay relaciones de uno a varios entre las tablas **Date** (Fecha) y **SalesRevenueSummary** (Resumen de los ingresos por ventas).|

La expresión siguiente define la medida **Revenue % All Region** (% ingresos toda la región):

```dax
Revenue % All Region =
DIVIDE(
    SUM(Sales[Revenue]),
    SUM(SalesRevenueSummary[RevenueAllRegion])
)
```

> [!NOTE]
> Tenga cuidado y evite la divulgación de hechos confidenciales. Si solo hay dos regiones en este ejemplo, un usuario del informe puede calcular los ingresos de la otra región.

## <a name="avoid-using-rls"></a>Evitación del uso de RLS

Evite el uso de RLS, siempre que tenga sentido hacerlo. Si tiene solo un pequeño número de reglas de RLS simplista que aplican filtros estáticos, considere la posibilidad de publicar varios conjuntos de valores en su lugar. Ninguno de los conjuntos de datos define roles porque cada conjunto de datos contiene datos de un público de usuario de informes específico, que tiene los mismos permisos de datos. A continuación, cree un área de trabajo por público y asigne permisos de acceso al área de trabajo o a la aplicación.

Por ejemplo, una empresa que tiene solo dos regiones de ventas decide publicar un conjunto de datos _para cada región de ventas_ para diferentes áreas de trabajo. Los conjuntos de valores no aplican RLS. Sin embargo, usan [parámetros de consulta](/power-query/power-query-query-parameters) para filtrar los datos de origen. De este modo, el mismo modelo se publica en cada área de trabajo; solo tienen valores de parámetro de conjunto de datos diferentes. A los comerciales se les asigna acceso a solo una de las áreas de trabajo (o aplicaciones publicadas).

Hay varias ventajas asociadas con la evitación de RLS:

- **Mejor rendimiento de las consultas:** puede dar lugar a un rendimiento mejorado gracias a la reducción de filtros.
- **Modelos más pequeños:** aunque da como resultado más modelos, su tamaño es menor. Los modelos más pequeños pueden mejorar la capacidad de respuesta de la consulta y la actualización de datos, especialmente si la capacidad de hospedaje experimenta presión sobre los recursos. Además, es más fácil mantener los tamaños de modelo por debajo de los límites de tamaño impuestos por su capacidad. Por último, es más fácil equilibrar las cargas de trabajo entre diferentes capacidades, ya que puede crear áreas de trabajo en distintas capacidades —o mover áreas de trabajo a estas—.
- **Características adicionales**: se pueden usar características de Power BI que no funcionan con RLS, como [Publicar en Web](../collaborate-share/service-publish-to-web.md).

Sin embargo, hay desventajas asociadas a evitar RLS:

- **Varias áreas de trabajo:** se requiere un área de trabajo para cada audiencia de usuario de informes. Si se publican aplicaciones, también hay una aplicación por cada audiencia del usuario de informes.
- **Duplicación de contenido:** los informes y paneles se deben crear en cada área de trabajo. Su configuración y mantenimiento requiere un esfuerzo adicional, además de tiempo.
- **Usuarios con privilegios elevados:** los usuarios con privilegios elevados, que pertenecen a varias audiencias de usuarios de informes, no pueden ver una vista consolidada de los datos. Tendrán que abrir varios informes (desde diferentes áreas de trabajo o aplicaciones).

## <a name="troubleshoot-rls"></a>Solución de problemas de RLS

Si RLS produce resultados inesperados, compruebe los siguientes problemas:

- Existen relaciones incorrectas entre las tablas del modelo, en cuanto a las asignaciones de columnas y las direcciones de filtro.
- La propiedad de relación **Aplicar filtro de seguridad en ambas direcciones** no se ha configurado correctamente. Para obtener más información, vea [Instrucciones para relaciones bidireccionales](relationships-bidirectional-filtering.md).
- Las tablas no contienen datos.
- Se cargan valores incorrectos en las tablas.
- El usuario está asignado a varios roles.
- El modelo incluye tablas de agregación, y las reglas de RLS no filtran de forma coherente las agregaciones y los detalles. Para obtener más información, vea [Uso de agregaciones en Power BI Desktop (RLS para agregaciones)](../transform-model/desktop-aggregations.md#rls-for-aggregations).

Cuando un usuario específico no puede ver ningún dato, podría deberse a que su UPN no está almacenado o se ha escrito incorrectamente. Puede suceder repentinamente porque su cuenta de usuario ha cambiado como resultado de un cambio de nombre.

> [!TIP]
> Con fines de prueba, agregue una medida que devuelva la función DAX [USERNAME](/dax/username-function-dax). Puede asignarle un nombre similar a "Who Am I" (Quién soy). A continuación, agregue la medida a un objeto visual de tarjeta en un informe y publíquela en Power BI.

Cuando un usuario específico puede ver todos los datos, es posible que acceda a los informes directamente en el área de trabajo y sea el propietario del conjunto de datos. RLS solo se aplica cuando:

- El informe se abre en una aplicación.
- El informe se abre en un área de trabajo y el usuario se asigna al [rol Visor](../collaborate-share/service-new-workspaces.md#roles-in-the-new-workspaces).

## <a name="next-steps"></a>Pasos siguientes

Para obtener más información sobre este artículo, consulte los recursos siguientes:

- [Seguridad de nivel de fila (RLS) con Power BI](../admin/service-admin-rls.md)
- [Restricción del acceso a datos con seguridad de nivel de fila (RLS) en Power BI Desktop](../create-reports/desktop-rls.md)
- [Relaciones de modelos en Power BI Desktop](../transform-model/desktop-relationships-understand.md)
- ¿Tiene alguna pregunta? [Pruebe a preguntar a la comunidad de Power BI](https://community.powerbi.com/)
- ¿Sugerencias? [Ideas para contribuir a mejorar Power BI](https://ideas.powerbi.com/)