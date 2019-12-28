It is recommended to use provided apt repository https://apt.atomminer.com/ with automatic install script and built-in upgrade mechanism to make sure all the required dependencies and libs are installed properly by your package manager. Manual download and install is available via .deb installer script as well.


> All our .deb installer packages are signed with `EAAE802E` ID. It is always good idea to check installer signature before installing it if downloaded manually. Installer signature can be tested as follows: 
```
$ dpkg-sig -c atomminer-cli_1.0.2_amd64.deb
Processing atomminer-cli_1.0.2_amd64.deb...
GOODSIG _gpgrepo A9D00905E8A46F74B08526B9C2310688EAAE802E 1551689523
GOODSIG _gpgrepo0 A9D00905E8A46F74B08526B9C2310688EAAE802E 1551689531
```

We also provide pre-configured OS images. More detailed information about our custom-tailored OS you can find under [OS Section](/os/).

OS Image can be downloaded from main Downloads page at https://atomminer.com/downloads

Provided ova image is in Open Virtualization Format 1.0 and can be used with both VmWare and VirtualBox with or without VT-x/VT-d enabled in bios. Though it is highly recommended to enable Virtualization technology in BIOS, if available to improve overall VM performance

Please refer to VM setup instructions for more details:

* [VMWare](/software/vmware/)
* [Virtual Box](/software/vbox/)
