Returns system info.
 
HTTP GET: `N/A`

HTTP POST:
```
$ curl localhost:9123 --data-binary '{"cmd":"stop","params":[]}'
```
```
$ curl localhost:9123 --data-binary '{"cmd":"restart","params":[]}'
```
CLI:
```bash
$ atomminer-cli --raw stop
```
```bash
$ atomminer-cli --raw restart
```

Response example:
```json
{
	"result": true,
	"error": null,
	"response": [{"pid":26325}]
}
```

### Response fields

<table>
	<tr>
		<th>Field</th>
		<th>Type</th>
		<th>Description</th>
	</tr>
	<tr>
		<td>result</td>
		<td>bool</td>
		<td>Indicates whether `response` contains actual data</td>
	</tr>
	<tr>
		<td>error</td>
		<td>null or string</td>
		<td>`null` when response is present or error description otherwise</td>
	</tr>
	<tr>
		<td>response</td>
		<td>Array</td>
		<td>List of device objects</td>
	</tr>
	<tr>
		<td>pid</td>
		<td>int</td>
		<td>ID of the process that being stopped/restarted</td>
	</tr>
</table>