It is recommended to use provided apt repository https://apt.atomminer.com/ with automatic install script and built-in upgrade mechanism to make sure all the required dependencies and libs are installed properly by your package manager.

| Architecture | Type | sha1sum | Download |
| :--------- | :------: | :------: | :------ |
| i386 | deb | sig | link here |
| amd64 | deb | sig | link here |
| armhf | deb | sig | link here |
| i386 | tar.gz | sig | link here |
| amd64 | tar.gz | sig | link here |
| armhf | tar.gz | sig | link here |


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
| VBox | 32bit x86 | sig | link here |
| VBox | 64bit x64 | sig | link here |
| VMWare | 32bit x86 | sig | link here |
| VMware | 64bit x64 | sig | link here |
| LiveCD | 32bit x86 | sig | link here |
| LiveCD | 64bit x64 | sig | link here |