---

copyright:
  years: 2016, 2017
lastupdated: "2017-07-14"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# Tutorial Introdução

{: #gettingstartedtemplate}

O {{site.data.keyword.mobileanalytics_full}} fornece aos desenvolvedores, administradores de TI e partes interessadas nos negócios insight sobre como seus apps móveis estão sendo executados e como estão sendo usados. O {{site.data.keyword.mobileanalytics_short}} permite que você:

* Monitore desempenho e uso de todos os seus aplicativos da sua área de trabalho ou tablet. 
* Identifique rapidamente tendências e anomalias, realize drill down para resolver os problemas e acione alertas quando Key Metrics atingir um limite crítico. 
{: shortdesc}

Para que o serviço do {{site.data.keyword.mobileanalytics_short}} esteja pronto para execução rapidamente, siga estas etapas:

1. Após você criar uma instância <!--[create an instance](https://console.{DomainName}/docs/services/reqnsi.html#req_instance)-->do serviço {{site.data.keyword.mobileanalytics_short}}, será possível acessar o Console do {{site.data.keyword.mobileanalytics_short}} clicando em seu tile na seção **Serviços** do Painel do {{site.data.keyword.Bluemix}}. Uma opção **Modo demo** está disponível no console do {{site.data.keyword.mobileanalytics_short}}, no qual as visualizações e os gráficos exibem *dados demo*. O modo demo é o modo padrão do console quando é ativado inicialmente após o serviço ser instanciado. Quando você tiver seus próprios aplicativos e dados de analítica preenchidos no serviço, será possível alternar o modo demo para *desligado* a fim de visualizar os dados dos seus aplicativos em diferentes gráficos. O console do {{site.data.keyword.mobileanalytics_short}} é somente leitura quando no modo de
demo; portanto, você não poderá criar novas definições de alerta.

2. Instale os [SDKs do cliente](/docs/services/mobileanalytics/install-client-sdk.html) {{site.data.keyword.mobileanalytics_short}}. É possível usar opcionalmente a {{site.data.keyword.mobileanalytics_short}} [API de REST ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://mobile-analytics-dashboard.{DomainName}/analytics-service/){:new_window}.
	
	- Aplicativo Configuração de Serviço da Web
	
		Para o Web SDK, para configurar sua instãncia de serviço para permitir um servidor de aplicativos, é necessário fornecer a URL do seu servidor de aplicativos por meio da API de REST de Configuração de Serviço por meio do Swagger UI. Os métodos POST, GET, PUT e DELETE são fornecidos para as operações CRUD da configuração de serviço que é uma lista de URLs permitidas. Para configurações GET e DELETE de sua instância de serviço, use sua chave API. Para criar e atualizar a configuração de serviço, use os métodos POST e PUT com as URLs permitidas listadas como o corpo {"allowedUrls":["http://abc.com","https://www.xyz.com"]}. Se você acessando de um navegador no mesmo sistema que o servidor da web, forneça "http://localhost" como a URL permitida.

3. Importe os SDKs do cliente e inicialize-os com o fragmento de código a seguir para registrar a analítica de uso:

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
		
4. Inicialize o SDK do cliente do {{site.data.keyword.mobileanalytics_short}} em seu código do aplicativo para registrar a analítica de uso e as sessões do aplicativo usando o valor [API Key](/docs/services/mobileanalytics/sdk.html#analytics-clientkey).	
	
	- Android
	
		```
		BMSClient.getInstance().initialize(getApplicationContext(), BMSClient.REGION_US_SOUTH); // You can change the region
		Analytics.init(getApplication(), "your_app_name_here", "your_api_key_here", hasUserContext, collectLocation, Analytics.DeviceEvent.ALL);
		```
		{: codeblock}
	    
		O parâmetro **bluemixRegion** especifica qual implementação do {{site.data.keyword.Bluemix_notm}} você está usando, por exemplo, `BMSClient.REGION_US_SOUTH` e `BMSClient.REGION_UK`. 
	    <!-- , or `BMSClient.Region.Sydney`.-->
	    
		Configure o valor para `hasUserContext` como **true** ou **false**. Se false (valor padrão), cada dispositivo será contado como um usuário ativo.
		
		Configure o valor para `collectLocation` como **true** ou **false**. Se true, os dados de localização do dispositivo serão enviados como parte do log Appsession. 

	- iOS
	  
		Inicialize o Client SDK dentro de seu código de aplicativo para registrar a análise de dados de uso e as sessões de aplicativo, usando o valor da [Chave API](/docs/services/mobileanalytics/sdk.html#analytics-clientkey).
		
		```Swift
		BMSClient.sharedInstance.initialize(bluemixRegion: BMSClient.Region.usSouth) // You can change the region
		Analytics.initialize(appName: "your_app_name_here", apiKey: "your_api_key_here", hasUserContext: false, collectLocation: true, deviceEvents: deviceEvents: .lifecycle, .network)
		```
		{: codeblock}
				
		O parâmetro **bluemixRegion** especifica qual implementação do IBM Cloud está em uso, por exemplo, `BMSClient.Region.usSouth` ou `BMSClient.Region.unitedKingdom`.
		<!-- , or `BMSClient.REGION_SYDNEY`. -->
	 
		Configure o valor para `hasUserContext` como **true** ou **false**. Se false (valor padrão), cada dispositivo será contado como um usuário ativo.
		
		Configure o valor para `collectLocation` como **true** ou **false**. Se true, os dados de localização do dispositivo serão enviados como parte do log Appsession. 
	
	- Cordova
		
		Inicialize o Client SDK dentro de seu código de aplicativo para registrar a análise de dados de uso e as sessões de aplicativo, usando o valor da [Chave API](/docs/services/mobileanalytics/sdk.html#analytics-clientkey).
		
		```
		var appName = "your_app_name_here";
		var apiKey = "your_api_key_here";
		BMSClient.initialize(BMSClient.REGION_US_SOUTH); // You can change the region
		BMSAnalytics.initialize(appName, apiKey, hasUserContext, collectLocation, [BMSAnalytics.ALL])
		```
		{: codeblock}
		
		O parâmetro **bluemixRegion** especifica qual implementação do IBM Cloud está em uso, por exemplo, `BMSClient.REGION_US_SOUTH` ou `BMSClient.REGION_UK`.
		<!-- , or `BMSClient.REGION_SYDNEY`. -->
		Configure o valor para `hasUserContext` como **true** ou **false**. Se false (valor padrão), cada dispositivo será contado como um usuário ativo.
		
		Configure o valor para `collectLocation` como **true** ou **false**. Se true, os dados de localização do dispositivo serão enviados como parte do log Appsession.
    
	- Web
		
		Inicialize o Client SDK dentro de seu código de aplicativo para registrar a análise de dados de uso e as sessões de aplicativo, usando o valor da [Chave API](/docs/services/mobileanalytics/sdk.html#analytics-clientkey).
		
		```
		var appName = "your_app_name_here";
		var apiKey = "your_api_key_here";
		BMSAnalytics.Client.initialize(BMSAnalytics.Client.REGION_US_SOUTH);
		BMSAnalytics.initialize(appName,apiKey,hasUserContext,BMSAnalytics.DeviceEvents.ALL,instanceId);
		``` 
		{: codeblock}

		O parâmetro `bluemixRegion` especifica qual implementação do {{site.data.keyword.Bluemix_notm}} você está usando, por exemplo, `BMSAnalytics.Client.REGION_US_SOUTH` e `BMSAnalytics.Client.REGION_UK`. Configure o valor para `hasUserContext` como `true` ou `false`. Se false (valor padrão), cada dispositivo será contado como um usuário ativo. Configure o `instanceId` para seu instanceId de serviço, que é uma sequência alfanumérica que obtida da URL do navegador para sua instância de serviço depois da sequência "...mobile-analytics_Prod/" and upto "/". 

		Observe que o nome que você seleciona para seu aplicativo (`your_app_name_here`) é exibido no console do {{site.data.keyword.mobileanalytics_short}} como o nome do aplicativo. O nome do aplicativo é usado como um filtro para procurar logs do aplicativo no painel. Ao usar o mesmo nome de aplicativo entre as plataformas (por exemplo, Android e iOS), é possível ver todos os logs desse aplicativo com o mesmo nome, independentemente de qual plataforma os logs foram enviados.

5. Enviar a análise de uso registrada para o serviço do {{site.data.keyword.mobileanalytics_short}}. Uma maneira simples de testar a análise é executar o código a seguir quando o aplicativo for iniciado:

	- Android
	
		Use o método `Analytics.send()` para enviar os dados de analítica para o servidor. É possível colocar o método `Analytics.send()` em qualquer lugar no método `onCreate` da atividade principal em seu aplicativo Android ou em um local que funcione melhor para o seu projeto. 
	
		É possível inserir `Analytics.send()` em qualquer lugar.
	
	- iOS
	
		Use o método `Analytics.send` para enviar os dados de análise para o servidor. É possível colocar o método `Analytics.send` em qualquer lugar no método `application(_:didFinishLaunchingWithOptions:)` de seu delegado de aplicativo ou em um local que funcione melhor para o seu projeto. 
	
	- Cordova
		
		Use o método `BMSAnalytics.send` para enviar dados de analítica para o servidor. Coloque o método `BMSAnalytics.send` em um local que funcione melhor para o seu projeto.
		
	- Web
		
		Use o método `BMSAnalytics.send` para enviar dados de analítica para o servidor. Coloque o método `BMSAnalytics.send` em um local que funcione melhor para o seu projeto. 
		
6. Percorra o tópico [Instrumentando seu aplicativo](/docs/services/mobileanalytics/sdk.html) para saber mais sobre recursos adicionais do {{site.data.keyword.mobileanalytics_short}}, tais como [criação de log](/docs/services/mobileanalytics/sdk.html#app-monitoring-logger), [solicitações de rede](/docs/services/mobileanalytics/sdk.html#network-requests), [criação de log de localização](/docs/services/mobileanalytics/sdk.html#location-logging) e [análise de travamento](/docs/services/mobileanalytics/sdk.html#report-crash-analytics).
	
7. Compile e execute o aplicativo em seu emulador ou dispositivo.

8. Acesse o console do {{site.data.keyword.mobileanalytics_short}} para ver a analítica de uso para seu aplicativo. É possível também monitorar seu aplicativo <!--[creating custom charts](app-monitoring.html#custom-charts),-->[configurando alertas](/docs/services/mobileanalytics/app-monitoring.html#alerts) e [monitorando travamentos do aplicativo](/docs/services/mobileanalytics/app-monitoring.html#monitor-app-crash).

# Links relacionados
{: #rellinks notoc}

## SDK
{: #sdk notoc}
* [SDK do Android![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-analytics){: new_window}  
* [SDK do iOS![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-analytics){: new_window}
* [Cordova Plugin Core SDK ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.npmjs.com/package/bms-core){: new_window}
* [Web SDK ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-web-analytics/){: new_window}
## Referência de API
{: #api notoc}
* [API de REST ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://mobile-analytics-dashboard.{DomainName}/analytics-service/){:new_window}
