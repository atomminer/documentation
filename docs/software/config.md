Configuration file is required for correct operation of atomminer. Conf file is expected to be in valid JSON format. Miner will start mining random coin to our donation address 'donate@atomminer.com' (this email does not exist, please do not send us any communitcation there)

Upon startup, if no confi override is provided, miner is looking for valid conf file (atomminer.conf) in following order:

1. The same path `atomminer-cli` is located
2. `/var/atomminer/atomminer.conf` is attempted to load
3. Miner is trying to load `~/.atomminer/atomminer.conf` 

!!! Note
	If configuration fil contains errors or has invalid format or missing, miner will fall back to donation address.


### Configuration file override

It is supported to have conf file in any location. To point miner to the conf file, cimply add `-conf=path_to_conf` to the connamd line when starting it. You can control default location of miner's cache, log and firmware storage with `-datadir=path` command line switch

Following example will start the miner with config file named `my.conf` located in the home folder and use `am_data` folder to store firmware images, cahce files, logs etc.
```bash
$ atomminer-cli -conf=/home/atomminer/my.conf -datadir=/home/atomminer/am_data
```

### Minimal config file

It is sufficient to only supply your registered and activated email in the conf to start mining with all other settings at their default values:
```json
{"user": "donate@atomminer.com"}
```

### Full configuration file

Following is the config file with its default values:
```json
{
	"user": "donate@atomminer.com",
	"rigname": "",

	"logtofile": false,
	"logdebug": false,
	"logdevice": false,
	"report_connection_errors": false,

	"nodownload": false,
	"download_limit": 0,
	
	"report_hashrate": true,
	
	"smartconfig": true,
	"smartconfig_limit": 8,
	
	"coin_filter": "*",
	"profit_model": "",
		
	"alien_enable": false,
	"alien_algo": "",
	"alien_pool": "",
	"alien_user": "",
	"alien_pass": "",
		
	"proxy": "",
	
	"api": false,
	"api_bind": "0.0.0.0",
	"api_port": 9123,
	"apiuser": "",
	"apipass": "",

	"wallets" :[]
}

```

#### user

Type: `string`<br>
Default: `donate@atomminer.com`<br>
Validation: none<br>
Rgistered and activated AtomMiner's Online Wallet username. All mined coins will be credited to the owner of that registered email.

#### rigname

Type: `string`<br>
Default: empty string<br>
Validation: `^[A-Za-z0-9-_]+`<br>
Textual name of the miner. Will be displayed as 'worker name' on the pool. Does not affect anything, only providing easier way to identify your mining rigs. Allowed symbols: Latin letters a-z in either case, digits 0-9 and symbols '-' and '_'. All other symbols will be stripped out if used.

####  logtofile

Type: `bool`<br>
Default: `false`<br>
Validation: none<br>
Instructs miner to log errors, critical errors and crash debug info into file. File locations: `%datadir%/log/error.log` `%datadir%/log/crash.log`

####  logdebug

Type: `bool`<br>
Default: `false`<br>
Validation: none<br>
Instructs miner to provide more debug information on system status and events

####  logdevice

Type: `bool`<br>
Default: `false`<br>
Validation: none<br>
Instructs miner to provide more device related information in the logs

####  report_connection_errors

Type: `bool`<br>
Default: `false`<br>
Validation: none<br>
Instructs to print out warning when connection errors occur

####  nodownload

Type: `bool`<br>
Default: `false`<br>
Validation: none<br>
Prevent miner from downloading any updates, including new firmware and software updates

####  download_limit

Type: `int`<br>
Default: `0`<br>
Validation: none<br>
Limits download speed on firmware and software download. Speed limit is specified in KB/s. 0 = unlimited. Can be useful on the systems with slow internet like 2G networks.

####  report_hashrate

Type: `bool`<br>
Default: `true`<br>
Validation: none<br>
Tells miner to display hashrate and accepted/rejected shares from the pool in the log.

####  smartconfig

Type: `bool`<br>
Default: `true`<br>
Validation: none<br>
Only applies to a system with multiple AM01 miners connected. Allows semi-simultaneous physical miners reconfiguration which will reduce reconfiguration speed (when 2 or more miners used)

####  smartconfig_limit

Type: `int`<br>
Default: `8`<br>
Validation: none<br>
Miner will attempt to group miners for simultaneous config. This param indicates maximum group size. Software will analyze USB bus delays and other factors before reconfiguring miners. It is up to software to reduce maximum group size or even use one-by-one configuration if smart config won't provide significant speed advantage.

