## Seaside 3.0 ##
[Seaside3.0](http://www.seaside.st/community/development/seaside30) on GLASS requires [Gemstone/S 64 2.4.4.1](http://gemstonesoup.wordpress.com/2010/07/15/gemstones-64-version-2-4-4-1-is-shipping/) which is available on the [GLASS downloads page](http://seaside.gemstone.com/downloads.html).

For info on setting up web servers (lighttpd, apache, or nginx) or using Hyper and FastCGI, see the [Seaside page](SeasideConfiguration.md).

It is possible to load all of the Seaside 3.0 packages into GLASS using the following expression:
```
  MCPlatformSupport commitOnAlmostOutOfMemoryDuring: [
    ConfigurationOfMetacello project updateProject.
    ConfigurationOfMetacello loadLatestVersion.
    Gofer project load: 'Seaside30'.
  ].
```
Beginning with Seaside 3.0.0-alpha5.15 groups have been defined to make it possible to easily load bits and pieces and [more importantly the configurations for the Magritte2 and Pier2 projects have been changed so that they take advantage of the new organization](http://forum.world.st/ANN-new-config-versions-for-Seaside30-Grease-Magritte2-Pier2-Pier2AddOns-td2287876.html#a2287876), so it is worth reading through the following section to get a feel for the changes and new possibilities.
### Base group ###
The base group for Seaside 3.0.0-alpha5.15 includes the following packages:
  * Seaside-Core
  * Seaside-Canvas
  * Seaside-Session
  * Seaside-Component
  * Seaside-RenderLoop
  * Seaside-Tools-Core
  * Seaside-Flow
  * Seaside-Environment
  * Seaside-Widgets
These packages form the core of Seaside 3.0 and therefore should be loaded as a unit. The 'Base' Metacello group has been defined to make that easy.
#### Loading ####
To load the Seaside 3.0 'Base' group into GLASS, evaluate the following expression:
```
  Gofer project load: 'Seaside30' group: 'Base'.
```
At this point in time there are no applications registered and there are no [web server adaptors](http://blog.fitzell.ca/2009/03/seaside-server-adaptors.html) loaded. The 'Base' group does form a nice dependency for a Seaside application.
### Magritte2 and Pier2 ###
[Magritte2](http://www.lukas-renggli.ch/smalltalk/magritte) and [Pier2](http://www.piercms.com/) are two Seaside applications that are built on top of Seaside 3.0. When you load Magritte2 or Pier2 into GLASS, only the 'Base' Seaside3.0 group is loaded so you will need to load a web adaptor at a minimum.
#### Loading ####
To load the Seaside3.0 support for Magritte2 into GLASS, evaluate the following expression:
```
MCPlatformSupport commitOnAlmostOutOfMemoryDuring: [
  ConfigurationOfMetacello project updateProject.
  ConfigurationOfMetacello loadLatestVersion.
  Gofer project load: 'Magritte2' group: 'Magritte-Seaside'.
].
```
As part of the Magritte-Seaside target, a Magritte example application is registered.
To load the Pier2 into GLASS, evaluate the following expression:
```
MCPlatformSupport commitOnAlmostOutOfMemoryDuring: [
  ConfigurationOfMetacello project updateProject.
  ConfigurationOfMetacello loadLatestVersion.
  Gofer project load: 'Pier2'.
  Gofer project load: 'PierAddOns2'.
  PRDistribution new register. "create and register the Pier Seaside3.0 application"
].
```
The PierAddOns2 project includes the Pier-Setup mcz package simplifies the creation of a new Pier instance (defining **PRDistribution**).
### Server Adaptors ###
Now is the time to think about which adaptor you will use to server your web pages. For GLASS you can choose the [Swazoo Adaptor](SwazooAdaptor.md) or the [FastCGI Adaptor](FastCGIAdaptor.md). To install evaluate one of the following expressions:
```
MCPlatformSupport commitOnAlmostOutOfMemoryDuring: [
  ConfigurationOfMetacello project updateProject.
  ConfigurationOfMetacello loadLatestVersion.
  Gofer project load: 'Seaside30' group: 'Seaside-Adaptors-FastCGI'.
  Gofer project load: 'Seaside30' group: 'Seaside-Adaptors-Swazoo'.
  Gofer project load: 'Seaside30' group: #('Seaside-Adaptors-FastCGI' 'Seaside-Adaptors-Swazoo').
].
```
While we're talk about adaptors don't forget to take a look at:
    * [Controlling Seaside 3.0 Gems](ControllingSeaside30Gems.md)
    * [Maintenance VM Tasks](MaintenanceVMTasks.md)
### Development group ###
The development group for Seaside 3.0.0-alpha5.15 includes the following targets:
  * Base group
  * Seaside-Development
To install the development group into GLASS evaluate the following expression:
```
MCPlatformSupport commitOnAlmostOutOfMemoryDuring: [
  ConfigurationOfMetacello project updateProject.
  ConfigurationOfMetacello loadLatestVersion.
  Gofer project load: 'Seaside30' group: 'Development'.
].
```
**Note:** _if you intend to load the 'Development' group, there is no need load the 'Base' group separately._
### Loading Additional Seaside 3.0 packages ###
The remaining Seaside 3.0.0-alpha5.15 packages can be loaded independently into GLASS if desired:
  * RSS-Core
  * RSS-Examples
  * Javascript-Core
  * JQuery-Core
  * JQuery-UI
  * Prototype-Core
  * Scriptaculous-Core
  * Scriptaculous-Components
  * Seaside-Email
  * Seaside-Examples
  * Seaside-HTML5
  * Seaside-InternetExplorer
  * Seaside-Tools-OmniBrowser
  * Seaside-Tools-Web
  * Seaside-Welcome
You may use any one of the following expressions to install the package into GLASS:
```
MCPlatformSupport commitOnAlmostOutOfMemoryDuring: [
  ConfigurationOfMetacello project updateProject.
  ConfigurationOfMetacello loadLatestVersion.
  Gofer project load: 'Seaside30' group: 'RSS-Core'.
  Gofer project load: 'Seaside30' group: 'RSS-Examples'.
  Gofer project load: 'Seaside30' group: 'Javascript-Core'.
  Gofer project load: 'Seaside30' group: 'JQuery-Core'.
  Gofer project load: 'Seaside30' group: 'JQuery-UI'.
  Gofer project load: 'Seaside30' group: 'Prototype-Core'.
  Gofer project load: 'Seaside30' group: 'Scriptaculous-Core'.
  Gofer project load: 'Seaside30' group: 'Scriptaculous-Components'.
  Gofer project load: 'Seaside30' group: 'Seaside-Email'.
  Gofer project load: 'Seaside30' group: 'Seaside-Examples'.
  Gofer project load: 'Seaside30' group: 'Seaside-HTML5'.
  Gofer project load: 'Seaside30' group: 'Seaside-InternetExplorer'.
  Gofer project load: 'Seaside30' group: 'Seaside-Tools-OmniBrowser'.
  Gofer project load: 'Seaside30' group: 'Seaside-Tools-Web'.
  Gofer project load: 'Seaside30' group: 'Seaside-Welcome'.
].
```
If you are installing more than one package you may combine the package names into a single expression like the following:
```
MCPlatformSupport commitOnAlmostOutOfMemoryDuring: [
  ConfigurationOfMetacello project updateProject.
  ConfigurationOfMetacello loadLatestVersion.
  Gofer project 
    load: 'Seaside30' 
    group: #('RSS-Core' 'Prototype-Core' 'Seaside-Tools-OmniBrowser').
].
```
### Load Pier, Magritte, and Seaside Avoiding Out of Memory Conditions ###
If you'd like to install Seaside3.0, Pier and Magritte, the following expression should be used:
```

| autoCommit|
autoCommit := MCPlatformSupport autoCommit.
MCPlatformSupport autoCommit: true. "needed if loading from Topaz"
MCPlatformSupport commitOnAlmostOutOfMemoryDuring: [[
                 ConfigurationOfMetacello project updateProject.
                 ConfigurationOfMetacello loadLatestVersion.
                 Gofer project load: 'Seaside30'group: #( 'ALL').
                 Gofer project load: 'Pier2' group: 'ALL'.
                 Gofer project load: 'PierAddOns2' group: 'ALL'.
         ]
                 on: Warning
                 do: [:ex |
                         Transcript cr; show: ex description.
                         ex resume ]].
MCPlatformSupport autoCommit: autoCommit.
```
Note the use of `MCPlatformSupport commitOnAlmostOutOfMemoryDuring:` that avoids most out-f-memory situations.