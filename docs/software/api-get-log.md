Returns system info.
 
HTTP GET: 
```bash
$ curl localhost:9123/log?since=00000c88
```

HTTP POST:
```
$ curl localhost:9123 --data-binary '{"cmd":"log","params":["00000c88"]}'
```
CLI: 'N/A'

Response example:
```json
[{
	"tag": "debug",
	"message": "[2019-12-28 14:26:35] New job 3d received for PYE",
	"hash": "00000ce8"
}, {
	"tag": "",
	"message": "[2019-12-28 14:26:33] [SLOTH] Share A/R 20895/2 Accepted",
	"hash": "00000c8f"
}]
```

### Request fields

(optional) HTTP GET param `since` (first param in JSON params array) should be treated as mssages since. API call will return only log messages produced after the message identified via `since` hash.

### Response fields

<table id="tbl1">
	<tr>
		<th>Field</th>
		<th>Type</th>
		<th>Description</th>
	</tr>
	<tr>
		<td>tag</td>
		<td>string</td>
		<td>Log message category</td>
	</tr>
	<tr>
		<td>message</td>
		<td>string</td>
		<td>Log message string</td>
	</tr>
	<tr>
		<td>hash</td>
		<td>string</td>
		<td>Message hash ID. Can be used as `since` to receive newer messages after specified one</td>
	</tr>
</table>