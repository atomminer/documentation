# Software Requirements

AtomMiner software can and should run under most modern Linux distributions, or inside virtual Linux environment if native Linxu OS is not available for some reason.

## Host Computer Requirements

We have minimal requirements to the host computer with idea in mind that our control interface can be used on as many computers and/or controllers as possible. To be able to start mining with AtomMiner miners, host computer must have:

* internet connection (minimum recommended 2G+EDGE);
* x86, x86_64 (amd64), ARMv6 (hard floating point) or ARMv7 CPU;
* at least 128Mb of RAM with console or 256Mb with GUI;
* USB compatible host controller (USB2.0 or USB3.0 recommended);

!!! note ""
    We highly recommend to use Raspberry Pi (models 1, 2, 3, W and W Zero are supported right out of the box) or similar board as a dedicated miner controller to maintain 24/7 mining.


## Dependencies

Following libraries are required to run atomminer tools. All of them should be available from the default package manager.

* glibc (>=2.23)
* libstdc++ (>=3.4.21)
* libcurl3-gnutls (>=7.47)
* libusb-1.0 (>=1.0)

Detailed dependencies list output:
```
$ ldd atomminer-cli 
    linux-vdso.so.1 =>  (0x00007ffed99af000)
    libdl.so.2 => /lib/x86_64-linux-gnu/libdl.so.2 (0x00007f1521721000)
    libcurl-gnutls.so.4 => /usr/lib/x86_64-linux-gnu/libcurl-gnutls.so.4 (0x00007f15214b4000)
    libusb-1.0.so.0 => /lib/x86_64-linux-gnu/libusb-1.0.so.0 (0x00007f152129c000)
    librt.so.1 => /lib/x86_64-linux-gnu/librt.so.1 (0x00007f1521094000)
    libpthread.so.0 => /lib/x86_64-linux-gnu/libpthread.so.0 (0x00007f1520e77000)
    libstdc++.so.6 => /usr/lib/x86_64-linux-gnu/libstdc++.so.6 (0x00007f1520af5000)
    libgcc_s.so.1 => /lib/x86_64-linux-gnu/libgcc_s.so.1 (0x00007f15208df000)
    libc.so.6 => /lib/x86_64-linux-gnu/libc.so.6 (0x00007f1520515000)
    /lib64/ld-linux-x86-64.so.2 (0x00007f1521925000)
    libidn.so.11 => /usr/lib/x86_64-linux-gnu/libidn.so.11 (0x00007f15202e2000)
    librtmp.so.1 => /usr/lib/x86_64-linux-gnu/librtmp.so.1 (0x00007f15200c6000)
    libnettle.so.6 => /usr/lib/x86_64-linux-gnu/libnettle.so.6 (0x00007f151fe90000)
    libgnutls.so.30 => /usr/lib/x86_64-linux-gnu/libgnutls.so.30 (0x00007f151fb60000)
    libgssapi_krb5.so.2 => /usr/lib/x86_64-linux-gnu/libgssapi_krb5.so.2 (0x00007f151f916000)
    liblber-2.4.so.2 => /usr/lib/x86_64-linux-gnu/liblber-2.4.so.2 (0x00007f151f707000)
    libldap_r-2.4.so.2 => /usr/lib/x86_64-linux-gnu/libldap_r-2.4.so.2 (0x00007f151f4b6000)
    libz.so.1 => /lib/x86_64-linux-gnu/libz.so.1 (0x00007f151f29c000)
    libudev.so.1 => /lib/x86_64-linux-gnu/libudev.so.1 (0x00007f1521aff000)
    libm.so.6 => /lib/x86_64-linux-gnu/libm.so.6 (0x00007f151ef93000)
    libhogweed.so.4 => /usr/lib/x86_64-linux-gnu/libhogweed.so.4 (0x00007f151ed60000)
    libgmp.so.10 => /usr/lib/x86_64-linux-gnu/libgmp.so.10 (0x00007f151eae0000)
    libp11-kit.so.0 => /usr/lib/x86_64-linux-gnu/libp11-kit.so.0 (0x00007f151e87c000)
    libtasn1.so.6 => /usr/lib/x86_64-linux-gnu/libtasn1.so.6 (0x00007f151e669000)
    libkrb5.so.3 => /usr/lib/x86_64-linux-gnu/libkrb5.so.3 (0x00007f151e397000)
    libk5crypto.so.3 => /usr/lib/x86_64-linux-gnu/libk5crypto.so.3 (0x00007f151e168000)
    libcom_err.so.2 => /lib/x86_64-linux-gnu/libcom_err.so.2 (0x00007f151df64000)
    libkrb5support.so.0 => /usr/lib/x86_64-linux-gnu/libkrb5support.so.0 (0x00007f151dd59000)
    libresolv.so.2 => /lib/x86_64-linux-gnu/libresolv.so.2 (0x00007f151db3e000)
    libsasl2.so.2 => /usr/lib/x86_64-linux-gnu/libsasl2.so.2 (0x00007f151d923000)
    libgssapi.so.3 => /usr/lib/x86_64-linux-gnu/libgssapi.so.3 (0x00007f151d6e2000)
    libffi.so.6 => /usr/lib/x86_64-linux-gnu/libffi.so.6 (0x00007f151d4da000)
    libkeyutils.so.1 => /lib/x86_64-linux-gnu/libkeyutils.so.1 (0x00007f151d2d6000)
    libheimntlm.so.0 => /usr/lib/x86_64-linux-gnu/libheimntlm.so.0 (0x00007f151d0cd000)
    libkrb5.so.26 => /usr/lib/x86_64-linux-gnu/libkrb5.so.26 (0x00007f151ce43000)
    libasn1.so.8 => /usr/lib/x86_64-linux-gnu/libasn1.so.8 (0x00007f151cba1000)
    libhcrypto.so.4 => /usr/lib/x86_64-linux-gnu/libhcrypto.so.4 (0x00007f151c96e000)
    libroken.so.18 => /usr/lib/x86_64-linux-gnu/libroken.so.18 (0x00007f151c758000)
    libwind.so.0 => /usr/lib/x86_64-linux-gnu/libwind.so.0 (0x00007f151c52f000)
    libheimbase.so.1 => /usr/lib/x86_64-linux-gnu/libheimbase.so.1 (0x00007f151c320000)
    libhx509.so.5 => /usr/lib/x86_64-linux-gnu/libhx509.so.5 (0x00007f151c0d5000)
    libsqlite3.so.0 => /usr/lib/x86_64-linux-gnu/libsqlite3.so.0 (0x00007f151be00000)
    libcrypt.so.1 => /lib/x86_64-linux-gnu/libcrypt.so.1 (0x00007f151bbc8000)
```
