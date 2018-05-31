---

copyright:
  years: 2015, 2017
lastupdated: "2017-08-06"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# メトリックおよびイベントの使用
{: #usingmetrics}

## Mobile Analytics によるアプリケーションのモニター

{{site.data.keyword.mobileanalytics_full}} には、モバイル・アプリケーションのモニタリングや分析を行う機能が備えられています。 {{site.data.keyword.mobileanalytics_short}} クライアント SDK を使用して、アプリケーション・ログを記録したりデータをモニターしたりできます。 開発者は、このデータを {{site.data.keyword.mobileanalytics_short}} サービスに送信するタイミングを制御できます。 データが {{site.data.keyword.mobileanalytics_short}} に送信されたら、{{site.data.keyword.mobileanalytics_short}} コンソールを使用して、モバイル・アプリケーション、デバイス、アプリケーション・ログに関する分析の洞察を得ることができます。
{: shortdesc}

##定義済みメトリック

**定義済みメトリック**を使用して、以下のような疑問に答えることができます:

* 新規ユーザーは何人いるか?  
* アプリケーションをアクティブに使用している人は何人いるのか?  
* ユーザーはどのくらいの頻度でアプリケーションを使用しているのか? 
* ユーザーはどんな時刻にアプリケーションを使用しているのか?  
* ユーザーに好まれているデバイス・モデルは何か? 
* レガシー・オペレーティング・システムのサポートをいつ廃止すべきか? 
* パフォーマンスの問題が発生しているアプリケーションはどれか?  

##カスタム・イベント

独自の**カスタム・イベント**を追加することにより、以下のような疑問に答えることができます。 

* 最も使用されているフィーチャーと最も使用されていないフィーチャーは何か?  
* ユーザーはアプリのどこから入ってどこで終わらせているか?  
* ユーザーが最もよく表示するアクティビティーは何か?  
* ユーザーはアプリのワークフロー (例えば変換ファネル) を終了しているか?   

クライアント・サイドのログと使用データは自動的に収集され、要求に応じて Mobile Analytics サービスに送信されます。 開発者と管理者は、{{site.data.keyword.mobileanalytics_short}} サービス・ダッシュボードを使用して、クライアント SDK によって収集されたデータを見ることができます。

## データ可視化
{: data-visualization notoc}

分析サービスによって収集されたすべてのデータを、{{site.data.keyword.mobileanalytics_short}} ダッシュボードで視覚化できます。このダッシュボードは、{{site.data.keyword.Bluemix_notm}} ダッシュボードで IBM {{site.data.keyword.mobileanalytics_short}} サービス・タイル・インスタンスをクリックすることによってアクセスできます。<!--You can also create custom charts, based on data that is collected by the analytics service in the dashboard.--> モバイル分析の概要ビューに加えて、クライアント・ログや取り込まれたクライアント異常終了データに対してロー検索を行う機能も、分析フィーチャーに組み込まれています。さらに、{{site.data.keyword.mobileanalytics_short}} サービスに送り込まれるクライアント API ファンクション・コールで明示的に提供される追加データに対するロー検索機能も含まれます。 

