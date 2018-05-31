---

copyright:
 years: 2017

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# アプリの装備
{: #Instrument}
最終更新日: 2018 年 1 月 18 日
{: .last-updated}

##{{site.data.keyword.mobileanalytics_short}} クライアント SDK の初期化 

使用分析やアプリケーション・セッションを記録するために、[API キー](/docs/services/mobileanalytics/sdk.html#analytics-clientkey)値を使用して、アプリケーション・コード内で {{site.data.keyword.mobileanalytics_short}} クライアント SDK を初期化します。	
	
- **Android**
	
```
		BMSClient.getInstance().initialize(getApplicationContext(), BMSClient.REGION_US_SOUTH); // You can change the region
		Analytics.init(getApplication(), "your_app_name_here", "your_api_key_here", hasUserContext, collectLocation, Analytics.DeviceEvent.ALL);
```
		{: codeblock}
	    
**bluemixRegion** パラメーターは、使用する {{site.data.keyword.Bluemix_notm}} デプロイメントを指定します。例えば、`BMSClient.REGION_US_SOUTH` や `BMSClient.REGION_UK` などです。 
	    
	    
`hasUserContext` の値を **true** または **false** に設定します。 false (デフォルト値) の場合、各デバイスがアクティブ・ユーザーとしてカウントされます。
		
`collectLocation` の値を **true** または **false** に設定します。 true の場合、デバイスの場所データが Appsession ログの一部として送信されます。 

- **iOS**
	  
使用分析やアプリケーション・セッションを記録するために、[API キー](/docs/services/mobileanalytics/sdk.html#analytics-clientkey)値を使用して、アプリケーション・コード内でクライアント SDK を初期化します。
		
```Swift
		BMSClient.sharedInstance.initialize(bluemixRegion: BMSClient.Region.usSouth) // You can change the region
		Analytics.initialize(appName: "your_app_name_here", apiKey: "your_api_key_here", hasUserContext: false, collectLocation: true, deviceEvents: deviceEvents: .lifecycle, .network)
```
		{: codeblock}
				
**bluemixRegion** パラメーターは、使用する IBM Cloud デプロイメント (例: `BMSClient.Region.usSouth` や `BMSClient.Region.unitedKingdom` など) を指定します。
		
	 
`hasUserContext` の値を **true** または **false** に設定します。 false (デフォルト値) の場合、各デバイスがアクティブ・ユーザーとしてカウントされます。
		
`collectLocation` の値を **true** または **false** に設定します。 true の場合、デバイスの場所データが Appsession ログの一部として送信されます。 
	
- **Cordova**
		
使用分析やアプリケーション・セッションを記録するために、[API キー](/docs/services/mobileanalytics/sdk.html#analytics-clientkey)値を使用して、アプリケーション・コード内でクライアント SDK を初期化します。
		
```
		var appName = "your_app_name_here";
		var apiKey = "your_api_key_here";
		BMSClient.initialize(BMSClient.REGION_US_SOUTH); // You can change the region
		BMSAnalytics.initialize(appName, apiKey, hasUserContext, collectLocation, [BMSAnalytics.ALL])
```
		{: codeblock}
		
**bluemixRegion** パラメーターは、使用する IBM Cloud デプロイメント (例: `BMSClient.REGION_US_SOUTH` や `BMSClient.REGION_UK` など) を指定します。
		
`hasUserContext` の値を **true** または **false** に設定します。 false (デフォルト値) の場合、各デバイスがアクティブ・ユーザーとしてカウントされます。
		
`collectLocation` の値を **true** または **false** に設定します。 true の場合、デバイスの場所データが Appsession ログの一部として送信されます。
    
- **Web**
		
使用分析やアプリケーション・セッションを記録するために、[API キー](/docs/services/mobileanalytics/sdk.html#analytics-clientkey)値を使用して、アプリケーション・コード内でクライアント SDK を初期化します。
		
```
		var appName = "your_app_name_here";
		var apiKey = "your_api_key_here";
		BMSAnalytics.Client.initialize(BMSAnalytics.Client.REGION_US_SOUTH);
		BMSAnalytics.initialize(appName,apiKey,hasUserContext,BMSAnalytics.DeviceEvents.ALL,instanceId);
``` 
		{: codeblock}

`bluemixRegion` パラメーターは、使用する {{site.data.keyword.Bluemix_notm}} デプロイメントを指定します。 `hasUserContext` の値を `true` または `false` に設定します。 false (デフォルト値) の場合、各デバイスがアクティブ・ユーザーとしてカウントされます。`instanceId` をご使用のサービス・インスタンス ID に設定します。これは、ご使用のサービス・インスタンス用にブラウザー URL から取得した英数字ストリングで、"...mobile-analytics_Prod/" から "/" までの部分となります。 

**注**: アプリケーション用に選択した名前 (`your_app_name_here`) は、アプリケーション名として {{site.data.keyword.mobileanalytics_short}} コンソールに表示されます。 アプリケーション名は、ダッシュボードでアプリケーション・ログを検索する場合にフィルターとして使用されます。 複数のプラットフォーム (例えば Android と iOS) で同じアプリケーション名を使用すると、ログの送信元がどのプラットフォームであっても、同じ名前のアプリケーションからのすべてのログを表示できます。

##{{site.data.keyword.mobileanalytics_short}} サービスへのアプリ・データの送信

記録した使用分析を {{site.data.keyword.mobileanalytics_short}} サービスに送信します。 分析のテストは、アプリケーションの開始時に次のコードを実行すると簡単に行えます。


- **Android**
	
`Analytics.send()` メソッドを使用して、分析データをサーバーに送信します。 `Analytics.send()` メソッドを、Android アプリケーションのメインアクティビティーの `onCreate` メソッド内か、プロジェクトで最も適切な場所に置きます。 
	
`Analytics.send()` はどこにでも挿入できます。
	
- **iOS**
	
`Analytics.send` メソッドを使用して、分析データをサーバーに送信します。 `Analytics.send` メソッドを、アプリケーション・デリゲートの `application(_:didFinishLaunchingWithOptions:)` メソッド内の任意の場所か、プロジェクトで最も適切な場所に置くことができます。 
	
- **Cordova**
		
`BMSAnalytics.send` メソッドを使用して、分析データをサーバーに送信します。 `BMSAnalytics.send` メソッドを、プロジェクトで最もうまく動作する場所に配置してください。
		
- **Web**
		
`BMSAnalytics.send` メソッドを使用して、分析データをサーバーに送信します。 `BMSAnalytics.send` メソッドを、プロジェクトで最もうまく動作する場所に配置してください。 
		



[ロギング](/docs/services/mobileanalytics/sdk.html#app-monitoring-logger)、[ネットワーク要求](/docs/services/mobileanalytics/sdk.html#network-requests)、[場所のロギング](/docs/services/mobileanalytics/sdk.html#location-logging)、[クラッシュ分析](/docs/services/mobileanalytics/sdk.html#report-crash-analytics)など、その他の {{site.data.keyword.mobileanalytics_short}} 機能について詳しくは、[アプリケーションの装備](/docs/services/mobileanalytics/sdk.html)トピックをご覧ください。


次のステップでは、**エミュレーターまたはデバイスでアプリケーションをコンパイルして実行します**。
