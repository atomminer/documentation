Returns list of known firmware algo images.
 
HTTP GET:
```
$ curl localhost:9123/firmware
```
HTTP POST:
```
$ curl localhost:9123 --data-binary '{"cmd":"listfirmware","params":[]}'
```
CLI:
```bash
$ atomminer-cli --raw list firmware
```

Response example:
```json
{
	"result": true,
	"error": null,
	"response": [{
		"tag": "0256414828bd7b1327767b0c2075242661e5dde7",
		"file": "0B0001005D21BD5A.img",
		"size": 2884317,
		"algo": "sha256q",
		"hashrate": 150000000,
		"version": "01.00",
		"status": 1,
		"progress": 0
	}, {
		"tag": "11bddc94735a0f86c8f1db571b891ed0accd294d",
		"file": "0D0001005DEAB2C6.img",
		"size": 2955487,
		"algo": "tribus",
		"hashrate": 25000000,
		"version": "01.00",
		"status": 1,
		"progress": 0
	},
	....<skippep>...
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
		<td>tag</td>
		<td>string</td>
		<td>Internal firmware ID</td>
	</tr>
	<tr>
		<td>file</td>
		<td>string</td>
		<td>Firmware filename on disk</td>
	</tr>
	<tr>
		<td>size</td>
		<td>int</td>
		<td>Size on disk in bytes</td>
	</tr>
	<tr>
		<td>algo</td>
		<td>string</td>
		<td>Hashing algorithm</td>
	</tr>
	<tr>
		<td>hashrate</td>
		<td>int</td>
		<td>Expected hashrate. Can be 0 for unofficial and non-public firmware images</td>
	</tr>
	<tr>
		<td>version</td>
		<td>string</td>
		<td>Hashing algo version</td>
	</tr>
	<tr>
		<td>status</td>
		<td>int</td>
		<td>Firmware status</td>
	</tr>
	<tr>
		<td>progress</td>
		<td>int</td>
		<td>Download progress or 0 for downloaded images**</td>
	</tr>
</table>

Firmware status is declared as following:
```c++
enum FwStatus {
    FwUnknown = 0,
    FwReady = 1,
    FwInvalid = 2,
    FwDownloading = 3,
    FwRemoteNew = 4,
};
```

** `progress` is holding current percentage if firmware status is FwDownloading. Progress value is 100*percent. Example: `"progress":3478` stands for 34.78% of image has been downloaded.