![http://gemstonesoup.files.wordpress.com/2010/05/menubar_update.png](http://gemstonesoup.files.wordpress.com/2010/05/menubar_update.png)

The commands on the **Update… menu** allow you to easily update the software on both the client (Squeak or Pharo) and the server. For a better understanding of the relationship between the client and server software see [this section](GemToolsClientServerDependencies.md).

Both the client and server code is now managed via [Metacello](http://code.google.com/p/metacello/). ConfigurationOfGemTools is used to manage the GemTools software that runs on the client and ConfigurationOfGLASS is used to manage the GLASS software that runs on the server. It is worth taking the [Metacello Tutorial](http://code.google.com/p/metacello/wiki/Tutorial) in order to load and upgrade software in GLASS. Then take a look at [GLASS and Metacello overview](GLASSAndMetacello.md) for specific information about how Metacello is used in GLASS.

When you are ready to update your GemTools Client and GLASS Server, you should always use the Update Client command first. The update for the GemTools Client may contain new code for updating the server as well as bugfixes and new features. After running the Update Client command, you may run the Update GLASS command.

### Update GemTools Launcher ###
To update the GemTools Launcher:
  1. click on the 'Update...' button in the GemTools launcher
  1. select the 'Update GemTools Launcher' menu item
  1. select the latest version in the version list and wait patiently while the upgrade proceeds
  1. save your client image before proceeding.

The **Update GemTools Launcher** command updates the ConfigurationOfGemTools configuration to ensure that all of the latest versions are available.

A list of the versions that are later than current version is displayed from which you may choose a version to be loaded. If there are no more recent release or beta version, you have the option to see ALL versions.

![http://gemstonesoup.files.wordpress.com/2010/05/updateclient.png](http://gemstonesoup.files.wordpress.com/2010/05/updateclient.png)

#### Show All Versions ####

All versions will include development versions of the GemTools project, but I don’t recommend that you load development versions as they **are** under development and are likely to be unstable.

![http://gemstonesoup.files.wordpress.com/2010/05/updateclientall.png](http://gemstonesoup.files.wordpress.com/2010/05/updateclientall.png)

When the load is complete, it is a good idea to save your client image.

#### Full Version Descriptions ####

If you choose the **Full Versions Descriptions** option, the version description field for each of the versions is extracted and presented in a workspace window.

![http://gemstonesoup.files.wordpress.com/2010/05/clientversion1.png](http://gemstonesoup.files.wordpress.com/2010/05/clientversion1.png)

### Update GLASS ###
After you have updated the GemTools Client, you may update the Glass Server with the **Update GLASS** command:

  1. click on the 'Update...' button in the GemTools launcher
  1. select the 'Update GLASS' menu item
  1. select the latest version in the version list and wait patiently while the upgrade proceeds
  1. make a backup so you won't have to update again.

The **Update GLASS** command updates the [ConfigurationOfGLASS](ConfigurationOfGLASS.md) configuration to ensure that all of the latest versions are available.

A list of the versions that are later than current version is displayed from which you may choose a version to be loaded. If there are no more recent release or beta version, you have the option to see ALL versions.

![http://gemstonesoup.files.wordpress.com/2010/05/udateserver.png](http://gemstonesoup.files.wordpress.com/2010/05/udateserver.png)

#### Show All Versions ####

All versions will include development versions of the GLASS project, but I don’t recommend that you load development versions as they **are** under development and are likely to be unstable.

![http://gemstonesoup.files.wordpress.com/2010/05/updateserverall1.png](http://gemstonesoup.files.wordpress.com/2010/05/updateserverall1.png)

Once you’ve selected a version to load, all of the GemTools windows associated with the session are automatically closed and the version is loaded. When the load is complete a commit is performed and the session is logged out and in again. Progress messages are printed to the client Transcript window while the load operation is performed.

It is a good idea to [backup your repository](GemToolsAdmin#Backup.md) right before you perform the Update GLASS command and again immediately after the load is complete. With backups you will always be able to return to a know point.

#### Full Version Descriptions ####

If you choose the **Full Versions Descriptions** option, the version description field for each of the versions is extracted and presented in a workspace window.

![http://gemstonesoup.files.wordpress.com/2010/05/serverversion.png](http://gemstonesoup.files.wordpress.com/2010/05/serverversion.png)