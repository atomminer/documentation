# Known Software Issues and/or problems

This section lists all known major and minor issues along with ways to fix them and various workarounds.
Please dont forget to upgrade to the latest software version (1.0.3RC6).

??? question "atomminer-cli 1.0.3RC5 install failure"
	**Symptoms**

	atomminer-cli v1.0.3RC5 installer failed with error but software has been installed and works as usual

	**Cause**
  	
  	We've discovered technical issues that could stop installer from finishing up correctly after install is actually finished. 

	**Resolution**

	This problem has been fixed in 1.0.3RC6. Please update/upgrade/reinstall atomminer-cli to remove apt-get warnings.


??? question "Upgrade to 1.0.3RC6 fails due to atomminer-cli 1.0.3RC5 uninstall error"
	**Symptoms**

	`sudo apt remove atomminer-cli` and `sudo apt install atomminer-cli` fails with error when removing or reinstalling or upgrading software version 1.0.3RC5

	**Cause**
  	
  	Problem is caused by the uninstall script that may return wrong value under certain conditions (known arch: armhf, arm64). This makes OS (typically debian 8 and debian 9) think that uninstall process has failed.

	**Resolution**

	Override return value of the uninstall aux script then perform actual uninstall before installing newer software version:
	```
	sudo echo "exit 0" > /var/lib/dpkg/info/atomminer-cli.prerm
	sudo apt remove --purge atomminer-cli
	```


