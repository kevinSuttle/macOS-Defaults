# OSX Default Values Command Reference

## chflags
change file flags

```
usage: chflags [-fhv] [-R [-H | -L | -P]] flags file ...
```

[chflags man page](https://developer.apple.com/library/mac/documentation/Darwin/Reference/ManPages/man1/chflags.1.html)


## defaults
Command line interface to a user's defaults.

```
❯ defaults

Syntax:

'defaults' [-currentHost | -host <hostname>] followed by one of the following:

  read                                 shows all defaults
  read <domain>                        shows defaults for given domain
  read <domain> <key>                  shows defaults for given domain, key

  read-type <domain> <key>             shows the type for the given domain, key

  write <domain> <domain_rep>          writes domain (overwrites existing)
  write <domain> <key> <value>         writes key for domain

  rename <domain> <old_key> <new_key>  renames old_key to new_key

  delete <domain>                      deletes domain
  delete <domain> <key>                deletes key in domain

  import <domain> <path to plist>      writes all of the keys in path to domain
  export <domain> <path to plist>      saves domain as a binary plist to path
  domains                              lists all domains
  find <word>                          lists all entries containing word
  help                                 print this help

<domain> is ( <domain_name> | -app <application_name> | -globalDomain )
         or a path to a file omitting the '.plist' extension

<value> is one of:
  <value_rep>
  -string <string_value>
  -data <hex_digits>
  -int[eger] <integer_value>
  -float  <floating-point_value>
  -bool[ean] (true | false | yes | no)
  -date <date_rep>
  -array <value1> <value2> ...
  -array-add <value1> <value2> ...
  -dict <key1> <value1> <key2> <value2> ...
  -dict-add <key1> <value1> ...
```

**Tip:** Use `defaults domains` to to list all domains available. 

[defaults man page](https://developer.apple.com/library/mac/documentation/Darwin/Reference/ManPages/man1/defaults.1.html)  


## launchctl: 
Unload daemons/agents and generally control launchd

```  
❯ launchctl help

usage: launchctl <subcommand>
	load       	Load configuration files and/or directories
	unload     	Unload configuration files and/or directories
	start      	Start specified job
	stop       	Stop specified job
	submit     	Submit a job from the command line
	remove     	Remove specified job
	bootstrap  	Bootstrap launchd
	list       	List jobs and information about jobs
	setenv     	Set an environmental variable in launchd
	unsetenv   	Unset an environmental variable in launchd
	getenv     	Get an environmental variable from launchd
	export     	Export shell settings from launchd
	debug      	Set the WaitForDebugger flag for the target job to true.
	limit      	View and adjust launchd resource limits
	stdout     	Redirect launchd's standard out to the given path
	stderr     	Redirect launchd's standard error to the given path
	shutdown   	Prepare for system shutdown
	singleuser 	Switch to single-user mode
	getrusage  	Get resource usage statistics from launchd
	log        	Adjust the logging level or mask of launchd
	umask      	Change launchd's umask
	bsexec     	Execute a process within a different Mach bootstrap subset
	bslist     	List Mach bootstrap services and optional servers
	bstree     	Show the entire Mach bootstrap tree. Requires root privileges.
	managerpid 	Print the PID of the launchd managing this Mach bootstrap.
	manageruid 	Print the UID of the launchd managing this Mach bootstrap.
	managername	Print the name of this Mach bootstrap.
	asuser     	Execute a subcommand in the given user's context.
	exit       	Exit the interactive invocation of launchctl
	quit       	Quit the interactive invocation of launchctl
	help       	This help output
```

**Tip:** Use `launchctl list` to show the currently set values for `launchctl`.

[launchctl man page](https://developer.apple.com/library/mac/documentation/Darwin/Reference/ManPages/man1/launchctl.1.html)


## mdutil
Manage the metadata stores used by Spotlight

```
Usage: mdutil -pEsa -i (on|off) -d volume ...
       mdutil -t {volume-path | deviceid} fileid
	Utility to manage Spotlight indexes.
	-p             Publish metadata.
	-i (on|off)    Turn indexing on or off.
	-d             Disable Spotlight activity for volume (re-enable using -i on).
	-E             Erase and rebuild index.
	-s             Print indexing status.
	-t             Resolve files from file id with an optional volume path or device id.
	-a             Apply command to all volumes.
	-V vol         Apply command to all stores on the specified volume.
	-v             Display verbose information.
NOTE: Run as owner for network homes, otherwise run as root.
```

[mdutil man page](https://developer.apple.com/library/mac/documentation/Darwin/Reference/ManPages/man1/mdutil.1.html)

## nvram
Manipulate firmware NVRAM variables

```
nvram [-x] [-p] [-f filename] [-d name] [-c] name[=value] ...
	-x         use XML format for printing or reading variables
	           (must appear before -p or -f)
	-p         print all firmware variables
	-f         set firmware variables from a text file
	-d         delete the named variable
	-c         delete all variables
	name=value set named variable
	name       print variable
Note that arguments and options are executed in order.
```

**Tip:** Use `nvram -xp` to show all firmware variables in XML format.

[nvram man page](https://developer.apple.com/library/mac/documentation/Darwin/Reference/ManPages/man8/nvram.8.html)


## PListBuddy
Read and write values to plists

```
❯ /usr/libexec/PlistBuddy

Usage: PlistBuddy [-cxh] <file.plist>
    -c "<command>" execute command, otherwise run in interactive mode
    -x output will be in the form of an xml plist where appropriate
    -h print the complete help info, with command guide
```

### PListBuddy help
```
❯ /usr/libexec/PlistBuddy -h

Command Format:
    Help - Prints this information
    Exit - Exits the program, changes are not saved to the file
    Save - Saves the current changes to the file
    Revert - Reloads the last saved version of the file
    Clear [<Type>] - Clears out all existing entries, and creates root of Type
    Print [<Entry>] - Prints value of Entry.  Otherwise, prints file
    Set <Entry> <Value> - Sets the value at Entry to Value
    Add <Entry> <Type> [<Value>] - Adds Entry to the plist, with value Value
    Copy <EntrySrc> <EntryDst> - Copies the EntrySrc property to EntryDst
    Delete <Entry> - Deletes Entry from the plist
    Merge <file.plist> [<Entry>] - Adds the contents of file.plist to Entry
    Import <Entry> <file> - Creates or sets Entry the contents of file

Entry Format:
    Entries consist of property key names delimited by colons.  Array items
    are specified by a zero-based integer index.  Examples:
        :CFBundleShortVersionString
        :CFBundleDocumentTypes:2:CFBundleTypeExtensions

Types:
    string
    array
    dict
    bool
    real
    integer
    date
    data

Examples:
    Set :CFBundleIdentifier com.apple.plistbuddy
        Sets the CFBundleIdentifier property to com.apple.plistbuddy
    Add :CFBundleGetInfoString string "App version 1.0.1"
        Adds the CFBundleGetInfoString property to the plist
    Add :CFBundleDocumentTypes: dict
        Adds a new item of type dict to the CFBundleDocumentTypes array
    Add :CFBundleDocumentTypes:0 dict
        Adds the new item to the beginning of the array
    Delete :CFBundleDocumentTypes:0 dict
        Deletes the FIRST item in the array
    Delete :CFBundleDocumentTypes
        Deletes the ENTIRE CFBundleDocumentTypes array
```

[PlistBuddy man page](https://developer.apple.com/library/mac/documentation/Darwin/Reference/ManPages/man8/PlistBuddy.8.html)


## pmset
Manipulate power management settings

**Tips:**     
* Use `pmset -g` to show the currently settings.
* Use `pmset -g ps` to show power source info.

```
❯ pmset -g
Active Profiles:
Battery Power		-1*
AC Power		-1
Currently in use:
 standbydelay         86400
 standby              1
 halfdim              1
 hibernatefile        /var/vm/sleepimage
 darkwakes            0
 gpuswitch            2
 disksleep            10
 sleep                10
 autopoweroffdelay    14400
 hibernatemode        3
 autopoweroff         1
 ttyskeepawake        1
 displaysleep         2
 acwake               0
 lidwake              1
```

```
❯ pmset -g ps
Now drawing from 'Battery Power'
 -InternalBattery-0	98%; discharging; 4:52 remaining
```
[pmset man page](https://developer.apple.com/library/mac/documentation/Darwin/Reference/ManPages/man1/pmset.1.html)


## scutil
Manage system configuration parameters 

```
Usage: scutil
	interactive access to the dynamic store.

   or: scutil --prefs [preference-file]
	interactive access to the [raw] stored preferences.

   or: scutil [-W] -r nodename
   or: scutil [-W] -r address
   or: scutil [-W] -r local-address remote-address
	check reachability of node, address, or address pair (-W to "watch").

   or: scutil -w dynamic-store-key [ -t timeout ]
	-w	wait for presense of dynamic store key
	-t	time to wait for key

   or: scutil --get pref
   or: scutil --set pref [newval]
   or: scutil --get filename path key
	pref	display (or set) the specified preference.  Valid preferences
		include:
			ComputerName, LocalHostName, HostName
	newval	New preference value to be set.  If not specified,
		the new value will be read from standard input.

   or: scutil --dns
	show DNS configuration.

   or: scutil --proxy
	show "proxy" configuration.

   or: scutil --nwi
	show network information

   or: scutil --nc
	show VPN network configuration information. Use --nc help for full command list
```
[scutil man page](https://developer.apple.com/library/mac/documentation/Darwin/Reference/ManPages/man8/scutil.8.html)


## systemsetup
Configuration tool for certain machine settings in System Preferences.  

```
❯ systemsetup -help

systemsetup Help Information
-------------------------------------
Usage: systemsetup -getdate
	Display current date.

Usage: systemsetup -setdate <mm:dd:yy>
	Set current date to <mm:dd:yy>.

Usage: systemsetup -gettime
	Display current time.

Usage: systemsetup -settime <hh:mm:ss>
	Set current time to <hh:mm:ss>.

Usage: systemsetup -gettimezone
	Display current time zone.

Usage: systemsetup -settimezone <timezone>
	Set current time zone to <timezone>. Use "-listtimezones" to list time zones.

Usage: systemsetup -listtimezones
	List time zones supported by this machine.

Usage: systemsetup -getusingnetworktime
	Display whether network time is on or off.

Usage: systemsetup -setusingnetworktime <on off>
	Set using network time to either <on> or <off>.

Usage: systemsetup -getnetworktimeserver
	Display network time server.

Usage: systemsetup -setnetworktimeserver <timeserver>
	Set network time server to <timeserver>.

Usage: systemsetup -getsleep
	Display amount of idle time until computer, display and hard disk sleep.

Usage: systemsetup -setsleep <minutes>
	Set amount of idle time until computer, display and hard disk sleep to <minutes>.
	Specify "Never" or "Off" for never.

Usage: systemsetup -getcomputersleep
	Display amount of idle time until computer sleeps.

Usage: systemsetup -setcomputersleep <minutes>
	Set amount of idle time until compputer sleeps to <minutes>.
	Specify "Never" or "Off" for never.

Usage: systemsetup -getdisplaysleep
	Display amount of idle time until display sleeps.

Usage: systemsetup -setdisplaysleep <minutes>
	Set amount of idle time until display sleeps to <minutes>.
	Specify "Never" or "Off" for never.

Usage: systemsetup -getharddisksleep
	Display amount of idle time until hard disk sleeps.

Usage: systemsetup -setharddisksleep <minutes>
	Set amount of idle time until hard disk sleeps to <minutes>.
	Specify "Never" or "Off" for never.

Usage: systemsetup -getwakeonmodem
	Display whether wake on modem is on or off.

Usage: systemsetup -setwakeonmodem <on off>
	Set wake on modem to either <on> or <off>.

Usage: systemsetup -getwakeonnetworkaccess
	Display whether wake on network access is on or off.

Usage: systemsetup -setwakeonnetworkaccess <on off>
	Set wake on network access to either <on> or <off>.

Usage: systemsetup -getrestartpowerfailure
	Display whether restart on power failure is on or off.

Usage: systemsetup -setrestartpowerfailure <on off>
	Set restart on power failure to either <on> or <off>.

Usage: systemsetup -getrestartfreeze
	Display whether restart on freeze is on or off.

Usage: systemsetup -setrestartfreeze <on off>
	Set restart on freeze to either <on> or <off>.

Usage: systemsetup -getallowpowerbuttontosleepcomputer
	Display whether the power button is able to sleep the computer.

Usage: systemsetup -setallowpowerbuttontosleepcomputer <on off>
	Enable or disable whether the power button can sleep the computer.

Usage: systemsetup -getremotelogin
	Display whether remote login is on or off.

Usage: systemsetup -setremotelogin <on off>
	Set remote login to either <on> or <off>. Use "systemsetup -f -setremotelogin off" to suppress prompting when turning remote login off.

Usage: systemsetup -getremoteappleevents
	Display whether remote apple events are on or off.

Usage: systemsetup -setremoteappleevents <on off>
	Set remote apple events to either <on> or <off>.

Usage: systemsetup -getcomputername
	Display computer name.

Usage: systemsetup -setcomputername <computername>
	Set computer name to <computername>.

Usage: systemsetup -getlocalsubnetname
	Display local subnet name.

Usage: systemsetup -setlocalsubnetname <name>
	Set local subnet name to <name>.

Usage: systemsetup -getstartupdisk
	Display current startup disk.

Usage: systemsetup -setstartupdisk <disk>
	Set current startup disk to <disk>.

Usage: systemsetup -liststartupdisks
	List startup disks on this machine.

Usage: systemsetup -getwaitforstartupafterpowerfailure
	Get the number of seconds after which the computer will start up after a power failure.

Usage: systemsetup -setwaitforstartupafterpowerfailure <seconds>
	Set the number of seconds after which the computer will start up after a power failure. The <seconds> value must be a multiple of 30 seconds.

Usage: systemsetup -getdisablekeyboardwhenenclosurelockisengaged
 	Get whether or not the keyboard should be disabled when the X Serve enclosure lock is engaged.

Usage: systemsetup -setdisablekeyboardwhenenclosurelockisengaged <yes no>
 	Set whether or not the keyboard should be disabled when the X Serve enclosure lock is engaged.

Usage: systemsetup -version
	Display version of systemsetup tool.

Usage: systemsetup -help
	Display help.

Usage: systemsetup -printCommands
	Display commands.
```


**Tip:** Use `systemsetup -printCommands` to show the available commands.

```
❯ systemsetup -printCommands
systemsetup -getdate
systemsetup -setdate <mm:dd:yy>
systemsetup -gettime
systemsetup -settime <hh:mm:ss>
systemsetup -gettimezone
systemsetup -settimezone <timezone>
systemsetup -listtimezones
systemsetup -getusingnetworktime
systemsetup -setusingnetworktime <on off>
systemsetup -getnetworktimeserver
systemsetup -setnetworktimeserver <timeserver>
systemsetup -getsleep
systemsetup -setsleep <minutes>
systemsetup -getcomputersleep
systemsetup -setcomputersleep <minutes>
systemsetup -getdisplaysleep
systemsetup -setdisplaysleep <minutes>
systemsetup -getharddisksleep
systemsetup -setharddisksleep <minutes>
systemsetup -getwakeonmodem
systemsetup -setwakeonmodem <on off>
systemsetup -getwakeonnetworkaccess
systemsetup -setwakeonnetworkaccess <on off>
systemsetup -getrestartpowerfailure
systemsetup -setrestartpowerfailure <on off>
systemsetup -getrestartfreeze
systemsetup -setrestartfreeze <on off>
systemsetup -getallowpowerbuttontosleepcomputer
systemsetup -setallowpowerbuttontosleepcomputer <on off>
systemsetup -getremotelogin
systemsetup -setremotelogin <on off>
systemsetup -getremoteappleevents
systemsetup -setremoteappleevents <on off>
systemsetup -getcomputername
systemsetup -setcomputername <computername>
systemsetup -getlocalsubnetname
systemsetup -setlocalsubnetname <name>
systemsetup -getstartupdisk
systemsetup -setstartupdisk <disk>
systemsetup -liststartupdisks
systemsetup -getwaitforstartupafterpowerfailure
systemsetup -setwaitforstartupafterpowerfailure <seconds>
systemsetup -getdisablekeyboardwhenenclosurelockisengaged
systemsetup -setdisablekeyboardwhenenclosurelockisengaged <yes no>
systemsetup -version
systemsetup -help
systemsetup -printCommands
```
[systemsetup man page](https://developer.apple.com/library/mac/documentation/Darwin/Reference/ManPages/man8/systemsetup.8.html)


## tmutil
Time Machine utility

```
❯ tmutil
Usage: tmutil help <verb>

Usage: tmutil version

Usage: tmutil enable

Usage: tmutil disable

Usage: tmutil startbackup [-a | --auto] [-b | --block] [-r | --rotation] [-d | --destination dest_id]

Usage: tmutil stopbackup

Usage: tmutil enablelocal

Usage: tmutil disablelocal

Usage: tmutil snapshot

Usage: tmutil delete snapshot_path ...

Usage: tmutil restore [-v] src dst

Usage: tmutil compare [-a@esmugtndEX] [-D depth] [-I name]
       tmutil compare [-a@esmugtndEX] [-D depth] [-I name] snapshot_path
       tmutil compare [-a@esmugtndEUX] [-D depth] [-I name] path1 path2

Usage: tmutil setdestination [-a]  mount_point
       tmutil setdestination [-ap] afp://user[:pass]@host/share

Usage: tmutil removedestination destination_id

Usage: tmutil destinationinfo [-X]

Usage: tmutil addexclusion [-p] item ...

Usage: tmutil removeexclusion [-p] item ...

Usage: tmutil isexcluded item ...

Usage: tmutil inheritbackup machine_directory
       tmutil inheritbackup sparse_bundle

Usage: tmutil associatedisk [-a] mount_point volume_backup_directory

Usage: tmutil latestbackup

Usage: tmutil listbackups

Usage: tmutil machinedirectory

Usage: tmutil calculatedrift machine_directory

Usage: tmutil uniquesize path ...

Use `tmutil help <verb>` for more information about a specific verb.
```

[tmutil man page](https://developer.apple.com/library/mac/documentation/Darwin/Reference/ManPages/man8/tmutil.8.html)
