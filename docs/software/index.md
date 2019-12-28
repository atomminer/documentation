# Quick Start Guide

Current Software Version: `1.0.3RC6`

Control software is designed to run native under most modern Linux OS, while was tested unde Ubuntu and Debian distros: Ubuntu 16.04, Ubuntu 16.10, Ubuntu 17.04, Ubuntu 17.10, Ubuntu 18.04, Debian 8, Debian 9. Other distribution should work no as well, plese refer to [Requirements](/software/requirements) and [Installation](/software/install) sections for more details.

Other Operating Systems such as various Windows and MacOS verions can be used as well with Virtual Machine environment like VirtualBox or VMWare.

Control software is provided in form of compiled binaries for amd64, x86 and armhf architectures.

As of version 1.0.3, we're providing set of tools to operate your AtomMiner miners, which includes:

* `atomminer-cli` main software that will put your miners to work
* `am-fwupdate` firmware update utility 

## Intro

`atomminer-cli` comes pacakged with many features that, we hope, will make your minig operations more efficient and reliable. We constantly keep adding new features and implementing requests proposed by our users. We'll try to keep this project up to date most of the time.

Main software features (starting from 1.0.3):

* `atomminer-cli` automatically integrates with our mining pool https://pool.atomminer.com and provides you with firmware and coin updates in the real time. You will never have to watch which coins are still available and/or delisted. `atomminer-cli` will try to do its best to maximize your profits even in case of technical problems or maintenance on one of the pools;
* now you have the option to use our online wallet (still under development) or go with anonymous mining with automatic payout straight your wallet or your exchange account;
* new automatic failover algorithm working with all available pools: as long as there's at least 1 active connection alive, your miners will keep mining what's available while waiting for the main pool to reconnect;
* as of v.1.0.3, firmware images are delivered in complete auto-pilot mode with no restart required whatsoever;
* 99% of miner's functions can be controlled manually from [command line](/software/cli) or via [API calls](/software/api);
* reduced data usage and lowered requirements for minimal internet connection bandwidth in stratum mining mode;
* and many more...[changelog 1.0.3](/changelog)

## Application Repository

We're providing native application repository for Debian and Unbuntu based distributions for automated installation. Installation scripts and binaries for other Linux distributions or manual install can be found at https://apt.atomminer.com/

