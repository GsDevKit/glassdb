
```
MCPlatformSupport commitOnAlmostOutOfMemoryDuring: [[
	ConfigurationOfMetacello project updateProject.
	ConfigurationOfMetacello loadLatestVersion.
	Gofer project load: 'GsMisc' version: '0.236'.
	Gofer project load: 'GsSOAP' version: '0.232'.
	
	Gofer project load: 'Seaside28' version: '2.8.4.7'.
	Gofer project load: 'Seaside28Examples' version: '2.8'.
	Gofer project load: 'GsSeasideTesting28' version: '1.0'.
	Gofer project load: 'GsSqueakSource' version: '2.0-alpha.3'.
	Gofer project load: 'Magritte' version: '1.2.1.4.1'.
	Gofer project load: 'GsScaffolding' version: '1.0'.
	Gofer project load: 'Pier' version: '1.2.1.4'.
	Gofer project load: 'GsSeasideTesting28' version: '1.0' group: #( 'PierTesting' ).
	Gofer project load: 'PierAddOns' version: '1.0.2'.
  ]
		on: Warning
		do: [:ex | ex resume ]].
```