---

copyright:
 years: 2017

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# Instrumente seu app
{: #Instrument}
Última atualização: 18 de janeiro de 2018
{: .last-updated}

##Inicialize o {{site.data.keyword.mobileanalytics_short}} Client SDK 

Inicialize o SDK do cliente do {{site.data.keyword.mobileanalytics_short}} em seu código do aplicativo para registrar a analítica de uso e as sessões do aplicativo usando o valor [API Key](/docs/services/mobileanalytics/sdk.html#analytics-clientkey).	
	
- **Android**
	
```
		BMSClient.getInstance().initialize(getApplicationContext(), BMSClient.REGION_US_SOUTH); // You can change the region
		Analytics.init(getApplication(), "your_app_name_here", "your_api_key_here", hasUserContext, collectLocation, Analytics.DeviceEvent.ALL);
```
		{: codeblock}
	    
O parâmetro **bluemixRegion** especifica qual implementação do {{site.data.keyword.Bluemix_notm}} você está usando, por exemplo, `BMSClient.REGION_US_SOUTH` e `BMSClient.REGION_UK`. 
	    
	    
Configure o valor para `hasUserContext` como **true** ou **false**. Se false (valor padrão), cada dispositivo será contado como um usuário ativo.
		
Configure o valor para `collectLocation` como **true** ou **false**. Se true, os dados de localização do dispositivo serão enviados como parte do log Appsession. 

- **iOS**
	  
Inicialize o Client SDK dentro de seu código de aplicativo para registrar a análise de dados de uso e as sessões de aplicativo, usando o valor da [Chave API](/docs/services/mobileanalytics/sdk.html#analytics-clientkey).
		
```Swift
		BMSClient.sharedInstance.initialize(bluemixRegion: BMSClient.Region.usSouth) // You can change the region
		Analytics.initialize(appName: "your_app_name_here", apiKey: "your_api_key_here", hasUserContext: false, collectLocation: true, deviceEvents: deviceEvents: .lifecycle, .network)
```
		{: codeblock}
				
O parâmetro **bluemixRegion** especifica qual implementação do IBM Cloud está em uso, por exemplo, `BMSClient.Region.usSouth` ou `BMSClient.Region.unitedKingdom`.
		
	 
Configure o valor para `hasUserContext` como **true** ou **false**. Se false (valor padrão), cada dispositivo será contado como um usuário ativo.
		
Configure o valor para `collectLocation` como **true** ou **false**. Se true, os dados de localização do dispositivo serão enviados como parte do log Appsession. 
	
- **Cordova**
		
Inicialize o Client SDK dentro de seu código de aplicativo para registrar a análise de dados de uso e as sessões de aplicativo, usando o valor da [Chave API](/docs/services/mobileanalytics/sdk.html#analytics-clientkey).
		
```
		var appName = "your_app_name_here";
		var apiKey = "your_api_key_here";
		BMSClient.initialize(BMSClient.REGION_US_SOUTH); // You can change the region
		BMSAnalytics.initialize(appName, apiKey, hasUserContext, collectLocation, [BMSAnalytics.ALL])
```
		{: codeblock}
		
O parâmetro **bluemixRegion** especifica qual implementação do IBM Cloud está em uso, por exemplo, `BMSClient.REGION_US_SOUTH` ou `BMSClient.REGION_UK`.
		
Configure o valor para `hasUserContext` como **true** ou **false**. Se false (valor padrão), cada dispositivo será contado como um usuário ativo.
		
Configure o valor para `collectLocation` como **true** ou **false**. Se true, os dados de localização do dispositivo serão enviados como parte do log Appsession.
    
- **Web**
		
Inicialize o Client SDK dentro de seu código de aplicativo para registrar a análise de dados de uso e as sessões de aplicativo, usando o valor da [Chave API](/docs/services/mobileanalytics/sdk.html#analytics-clientkey).
		
```
		var appName = "your_app_name_here";
		var apiKey = "your_api_key_here";
		BMSAnalytics.Client.initialize(BMSAnalytics.Client.REGION_US_SOUTH);
		BMSAnalytics.initialize(appName,apiKey,hasUserContext,BMSAnalytics.DeviceEvents.ALL,instanceId);
``` 
		{: codeblock}

O parâmetro `bluemixRegion` especifica qual implementação do {{site.data.keyword.Bluemix_notm}} você está usando. Configure o valor para `hasUserContext` como `true` ou `false`. Se false (valor padrão), cada dispositivo será contado como um usuário ativo. Configure o `instanceId` para seu instanceId de serviço, que é uma sequência alfanumérica que obtida da URL do navegador para sua instância de serviço depois da sequência "...mobile-analytics_Prod/" and upto "/". 

**Nota**: o nome que você seleciona para seu aplicativo (`your_app_name_here`) é exibido no console do {{site.data.keyword.mobileanalytics_short}} como o nome do aplicativo. O nome do aplicativo é usado como um filtro para procurar logs do aplicativo no painel. Ao usar o mesmo nome de aplicativo entre as plataformas (por exemplo, Android e iOS), é possível ver todos os logs desse aplicativo com o mesmo nome, independentemente de qual plataforma os logs foram enviados.

##Enviar dados do app para o serviço {{site.data.keyword.mobileanalytics_short}}

Enviar a análise de uso registrada para o serviço do {{site.data.keyword.mobileanalytics_short}}. Uma maneira simples de testar a análise é executar o código a seguir quando o aplicativo for iniciado:


- **Android**
	
Use o método `Analytics.send()` para enviar os dados de analítica para o servidor. É possível colocar o método `Analytics.send()` em qualquer lugar no método `onCreate` da atividade principal em seu aplicativo Android ou em um local que funcione melhor para o seu projeto. 
	
É possível inserir `Analytics.send()` em qualquer lugar.
	
- **iOS**
	
Use o método `Analytics.send` para enviar os dados de análise para o servidor. É possível colocar o método `Analytics.send` em qualquer lugar no método `application(_:didFinishLaunchingWithOptions:)` de seu delegado de aplicativo ou em um local que funcione melhor para o seu projeto. 
	
- **Cordova**
		
Use o método `BMSAnalytics.send` para enviar dados de analítica para o servidor. Coloque o método `BMSAnalytics.send` em um local que funcione melhor para o seu projeto.
		
- **Web**
		
Use o método `BMSAnalytics.send` para enviar dados de analítica para o servidor. Coloque o método `BMSAnalytics.send` em um local que funcione melhor para o seu projeto. 
		



Percorra o tópico [Instrumentando seu aplicativo](/docs/services/mobileanalytics/sdk.html) para saber mais sobre recursos adicionais do {{site.data.keyword.mobileanalytics_short}}, tais como [criação de log](/docs/services/mobileanalytics/sdk.html#app-monitoring-logger), [solicitações de rede](/docs/services/mobileanalytics/sdk.html#network-requests), [criação de log de localização](/docs/services/mobileanalytics/sdk.html#location-logging) e [análise de travamento](/docs/services/mobileanalytics/sdk.html#report-crash-analytics).


Sua próxima etapa é **Compilar e executar o aplicativo em seu emulador ou dispositivo**.
