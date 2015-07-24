With Seaside 3.0.0-alpha5.15 the [runSeasideGems30](RunSeasideGems30Script.md) script is configurable_**without having to edit the script**_. You can use the following expressions to control which web server adaptor is used, the number of gems launched by the script and the port that each gem's adaptor will listen on:
```
"Specify FastCGI for runSeasideGems30 and start 3 vms listening on 
 ports 9001,  9002, and 9003"
WAGemStoneRunSeasideGems default
	name: 'FastCGI';
	adaptorClass: WAFastCGIAdaptor;
	ports: #(9001 9002 9003).

"Specify Swazoo for runSeasideGems30 and start 1 vm listening on port 8383"
WAGemStoneRunSeasideGems default
	name: 'Swazoo';
	adaptorClass: WAGsSwazooAdaptor;
	ports: #(8383).
```
Also in addition to the [GemTools Launcher Admin>>Seaside gems menu item](GemToolsAdmin#Seaside_gems.md), you can start/stop/restart the seaside gems programmatically:
```
WAGemStoneRunSeasideGems startGems.   "start gems"
WAGemStoneRunSeasideGems stop.        "stop gems"
WAGemStoneRunSeasideGems restartGems. "restart gems"
```