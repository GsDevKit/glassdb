The GemTools Launcher is the main window for the new GemTools Client. From this window, you can manage multiple GemStone/S sessions against multiple stones. The Launcher gives you a view of all of your sessions. When a session is selected, the [annotation pane](GemToolsAnnotationPane.md) provides an overview of important session information, the [menu bar](GemToolsMenuBar.md) provides easy access to commands and development tools, and the [text pane](GemToolsWorkspace.md) provides access to session workspaces.

To open the GemTools Launcher window, evaluate the following in your Smalltalk client workspace:
```
OGLauncher open
```

![http://gemstonesoup.files.wordpress.com/2010/05/emptylauncher.png](http://gemstonesoup.files.wordpress.com/2010/05/emptylauncher.png)

The default session (Glass) is an [Appliance template](GemToolsSessionMenu#Appliance_template.md), which is suitable for use on a GLASS appliance or any installation where the GemTools Client and stone are running on the same machine. Edit the template to reflect the name of your machine and the name of your stone:
```
OGApplianceSessionDescription new
	name: 'Glass';
	stoneHost: 'glass';
	stoneName: 'seaside';
	yourself.
```
See the [Session Menu](GemToolsSessionMenu.md) section for more details on working with sessions.

Press the [Login button](GemToolsSessionMenu#Login.md) to connect a session to your server.

![http://gemstonesoup.files.wordpress.com/2010/04/activelauncher2.png](http://gemstonesoup.files.wordpress.com/2010/04/activelauncher2.png)

GemTools windows opened from the GemTools Launcher button bar are associated with the selected session. GemTools windows opened by executing commands within the context of another GemTools window are associated with the originating window’s session.

You may login to more than one session at any one time. The **G/S`[`<session name>:<session number>`]`** in the title bar of a GemTools window indicates which session is associated with the window. Pressing the [Logout](GemToolsLogout.md) button or selecting the [Logout](GemToolsLogout.md) menu item terminates the selected session and closes all of the GemTools windows associated with the session.

When you close the GemTools Launcher window, the GemTools windows associated with all of the logged in sessions are automatically closed.

If you save your Smalltalk image, while sessions are logged in, none of the existing sessions nor their associated GemTools windows will be affected. However, when the image is restarted all session related GemTools windows will be closed and the sessions will be reset to a logged out state.