![http://gemstonesoup.files.wordpress.com/2010/05/sessionmenu.png](http://gemstonesoup.files.wordpress.com/2010/05/sessionmenu.png)

### Copy Session... ###
The **Copy session** command copies the selected session and creates a new session whose name has ‘ copy’ appended.

If you copy a logged in session, only the [session description](GemToolsSessionMenu#New_Session.md) information is copied (i.e., the new session is not in a logged in state).
### Delete Session ###
The **Delete session** command removes the selected session from the list.

The collection of sessions is stored in the Sessions class variable of the client class OGLauncherNode.

A logged in session may not be deleted.
### Edit Session ###
The **Edit session** command gives you an opportunity to change the values of fields in the [session description](GemToolsSessionMenu#New_Session.md). You may also change the class of the [session description](GemToolsSessionMenu#New_Session.md) (OGApplianceSessionDescription, OGStandardSessionDescription, or OGCustomSessionDescription) to expose more or fewer fields.

When you press Okay, the expression is evaluated and the resulting SessionDescription is associated with the selected session.

A logged in session may not be edited.
### New Session ###
When you create a **New session**, you are given a choice of session templates: [Appliance](GemToolsSessionMenu#Appliance_template.md), [Standard](GemToolsSessionMenu#Standard_template.md) and [Custom](GemToolsSessionMenu#Custom_template.md).

#### Appliance template ####
The **Appliance template** is suitable for logging into a GLASS appliance or an installation where your GemTools Client and the stone are running on the same machine:
```
OGApplianceSessionDescription new
	name: 'Glass';
	stoneHost: 'glass';
	stoneName: 'seaside';
	yourself.
```
#### Standard template ####
If you are logging into a stone from a remote GemTools Client or have  started a non-standard netldi, or have changed the password for the DataCurator user, then the **Standard template** is suitable:
```
OGStandardSessionDescription new
	name: 'Standard';
	stoneHost: 'glass';
	stoneName: 'seaside';
	gemHost: 'glass';
	netLDI: '50377';
	userId: 'DataCurator';
	password: 'swordfish';
	backupDirectory: '';
	yourself.
```
#### Custom template ####
The **Custom template** provides access to some of the more esoteric login parameters:
```
OGCustomSessionDescription new
	name: 'Standard';
	stoneHost: 'glass';
	stoneName: 'seaside';
	gemHost: 'glass';
	netLDI: '50377';
	gemTask: 'gemnetobject';
	userId: 'DataCurator';
	password: 'swordfish';
	osUserId: '';
	osPassword: '';
	backupDirectory: '';
	dataDirectory: '';
	yourself.
```
### Login ###
When the **Login** command is executed, a new gem is launched against the named stone using the netldi of the given name (or port number).

When the gem is started, it creates a log file in the home directory (typically) of the user that owns the gem process (in the appliance that would be /home/glass). If the gem process ever exits unexpectedly, you can check in the log file for error messages.