---

copyright:
 years: 2017

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# Pré-requisitos
{: #prerequisites}
Última atualização: 18 de janeiro de 2018
{: .last-updated}


## Criando uma instância de serviço Mobile Analytics
{: #prerequisites_1}

1. No [IBM Cloud Catalog](https://console.ng.bluemix.net/catalog/), clique em **Mobile** > **Mobile Analytics**.
2. Forneça um nome de Serviço.
3. Clique em **Criar**.
4. Escolha se conectar a outros apps existentes ou deixe desvinculado.


É possível escolher criar um serviço de limite ou um serviço desvinculado. Os serviços de limite estão conectados a outros aplicativos IBM Cloud, enquanto os serviços desvinculados são independentes e não conectados a outros aplicativos. 

## Inicializando o seu app
{: #prerequisites_app}

[Importar](/docs/services/mobileanalytics/available-client-sdk.html) e instale o {{site.data.keyword.mobileanalytics_short}} [Client SDKs](/docs/services/mobileanalytics/install-client-sdk.html). É possível usar opcionalmente a {{site.data.keyword.mobileanalytics_short}} [API de REST ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://mobile-analytics-dashboard.{DomainName}/analytics-service/){:new_window}.


###Importe os SDKs

Importe os SDKs do cliente e inicialize-os com o fragmento de código a seguir para registrar a analítica de uso:

- Android
	
    Inclua as seguintes instruções `importar` no início do seu arquivo de projeto:
		
	```
		import com.ibm.mobilefirstplatform.clientsdk.android.core.api.*;
import com.ibm.mobilefirstplatform.clientsdk.android.analytics.api.*;
import com.ibm.mobilefirstplatform.clientsdk.android.logger.api.*;
	```
    {: codeblock}

- iOS

    O SDK do Swift está disponível para iOS e watchOS.
		
    Importe as estruturas `BMSCore` e `BMSAnalytics` ao incluir as instruções de `importação` a seguir no início do seu arquivo de projeto `AppDelegate.swift`:
	
	```Swift 		import BMSCore 		import BMSAnalytics
	```
    {: codeblock}
   
- Cordova
			
    Inclua o plug-in Cordova executando o comando a seguir por meio do diretório-raiz do seu aplicativo Cordova:
	
	```Javascript 		cordova plugin add bms-core
	```
    {: codeblock}
   
- Web
	
    Inclua o plug-in da web incluindo esse script no arquivo `index.html` do app da web:
	
	```Html
		<script src="bms-clientsdk-web-analytics/bmsanalytics.js"></script>
	```
    {: codeblock}

    Ou usando requirejs carregador de módulo. O nome usado como API de referência é o mesmo que o nome de argumento (`BMSAnalytics`) usado. 
	
	 ```Javascript
	 	require.config({
	    'paths': {
	        'bmsanalytics': 'bms-clientsdk-web-analytics/bmsanalytics' 	 	}
		}); 			require(['bmsanalytics'], function(BMSAnalytics) {
		    BMSAnalytics.send();
		}
	```
    {: codeblock}
		
		
Sua próxima etapa é para [Instrumentar seu aplicativo](app-instrument.html).


