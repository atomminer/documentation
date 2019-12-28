# VMWare Installation

Pre-installed VMware image can be downloadede from official <a target="_blank" href="https://atomminer.com/downloads">Downloads</a>

!!! Note 
	Please consult with your legal adviser if you can operate free version of VMware for mining without violating their <a target="_blank" href="https://www.vmware.com/download/eula/universal_eula.html">EULA</a>

Steps here are provided for VMWare Workstation Player 15, but should be identical for other VMWare versions and products.

Hit Open a Virtual Machine and point it to downloaded .ova file:

![Screenshot](/img/vm-import.png)

hit import and agree to try relaxed OVF specification if prompted:

![Screenshot](/img/relaxed-import.png)

Once VM image is imported into the VM, you'll find atomminer_1.0.3RC3 in the virtual machines list:

![Screenshot](/img/vm-imported.png)

Power on the machine and let it boot:

![Screenshot](/img/vm-runninng.png)

## Settign up mining software

!!! Warning
	By default, VM is configured to mine to donate@atomminer.com email address. It is highly recommended that you change username to your registered email or setup anonymous wallets in the [configuration file](/software/config/) before connecting miners to it.

Miner's log screen is bound to Linux's default tty1 and login screen is on the tty2. SSH server is installed in the VM by default, but disabled for security reasons. It is **HIGHLY RECOMMENDED** to change default password before enabling SSH on the VM.

To switch between tty's you can hold down Alt key and use left or right arrows, or use `Alt + F1` for tty1 and `Alt + F2` for tty2.

Default login credentials:

```
login   : atomminer
password: atom
```

[Configuration file](/software/config/) is located at `/var/atomminer/atomminer.conf` easiest way to modify config file is to use nano

```
nano /var/atomminer/atomminer.conf
```

Once done changing atomminer.conf file, save and switch back to tty1 by hitting `Alt + F1` keys. Some settings in the config file can't be applied on-the-fly and requre miner restart. Restart the miner if prmpted. To restart mining software hit `Ctrl + C` while on the tty1 which will restart miner causing it to reload config settings.

## Connecting Miner(s)

Available USB devices are displayed as images in the bottom-right corner of VMWare. Find AM01 device and choose Connect. AM01 can be identified in different ways depending on your host OS. Known variations are "AM01", "AtomMiner AM01", "MCS", "MCS AM01", "16d0:0e1e". Windows OS is known to name AM01 devices in unpredicatable way.

Once connected, miner should be recognized by the VM and programmed by mining software as shown on the screenshot below

![Screenshot](/img/vm-miner-connected.png)

Once AM01 is connected, you should see device statistics including hashrate and device temperature along with accepted/rejected shares every once in a while:

![Screenshot](/img/vm-mining.png)