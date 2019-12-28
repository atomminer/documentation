# Running Miner Software

Miner software is configured to start automatically on tty1 in the pre-configured Virtual Machine image, while you should start it manually on self-serviced Linux install.

Only one single running instance of the atomminer-cli is allowed at the time to prevent USB device misconfiguration and provide proper communication with minimal delays.

## Start miner

To start software just type in your terminal
```
atomminer-cli
```
If software can be started, it will start with the log similar to following:
```
~$ atomminer-cli
AtomMiner CLI Miner 1.0.3RC3 
  -- built on Jun  1 2019 18:59:15 with x86_64 GCC 5.4.0 20160609

 Running on   : linux 4.4.0-135-generic x86_64
 OS           : Ubuntu 16.04.5 LTS
 Virtual  RAM : 0kB/3.18GB/8.38GB
 Physical RAM : 4.66MB/6.04GB/7.60GB
 CPU          : 4x2.4GHz 0.00/21.68

[2019-06-03 10:53:24] + Starting miner...
[2019-06-03 10:53:24] + Starting Device Manager...
[2019-06-03 10:53:24] + Starting Pool manager...
[2019-06-03 10:53:24] + Running...waiting for a job from the pool
```
In case atomminer-cli is already running on this machine, information about running instance will be printed out: running process ID, uptime and whether API and/or WWW servers are started.
```
~$ atomminer-cli
AtomMiner CLI Miner 1.0.3RC6 
  -- built on Dec 21 2019 08:43:41 with x86_64 GCC 5.4.0 20160609

AtomMiner CLI v.1.0.3RC6 is already running with PID 26325.
   Status :  Running  with PID: 26325 for 2 days 53:46:42
   API srv:  On   at http://esdev:9123
   Cloud  :  Off
```

## Stop miner

To stop running instance of `atomminer-cli` you can add stop keyword to the cli. Example output: 
```
~$ atomminer-cli stop
AtomMiner CLI Miner 1.0.3RC3 
  -- built on Jun  1 2019 18:59:15 with x86_64 GCC 5.4.0 20160609

+ Stopped atomminer-cli with PID:19516
```  
in case there's no running instance found, output will be as follows:
```
~$ atomminer-cli stop
AtomMiner CLI Miner 1.0.3RC3 
  -- built on Jun  1 2019 18:59:15 with x86_64 GCC 5.4.0 20160609

AtomMiner CLI is not started. Please start the CLI and try again
```

## Autostart

There's multiple options of setting up atomminer-cli to start and begin mining on system startup at user's choice. Most popular choices are:
 * Create a symlink to user's autostart items. Cons: miner will not start until user is logged in
 * Create a system service that will start miner. Cons: will be started as root with no option to see real-time log
 * Add autostart via cron in terminal multiplexer

For simplicity, below are instructions on how to run have `atomminer-cli` to autostart with `screen` multiplexe and cron. First of all you will need `screen`to be installed as it is not default package in some linux distributions. To install screen on Debian based distro (Ubuntu, Raspbian, etc.):  
```
sudo apt-get install screen
```  
we've included autostart script with `atomminer-cli` for miner's convenience that will keep restarting cli if something bad happened or miner was accidentally stoped from another terminal. Helper script is located at `/var/atomminer/atomminer`. 
To use enable this script to be started at every system boot edit cron jobs by typing
```
crontab -e
```
in the opened editor add followinf line at the very bottom:
```
@reboot screen -dmS cli /var/atomminer/atomminer
```
save an exit. Now `/var/atomminer/atomminer` will be started in the named (background) terminal every time system boots up even if user is not logging in.

Upon login you can check if your screen has started:
```
pi@raspberrypi:~ $ screen -ls
There are screens on:
	4466.cli	(17/05/19 21:22:57)	(Detached)
1 Sockets in /run/screen/S-pi.
```

to attach to the named screen from the current terminal following command can be used:
```
screen -r cli
```
that should attach current terminal to the `cli` terminal runnin `atomminer-cli` and show real-time miner log