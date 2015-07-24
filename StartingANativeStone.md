Assuming that you have installed GemStone in `/opt/gemstone/product`, follow these steps for starting and stopping the stone:

  1. Define $GEMSTONE environment variables ($GEMSTONE/bin and $GEMSTONE/seaside/bin added to your $PATH environment variable):
```
source /opt/gemstone/product/seaside/defSeaside
```
  1. Copy `system.conf` and GLASS `extent0.dbf` files to data directory:
```
cp $GEMSTONE/seaside/system.conf \ 
  $GEMSTONE/seaside/data
chmod +w $GEMSTONE/seaside/data/system.conf
cp $GEMSTONE/bin/extent0.seaside.dbf \
  $GEMSTONE/seaside/data/extent0.dbf
chmod +w $GEMSTONE/seaside/data/extent0.dbf
```
  1. Start `netldi` and `stone` processes:
```
startnet
startGemstone
```
  1. Ensure `stone` process is running:
```
gslist -lcv
```
  1. Stop `stone` process:
```
stopGemstone
```