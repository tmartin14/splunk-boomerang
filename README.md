# splunk-boomerang
This is a Splunk Application for visualizing data sent from <a href="https://soasta.github.io/boomerang/doc/">Boomerang.js</a>

## Installation
- The installation of End User Monitoring consists of 3 parts:
  - Configure an HTTP Event Collector endpoint to recieve the metrics
  - Edit the inputs.conf file for your new HEC input (allow CrossOriginSharingPolicy)
  - Add Boomerang.js to your web pages
  
Detailed installation instructions can be found in the Setup Instructions dashboard in the app.

<a href="BoomerangDashboard.png" rel="Sample Screenshot"><img src="BoomerangDashboard.png" alt="Sample Screenshot" /></a>

## Quick Installation Sample
Add the following code to your web pages (in the \"\<HEAD\>\" section)
~~~~
<HEAD>
<script src="/js/boomerang.js" />
<script src="/js/plugins/rt.js" />
<script src="/js/plugins/navtiming.js" />
<script src="/js/plugins/guid.js" />

<script>
 BOOMR.init({
    beacon_url: "http://splunk_server:HECport/services/collector/raw?channel=XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX",
    beacon_auth_token: "Splunk XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX",
    beacon_type: "POST"
 });
  
 BOOMR.addVar({ "ua_raw": navigator.userAgent	 });          // used in Splunk dashboards
 BOOMR.addVar({ "guid": BOOMR.utils.getCookie("GUID")	 });  // uniquely identify this user
</script>     
...
</HEAD>
~~~~

Optionally add in any other metrics in you like anywhere in your web page
~~~~
<script>
    BOOMR.addVar({
  		"activity_name": "checkout",		
  		"item_id": 1234,
  		"item_name": "iPad Air",
  		"order_total": 450.00
  	});
  </script>     
  ~~~~
  
