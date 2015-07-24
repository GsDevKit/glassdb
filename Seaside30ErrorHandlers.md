There are three error handlers that you should be using with GLASS:
  1. [WAWalkbackErrorHandler](Seaside30ErrorHandlers#WAWalkbackErrorHandler.md)
  1. [WARemoteDebuggingWalkbackErrorHandler](Seaside30ErrorHandlers#WARemoteDebuggingWalkbackErrorHandler.md)
  1. [WAGemStoneProductionErrorHandler](Seaside30ErrorHandlers#WAGemStoneProductionErrorHandler.md)

# WAWalkbackErrorHandler #
The WAWalkbackErrorHandler brings up a Seaside Walkback page that looks like the following:

<img src='http://gemstonesoup.files.wordpress.com/2011/12/wawalkback.png' width='285' height='300'>

If you click on the <b>Debug</b> link, a <i>hard break</i> will be triggered.<br>
<br>
If the Seaside server was launched from a GemTools image when the <i>hard break</i> is triggered, then a debugger window will open.<br>
<br>
If the Seaside server was run from a topaz session, then the topaz process will exit with an error. You should use the <a href='Seaside30ErrorHandlers#WAGemStoneProductionErrorHandler.md'>WAGemStoneProductionErrorHandler</a> instead.<br>
<h1>WARemoteDebuggingWalkbackErrorHandler</h1>
The WARemoteDebuggingWalkbackErrorHandler brings up a Seaside Walkback page that looks like the following:<br>
<br>
<img src='http://gemstonesoup.files.wordpress.com/2011/12/walkback.png' width='285' height='300'>

If you click on the <b>Debug</b> link, a continuation is snapped off and added to the ObjectLog. You can bring the debugger up on a continuation in the ObjectLog by using the <a href='http://code.google.com/p/glassdb/wiki/GemToolsDebug'>Debug menu</a> in GemTools.<br>
<br>
Use WARemoteDebuggingWalkbackErrorHandler when you are doing development and have launched the Seaside gems in separate topaz processes.<br>
<br>
<h1>WAGemStoneProductionErrorHandler</h1>
When an exception is hit while using the WAGemStoneProductionErrorHandler a page that looks like the following is displayed:<br>
<br>
<img src='http://gemstonesoup.files.wordpress.com/2011/12/productionwarning.png' width='300' height='46'>

A continuation is automatically added to the ObjectLog and like the <a href='Seaside30ErrorHandlers#WARemoteDebuggingWalkbackErrorHandler.md'>WARemoteDebuggingWalkbackErrorHandler</a>, the continuation can be debugged in GemTools.<br>
<br>
The WAGemStoneProductionErrorHandler is intended to be used in production, when you don't want your uses to be confronted with a Smalltalk walkback window.<br>
<br>
The page that is displayed by WAGemStoneProductionErrorHandler can be customized.