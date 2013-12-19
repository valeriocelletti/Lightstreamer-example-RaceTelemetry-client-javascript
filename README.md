# Lightstreamer - Race Telemetry Demo - HTML Client #

This project includes a simple web client front-end example for the [Lightstreamer - Race Telemetry Demo - Java Adapter](https://github.com/Weswit/Lightstreamer-example-RaceTelemetry-adapter-java).

<table>
  <tr>
    <td style="text-align: left">
      &nbsp;<a href="http://demos.lightstreamer.com/WebTelemetryDemo/" target="_blank"><img src="screen_telemetry.png"></a>&nbsp;
      
    </td>
    <td>
      &nbsp;An online demonstration is hosted on our servers at:<br>
      &nbsp;<a href="http://demos.lightstreamer.com/WebTelemetryDemo/" target="_blank">http://demos.lightstreamer.com/WebTelemetryDemo/</a>
    </td>
  </tr>
</table>

The Web-Telemetry Demo uses the <b>JavaScript Client API for Lightstreamer</b> to show how Lightstreamer can be used to send real-time telemetry data through the Web.<br>
In this demo, the data is generated by a feed simulator. Actual feed adapters were created to deliver real data.<br>

The demo includes the following client-side technologies:
* A [Subscription](http://www.lightstreamer.com/docs/client_javascript_uni_api/Subscription.html) containing 1 item, subscribed to in <b>MERGE</b> mode, with some of the metrics pertaining to the car, feeding a [StaticGrid](http://www.lightstreamer.com/docs/client_javascript_uni_api/StaticGrid.html).
* A [Subscription](http://www.lightstreamer.com/docs/client_javascript_uni_api/Subscription.html) containing 1 item, subscribed to in <b>DISTINCT</b> mode, with the data for each lap feeding a [DynaGrid](http://www.lightstreamer.com/docs/client_javascript_uni_api/DynaGrid.html).
* A [Subscription](http://www.lightstreamer.com/docs/client_javascript_uni_api/Subscription.html) containing 1 item (the same of the first Subscription but at a lower frequency), subscribed to in <b>MERGE</b> mode feeding two [Chart](http://www.lightstreamer.com/docs/client_javascript_uni_api/Chart.html)s, used to plot the speed and the engine RPM.

# Deploy #

Before you can run the demo some dependencies need to be solved:

-  Get the lightstreamer.js file from the [latest Lightstreamer distribution](http://www.lightstreamer.com/download) 
   and put it in the src/js folder of the demo (if that is the case, please create it). Alternatively you can build a lightstreamer.js file from the 
   [online generator](http://www.lightstreamer.com/distros/Lightstreamer_Allegro-Presto-Vivace_5_1_1_Colosseo_20130305/Lightstreamer/DOCS-SDKs/sdk_client_javascript/tools/generator.html).
   In that case be sure to include the LightstreamerClient, Subscription, DynaGrid, StaticGrid, Chart, SimpleChartListener and StatusWidget modules and to use the "Use AMD" version.
-  Get the require.js file form [requirejs.org](http://requirejs.org/docs/download.html) and put it in the src/js folder of the demo.

You can deploy this demo in order to use the Lightstreamer server as Web server or in any external Web Server you are running. 
If you choose the former case please create the folders "<LS_HOME>/pages/demos/RaceTelemetryDemo" then copy here the contents of the /src folder of this project.<br>
The client demo configuration assumes that Lightstreamer Server, Lightstreamer Adapters and this client are launched on the same machine. Hence the [FORMULA1_ADAPTER](https://github.com/Weswit/Lightstreamer-example-RaceTelemetry-adapter-java) and [LiteralBasedProvider](https://github.com/Weswit/Lightstreamer-example-ReusableMetadata-adapter-java) Adapters have to be deployed in your local Lightstreamer server instance.<br>
If you need to targeting a different Lightstreamer server please search this line:
```js
var lsClient = new LightstreamerClient(protocolToUse+"//localhost:8080","F1Telemetry");
```
in js/lsClient.js file and change it accordingly. For example if you want to target the adapter deployed in our server you should substitute with this:
```js
var lsClient = new LightstreamerClient(protocolToUse+"//push.lightstreamer.com","F1Telemetry");
```
<br>
The demo are now ready to be launched.

# See Also #

## Lightstreamer Adapters needed by this demo client ##

* [Lightstreamer - Race Telemetry Demo - Java SE  Adapter](https://github.com/Weswit/Lightstreamer-example-RaceTelemetry-adapter-java)
* [Lightstreamer - Reusable Metadata Adapters - Java Adapter](https://github.com/Weswit/Lightstreamer-example-ReusableMetadata-adapter-java)

## Similar demo clients that may interest you ##

* [Lightstreamer - Stock-List Demos - HTML Clients](https://github.com/Weswit/Lightstreamer-example-StockList-client-javascript)

# Lightstreamer Compatibility Notes #

- Compatible with Lightstreamer JavaScript Client library version 6.0 or newer.
