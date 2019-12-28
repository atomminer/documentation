Returns system info.
 
HTTP GET:
```
$ curl localhost:9123/stats
```
HTTP POST: `N/A` <br>
CLI: `N/A`

Response example:
```json
{
	"version": "AtomMiner CLI 1.0.3RC6",
	"status": "Ready",
	"miners": 2,
	"uptime": 463427,
	"pid": 26325,
	"online": false,
	"cloud": false,
	"coins": "SLOTH,LOG",
	"accepted": 396374,
	"rejected": 1,
	"ram": 17186816,
	"cpu": 7.295731
}
```

<table id="tbl1">
	<tr>
		<th>Field</th>
		<th>Type</th>
		<th>Description</th>
	</tr>
	<tr>
		<td>version</td>
		<td>string</td>
		<td>Software version</td>
	</tr>
	<tr>
		<td>status</td>
		<td>string</td>
		<td>Current status</td>
	</tr>
	<tr>
		<td>miners</td>
		<td>int</td>
		<td>Amount of known/connected miners</td>
	</tr>
	<tr>
		<td>uptime</td>
		<td>int</td>
		<td>App uptime in seconds</td>
	</tr>
	<tr>
		<td>pid</td>
		<td>int</td>
		<td>PID of the process</td>
	</tr>
	<tr>
		<td>online</td>
		<td>bool</td>
		<td>Indicates if software is online</td>
	</tr>
	<tr>
		<td>cloud</td>
		<td>bool</td>
		<td>Cloud connection status</td>
	</tr>
	<tr>
		<td>coins</td>
		<td>string</td>
		<td>List of currently mined coins</td>
	</tr>
	<tr>
		<td>accepted</td>
		<td>int</td>
		<td>Amount of accepted shares (global)</td>
	</tr>
	<tr>
		<td>rejected</td>
		<td>int</td>
		<td>Amount of rejected shares (global)</td>
	</tr>
	<tr>
		<td>ram</td>
		<td>int</td>
		<td>AtomMiner RAM usage</td>
	</tr>
	<tr>
		<td>cpu</td>
		<td>double</td>
		<td>AtomMiner CPU usage</td>
	</tr>
</table>