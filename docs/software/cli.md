It is important to understand 2 different calls availabel via cli:

* command line switches that starts with '-' symbol are affecting only the binary that is being started

* switches that don't have '-' symbol at the beginning will run requested command on the _remote_ running app via interna RPC and print out the results.

Exceptions: 
`help`, `conf`, `datadir` which are always treated as commands to be executed on the current binary and never being sent to running instance via RPC.

#### CLI Example of local and RPC call:

```atomminer-cli -ls``` will print out the list of miners that are connected to USB Bus: 
```bash
$ atomminer-cli -ls
AtomMiner CLI Miner 1.0.3RC6 
  -- built on Dec 28 2019 14:43:07 with x86_64 GCC 5.4.0 20160609

List of connected devices:
============================================================
USB:01. AtomMiner-AM01: 762563f99b2c37f8  Fw: 0.0.4.12 built on Jan  9 2019 01:39:07
============================================================

```
```atomminer-cli list device``` from another hand, will send command to the running instance of the miner and pull actual mining details from it:
```bash
$ atomminer-cli list device
AtomMiner CLI Miner 1.0.3RC6 
  -- built on Dec 28 2019 14:43:07 with x86_64 GCC 5.4.0 20160609

List of known devices:
[USB] 762563f99b2c37f8 Status: Working SLOTH (keccak) at 539.70Mh/s Expected: 540.00Mh/s
```

## Help command
List of available command can be retrieved by supplying `help` or `-h` for short:
```bash
atomminer-cli help
AtomMiner CLI Miner 1.0.3RC6 
  -- built on Dec 28 2019 14:43:07 with x86_64 GCC 5.4.0 20160609

More detailed info and examples are availabe at:
https://docs.atomminer.com/software/cli
https://docs.atomminer.com/software/integration

================ Local Commands ================
[-h] --help     Print this help.
[-v] --verbose  Forcing verbose output, providing extended info where available.
--raw           Prints out full RPC response in raw format.
--nodownload    Prevents miner from automatically downloading any updates.
-conf=PATH      Overrides default configration file.
-datadir=PATH   Overrides default data folder.

-checkupdates   Check for updates
-update         Install software updates [Deprecated as of 1.0.3RC6]

-ls        List connected devices
-resetall  Resets (power cycle) all connected AM01 devices.
-program   Program specified device(s) with algo. Use '-program help' for more info.

================ RPC Commands ================
status     Prints status of the running software miner
stop       Stop miner software
restart    Restart miern software

info [help] [system|device|firmware|pool
list  [help] [device|firmware|pool] [params]
reset [help] [device|firmware|pool] [params]
disable [help] [device|firmware|pool] [params]
enable [help] [device|firmware|pool] [params]
update [help] [firmware|software|all]

AtomMiner CLI v.1.0.3RC6 is already running with PID 13049.
   Status :  Running  with PID: 13049 for 00:18:35
   API srv:  On   at http://esdev:9123
   Cloud  :  Off 

```


!!! Note
	Update commands are disable as of version 1.0.3RC6 in favor to different auto-update approach. More info to be released soon


`-program`, `info`, `list`, `enable`, `disable` and `reset` commands have their own set of help descriptions and can be inspected supplying help switch to the command:
```bash
$ atomminer-cli list help
AtomMiner CLI Miner 1.0.3RC6 
  -- built on Dec 28 2019 14:43:07 with x86_64 GCC 5.4.0 20160609

More detailed info and examples are availabe at:
https://docs.atomminer.com/software/cli
https://docs.atomminer.com/software/integration

Request list of pools, firmware images or device from running miner. Command format:
atomminer-cli [options] list [device|firmware|pool]
   device   - prints device list similar to -ls cmd
   firmware - prints list of known firmware images
   pool     - prints list of known stratum pools

Options:
--verbose  - provide more detailed statistics of requested info.
--raw      - prints out raw json response.
```