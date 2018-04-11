---

copyright:
  years: 2015, 2017
lastupdated: "2017-08-06"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# In-App Feedback Analysis
{: #In-App}

## In-app Feedback Analysis with Mobile Analytics

With this feature of {{site.data.keyword.mobileanalytics_short}} -

- **Users and Testers** can record and send feedback and bug reports 'In-app', as they run and use the application
- **App owners** get a deeper sense of the application's user experience with this context rich user feedback
- **Developers** on the other hand receive accurate application contexts to diagnose and fix bugs / feature deficiencies


## Enabling In-app Feedback

Complete the following steps to enable your mobile application to capture In-App user feedback

**Intrument your app:**

 - Intrument your mobile app to enter the feedback-mode. Call the API  `Analytics.triggerFeedbackMode();`  to invoke the feedback-mode. For more information [refer the documentation](/docs/services/mobileanalytics/sdk.html)
 - The API can be called on any application event such as buttons, menu actions or gestures 
 
**Receive In-app Feedback**

 - End users and testers of your app can switch over to the feedback-mode by triggering the application action that instrumented for this in the previous step
 - From within the feedback-mode rich contextual feedback along with a screenshot can be gathered and sent the {{site.data.keyword.mobileanalytics_short}} service

![capture and send](images/in_app_capture.png)

**Analyze the In-App Feedback and act on it**

 - {{site.data.keyword.mobileanalytics_short}} service receives and consolidates the rich contextual feedback sent from mobile applications
 - Logon to the Mobile Analytics Service Console and select **User Feedback** option in the left navigation pane of the {{site.data.keyword.mobileanalytics_short}} service console to view the feedbacks

![Feedback](images/in_app_user_feedback.png)
 
 - An app owner can review the feedback, add comments and tag the feedback with a **review status**.  Comments could typically be actions planned such as links to Git issues created to work on the feedback or comments could be statement of reasons as to why no action is required on the feedback.   
 - The Review Status can be used to efficiently manage feedback by categorizing them under one of the different status

![Review Feedback](images/in_app_review_feedback.png) 

**Note:**

 - The feature is enabled only for users who have opted the `Advanced Plan`. Select **Plan** in the {{site.data.keyword.mobileanalytics_short}} service console to [upgrade](https://console-tok02-red.cdn.s-bluemix.net/docs/account/change-plan.html#changing) .

 - Currently, this feature is only supported on Android.






