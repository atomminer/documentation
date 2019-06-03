It is recommended to use provided apt repository https://apt.atomminer.com/ with automatic install script and built-in upgrade mechanism to make sure all the required dependencies and libs are installed properly by your package manager.

| Arch | Type | sha1sum | Download |
| :---- | :---: | :---: | :------- |
| i386 | deb | a9182301b12a2325511cb34aca965ebb7683b748 | <a target="_blank" href="https://apt.atomminer.com//i386/atomminer-cli_1.0.3RC3_i386.deb">atomminer-cli_1.0.3RC3_i386.deb</a> |
| amd64 | deb | d6836995070ff3aec3018e26a6a5a1ce60b6fd17 | <a target="_blank" href="https://apt.atomminer.com//amd64/atomminer-cli_1.0.3RC3_amd64.deb">atomminer-cli_1.0.3RC3_amd64.deb</a> |
| armhf | deb | 84d1d1cfc7f2e7e49ac705db371e868c5e92b293 | <a target="_blank" href="https://apt.atomminer.com//armhf/atomminer-cli_1.0.3RC3_armhf.deb">atomminer-cli_1.0.3RC3_armhf.deb</a> |
| i386 | tar.gz | 6c09c5524ec49451c0b4add26b7adfed6111b6cc | <a target="_blank" href="https://apt.atomminer.com//i386/atomminer-cli_1.0.3RC3_i386.tar.gz">atomminer-cli_1.0.3RC3_i386.tar.gz</a> |
| amd64 | tar.gz | 53aa2ee824b5180d1db1a9b967d00225ff610a6a | <a target="_blank" href="https://apt.atomminer.com//amd64/atomminer-cli_1.0.3RC3_amd64.tar.gz">atomminer-cli_1.0.3RC3_amd64.tar.gz</a> |
| armhf | tar.gz | 7a366d6ab549f1eba83a0e2b4d542663b61037f2 | <a target="_blank" href="https://apt.atomminer.com//armhf/atomminer-cli_1.0.3RC3_armhf.tar.gz">atomminer-cli_1.0.3RC3_armhf.tar.gz</a> |


> All our .deb installer packages are signed with `EAAE802E` ID. It is always good idea to check installer signature before installing it if downloaded manually. Installer signature can be tested as follows: 
```
$ dpkg-sig -c atomminer-cli_1.0.2_amd64.deb
Processing atomminer-cli_1.0.2_amd64.deb...
GOODSIG _gpgrepo A9D00905E8A46F74B08526B9C2310688EAAE802E 1551689523
GOODSIG _gpgrepo0 A9D00905E8A46F74B08526B9C2310688EAAE802E 1551689531
```

We also provide pre-configured OS images. More detailed information about our custom-tailored OS you can find under [OS Section](/os/).

| VM | Arch | sha1sum | Download |
| :---- | :---: | :---: | :-- |
| OVA | 32bit x86 | f420f266f08be1bb803edd3ffcf7ee21193332fb | <a target="_blank" href="https://static.atomminer.com/os/atomminer_1.0.3RC3.ova">atomminer_1.0.3RC3.ova</a> |

Provided ova image is in Open Virtualization Format 1.0 and can be used with both VmWare and VirtualBox with or without VT-x/VT-d enabled in bios. Though it is highly recommended to enable Virtualization technology in BIOS, if available to improve overall VM performance

Please refer to VM setup instructions for more details:

* [VMWare](/software/vmware/)
* [Virtual Box](/software/vbox/)
