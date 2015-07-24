### 1.0-beta.8.7 ###
  * DaleHenrichs 6/20/2012 10:13
  * Announcements
  * 1.0-beta.8.7 (dkh.144):
    * open 1.0-beta.8.7 for deveopment
    * Configurations don''t have to be explicitly loaded now that we are bootstrapping Metacello 1.0-beta.31.1
  * 1.0-beta.8.7 (dkh.145):
    * tweak to get the load to load correctly ... satisfactory results, but nee dto look closer
  * 1.0-beta.8.7 (dkh.148):
    * support for GemStone 3.1
  * 1.0-beta.8.7 (dkh.149):
    * libICU (Unicode) support for GemStone 3.1
  * 1.0-beta.8.7 (dkh.150):
    * libICU (Unicode) support for GemStone 3.1....round 2
### 1.0-beta.8.6 ###
  * DaleHenrichs 11/17/2011 13:53
  * Announcements
    * [GemTools 1.0-beta.8.6](http://gemstonesoup.wordpress.com/2011/11/18/gemtools-1-0-beta-8-6/)
  * 1.0-beta.8.6 (dkh.141):
    * open 1.0-beta.8.6 for deveopment
    * fix [Issue 308](https://code.google.com/p/glassdb/issues/detail?id=308): ConfigurationOfGrease (and others) dirty after a load
  * 1.0-beta.8.6 (dkh.142):
    * fix [Issue 309](https://code.google.com/p/glassdb/issues/detail?id=309): ConfigurationofMetacello dirtied during GLASS 1.0-beta.8.7.1 load
    * upgrade process now involves:
      * preload of basic Metacello packages for version 1.0-beta.31.1 to ensure symbolic versions and MetacelloSkipDirtyPackageLoad notification are available for subsequent load operations ... this preload does not use Metacello
      * load of just ''Core'' and ''Monticello'' GLASS projects to ensure that the latest Monticello is available
      * ''Standard'' load of the GLASS project

### 1.0-beta.8.5 ###
  * DaleHenrichs 10/20/2011 16:57
  * Announcements
    * [GLASS 1.0-beta.8.7 released](http://forum.world.st/GLASS-1-0-beta-8-7-released-td3923882.html)
    * [GemTools 1.0-beta.8.5](http://gemstonesoup.wordpress.com/2011/10/21/gemtools-1-0-beta-8-5/)
  * adjust for new GCI error message behavior
  * stop using a deprecated method
  * add GemTools support for MetacelloBrowser
  * fix a bug in OGUpgradeJadeServer>>upgradeGLASSServer
  * add support for SymbolList Browser
  * 1.0-beta.8.5 (dkh.126):
    * support for button panel in MetacelloBrowser for GemTools
  * 1.0-beta.8.5 (dkh.127):
    * remove unnecessary logging
  * 1.0-beta.8.5 (dkh.128):
    * tweak upgrade process to make sure that Monticello gets loaded so we can leverage any load bugfixes for remaining package loads
  * 1.0-beta.8.5 (dkh.129):
    * let''s load Metacello before doing anything else during a GLASS upgrade
  * 1.0-beta.8.5 (dkh.130):
    * fix [Issue 280](https://code.google.com/p/glassdb/issues/detail?id=280): GemTools login error: ''Network error - text follows'', does not follow with error message...
  * 1.0-beta.8.5 (dkh.131):
    * fix [Issue 250](https://code.google.com/p/glassdb/issues/detail?id=250): order and size of args asociated with #halt changed in Gci3xErrStype64 (GemStone 3.0)
  * 1.0-beta.8.5 (dkh.132):
    * revert load order change from (dkh.129)
    * don''t show #broken versions in GLASS update menu
  * 1.0-beta.8.5 (dkh.133):
    * tweak Update GemTools menu builder
  * 1.0-beta.8.5 (dkh.134):
    * to work around Metacello [Issue 136](https://code.google.com/p/glassdb/issues/detail?id=136) ... needs latest configuration versions loaded
  * 1.0-beta.8.5 (dkh.136):
    * Need to load GLASS twice (wince) to make sure that 1) we''ve got the latest and greatest Metacello ... and we cannot short circuit the load then 2) any incorrect loads during first pass get correct now that we''ve got the latest and greatest Metacello
  * 1.0-beta.8.5 (dkh.137):
    * fix [Issue 291](https://code.google.com/p/glassdb/issues/detail?id=291): Maintenance Gem Topaz Exit [3.0 / GemStone 3.0](Seaside.md)
    * fix [Issue 132](https://code.google.com/p/glassdb/issues/detail?id=132): Use System class>>#''_cacheName:'' to make session recognizable in vsd
  * 1.0-beta.8.5 (dkh.138):
    * patch for Squeak from Tim Felgentreff
  * 1.0-beta.8.5 (dkh.139):
    * remove MetacelloBrowser from config
    * add some Help Browser messages...
### 1.0-beta.8.4 ###
  * DaleHenrichs 12/16/2010 12:40
  * Announcement
  * consolidate changes, so that we''re back to one GemTools-Client that works in both Pharo1.0 and Pharo1.1
  * no longer need GemTools-ProfStef
  * tweaks for Pharo 1.1.1 (pick up Johan''s changes, but use UIManager instead of PopUpMenu)
  * significant performance improvement when using SHOUT ... reduce round trips drastically!
  * fix [Issue 171](https://code.google.com/p/glassdb/issues/detail?id=171): http://code.google.com/p/glassdb/issues/detail?id=171 "need to be able to set ''Popup on debug'' without having to login"
  * fix [Issue 167](https://code.google.com/p/glassdb/issues/detail?id=167): http://code.google.com/p/glassdb/issues/detail?id=167 "Admin>>Repository>>restore w/tranlogs should be removed"
  * fix [Issue 143](https://code.google.com/p/glassdb/issues/detail?id=143): http://code.google.com/p/glassdb/issues/detail?id=143 "incorrect download path in help browser"
  * port Help Browser topics to version 1.1 of HelpSystem
  * 3.0 gci compatability
  * fixed [Issue 204](https://code.google.com/p/glassdb/issues/detail?id=204): http://code.google.com/p/glassdb/issues/detail?id=204 "remove_ assignments from GemTools code"
### 1.0-beta.8.3 ###
  * DaleHenrichs 10/4/2010 15:56
  * Announcement
    * [GemTools 1.0-beta.8.3 for Pharo 1.1](http://gemstonesoup.wordpress.com/2010/10/04/gemtools-1-0-beta-8-3-for-pharo-1-1/)
    * [GemTools for pharo 1.1](http://forum.world.st/GemTools-for-pharo-1-1-tp2542305p2955241.html)
    * 
  * pick up Pharo 1.1 changes from Norbert
### 1.0-beta.8.2 ###
  * DaleHenrichs 8/17/2010 17:30
  * Announcement
    * [GemTools 1.0-beta.8.2 released](http://forum.world.st/GemTools-1-0-beta-8-2-released-td2335893.html#a2335893)
  * improve debugger window title error messages for UserDefinedErrors and Halts. Need GLASS 1.0-beta.8.3 or later to see the improved results (see [Issue 32](https://code.google.com/p/glassdb/issues/detail?id=32)).
### 1.0-beta.8.1 ###
  * DaleHenrichs 7/29/2010 13:10
  * upgrade GLASS support for GemStone 3.0
  * fix a problem in restartSeaside gems after restore
### 1.0-beta.8 ###
  * DaleHenrichs 7/14/2010 20:23
  * Downloads
    * [Download GemTools 1.0-beta.8 for 231 One-Click](http://seaside.gemstone.com/squeak/GemTools-1.0-beta.8-231x.app.zip)
    * [Download GemTools 1.0-beta.8 for 244 One-Click](http://seaside.gemstone.com/squeak/GemTools-1.0-beta.8-244x.app.zip)
  * Announcements:
    * [GemStone/S 64 Version 2.4.4.1 is Shipping](http://gemstonesoup.wordpress.com/2010/07/15/gemstones-64-version-2-4-4-1-is-shipping/)
  * update instructions for building your own GemTools image (add GemStone/S 2.4 instructions)
  * use HelpBrowser for Squeak
### 1.0-beta.7 ###
  * DaleHenrichs 7/13/2010 15:41
  * [Download 1.0-beta.6 One-Click GemTools](http://seaside.gemstone.com/squeak/GemTools-1.0-beta.6.zip) and [update GemTools to 1.0-beta.7](GemToolsUpdate#Update_GemTools_Launcher.md).
  * add support for start/stop/restart Seaside30 gems
### 1.0-beta.6 ###
  * DaleHenrichs 5/26/2010 16:10
  * [Download 1.0-beta.6 One-Click GemTools](http://seaside.gemstone.com/squeak/GemTools-1.0-beta.6.zip)
  * Announcements:
    * [GemTools Client 1.0-beta.6](http://gemstonesoup.wordpress.com/2010/05/26/gemtools-client-1-0-beta-6/)
  * fixed highlighting for class definition/creation template
  * enabled syntax highlighting in workspaces
  * double click includes leading $`_`. In package GemTools-Overrides that is not loaded by default, because it stomps on a method in Character.
  * GsOBColumnPanel>>currentNode sends #currentNode to server-side, fixing a couple of ancient bugs
  * reset GLASS version after doing a Server update
  * exclude #baseline versions from update glass client version list
  * add proportional splitters to inspectors (resize panes vertically)
  * Use Help System instead of ProfStef
  * fix [Issue 54](https://code.google.com/p/glassdb/issues/detail?id=54) "Typos and unclear instructions in GemTools ProfStef tutorial"
  * add ''Admin>>Doit...>>Version Report'' menu item (included in bug report template) that shows versions of all installed configs
  * add toggle ''Admin>>Commit on Almost Out of Memory'' command
  * upgrade path from 0.231,  0.232.2 and 1.0-beta.0 through 1.0-beta.7 to 1.0-beta.8
  * tested with:
    * Pharo 1.0
    * Squeak 4.1
### 1.0-beta.5 ###
  * fix bug in the new GCI library code ... linux-gnu is also a valid os name
### 1.0-beta.4 ###
  * - Rename GCI library for Squeak 3.11.3-2135
### 1.0-beta.3 ###
see [GemTools Client 1.0-beta.3](http://gemstonesoup.wordpress.com/2010/01/25/gemtools-client-1-0-beta-3/)