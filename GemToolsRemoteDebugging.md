Head over to http://glass/seaside/tests/alltests in your browser:

  1. Click on the Error tab
  1. Click on the ‘Raise zero divide’ link
  1. Click on the ‘Remote Debug’ link on the walkback page.
  1. [Follow the instructions on this page](GemToolsDebug.md) for bringing up the debugger in your development image.

**NOTE:** The following features are only available for Seaside28. You can save code in the debugger, set breakpoints and step around. There are a couple of problems with proceed, so unless you’ve set a breakpoint that prevents flying off the end of the stack, you shouldn’t use proceed. By implication there are certain points in a stack that you can’t step over.