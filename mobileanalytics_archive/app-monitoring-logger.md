---

copyright:
  years: 2015, 2016

---
# Enabling, configuring, and using Logger
{: #enable-logger}
Last updated: 29 March 2016*
{: .last-updated}

The {{site.data.keyword.mobileanalytics_full}} Client SDK provides a logging framework that is similar to other log frameworks that you might be familiar with, such as `java.util.logging` or `log4j`. The logging framework supports multiple per-package logger instances, different log levels, capturing of stack traces for an application crash, and more.

You can also configure the logged data to be stored on the device where the application is running. You can send these device logs to the {{site.data.keyword.mobileanalytics_short}} Service at a later time.

The {{site.data.keyword.mobileanalytics_short}} Client SDK logging framework supports the following log levels, which are listed from least to most verbose, with recommended use guidelines:

* `FATAL` - Use for unrecoverable crashes or hangs. The FATAL level is reserved for logging unrecoverable errors, which appear to users as an application crash
* `ERROR` - Use for unexpected exceptions or unexpected network protocol errors
* `WARN` - To log usage warnings that are not considered critical errors, such as usage of deprecated APIs or slow network response
* `INFO` - Use for reporting initialization events and other data that might be important, but not urgent
* `DEBUG` - Use for reporting debug statements to help developers resolve application defects

For example, when the logger level is configured to FATAL, the logger captures uncaught exceptions, but does not capture any logs that lead up to the crash event. Alternatively, a more verbose logger level ensures that logs that might lead to a FATAL logger entry, such as WARN and ERROR, are also captured.


<!--**Note:** Find full Logger API references for each platform at [SDKs, samples, API reference](sdks-samples-apis.html). The Logger API is part of the--> <!--{{site.data.keyword.mobileanalytics_short}} Client SDK Core.-->

<!--### Cordova-->


<!--```JavaScript-->

<!--var logger = MFPLogger.getInstance("myLogger");-->

<!--logger.debug("debug info");-->
<!--logger.info("info message");-->
<!--logger.warn("warning message");-->
<!--logger.fatal("fatal message");-->

<!--```-->


## Sample usage
{: #sample-logger-usage}

**Note:** Make sure that you set up the [{{site.data.keyword.mobileanalytics_short}} Client SDK](sdk.html) before using the logging framework.
<!-- link to getting-started.md-->

The following code snippets show sample Logger usage:

### Android
{: #enable-logger-sample-android}

```Java
// Configure Logger to save logs to the device
Logger.storeLogs(true);

// Set the minimum log level to be printed in the console and saved on the device
Logger.setLogLevel(Logger.LEVEL.INFO);

// Create two logger instances
// You can create multiple log instances to organize your logs
Logger logger1 = Logger.getLogger("logger1");
Logger logger2 = Logger.getLogger("logger2");

// Log messages with different levels
// Debug message for feature 1
// Info message for feature 2
logger1.debug("debug message"); //this message will not be logged because the logLevelFilter is set to Info
logger2.info("info message");

// Send logs to the {{site.data.keyword.mobileanalytics_short}} Service
Logger.send();```

### iOS - Swift
{: #enable-logger-sample-swift}

```Swift
// Configure Logger to save logs to the device
Logger.logStoreEnabled = true

// Set the minimum log level to be printed in the console and saved on the device
Logger.logLevelFilter = LogLevel.Info

// Create two logger instances
// You can create multiple log instances to organize your logs
let logger1 = Logger.loggerForName("feature1Logger")
let logger2 = Logger.loggerForName("feature2Logger")

// Log messages with different levels
logger1.debug("debug message for feature 1") //this message will not be logged because the logLevelFilter is set to Info
logger2.info("info message for feature 2")

// Send persisted logs to the {{site.data.keyword.mobileanalytics_short}} Service
Logger.send()

```

<!-- ### Cordova-->
<!--{: #enable-logger-sample-cordova}-->

<!--// Enable persisting logs-->
<!--MFPLogger.setCapture(true);-->

<!--// Set the minimum log level to be printed and persisted-->
<!--MFPLogger.setLevel(MFPLogger.INFO);-->

<!--var logger1 = MFPLogger.getInstance("logger1");-->
<!--var logger2 = MFPLogger.getInstance("logger2");   -->

<!--// Log messages with different levels-->
<!--logger1.debug ("debug message");-->
<!--logger2.info ("info message");-->

<!--// Send persisted logs to the {{site.data.keyword.mobileanalytics_short}} Service-->
<!--```-->

## Enabling the {{site.data.keyword.mobileanalytics_short}} Client SDK internal logs
{: #enable-logger-sdklogs}

The {{site.data.keyword.mobileanalytics_short}} Client SDK provides a better development experience by not unnecessarily increasing the console output with its internal debug messages. Therefore, by default, internal log messages that are produced by the {{site.data.keyword.mobileanalytics_short}} SDK with the DEBUG level are not printed. You can enable printing of all internal log messages of the {{site.data.keyword.mobileanalytics_short}} Client SDK with the following API:

### Android
{: #enable-logger-print-android}
```
Logger.setSDKDebugLoggingEnabled(true);
```

### iOS - Swift
{: #enable-logger-print-swift}
```
Logger.sdkDebugLoggingEnabled = true
```

## Next steps
{: #next-steps}

* Launch the MobileFirst Analytics Console to view usage analytics:
  * [Create custom charts](custom_charts/c_op_analytics_custom_charts.html)
  * [Create alerts](alerts/c_op_analytics_alerts.html)
  * Troubleshoot your apps with [app crash](app_crash/c_op_analytics_crashes.html) data
