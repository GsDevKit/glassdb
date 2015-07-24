### baseline 0.237-baseline ###
```
baseline0237: spec 
	<version: '0.237-baseline'>
	
	spec for: #common do: [
		spec blessing: #baseline.
		spec repository: 'http://seaside.gemstone.com/ss/monticello'.].
	spec for: #gemstone do: [
		spec 
			package: 'Change-Notification' with: [ spec requires: #('Monticello') ];
			package: 'PackageInfo-Base' with: [ spec requires: #('Core') ];
			package: 'Monticello' with: [ spec requires: #('PackageInfo-Base') ];
			yourself.
		spec
			project: 'Core' with: [
				spec
					className: 'ConfigurationOfGsCore';
					file: 'ConfigurationOfGsCore';
					repository: 'http://seaside.gemstone.com/ss/MetacelloRepository' ];
			yourself].
```
### version 0.237 ###
```
version02370: spec
	<version: '0.237' imports: #('0.237-baseline' )>

	spec for: #'common' do: [
		spec blessing: #'release'.
		spec description: '- adjust the direction of comparison (again) [Monticello]
  - button label with (image>) should be used when image is parent of selected mcz file
  - button label with (image<) should be used when image is child of selected mcz
- improve MCPackageLoader>>analyze algorithm for eliminated removals that have a corresponding add when doing a multy package load
'.
		spec author: 'DaleHenrichs'.
		spec timestamp: '5/26/2010 16:49'.
].
	spec for: #'gemstone' do: [
		spec project: 'Core' with: '0.238'.
		spec package: 'PackageInfo-Base' with: 'PackageInfo-Base.g-dkh.30'.].
	spec for: #'gs2.x' do: [
		spec 
			package: 'Monticello' with: 'Monticello.g-DaleHenrichs.405';
			package: 'Change-Notification' with: 'Change-Notification-dkh.3'.].
	spec for: #'gs3.x' do: [
		spec 
			package: 'Monticello' with: 'Monticello.v3-DaleHenrichs.403';
			package: 'Change-Notification' with: 'Change-Notification.v3-DaleHenrichs.4'.].
```