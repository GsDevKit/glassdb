### 1.0-beta.9 ###
  * DaleHenrichs 3/13/2013 10:17
  * Announcement
    * [GLASS 1.0-beta.9 released](http://forum.world.st/GLASS-1-0-beta-9-released-tp4676653.html)
  * support for GemStone/S 3.1.0.3 release
  * GsCore 0.247 (dkh.286)
    * Metacello 1.0-beta.32 support
    * 0.247 (dkh.256):
      * improve FileDirectory>.assureExistence logic
      * Symbol>>precedence should answer 0 if it''s an invalid selector
    * 0.247 (dkh.257):
      * redo proxy support fix for PUT with proper method annotations
      * merge Bootstrap-dkh.207
      * merge Core-dkh.58
      * merge Squeak-dkh.281
      * support for Metacello 1.0-beta.32 for GemStone3.x
    * 0.247 (dkh.258):
      * Zinc support
    * 0.247 (dkh.265):
      * pick up newer version of Scanner from Pharo. fix bugs in Scanner>>scanMessageParts: for use in ChangeList class>parseSelector: for use by FileTree
      * subclasses of GsFile have to be treated differently for MagLev
    * 0.247 (dkh.268):
      * integrate 0.246.2 changes
    * 0.247 (dkh.269):
      * WriteStream>>space: for Squeak/Pharo compat
    * 0.247 (dkh.270):
      * another Scanner scanMesageparts: bugfix
    * 0.247 (dkh.271):
      * ODE support: regex-based senders/implementors
    * 0.247 (dkh.272):
      * adjust TestResult printString
      * gs bugfix (Integer>>printStringRadix:showRadix:) in 3.1.0.1
    * 0.247 (dkh.274):
      * RefactoringBrowser support
    * 0.247 (dkh.276):
      * revert SystemNavigation>>sendersOf: old implementation still needed.
      * defer integration of Paul''s contributions one cycle
    * 0.247 (dkh.277):
      * merge Core.v3-dkh.73, Bootstrap.v3-dkh.227, Squeak.v3-dkh.292 into 2.x (FileTree 1.0.1 support)
      * merge Squeak-dkh.284 into 3.x
      * [Issue 356](https://code.google.com/p/glassdb/issues/detail?id=356): variableSubclasses incorrectly handled for Monticello
    * 0.247 (dkh.278):
      * get Metacello Preview 1.0.0-beta.32.4 running on GemStone 3.0.1
    * 0.247 (dkh.279):
      * [Issue 356](https://code.google.com/p/glassdb/issues/detail?id=356): variableSubclasses incorrectly handled for Monticello (3.1.x variant)
    * 0.247 (dkh.282):
      * tweak SqueakTests>>testDateAndTimeFromString to pass no matter when the sample is taken (2.4.x and 3.x) tracked as internal [Bug 42882](https://code.google.com/p/glassdb/issues/detail?id=2882)
    * 0.247 (dkh.284):
      * make SqueakTests>>testDateArithmetic less sensitive to round-off errors
  * GsMisc 0.242 (dkh.110)
    * open 0.242 for development
    * 0.242 (dkh.102):
      * zinc support
    * 0.242 (dkh.105):
      * merge 2.x Zinc support
    * 0.242 (dkh.106):
      * fix [Issue 351](https://code.google.com/p/glassdb/issues/detail?id=351) - Announcements issue with Pier3
    * 0.242 (dkh.107):
      * clean up minor test issues
    * 0.242 (dkh.108):
      * clean up 3.1.x minor test issues
    * 0.242 (dkh.108):
      * fix an issue in GLASSProejctSupport building 1.0-beta.9 for G/S 3.1.0.3 release
  * GsMonticello 0.244.2 (dkh.172)
    * 0.244 (dkh.154)
      * reconcile with FileTree changes (3.1.0.x for now)
    * 0.244 (dkh.155)
      * use Scanner>>scanMessageParts: in ChangeList class>parseSelector: for use by FileTree
      * add some more parseSelector: tests
    * 0.244.2 (dkh.160):
      * integrate 0.244.1 changes
    * 0.244.2 (dkh.161):
      * improve debuggability of dependency warnings: required IV has a dictionary mapping unresolved to references ... very useful
    * 0.244.2 (dkh.162)
      * revert previous change ... useful but unloadable ....:
    * 0.244.2 (dkh.163)
      * merge changes from Monticello.v3-dkh.453
      * [Issue 356](https://code.google.com/p/glassdb/issues/detail?id=356): variableSubclasses incorrectly handled for Monticello
    * 0.244.2 (dkh.164):
      * get Metacell Preview 1.0.0-beta.32.4 running on GemStone 3.0.1
    * 0.244.2 (dkh.165):
      * [Issue 356](https://code.google.com/p/glassdb/issues/detail?id=356): variableSubclasses incorrectly handled for Monticello (3.1.x variant)
    * 0.244.2 (dkh.166):
      * tracing to gather info about why GsDeployer class>>deploy: only fails in 3.1.0.2 test on travis...
    * 0.244.2 (dkh.167):
      * put halt in GsDeployerTest>>testBug40559 to get error stack from travis run
    * 0.244.2 (dkh.168):
      * need to dump exception description .... getting close
    * 0.244.2 (dkh.169):
      * fix up a test case to make it more reliable in G/S 2.4.4.x
    * 0.244.2 (dkh.170):
      * have to limit maxThreads on listInstances: (3.1.0.x) so that tests can run in travisCI (see http://kermit.gemstone.com/bug?bug=42908)
    * 0.244.2 (dkh.171):
      * fix 3.0.1 config
  * GsSqueakCommon 0.9.4 (dkh.24)
    * 0.9.4 (dkh.23):
      * zinc support

### 1.0-beta.8.7.4 ###
  * DaleHenrichs 11/15/2012 10:04
  * support for GemStone/S 3.1.0.2 release
  * GsCore 0.246.2 (dkh.266)
    * fix [bug42589](https://code.google.com/p/glassdb/issues/detail?id=589): Stack overflow in seaside upgrade
  * GsMonticello 0.243.1 (dkh.156)
    * fix [bug42589](https://code.google.com/p/glassdb/issues/detail?id=589): Stack overflow in seaside upgrade
  * GsMonticello 0.243.1 (dkh.158)
    * ump version to force load
### 1.0-beta.8.7.3 ###
  * DaleHenrichs 9/21/2012 14:17
  * Announcements
  * 1.0-beta.8.7.3 (dkh.213):
    * support for GemStone/S 3.1.0.1 release
    * GsCore 0.246.1 (dkh.262)
      * fix [issue 352](https://code.google.com/p/glassdb/issues/detail?id=352) - CharcterCollection>>_findSmallString:startingAt:ignoreCase: and friends deleted in GemStone/S 3.1.0.1
      * add test for [Issue 348](https://code.google.com/p/glassdb/issues/detail?id=348) - SequenceableCollection>>copyFrom:to:into:startingAt: no longer throws errors in 3.1
    * GsMisc 0.241.1 (dkh.103)
      * fix [Issue 353](https://code.google.com/p/glassdb/issues/detail?id=353) - UTF8 tests failing in 3.1.0.1
  * 1.0-beta.8.7.3 (dkh.214):
    * latest version of Metacello (1.0-beta.31.1.5)
### 1.0-beta.8.7.2 ###
  * DaleHenrichs 6/19/2012 17:03
  * Announcements
    * [GLASS 1.0-beta.8.7.2 released](http://forum.world.st/GLASS-1-0-beta-8-7-2-released-td4635736.html)
  * Grease 1.0.7.1
    * reimplement SendMail>>connectTo:on: to be portable between GemStone/S 2.x and 3.x
    * Port Grease to Pharo2.0.
    * BlockContext class no longer exists in Pharo2.0, so the BlockContext extension methods only needed for Pharo1.3 and earlier
    * Slime not ported to Pharo2.0, yet, so exclude
    * GemStone 3.1 support for libICU (Unicode)
    * Adjust Utf8 code .. libICU produces a ByteArray when it encodes to UTF8, but Seaside wants Strings
  * GsCore 0.246
    * 0.245.2 (dkh.242):
      * clean up 3.0.1 sent by not implemented symbols masked by an SentButNotImplementedTest>>expectedFailure
    * 0.245.2.1 (dkh.244)
      * support for FileTree
    * 0.246 (dkh.245)
      * fix [Issue 343](https://code.google.com/p/glassdb/issues/detail?id=343): pool dictionary / SharedPool affinity broken
    * 0.246 (dkh.246):
      * port fix for [Issue 343](https://code.google.com/p/glassdb/issues/detail?id=343) to 3.x
      * port FileTree support to 3.x
      * port fix for [Issue 304](https://code.google.com/p/glassdb/issues/detail?id=304) to 3.x
    * 0.246 (dkh.247):
      * Class>>byteSubclass:classVars:classInstVars:poolDictionaries:inDictionary:newVersionOf:description:options: is no longer needed ... the base version is preferable
    * 0.246 (dkh.248):
      * clean up SentButNotImplementedTest for 3.1
    * 0.246 (dkh.249):
      * clean up FileDirectory tests for OSX and GemStone2.4
    * 0.246 (dkh.250):
      * Zinc support
    * 0.246 (dkh.251):
      * Additional Zinc support
    * 0.246 (dkh.252):
      * Additional 3.1 work
      * merge 249-251 work
  * GsMisc
    * 0.240.1 (dkh.89);
      * eimplement SendMail>>connectTo:on: to be portable between GemStone/S 2.x and 3.x
    * 0.241 (dkh.91):
      * update the bootstrap script for 3.1
    * 0.241 (dkh.92):
      * libICU support for 3.1
    * 0.241 (dkh.93):
      * the class Utf8 is a ByteArray and the result of encodeasUTF8 is an instance of Utf8
    * 0.241 (dkh.94):
      * continue working through Utf8 issues
    * 0.241 (dkh.95):
      * Utf8 tests passing ... but not done
    * 0.241 (dkh.96):
      * Support for 3.1 in GemStone-Release-Support
    * 0.241 (dkh.97):
      * missed some Utf8 cleanup
    * 0.241 (dkh.97):
      * missed some Utf8 cleanup
    * 0.241 (dkh.98):
      * use Unicode**classes instead of Utf8** classes
  * GsMonticello 0.243
    * 0.243 (dkh.144)
      * FileTree support
      * tests for [Issue 343](https://code.google.com/p/glassdb/issues/detail?id=343): pool dictionary / SharedPool affinity broken
    * 0.243 (dkh.146):
      * port fix for [Issue 309](https://code.google.com/p/glassdb/issues/detail?id=309) to 3.x
      * port fix for [Bug41597](https://code.google.com/p/glassdb/issues/detail?id=597): Instance Migration should not require code mod privilege
      * FileTree support for 3.x
      * port tests for [Issue 343](https://code.google.com/p/glassdb/issues/detail?id=343) to 3.x
    * 0.243 (dkh.147):
      * make it possible to skip automatic initialization on a class by class basis with MCPerformPostloadNotification. Useful during GemStone upgrade when all methods removed and recompiled.
    * 0.243 (dkh.148):
      * fix bug in MCPerformPostloadNotification
    * 0.243 (dkh.149):
      * clean up SentButNotImplemented for GemStone3.1
    * 0.243 (dkh.150):
      * fix MCHttpRepositoryTest>>testBug38412 in presence of proxy server
    * 0.243 (dkh.151):
      * fix MCHttpRepositoryTest>>testBug38412 for 2.4.x
  * GsOB 0.242.1
    * 0.242.1 (dkh.84);
      * clean up 3.0.1 sent by not implemented symbols masked by an SentButNotImplementedTest>>expectedFailures
    * 0.242.1 (dkh.85):
      * "merge" OB-Standard for 3.x
  * GsSqueakCommon 0.9.3
    * 0.9.3 (dkh.20):
      * GemStone 3.1 liICU (Unicode) support
    * 0.9.3 (dkh.21):
      * DynamicVariable and friends for Zinc
### 1.0-beta.8.7.1 ###
  * DaleHenrichs 11/17/2011 14:15
  * Announcements
    * [GemStone/S 64 3.0.1 is Shipping](http://gemstonesoup.wordpress.com/2011/11/15/gemstones-64-3-0-1-is-shipping/)
  * GsCore 0.245.1
    * 0.245.1 (dkh.232):
      * open 0.245.1 for development.
      * support for GemStone/S 2.4.5 release
      * Regex depends upon Squeak
    * 0.245.1 (dkh.233):
      * autoMigrate turned off incorrectly
    * 0.245.1 (dkh.234):
      * Integrate fix for [Bug41763](https://code.google.com/p/glassdb/issues/detail?id=763): versioning class references instance of GsClassDocumentation, does not copy
      * adjust tests for GemStone/S 2.4.5
      * fix [Issue 304](https://code.google.com/p/glassdb/issues/detail?id=304): printString from DateAndTime created with ScaledDecimal contains unnecessary dot
    * 0.245.1 (dkh.235):
      * adjust tests for GemStone/S 2.4.5
    * 0.245.1 (dkh.236):
      * additional fixes for [Bug41763](https://code.google.com/p/glassdb/issues/detail?id=763): versioning class references instance of GsClassDocumentation, does not copy
      * use Issue29FixANeeded and Issue29FixBNeeded for project attributes (affects 0.245 as well)
    * 0.245.1 (dkh.237):
      * get the packaging of_description and _description: right
    * 0.245.1 (dkh.238):
      * straighten out tests
    * 0.245.1 (dkh.239):
      * straighten out 2.4.4.7 tests
      * straighten out 2.4.4 tests
      * straighten out 2.3.1 tests
    * 0.245.1 (dkh.240):
      * additional patch for [Bug41763](https://code.google.com/p/glassdb/issues/detail?id=763)
  * GsMisc 0.240
    * 0.240 (dkh.84)
      * 0.240 opened for development
      * support for GemStone/S 2.4.5 release
    * 0.240 (dkh.85)
      * hackery for bootstrapping Metacello
    * 0.240 (dkh.86)
      * fix repositoryMap algorithm
      * no longer need to load GoferProjectLoader separately
  * GsMonticello 0.242
    * 0.242 (dkh.137):
      * open 0.242 for development
      * Integrate fix for [Bug41597](https://code.google.com/p/glassdb/issues/detail?id=597): Instance Migration should not require code mod privilege
      * adjust tests for GemStone/S 2.4.5
    * 0.242 (dkh.138):
      * fix [Issue 308](https://code.google.com/p/glassdb/issues/detail?id=308): ConfigurationOfGrease (and others) dirty after a load
    * 0.242 (dkh.139):
      * fix [Issue 309](https://code.google.com/p/glassdb/issues/detail?id=309): ConfigurationofMetacello dirtied during GLASS 1.0-beta.8.7.1 load
    * 0.242 (dkh.140):
      * additional patch for [Issue 309](https://code.google.com/p/glassdb/issues/detail?id=309)
    * 0.242 (dkh.141):
      * workaround for [Issue 311](https://code.google.com/p/glassdb/issues/detail?id=311): sent bug not implemented in GLASS 1.0-beta.8.7.1 Minimal load
### 1.0-beta.8.7 ###
  * DaleHenrichs 10/20/2011 15:10
  * Announcements
    * [GLASS 1.0-beta.8.7 released](http://forum.world.st/GLASS-1-0-beta-8-7-released-td3923882.html)
    * [GLASS 1.0-beta.8.7 released](http://gemstonesoup.wordpress.com/2011/10/21/glass-1-0-beta-8-7-released)
  * GsCore 0.245
    * factor GsDeployer to expose autoMigrate and bulkMigrate options
    * fix a Notification bug revealed by porting MetacelloBrowser
    * clean up suprious CompileWarings
    * tests passing in GemStone 3.0
    * pick up changes from 3.0 ... AssertionFailure and friends
    * tweak assertion failure tests
    * add a missing call to #_checkCompileResult:source:
    * move GemStone-Deployment from Core to Monticello
    * fix [Issue 252](https://code.google.com/p/glassdb/issues/detail?id=252): cannot bootstrap GsDeployer
    * fix [Issue 220](https://code.google.com/p/glassdb/issues/detail?id=220): extent0.seaside.dbf contains reference to repository on GemStone build machine
    * moved a method that created a dependency during bootstrap from core to bootstrap
    * get the tests passing again
    * MetacelloBrowser event support
    * fix [Issue 53](https://code.google.com/p/glassdb/issues/detail?id=53): GsFile doesn''t understand crlf
    * fix [Issue 241](https://code.google.com/p/glassdb/issues/detail?id=241): GsPharo-Core does not implement Collection>>#groupedBy:
    * fix [Issue 148](https://code.google.com/p/glassdb/issues/detail?id=148): DateAndTimeANSI>>#''dayOfWeek'' gives GMT not local
    * fix [Issue 229](https://code.google.com/p/glassdb/issues/detail?id=229): ScaledDecimal class>>readFrom: returns Number not ScaledDecimal
    * fix [Issue 230](https://code.google.com/p/glassdb/issues/detail?id=230):	Number class>>readFrom: fails when Locale class>>decimalPoint not ''.''
    * pick up latest 3.0 patches from Allen
    * merge Bootstrap-DaleHenrichs.197, Bootstrap.v3-DaleHenrichs.208, Bootstrap.v3-DaleHenrichs.209
    * merge Core-dkh.43, Core.v3-DaleHenrichs.58
    * merge Squeak-dkh.258
    * use SessionTemps directly for myDependents...
    * GsFile class>_createDirectory... changed ... fix usage
    * standard SUnit tests are now part of base, so adjust tests for expected failures extension
    * TestResource class>>reset is now correct in base
    * clean up Smalltalk reference in Core .... bootstrapping problem
    * 0.245 (DaleHenrichs.191):
      * fix up an undeclared global during bootstrapping
    * 0.245 (DaleHenrichs.192):
      * add a FileStream implementation
      * Iliad support
    * 0.245 (DaleHenrichs.193):
      * made another pass through FileStream implementation to make it a bit more portable
      * writing a bunch of tests:
        * 186 run, 164 passes, 8 expected failures, 14 failures, 0 errors, 0 unexpected passes
    * 0.245 (DaleHenrichs.194):
      * FileStream looks good for 2.x ... tests running green:
        * 186 run, 178 passes, 8 expected failures, 0 failures, 0 errors, 0 unexpected passes
    * 0.245 (DaleHenrichs.195):
      * Iliad support
    * 0.245 (dkh.196):
      * incorporate Allen''s most recent  patches
      * changes for new Random classes
      * merge Core-DaleHenrichs.44
      * expectedFailures for tests that will be fixed later
      * 597 run, 595 passes, 2 expected failures, 0 failures, 0 errors, 0 unexpected passes
    * 0.245 (dkh.197):
      * integrate Sport3.010.NickAger.24, Squeak.dkh.258, Squeak.NickAger.262 and Squeak.NickAger.264.
      * this checkin is aimed at support for tODE in GLASS 1.0-beta.8.7
      * fix [Issue 281](https://code.google.com/p/glassdb/issues/detail?id=281): OrderedCollection>>#at:ifAbsentPut: required by WAUrl from Seaside-Core-pmm.732
      * fix [Issue 275](https://code.google.com/p/glassdb/issues/detail?id=275): Integrate support for Pharo''s Stream <<
    * 0.245 (dkh.198):
      * merge in tODE support for GemStone 3.0:
        * Sport (DaleHenrichs.26, NickAger.24)
        * Squeak (dkh.261, dkh.265)
      * fix [Issue 243](https://code.google.com/p/glassdb/issues/detail?id=243): more httpsocket issues
    * 0.244.1 (dkh.199):
      * version 0.244.1 added to avoid having the GsRandom package inadvertantly loaded into GemStone 3.0
    * 0.245 (dkh.200):
      * add Behavior>>methodsDo: for compatibility with GemStone3.0
    * 0.245 (dkh.201):
      * pick up Allen''s patch methods
      * replace usage of Behavior>>_methodDict
    * 0.245 (dkh.202):
      * correct implementation of Behavior>>methodsDo:
    * 0.245 (dkh.203):
      * Text class>>streamContents: fix long standing bug related to streamContents and presized stream contents ...
    * 0.245 (dkh.204) [3.0]:
      * merge Squeak.v3-dkh.267, Squeak-dkh.266
    * 0.245 (dkh.206):
      * address GemStone2.3.x upgrade issues
    * 0.245 (dkh.207):
      * fix [Issue 293](https://code.google.com/p/glassdb/issues/detail?id=293): FileDirectory>>directoryNamed: unconditionally returns instance of FileDirectory
    * 0.245 (dkh.208):
      * remove some incorrect code in ExceptionA>>description for GemStone 2.3
    * 0.245 (dkh.209):
      * GemStone 2.3 compatibility code
    * 0.245 (dkh.210):
      * get tests passing for GemStone2.3
    * 0.245 (dkh.213):
      * fix [Issue 260](https://code.google.com/p/glassdb/issues/detail?id=260): Sorting of SortedCollection superfluous
    * 0.245 (dkh.214):
      * fix [Issue 294](https://code.google.com/p/glassdb/issues/detail?id=294): PlusInfinity and friends don''t produce parseable strings ... sort of
    * 0.245 (dkh.215):
      * fix [Issue 299](https://code.google.com/p/glassdb/issues/detail?id=299): Collection>>ifEmpty: has wrong return value if not empty
    * 0.245 (dkh.216):
      * Swazoo 2.3.0.0 support
    * 0.245 (dkh.217):
      * need to use non-swazoo-specific methods for sport ...
    * 0.245 (dkh.218):
      * need to use non-swazoo-specific methods for sport ... complete the set of methods needed
    * 0.245 (dkh.219):
      * integrate recent changes into 3.0.1
    * 0.245 (dkh.221):
      * fix sent but not implemented
      * port SqueakTests>>testExceiptionalFloats to GemStone 2.3
    * 0.245 (dkh.222):
      * add GemStone-245-Exceptions to declare base overrides for tests
    * 0.245 (dkh.223):
      * integrate changes for GemStone 3.0
    * 0.245 (dkh.224):
      * fix [Bug41862](https://code.google.com/p/glassdb/issues/detail?id=862): Class>>description collides with Magritte use of #description
    * 0.245 (DataCurator.225):
      * remove Class>>byteSubclass:classVars:classInstVars:poolDictionaries:inDictionary:newVersionOf:description:isInvariant:isModifiable: as it is no longer used
    * 0.245 (dkh.226):
      * GemStone 3.0.1 fix for [Issue 130](https://code.google.com/p/glassdb/issues/detail?id=130): remote breakpoints don''t work
      * workarounds for [Issue 302](https://code.google.com/p/glassdb/issues/detail?id=302):  GemStone 3.0.1 class-side #comment method scheme is incompatible with Squeak/Pharo/VW
    * 0.245 (dkh.227):
      * update BreakpointTest to test most recent issue
    * 0.245 (dkh.228):
      * clean up tests when run against Minimal GLASS group
    * 0.245 (dkh.229):
      * use #cull: in NumberParser>>expected:
    * 0.245 (dkh.230):
      * fix Breakpoint test (when running Native code)
      * fix SqueakTest>>testExceptionalFloats ... no longer need conditional code for GemStone 2.3
  * GsMonticello 0.241
    * fix [Issue 252](https://code.google.com/p/glassdb/issues/detail?id=252): cannot bootstrap GsDeployer
    * remove reference GoferVersionReference which causes dependency problem during bootstrapping
    * fix Gofer reference ... for bootstrapping
    * another bootstrapping fix
    * compensate for for bootstrapping error related to [Issue 246](https://code.google.com/p/glassdb/issues/detail?id=246) bugfix
    * fix bugs introduced by bootstrapping bugfixes
    * MetacelloBrowser event support
    * fix [Issue 210](https://code.google.com/p/glassdb/issues/detail?id=210):  Programmatic access to Update...>Update GLASS
    * use SessionTemps directly for myDependents...
    * nice to get feedback about number of classes and number of instances migrated during classHistory clean up step/bulk migrate
    * 0.241 (DaleHenrichs.118):
      * need to check that actual superclass is identical to the class found in globals for #hasSimpleModsRelativeTo:
      * some more support for MetacelloBrowser
    * 0.241 (dkh.119):
      * changes for new Random classes
      * merge Monticello.g-DaleHenrichs.429
      * 597 run, 595 passes, 2 expected failures, 0 failures, 0 errors, 0 unexpected passes
    * 0.241 (dkh.120):
      * invert comparison direction in MCWorkingCopy>>changesRelativeToRepository: so that the #remove/#add sense is correct
    * 0.241 (dkh.121):
      * persistent author initials can be set by defining #''GS\_tODE\_AuthorInitials'' in UserGlobals with desired author initials string (in support of tODE)
    * 0.241 (dkh.122):
      * merge in tODE support for GemStone 3.0:
        * Monticello (dkh.434, dkh.431)
    * 0.241 (dkh.123) [3.0]:
      * replace use of
    * 0.241 (dkh.124):
      * create MCMethodDefinition class>>resetCachedDefinitions ... readOnly code support
    * 0.241 (dkh.125) [3.0]:
      * merge Monticello.g-dkh.432
    * 0.241 (dkh.126):
      * fix host name display for MCServerDirectoryRepository (after 3.0 ipv6 fixes)
    * 0.241 (dkh.127):
      * remove GsDeployer>>doPageOrderBulkMigrate until needed...Will not work in GemStone2.3
    * 0.241 (dkh.128):
      * [Issue 62](https://code.google.com/p/glassdb/issues/detail?id=62): MCDefinition Instance class var should be session temp
    * 0.241 (dkh.129):
      * fix [Issue 257](https://code.google.com/p/glassdb/issues/detail?id=257): Bug in Monticello with empty category name from dynamically generated methods
    * 0.241 (dkh.130):
      * fix  [Issue 285](https://code.google.com/p/glassdb/issues/detail?id=285): Changing class category does not reset class cache
    * 0.241 (dkh.131):
      * fix [Issue 286](https://code.google.com/p/glassdb/issues/detail?id=286): GsDeployer>>doBulkMigrate fails if there are more than 2000 classes ....
    * 0.241 (dkh.132):
      * swazoo support
      * clean up authorInitials logic a bit
    * 0.241 (dkh.133):
      * integrate recent changes for 3.0.1
    * 0.241 (dkh.134):
      * additional fallout from bugfix for [Bug41862](https://code.google.com/p/glassdb/issues/detail?id=862) (#classComment checks for class-side #comment method)
    * 0.241 (dkh.135):
      * clean up tests when run against Minimal GLASS group
      * fix rename category bug
  * GsOB 0.242
    * get the tests passing again
    * pick up latest announcements package (fix for [Issue 253](https://code.google.com/p/glassdb/issues/detail?id=253))
    * fix [Issue 67](https://code.google.com/p/glassdb/issues/detail?id=67): Class comment lost on rename (and possibly on redefinition, too)
    * add SymbolList browser ...
    * rename to OBSymbolListBrowser
    * support for MBOBConfigurationBrowser
    * 0.242 (DaleHenrichs.76):
      * fix a minor bug resulting from Globals browser changes
    * 0.242 (dkh.77):
      * merge OB-Standard.g-DaleHenrichs.436
      * 597 run, 595 passes, 2 expected failures, 0 failures, 0 errors, 0 unexpected passes
    * 0.242 (dkh.78) [3.0]:
      * OBRecentClasses list doesn''t need to be persistent ...
      * support for cloud foundry code sharing
    * 0.242 (dkh.79):
      * remove support for OBSymbolListBrowser in GemStone 2.x for now
    * 0.242 (dkh.80):
      * workarounds for [Issue 302](https://code.google.com/p/glassdb/issues/detail?id=302):  GemStone 3.0.1 class-side #comment method scheme is incompatible with Squeak/Pharo/VW
    * 0.242 (dkh.82):
      * clean up tests when run against Minimal GLASS group
  * GsMisc 0.239
    * fix [Issue 253](https://code.google.com/p/glassdb/issues/detail?id=253): unsubscribing in middle of event handling is Trouble for Announcements
    * merge Announcements.g-DaleHenrichs.14
    * 0.239 (DaleHenrichs.72):
      * refactored scripts in support of upgradeSeasideImage.topaz
    * 0.239 (dkh.73):
      * add support for additional email headers (SMTPMail-dkh.8)
    * 0.239.1 (dkh.79):
      * fix [Issue 269](https://code.google.com/p/glassdb/issues/detail?id=269): SmaCC: scanner uses incorrect stream indexing
    * 0.239.1 (dkh.80):
      * missed the package update for SmaCC
  * GsMisc 0.239.1
    * add support SMTP AUTH LOGIN (SMTPMail-topa.9)
    * 0.239.1 (dkh.75):
      * taking a crack at trying to use older version of XML Parser for GemStone 2.3
    * 0.239.1 (dkh.77):
      * GemStone 2.3 compatibility code
    * 0.239.1 (dkh.78):
      * fix [Issue 124](https://code.google.com/p/glassdb/issues/detail?id=124): GemToGemAnnouncement registeredSessions at risk for duplicates
    * 0.239.1 (dkh.79):
      * fix [Issue 269](https://code.google.com/p/glassdb/issues/detail?id=269): SmaCC: scanner uses incorrect stream indexing
    * 0.239.1 (dkh.81):
      * preparing for GLASS 1.0-beta.8.7/GemStone 3.0.1 releases
    * 0.239.1 (dkh.82):
      * integrate fixes for GemStone 3.0
  * GsSqueakCommon 0.9.2
    * support method (asStringOrText) for MetacelloBrowser
    * support for MetacelloBrowser
    * 0.9.2 (DaleHenrichs.11):
      * Iliad support
    * 0.9.2 (dkh.12):
      * more Iliad support
    * 0.9.2 (dkh.13):
      * more Iliad support
    * 0.9.2 (dkh.14):
      * changes for new Random classes
      * 597 run, 595 passes, 2 expected failures, 0 failures, 0 errors, 0 unexpected passes
    * 0.9.2 (dkh.15):
      * SqueakSource3 support
    * 0.9.2 (dkh.16):
      * Grease 1.0.6.2
    * 0.9.2 (dkh.17):
      * Grease 1.0.6.3
      * clean up tests when run against Minimal GLASS group

### 1.0-beta.8.6 ###
  * DaleHenrichs 3/3/2011 15:50
  * Announcement
    * [GLASS 1.0-beta.8.6 released](http://forum.world.st/GLASS-1-0-beta-8-6-released-tp3334541p3334541.html)
    * [GLASS 1.0-beta.8.6 released](http://gemstonesoup.wordpress.com/2011/03/03/glass-1-0-beta-8-6-released/)
  * Core 0.244
    * get Seaside3.0 running on GemStone3.0beta3
    * fix [Issue 212](https://code.google.com/p/glassdb/issues/detail?id=212):  FileDirectory class>>onClient switched sense
    * fix [Issue 214](https://code.google.com/p/glassdb/issues/detail?id=214): Seaside3.0 full stack continuation has Semaphore references
    * GsDeploy class added to Core
    * autoCommit must be true when loading Pier2 to avoid issues with allInstances
    * fix [Issue 227](https://code.google.com/p/glassdb/issues/detail?id=227) fix move additional methods up to CharacterCollection that should work on MultiByteStrings as well
    * fix [Issue 242](https://code.google.com/p/glassdb/issues/detail?id=242): class instance variables not copied to new class version
    * fix [Issue 244](https://code.google.com/p/glassdb/issues/detail?id=244): unzip errors on .mcz files , 