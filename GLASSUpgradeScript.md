If your repository is already at or above GLASS 1.0-beta.8, you can use the following script to programmatically upgrade GLASS:

```
| versionString |
versionString := '1.0-beta.8.7.1'.
MCPlatformSupport
  autoCommit: true;
  autoMigrate: true.
ConfigurationOfMetacello project currentVersion versionNumber < '1.0-beta.31.1' asMetacelloVersionNumber
    ifTrue: [
        (Gofer new)
            gemsource: 'metacello';
            version: 'Gofer-Core.gemstone-dkh.135';
            version: 'Metacello-Base-DaleHenrichs.19';
            version: 'Metacello-Core-dkh.468';
            version: 'Metacello-MC-dkh.531';
            version: 'Metacello-Platform.gemstone-dkh.23';
            load].
MCPlatformSupport commitOnAlmostOutOfMemoryDuring: [[[ 
  ConfigurationOfGLASS project updateProject.
  (ConfigurationOfGLASS project version: versionString) load: #( 'Core' 'Monticello' ).
  (ConfigurationOfGLASS project version: versionString) load.
 ]
    on: (Smalltalk at: #MetacelloSkipDirtyPackageLoad)
    do: [:ex | ex resume: false ]]
        on: Warning
        do: [:ex | 
            Transcript cr; show: ex description.
            ex resume ]].
```
The above sequence ensures that you've got the latest versions of each of the configuration packages already loaded in the image (thus avoiding Metacello [Issue 136](https://code.google.com/p/glassdb/issues/detail?id=136)), before loading the GLASS configuration.