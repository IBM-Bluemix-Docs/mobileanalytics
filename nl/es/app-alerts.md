---

copyright:
  years: 2015, 2017
lastupdated: "2017-08-06"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# Configuración de alertas
{: #alerts}

## Establecimiento de alertas con Mobile Analytics 

Puede establecer umbrales en las definiciones de alerta en la consola de {{site.data.keyword.mobileanalytics_short}} para supervisar mejor las actividades.

Puede configurar umbrales que, si se superan, activan alertas para notificar al monitor de la consola de {{site.data.keyword.mobileanalytics_short}}. Las alertas activadas se pueden visualizar en la consola o bien se pueden gestionar con un webhook personalizado. <!-- This feature provides a proactive means of detecting app log errors, server log errors, extended periods of network latency, and authentication failures.--> Gracias a esta función, se pueden detectar de forma proactiva errores y detenciones anómalas de la aplicación en los registros de cliente. Gracias a los umbrales y las alertas reactivos, no hace falta que examine a conciencia los datos y puede establecer umbrales con un espectro de granularidad amplio.

## Creación de una definición de alerta para registros de aplicaciones
{: #alert-def-client-logs notoc}

Puede crear una definición de alerta basada en registros de aplicaciones.

En este ejemplo, utilice los datos de registro de la aplicación para crear una definición de alerta. La alerta supervisa todos los registros de aplicaciones recibidos en los últimos 5 minutos y sigue efectuando comprobaciones cada 5 minutos hasta que se inhabilita o se suprime la definición de alerta. Se activa una alerta para cada dispositivo que ha enviado 3 o más registros de error de aplicación con el mismo nombre y la misma versión de la aplicación.

1. En la consola de {{site.data.keyword.mobileanalytics_short}}, pulse **Definiciones** para ir a la página Definiciones de alertas.
2. Pulse **Crear alerta** para crear una alerta.
3. Indique los siguientes valores:
	* Nombre de alerta: alerta para registros de app
	* Mensaje: alerta de mensaje de error
	* Frecuencia de consulta: 5 minutos
	* Tipo de evento: registros de app
		* Propiedad: nivel de registro
			* Valor: error
			* Umbral
				* Tipo de umbral: total para instancia de aplicación

					**Nota**: Si elige la opción Promedio para aplicación, se calcula el promedio de los registros de app por el número de dispositivos. Por ejemplo, si tiene dos dispositivos y uno envía seis registros de app, mientras que el otro envía tres, la media será de 4,5 registros de app.
				* Operador: es igual o mayor que 3
	<!-- insert alert definition tab image? -->

4. Pulse **Siguiente** y proporcione el siguiente valor:
	* Método: solo consola de analíticas

		**Nota**: Elija la opción Consola de analíticas y POST de red si también desea enviar un mensaje POST con una carga útil JSON a su dirección URL personalizada. Si elige esta opción, estarán disponibles los siguientes campos:
		* URL POST de red
        * Cabeceras
        * Tipo de autenticación
5. Pulse **Guardar**.

Ha creado una definición de alerta para activar una alerta al término de cada intervalo de 5 minutos si los registros de app alcanzan el umbral de 3 o más registros de error.

## Creación de una definición de alerta para bloqueos de aplicaciones
{: #alert-def-app-crash notoc}

Puede crear una definición de alerta basada en bloqueos de aplicaciones.

En este ejemplo se utilizan los datos de bloqueo de aplicaciones para crear una definición de alerta. La alerta supervisa todos los bloqueos de aplicaciones de los últimos 2 minutos y sigue efectuando comprobaciones cada 2 minutos hasta que se inhabilita o se suprime la definición de alerta. Se activa una alerta para cada aplicación bloqueada 5 o más veces. Para obtener más información sobre los bloqueos de aplicaciones, consulte [Bloqueos de aplicaciones](#app_crash).

1. En la consola de {{site.data.keyword.mobileanalytics_short}}, pulse **Definiciones** para mostrar la página Definiciones de alertas.
2. Pulse **Crear alerta**.
3. Indique los siguientes valores:
	* Nombre de la alerta: alerta para bloqueos de aplicaciones
	* Mensaje: alerta de bloqueo de app
	* Frecuencia de consulta: bloqueos de aplicación
		* Frecuencia de consulta: 2 minutos
	* Tipo de evento: bloqueos de aplicación
		* Nombre de la aplicación: cualquier aplicación
		* Versión de la aplicación: cualquier versión
    * Umbral
      * Tipo de umbral: recuento de bloqueos
      * Operador: es igual o mayor que 5
4. Pulse el separador **Método de distribución** e indique el siguiente valor:
  * Método: solo consola de analíticas

    **Nota**: Elija la opción **Consola de analíticas y POST de red** si también desea enviar un mensaje POST con una carga útil JSON a su dirección URL personalizada. Si elige esta opción, estarán disponibles los siguientes campos:
      * URL POST de red (obligatorio)
      * Cabeceras (opcional)
      * Tipo de autenticación (obligatorio)
5. Pulse **Guardar**.

## Gestión de definiciones de alerta
{: #managing-alert-definitions notoc}

En este ejemplo se gestionan las definiciones de alerta desde la página Gestión de alertas.

1. En la consola de {{site.data.keyword.mobileanalytics_short}}, pulse **Registros**. Esta acción abre la página Registros de alertas.
2. Opcional: Marque o desmarque el recuadro de selección de la columna **Habilitado** para habilitar o inhabilitar una definición de alerta en concreto.
3. Opcional: Pulse el icono **Duplicar** si desea crear una copia de una definición de alerta y cambiar algunos valores.
4. Opcional: Pulse el icono **Lápiz** si desea editar una definición de alerta.
5. Opcional: Pulse el icono **Papelera** si desea suprimir una definición de alerta.

## Visualización de los detalles de alertas
{: #viewing-alert-details notoc}

En este ejemplo se muestran los detalles de las alertas activadas desde la página Registro de alertas.

1. En la consola de {{site.data.keyword.mobileanalytics_short}}, pulse **Registros**. Esta acción le dirige a la página Registro de alertas.
2. Pulse el icono **+** de cualquiera de las alertas. Con esta acción se muestran las secciones **Definición de alerta** e **Instancias de alerta**.

    **Nota**: Si la definición de alerta correspondiente no se ha suprimido o modificado, puede editarla pulsando **Editar alerta**. De lo contrario, no podrá pulsar el botón **Editar alerta** y se mostrará el siguiente mensaje:

    `Esta definición de alerta se ha modificado o suprimido.`

3. Opcional: Seleccione una alerta y pulse el icono **Papelera** para suprimir la alerta.

