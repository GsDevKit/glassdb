### baseline 0.239-baseline ###
```
baseline02390: spec 
	<version: '0.239-baseline'>
	
	spec for: #common do: [
		spec blessing: #baseline.
		spec repository: 'http://seaside.gemstone.com/ss/monticello' ].
	spec for: #gemstone do: [
		spec
			package: 'Core' with: [ spec preLoadDoIt: #preLoad02322.];
			package: 'Base-Bootstrap' with: [ spec requires: #('Core') ];
			package: 'Bootstrap' with: [ spec requires: #('Base-Bootstrap') ];
			package: 'GemStone-Indexing-Extensions' with: [
				spec 
					requires: #('Bootstrap');
					repository: 'http://seaside.gemstone.com/ss/QueryExtensions' ];
			package: 'GsRandom' with: [ spec requires: #('Base-Bootstrap') ];
			package: 'Sport' with: [ 
				spec 
				requires: #('GsRandom' 'Bootstrap');
					repository: 'http://seaside.gemstone.com/ss/hyper' ];
			package: 'Squeak' with: [ 
				spec 
					requires: #('Sport');
					postLoadDoIt: #postLoad233.];
			package: 'VB-Regex' with: [ 
				spec 
					requires: #('Core');
					repository: 'http://seaside.gemstone.com/ss/VBRegex' ];
			yourself].
	spec for: #'gs2.x' do: [
		spec package: 'GemStone-Exceptions' with: [ spec requires: #('Bootstrap' 'Sport') ]].
	spec for: #'gs2.3.x' do: [
		spec package: 'GemStone-23x-Exceptions' with: [ spec requires: #('GemStone-Exceptions') ]].
	spec for: #'gs3.x' do: [ ].
```
### version 0.239 ###
```
version02390: spec
	<version: '0.239' imports: #('0.239-baseline' )>

	spec for: #'common' do: [
		spec blessing: #'release'.
		spec description: '
- add Behavior>>storeOn: to support Magritte 1.2.1 [Squeak]
- Tirade support from Ryan Simmons [Squeak]
- Pier-Book support [Squeak]
- 2.3.x support [GemStone-23x-Exceptions]
- TranscriptProxy class>>tab [Bootstrap]
- Gofer Project Loader support [Bootstrap, Squeak]
- bootstrapping fixes and support for Metacello 1.0-beta.26.1 [Core]
- tweak SequenceableCollection>>detectMax: [Squeak]
'.
		spec author: 'DaleHenrichs'.
		spec timestamp: '5/26/2010 16:50'.
].
	spec for: #'gemstone' do: [
		spec 
			package: 'GemStone-Indexing-Extensions' with: 'GemStone-Indexing-Extensions-dkh.3';
			package: 'GsRandom' with: 'GsRandom-obi.7';
			package: 'VB-Regex' with: 'VB-Regex-STA.19'.].
	spec for: #'gs2.x' do: [
		spec 
			package: 'Core' with: 'Core-DaleHenrichs.31';
			package: 'Base-Bootstrap' with: 'Base-Bootstrap-dkh.16';
			package: 'Bootstrap' with: 'Bootstrap-DaleHenrichs.179';
			package: 'GemStone-Exceptions' with: 'GemStone-Exceptions-Dalehenrichs.35';
			package: 'Sport' with: 'Sport3.010-dkh.20';
			package: 'Squeak' with: 'Squeak-DaleHenrichs.225'.].
	spec for: #'gs2.3.x' do: [
		spec package: 'GemStone-23x-Exceptions' with: 'GemStone-23x-Exceptions-DaleHenrichs.1'.].
	spec for: #'gs3.x' do: [
		spec 
			package: 'Core' with: 'Core.v3-DaleHenrichs.30';
			package: 'Base-Bootstrap' with: 'Base-Bootstrap.v3-dkh.16';
			package: 'Bootstrap' with: 'Bootstrap.v3-DaleHenrichs.178';
			package: 'Sport' with: 'Sport3.010.v3-DaleHenrichs.21';
			package: 'Squeak' with: 'Squeak.v3-DaleHenrichs.220'.].
```