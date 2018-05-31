---

copyright:
  years: 2016, 2017
lastupdated: "2017-07-14"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# 入門チュートリアル

{: #gettingstartedtemplate}

{{site.data.keyword.mobileanalytics_full}} は、開発者、IT 管理者、ビジネス関係者に、モバイル・アプリのパフォーマンスや使用状況についての洞察を提供します。 {{site.data.keyword.mobileanalytics_short}} では、以下を行うことができます。

* アプリケーションのパフォーマンスと使用状況を、デスクトップまたはタブレットからモニターします。 
* 傾向と異常を迅速に特定し、詳しく調べて問題を解決し、主要な測定基準がクリティカルしきい値を超えた場合にはアラートをトリガーします。 
{: shortdesc}

{{site.data.keyword.mobileanalytics_short}} サービスを迅速に稼働するには、以下のステップを実行します。

1. {{site.data.keyword.mobileanalytics_short}} サービスのインスタンスを作成<!--[create an instance](https://console.{DomainName}/docs/services/reqnsi.html#req_instance)-->した後、{{site.data.keyword.Bluemix}} ダッシュボードの**「サービス」**セクション内のタイルをクリックして、{{site.data.keyword.mobileanalytics_short}} コンソールにアクセスできます。 **デモ・モード**・オプションは{{site.data.keyword.mobileanalytics_short}} コンソールで使用できます。さまざまなビューやグラフに*デモ・データ*が表示されます。デモ・モードは、サービスのインスタンスが生成された後で、コンソールが最初に起動するときのコンソールのデフォルト・モードです。 独自のアプリケーションと分析データがサービスに取り込まれている場合は、デモ・モードを*「オフ」*に切り替えると、アプリケーションのデータを別のグラフに表示できます。 {{site.data.keyword.mobileanalytics_short}} コンソールはデモ・モードの場合は読み取り専用であるため、新規アラート定義を作成することはできません。

2. {{site.data.keyword.mobileanalytics_short}} [クライアント SDK](/docs/services/mobileanalytics/install-client-sdk.html) をインストールします。 オプションで、{{site.data.keyword.mobileanalytics_short}} [REST API ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://mobile-analytics-dashboard.{DomainName}/analytics-service/){:new_window} を使用できます。
	
	- Web アプリ・サービスの構成
	
		Web SDK でアプリ・サーバーを許可するようサービス・インスタンスを構成するには、Swagger UI からサービス構成 REST API を使用してアプリ・サーバーの URL を指定する必要があります。許可された URL のリストであるサービス構成の CRUD 操作用に POST、GET、PUT、および DELETE メソッドが提供されています。サービス・インスタンスの構成を GET および DELETE するには、API キーを使用します。サービス構成を作成および更新するには、POST メソッドおよび PUT メソッドを使用し、それに許可された URL を本文 {"allowedUrls": ["http://abc.com", "https://www.xyz.com"]} としてリストして指定します。Web サーバーと同じシステムのブラウザーからアクセスしている場合は、許可される URL として http://localhost を指定します。

3. クライアント SDK をインポートし、次のコード・スニペットで初期設定して、使用分析を記録するようにします。

	- Android
	
		以下の `import` ステートメントをプロジェクト・ファイルの先頭に追加します。
		
		```
		import com.ibm.mobilefirstplatform.clientsdk.android.core.api.*;
		import com.ibm.mobilefirstplatform.clientsdk.android.analytics.api.*;
		import com.ibm.mobilefirstplatform.clientsdk.android.logger.api.*;
		```
		{: codeblock}

	- iOS

		Swift SDK は iOS および watchOS で使用できます。
		
		以下の `import` ステートメントを `AppDelegate.swift` プロジェクト・ファイルの先頭に追加して、`BMSCore` および `BMSAnalytics` フレームワークをインポートします。
	
		```Swift
		import BMSCore
		import BMSAnalytics
		```
		{: codeblock}
   
	- Cordova
			
		Cordova アプリケーション・ルート・ディレクトリーから次のコマンドを実行して、Cordova プラグインを追加します。
	
		```Javascript
		cordova plugin add bms-core
		```
		{: codeblock}
   
	- Web
	
		Web アプリの `index.html` ファイルに次のスクリプトを追加して、Web プラグインを追加します。
	
		```Html
		<script src="bms-clientsdk-web-analytics/bmsanalytics.js"></script>
		```
		{: codeblock}

		あるいは、モジュール・ローダー requirejs を使用する方法もあります。参照 API として使用する名前は、使用している引数名 (`BMSAnalytics`) と同じです。 
	
	 	```Javascript
	 	require.config({
	    'paths': {
	        'bmsanalytics': 'bms-clientsdk-web-analytics/bmsanalytics'
	    	}
		});
			require(['bmsanalytics'], function(BMSAnalytics) {
		    BMSAnalytics.send();
		}
		```
		{: codeblock}
		
4. 使用分析やアプリケーション・セッションを記録するために、[API キー](/docs/services/mobileanalytics/sdk.html#analytics-clientkey)値を使用して、アプリケーション・コード内で {{site.data.keyword.mobileanalytics_short}} クライアント SDK を初期化します。	
	
	- Android
	
		```
		BMSClient.getInstance().initialize(getApplicationContext(), BMSClient.REGION_US_SOUTH); // You can change the region
		Analytics.init(getApplication(), "your_app_name_here", "your_api_key_here", hasUserContext, collectLocation, Analytics.DeviceEvent.ALL);
		```
		{: codeblock}
	    
		**bluemixRegion** パラメーターは、使用する {{site.data.keyword.Bluemix_notm}} デプロイメントを指定します。例えば、`BMSClient.REGION_US_SOUTH` や `BMSClient.REGION_UK` などです。 
	    <!-- , or `BMSClient.Region.Sydney`.-->
	    
		`hasUserContext` の値を **true** または **false** に設定します。 false (デフォルト値) の場合、各デバイスがアクティブ・ユーザーとしてカウントされます。
		
		`collectLocation` の値を **true** または **false** に設定します。 true の場合、デバイスの場所データが Appsession ログの一部として送信されます。 

	- iOS
	  
		使用分析やアプリケーション・セッションを記録するために、[API キー](/docs/services/mobileanalytics/sdk.html#analytics-clientkey)値を使用して、アプリケーション・コード内でクライアント SDK を初期化します。
		
		```Swift
		BMSClient.sharedInstance.initialize(bluemixRegion: BMSClient.Region.usSouth) // You can change the region
		Analytics.initialize(appName: "your_app_name_here", apiKey: "your_api_key_here", hasUserContext: false, collectLocation: true, deviceEvents: deviceEvents: .lifecycle, .network)
		```
		{: codeblock}
				
		**bluemixRegion** パラメーターは、使用する IBM Cloud デプロイメント (例: `BMSClient.Region.usSouth` や `BMSClient.Region.unitedKingdom` など) を指定します。
		<!-- , or `BMSClient.REGION_SYDNEY`. -->
	 
		`hasUserContext` の値を **true** または **false** に設定します。 false (デフォルト値) の場合、各デバイスがアクティブ・ユーザーとしてカウントされます。
		
		`collectLocation` の値を **true** または **false** に設定します。 true の場合、デバイスの場所データが Appsession ログの一部として送信されます。 
	
	- Cordova
		
		使用分析やアプリケーション・セッションを記録するために、[API キー](/docs/services/mobileanalytics/sdk.html#analytics-clientkey)値を使用して、アプリケーション・コード内でクライアント SDK を初期化します。
		
		```
		var appName = "your_app_name_here";
		var apiKey = "your_api_key_here";
		BMSClient.initialize(BMSClient.REGION_US_SOUTH); // You can change the region
		BMSAnalytics.initialize(appName, apiKey, hasUserContext, collectLocation, [BMSAnalytics.ALL])
		```
		{: codeblock}
		
		**bluemixRegion** パラメーターは、使用する IBM Cloud デプロイメント (例: `BMSClient.REGION_US_SOUTH` や `BMSClient.REGION_UK` など) を指定します。
		<!-- , or `BMSClient.REGION_SYDNEY`. -->
		`hasUserContext` の値を **true** または **false** に設定します。 false (デフォルト値) の場合、各デバイスがアクティブ・ユーザーとしてカウントされます。
		
		`collectLocation` の値を **true** または **false** に設定します。 true の場合、デバイスの場所データが Appsession ログの一部として送信されます。
    
	- Web
		
		使用分析やアプリケーション・セッションを記録するために、[API キー](/docs/services/mobileanalytics/sdk.html#analytics-clientkey)値を使用して、アプリケーション・コード内でクライアント SDK を初期化します。
		
		```
		var appName = "your_app_name_here";
		var apiKey = "your_api_key_here";
		BMSAnalytics.Client.initialize(BMSAnalytics.Client.REGION_US_SOUTH);
		BMSAnalytics.initialize(appName,apiKey,hasUserContext,BMSAnalytics.DeviceEvents.ALL,instanceId);
		``` 
		{: codeblock}

		`bluemixRegion` パラメーターは、使用する {{site.data.keyword.Bluemix_notm}} デプロイメントを指定します。例えば、`BMSAnalytics.Client.REGION_US_SOUTH` や `BMSAnalytics.Client.REGION_UK` などです。 `hasUserContext` の値を `true` または `false` に設定します。 false (デフォルト値) の場合、各デバイスがアクティブ・ユーザーとしてカウントされます。`instanceId` をご使用のサービス・インスタンス ID に設定します。これは、ご使用のサービス・インスタンス用にブラウザー URL から取得した英数字ストリングで、"...mobile-analytics_Prod/" から "/" までの部分となります。 

		アプリケーション用に選択した名前 (`your_app_name_here`) が、アプリケーション名として{{site.data.keyword.mobileanalytics_short}} コンソールに表示されます。アプリケーション名は、ダッシュボードでアプリケーション・ログを検索する場合にフィルターとして使用されます。 複数のプラットフォーム (例えば Android と iOS) で同じアプリケーション名を使用すると、ログの送信元がどのプラットフォームであっても、同じ名前のアプリケーションからのすべてのログを表示できます。

5. 記録した使用分析を {{site.data.keyword.mobileanalytics_short}} サービスに送信します。 分析のテストは、アプリケーションの開始時に次のコードを実行すると簡単に行えます。

	- Android
	
		`Analytics.send()` メソッドを使用して、分析データをサーバーに送信します。 `Analytics.send()` メソッドを、Android アプリケーションのメインアクティビティーの `onCreate` メソッド内か、プロジェクトで最も適切な場所に置きます。 
	
		`Analytics.send()` はどこにでも挿入できます。
	
	- iOS
	
		`Analytics.send` メソッドを使用して、分析データをサーバーに送信します。 `Analytics.send` メソッドを、アプリケーション・デリゲートの `application(_:didFinishLaunchingWithOptions:)` メソッド内の任意の場所か、プロジェクトで最も適切な場所に置くことができます。 
	
	- Cordova
		
		`BMSAnalytics.send` メソッドを使用して、分析データをサーバーに送信します。 `BMSAnalytics.send` メソッドを、プロジェクトで最もうまく動作する場所に配置してください。
		
	- Web
		
		`BMSAnalytics.send` メソッドを使用して、分析データをサーバーに送信します。 `BMSAnalytics.send` メソッドを、プロジェクトで最もうまく動作する場所に配置してください。 
		
6. [ロギング](/docs/services/mobileanalytics/sdk.html#app-monitoring-logger)、[ネットワーク要求](/docs/services/mobileanalytics/sdk.html#network-requests)、[場所のロギング](/docs/services/mobileanalytics/sdk.html#location-logging)、[クラッシュ分析](/docs/services/mobileanalytics/sdk.html#report-crash-analytics)など、その他の {{site.data.keyword.mobileanalytics_short}} 機能について詳しくは、[アプリケーションの装備](/docs/services/mobileanalytics/sdk.html)トピックをご覧ください。
	
7. エミュレーターまたはデバイスでアプリケーションをコンパイルして実行します。

8. {{site.data.keyword.mobileanalytics_short}} のコンソールに移動して、ご使用のアプリケーションの使用量分析を表示できます。 また、<!--[creating custom charts](app-monitoring.html#custom-charts),-->[アラートの設定](/docs/services/mobileanalytics/app-monitoring.html#alerts)および[アプリの異常終了のモニター](/docs/services/mobileanalytics/app-monitoring.html#monitor-app-crash)によっても、アプリケーションをモニターできます。

# 関連リンク
{: #rellinks notoc}

## SDK
{: #sdk notoc}
* [Android SDK ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-analytics){: new_window}  
* [iOS SDK ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-analytics){: new_window}
* [Cordova プラグインのコア SDK ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン ")](https://www.npmjs.com/package/bms-core){: new_window}
* [Web SDK ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-web-analytics/){: new_window}
## API リファレンス
{: #api notoc}
* [REST API ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://mobile-analytics-dashboard.{DomainName}/analytics-service/){:new_window}
