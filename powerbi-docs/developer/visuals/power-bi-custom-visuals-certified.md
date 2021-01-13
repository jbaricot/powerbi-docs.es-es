---
title: Objetos visuales de Power BI certificados en análisis integrados de Power BI para obtener una mejor información de BI insertada
description: Requisitos y proceso para enviar un objeto visual personalizado para que se certifique y una lista de objetos visuales de Power BI certificados. Consiga mejores conclusiones insertadas de BI con los análisis insertados de Power BI.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: how-to
ms.date: 03/08/2020
ms.openlocfilehash: 5f337197655d41b830b237c04faa2642991c34ee
ms.sourcegitcommit: a5e98bc86915f7bea6a0ab5df282683840e63d2c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/07/2021
ms.locfileid: "97969820"
---
# <a name="get-a-power-bi-visual-certified"></a>Obtención de un objeto visual de Power BI certificado

Los objetos visuales de Power BI certificados son objetos visuales de Power BI de [AppSource](https://appsource.microsoft.com/en-us/marketplace/apps?page=1&product=power-bi-visuals) que cumplen los [requisitos de código](#certification-requirements) del equipo de Microsoft Power BI. Estos objetos visuales se prueban para confirmar que no acceden a recursos o servicios externos y que siguen patrones y directrices de codificación seguros.

Una vez que un objeto visual de Power BI está certificado, ofrece más características. Por ejemplo, puede [exportar el objeto visual a PowerPoint](../../consumer/end-user-powerpoint.md) o mostrarlo en los correos electrónicos recibidos, cuando un usuario [se suscribe a páginas del informe](../../consumer/end-user-subscribe.md).

El proceso de certificación es opcional. Que un objeto visual de Power BI no esté certificado no significa necesariamente que sea poco seguro. Algunos objetos visuales de Power BI no están certificados porque no cumplen uno o varios de los [requisitos de certificación](power-bi-custom-visuals-certified.md#certification-requirements). Por ejemplo, un objeto visual de Power BI de mapa que conecta con un servicio externo o un objeto visual de Power BI que usa bibliotecas comerciales.

> [!NOTE]
> Microsoft no es autor de los objetos visuales de Power BI de terceros. Para comprobar la funcionalidad de objetos visuales de terceros, póngase en contacto directamente con el autor del objeto visual.

## <a name="certification-requirements"></a>Requisitos de certificación

Para [certificar](#get-a-power-bi-visual-certified) un objeto visual de Power BI, este debe cumplir los requisitos indicados en esta sección. 

### <a name="general-requirements"></a>Requisitos generales

El Centro de partners debe aprobar el objeto visual de Power BI. Se recomienda que el objeto visual de Power BI ya esté en [AppSource](https://appsource.microsoft.com/marketplace/apps?page=1&product=power-bi-visuals). Para aprender a publicar un objeto visual de Power BI en AppSource, consulte [Publicación de objetos visuales de Power BI en el Centro de partners](office-store.md).

Antes de enviar el objeto visual de Power BI para que se certifique, compruebe que cumple las [directrices de los objetos visuales de Power BI](guidelines-powerbi-visuals.md).

Al enviar el objeto visual de Power BI, asegúrese de que el paquete compilado coincida exactamente con el paquete enviado.

### <a name="code-repository-requirements"></a>Requisitos del repositorio de código

Aunque no tiene que compartir el código públicamente en GitHub, el repositorio de código tiene que estar disponible para que lo revise el equipo de Power BI. La mejor manera de hacerlo consiste en proporcionar el código fuente (JavaScript o TypeScript) en GitHub.

El repositorio debe cumplir con los siguientes requisitos:
* Código para un solo objeto visual de Power BI. No puede contener código de varios objetos visuales de Power BI o código no relacionado.
* Una rama llamada **certificación** (en minúscula). El código fuente de esta rama tiene que coincidir con el del paquete enviado. Este código solo se puede actualizar durante el siguiente proceso de envío, si va a volver a enviar el objeto visual de Power BI.

Si el objeto visual de Power BI usa paquetes NPM privados o submódulos de Git, debe proporcionar acceso a los repositorios adicionales que contienen este código.

Para saber cuál es el aspecto de un repositorio de objetos visuales de Power BI, revise el repositorio de GitHub para obtener el [gráfico de barras de ejemplo de objetos visuales de Power BI](https://github.com/microsoft/PowerBI-visuals-sampleBarChart).

### <a name="file-requirements"></a>Requisitos de archivos

Use la versión más reciente de la API para escribir el objeto visual de Power BI.

El repositorio debe incluir los siguientes archivos:
* **.gitignore**: agregue `node_modules`, `.tmp` y `dist` a este archivo. El código no puede incluir las carpetas *node_modules*, *.tmp* o *dist*.
* **capabilities.json**: si va a enviar una versión más reciente del objeto visual de Power BI con cambios en las propiedades de este archivo, compruebe que no interrumpe los informes de los usuarios existentes.
* **pbiviz.json** 
* **package.json**. El objeto visual debe tener instalados el siguiente paquete:
   * ["tslint"](https://www.npmjs.com/package/tslint): versión 5.18.0 o superior
   * ["typescript"](https://www.npmjs.com/package/typescript): versión 3.0.0 o superior
   * ["tslint-microsoftcontrib"](https://www.npmjs.com/package/tslint-microsoft-contrib): versión 6.2.0 o superior
   * El archivo debe contener un comando para ejecutar linter: `"lint": "tslint -c tslint.json -p tsconfig.json"`
* **package-lock.json**
* **tsconfig.json**

### <a name="command-requirements"></a>Requisitos de comandos

Asegúrese de que los siguientes comandos no devuelven errores.

* `npm install`
* `pbiviz package`
* `npm audit`: no debe devolver ninguna advertencia de nivel alto o moderado.
* [TSlint de Microsoft](https://www.npmjs.com/package/tslint-microsoft-contrib) con la [configuración requerida](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/blob/master/tslint.json). Este comando no debe devolver ningún error de lint.

### <a name="compiling-requirements"></a>Requisitos de compilación

Use la versión más reciente de [powerbi-visuals-tools](https://www.npmjs.com/package/powerbi-visuals-tools) para escribir el objeto visual de Power BI.

Debe compilar el objeto visual de Power BI con `pbiviz package`. Si va a usar sus propios scripts de compilación, proporcione un comando de compilación `npm run package` personalizado.

### <a name="source-code-requirements"></a>Requisitos del código fuente

Compruebe que sigue la lista de directivas de [certificación adicional de objetos visuales de Power BI](/legal/marketplace/certification-policies#1200-power-bi-visuals-additional-certification). Si el envío no sigue estas directrices, el correo electrónico de rechazo del Centro de partners incluirá los números de la directiva que aparecen en este vínculo.

Siga los requisitos de código que se enumeran a continuación para asegurarse de que el código está en línea con las directivas de certificación de Power BI.  

**Obligatorio**
* Use solo componentes públicos de OSS que se puedan revisar, como bibliotecas JavaScript o TypeScript públicas.
* El código debe admitir la [API de representación de eventos](event-service.md).
* Asegúrese de que DOM se manipule de forma segura. Use el saneamiento de los datos de usuario o de entrada de usuario antes de agregarlos a DOM.
* Use el [informe de ejemplo](https://github.com/PowerBi-Projects/PowerBI-visuals/tree/gh-pages/assets) como conjunto de datos de prueba.

**No permitido**
* Acceder a recursos o servicios externos. Por ejemplo, ninguna solicitud HTTP/S ni WebSocket puede salir de Power BI a ningún servicio.
* Usar `innerHTML` o `D3.html(user data or user input)`.
* Errores o excepciones de JavaScript en la consola del explorador, en los datos de entrada.
* Código arbitrario o dinámico como `eval()`, uso no seguro de `settimeout()`, `requestAnimationFrame()`, `setinterval(user input function)` y datos de usuarios o de entrada de usuario.
* Archivos o proyectos de JavaScript reducidos.

## <a name="submitting-a-power-bi-visual-for-certification"></a>Envío de un objeto visual de Power BI para certificación

Puede solicitar que el equipo de Power BI certifique su objeto visual de Power BI mediante el Centro de partners.

>[!TIP]
>El proceso de certificación de Power BI puede tardar un tiempo. Si va a crear un objeto visual de Power BI, se recomienda publicarlo a través del Centro de partners antes de solicitar la certificación de Power BI. Esto garantiza que la publicación del objeto visual no se retrase.

Para solicitar la certificación de Power BI:

1. Inicie sesión en el Centro de datos.
2. En la página **Información general**, elija su objeto visual de Power BI y vaya a la página de configuración del **producto**.
3. Active la casilla **Request Power BI certification** (Solicitar la certificación de Power BI).
4. En la página **Revisar y publicar**, en el cuadro de texto **Notas para la certificación**, proporcione un vínculo al código fuente y las credenciales necesarias para acceder a él.

### <a name="private-repository-submission-process"></a>Proceso de envío de un repositorio privado

Si utiliza un repositorio privado como GitHub para enviar el objeto visual de Power BI para su certificación, siga las instrucciones de esta sección.
1. Cree una cuenta para el equipo de validación.
2. Configure la [autenticación en dos fases](https://help.github.com/github/authenticating-to-github/securing-your-account-with-two-factor-authentication-2fa) para la cuenta.
3. [Genere un nuevo conjunto de códigos de recuperación](https://help.github.com/github/authenticating-to-github/configuring-two-factor-authentication-recovery-methods#generating-a-new-set-of-recovery-codes).
4. Al enviar el objeto visual de Power BI, proporcione lo siguiente:
    * Un vínculo al repositorio
    * Las credenciales de inicio de sesión (incluida una contraseña)
    * Los códigos de recuperación
    * Los permisos de solo lectura para nuestra cuenta ([pbicvsupport](https://github.com/pbicvsupport))

## <a name="certified-power-bi-visual-badges"></a>Distintivos de objetos visuales de Power BI certificados

Una vez certificado un objeto visual de Power BI, obtiene un distintivo designado que indica que está certificado.

### <a name="certified-power-bi-visuals-in-appsource"></a>Objetos visuales de Power BI certificados en AppSource

* Al buscar en línea [objetos visuales de Power BI en AppSource](https://appsource.microsoft.com/marketplace/apps?product=power-bi-visuals), un pequeño distintivo amarillo en la tarjeta del objeto visual indica que se trata de un objeto visual de Power BI certificado.

    ![Objeto visual de Power BI certificado de AppSource](media/power-bi-custom-visuals-certified/certified-visual-yellow-small.png)

* Después de hacer clic en la tarjeta del objeto visual de Power BI, un distintivo amarillo titulado *PBI Certified* indica que este objeto visual de Power BI está certificado.

    ![Objeto visual de Power BI certificado de la página de la aplicación](media/power-bi-custom-visuals-certified/certified-visual-yellow-big.png)

### <a name="certified-power-bi-visuals-in-the-power-bi-interface"></a>Objetos visuales de Power BI certificados en la interfaz de Power BI

* Al importar un objeto visual de Power BI desde dentro de Power BI (escritorio o servicio), un distintivo azul indica que el objeto visual de Power BI está certificado.

    ![Objeto visual de Power BI certificado de la interfaz de Power BI](media/power-bi-custom-visuals-certified/certified-visual-blue.png)

* Puede mostrar solo los objetos visuales de Power BI certificados seleccionando la opción de filtro *Certificado por Power BI*.

## <a name="publication-timeline"></a>Plazos de publicación

La implementación en AppSource es un proceso que puede tardar cierto tiempo. El objeto visual de Power BI estará disponible para su descarga en AppSource cuando este proceso haya finalizado.

### <a name="when-will-users-be-able-to-download-my-visual"></a>¿Cuándo podrán los usuarios descargar el objeto visual?

* Si es la primera vez que envía un objeto visual de Power BI, estará listo para descargarlo unas horas después de que reciba un correo electrónico de AppSource.

* Si ha enviado una actualización de un objeto visual de Power BI existente, los usuarios podrán descargarla en el plazo de un mes desde su envío.

    >[!NOTE]
    > El campo *versión* de AppSource se actualizará con el día en que AppSource aprobó el objeto visual de Power BI, aproximadamente una semana después de haber enviado el objeto visual. Los usuarios podrán descargar el objeto visual actualizado, pero las características actualizadas no surtirán efecto. Las nuevas capacidades del objeto visual afectarán a los informes de los usuarios transcurrido un mes aproximadamente. 

### <a name="when-will-my-power-bi-visual-display-a-certification-badge"></a>¿Cuándo mostrará el objeto visual de Power BI un distintivo de certificación?

* Si ha enviado un objeto visual de Power BI por primera vez, el distintivo de certificación aparecerá en el plazo de un día desde que reciba el correo electrónico de aprobación de AppSource.

* Si está solicitando la certificación de un objeto visual de Power BI, el distintivo de certificación estará visible en el plazo de un mes de su envío.

## <a name="next-steps"></a>Pasos siguientes

* Si es desarrollador web y está interesado en crear sus propios objetos visuales de Power BI y agregarlos a  [Microsoft AppSource](https://appsource.microsoft.com), empiece con el tutorial  [Desarrollo de un objeto visual Circle Card de Power BI](develop-circle-card.md).

* Para obtener más información sobre los objetos visuales, vea las [preguntas más frecuentes sobre objetos visuales certificados](power-bi-custom-visuals-faq.md#certified-power-bi-visuals).

* [Lista de reproducción sobre objetos visuales de Power BI de Microsoft en YouTube](https://www.youtube.com/playlist?list=PL1N57mwBHtN1vIjfvuBIzZllrmKo-Vz6x)

* [Objetos visuales en Power BI](power-bi-custom-visuals.md)

* [Publicación de objetos visuales de Power BI en Microsoft AppSource](office-store.md)

* ¿Tiene más preguntas? [Pruebe la comunidad de Power BI](https://community.powerbi.com/)
