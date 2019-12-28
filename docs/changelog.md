# Software Changelog

## Version 1.0.3RC6 released on 12/23/2019

<div markdown="1" class="row"><ul class="changelog-list">
<li>fixed unexpected crashes when mining at NOMP pools
<li>API server can be modified on the fly
<li>added API authentification
<li>added list of pools to API
<li>added a lot of API reporting calls
<li>added blockstamp algo support
<li>added tribus algo support
<li>added blake2s algo support
<li>added 'd1' profit estimation and switching algorithm
<li>fixed minor issues with local cache that could lead to occasional crashes
<li>improved stale share detection
</ul></div>

## Version 1.0.3RC5 released on 07/24/2019

<div markdown="1" class="row"><ul class="changelog-list">
<li>fixed odo to reduce amount of above target rejected shares
<li>fixed miner not picking up sha256t and sha256q algos on profits witcher
<li>fixed fimware versioning issue
<li>fixed various cache issues during software update
<li>added on-screen notification when new software version is available
</ul></div>

## Version 1.0.3RC4 released on 07/21/2019

<div markdown="1" class="row"><ul class="changelog-list">
<li>removed annoying warning when mining with alien setup
<li>on conf errors, software falls back to donate@atomminer.com until errors are fixed
<li>alien pool, if setup, has higher priority than anything else
<li>added support for client.reconnect command used by MRR and other services
<li>added custom DNS servers
<li>added compression and encryption to all API calls
<li>added support for NOMP based pools that don't follow stratum protocol
<li>alien pool address can include optional "stratum+tcp://"
<li>fixed groestl algo reporting wrong hashrate
<li>fixed problem when miner stalls on raspberry W Zero
<li>added myriad-groestl algo support
<li>added sha256t algo support
<li>added sha256q algo support
<li>added odocrypt algo support
<li>fixed algo version selection. newest available version of algo will be used
<li>few minor internal improvements
</ul></div>

## Version 1.0.3RC3 released on 06/01/2019

<div markdown="1" class="row"><ul class="changelog-list">
<li>added cpu and memory usage report to the CLI
<li>added '-clean' CLI command that will remove log and cache files
<li>added software selfupdate mechanism along with manual update
<li>old large log files are removed upon startup
<li>skein2 algo support
<li>gr0estl algo support
<li>sha256 algo support
<li>added 3rd party pools support
<li>added firmware/ folder rescan every 60 seconds to pick up manually downloaded or custom algo images
<li>optimized firmware updates to reduce internet traffic usage
<li>firmware cache moved to more logical cache/ subfolder
<li>fixed problem when cli is eating up all availbale system handles
<li>miners being automatically reprogrammed with newer firmware version when it is downloaded and verified
<li>fixed crash when firmware.cache is corrupted or has invalid data
<li>properly implemented '-program' cli command
<li>added help output for most of the cli commands
<li>added log to file conf option. currently unconditional logging is enabled for updates in log/update.log
<li>added rigname validation to only allow ^[A-Za-z0-9-_]+ names
<li>lots of internal improvements to lower CPU and RAM requirements
</ul></div>
