---

copyright:
  years: 2015, 2017
lastupdated: "2017-08-06"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# Supervisión de bloqueos de aplicaciones
{: #monitor-app-crash}

Puede consultar la información de los bloqueos de aplicaciones en la consola de {{site.data.keyword.mobileanalytics_short}} a fin de supervisar las aplicaciones y resolver los posibles problemas de forma más eficaz.

## Supervisión de bloqueos de aplicaciones
{: #app-crash notoc}

En la tabla **Visión general de bloqueos** de la página **Bloqueos** se muestran las siguientes columnas de datos:

* Aplicación: nombre de la aplicación
* Bloqueos: número total de bloqueos de dicha app
* Usos totales: número total de veces que un usuario abre y cierra dicha app
* Frecuencia de bloqueo: porcentaje de bloqueos por uso

Puede consultar rápidamente la información relacionada con los bloqueos de aplicaciones en la tabla **Bloqueos**. <!--In the **Overview** page of the **Dashboard** section,--> El gráfico de barras **Bloqueos** muestra un histograma de bloqueos a lo largo del tiempo.

Puede visualizar los datos de bloqueos de dos formas:

1. Visualizar frecuencia de bloqueos: frecuencia de bloqueos con el tiempo
2. Visualizar bloqueos totales: bloqueos totales con el tiempo

## Resolución de problemas de bloqueos de apps
{: #app-crash-troubleshooting notoc}

La página **Resolución de problemas** de la consola de <!-- **Applications** section of the --> {{site.data.keyword.mobileanalytics_short}} ofrece una vista granular de los bloqueos de app, utilizando la tabla **Resumen de bloqueos**.

La tabla **Resumen de bloqueos** se puede ordenar e incluye las siguientes columnas de datos:

* Bloqueos
* Dispositivos
* Último bloqueo
* Aplicación
* Sistema operativo
* Mensaje

Pulse el icono +, situado junto a cualquier entrada, para ver la tabla **Detalles de bloqueo**, que incluye las siguientes columnas:

* Tiempo de bloqueo
* Versión de la aplicación
* Versión de sistema operativo
* Modelo del dispositivo
* ID del dispositivo
* Descargar: enlace para descargar los registros que han provocado el bloqueo

Expanda cualquier entrada de la tabla **Detalles de bloqueo** para obtener información más detallada (por ejemplo, un seguimiento de pila).

**Nota**: Los datos de la tabla **Resumen de bloqueos** se rellenan consultando los registros de app de nivel muy grave. Si su aplicación no recopila dichos registros, no habrá datos disponibles.
