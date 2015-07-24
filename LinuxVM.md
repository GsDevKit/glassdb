Starting with version 3.11-3 of the Squeak vm(see 'http://lists.squeakfoundation.org/pipermail/vm-dev/2009-September/003206.html'), the GCI library file must be copied into the directory containing the vm (or in one of the directories specified in the -plugins argument).

For a native Linux stone:
```
	cp $GEMSTONE/lib32/libgcirpc.so \
		<vm directory>/so.gciForLinux
```
For GemStone 2.3.x copy the files from the GemTools-1.0-beta.8-231x one-click:
```
	cp  GemTools-1.0-beta.8-231x.app/Contents/Resources/gciForLinux.so \
		<vm directory>/gciForLinux.so
```
For Gemstone 2.4.4.1 copy the files from the GemTools-1.0-beta.8-244x one-click
```
	cp  GemTools-1.0-beta.8-244x.app/Contents/Resources/gciForLinux.so \
		<vm directory>/gciForLinux.so
```

If you are using an appliance, copy the GCI library from the appliance installation:
```
	scp glass@<APPLIANCE IPAddress>:/opt/gemstone/product/lib32/libgcirpc.so \
		<vm directory>/so.gciForLinux
```