Code that executes on the GemStone server may write to the **Transcript** global variable. If a GemTools client is connected to the server and the client Transcript window is open (should be opened before login), then the server-side **Transcript** information will show up in the client Transcript window.

If no GemTools client is connected, then the output is written to the gem log prefixed with the string '--transcript--'.

In either case a debug entry labeled '--transcript--' is added to the ObjectLog.