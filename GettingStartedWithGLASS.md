The best way to get started with [GLASS](GLASS.md) is to (the following instructions have not been tested with Squeak, but it is expected that the instructions will work equally well for Squeak):
  * [Download the GemTools 1.0-beta.8 One-Click client](http://seaside.gemstone.com/downloads.html) which is based on [Pharo 1.0](http://www.pharo-project.org/pharo-download/release-1-0)
    * or [Install GemTools into a Squeak or Pharo image](http://code.google.com/p/glassdb/wiki/InstallGemTools)
  * Open a [GemTools Help Browser](GemToolsHelp.md) for up-to-date help on the following topics:
    1. [GemStone/S Server installation](GettingStartedWithGLASS#GemStone_/S_Server_installation.md)
    1. [Custom Extent Creation](GettingStartedWithGLASS#Custom_Extent_Creation.md)
    1. [Install GemTools](GettingStartedWithGLASS#Install_GemTools.md)
    1. [Install GCI library files](GettingStartedWithGLASS#Install_GCI_library_files.md)
    1. [Define GemTools Session](GettingStartedWithGLASS#Define_GemTools_Session.md)
    1. [Open GemTools Launcher](GettingStartedWithGLASS#Open_GemTools_Launcher.md)
    1. [Start stone and netldi](GettingStartedWithGLASS#Start_stone_and_netldi.md)
    1. [Log into the GemStone server](GettingStartedWithGLASS#Log_into_the_GemStone_server.md)
    1. [Backup repository](GettingStartedWithGLASS#Backup_repository.md)
    1. [Update GLASS](GettingStartedWithGLASS#Update_GLASS.md)
    1. [Load optional projects](GettingStartedWithGLASS#Load_optional_projects.md)

### GemStone/S Server installation ###
If you have experience installing GemStone/S, and are comfortable with setting up Apache or FastCGI and other system and network administration tasks, the native install is a good option:

  * download native install for Linix or Mac from http://seaside.gemstone.com/downloads.html
  * follow the installation instructions at http://seaside.gemstone.com/userguide.html#Linux-installation
  * follow the installation instructions that other folks have documented http://gemstonesoup.wordpress.com/glass-101/#GLASSonSlicehost
  * follow the getting starting gemstone instructions at http://seaside.gemstone.com/userguide.html#starting-gemstone

Otherwise, you should consider installing VMWare and then downloading the VMWare GLASS appliance. With the appliance GemStone, the server gems and Apache are automatically started and shutdown, so there's very little muss and fuss involved:

  * download VMWare GLASS appliance from http://seaside.gemstone.com/downloads.html
  * follow the installation instructions at http://seaside.gemstone.com/userguide.html#MacOSX-installation

Once you have your GemStone server (or appliance) installed, you should follow the instructions for [installing GemTools](GettingStartedWithGLASS#Install_GemTools.md).

### Custom Extent Creation (GemStone 2.4.4.1) ###
GemStone/S ships with a pre-built extent `$GEMSTONE/bin/extent0.seaside.dbf`. In GemStone 2.4.4.1 and later, the extent is preloaded with only the base GLASS classes loaded (Seaside is not preloaded). To create a custom extent, simply load the Metacello configurations for the projects that you want loaded into your extent.

### Custom Extent Creation (GemStone 2.3.x) ###
GemStone/S ships with a pre-built extent `$GEMSTONE/bin/extent0.seaside.dbf`. If you want to bootstrap your own extent, then follow these instructions:

  1. Stop your stone:
```
      stopGemstone
```
  1. Copy a virgin extent into the seaside/data directory:
```
      cp $GEMSTONE/bin/extent0.dbf $GEMSTONE/seaside/data
      chmod +w $GEMSTONE/seaside/data/extent0.dbf
```
  1. Start your stone:
```
      startGemStone
```
  1. Download (from http://seaside.gemstone.com/squeak/bootstrap_1.0-beta.4.zip) and unzip bootstrap\_1.0-beta.4.zip.
  1. cd to the bootstrap-1.0-beta.4 directory
  1. Edit the .topazini file to match your stone.
  1. Launch topaz:
> > topaz -l -T50000
  1. `login` and `input installMaster.topaz`
  1. Exit topaz.

If you don't already have a GemTools Launcher then follow the [installation instructions in the GemTools Installation section](GettingStartedWithGLASS#Installation.md). If you already have a GemTools Launcher then you should follow the [updating instructions in the GemTools Installation section](GettingStartedWithGLASS#Updating.md).

### Install GemTools ###
To install GemTools you must load the configurationOfGemTools into your image.

As an alternative to building your own GemTools client image, you can [download a one-click Pharo image](http://gemstonesoup.wordpress.com/2010/05/28/gemtools-1-0-beta-6-one-click-available/) with GemTools pre-installed and then skip to the [Define GemTools Session section](GettingStartedWithGLASS#Define_GemTools_Session.md).

#### Installation ####
In Pharo, evaluate the following statements:
```
  Gofer new
        squeaksource: 'MetacelloRepository';
        package: 'ConfigurationOfGemTools';
        load.
```
In Squeak image, evaluate the following statements:
```
  (Installer repository:
    'http://www.squeaksource.com/MetacelloRepository')
        install: 'ConfigurationOfGemTools'. 
```
#### Updating ####
Then evaluate the following expression to load the lastest version of GemTools:
```
  (Smalltalk at: #ConfigurationOfGemTools) 
	perform: #loadLatestVersion.
```
This expression opens the GemTools Help Browser (Pharo only in 1.0-beta.6):
```
  (Smalltalk at: #GemToolsHelpBrowser) open. 
```
### Install GCI library files ###
The GCI library file is a C library that contains code for communicating with the GemStone server. The source directory, destination directory and name of the GCI library file depends upon which platform you are running and how you have installed GemStone.

If you have done a native install and are running your GemTools image on the same OS as the stone, then you will copy the GCI library file from $GEMSTONE/lib32.

If the OS where the stone is running differs from the OS where you are running GemTools OS, then you should download the GemTools one-click from the [GLASS downloads page](http://seaside.gemstone.com/downloads.html) and copy the GCI library file from GemTools-1.0-beta.8-`*`x.app/Contents/Resources.

If you are using an appliance and running GemTools on Linux, you may copy the GCI library from the appliance itself.

For more information, see James' blog post: 'http://programminggems.wordpress.com/2010/02/02/name-and-location-of-gci-library/'

To finish the GCI library installation please see the instruction page for the OS upon which you are running GemTools:

  * [Mac](MacGCIInstall.md)
  * [Windows](WindowsGCIInstall.md)
  * [Linux vms preceding 3.11-3](OldLinuxVM.md)`*`
  * [Linux 3.11-3 or later vm](LinuxVM.md)`*`

`*` Note that the installation instructions for Linux is dependent upon which version of the vm that you are running.

### Define GemTools Session ###
In order to log into the stone using the GemTools Launcher, you must create a session description that includes information such as the hostName for the stone, the name of the stone, GemStone username, password, etc.

There are three different variants of session descriptions that should be used base upon the level of control you need:

  * [Appliance Session](ApplianceSessionDescription.md) should be used if you are using a standard GLASS appliance
  * [Standard Session](StandardSessionDescription.md) should be used if you have native install
  * [Custom Session](CustomSessionDescription.md) should be used if you need full control of the session description

If you have a GemTools launcher open, you can use the [New session button](http://code.google.com/p/glassdb/wiki/GemToolsSessionMenu#New_Session) to create a session description.

The [Edit session button](http://code.google.com/p/glassdb/wiki/GemToolsSessionMenu#Edit_Session) to change individual field values.
### Open GemTools Launcher ###
To open the GemTools launcher evaluate the following expression:
```
	OGLauncher open. 
```
After double checking that your session descriptions are correct, this is a good time to save your pharo image.
### Start stone and netldi ###
After installing the GemStone/S server you need to start a stone and a netldi. The netldi process is needed so that the GemTools client can communicate with the stone.

If you are using a native install, then follow the [starting gemstone instructions](StartingANativeStone.md).

If you are using an appliance, you only need to launch the appliance itself, since the stone and netldi processes are started automatically.
### Log into the GemStone server ###
Select the desired session in the GemTools Launcher session list and press the [Login button](GemToolsSessionMenu#Login.md).

Upon a successful login, the annotation pane will be filled with useful information about your session. The button bar will also be updated.
### Backup repository ###
It is always a good idea to make a backup of your repository before doing an update. You never know what might happen during the upgrade process so it is prudent to make a backup.

To make a backup click on the 'Admin...' button and select the 'Repository>>Backup' menu item. You will be prompted for a backup file name. I usually use the version name as the name of my backup (i.e., '0.231.dbf').

You can control where the backup directory is located by setting the #backupDirectory: in your session description. By default, the backups are stored in $GEMSTONE/seaside/data/backups.

If you do need to restore from a backup click on the 'Admin...' button and select the 'Repository>>Restore w/o tranlogs' menu item. You will be given a list of backup file names to choose from.

See the [Backup](GemToolsAdmin#Backup.md) section for more information.
### Update GLASS ###
If you haven't already done so, you should make sure that you are using the [latest version of the GemTools client](http://code.google.com/p/glassdb/wiki/GemToolsUpdate) as you always should upgrade your client when you upgrade the server:
  1. click on the 'Update...' button in the GemTools launcher
  1. select the 'Update GLASS' item
  1. select the '[1.0-beta.8 [beta](http://code.google.com/p/glassdb/wiki/GlassReleaseLog#1.0-beta.8)]' item and wait patiently while the upgrade progresses. You can watch progress on the **Transcript**.
  1. make a backup named '1.0-beta.8.dbf' so you won't have to update again.

See the [GemTools Update GLASS](GemToolsUpdate#Update_GLASS.md) section for more info on updating the server.

If you are using Seaside2.8 and GemStone 2.3 ([the appliance](http://gemstonesoup.wordpress.com/2008/10/11/glass-appliance-10beta11-is-available/)) then you should update to [GemTools 1.0-beta.8.5](http://code.google.com/p/glassdb/wiki/GemToolsReleaseLog?ts=1316214614&updated=GemToolsReleaseLog#1.0-beta.8.5) and [GLASS 1.0-beta.8.7](http://code.google.com/p/glassdb/wiki/GlassReleaseLog?ts=1316213963&updated=GlassReleaseLog#1.0-beta.8.7) for best results.
### Load optional projects ###
If you are using [GLASS 1.0-beta.8.4](http://code.google.com/p/glassdb/wiki/GlassReleaseLog#1.0-beta.8.4) see [Seaside 2.8 for 1.0-beta.8.4 options](Seaside28_10beta84.md).

Once you've updated the base system, you may want to do a "full load" of the packages that were loaded by GLASS.230-dkh.231. The following expressions can be evaluated in a GemStone workspace:
```
MCPlatformSupport commitOnAlmostOutOfMemoryDuring: [
  [ 
        ConfigurationOfMetacello project updateProject.
        ConfigurationOfMetacello loadLatestVersion.
	#( ConfigurationOfGsSOAP ConfigurationOfSeaside28 
		ConfigurationOfSeaside28Examples ConfigurationOfGsSeasideTesting28 
		ConfigurationOfMagritte ConfigurationOfGsScaffolding ConfigurationOfPier 
		ConfigurationOfPierAddOns) do: [:configName |
			Smalltalk at: configName ifPresent: [:config | config project updateProject ]].
       Gofer project load: 'GsSOAP' version: '0.233'.
        
        Gofer project load: 'Seaside28' version: '2.8.5'.
        Gofer project load: 'Seaside28Examples' version: '2.8'.
        Gofer project load: 'GsSeasideTesting28' version: '1.0'.
        Gofer project load: 'Magritte' version: '1.2.1.5'.
        Gofer project load: 'GsScaffolding' version: '1.0'.
        Gofer project load: 'Pier' version: '1.2.1.6'.
        Gofer project load: 'GsSeasideTesting28' version: '1.0' group: #( 'PierTesting' ).
        Gofer project load: 'PierAddOns' version: '1.0.5'.
  ]
                on: Warning
                do: [:ex | ex resume ]].
```
If you want a subset of the "full load", then you can edit the above expression to load only the parts that you are interested in.

See the [Seaside 3.0 Load Options](Seaside30LoadOptions.md) page.