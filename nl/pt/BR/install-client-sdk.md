---

copyright:
  years: 2015, 2017
lastupdated: "2017-01-13"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

#Instale o SDK
{: #mobileanalytics_sdk}

## Instale o {{site.data.keyword.mobileanalytics_short}} SDKs do Cliente

Os {{site.data.keyword.mobileanalytics_short}}
Client SDKs estão atualmente disponíveis para Android, iOS, WatchOS, Cordova e Web.
{: shortdesc}

## Instalando o Android Client SDK
{: #install-sdk-android}

[![Maven Central](https://maven-badges.herokuapp.com/maven-central/com.ibm.mobilefirstplatform.clientsdk.android/analytics/badge.svg)](https://maven-badges.herokuapp.com/maven-central/com.ibm.mobilefirstplatform.clientsdk.android/analytics)

O {{site.data.keyword.mobileanalytics_short}} Client SDK é distribuído com o Gradle, um gerenciador de dependências para projetos Android. O Gradle faz download automaticamente dos artefatos de repositórios e os disponibiliza em seu aplicativo Android.

1. Crie um projeto [Android Studio![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](http://developer.android.com/sdk/index.html){: new_window} ou abra um projeto existente.

2. Abra o arquivo `build.gradle` que está em seu **módulo de aplicativo**.

  **Dica**: o seu projeto do Android pode ter dois arquivos `build.gradle`: um para o projeto e um para o módulo de aplicativo. Certifique-se de usar o arquivo de **módulo de aplicativo**.

3. Localize a seção `Dependencies` do arquivo `build.gradle` e inclua uma dependência de compilação para o SDK do cliente {{site.data.keyword.mobileanalytics_short}}. Sua instrução de repositórios deve ser semelhante ao exemplo de código a seguir:

	```
      dependencies {
        compile 'com.ibm.mobilefirstplatform.clientsdk.android:analytics:1.+'
        " Compile com.google.android.gms:play-services-local: 10.0.1 '
    	// other dependencies  
      }
  	```
  	{: codeblock}
	
	A primeira dependência é para o clientsdk Mobile Analytics Service e a segunda é para a criação de log de local do lado do cliente. A segunda dependência será necessária apenas se você ativar a coleta de local do lado do cliente.
    	

4. Sincronize seu projeto com o Gradle clicando em **Ferramentas &gt; Android &gt; Sincronizar projeto com arquivos do Gradle**.

5. Abra o arquivo `AndroidManifest.xml` para seu projeto do Android. Esse arquivo pode ser encontrado em **app > manifests**. Inclua a permissão de acesso à Internet e de acesso local no elemento `<manifest>`:

	```
	 <uses-permission android:name="android.permission.INTERNET" />
	 <uses-permission android:name="android.permission.ACCESS_FINE_LOCATION"/>
	 <uses-permission android:name="android.permission.ACCESS_COARSE_LOCATION"/>
	```
   Se você estiver usando a versão sdk maior que >= 1.2, então, será necessário colocar isso abaixo da parte sob o elemento `<application>` do arquivo `AndroidManifest.xml`.
   	
    ```
	 <activity
            android:name="com.ibm.mobilefirstplatform.clientsdk.android.ui.UIActivity"
            android:label="@string/app_name"
            android:launchMode="singleTask">
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />
                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
        </activity>
	```
   	{: codeblock}
   

Agora você instalou o SDK do cliente Android. A seguir, [importe e inicialize](sdk.html#initalize-ma-sdk) o Analytics Client SDK.   

## Instalando o Swift SDK
{: #installing-sdk-ios}

![CocoaPods Compatible](https://img.shields.io/cocoapods/v/BMSAnalytics.svg)

O SDK do {{site.data.keyword.mobileanalytics_full}} permite instrumentar seu aplicativo móvel. O SDK do Swift está disponível para iOS e watchOS.

### Antes de iniciar
{: #before-you-begin-ios notoc}

Assegure-se de configurar corretamente o Xcode. Para aprender a configurar seu ambiente de desenvolvimento iOS, consulte o [website do Apple Developer ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://developer.apple.com/support/xcode/){: new_window}. Leia sobre os [Requisitos do Xcode ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-analytics/tree/development#requirements){: new_window} for Client SDK Swift Analytics.

#### Ativar API de localização 
Para permitir o trabalho correto da API local é necessário incluir uma propriedade no arquivo Info.plist na pasta do projeto de seu aplicativo, ou seja, `Privacidade - Descrição de uso do local` e como o valor fornece a justificativa adequada para incluir a API local como "O aplicativo requer que o serviço de localização seja ativado" ou algo parecido com isso.

O {{site.data.keyword.mobileanalytics_short}} SDK é distribuído com [CocoaPods ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://cocoapods.org/){: new_window} e [Carthage ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://github.com/Carthage/Carthage#getting-started){: new_window}, que são gerenciadores de dependência para projeto Cocoa. O CocoaPods e o Carthage fazem download automaticamente de artefatos de repositório e os disponibilizam para seu aplicativo. Selecione CocoaPods ou Carthage:

#### CocoaPods
{: #cocoapods notoc}

1. Siga as instruções do [{{site.data.keyword.Bluemix_notm}} Mobile Services Swift SDK ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-analytics/tree/development#cocoapods){: new_window} no GitHub para instalar o `BMSAnalytics` usando Cocoapods e incluí-lo em seu Podfile. 
	
2. Depois de ter instalado o SDK do cliente iOS, [importe e inicialize](sdk.html#initalize-ma-sdk) o SDK do cliente Analytics.   

#### Carthage
{: #carthage notoc}

Se você não estiver usando o CocoaPods, será possível incluir estruturas em seu projeto usando [Carthage ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://github.com/Carthage/Carthage#if-youre-building-for-ios-tvos-or-watchos){: new_window}.

1. Siga as [instruções de instalação do Carthage ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-analytics/tree/development#carthage){: new_window} no GitHub para instalar o `BMSAnalytics`.

2. Depois de ter instalado o SDK do cliente iOS, [importe e inicialize](sdk.html#initalize-ma-sdk) o SDK do cliente Analytics.


## Instalando o plug-in Cordova
{: #installing-sdk-cordova}

O plug-in Cordova do {{site.data.keyword.mobileanalytics_full}} permite que você instrumente seu aplicativo móvel. 

1. Crie um projeto [Cordova ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](http://cordova.apache.org/#getstarted){: new_window} ou abra um projeto existente.

2. Inclua as plataformas Android e iOS em seu aplicativo Cordova. Execute um ou ambos os comandos a seguir da linha de comandos. Atualmente, a CLI Cordova V6.3.0 ou anterior é suportada:
   
   Android:

	 ```
	 cordova platform add android@5.2.2
	 ```
	 {: codeblock}
	
   IOS:
   	
	```
	cordova platform add ios
	```
   {: codeblock}
	
3. Se você incluiu a plataforma Android, deve-se incluir o nível mínimo de API suportado no arquivo `config.xml` do aplicativo Cordova. Abra o arquivo `config.xml` e inclua a linha a seguir no elemento `<platform name="android">`:

	```
	<platform name="android">  
  	 <preference name="android-minSdkVersion" value="15"/>
  	<preference name="android-targetSdkVersion" value="23"/>
  	 <!-- add minimum and target Android API level declaration -->
  	</platform>
	```
   {: codeblock}

 O valor *minSdkVersion* deve ser da versão `15` ou superior. Consulte o [Android Platform Guide ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://cordova.apache.org/docs/en/latest/guide/platforms/android/){: new_window} para se
manter atualizado com o *targetSdkVersion* suportado para o SDK do Android.

4. Se você incluiu o sistema operacional iOS, atualize o elemento `<platform name="ios">` com uma declaração de destino:

	```
	<platform name="ios">
    <preference name="deployment-target" value="8.0"/>
     <!-- add deployment target declaration -->
  	</platform>
	```
	{: codeblock}

5. Inclua o plug-in `bms-core`.
 	
	 ```
	 cordova plugin add bms-core
	 ```
	 {: codeblock}

6. Verifique se o plug-in foi instalado com êxito executando o comando a seguir:
	
	```
	cordova plugin list
	```
	{: codeblock}
	
7. [Configure seu ambiente Android e iOS ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.npmjs.com/package/bms-core#4-configuring-your-platform){: new_window}.

8. Agora você instalou o plug-in do Cordova e configurou seus ambientes. A seguir, [importe e inicialize](sdk.html#initalize-ma-sdk) o Analytics Client SDK.

#### Ativação do serviço de localização à frente do plug-in cordova bms-core versão (>2.4.+).
9. Para que o aplicativo Cordova-ios permita o funcionamento correto da API local, é necessário incluir uma propriedade no arquivo Info.plist na pasta do projeto de seu aplicativo, ou seja, `Privacidade - Descrição de uso local` e como o valor fornece a justificativa adequada para incluir a API local como "O aplicativo requer que o serviço de localização seja ativado" ou algo parecido com isso.

10. Para que o aplicativo Cordova-android permita o funcionamento correto da API local, coloque o seguinte no arquivo AndroidManifest.xml do aplicativo.
	```
	 <uses-permission android:name="android.permission.INTERNET" />
	 <uses-permission android:name="android.permission.ACCESS_FINE_LOCATION"/>
	 <uses-permission android:name="android.permission.ACCESS_COARSE_LOCATION"/>
	```
	{: codeblock}
	
   Em seguida, é necessário colocar isso abaixo da parte sob o elemento `<application>` do arquivo `AndroidManifest.xml`.
   	```
	 <activity
            android:name="com.ibm.mobilefirstplatform.clientsdk.android.ui.UIActivity"
            android:label="@string/app_name"
            android:launchMode="singleTask">
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />
                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
        </activity>
	```
	{: codeblock}

## Installing the Web plugin
{: #web-sdk-cordova}

O {{site.data.keyword.mobileanalytics_full}} SDK permite que você instrumente seu aplicativo da web.

1. Assegure-se de ter um servidor da web e uma configuração do navegador (por exemplo, Chrome, Firefox).
2. Crie um novo aplicativo da web ou use um já existente e coloque isso [WebSDK](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-web-analytics/) dentro de seu projeto a ser acessado pelo código de aplicativo.
3. Inclua o plug-in da web incluindo este script no arquivo `index.html` do aplicativo da web:
	
	```Html
  	<script src="bms-clientsdk-web-analytics/bmsanalytics.js"></script>
	```
	{: codeblock}
Ou usando o carregador de módulo requirejs. O nome usado como API de referência é o mesmo que o nome do argumento (`BMSAnalytics`) usado.
	
   ```Javascript 	 	require.config({ 	 'paths': {
	   'bmsanalytics': 'bms-clientsdk-web-analytics/bmsanalytics' 	 	}
	});

		<script src="bms-clientsdk-web-analytics/bmsanalytics.js"></script>
    ```
 	    {: codeblock}

	Ou usando requirejs carregador de módulo. O nome usado como API de referência é o mesmo que o nome de argumento (`BMSAnalytics`) usado. 
	
	  ```Javascript
	 	require.config({
	    'paths': {
	        'bmsanalytics': 'bms-clientsdk-web-analytics/bmsanalytics' 	 	}
		});
	  ```
	{: codeblock}




# Links Relacionados
{: #rellinks notoc}

## SDK
{: #sdk notoc}
* [SDK do Android![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-analytics){: new_window}  
* [SDK do iOS![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-analytics){: new_window}
* [Cordova Plugin Core SDK ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.npmjs.com/package/bms-core){: new_window}
* [Web SDK![External link icon](../../icons/launch-glyph.svg "External link icon")](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-web-analytics/){: new_window}
## Referência de API
{: #api notoc}
* [API de REST ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://mobile-analytics-dashboard.{DomainName}/analytics-service/){:new_window}
