Seaside3.0 is supported on GemStone/S 64 2.4.4.1 and older.

To load the full Seaside3.0 release including development tools:
```
MCPlatformSupport commitOnAlmostOutOfMemoryDuring: [
  [ 
	ConfigurationOfMetacello project updateProject.
	ConfigurationOfMetacello loadLatestVersion.
	Gofer project load: 'Seaside30'.
  ]
		on: Warning
		do: [:ex | ex resume ]].
```

To load the minimal Pier2 installation using the FastCGI adaptor:
```

MCPlatformSupport commitOnAlmostOutOfMemoryDuring: [[ 
		ConfigurationOfMetacello project updateProject.
		ConfigurationOfMetacello loadLatestVersion.
		Gofer project load: 'PierAddOns2'.
		Gofer project 
			load: 'Seaside30' 
			group: #( 'Seaside-Adaptors-FastCGI').
	]
		on: Warning
		do: [:ex | 
			Transcript cr; show: ex description.
			ex resume ]].
```