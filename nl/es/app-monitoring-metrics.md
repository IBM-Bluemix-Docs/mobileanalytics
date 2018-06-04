---

copyright:
  years: 2015, 2017
lastupdated: "2017-08-06"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# Uso de métricas y eventos
{: #usingmetrics}

## Supervisión de aplicaciones con Mobile Analytics

{{site.data.keyword.mobileanalytics_full}} proporciona funciones de supervisión y analíticas para sus aplicaciones móviles. Puede grabar registros de aplicaciones y supervisar datos con el SDK de cliente de {{site.data.keyword.mobileanalytics_short}}. Los desarrolladores pueden elegir cuándo desean enviar estos datos al servicio {{site.data.keyword.mobileanalytics_short}}. Al entregar los datos a {{site.data.keyword.mobileanalytics_short}}, puede utilizar la consola de {{site.data.keyword.mobileanalytics_short}} para obtener información analítica sobre las aplicaciones móviles, los dispositivos y los registros de la aplicación.
{: shortdesc}

##Métricas predefinidas

Gracias a las **métricas predefinidas** puede responder a las siguientes preguntas:

* ¿Cuántos usuarios nuevos tengo?  
* ¿Cuántas personas utilizan mi aplicación de forma activa?  
* ¿Con qué frecuencia utilizan mi aplicación? 
* ¿A qué hora del día utilizan mi aplicación?  
* ¿Qué modelos de dispositivo prefieren mis usuarios? 
* ¿Cuándo debería anular el soporte para los sistemas operativos existentes? 
* ¿Qué aplicaciones tienen problemas de rendimiento?  

##Eventos personalizados

Al añadir sus propios **sucesos personalizados**, puede responder a las siguientes preguntas: 

* ¿Qué características se utilizan más y cuáles menos?  
* ¿Desde dónde entran y salen los usuarios de mi app?  
* ¿Qué actividades ven más los usuarios?  
* ¿Completan los usuarios los flujos de trabajo de la app (por ejemplo, canalizaciones de conversión)?   

Los registros de lado del cliente y los datos de uso se recopilan automáticamente y se envían al servicio Mobile Analytics a petición. Los desarrolladores y administradores pueden utilizar el panel de control de servicio {{site.data.keyword.mobileanalytics_short}} para ver datos recopilados por el SDK de cliente.

## Visualización de datos
{: data-visualization notoc}

Todos los datos recopilados por el servicio de análisis se pueden visualizar mediante el panel de control de {{site.data.keyword.mobileanalytics_short}}, al que se puede acceder desde el panel de control de {{site.data.keyword.Bluemix_notm}} pulsando la instancia de mosaico de servicio {{site.data.keyword.mobileanalytics_short}} de IBM. <!--You can also create custom charts, based on data that is collected by the analytics service in the dashboard.--> Además de una vista rápida de los análisis móviles, la función de análisis incluye la capacidad de realizar una búsqueda en bruto en los registros de clientes, en los datos de bloqueo de los clientes capturados, y cualquier dato adicional que proporcione de forma explícita mediante las llamadas de la función API del cliente que proveen al servicio {{site.data.keyword.mobileanalytics_short}}. 

