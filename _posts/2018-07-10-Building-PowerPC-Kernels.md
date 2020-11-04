---
layout: post
title: Building Linux Kernel for PowerPC
date:  2018-07-10 15:05:14 +0530
categories: kernel
author: linuxppc
tags: [powerpc, build, howto]
---

*A better rendered version of the 
[original wiki page](https://github.com/linuxppc/wiki/wiki/Building-powerpc-kernels)*

## Toolchain

If you're not lucky enough to have a powerpc laptop, you can build with a cross compiler.

Some distros ship a cross toolchain, otherwise you can use a tarball.

### Any distro

You can use the toolchains helpfully provided by [bootlin](https://toolchains.bootlin.com/).

```sh
cd /tmp
wget http://toolchains.free-electrons.com/downloads/releases/toolchains/powerpc64le-power8/tarballs/powerpc64le-power8--glibc--bleeding-edge-2017.05-toolchains-1-1.tar.bz2
tar -xf powerpc64le-power8--glibc--bleeding-edge-2017.05-toolchains-1-1.tar.bz2

wget http://toolchains.free-electrons.com/downloads/releases/toolchains/powerpc64-power8/tarballs/powerpc64-power8--glibc--bleeding-edge-2017.05-toolchains-1-1.tar.bz2
tar -xf powerpc64-power8--glibc--bleeding-edge-2017.05-toolchains-1-1.tar.bz2
```

Then for little endian:

    export CROSS_COMPILE=/tmp/powerpc64le-power8--glibc--bleeding-edge/bin/powerpc64le-linux-

or for big endian:

    export CROSS_COMPILE=/tmp/powerpc64-power8--glibc--bleeding-edge/bin/powerpc64-linux-

### Ubuntu

Install the cross-toolchain with:

    sudo apt-get install gcc-powerpc64le-linux-gnu gcc-powerpc-linux-gnu libc-dev-powerpc-cross libc-dev-ppc64el-cross

If you don't already have them installed, you also need `make gcc bc`.

Then for little endian:

    export CROSS_COMPILE=powerpc64le-linux-gnu-

or for big endian:

    export CROSS_COMPILE=powerpc-linux-gnu-

### Fedora

Install the cross-toolchain with:

    sudo dnf install gcc-c++-powerpc64-linux-gnu binutils-powerpc64-linux-gnu gcc-powerpc64-linux-gnu

Then for both endians:

    export CROSS_COMPILE=powerpc64-linux-gnu-

## Building

When cross-building you need to tell the kernel build system that you want to
build for the powerpc architecture, and tell it where your toolchain is. You can
do that by setting environment variables (as we'll show here), or on the `make`
command line.

To set the architecture use:

    export ARCH=powerpc

We also need to set the cross compiler. Depending on which one you're using, and
which endian you're building for it differs slightly. If you followed the
instructions above to install a toolchain, you've already done it by setting `CROSS_COMPILE`. If you
didn't follow the instructions above then you'll have to set `CROSS_COMPILE` to
the path of your cross compiler.

Then you can build the kernel for little endian with:

```sh
make powernv_defconfig        # or pseries_le_defconfig, or ppc64le_defconfig
make
```

Or for big endian with:

```sh
make ppc64_defconfig        # or pseries_defconfig, pmac32_defconfig etc.
make
```

For a faster build use:

    make -j $(nproc)