####  coin_filter

Type: `string`<br>
Default: `*`<br>
Validation: none<br>
This field controls which coins can be mined by the software. Default value of `*` allows miner to choose between all available coins on the pool. Mining algos that don't have firmware algo image will be ignored by the miner. Coins disable via CLI/API will be skipped as well. Coins are filtered by its symbol (ticker). Multiple coins should be separated by empty space. To disable a coin add '!' followed by coin ticker/symbol. It is recommended to leave `*` in the `coin_filter` string as it will allow mining software to pick up new coins when they are added to the pool.<br>
In case only 1 coin considered, you can use `MAX` for mining maxcoin only; or `MAX LOG OCP` to only allow switching between MAX, LOG and OCP coins.<br>
Due to numerous requests from our miners, value of `* !SLOTH` will disable SLOTH coin from coin selection:
```
"coin_filter": "* !SLOTH",
```
Multiple coins can be disabled in similar way: `* !SLOTH !OCP` will disable SLOTH and OCP coins.<br>
It is also possible to disable all coins and prevent miner from connecting to <a target="_blank" href="https://pool.atomminer.com">atomminer pool</a> if you're willing to use a 3rd party pool only.

####  profit_model

Type: `string`<br>
Default: empty<br>
Validation: none<br>
Profit estimation algorithm selection that affects device switching between coins and mining algos. Available options are `d1` (as of version 1.0.3RC) and anything else. D1 algo is using most coin params and elements of fuzzy logic to analyze coin performances and signal MiningManager to switch miners to more profitable coins. Any value other than `d1` will use flat profit estimation based on coin difficulty, block time and block reward.


####  alien_enable

Type: `bool`<br>
Default: `false`<br>
Validation: none<br>
Enables or disables 3rd party pool. By default, miner will keep mining on the 3rd party pool with fallback to default profit switching model if specified pool is going offline or disconnect happens. Please note, we don't have any control of any 3rd party pool and can not guarantee any uptime and or payouts made by them.

####  alien_algo

Type: `string`<br>
Default: empty string<br>
Validation: none<br>
Mining algo to be used with 3rd party pool

####  alien_pool

Type: `string`<br>
Default: empty string<br>
Validation: none<br>
Stratum URL for connecting to the pool. Only stratum based pools are supported! 'stratum+tcp://' is optional and could be omitted.

####  alien_user

Type: `string`<br>
Default: empty string<br>
Validation: none<br>
3rd party username as required by the pool

####  alien_pass

Type: `string`<br>
Default: empty string<br>
Validation: none<br>
Password as required by the 3rd party pool

####  api

Type: `bool`<br>
Default: `false`<br>
Validation: none<br>
Enable/Disable built-in API server

####  api_bind

Type: `string`<br>
Default: `0.0.0.0`<br>
Validation: none<br>
IP address of the network interface to bind API server to. Default `0.0.0.0` will make API server accessible from the network. Loopback adapter `127.0.0.1` will only allow API communitcation from local PC.

####  api_port

Type: `int`<br>
Default: `9123`<br>
Validation: none<br>
Local port number to start API server on

####  apiuser

Type: `string`<br>
Default: empty string<br>
Validation: none<br>
Username for API server authentification. If API Auth is not required, both `apiuser` and `apipass` should be empty strings

####  apipass

Type: `string`<br>
Default: empty string<br>
Validation: none<br>
API Auth password

####  wallets

Type: `array`<br>
Default: empty<br>
Validation: none<br>
Array of objects that can specify custom login string when using <a target="_blank" href="https://pool.atomminer.com">atomminer pool</a>. If you're using wallet override like shown in exaple belowm you're miner will not report any statistics under your main email address on the pool. These logins are treated as independent anonymous connections to the pool and not attached or associated with your profile in any way.
Following is the example that will make miner to mine SLOTH with anonymous wallet address and donate all BOOT coins to AtomMiner.
```json
"wallets" :[
	{"SLOTH":"SYX8G4fGaNr7TPCLBPD7HRoLbUF2ABPETT"},
	{"BOOT":"donate@atomminer.com"}
]
```

!!! Note
	Please do not mine SLOTH on SYX8G4fGaNr7TPCLBPD7HRoLbUF2ABPETT as you will not receive any reward mined on this address.