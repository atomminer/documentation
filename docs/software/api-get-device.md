Returns list of known and connected miners. 
 
HTTP GET:
```bash
$ curl localhost:9123/device
```
HTTP POST:
```bash
$ curl localhost:9123 --data-binary '{"cmd":"listdevice","params":[]}'
```
CLI:
```bash
$ atomminer-cli --raw list device
```

Response example:

```json
{
	"result": true,
	"error": null,
	"response": [{
		"serial": "76*************8",
		"type": "USB",
		"name": "AM01",
		"version": "0.0.4.12",
		"firmware": "1.3",
		"lasterror": "",
		"working": true,
		"status": "Working",
		"allocation": "SLOTH",
		"algo": "keccak",
		"hashrate": 539636541.563268,
		"expected": 540000000.000000,
		"temp": 51.090387,
		"vcc": 0.989182,
		"vccaux": 1.779190,
		"power": 0,
		"accepted": 0,
		"rejected": 0,
		"hw": 0,
		"uptime": 364419
	},
	{
		"serial": "03*************a",
		"type": "USB",
		"name": "AM01",
		"version": "0.0.4.12",
		"firmware": "1.1",
		"lasterror": "",
		"working": true,
		"status": "Working",
		"allocation": "BZL",
		"algo": "tribus",
		"hashrate": 25365356.346721,
		"expected": 25000000.000000,
		"temp": 39.87436,
		"vcc": 1.001282,
		"vccaux": 1.783261,
		"power": 900,
		"accepted": 0,
		"rejected": 0,
		"hw": 0,
		"uptime": 124425
	}]
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
</table>

#### Device object fields

<table id="tbl1"	>
	<tr>
		<th>Field</th>
		<th>Type</th>
		<th>Description</th>
	</tr>
	<tr>
		<td>serial</td>
		<td>string</td>
		<td>Device serial number</td>
	</tr>
	<tr>
		<td>type</td>
		<td>string</td>
		<td>Device connection type. Currently only USB devices supported</td>
	</tr>
	<tr>
		<td>name</td>
		<td>string</td>
		<td>User-friendly device name</td>
	</tr>
	<tr>
		<td>version</td>
		<td>string</td>
		<td>Device hardware version</td>
	</tr>
	<tr>
		<td>firmware</td>
		<td>string</td>
		<td>Mining algo version</td>
	</tr>
	<tr>
		<td>lasterror</td>
		<td>string</td>
		<td>Last device error or empty string</td>
	</tr>
	<tr>
		<td>working</td>
		<td>bool</td>
		<td>Indicates if device is hashing at the request time</td>
	</tr>
	<tr>
		<td>status</td>
		<td>string</td>
		<td>User-friendly device status</td>
	</tr>
	<tr>
		<td>allocation</td>
		<td>string</td>
		<td>Coin symbol this device is currently allocated to</td>
	</tr>
	<tr>
		<td>algo</td>
		<td>string</td>
		<td>Mining algorithm name</td>
	</tr>
	<tr>
		<td>hashrate</td>
		<td>double</td>
		<td>Current device hashrate in h/s</td>
	</tr>
	<tr>
		<td>expected</td>
		<td>double</td>
		<td>Expected device hashrate in h/s</td>
	</tr>
	<tr>
		<td>temp</td>
		<td>double</td>
		<td>Current device temperature, degrees Celsius</td>
	</tr>
	<tr>
		<td>vcc</td>
		<td>double</td>
		<td>Current core voltage, V</td>
	</tr>
	<tr>
		<td>vccaux</td>
		<td>double</td>
		<td>Current auxilary voltage, V </td>
	</tr>
	<tr>
		<td>power</td>
		<td>double</td>
		<td>Reserved for future use. Current device power consumption, W</td>
	</tr>
	<tr>
		<td>accepted</td>
		<td>int</td>
		<td>Amount of correct solutions accepted by the pool</td>
	</tr>
	<tr>
		<td>rejected</td>
		<td>int</td>
		<td>Amount of correct solutiosn rejected by the pool</td>
	</tr>
	<tr>
		<td>hw</td>
		<td>int</td>
		<td>Amount of hardware errors. Note: device will be reset automatically if hardware errors excceds internal threshold</td>
	</tr>
	<tr>
		<td>uptime</td>
		<td>int</td>
		<td>Seconds since device last reboot or reconfiguration</td>
	</tr>
</table>