![http://gemstonesoup.files.wordpress.com/2010/05/menubar_admin2.png](http://gemstonesoup.files.wordpress.com/2010/05/menubar_admin2.png)

The **Admin… menu** is primarily intended to provide commands for performing System Administration activities.

### Repository ###
For more details on the GemStone/S backup and restore commands, read Chapter 9 of the System Administration Guide paying special attention to Sections 9.4 and 9.5.

Before putting a system into production, I suggest that you read Chapter 9 of the SAG and experiment with the backup/restore commands using topaz.

#### List backup files ####
![http://gemstonesoup.files.wordpress.com/2010/05/backuplist.png](http://gemstonesoup.files.wordpress.com/2010/05/backuplist.png)
#### Backup ####
The **Backup** command creates a backup file in the backup directory (by default $GEMSTONE/seaside/backups). You can change the location of the backup directory using the [Edit Session](GemToolsSessionMenu#Edit_Session.md) command on the [Session Menu](GemToolsSessionMenu.md).

It is perfectly okay to make a backup of a system that is currently running (i.e., multiple gems running).
#### Restore w/o tranlogs ####
Before the stone starts a restore from backup, all non-essential gems are shut down, including the Seaside Gems and the Maintenance VM. When the restore from backup is complete the Seaside Gems and Maintenance VM need to be restarted manually (see the [Seaside gems](GemToolsAdmin#Seaside_gems.md) command).

The **Restore Backup w/o tranlogs** command restores the repository to exactly the state it was in when the backup was made. This command is intended to to be used to restore a checkpoint of the repository.

Ongoing progress for both commands is written to the [Transcript window](GemToolsTranscript.md).

You are prompted for the name of the backup file from a list like the one below:

![http://gemstonesoup.files.wordpress.com/2010/05/choosebackup.png](http://gemstonesoup.files.wordpress.com/2010/05/choosebackup.png)

#### Restore w/tranlogs ####
Before the stone starts a restore from backup, all non-essential gems are shut down, including the Seaside Gems and the Maintenance VM. When the restore from backup is complete the Seaside Gems and Maintenance VM need to be restarted manually (see the [Seaside gems](GemToolsAdmin#Seaside_gems.md) command).

The **Restore Backup w/tranlogs** command restores the repository and replays all of the subsequent changes using the transaction logs. This command is intended to be used to recover from a system crash, where the extent file was somehow corrupted.

Ongoing progress for both commands is written to the [Transcript window](GemToolsTranscript.md).

You are prompted for the name of the backup file from a list like the one below:

![http://gemstonesoup.files.wordpress.com/2010/05/choosebackup.png](http://gemstonesoup.files.wordpress.com/2010/05/choosebackup.png)
#### Mark For Collection ####
### Seaside gems ###
The  Seaside gems commands executes the `$GEMSTONE/seaside/bin/runSeasideGems` shell script on the server machine. By default this script starts the Maintenance VM and 3 FastCGI Seaside gems listening on ports 9001, 9002, and 9003. The script can be edited to change the number and types of gems that are started.

For Seaside30, the script`$GEMSTONE/seaside/bin/runSeasideGems30` and the number of gems and adaptor used by the script is defined by `WAGemStoneRunSeasideGems default`. See [Configuring the $GEMSTONE/seaside/bin/runSeasideGems30 script](ControllingSeaside30Gems.md) for more information.

If you don’t start a Maintenance VM during development, then you should plan on running a `SystemRepository markForCollection` or the [Mark For Collection](GemToolsAdmin#Mark_For_Collection.md) command periodically to make sure that the persistent objects are garbage collected.

Ongoing progress for these commands is written the client Transcript window.
#### Start ####
Executes `$GEMSTONE/seaside/bin/runSeasideGems start`.
#### Stop ####
Executes `$GEMSTONE/seaside/bin/runSeasideGems stop`.
#### Restart ####
Executes `$GEMSTONE/seaside/bin/runSeasideGems restart`.
### DoIt... ###
The **DoIt** commands includes a collection of scripts that Gerhard Obermann has found useful over the years working with GemStone.You can learn a fair amount about GemStone by taking a look at the information provided by these scripts.
#### Changed Packages And Methods ####
The **Change Packages And Methods** command provides a quick overview of the unsaved changes that you have made to the code.
![http://gemstonesoup.files.wordpress.com/2010/05/changedpnm.png](http://gemstonesoup.files.wordpress.com/2010/05/changedpnm.png)
#### Client Version Report ####
![http://gemstonesoup.files.wordpress.com/2010/05/clientversion.png](http://gemstonesoup.files.wordpress.com/2010/05/clientversion.png)
#### Empty Object Log ####
The **Empty Object Log** command empties the entire ObjectLog (also see the [Remove Continuations from Object Log](GemToolsDebug#Remove_Continuations_from_Object_Log.md) command in the [Debug… menu](GemToolsDebug.md)).
#### File Size Report ####
![http://gemstonesoup.files.wordpress.com/2010/05/filesize.png](http://gemstonesoup.files.wordpress.com/2010/05/filesize.png)
#### Gem Configuration Report ####
![http://gemstonesoup.files.wordpress.com/2010/05/gemconfig.png](http://gemstonesoup.files.wordpress.com/2010/05/gemconfig.png)
#### Show Object Log ####
The **Show Object Log** command provides a workspace with the String version of the Object Log.
![http://gemstonesoup.files.wordpress.com/2010/05/objectlog.png](http://gemstonesoup.files.wordpress.com/2010/05/objectlog.png)
#### Stone Configuration Report ####
![http://gemstonesoup.files.wordpress.com/2010/05/stoneconfig.png](http://gemstonesoup.files.wordpress.com/2010/05/stoneconfig.png)
#### Stone Version Report ####
![http://gemstonesoup.files.wordpress.com/2010/05/stoneversion.png](http://gemstonesoup.files.wordpress.com/2010/05/stoneversion.png)
#### User Sessions Report ####
![http://gemstonesoup.files.wordpress.com/2010/05/usersession.png](http://gemstonesoup.files.wordpress.com/2010/05/usersession.png)
#### Version Report ####
![http://gemstonesoup.files.wordpress.com/2010/05/versionreport.png](http://gemstonesoup.files.wordpress.com/2010/05/versionreport.png)
### Browser Preferences ###
#### Annotation Panes ####
#### Mercury panel ####
#### Optional Buttons ####
#### Enable all ####
#### Disable all ####
### Commit on Almost Out of Memory ###
You can enable/disable Commit on AlmostOutOfMemory by using MCPlatformSupport class>>commitOnAlmostOutOfMemoryDuring:.
### Popup on debug ###
### Send Bug Report ###