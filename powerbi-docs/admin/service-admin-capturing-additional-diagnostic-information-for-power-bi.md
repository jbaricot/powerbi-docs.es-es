---
title: Captura de información de diagnóstico para obtener soporte técnico
description: Instrucciones para recopilar manualmente información de diagnóstico del servicio Power BI Envíe esta información al soporte técnico para ayudarles a solucionar problemas.
author: kfollis
ms.author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 01/21/2021
ms.custom: seodec18
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 59e434d571c5b8d10c944bc385fb4e18ed89963c
ms.sourcegitcommit: 84f0e7f31e62cae3bea2dcf2d62c2f023cc2d404
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/26/2021
ms.locfileid: "98781388"
---
# <a name="capture-diagnostic-information-from-the-power-bi-service"></a>Captura de información de diagnóstico desde el servicio Power BI

Antes de ponerse en contacto con Soporte técnico de Microsoft para obtener ayuda con un problema con el servicio Power BI, puede recopilar archivos que nos ayuden a resolver el problema. Se recomienda obtener un seguimiento del explorador desde la sesión del explorador. Un seguimiento del explorador es un archivo de diagnóstico que puede proporcionar detalles importantes sobre lo que está ocurriendo en el servicio Power BI cuando se produce el problema.

Los administradores de Power BI pueden usar la experiencia **Ayuda y soporte técnico** en el [Centro de administración de Power Platform](https://admin.powerplatform.microsoft.com/) para obtener soluciones de autoayuda y ponerse en contacto con el soporte técnico. Los archivos de diagnóstico que se recopilan con los pasos siguientes se pueden adjuntar a la solicitud de soporte técnico para facilitar la solución de problemas. Para obtener más opciones de soporte técnico, vea [Opciones de soporte técnico de Power BI](service-support-options.md).

Para recopilar un seguimiento del explorador y otra información de la sesión, siga los pasos que se indican a continuación para el explorador que use.

## <a name="collect-a-browser-trace"></a>Recopilación de un seguimiento del explorador

> [!IMPORTANT]
>Inicie sesión en el [servicio Power BI](https://app.powerbi.com) *antes* de empezar a recopilar información de seguimiento del explorador, independientemente del explorador que use. Este paso es importante para asegurarse de que la información de seguimiento no incluye información confidencial relacionada con el inicio de sesión.

#### <a name="google-chrome-or-microsoft-edge"></a>[Google Chrome o Microsoft Edge](#tab/google-chrome-or-microsoft-edge)

Google Chrome y Microsoft Edge (Chromium) se basan en el [proyecto de código abierto de Chromium](https://www.chromium.org/Home). En los pasos siguientes se muestra cómo usar las herramientas de desarrollo, que son similares en los dos exploradores. Para obtener más información, consulte [Chrome DevTools](https://developers.google.com/web/tools/chrome-devtools) y [Herramientas de desarrollo de Microsoft Edge (Chromium)](/microsoft-edge/devtools-guide-chromium).

1. Después de iniciar sesión, presione F12 en el teclado. O bien, en Microsoft Edge, seleccione **Configuración y más (...)**  > **Más herramientas** > **Herramientas de desarrollo**. En Google Chrome, seleccione **Personaliza y controla Google Chrome** :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/chromium-icon-settings.png" alt-text="menú Configuración de Google Chrome" border="false":::. > **Más herramientas** > **Herramientas de desarrollo**.
1. Prepárese para recopilar el seguimiento del explorador estableciendo las opciones de seguimiento. También detendrá y borrará toda la información que se recopiló antes de empezar a reproducir el problema. De forma predeterminada, el explorador solo conserva la información de seguimiento de la página que está cargada actualmente. Siga estos pasos para configurar el explorador con el fin de conservar toda la información de seguimiento, incluso si la reproducción va a más de una página:
    1. En la ventana **Herramientas de desarrollo**, seleccione la pestaña **Red**. A continuación, seleccione **Conservar el registro**.
    
       :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/browser-trace-preserve-log.png" alt-text="Herramientas de desarrollo con la pestaña Red y la opción Conservar el registro seleccionadas" :::

     2. Seleccione la pestaña **Consola** y, después, seleccione **Configuración** > **Conservar el registro**. 
   
           :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/browser-trace-console-settings.png" alt-text="Herramientas de desarrollo con la pestaña Consola y la opción Conservar el registro seleccionadas" :::

        Vuelva a seleccionar **Configuración** para cerrar la **Configuración de la consola**.

3. A continuación, detenga y borre cualquier grabación en curso. Seleccione la pestaña **Red**, **Stop recording network log** (Dejar de grabar el registro de red) y después **Borrar**.
   
   :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/browser-trace-stop-recording.png" alt-text="Herramientas de desarrollo con la pestaña Red y las opciones para detener y borrar la grabación seleccionadas" :::
     
2. Ahora, reproducirá el problema que tenía en el servicio Power BI. Para empezar, en **Herramientas de desarrollo**, seleccione la pestaña **Red**. Seleccione **Record network log** (Grabar registro de red).

    > [!IMPORTANT]
    >Actualice la página del explorador en el servicio Power BI antes de empezar a reproducir el problema para que los seguimientos se capturen correctamente.

   Reproduzca los pasos que provocaron el problema para el que necesita ayuda.

     :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/browser-trace-record-network-log.png" alt-text="Herramientas de desarrollo con la pestaña Red y la opción para grabar el registro de red seleccionadas" :::

    Cuando reproduzca el problema, verá un resultado similar al de la siguiente imagen en la ventana **Herramientas de desarrollo**.

    :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/browser-trace-output.png" alt-text="Herramientas de desarrollado con la pestaña Red en la que se muestra la salida de la sesión" :::.
    
3. Después de reproducir el comportamiento del problema, debe guardar los archivos de registro y adjuntarlos a la solicitud de soporte técnico.
    1. Para exportar el registro de red, en **Herramientas de desarrollo**, seleccione la pestaña **Red**. Seleccione **Stop recording network log** (Dejar de grabar el registro de red). A continuación, seleccione **Exportar HAR...** y guarde el archivo.

         :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/browser-trace-export-har.png" alt-text="Herramientas de desarrollo con la pestaña Red y las opciones para detener la grabación y exportar HAR seleccionadas" :::

    2. Para exportar la salida de la consola, en **Herramientas de desarrollo**, seleccione la pestaña **Consola**. Haga clic con el botón derecho en un mensaje que se muestra, seleccione **Guardar como...** y guarde la salida de la consola como un archivo de texto.
    
         :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/browser-trace-save-as.png" alt-text="Herramientas de desarrollo con la pestaña Consola seleccionada y la opción Guardar como mostrada" :::

   Empaquete el archivo HAR guardado, la salida de la consola y la grabación de pantalla en un formato comprimido, como .zip, y adjunte el archivo a la solicitud de soporte técnico.

#### <a name="apple-safari"></a>[Apple Safari](#tab/apple-safari)

En los pasos siguientes se muestra cómo usar las herramientas de desarrollo en Apple Safari. Para obtener más información, consulte [Introducción a las Herramientas de desarrollo de Safari](https://support.apple.com/guide/safari-developer/safari-developer-tools-overview-dev073038698/11.0/mac).

1. Después de iniciar sesión, habilite las herramientas de desarrollo en Apple Safari:
    1. En el encabezado de página, seleccione **Safari** > **Preferencias**.
    
       :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/safari-preferences.png" alt-text="Menú de Apple Safari con la opción Preferencias seleccionada" :::

    2. Seleccione **Avanzado** y, después, **Mostrar el menú Desarrollo en la barra de menús** para habilitar las herramientas de desarrollo.
    
       :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/safari-show-develop-menu.png" alt-text="Menú Avanzado de Safari con la opción Mostrar el menú Desarrollo en la barra de menús seleccionada" :::

2. A continuación, establecerá las opciones en el **inspector web** para permitir que el explorador mantenga toda la información de seguimiento. De forma predeterminada, el explorador solo conserva la información de seguimiento de la página que está cargada actualmente. Esta configuración garantiza que la información de seguimiento se recopila incluso si la reproducción requiere ir a más de una página.

    1. Seleccione **Desarrollo** > **Mostrar inspector web**.
    
        :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/safari-web-inspector.png" alt-text="Menú Desarrollo con la opción Mostrar inspector web seleccionada" :::

    2. Seleccione **Red** > **Conservar registro**.
       
         :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/safari-network-preserve-log.png" alt-text="Menú del inspector web con las opciones Red y Conservar registro seleccionadas" :::

    1. Seleccione **Consola** > **Conservar registro**.
   
       :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/safari-console-preserve-log.png" alt-text="Menú del inspector web con las opciones Consola y Conservar registro seleccionadas" :::

3. Una vez establecidas las opciones, seleccione **Red** > **Borrar elementos de red** para asegurarse de que los registros contienen solo los detalles sobre la reproducción del problema.

    :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/safari-clear-network-items.png" alt-text="Menú del inspector web con las opciones Red y Borrar elementos de red seleccionadas" :::


4. Ahora está listo para reproducir el problema. 
    > [!IMPORTANT]
    >Actualice la página del explorador en el servicio Power BI antes de empezar a reproducir el problema para que los seguimientos se capturen correctamente.

    Siga los pasos para reproducir el problema que tiene. Cuando reproduzca el problema, verá un resultado similar al de la siguiente imagen en la ventana **Red**.

    :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/safari-session-output.png" alt-text="Ventana Red en la que se muestra la salida de ejemplo" :::.

5. Después de reproducir el comportamiento del problema, debe guardar los archivos de registro y adjuntarlos a la solicitud de soporte técnico.

    1. Para exportar el registro de red, en la pestaña **Red**, seleccione **Exportar** y guarde el archivo en formato HAR.

         :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/safari-export.png" alt-text="Pestaña Red con la opción de exportación seleccionada" :::

    2. Para exportar la salida de la consola, en el panel de herramientas **Desarrollo**, seleccione la pestaña **Consola** y expanda la ventana. Coloque el cursor al principio del resultado de la consola y, a continuación, arrastre y seleccione todo el contenido del resultado. Use Comando-C para copiar el resultado y guárdelo en un archivo de texto.

   Empaquete el archivo HAR guardado, la salida de la consola y la grabación de pantalla en un formato comprimido, como .zip, y adjunte el archivo a la solicitud de soporte técnico.

#### <a name="firefox"></a>[Firefox](#tab/firefox)

En los pasos siguientes se muestra cómo usar las herramientas de desarrollo en Firefox. Para más información, vea [Herramientas de desarrollo de Firefox](https://developer.mozilla.org/docs/Tools).

1. Después de iniciar sesión, presione F12 en el teclado. O bien, en Firefox, seleccione el **menú Abrir** :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/firefox-menu.png" alt-text="icono del menú de Firefox" border="false"::: > **Desarrollador web** > **Alternar herramientas**. Las herramientas aparecen en la parte inferior de la pantalla.

1. A continuación, establecerá las opciones en el **Inspector** para permitir que el explorador mantenga toda la información de seguimiento. De forma predeterminada, el explorador solo conserva la información de seguimiento de la página que está cargada actualmente. Esta configuración garantiza que la información de seguimiento se recopila incluso si la reproducción requiere ir a más de una página.

    1. En la ventana **Inspector**, seleccione la pestaña **Red**. A continuación, seleccione **Registros persistentes**.
    
       :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/firefox-network-persist-logs.png" alt-text="Herramientas del inspector con la pestaña Red y la opción Registros persistentes seleccionadas" :::

     2. Seleccione la pestaña **Consola** y, después, seleccione **Configuración de la consola** > **Registros persistentes**. 
   
           :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/firefox-console-persist-logs.png" alt-text="Herramientas del inspector con la pestaña Consola y la opción Registros persistentes seleccionadas" :::

3. Una vez establecidas las opciones, borre cualquier grabación en curso. Seleccione la pestaña **Red** y, después, **Borrar**.
   
   :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/browser-trace-stop-recording.png" alt-text="Herramientas de desarrollo con la pestaña Red y las opciones para detener y borrar la grabación seleccionadas" :::
     
2. Ahora está listo para reproducir el problema. 
    > [!IMPORTANT]
    >Actualice la página del explorador en el servicio Power BI antes de empezar a reproducir el problema para que los seguimientos se capturen correctamente.
 
    Siga los pasos para reproducir el problema que tiene.
    
3. Después de reproducir el comportamiento del problema, debe guardar los archivos de registro y adjuntarlos a la solicitud de soporte técnico.
    1. Para exportar el registro de red, seleccione **Red** > **Importar/Exportar archivo HAR** y, después, **Guardar todo como HAR**.

         :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/firefox-save-har.png" alt-text="Pestaña Red con el menú Importar/Exportar archivo HAR y Guardar todo como HAR seleccionados" :::

    2. Para exportar la salida de la consola, seleccione la pestaña **Consola**. Haga clic con el botón derecho en un mensaje que se muestra, seleccione **Exportar mensajes visibles a** y guarde la salida de la consola como un archivo de texto.
    
         :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/firefox-export-visible-messages.png" alt-text="Pestaña Consola seleccionada y opción Exportar mensajes visibles a mostrada" :::

   Empaquete el archivo HAR guardado, la salida de la consola y la grabación de pantalla en un formato comprimido, como .zip, y adjunte el archivo a la solicitud de soporte técnico.

---

Después de recopilar los archivos de diagnóstico, adjúntelos a la solicitud de soporte técnico para ayudar al ingeniero de soporte técnico a solucionar el problema. El archivo HAR contendrá toda la información sobre las solicitudes de red entre la ventana del explorador y el servicio Power BI, por ejemplo:

* Los identificadores de actividad de cada solicitud.

* La marca de tiempo precisa de cada solicitud.

* Cualquier información de error devuelta al cliente.

Este seguimiento también contendrá los datos usados para completar los elementos visuales que se muestran en la pantalla.

## <a name="next-steps"></a>Pasos siguientes

* [Seguimiento del estado del servicio Power BI en Microsoft 365](service-admin-health.md)
* [Habilitación de las notificaciones de interrupción del servicio](service-interruption-notifications.md)
* [Unirse a la Comunidad de Power BI](https://community.powerbi.com/)
