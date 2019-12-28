# Linux Installation

The easiest way to install latest version of AtomMiner control software would be to add https://apt.atomminer.com/ repository into your sources.list and let your 
package manager to handle the install.

## Addind Repository

The easiest way to add repository to your sources.list is to run following command:

`wget -q -O - https://apt.atomminer.com/add | sudo sh`

if you don't want to use automatic repository config script, you still can import repository key and add repositpry manually, following commands might be used:
```
$ wget -q -O - https://apt.atomminer.com/KEY.gpg | sudo apt-key add -
$ sudo add-apt-repository 'deb https://apt.atomminer.com /'
```

That's it!

## Install from Repository

Now you can install `atomminer-cli` with your system packet manager:

```
sudo apt-get install atomminer-cli
```

All files will be installed to `/var/atomminer/`. You can edit /var/atomminer/atomminer.conf with your credentials and start it by typing `atomminer-cli` in terminal.

### Manual Install

In case .deb installer was downloaded manually, you will need to install it using following command:

```
sudo dpkg -i atomminer-cli_1.0.3RC3_armhf.deb
```
replace `atomminer-cli_1.0.3RC3_armhf.deb` with the filename of the downloaded file.

### Generic Linux Install

It is recommended to have all files in /var/atomminer which is used by `atomminer-cli` by default. This folder can be changed to another location by adding alternative path, for instance `-data=/home/pi/myatommyner` which is described in [Configuration file](/software/cli) section.

From now on, we're assuming installation will be done to default location. Make sure current user has write permissions in `/var/atomminer/`. Unpack downloaded binaries for your architecture:
```
tar -xvf atomminer-cli_1.0.2_amd64.tar.gz
```

The directory layout if atomminer-cli install location is as follows:
```
.
├─ backup/				# rw
├─ cache/				# rw
├─ firmware/			# rw
├─ log/					# rw
├─ settings/			# rw
├─ atomminer.conf	    # rw  Refer to Configuration section
├─ atomminer 			# rwx Helper shell script
├─ atomminer-cli 		# rwx Main binary
├─ am-fwupdate 			# rwx Firmwate update utility 
├─ atomminer.png		# rw  Icon image 
```

atomminer-cli will need to have -rw- access to AM01 miners connected to USB port. By default, for security reasons Linux system will assign 660 permissions to newly connected USB devices. You will have an option to run atomminer-cli as superuser if running on minimal root-mode installation, which could potentially be a security threat, or to create a udev-based USB permission rule which assigns any custom permission mode of your choice.

Create file `/etc/udev/rules.d/88-atomminer.rules` with following text:

```
# AtomMiner USB driver for AM01 device (C) AtomMiner
# Rules written by AtomMiner ( atom@atomminer.com )
KERNEL=="*", SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", ACTION=="add", ATTR{idProduct}=="0e1e", ATTR{idVendor}=="16d0", MODE="0666", SYMLINK+="am01-%k"
```

Force udev to reload rules:
```
sudo udevadm control --reload-rules && udevadm trigger
```

you might want to unplug you miner and plug it back in to verify device permissions has changed the way you need them:

```
$ ls -la /dev/am01*
lrwxrwxrwx 1 root root 15 Apr  7 22:28 /dev/am01-1-1.1.1.1 -> bus/usb/001/007
lrwxrwxrwx 1 root root 15 Apr  7 22:28 /dev/am01-1-1.1.1.2 -> bus/usb/001/010
lrwxrwxrwx 1 root root 15 Apr  7 22:28 /dev/am01-1-1.1.1.3 -> bus/usb/001/014
lrwxrwxrwx 1 root root 15 Apr  7 22:28 /dev/am01-1-1.1.2.2 -> bus/usb/001/009
lrwxrwxrwx 1 root root 15 Apr  7 22:28 /dev/am01-1-1.1.2.3 -> bus/usb/001/012

$ls -la /dev/bus/usb/001/007
crw-rw-rw- 1 root root 189, 21 Apr  7 22:28 007
```