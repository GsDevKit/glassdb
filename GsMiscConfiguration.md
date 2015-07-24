GsMisc is a catchall project that manages a number of single package projects. Here’s the list of packages currently available in the GsMisc project (as of [GLASS 1.0-beta.8](http://code.google.com/p/glassdb/wiki/GlassReleaseLog#1.0-beta.8)):

  * MockGemStone
  * SMTPMail
  * Utf8Encoding
  * Announcements
  * XML-Parser
  * SIXX
  * SmaCC
  * System-Digitial-Signatures
  * GemStone-Release-Support
## Loading ##
You _can_ load the entire package using the following expression:

```
  Gofer project load: 'GsMisc'.
```

However, unlike many projects, this project is just a collection of miscellaneous packages so it is more likely that you will be interested in loading one package (mail support):
```
  Gofer project load: 'GsMisc' group: 'SMTPMail'.
```

or a couple of packages (like SIXX and Utf8Encoding):

```
  Gofer project load: 'GsMisc' group: #('SIXX' 'Utf8Encoding').
```
Note that in the case of 'SIXX' which relies on the 'XML-Parser', the dependent packages are automatically loaded for you.