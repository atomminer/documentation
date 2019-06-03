# Software Changelog

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
