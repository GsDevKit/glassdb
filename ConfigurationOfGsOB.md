### baseline 0.238-baseline ###
```
baseline0238: spec 
	<version: '0.238-baseline'>
	
	spec for: #common do: [
		spec blessing: #baseline.
		spec repository: 'http://seaside.gemstone.com/ss/GemStone'.].
	spec for: #gemstone do: [
		spec 
			project: 'Announcements' with: [
				spec
					className: 'ConfigurationOfGsMisc';
					loads: #('Announcements');
					file: 'ConfigurationOfGsMisc';
					repository: 'http://seaside.gemstone.com/ss/MetacelloRepository' ];
			project: 'Change-Notification' with: [
				spec
					className: 'ConfigurationOfGsMonticello';
					loads: #('Change-Notification');
					file: 'ConfigurationOfGsMonticello';
					repository: 'http://seaside.gemstone.com/ss/MetacelloRepository' ];
			project: 'Core' with: [
				spec
					className: 'ConfigurationOfGsCore';
					file: 'ConfigurationOfGsCore';
					repository: 'http://seaside.gemstone.com/ss/MetacelloRepository' ];
			project: 'Monticello' with: [
				spec
					className: 'ConfigurationOfGsMonticello';
					file: 'ConfigurationOfGsMonticello';
					repository: 'http://seaside.gemstone.com/ss/MetacelloRepository' ];
			yourself.
		spec 
			package: 'OmniBrowser' with: [ spec requires: #('Core') ];
			package: 'OB-GemStone-Platform' with: [ spec requires: #('OmniBrowser') ];
			package: 'OB-Monticello' with: [ spec requires: #('OB-Standard' 'Monticello') ];
			package: 'OB-SUnitIntegration' with: [ spec requires: #('OB-Standard') ];
			package: 'OB-SUnitGUI' with: [ 
				spec 
					requires: #('OB-Standard');
					repository: 'http://seaside.gemstone.com/ss/obsunit' ];
			package: 'OB-Standard' with: [ 
				spec requires: #('OB-GemStone-Platform' 'Change-Notification') ];
			package: 'OB-Tools' with: [ spec requires: #('OB-Standard' 'Announcements') ];
			package: 'JadeServer' with: [ 
				spec 
					requires: #('OB-Tools');
					repository: 'http://seaside.gemstone.com/ss/GLASSClient' ]].
```
### version 0.238 ###
```
version02380: spec
	<version: '0.238' imports: #('0.238-baseline' )>

	spec for: #'common' do: [
		spec blessing: #'release'.
		spec description: '- fixes for Issue 15 (http://code.google.com/p/glassdb/issues/detail?id=15) "usability issues with Pharo tools"
  - fixed highlighting for class definition/creation template (need GemTools 1.0-beta.6) [JadeServer]
  - optional buttons always available for OB-Monticello browsers [OB-Monticello]
  - update shout highlighting algorithm
  - adjust the direction of comparison (again) [OB-Monticello]
    - button label with (>) produces changes that represent what would happen if the working copy were loaded into an image containing the selected or installed version from the repository. 
    - button label with (<) produces changes that represent what would happen if the selected version in the repository were loaded into an image containing the working copy
  - add ''methods containing (case sensitive)'' menu item for defintion pane
- strip #baseline blessings from version list for update server
- fix Issue 8: http://code.google.com/p/glassdb/issues/detail?id=8 "MNU in pharo tools during Merge" [OB-Monticello, OB-Standard]
- workaround for bug39741 on 2.3.x [OmniBrowser]
- tools tips added to Monticello Browser [OB-Monticello]
'.
		spec author: 'DaleHenrichs'.
		spec timestamp: '5/26/2010 16:48'.
].
	spec for: #'gemstone' do: [
		spec 
			project: 'Core' with: '0.238';
			project: 'Announcements' with: '0.235';
			project: 'Change-Notification' with: '0.236';
			project: 'Monticello' with: '0.237'.
		spec 
			package: 'OmniBrowser' with: 'OmniBrowser-DaleHenrichs.445';
			package: 'OB-GemStone-Platform' with: 'OB-GemStone-Platform-dkh.68';
			package: 'OB-Monticello' with: 'OB-Monticello-DaleHenrichs.103';
			package: 'OB-SUnitIntegration' with: 'OB-SUnitIntegration-dkh.10';
			package: 'OB-SUnitGUI' with: 'OB-SUnitGUI.g-dkh.60';
			package: 'JadeServer' with: 'JadeServer-DaleHenrichs.9'.].
	spec for: #'gs2.x' do: [
		spec 
			package: 'OB-Standard' with: 'OB-Standard.g-DaleHenrichs.433';
			package: 'OB-Tools' with: 'OB-Tools.g-DaleHenrichs.128'.].
	spec for: #'gs2.3.x' do: [
		spec package: 'OmniBrowser' with: 'OmniBrowser.v2.3-DaleHenrichs.446'.].
	spec for: #'gs3.x' do: [
		spec 
			package: 'OB-Standard' with: 'OB-Standard.v3-DaleHenrichs.434';
			package: 'OB-Tools' with: 'OB-Tools.v3-DaleHenrichs.133'.].
```