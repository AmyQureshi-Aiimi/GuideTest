# Auditing

Secondary auditing sends user activity to a second audit location outside of Workplace AI. Enabling this does not change how primary auditing is logged, that is always sent to Elastic.

A plugin must be configured and secondary auditing must be enabled and configured in the Control Hub. We currently have a plugin for CEF Audit Provider available.

### CEF Auditing

CEF stands for Common Event Format. The CEF Audit Provider plugin creates CEF format messages and logs them via log4net. Using log4net allows the destination to be anything supported by log4net. For example, a rolling file, a database or a remote syslog service.

## Configuring the CEF Audit Provider Plugin

### Create a Log4Net file

1. Create a file called log4net.config
2. The file must start with `<log4net>` and end with `</log4net>` .
3. Save this file in the Search API folder.

### log4net: logger

To configure CEF auditing, you must set a log4net _logger_ in the log4net.config file. This is currently limited to user activity, so needs to go in the Search API folder.

1. Add the following code to the log4net file.
   * Make sure this is between `<log4net>` and `</log4net>`_._

<pre class="language-log" data-overflow="wrap" data-line-numbers><code class="lang-log"><strong>&#x3C;logger additivity="false" name="cef">
</strong>  &#x3C;level value="INFO"/>
  &#x3C;appender-ref ref="CEFFileAudit" />
 &#x3C;/logger>
</code></pre>

2. Save the log4net.config file.

All CEF messages will be sent to this logger. It is configured to use the `CEFFileAudit` appender to output the messages.&#x20;

`additivity="false"` - This means messages will only go to this appender. Because of this, to see any messages the `level` must be at least `INFO`.

### log4net: appender

Once the logger is created, a matching appender is needed. The example below uses the RollingFileAppender, but others can be configured as needed.

* The below code is added to the Log4net.config file.
  1. It sits above the logger configuration but still between the _\<log4net>_ and _\</log4net>._
  2. The file value path should match your systems setup.

{% code overflow="wrap" lineNumbers="true" %}
```log
<appender name="CEFFileAudit" type="log4net.Appender.RollingFileAppender">
 <file value="c:/tmp/logs/InsightMaker.Middleware.Search.UserActivity.log" />
 <appendToFile value="true" />
 <rollingStyle value="Size" />
 <maxSizeRollBackups value="10" />
 <maximumFileSize value="10240KB" />
 <staticLogFileName value="true" />
 <layout type="log4net.Layout.PatternLayout">
  <!-- date hostname  CEF:1|DeviceVendor|DeviceProduct|DeviceVersion|DeviceEventClassID|Name|Severity|[Extension] -->
  <!-- date and hostname are optional, they are part of the syslog spec which CEF is built on -->
  <conversionPattern value="%date{yyyy-MM-dd HH:mm:ss,ffff} %P{hostname} %P{cefVersion}|%P{imCompany}|%P{imProduct}|%P{imVersion}|%P{imEventType}|%P{imEventName}|%P{imEventSeverity}|%P{imEventProperties}%newline" />
    </layout>
```
{% endcode %}

The Workplace AI and CEF specific config is defined in the _conversionPattern,_ it defines the format of the audit message.

You can customise the audit message with the components from the table.

<table><thead><tr><th width="298.716796875">Component</th><th width="460.8087158203125">Description</th></tr></thead><tbody><tr><td>%date{yyyy-MM-dd HH:mm:ss,ffff}</td><td>The date in the specified format.</td></tr><tr><td>%P{hostname}</td><td>The hostname. This is constructed using the same logic as the agent name (without the suffix) so environmental overrides will be included.</td></tr><tr><td>%P{cefVersion}</td><td>The CEF version header. This is hardcoded to CEF:1.</td></tr><tr><td>%P{imCompany}</td><td>Aiimi</td></tr><tr><td>%P{imProduct}</td><td>The part of the Workplace AI that produced the audit. This is calculated from the entry assembly.</td></tr><tr><td>%P{imVersion}</td><td>The product version. This is calculated from build tag, which should be the version e.g. 2024.02.1.</td></tr><tr><td>%P{imEventType}</td><td>The type of event: analytics, collection, view_folder, hit, linkHit, search or tool_call.</td></tr><tr><td>%P{imEventName}</td><td>The sub type of event. For example, for hit it could be preview or download.</td></tr><tr><td>%P{imEventSeverity}</td><td>As this is an audit it defaults to the CEF medium (5).</td></tr><tr><td>%P{imEventProperties}</td><td>Additional properties formatted as per the CEF extension field. The specifics depend on the event type, this could include: user, email, search terms, query string, etc.</td></tr></tbody></table>

## Control Hub Configuration

Once you have set up the logger and appender you need to enable and configure secondary auditing in Control Hub.

1. Within the Control Hub go to Security > Auditing.
2. **Secondary Auditing Interests** - Check which event types from Workplace AI are sent to the secondary audit.
3. **Secondary Audit Provider** - Select the provider for this secondary audit.
   * This is currently limited to CEFAudit only.
4. **Logger Name** - Enter the name of the log4net logger created above.
5. **Date Format** - Enter the format for date ranges.
   * The CEF specification recommends a US date format.
   * This only converts date range fields. Dates sent as a string will be logged in the format used by the middleware.
6. **Include Lenses** - If checked, when logging search messages, the file lens used will be included in CEF.
   * This is enabled by default but can quickly fill up an audit trail.
7. **Include identifiers** - If checked, when logging search messages, the file identifier for files on each result page will be included in CEF.
   * This is enabled by default but can quickly fill up an audit trail.



