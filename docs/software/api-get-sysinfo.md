Returns system info.
 
HTTP GET:
```
$ curl localhost:9123/sysinfo
```
HTTP POST:
```
$ curl localhost:9123 --data-binary '{"cmd":"infosystem","params":[]}'
```
CLI:
```bash
$ atomminer-cli --raw info system
```

Response example:
```json
{
	"cpu": "4x2.4GHz",
	"arch": "x86_64",
	"platform": "linux 4.4.0-135-generic x86_64",
	"os": "Ubuntu 16.04.5 LTS",
	"ram": "7.60GB",
	"vram": "8.38GB",
	"timestamp": 1577370123,
	"vram_used": 3855486976,
	"vram_atom": 5492736,
	"ram_used": 6972715008,
	"ram_atom": 17186816,
	"cpu_all": 39.672852,
	"cpu_atom": 7.181873,
	"sw": "atomminer-cli v1.0.3RC6"
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
		<td>cpu</td>
		<td>string</td>
		<td>CPU type</td>
	</tr>
	<tr>
		<td>arch</td>
		<td>string</td>
		<td>CPU architecture</td>
	</tr>
	<tr>
		<td>platform</td>
		<td>string</td>
		<td>Platform name or description</td>
	</tr>
	<tr>
		<td>os</td>
		<td>string</td>
		<td>Operating System name, if known</td>
	</tr>
	<tr>
		<td>ram</td>
		<td>string</td>
		<td>Total RAM on the host PC</td>
	</tr>
	<tr>
		<td>vram</td>
		<td>string</td>
		<td>Total Virtual RAM</td>
	</tr>
	<tr>
		<td>timestamp</td>
		<td>int</td>
		<td>UNIX timestamp when current snapshot was taken</td>
	</tr>
	<tr>
		<td>vram_used</td>
		<td>int</td>
		<td>Total used Virtual RAM</td>
	</tr>
	<tr>
		<td>vram_atom</td>
		<td>int</td>
		<td>Virtual RAM used by AtomMiner</td>
	</tr>
	<tr>
		<td>ram_used</td>
		<td>int</td>
		<td>Total RAM used</td>
	</tr>
	<tr>
		<td>ram_atom</td>
		<td>int</td>
		<td>RAM used by AtomMiner</td>
	</tr>
	<tr>
		<td>cpu_all</td>
		<td>double</td>
		<td>Percentage of CPU load/usage</td>
	</tr>
	<tr>
		<td>cpu_atom</td>
		<td>double</td>
		<td>CPU usage by AtomMiner</td>
	</tr>
	<tr>
		<td>sw</td>
		<td>string</td>
		<td>Software name and version</td>
	</tr>
</table>