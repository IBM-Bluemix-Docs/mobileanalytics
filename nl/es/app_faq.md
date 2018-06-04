---

copyright:
  years: 2015, 2017
lastupdated: "2018-02-19"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}


# Preguntas más frecuentes 
{: #faq}


1. **¿Qué es {{site.data.keyword.mobileanalytics_full}}?**
	
	{{site.data.keyword.mobileanalytics_full}} es un servicio que proporciona información histórica en tiempo real sobre el rendimiento de las aplicaciones para móviles y cómo se utilizan. Utilizando {{site.data.keyword.mobileanalytics_short}}, los desarrolladores de aplicaciones y los propietarios de aplicaciones pueden tomar decisiones de control de datos supervisando tendencias en usuarios activos, sesiones, plataformas móviles y bloqueos de aplicación. También puede establecer alertas sobre métricas seleccionadas que, una vez desencadenadas, envían mensajes a cualquier punto final de REST, incluido un servicio de envío por push o los servicios de mensajería interna.


2. **¿Qué puedo hacer con {{site.data.keyword.mobileanalytics_short}} para {{site.data.keyword.Bluemix_notm}}?**

	Como gestor de producto de la aplicación para móviles, puede ver cuánta gente utilizar su aplicación (métricas de usuario) y cuándo la utilizan (métricas de sesión). Esta información se presenta como una serie temporal y se actualiza en tiempo real para que pueda ver el efecto de los cambios realizados en la aplicación. Puede filtrar para ver versiones específicas de la aplicación o sistemas operativos para tomar decisiones sobre el proceso de desuso y priorización. 
	
	Como usuario de marketing de aplicaciones para móvil, puede utilizar métricas de usuario y sesión para supervisar la colaboración, gestionar la rotación y evaluar la eficacia de las tareas de marketing de aplicaciones para móviles observando los cambios a lo largo del tiempo y correlacionando con sus fechas de sucesos.
	
	Como desarrollador de aplicaciones para móviles, puede utilizar las métricas de bloqueos para descubrir y resolver problemas de rendimiento de aplicaciones para móviles antes de que decepcionen a los usuarios y dañen la reputación de la aplicación. Puede supervisar el recuento de bloqueos y el índice de bloqueos desde la consola de análisis y puede priorizar los bloqueos que afectan a la mayoría de los usuarios. Puede establecer alertas para enviar notificaciones o realizar acciones automatizadas cuando los bloqueos exceden un umbral determinado y puede resolver problemas accediendo a los detalles sobre las instancias de bloqueo para ver los registros de dispositivo y los seguimientos de pila de la aplicación.
	
	Asegúrese de que no comparte información personal mediante {{site.data.keyword.mobileanalytics_short}}.

3. **¿Necesito habilidades de analista de datos para utilizar Mobile Analytics?**

	No, {{site.data.keyword.mobileanalytics_short}} ofrece una consola de análisis lista para usar para las partes interesadas del negocio y los desarrolladores de aplicaciones. No es necesario poseer habilidades de consulta.

4. **¿Puede realizar consultas personalizadas en mis datos analíticos?**

    {{site.data.keyword.mobileanalytics_short}} no permite realizar consultas personalizadas, pero existe una consideración sobre esta característica en el futuro.
	
5. **¿Cómo puedo conectar mi aplicación a {{site.data.keyword.mobileanalytics_short}}?**

    [Descargue nuestro SDK para iOS o Android de código abierto](install-client-sdk.html), o utilice {{site.data.keyword.mobileanalytics_short}} [API REST](https://mobile-analytics-dashboard.{DomainName}/analytics-service/) para otras plataformas. 

6. **¿En qué regiones de IBM Cloud está disponible Mobile Analytics?**

    Actualmente, Mobile Analytics está disponible en Estados Unidos - Sur y en el Reino Unido. La disponibilidad en otras regiones está planificada pero todavía no se ha determinado el periodo de tiempo.

7. **¿Cuánto cuesta este servicio?**

    Los 100 primeros millones de sucesos que se recopilan cada mes son gratuitos y, a partir de esa cantidad, el coste es de 1 $ por millón de sucesos.
	
8. **¿Qué es un suceso?**

    Los sucesos actuales incluyen inicio de sesión de aplicación, fin de sesión de aplicación (incluido bloqueo de la aplicación), notificaciones de alertas y entradas de registro.
	
9. **¿Cómo puedo calcular cuándo me costará el servicio al mes?**

    Puesto que el precio depende del número de sucesos que se envían al servicio por cuenta de cliente, estimar el precio significa estimar la cantidad de sucesos.  
	
	El importe que se le cargará es la suma de sucesos de todas las aplicaciones que tenga conectadas a {{site.data.keyword.mobileanalytics_short}}. Para una determinada aplicación, el número de sucesos depende del grado de preparación que haya implementado dentro de la aplicación, del número de usuarios y del nivel de actividad de los usuarios. 
	
	Utilice esta fórmula para calcular el uso:
sucesos por mes por app = (usuarios por día)(sesiones por usuario por día)(días al mes)(sucesos por sesión)
	
	Los sucesos por sesión pueden oscilar entre 2 y varios cientos, en función de las llamadas de red, analíticas personalizadas, capturas de registro y definiciones de alerta que haya configurado el desarrollador en la aplicación.

9. **¿Cuánto tiempo se conservan mis datos analíticos?**

    Los datos se conservan al menos durante 30 días.
	
10. **¿Cuánto tiempo tardan los datos en visualizarse en la consola de {{site.data.keyword.mobileanalytics_short}}?**

    Los datos en la consola de {{site.data.keyword.mobileanalytics_short}} son casi en tiempo real, lo que significa que los datos se visualizan en un periodo de segundos de los sucesos reales.
	
11. **¿Qué diferencia hay entre {{site.data.keyword.mobileanalytics_full}} y Mobile Analytics de MobileFirst Platform Foundation?**

    El usuario y la sesión son similares a estas dos consolas, pero la analítica que se entrega con MobileFirst Platform Foundation contiene configuraciones y métricas adicionales que permiten a los clientes gestionar su propio clúster de análisis localmente. Además, la consola de analíticas de MobileFirst Platform Foundation desglosa las métricas para adaptadores y procedimientos de adaptadores, mientras que en el servicio {{site.data.keyword.mobileanalytics_short}}, estas métricas se integran en tablas y gráficos de solicitudes de red.
	
12. **Estoy utilizando MobileFirst Platform Foundation localmente para desarrollar mis apps, pero no deseo alojar mi propio clúster de análisis. ¿Puedo utilizar {{site.data.keyword.mobileanalytics_full}} en su lugar?**

    Sí. Dispone de un par de opciones: si está utilizando MobileFirst Platform Foundation 7.x u 8.0 y sus apps están instrumentadas con SDK de MobileFirst Platform, puede configurar el servidor de MobileFirst para notificar datos de análisis a {{site.data.keyword.mobileanalytics_short}} para {{site.data.keyword.Bluemix_notm}}. Lea la publicación del blog [Configuring Mobile Analytics and Mobile Foundation IBM Cloud services ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://mobilefirstplatform.ibmcloud.com/blog/2016/07/11/analytics-bm-service/){: new_window} para ver más detalles. Como alternativa, puede instrumentar las apps utilizando el SDK de {{site.data.keyword.mobileanalytics_short}} de {{site.data.keyword.Bluemix_notm}} y notificar directamente al servicio {{site.data.keyword.mobileanalytics_short}}.
