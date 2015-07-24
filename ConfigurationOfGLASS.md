### baseline 1.0-beta.8-baseline ###
```
baseline10beta08: spec 
	<version: '1.0-beta.8-baseline'>
	
	spec for: #common do: [
		spec blessing: #baseline.].
	spec for: #gemstone do: [
		
		spec 
			project: 'Core' with: [
				spec
					className: 'ConfigurationOfGsCore';
					file: 'ConfigurationOfGsCore';
					repository: 'http://seaside.gemstone.com/ss/MetacelloRepository' ];
			project: 'Metacello' with: [
				spec
					className: 'ConfigurationOfMetacello';
					file: 'ConfigurationOfMetacello';
					repository: 'http://seaside.gemstone.com/ss/metacello' ];
			project: 'Metacello Tools' copyFrom: 'Metacello' with:[
				spec loads: #('OB-Metacello') ];
			project: 'Monticello' with: [
				spec
					className: 'ConfigurationOfGsMonticello';
					file: 'ConfigurationOfGsMonticello';
					repository: 'http://seaside.gemstone.com/ss/MetacelloRepository' ];
			project: 'OB' with: [
				spec
					className: 'ConfigurationOfGsOB';
					file: 'ConfigurationOfGsOB';
					repository: 'http://seaside.gemstone.com/ss/MetacelloRepository' ];
			project: 'Release Support' with: [
				spec
					className: 'ConfigurationOfGsMisc';
					loads: #('GemStone-Release-Support');
					file: 'ConfigurationOfGsMisc';
					repository: 'http://seaside.gemstone.com/ss/MetacelloRepository' ];
			yourself.
		spec
			group: 'default' with: #('Dev' );
			group: 'Minimal' with: #('Core' 'Monticello' 'Metacello' );
			group: 'Dev' with: #('Minimal' 'Release Support' 'OB' 'Metacello Tools' );
			yourself. ].
```
### version 1.0-beta.8 ###
```
version10beta08: spec 
	<version: '1.0-beta.8' imports: #('1.0-beta.8-baseline' )>
	
	spec for: #common do: [
		spec blessing: #beta.
		spec description: '
- Pare the GLASS config down to just represent the basic core of the GLASS system
- includes list of Configurations for projects that are supported in GLASS loaded from http://seaside.gemstone.com/ss/MetacelloRepository where such configurations are stored
- fix Issue 8: http://code.google.com/p/glassdb/issues/detail?id=8 "MNU in pharo tools during Merge"
- fix Issue 15: http://code.google.com/p/glassdb/issues/detail?id=15 "usability issues with Pharo tools"
- 3/19/2010 15:57
  - 5030 run, 5028 passes, 1 expected failures, 1 failures, 0 errors, 0 unexpected passes [w/o Metacello/Gofer]
  - 299 run, 298 passes, 0 expected failures, 1 failures, 0 errors, 0 unexpected passes [Metacello/Gofer]
'.
		spec author: 'DaleHenrichs'.
		spec timestamp: '5/25/2010 11:25' ].
	spec for: #gemstone do: [
		 spec 
			project: 'Core' with: '0.239';
			project: 'Metacello' with: '1.0-beta.26.1';
			project: 'Metacello Tools' with: '1.0-beta.26.1';
			project: 'Monticello' with: '0.237';
			project: 'OB' with: '0.238';
			project: 'Release Support' with: '0.236';
			yourself.].
```