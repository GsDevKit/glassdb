![http://gemstonesoup.files.wordpress.com/2010/05/menubar_transaction.png](http://gemstonesoup.files.wordpress.com/2010/05/menubar_transaction.png)
### Commit ###
The **Commit command** performs a `System commitTransaction`. All changes made since the last transaction boundary (commit or abort) are saved to the repository.

When committing, be aware that the GemTools windows will **not** be updated to reflect any changes that may have been made in other sessions.

If the commit fails, then an [Inspector](GemToolsInspector.md) is brought up on the result of executing [System transactionConflict](GemStoneSystemTransactionConflictsDictionary.md)
### Abort ###
The **Abort command** performs a `System abortTransaction`. All changes that you have made since the last transaction boundary (commit or abort) are lost.

When aborting, be aware the the GemTools windows will **not** be updated to reflect any changes that may have been made in other sessions.
### Auto Abort ###
### Auto Commit ###
By default **Auto Commit** is enabled. With **Auto Commit** enabled, the system performs a commit after every UI action that can change state. In the Browsers that means there are commits after virtually every menu operation. In a workspace or code definition pane, a commit is performed after  expression evaluation (doIt, printIt, inspectIt, etc.) and after an accept command.
### Auto Migrate ###
By default **Auto Migrate** is enabled. With **Auto Migrate** enabled, whenever a class is modified all instances of the class and all instances of all of its subclasses will be automatically migrated to the new class shape. This is normally done every time you change a class in a client Smalltalk, however, in GemStone, when there may be billions of instances in a repository, an allInstances call can be very expensive, so migration has been split out from class modification. Of course in a development environment, **Auto Migrate** is a very convenient/necessary feature.

For the **Auto Migrate** feature to operate **Auto Commit** must be enabled. Therefore if you disable **Auto Commit**, **Auto Migrate** will be disabled.

The status of **Auto Migrate**, **Auto Abort** and **Auto Commit** are displayed in the [annotation pane](GemToolsAnnotationPane.md).