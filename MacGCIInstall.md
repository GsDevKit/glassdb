On the Mac, the GCI library file must be copied into the vm.app/Contents/Resource directory.  The source depends upon whether you are running your stone on a Mac or some other OS:

For a native Mac stone
```
	cp $GEMSTONE/lib32/libgcirpc.so \
		vm.app/Contents/Resource/gciForMacintosh.so
```
For GemStone 2.3.x copy the files from the GemTools-1.0-beta.8-231x one-click:
```
	cp  GemTools-1.0-beta.8-231x/Contents/Resources/gciForMacintosh.so \
		vm.app/Contents/Resource/gciForMacintosh.so
```
For Gemstone 2.4.4.1 copy the files from the GemTools-1.0-beta.8-244x one-click
```
	cp  GemTools-1.0-beta.8-244x/Contents/Resources/gciForMacintosh.so \
		vm.app/Contents/Resource/gciForMacintosh.so
```