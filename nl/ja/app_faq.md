---

copyright:
  years: 2015, 2017
lastupdated: "2018-02-19"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}


# よくある質問 
{: #faq}


1. **{{site.data.keyword.mobileanalytics_full}} とは**
	
	{{site.data.keyword.mobileanalytics_full}} は、モバイル・アプリケーションのパフォーマンスや使用状況についてのリアルタイムの洞察や履歴に基づく洞察を提供するサービスです。 {{site.data.keyword.mobileanalytics_short}} を使用すると、アプリケーション開発者やアプリケーション所有者は、アクティブ・ユーザー、セッション、モバイル・プラットフォーム、アプリケーションの異常終了の傾向をモニターしてデータ主導型の決定を下すことができます。 選択したメトリックに対するアラートを設定し、アラートがトリガーされた場合にはプッシュ・サービスや内部メッセージング・サービスなどの REST エンドポイントにメッセージを送信するように構成できます。


2. **{{site.data.keyword.mobileanalytics_short}} for {{site.data.keyword.Bluemix_notm}} でできることは何ですか?**

	モバイル・アプリケーション・プロダクト・マネージャーは、自分のアプリケーションを使用している人数 (ユーザー・メトリック) や、それがいつ使用されているのか (セッション・メトリック) を知ることができます。 この情報は時系列で表示され、リアルタイムで更新されるので、アプリケーションに加えた変更の影響を調べることができます。 特定のアプリケーション・バージョンまたはオペレーティング・システムをフィルタリングして参照し、廃止や優先事項に関する決定を下すことができます。 
	
	モバイル・アプリケーション・マーケティング担当者は、ユーザー・メトリックとセッション・メトリックを使用して経時変化を観察し、イベント日に関連付けることで、顧客のエンゲージメントをモニターし、顧客離れに対処し、モバイル・アプリケーション・マーケティング活動の有効性を評価することができます。
	
	モバイル・アプリケーション開発者は、ユーザーの不満が募り、アプリケーションの評判に傷が付く前に、異常終了メトリックを使用することにより、モバイル・アプリケーションのパフォーマンスの問題を検出して解決できます。 異常終了の回数と発生率の両方を分析コンソールからモニターできます。また、最も多くのユーザーに影響を与えている異常終了を優先することができます。 指定したしきい値を異常終了数が超過した場合に通知を送信したり自動化されたアクションを実行したりするようにアラートを設定できます。また、異常終了の事象ごとにドリルダウンしてデバイス・ログやアプリケーション・スタック・トレースを参照してトラブルシューティングすることができます。
	
	{{site.data.keyword.mobileanalytics_short}} を使用して個人情報を共有しないでください。

3. **Mobile Analytics を使用するにはデータ・アナリストのスキルが必要ですか?**

	いいえ、{{site.data.keyword.mobileanalytics_short}} には、ビジネス関係者やアプリケーション開発者用に、すぐに使用できる分析コンソールが用意されています。 クエリー・スキルは不要です。

4. **分析データに対してカスタム・クエリーを実行できますか?**

    {{site.data.keyword.mobileanalytics_short}} ではカスタム・クエリーは使用できませんが、将来この機能を使用できるように検討中です。
	
5. **どのようにしてアプリケーションを {{site.data.keyword.mobileanalytics_short}} に接続するのですか?**

    [iOS または Android の場合はオープン・ソース SDK をダウンロード](install-client-sdk.html)し、他のプラットフォームの場合は {{site.data.keyword.mobileanalytics_short}} [REST API](https://mobile-analytics-dashboard.{DomainName}/analytics-service/) を使用します。 

6. **どの IBM Cloud 地域で Mobile Analytics を使用できますか?**

    現在のところ、Mobile Analytics は米国南部と英国で利用可能です。 他の地域で使用可能にすることも計画中ですが、その時期は未定です。

7. **このサービスのコストを教えてください。**

    各月に収集される最初の 1 億イベントは無料です。その後のイベントについては、100 万イベントごとに $1 の費用がかかります。
	
8. **イベントとは何ですか?**

    現時点で、報告されイベントには、アプリケーション・セッションの開始、アプリケーション・セッションの終了 (アプリケーション・クラッシュを含む)、アラート通知、ログ・エントリーが含まれます。
	
9. **1 カ月あたりのサービスのコストをどのように見積もることができますか?**

    価格設定はクライアント・アカウントごとにサービスに送信されたイベントの数に応じて異なるため、価格を見積もるということは、イベント数を見積もるということです。  
	
	課金価格は、{{site.data.keyword.mobileanalytics_short}} に接続したすべてのアプリケーションからのイベント数の合計になります。 特定のアプリケーションのイベントの数は、アプリケーション内に実装した装備の度合い、ユーザーの数、また、ユーザーがどれほどアクティブかに応じて異なります。 
	
	使用量を見積もるには、次の式を使用します。各アプリの月ごとのイベント数 = (1 日のユーザー数)(1 日のユーザーごとのセッション数)(月の日数)(セッションごとのイベント数)
	
	セッションごとのイベント数は、開発者がアプリケーションで構成したネットワーク呼び出し、カスタム分析、ログ・キャプチャー、アラート定義に応じて 2 から数百まで大きく変動する可能性があります。

9. **分析データの保持期間を教えてください。**

    データは少なくとも 30 日間保持されます。
	
10. **{{site.data.keyword.mobileanalytics_short}} コンソールにデータが表示されるまでどれくらいかかりますか?**

    {{site.data.keyword.mobileanalytics_short}} コンソールのデータは、ほぼリアルタイムです。つまり実際のイベントから数秒以内に表示されます。
	
11. **{{site.data.keyword.mobileanalytics_full}} と MobileFirst Platform Foundation のモバイル分析にはどんな違いがありますか?**

    これらの 2 つのコンソールのユーザーやセッションはよく似ていますが、MobileFirst Platform Foundation の分析のほうには、クライアントがオンプレミスで独自の分析クラスターを管理できるように、追加のメトリックや設定が含まれています。 また、MobileFirst Platform Foundation 分析コンソールでは、アダプターやアダプター・プロシージャー用のメトリックを細分化できます。一方、{{site.data.keyword.mobileanalytics_short}} サービスでは、これらのメトリックはネットワーク要求のグラフや表に統合されています。
	
12. **MobileFirst Platform Foundation をオンプレミスで使用してアプリを開発していますが、独自の分析クラスターをホストしたくありません。 代わりに、{{site.data.keyword.mobileanalytics_full}} を使用できますか?**

    はい。 選択肢がいくつかあります。MobileFirst Platform Foundation 7.x または 8.0 を使用していて、アプリを MobileFirst Platform SDK で装備している場合は、分析データを {{site.data.keyword.mobileanalytics_short}} for {{site.data.keyword.Bluemix_notm}} にレポートするように MobileFirst サーバーを構成できます。詳しくは、[Configuring Mobile Analytics and Mobile Foundation IBM Cloud services ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://mobilefirstplatform.ibmcloud.com/blog/2016/07/11/analytics-bm-service/){: new_window} のブログ投稿を参照してください。 また、{{site.data.keyword.Bluemix_notm}} {{site.data.keyword.mobileanalytics_short}} SDK を使用してアプリを計装し、{{site.data.keyword.mobileanalytics_short}} サービスに直接レポートすることもできます。
