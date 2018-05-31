---

copyright:
  years: 2015, 2017
lastupdated: "2017-08-06"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# 監視應用程式損毀
{: #monitor-app-crash}

您可以在 {{site.data.keyword.mobileanalytics_short}} 主控台中檢視應用程式損毀的相關資訊，以更適當地監視應用程式並進行疑難排解。

## 應用程式損毀監視
{: #app-crash notoc}

在**毀損**頁面上，**損毀概觀**表格會顯示下列資料直欄：

* 應用程式：應用程式名稱
* 損毀：該應用程式的損毀總數
* 使用總計：使用者開啟及關閉該應用程式的總次數
* 損毀比率：每次使用的損毀百分比

您可以在**損毀**表格中快速查看應用程式損毀的相關資訊。<!--In the **Overview** page of the **Dashboard** section,--> **損毀**長條圖會顯示一段時間內損毀的直方圖。

您可以使用兩種方式來顯示損毀資料：

1. 顯示損毀比率：一段時間的損毀比率
2. 顯示損毀總計：一段時間的損毀總計

## 應用程式損毀疑難排解
{: #app-crash-troubleshooting notoc}

<!-- **Applications** section of the -->{{site.data.keyword.mobileanalytics_short}} 主控台中的**疑難排解**頁面會使用**損毀摘要**表格提供應用程式損毀的細微視圖。

**損毀摘要**表格可進行排序，而且包括下列資料直欄：

* 損毀
* 裝置
* 前次損毀
* 應用程式
* OS
* 訊息

按一下任何項目旁的 + 圖示來顯示**損毀詳細資料**表格，其中包括下列直欄：

* 損毀時間
* 應用程式版本
* OS 版本
* 裝置模型
* 裝置 ID
* 下載：下載已導致損毀之日誌的鏈結

展開**損毀詳細資料**表格中的任何項目來取得更多詳細資料（包括堆疊追蹤）。

**附註**：**損毀摘要**表格的資料是透過查詢嚴重層次應用程式日誌來移入。如果您的應用程式未收集嚴重應用程式日誌，則沒有可用的資料。
