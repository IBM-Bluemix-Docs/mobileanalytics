---

copyright:
 years: 2017

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# 前提条件
{: #prerequisites}
最終更新日: 2018 年 1 月 18 日
{: .last-updated}


## Mobile Analytics サービス・インスタンスの作成
{: #prerequisites_1}

1. [IBM Cloud カタログ](https://console.ng.bluemix.net/catalog/)で、**「モバイル」** > **「Mobile Analytics」**をクリックします。
2. サービス名を入力します。
3. **「作成」**をクリックします。
4. 他の既存アプリに接続することを選択するか、またはアンバインドされたままにします。


バインドされたサービスまたはアンバインドされたサービスのいずれかを作成することを選択できます。バインドされたサービスは他の IBM Cloud アプリに接続されています。一方、アンバインドされたサービスはスタンドアロンであり、他のアプリには接続されていません。 

## アプリの初期化
{: #prerequisites_app}

{{site.data.keyword.mobileanalytics_short}}[Client SDK](/docs/services/mobileanalytics/available-client-sdk.html) を[インポート](/docs/services/mobileanalytics/install-client-sdk.html)してインストールします。オプションで、{{site.data.keyword.mobileanalytics_short}} [REST API ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://mobile-analytics-dashboard.{DomainName}/analytics-service/){:new_window} を使用できます。


###クライアント SDK のインポート

クライアント SDK をインポートし、次のコード・スニペットで初期設定して、使用分析を記録するようにします。

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
		
		
次のステップは[アプリの装備](app-instrument.html)です。


