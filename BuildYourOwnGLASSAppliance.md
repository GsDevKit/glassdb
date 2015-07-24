So you want to build you own GLASS appliance...

Start from a Debian Squeeze 64 bit net-install. These directions assume you are doing
just a standard system utilities install and will include steps for installing XFCE4 and other tools
which might not be needed depending on what basic Debian configuration you select.
You can download the latest Squeeze net-install iso from http://cdimage.debian.org/cdimage/daily-builds/daily/arch-latest/amd64/iso-cd/debian-testing-amd64-netinst.iso

Be sure as part of the install process to create a user account named 'glass'.
It is strongly recommended that you do not install dash as the default system shell or you
will run in to a world of hurt with bash scripts that use #!/bin/sh.

Be sure to name your machine, 'glass-appliance' if you want to use gemtools w/o providing your own session information.

Once the debian installation is complete, login as root and use apt-get to install some required software:

```
apt-get install sudo openssh-server linux-headers-2.6-amd64 gcc ntp unzip ia32-libs gpm
```

Add the user 'glass' to list of users allowed to sudo:

```
gpasswd -a glass sudo
```

From here on out, if you find using the console to be a pain, you can always ssh into the box and work that way. Just run 'ifconfig' to find out your current ip address.

Logout and login as 'glass' and start installing gemstone 2.4:

```
wget http://dl.dropbox.com/u/3649105/glass-appliance-2010.02.01/installGemstone2.4-Linux.sh
sh ./installGemstone2.4-Linux.sh
```

Make your topaz use easier by setting up a .topazini file. Create /home/glass/.topazini with the following content:
```
set GEMSTONE seaside
set user DataCurator
set password swordfish
login
```
Add the standard gemstone/seaside environment variables to your environment each time you start bash by adding to following to the end of /home/glass/.bashrc:
```
if [ -f /opt/gemstone/product/seaside/defSeaside ]; then
    . /opt/gemstone/product/seaside/defSeaside
fi
```
Logout and log back in so the changes you just made take effect in the bash shell you are using.

Download the following files and copy into /opt/gemstone/product/seaside/bin
```
wget http://dl.dropbox.com/u/3649105/glass-appliance-2010.02.01/seaside/bin/runSeasideGems
wget http://dl.dropbox.com/u/3649105/glass-appliance-2010.02.01/seaside/bin/startMaintenance30 
wget http://dl.dropbox.com/u/3649105/glass-appliance-2010.02.01/seaside/bin/startSeaside30_Adaptor
sudo mv runSeasideGems startMaintenance30 startSeaside30_Adaptor /opt/gemstone/product/seaside/bin/
sudo chmod a+x /opt/gemstone/product/seaside/bin/*
```
If you are using a limited amount of memory ( less than a gig ), download and install this 'mini-system' gemstone
configuration file:

```
wget http://dl.dropbox.com/u/3649105/glass-appliance-2010.02.01/seaside/data/system.conf
sudo mv system.conf /opt/gemstone/product/seaside/data
```
Install the start scripts for gemstone

```
wget http://dl.dropbox.com/u/3649105/glass-appliance-2010.02.01/init.d/gemstone
wget http://dl.dropbox.com/u/3649105/glass-appliance-2010.02.01/init.d/gs_adapter
wget http://dl.dropbox.com/u/3649105/glass-appliance-2010.02.01/init.d/netldi
sudo mv gemstone gs_adapter netldi /etc/init.d/
sudo chmod a+x /etc/init.d/*
sudo update-rc.d -f gemstone start 88 2 3 4 5 . stop 20 0 1 6 .
sudo update-rc.d -f netldi start 88 2 3 4 5 . stop 20 0 1 6 .
sudo update-rc.d -f gs_adapter start 95 2 3 4 5 . stop 13 0 1 6 .
```
Install a clean extent:

```
sudo cp /opt/gemstone/product/bin/extent0.dbf /opt/gemstone/product/seaside/data/
sudo chmod ug+w /opt/gemstone/product/seaside/data/extent0.dbf
```
Set permissions on the gemstone install:

```
sudo chown -R glass:glass /opt/gemstone/
```
Start gemstone
```
sudo /etc/init.d/gemstone start
sudo /etc/init.d/netldi start
```
Bootstrap our new extent. If you hit an out of temporary memory during this process,
you need to start over from 'Install a clean extent' and provide a higher -T value
when starting topaz.

```
wget http://dl.dropbox.com/u/3649105/glass-appliance-2010.02.01/bootstrap_1.0-beta.4.zip
unzip bootstrap_1.0-beta.4.zip
cd bootstrap_1.0-beta.4
topaz -l -T100000
```
In topaz:

```
> login
> input installMaster.topaz
> printit
| repo version |
repo := MCHttpRepository
    location: 'http://seaside.gemstone.com/ss/GLASSproject'
    user: ''
    password: ''.
version := repo loadVersionFromFileNamed: 'ConfigurationOfGLASS-dkh.87.mcz'.
version load.

ConfigurationOfGLASS project updateProject.
(ConfigurationOfGLASS project version: '1.0-beta.6')
    load: 'Seaside3.0 Dev'.   

%

> printit
WAEnvironment reloadApplications.
WABasicDevelopment initialize.
%

> commit
> quit
```


---


For a desktop environment, I prefer xfce4 because it is much lighter weight than KDE or Gnome and results in vms that are much smaller. If you aren't regularly uploading vms to remote locations for others to use, that may not be much of an issue for you, so feel free to use the desktop environment of your choice.

```
sudo apt-get install xfce4 gdm iceweasel xarchiver gtk2-engines-clearlooks xfce4-terminal
```
Reboot to start back into xfce4 where you will see a number of icons etc are missing.
This can easily be corrected by going to the xfce4 menu > settings appearance and selecting 'Tango' under the Icons tab.

Perhaps install some helpful ice weasel web development extensions:

  * screengrab
  * view source chart
  * web developer
  * jsview
  * javascript debugger
  * firebug
  * console
  * autofill forms


---


Install vmware tools...

Go to the virtual machine menu in vmware and select install vmware tools.
This will mount a virtual cd 'VMware tools' on your desktop. Copy the vmware tools
.tar.gz somewhere, unpack and follow the contained instructions. The default options
are all fine when being prompted by the install program.

Configure your xfce4 desktop at your leisure. I start by changing the resolution immediately.


---


Grab a prebuilt and fairly recent gemtools

```
cd ~/Desktop
wget http://dl.dropbox.com/u/3649105/glass-appliance-2010.02.01/gemtools-2.4-mac-linux.zip
unzip gemtools-2.4-mac-linux.zip
```

Note that this gemtools has the shared libraries needed to connect to gemstone from linux and mac machines, but you need to take additional installation steps to get the mac version running ( which is beyond the scope of this document ).


---


reboot and you have seaside 3 running on localhost ports 9001 to 9003.