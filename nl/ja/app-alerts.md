---

copyright:
  years: 2015, 2017
lastupdated: "2017-08-06"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# アラートの設定
{: #alerts}

## Mobile Analytics によるアラートの設定 

{{site.data.keyword.mobileanalytics_short}} コンソールでアラート定義にしきい値を設定すると、アクティビティーのモニターに役立ちます。

しきい値を構成して、そのしきい値を超過した場合にアラートをトリガーして {{site.data.keyword.mobileanalytics_short}} コンソール・モニターに通知するようにすることができます。 トリガーされたアラートは、コンソールで視覚化したり、カスタム Webhook で処理したりできます。<!-- This feature provides a proactive means of detecting app log errors, server log errors, extended periods of network latency, and authentication failures.--> この機能は、アプリケーション・ログ・エラー、アプリケーションの異常終了、サーバー・ログ・エラーを検出するプロアクティブな手段になります。 リアクティブのしきい値やアラートにより、データをふるいにかけたり、しきい値を細分して設定したりする必要がなくなります。

## アプリケーション・ログのアラート定義の作成
{: #alert-def-client-logs notoc}

アプリケーション・ログに基づくアラート定義を作成できます。

この例では、アプリケーション・ログ・データを使用してアラート定義を作成します。 アラートは、過去 5 分間に受け取ったすべてのアプリケーション・ログをモニターし、アラート定義が無効になるか削除されるまで、5 分ごとに検査し続けるとします。 デバイスが同じアプリケーション名で同じバージョンのアプリケーション・エラー・ログを 3 つ以上送信するたびに、アラートがトリガーされます。

1. {{site.data.keyword.mobileanalytics_short}} コンソールで、**「定義 (Definitions)」**をクリックして、「アラート定義 (Alert Definitions)」ページに進みます。
2. **「アラートの作成」**をクリックして、アラートを作成します。
3. 以下の値を入力します。
	* アラート名: アプリ・ログのアラート
	* メッセージ: エラー・メッセージのアラート
	* 照会の頻度: 5 分
	* イベント・タイプ: アプリ・ログ
		* プロパティー: ログ・レベル
			* 値: エラー
			* しきい値
				* しきい値のタイプ: アプリケーション・インスタンスの合計

					**注**: 「アプリケーションの平均」オプションを選択すると、アプリ・ログ数が、デバイス数で平均化された数になります。 例えば、デバイスが 2 つあり、一方のデバイスがアプリ・ログを 6 つ送信し、もう一方のデバイスがアプリ・ログを 3 つ送信した場合、アプリ・ログの平均は 4.5 になります。
				* 演算子: 3 以上
	<!-- insert alert definition tab image? -->

4. **「次へ」**をクリックして、次の値を入力します。
	* 方法: 分析コンソールのみ

		**注**: カスタマイズした URL に JSON ペイロードとともに POST メッセージを追加で送信する場合は、「分析コンソールとネットワーク・ポスト (Analytics Console and Network Post)」オプションを選択します。 このオプションを選択すると、以下のフィールドが使用可能になります。
		* ネットワーク・ポスト URL (Network Post URL)
        * ヘッダー (Headers)
        * 認証タイプ (Authentication Type)
5. **「保存」**をクリックします。

5 分間隔の最後にしきい値 (エラー・ログが 3 個以上) にアプリ・ログ数が達していればアラートをトリガーする、というアラート定義が作成されました。

## アプリケーション異常終了のアラート定義の作成
{: #alert-def-app-crash notoc}

アプリケーション異常終了に基づくアラート定義を作成できます。

この例では、アプリケーション異常終了データを使用して、アラート定義を作成します。 アラートは、過去 2 分間におけるすべてのアプリケーション異常終了をモニターし、アラート定義が無効になるか削除されるまで、2 分ごとに検査し続けるとします。 5 回以上異常終了した各アプリケーションに対してアラートがトリガーされるようにします。 アプリケーション異常終了について詳しくは、[アプリケーション異常終了](#app_crash)を参照してください。

1. {{site.data.keyword.mobileanalytics_short}} コンソールで、**「定義 (Definitions)」**をクリックして、「アラート定義 (Alert Definitions)」ページを表示します。
2. **「アラートの作成 (Create Alert)」**をクリックします。
3. 以下の値を入力します。
	* アラート名: アプリケーション異常終了のアラート
	* メッセージ: アプリ異常終了のアラート
	* 照会の頻度: アプリケーションの異常終了
		* 照会の頻度: 2 分
	* イベント・タイプ: アプリケーションの異常終了
		* アプリケーション名: 任意のアプリケーション
		* アプリケーションのバージョン: 任意のバージョン
    * しきい値
      * しきい値のタイプ: 異常終了回数
      * 演算子: 5 以上
4. **「分布方法 (Distribution Method)」**タブをクリックし、次の値を入力します。
  * 方法: 分析コンソールのみ

    **注**: カスタマイズされた URL に JSON ペイロードとともに POST メッセージを追加で送信する場合、**「分析コンソールとネットワーク・ポスト (Analytics Console and Network Post)」**オプションを選択します。 このオプションを選択すると、以下のフィールドが使用可能になります。
      * ネットワーク・ポスト URL (Network Post URL)(必須)
      * ヘッダー (Headers)(オプション)
      * 認証タイプ (Authentication Type)(必須)
5. **「保存」**をクリックします。

## アラート定義の管理
{: #managing-alert-definitions notoc}

この例では、「アラート管理 (Alert Management)」ページからアラート定義を管理します。

1. {{site.data.keyword.mobileanalytics_short}} コンソールで、**「ログ」**をクリックします。 このアクションにより、「アラート・ログ」ページが開きます。
2. オプション:**「有効」**列の下のチェック・ボックスを切り替えて、特定のアラート定義を有効または無効にします。
3. オプション: アラート定義のコピーを作成し、いくつかの値を変更する場合は、**「複写」**アイコンをクリックします。
4. オプション: アラート定義を編集する場合は、**「鉛筆 (Pencil)」**アイコンをクリックします。
5. オプション: アラート定義を削除する場合は、**「ごみ箱」**アイコンをクリックします。

## アラート詳細の表示
{: #viewing-alert-details notoc}

この例では、トリガーされたアラートの詳細を「アラート・ログ」ページから表示します。

1. {{site.data.keyword.mobileanalytics_short}} コンソールで、**「ログ」**をクリックします。 このアクションにより、「アラート・ログ」ページが開きます。
2. 任意のアラートの**「+」**アイコンをクリックします。 このアクションにより、**「アラート定義 (Alert Definition)」**セクションと**「アラート・インスタンス (Alert Instances)」**セクションが表示されます。

    **注**: 対応するアラート定義が削除も変更もされていない場合、**「アラートの編集 (Edit Alert)」**をクリックしてアラート定義を編集できます。 削除または変更されている場合、**「アラートの編集 (Edit Alert)」**ボタンを使用できず、以下のメッセージが表示されます。

    `このアラート定義は変更または削除されました。(This alert definition has since been modified or deleted.)`

3. オプション: アラートを削除するには、アラートを選択し**「ごみ箱」**アイコンをクリックします。

