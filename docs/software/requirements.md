# Software Requirements

AtomMiner software can and should run under most modern Linux distributions, or inside virtual Linux environment if native Linxu OS is not available for some reason.

## Host Computer Requirements

We have designed software with the following minimal requirements for the host computer to make sure that our control interface can be used on as many computers and/or controllers as possible. To be able to start mining with AtomMiner miners, host computer must have:

* internet connection (minimum recommended 2G+EDGE);
* x86, x86_64 (amd64), ARMv6 (hard floating point) or ARMv7 CPU;
* 96Mb of RAM with console or 256Mb with GUI;
* USB compatible host controller (USB2.0 or USB3.0 recommended);

!!! note ""
    We highly recommend to use Raspberry Pi (models 1, 2, 3, W and W Zero are supported right out of the box) or similar board as a dedicated miner controller to maintain 24/7 mining.


## Dependencies

Following libraries are required to run atomminer tools. All of them should be available from the default package manager.

* glibc (>=2.23)
* libusb-1.0 (>=1.0)

Detailed dependencies list output:
```
$ ldd atomminer-cli 
    linux-vdso.so.1 =>  (0x00007fff53ce0000)
    librt.so.1 => /lib/x86_64-linux-gnu/librt.so.1 (0x00007fa31af94000)
    libusb-1.0.so.0 => /lib/x86_64-linux-gnu/libusb-1.0.so.0 (0x00007fa31ad7c000)
    libdl.so.2 => /lib/x86_64-linux-gnu/libdl.so.2 (0x00007fa31ab78000)
    libpthread.so.0 => /lib/x86_64-linux-gnu/libpthread.so.0 (0x00007fa31a95b000)
    libm.so.6 => /lib/x86_64-linux-gnu/libm.so.6 (0x00007fa31a652000)
    libc.so.6 => /lib/x86_64-linux-gnu/libc.so.6 (0x00007fa31a288000)
    /lib64/ld-linux-x86-64.so.2 (0x00007fa31b19c000)
    libudev.so.1 => /lib/x86_64-linux-gnu/libudev.so.1 (0x00007fa31b373000)
```
