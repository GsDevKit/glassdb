For Squeak vms up to version 3.11-3 (see 'http://lists.squeakfoundation.org/pipermail/vm-dev/2009-September/003206.html'), the GCI library file must be copied into the directory containing the image and changes files that contains your GemTools install. Exupery vms (0.15.2f) also follow this convention.

For a native Linux stone:
```
	cp $GEMSTONE/lib32/libgcirpc.so \
		<image and changes directory>/gciForLinux.so
```

For GemStone 2.3.x copy the files from the GemTools-1.0-beta.8-231x one-click:
```
	cp  GemTools-1.0-beta.8-231x.app/Contents/Resources/gciForLinux.so \
		<image and changes directory>/gciForLinux.so
```
For Gemstone 2.4.4.1 copy the files from the GemTools-1.0-beta.8-244x one-click
```
	cp  GemTools-1.0-beta.8-244x.app/Contents/Resources/gciForLinux.so \
		<image and changes directory>/gciForLinux.so
```

If you are using an appliance, copy the GCI library from the appliance installation:
```
	scp glass@<APPLIANCE IPAddress>:/opt/gemstone/product/lib32/libgcirpc.so \
		<image and changes directory>/gciForLinux.so
```