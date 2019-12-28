Returns list of known pools.
 
HTTP GET:
```
$ curl localhost:9123/pool
```
HTTP POST:
```
$ curl localhost:9123 --data-binary '{"cmd":"listpool","params":[]}'
```
CLI:
```bash
$ atomminer-cli --raw list pool
```

Response example:
```json
{
	"result": true,
	"error": null,
	"response": [{
		"algo": "skein2",
		"address": "skein2.pool.atomminer.com:7123",
		"lasterror": "",
		"coin": "LOG",
		"alien": false,
		"type": "stratum",
		"status": "Online",
		"diff": 0.100000,
		"profitability": 4.290223,
		"coindiff": 3206.694090,
		"online": true,
		"user": "donate@atomminer.com",
		"accepted": 888,
		"rejected": 0,
		"reconnects": 10
	}, {
		"algo": "keccak",
		"address": "keccak.pool.atomminer.com:5123",
		"lasterror": "",
		"coin": "SLOTH",
		"alien": false,
		"type": "stratum",
		"status": "Online",
		"diff": 256.000000,
		"profitability": 32.144139,
		"coindiff": 50.227412,
		"online": true,
		"user": "SYX8G4fGaNr7TPCLBPD7HRoLbUF2ABPETT",
		"accepted": 12203,
		"rejected": 0,
		"reconnects": 7
	},
	...<skipped>...
	]
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
		<td>List of firmware objects</td>
	</tr>
</table>

#### Firmware object fields

<table id="tbl1"	>
	<tr>
		<th>Field</th>
		<th>Type</th>
		<th>Description</th>
	</tr>
	<tr>
		<td>algo</td>
		<td>string</td>
		<td>Hashing algorithm</td>
	</tr>
	<tr>
		<td>address</td>
		<td>string</td>
		<td>Pool address</td>
	</tr>
	<tr>
		<td>lasterror</td>
		<td>string</td>
		<td>Last pool error, if any</td>
	</tr>
	<tr>
		<td>coin</td>
		<td>string</td>
		<td>Coin symbol or ticker</td>
	</tr>
	<tr>
		<td>alien</td>
		<td>bool</td>
		<td>Indicates if pool supports AtomMiner extensions</td>
	</tr>
	<tr>
		<td>type</td>
		<td>string</td>
		<td>Pool type. Currently supported: startum and cloud</td>
	</tr>
	<tr>
		<td>status</td>
		<td>string</td>
		<td>Human readable pool state/status</td>
	</tr>
	<tr>
		<td>diff</td>
		<td>double</td>
		<td>Current pool difficulty</td>
	</tr>
	<tr>
		<td>profitability</td>
		<td>double</td>
		<td>Calculated coin profitability</td>
	</tr>
	<tr>
		<td>coindiff</td>
		<td>double</td>
		<td>Global coin difficulty</td>
	</tr>
	<tr>
		<td>online</td>
		<td>bool</td>
		<td>Indicates if pool is connected and operationable</td>
	</tr>
	<tr>
		<td>user</td>
		<td>string</td>
		<td>Loging username</td>
	</tr>
	<tr>
		<td>accepted</td>
		<td>int</td>
		<td>Amount of accepted shares</td>
	</tr>
	<tr>
		<td>rejected</td>
		<td>int</td>
		<td>Amount of rejected shares</td>
	</tr>
	<tr>
		<td>reconnects</td>
		<td>int</td>
		<td>How many times pool was reconnected to</td>
	</tr>
</table>

