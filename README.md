YOCTO BSP for Samsung Artik
=====================

To get the BSP you need to have `repo` installed and use it as:

Install the `repo` utility:

```bash
$ mkdir ~/bin
$ curl http://commondatastorage.googleapis.com/git-repo-downloads/repo > ~/bin/repo
$ chmod a+x ~/bin/repo
```
Download the BSP source:

```bash
$ PATH=${PATH}:~/bin
$ mkdir yocto-artik
$ cd yocto-artik
$ repo init -u https://github.com/eunchurn/artik710-yocto-bsp-repo -b morty
$ repo sync
```

At the end of the commands you have every metadata you need to start work with.

To start a simple image build:

```bash
$ source ./setup-environment build
$ bitbake core-image-minimal
```
It takes 2 or 3 hours. You can use any directory to host your build.

In the meantime create two partitions on your microSD. You can use gparted on your Ubuntu PC.

| path    | file system |
|:-------:|:-----------:|
|  boot   |     ext4    |
|  rootfs |     ext4    |

At the end you will get the following files, copy tem into the microSD:

```bash
$ cd ~/yocto-artik/poky/build/tmp/deploy/images/artik710
$ sudo cp Image /media/boot/
$ sudo cp Image-s5p6818-artik710-raptor-rev00.dtb /media/boot/s5p6818-artik710-raptor-rev00.dtb
$ sudo cp Image-s5p6818-artik710-raptor-rev01.dtb /media/boot/s5p6818-artik710-raptor-rev01.dtb
$ sudo cp Image-s5p6818-artik710-raptor-rev03.dtb /media/boot/s5p6818-artik710-raptor-rev03.dtb
$ cp u-boot.bin /media/boot/
$ cp u-boot-artik710.bin /media/boot/
```
