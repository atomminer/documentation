API server acts like hybrid HTTP json server and can accept either GET requests for certain endpoints or JSON POST commands for all available options. All API calls are available via cli even if API server is disabled.

## API Default Behavior

By default, API server is on and set to start on local port 9123 binding to ip 0.0.0.0 with authentification disabled. API server can be turned off by setting `api` value to false in the config file. API server can be turned on/off without app restart simply by editing config file.

`apibind` can be changed to a specific network IP interface if API visibility must be limited. 

!!! Note 
	`apibind` set to 127.0.0.1 will make API accessible only from localhost and restrict access to API from outside network.

In case 9123 is being used, `apiport` can be used to specify port API should start on.

API can be setup to request login/password as well via `apiuser`/`apipass` settings. As an authentification method we're using traditional HTTP basic access authentication i.e. API server expects Authorization provided among HTTP headers as required by <a target="_blank" href="https://tools.ietf.org/html/rfc7235">RFC7235 - HTTP/1.1: Authentication</a>

CLI will return human readable command output unless `--raw` switch specified: The best way to read JSON from api call is to append command line with `| sed '1,/^\s*$/d'` like following:
```bash
$ atomminer-cli status
AtomMiner CLI Miner 1.0.3RC6 
  -- built on Dec 24 2019 12:50:13 with x86_64 GCC 5.4.0 20160609

AtomMiner CLI v.1.0.3RC6 is already running with PID 26325.
   Status :  Running  with PID: 26325 for 5 days 130:03:26
   API srv:  On   at http://esdev:9123
   Cloud  :  Off 

```
versus
```bash
$ atomminer-cli --raw status
AtomMiner CLI Miner 1.0.3RC6 
  -- built on Dec 24 2019 12:50:13 with x86_64 GCC 5.4.0 20160609

{"result":true,"error":null,"response":[{"status":"Running","running":true,"pid":26325,"version":"1.0.3RC6","api":true,"api_port":9123,"api_bind":"0.0.0.0","www":false,"www_port":0,"www_bind":"","uptime":468122}]}
```
versus
```bash
$ atomminer-cli --raw status | sed '1,/^\s*$/d'
{"result":true,"error":null,"response":[{"status":"Running","running":true,"pid":26325,"version":"1.0.3RC6","api":true,"api_port":9123,"api_bind":"0.0.0.0","www":false,"www_port":0,"www_bind":"","uptime":468122}]}
```

## HTTP GET Endpoints

HTTP GET endpoints provided for backward compatibility with older software versions. Please use POST calls instead

| Endpoint | Description | Params |
|---	|---	|---	|
| [/device](/software/api-get-device) | List of connected devices | none | 
| [/firmware](/software/api-get-firmware) | List of available mining algo images | none |
| [/pool](/software/api-get-pool) | List of known pools | none |
| [/sysinfo](/software/api-get-sysinfo) | Provides system information about the host system | none |
| [/stats](/software/api-get-stats) | Provides mining statistics | none |
| [/log](/software/api-get-log) | Returns mining log | `since` - optional |
| [/stats](/software/api-get-stats) | Global app stats |
| / | Only accept POST commands. Returns warning on GET request | none |



