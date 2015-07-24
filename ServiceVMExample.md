## Intro ##
The Service VM example is intended to provide example code for creating and using a separate "Service VM" for offloading work that in a Squeak/Pharo Seaside application, you would have forked of a thread to do the work (see [Porting Application-Specific Seaside Threads to GemStone](http://gemstonesoup.wordpress.com/2007/05/10/porting-application-specific-seaside-threads-to-gemstone/) and [threads within a request](http://forum.world.st/threads-within-a-request-td2335295.html#a2335295) for more information).

The prototypical example would be to obtain a token from an external web-service (i.e., sending an HTTP request to obtain a token or other data). You would not want to defer the response to the user in this case, especially if the request can take several minutes to complete (or fail as the case may be).

## Service Gem ##
For GLASS the solution is to create a separate Service gem that services performs stashed in an RCQueue. RCQueues are conflict free with multiple producers and a single consumer - exactly our case.

The Service gem
  1. polls for tasks in the queue
  1. pulls tasks out of the queue
  1. forks a thread to perform each individual task
  1. when the task is complete, the ending state is committed and the thread terminates

## Loading and Installing the Example ##
### Loading ###
```
MCPlatformSupport commitOnAlmostOutOfMemoryDuring: [
         [
                 Gofer project load: 'GsServiceVMExample' version: '1.0.0'.
                 Gofer project load: 'Seaside30' group: 'Seaside-Adaptors-FastCGI'.
                   "OR"
                 Gofer project load: 'Seaside30' group: 'Seaside-Adaptors-Swazoo'.
         ]
             on: Warning
             do: [:ex |
                 Transcript cr; show: ex description.
                 ex resume ]].
WAAdmin 
	register: WAObjectLog 
	asApplicationAt: WAObjectLog entryPointName
	user: 'admin' password: 'tool'.
WAGemStoneMaintenanceTask initialize.
```
### Supporting Scripts ###
Here's the [runSeasideGems30](ServiceVMExampleRunSeasideGems30Script.md) and the [startServiceVM30](ServiceVMExampleStartServiceVM30Script.md) scripts that are needed to run this example.
## Running the Example ##
#### Component Based ####
With the Component Based example, you can interactively step through the three states of the service task.
```
http://example.com/examples/serviceInteractive
```
#### REST API ####
The RESTful API is intended to make it easy to use siege to initiate the various steps and thus load up the Service VM (yeah I'm using a GET to initiate work ... so sue me:):
```
http://example.com/examples/service/step1
http://example.com/examples/service/step2
http://example.com/examples/service/step3
```
The other two urls give you a page with three anchors that you can hit yourself and an url that allows you to get the status of a service task by id:
```
http://example.com/examples/service
http://example.com/examples/service/{taskid}
```