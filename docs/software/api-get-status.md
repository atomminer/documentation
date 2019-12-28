Returns current app status.
 
HTTP GET: `N/A`

HTTP POST: 
```bash
$ curl localhost:9123 --data-binary '{"cmd":"status","params":[]}'
```

CLI: 
```bash
$ atomminer-cli status
```

Response example:
```json
{
	"result": true,
	"error": null,
	"response": [{
		"status": "Running",
		"running": true,
		"pid": 26325,
		"version": "1.0.3RC6",
		"api": true,
		"api_port": 9123,
		"api_bind": "0.0.0.0",
		"www": false,
		"www_port": 0,
		"www_bind": "",
		"uptime": 463445
	}]
}
```

### Response fields

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
		<td>running</td>
		<td>bool</td>
		<td>Indicates when app is online and working</td>
	</tr>
	<tr>
		<td>pid</td>
		<td>int</td>
		<td>PID of the process</td>
	</tr>
	<tr>
		<td>api</td>
		<td>bool</td>
		<td>Indicates if API server is running</td>
	</tr>
	<tr>
		<td>api_port</td>
		<td>int</td>
		<td>API server port</td>
	</tr>
	<tr>
		<td>api_bind</td>
		<td>string</td>
		<td>IP address API is bound to (default: 0.0.0.0)</td>
	</tr>
	<tr>
		<td>www</td>
		<td>bool</td>
		<td>Deprecated</td>
	</tr>
	<tr>
		<td>www_port</td>
		<td>int</td>
		<td>Deprecated</td>
	</tr>
	<tr>
		<td>www_bind</td>
		<td>string</td>
		<td>Deprecated</td>
	</tr>
	<tr>
		<td>uptime</td>
		<td>int</td>
		<td>App uptime in seconds</td>
	</tr>
</table>