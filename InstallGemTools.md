## Pharo ##
Executing the following statements in a [Pharo](http://www.pharo-project.org/home) workspace installs the latest version of GemTools and opens the [GemTools Help Browser](GemToolsHelp.md). The [GemTools Help Browser](GemToolsHelp.md) provides detailed instructions for finishing the installation of GemTools:
```
  Gofer new
    squeaksource: 'MetacelloRepository';
    package: 'ConfigurationOfGemTools';
    load.
  (Smalltalk at: #ConfigurationOfGemTools) 
	perform: #loadLatestVersion.
  (Smalltalk at: #GemToolsHelpBrowser) open. 
```
## Squeak ##
Executing the following statements in a [Squeak](http://www.squeak.org/) workspace installs the latest version of GemTools and opens the [GemTools Help Browser](GemToolsHelp.md). The [GemTools Help Browser](GemToolsHelp.md) provides detailed instructions for finishing the installation of GemTools:
```
  Installer squeaksource
    project: 'MetacelloRepository';
    install: 'ConfigurationOfGemTools'. 
  (Smalltalk at: #ConfigurationOfGemTools) 
	perform: #loadLatestVersion.
  (Smalltalk at: #GemToolsHelpBrowser) open. "as of GemTools 1.0-beta.8, Help Browser on Squeak"
```