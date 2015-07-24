![http://gemstonesoup.files.wordpress.com/2010/05/menubar_debug.png](http://gemstonesoup.files.wordpress.com/2010/05/menubar_debug.png)

The **Debug… Menu** allows you to select a continuation to debug. see [Remote Seaside Debugging with Persistent Continuations](GemToolsRemoteDebugging.md) for information on initiating a Remote Debugging sequence.

In addition to the two commands [Remove Continuations from Object Log](GemToolsDebug#Remove_Continuations_from_Object_Log.md) and [Clear Object Log](GemToolsDebug#Clear_Object_Log.md), The **Debug… Menu** lists the continuations that are present in the Object Log. When you select a particular continuation, a [Remote Debugger](GemToolsDebug#Remote_Debugger.md) is brought up on the continuation. For a continuation with a leading ‘^’ , you may use the proceed command to resume the HTTP request that initiated the continuation (you also have to press on the Proceed link on the original page). The newest continuations are listed last. Continuations stay in the Object Log until deleted via the web interface or via one of the following commands.

### Remove Continuations from Object Log ###
This command removes all of the continuations from the Object Log, while leaving all of the other object log entries alone.
### Clear Object Log ###
This command remove all of the log entries from the Object Log.
### Remote Debugger ###
![http://gemstonesoup.files.wordpress.com/2010/05/debugger.png](http://gemstonesoup.files.wordpress.com/2010/05/debugger.png)