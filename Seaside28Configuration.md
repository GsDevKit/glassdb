## Seaside 2.8 ##
Here’s the list of packages available in the [Seaside2.8](http://seaside.st/community/development/seaside28) project:

  * Seaside2.8g1
  * SeasideAsync
  * Scriptaculous
  * RSRSS2
  * FastCGISeaside
  * HyperSeaside
For info on setting up web servers (lighttpd, apache, or nginx) or using Hyper and FastCGI, see the [Seaside page](SeasideConfiguration.md)

### Loading ###
```
  MCPlatformSupport commitOnAlmostOutOfMemoryDuring: [
    Gofer project load: 'Seaside28'.
  ].
```
## Additional Seaside 2.8 Projects ##
Here's a list of adddditional GLASS projects for Seaside 2.8:
  * Seaside28Examples
  * Magritte (see [Magritte](http://www.lukas-renggli.ch/smalltalk/magritte))
  * Pier (see [Pier](http://www.piercms.com/))
  * PierAddOns (see [Pier](http://www.piercms.com/))
  * GsSeasideTesting28 (see [GLASS 101: Using SeasideTesting with GLASS](http://gemstonesoup.wordpress.com/2009/02/10/glass-101-using-seasidetesting-with-glass/))
  * GsSqueakSource
  * GsScaffolding (see [Scaffolding for GemStone](http://gemstonesoup.wordpress.com/2008/11/13/scaffolding-for-gemstone/))
### Loading ###
Execute one or more of the following expressions to install the project or projects that you are interested in:
```
MCPlatformSupport commitOnAlmostOutOfMemoryDuring: [
        ConfigurationOfMetacello project updateProject.
        ConfigurationOfMetacello loadLatestVersion.

        Gofer project load: 'Seaside28Examples'.
        Gofer project load: 'GsSeasideTesting28'. "Seaside2.8 testing"
        Gofer project load: 'Magritte'.
        Gofer project load: 'Pier'.
        Gofer project load: 'GsSeasideTesting28' group: #( 'PierTesting' ). "Pier testing"
        Gofer project load: 'PierAddOns'.
        Gofer project load: 'GsSqueakSource'.
        Gofer project load: 'GsScaffolding'.
].
```