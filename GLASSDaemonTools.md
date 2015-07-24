**Note:** A script that automatically performs this setup for either Seaside 2.8 or Seaside 3.0 running on GemStone is at http://github.com/Monty/GemStone_daemontools_setup

# I PRINCIPLES #
## I.1 Intro ##
(If you’re familiar with daemontools, [skip to II Scripts](GLASSDaemonTools#II_SCRIPTS.md))
[Daemontools by D.J.Bernstein](http://cr.yp.to/daemontools.html) is a set of tools for managing services or programs that normally have a non-forking behaviour. The tools then take care of
concerns like logging (given log information is printed to the terminal, by default), restarting of dead processes &c. As per the intention of the author,
the daemontools installation and usage is often dissimilar to normal Unix/Linux or even MacOS[[Note 3](GLASSDaemonTools#Note3.md)].

The daemontools work by the notion of a ‘service’ that, essentially, is a
program in the aforementioned fashion. Each such service has a directory in a
well-known place in the filesystem where a ‘supervisor’ is able to find it.
From this moment on, the daemontools can be used to control the service; i.e.
shutting down, starting or restarting the service. The key point, in fact, is
that the supervisor takes care of restarting the service whenever it dies.
This is my motivation of taking the gems to the daemontools.



## I.2 Installations ##
Following the guides on the [web site](http://cr.yp.to/daemontools.html) of D.J.Bernstein is usually the best idea
to install the daemontools on any Unix/Linux. However, Debian provides some
packages for installation with APT. These packages introduce some differences
to the original installation. Debian specifics are marked **D< >** in the following.



## I.3 Directories ##
As said before, the daemontools, expect services to have a certain directory
in a well-known place. By default, this place would be /service
**D<**/etc/service**>**. Every directory beneath this place is checked regularly by the supervisor
for new services. If the supervisor finds a file called ‘run’ that is executable, this directory is treated as a service. N.B. it seems to be a common pattern to use only symlinks in the supervisors directory in order to maintain a
separate repository of services and/or service templates. **D<**There even is a
default directory, /etc/sv to put the original services in. See [III.5 Helpers](GLASSDaemonTools#III.5_Helpers.md)**>** We will
use this in [II.3.1 New Directory Layout](GLASSDaemonTools#II.3.1_New_Directory_Layout.md).



## I.4 Logging ##
If a service directory contains a directory called ‘log’ that looks like a service directory, this is treated as the services logging service.[[Note 4](GLASSDaemonTools#Note4.md)] Hence,
there has to be a ‘run’ file to make that working. Every output of the ‘main’
service (stdout) is then piped to the logging services input (stdin).


# II SCRIPTS #
## II.1 Patching ##
In order to behave as the daemontools expect, the scripts for the GS/SS gems,
i.e. the maintenance gem and the actual seaside gem, have to be patched, especially for logging handled by the daemontools.[[Note 5](GLASSDaemonTools#Note5.md)] For the seaside gem, I will
only give the patches for the FastCGI version, but the Hyper version should be
similar.


### II.1.1 'nohup' and 'exec' ###
Currently, GS/SS tries to avoid unexpected hangups by using the nohup(1) tool.
However, this conflicts with daemontools which are managing hangups themselves.
As I said above, the daemontools expect a foreground program, thus, the currently used backgrounding  must be removed.

Additionally, daemontools require the supervised service to be a singe pro-
cess. That is, a shell script that has child processes would not work correctly [[Note 6](GLASSDaemonTools#Note6.md)]. Unfortunately, that is exactly how the GS/SS gems work. To overcome
this, we use the exec(1) command which will replace the shell with the started
child.

Now the patching. For the maintenance gem that resides in $GEMSTONE/seaside/
bin/startMaintenance, the line
```
    cat << EOF | nohup $GEMSTONE/bin/topaz -l -T200000 2>&1 > \
    $GEMSTONE_LOGDIR/maintenance_gem.log &
```
should become
```
    exec $GEMSTONE/bin/topaz -l -T200000 2>&1 > \
    $GEMSTONE_LOGDIR/maintenance_gem.log << EOF
```
and for the seaside gem in $GEMSTONE/seaside/bin/seasideGem\_FastCGI, change
```
    cat << EOF | nohup $GEMSTONE/bin/topaz -l -T50000 2>&1 \
    >> $GEMSTONE_LOGDIR/FastCGI_server-${1}.log &
```
for
```
    exec $GEMSTONE/bin/topaz -l -T50000 2>&1 \
    >> $GEMSTONE_LOGDIR/FastCGI_server-${1}.log  << EOF
```
I did not alter the original files but named them differently,
‘maintenanceGem’ and ‘seasideGem\_FastCGI’, respectively; and put them besides
their originals. Note that these new scripts will
  * not go into background when started and
  * replace the shell they are started in
which was exactly the intention.



### II.1.2 Logging ###
To provide the output to the logging service, the output of the gem should be
simply printed and not be redirected to a file. Hence, for the maintenance gem,
change the line from [II.1.1 'nohup' and 'exec'](GLASSDaemonTools#II.1.1_'nohup'_and_'exec'.md)
```
    exec $GEMSTONE/bin/topaz -l -T200000 2>&1 > \
    $GEMSTONE_LOGDIR/maintenance_gem.log << EOF
```
to
```
    exec $GEMSTONE/bin/topaz -l -T200000 2>&1  << EOF
```
and for the seaside gem from
```
    exec $GEMSTONE/bin/topaz -l -T50000 2>&1 \
    >> $GEMSTONE_LOGDIR/FastCGI_server-${1}.log  << EOF
```
to
```
    exec $GEMSTONE/bin/topaz -l -T50000 2>&1 << EOF
```
Thus, all requirements are met.



## II.2 The 'run' Scripts ##
Essentially, all run scripts to follow are a variant of 'run that gem,' more
or less easy to configure. Thus, the simplest seaside gem run script would be

```
source /opt/gemstone/product/seaside/defSeaside
exec $GEMSTONE/seaside/bin/seasideGem_FastCGI 9001
```

However, there is a security problem, as this script is executed as root and,
subsequently, the gem is, too. To overcome this problem, daemontools provide
the setuidgid(8) tool which executes a command under a given user. Hence, the
improved version:

```
source /opt/gemstone/product/seaside/defSeaside
exec setuidgid gemstone $GEMSTONE/seaside/bin/seasideGem_FastCGI 9001
```

Now, let’s put it together: We create the directory
```
    /service/gs_fastcgi         D</etc/service/gs_fastcgi>
```
and put the run script there. Also, we create the directory
```
    /service/gs_maintenance     D</etc/serivce/gs_maintenance>
```
and put the run script there, replacing the actual command from
‘seasideGem\_FastCGI 9001’ to ‘maintenanceGem’. For simple setups, this should
suffice, skip to [III COMMANDS](GLASSDaemonTools#III_COMMANDS.md). For more complex setups, read on.


## II.3 Multiple Seaside Gems ##
When we want to run multiple seaside gems in parallel, it is desirable to not
have to write the run script for every gem and just change the port. When we
decide to change something, we don’t want to touch every run file; this is error prone.



### II.3.1 New Directory Layout ###
> As said in I.3, it might be useful to have a template for various services.
We use the service template directory [[Note 7](GLASSDaemonTools#Note7.md)] and create the service ‘gs\_fastcgi.’
However, unlike the setup in II.2, this service is never actually run. Instead,
it serves as template for out, say three, actual services. For each actual
service, we will have a directory in the service template directory, too. In
accordance with the Debian way, we will create links in the service directory
to enable such service (see III. for a Debian-provided tool assisting this procedure). Hence, when finished, the layout of our service template directory
should be:
```
D<# ls -l /etc/sv >
  # ls -l /service_tmpl
  total 0
  drwxr-xr-x 3 root root 4096  13:52 gs_fastcgi
  drwxr-xr-x 3 root root 4096  14:07 gs_fastcgi-1
  drwxr-xr-x 3 root root 4096  14:13 gs_fastcgi-2
  drwxr-xr-x 3 root root 4096  14:13 gs_fastcgi-3
  drwxr-xr-x 3 root root 4096  14:17 gs_maintainance
```
and of the service directory:
```
D<
  # ls -l /etc/service
  total 0
  lrwxrwxrwx 1 root root 20  14:07 gs_fastcgi-1 -> /etc/sv/gs_fastcgi-1
  lrwxrwxrwx 1 root root 20  14:11 gs_fastcgi-2 -> /etc/sv/gs_fastcgi-2
  lrwxrwxrwx 1 root root 20  14:11 gs_fastcgi-3 -> /etc/sv/gs_fastcgi-3
  lrwxrwxrwx 1 root root 23  14:17 gs_maintainance -> /etc/sv/gs_maintainance
>
  # ls -l /service
  total 0
  lrwxrwxrwx 1 root root 20  14:07 gs_fastcgi-1 -> /service_tmpl/gs_fastcgi-1
  lrwxrwxrwx 1 root root 20  14:11 gs_fastcgi-2 -> /service_tmpl/gs_fastcgi-2
  lrwxrwxrwx 1 root root 20  14:11 gs_fastcgi-3 -> /service_tmpl/gs_fastcgi-3
  lrwxrwxrwx 1 root root 23  14:17 gs_maintainance
    -> /service_tmpl/gs_maintainance
```
Note that the gs\_fastcgi service itself is not linked into the service directory.



### II.3.2 Common and Local Configuration ###
I decided to differentiate between a common configuration shared between all
services (such as the user that should run the gem) and ‘local’ configuration
that is unique to a certain service (such as the gem’s port). To enable this,
we will use a small shell trick. As the actual run script will reside in
D</etc/sv/gs\_fastcgi> /service\_tmpl/gs\_fastcgi, we will put the common configuration there. The local configuration will reside in the actual service’s template directory. This looks like this:
```
D<
  # ls -l /etc/sv/*fastcgi*/config*
  -rw-r--r-- 1 root root 32  14:07 /etc/sv/gs_fastcgi-1/config.local
  -rw-r--r-- 1 root root 32  14:10 /etc/sv/gs_fastcgi-2/config.local
  -rw-r--r-- 1 root root 32  14:10 /etc/sv/gs_fastcgi-3/config.local
  -rw-r--r-- 1 root root 86  13:42 /etc/sv/gs_fastcgi/config
 >
  # ls -l /service_tmpl/*fastcgi*/config*
  -rw-r--r-- 1 root root 32  14:07 /service_tmpl/gs_fastcgi-1/config.local
  -rw-r--r-- 1 root root 32  14:10 /service_tmpl/gs_fastcgi-2/config.local
  -rw-r--r-- 1 root root 32  14:10 /service_tmpl/gs_fastcgi-3/config.local
  -rw-r--r-- 1 root root 86  13:42 /service_tmpl/gs_fastcgi/config
```
What should go into the configuration

```
[config] As stated above, the common configuration can include the user that
    should run the gems. Also, I found it valuable to put the standard GS/SS
    stanza there that sets up the GS/SS shell environment:

    #!/bin/sh

    source /opt/gemstone/product/seaside/defSeaside

    export RUNASUSER=gemstone

```
```
[config.local] The only thing that is needed locally by each individual gem is
    its port, hence the local configuration becomes (for gs_fastcgi-1)

    #!/bin/sh

    export GEM_PORT=9001

    (with other port numbers for the other services)
```


### II.3.3 Adapting the 'run' Script ###
In order to make the run script reusable, we introduced configurations. To actually use these configuration the run script must be adapted:

```
#!/bin/sh

source /opt/gemstone/product/seaside/defSeaside
exec setuidgid $RUNASUSER $GEMSTONE/seaside/bin/seasideGem_FastCGI $GEM_PORT

```

However, to access the configuration variables, we have to include the config-
gurations. Not the facts that
  * the common configuration is in the directory the run script is actually residing in;
  * the local configuration in in the directory the run script is linked to.

Knowing this, a small shell trick that provides both directories mentioned
enables us to include both configurations. E.g. for the gs\_fastcgi-1 service
in the following script (the run script I currently use) ‘scriptpath’ would be
/service\_tmpl/gs\_fastcgi-1 D</etc/sv/gs\_fastcgi-1> whereas ‘orig\_scriptpath’
would be /service\_tmpl/gs\_fastcgi D</etc/sv/gs\_fastcgi>.

```
#!/bin/sh

old_pwd=$(pwd)
cd $(dirname $0)
scriptpath=$(pwd)
cd $old_pwd

orig_scriptpath=$(dirname "$(readlink -f $0)")

source $orig_scriptpath/config

[ -r $scriptpath/config.local ] && source $scriptpath/config.local


exec setuidgid $RUNASUSER $GEMSTONE/seaside/bin/seasideGem_FastCGI $GEM_PORT

```

This way, both the common and the local configurations are included. It is
possible to use this script for the maintenance gem, too (adapted as descibed
above)



## II.4 The Logging Scripts ##
For all services, the logging ‘run’ script simply is
```
#!/bin/sh
exec multilog t ./main

```

When this ‘run’ script is put into the log directory of a service and made executable, the daemontools automatically will start use this logging facility.
Note that the ‘multilog’ command provided by daemontools uses timestamps with
a special format (cf. tai64n(8)). To read multilog output more human-readable
refer to the ml**tools (cf. III.5).**

Note that if we are using the Multiple Gems layout from II.3, there is
no need to copy that script over and over. Simply put it into D</etc/sv/
gs\_fastcgi/log/run> /service\_tmpl/gs\_fastcgi/log/run and link to it from the
different actual service:
```
D<
  # ls -l /etc/sv/*/log/run
  lrwxrwxrwx 1 root root 26  13:55 /etc/sv/gs_fastcgi-1/log/run
    -> /etc/sv/gs_fastcgi/log/run
  lrwxrwxrwx 1 root root 26  13:55 /etc/sv/gs_fastcgi-2/log/run
    -> /etc/sv/gs_fastcgi/log/run
  lrwxrwxrwx 1 root root 26  13:55 /etc/sv/gs_fastcgi-3/log/run
    -> /etc/sv/gs_fastcgi/log/run
  -rwxr-xr-x 1 root root 33  14:02 /etc/sv/gs_fastcgi/log/run
  lrwxrwxrwx 1 root root 26  13:55 /etc/sv/gs_maintainance/log/run
    -> /etc/sv/gs_fastcgi/log/run
>
  # ls -l /etc/sv/*/log/run
  lrwxrwxrwx 1 root root 26  13:55 /etc/sv/gs_fastcgi-1/log/run
    -> /etc/sv/gs_fastcgi/log/run
  lrwxrwxrwx 1 root root 26  13:55 /etc/sv/gs_fastcgi-2/log/run
    -> /etc/sv/gs_fastcgi/log/run
  lrwxrwxrwx 1 root root 26  13:55 /etc/sv/gs_fastcgi-3/log/run
    -> /etc/sv/gs_fastcgi/log/run
  -rwxr-xr-x 1 root root 33  14:02 /etc/sv/gs_fastcgi/log/run
  lrwxrwxrwx 1 root root 26  13:55 /etc/sv/gs_maintainance/log/run
    -> /etc/sv/gs_fastcgi/log/run
```



# III COMMANDS #
## III.0 ##
Most of the commands explained here use the daemontools svc tool. This tool
takes an _directory_ as argument. Later, some Debian specific tools will be
mentioned, e.g. mlcat or mltail. These tools take a _service name_ as argument.
If your current working directory is /service D</etc/service> this makes no
difference. There are more tools in daemontools; see [2](Note2.md) or [8](Note8.md)



## III.1 Starting ##
Whenever you put a service into the service directory, whether by creating a
directory or linking into it, the supervisor will try to start it by running
its 'run' script. Hence, using the previously described method will already
have the service(s) started.

Should a service have been stopped in any way, use
```
  # svc -u /service/gs_yourservice
D<# svc -u /etc/service/gs_yourservice>
```
to start it.



## III.2 Restarting ##
Daemontools primary aim is to keep its services running. Thus, simply killing
your service by using
```
  # kill PIDOFYOURSERVICE
  # killall NAMEOFYOURSERVICE
```
would not stop your service completely but rather kill the application and
have it restarted by the supervisor. The svc tool can be used to do this, too:
```
  # svc -t /service/gs_yourservice
D<# svc -t /etc/service/gs_yourservice>
```
to terminate (signal(7) number 15, similar to kill),
```
  # svc -k /service/gs_yourservice
D<# svc -k /etc/service/gs_yourservice>
```
to kill (signal(7) number 9, similar to kill -9), or
```
  # svc -h /service/gs_yourservice
D<# svc -h /etc/service/gs_yourservice>
```
to send hangup (signal(7) number 1) to the service.



## III.3 Stopping ##
As mentioned above, terminating/killing a service does not keep it shut down.
To keep your service shut down, use
```
  # svc -d /service/gs_yourservice
D<# svc -d /etc/service/gs_yourservice>
```
When you issued this command, you might want to use svc -u as in III.1 to
bring it up again.



## III.4 Status ##
In order to see whether the services are running you might issue
```
  # svstat /service/gs_yourservice
D<# svstat /etc/service/gs_yourservice>
```
and it will print the status of the service. This is really useful if you do
this in the service directory /service D</etc/service>:
```
  # svstat *
```
as this provides an overview of all services. A healthy system might look like
```
  # svstat *
  gs_fastcgi-1: up (pid 8945) 1094 seconds
  gs_fastcgi-2: up (pid 31925) 14185 seconds
  gs_fastcgi-3: up (pid 31929) 14185 seconds
  gs_maintainance: up (pid 31909) 14199 seconds
```
but with several services not running, this might look like
```
  # svstat *
  gs_fastcgi-1: up (pid 8945) 1385 seconds
  gs_fastcgi-2: down 6 seconds, normally up
  gs_fastcgi-3: up (pid 31929) 14476 seconds
  gs_maintainance: down 3 seconds, normally up
```


## III.5 Helpers ##
When using the Debian daemontools-run package, there is an additional command
that should help you enabling or disabling services from your service template
directory. That way, we might have enabled the maintenance service by issuing
```
  # update-service --add /etc/sv/gs_maintenance
```
(where we could have specified an optional name for the link in the
/etc/service directory). Similar, the following command will remove the enabled service
```
  # update-service --remove /etc/sv/gs_maintenance
```
We could also list all services currently enabled:
```
  # update-service --list
  gs_fastcgi-1
  gs_fastcgi-2
  gs_fastcgi-3
  gs_maintainance
```
There is a Debian package called svtools that provides various tools for
  * managing/viewing multilog files (mlcat, mltail, mltac…)
  * creating services and init.d wrappers (svsetup, svinid-create)
  * various information (svdir, svinfo)

This package is also responsible for the creation of the /etc/sv directory.






# IV IMPROVEMENTS #
## IV.1 Restrictions ##
Now for the restriction mentioned initially. The runSeasideGems command no
longer works. It is responsible for starting/stopping/restarting the seaside
gems. Also, it is used from within the GemTools to perform these very tasks.
However, the techniques of the script interfere with the ones of daemontools.
Thus, I put an
```
    exit 0;
```
near the top of $GEMSTONE/seaside/bin/runSeasideGems. Unfortunately, it is not
possible to start/stop/restart the gems from within the GemTools with this
patch.

Another possibility is to change the script to use the svc tool. Thus, it
would be possible to use the GemTools for the start/stop/restarting, again.

## IV.2 Daemontools Everywhere ##
It is possible to use the daemontools to control the stone itself rather than
only the gems. However, you should be aware, that you have to
  * deal with the existing init.d scripts,
  * take care of the start/stop order of the netldi and the Stone.

#### Notes ####
##### Note3 #####
I will focus on Linux here, with special respect to Debian. I installed daemontools, daemontools-run, and svtools.
##### Note4 #####
Meta, isn’t it?
##### Note5 #####
Note that this is absolutely optional. The default GS/SS logging works when using daemontools, too.
##### Note6 #####
I.e. when using daemontools to stop a service, the shell script is terminated and not the children. This actually happened to me.
##### Note7 #####
Note that this directory is provided by default only by the Debian daemontools-run package. I will use /service\_tmpl/ here for the non-Debian case.
##### Note8 #####
supervise(8), svok(8), svstat(8), svscanboot(8), svscan(8), readproctitle(8), fghack(8), pgrphack(8), multilog(8), tai64n(8), tai64nlocal(8), setuidgid(8), envuidgid(8), envdir(8), softlimit(8), setlock(8)