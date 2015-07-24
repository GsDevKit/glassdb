With Seaside 3.0.0-alpha5.15 the [startMaintenance30](StartMaintenance30.md) script is configurable _**without having to edit the script**_. You can change the frequency, disable or replace the default tasks:
  * [Mark For Collection](MaintenanceVMTasks#Mark_For_Collection.md)
  * [Seaside Session Expiration](MaintenanceVMTasks#Seaside_Session_Expiration.md)

The [startMaintenance30](StartMaintenance30.md) script calls **WAGemStoneMaintenanceTask class>>performTasks:** once a minute. To add a task simply add a class-side method to **WAGemStoneMaintenanceTask** beginning with _**maintenanceTask**_ that returns a task definition and that task will be performed at the frequency desired.

There are two class-side methods in **WAGemStoneMaintenanceTask** for defining tasks:
  * **name:frequency:valuable:**
  * **name:frequency:valuable:reset:**
where:
    * _name_ is a simple identifier for the task.
    * _frequency_ is how often in minutes the task will be performed.
    * _valuable_ is sent the message **#value:** with the task instance as an argument to perform the task. The task instance has a _state_ instance variable that can be used to store state across task invocations. See [Seaside Session Expiration](MaintenanceVMTasks#Seaside_Session_Expiration.md) for an example of _state_ usage.
    * _reset_ is sent the message **#value:** with the task instance as an argument to reset the state of the task.

## Default Maintenance Tasks ##
### Mark For Collection ###
```
maintenanceTaskMarkForCollect
	^self 
		name: 'Mark For Collect'
		frequency: 60
		valuable: [:task | 
			GsFile gciLogServer: 'Starting markForCollect.: ', DateAndTime now printString.
      		[ 	
				System transactionMode == #autoBegin 
					ifTrue: [ System abortTransaction ]
					ifFalse: [ System beginTransaction ].
				SystemRepository markForCollection ] 
			  on: Error
        		  do: [:ex |
					((ex gsNumber == 3020) _or: [ex gsNumber == 3006])
					  ifTrue: [ | fileSize freeSpace used fileUnit freeUnit usedUnit converter |
					    fileSize := SystemRepository fileSize / 1024.0.
					    freeSpace := SystemRepository freeSpace / 1024.0.
					    used := fileSize - freeSpace.
					    fileUnit := fileSize > (1024)
					      ifTrue: [
					        fileSize := fileSize / 1024.
					        'M']
					      ifFalse: ['K'].
					    freeUnit := freeSpace > (1024)
					      ifTrue: [
					        freeSpace := freeSpace / 1024.
					        'M']
					      ifFalse: ['K'].
					    usedUnit := used > (1024)
					      ifTrue: [
					        used := used / 1024.
					        'M']
					      ifFalse: ['K'].
					    System transactionMode ~~ #autoBegin ifTrue: [ System beginTransaction ].
					    converter := GRNumberPrinter new precision: 2.
					    (ObjectLogEntry
					      trace: 'MTCE: Repository Size'
					      object: 'Repository: ', (converter print: fileSize) , fileUnit,
										    ', Free: ', (converter print: freeSpace), freeUnit,
										    ', Used: ', (converter print: used), usedUnit) addToLog.
					    (ObjectLogEntry trace: 'MTCE: MFC' object: ex) addToLog.
					    System commitTransaction.
					    GsFile gciLogServer: ex description]
					  ifFalse: [ex pass ]].
			GsFile gciLogServer: '...finished markForCollect.', DateAndTime now printString ]
```
### Seaside Session Expiration ###
```
maintenanceTaskExpiration
	^self 
		name: 'Seaside Session Expiration'
		frequency: 1
		valuable: [:task | | expired expirations transactionMode |
  			GsFile gciLogServer: 'Unregistering...', DateAndTime now printString.
			transactionMode := System transactionMode.
   			transactionMode ~~ #autoBegin ifTrue: [ System transactionMode: #autoBegin ].
  			expirations := task state.
  			System _sessionCacheStatAt: 5 put: expirations.
  			System _sessionCacheStatAt: 6 put: 0.
 			 expired := WABasicDevelopment reapSeasideCache.
  			expirations := expirations + 1.
			task state: expirations.
  			System _sessionCacheStatAt: 5 put: expirations.
  			System _sessionCacheStatAt: 6 put: expired.
  			expired > 0 ifTrue: [ (ObjectLogEntry trace: 'MTCE: expired sessions' object: expired) addToLog ].
  			GsFile gciLogServer: '...Expired: ', expired printString, ' sessions.'.
  			System commitTransaction.
  			System transactionMode: transactionMode ]
		reset: [:task | task state: 0 ]
```