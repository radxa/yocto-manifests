# Repository for rockchip yocto SDK

Yocto SDK for the Rockchip SOC boards  
  - wiki <http://opensource.rock-chips.com/wiki_Main_Page>.

## Quick Start

1. Get the code using the Manifest and Repo tool:  
     <https://source.android.com/setup/develop/repo>  
2. Config your local config file (build/conf/local.conf)
   * You can create a local.conf manually, follow:  
   *   <https://git.yoctoproject.org/cgit.cgi/poky/plain/meta-poky/conf/local.conf.sample>  
   * Or use the existing config files for demoing e.g.: rockchip-rk3326-evb.conf
3. Run "source ./oe-init-build-env" to setup bitbake environment
4. Run "bitbake core-image-minimal" to build the images
5. Flash the generated "build/tmp/deploy/\<MACHINE\>/update.img" to your device
6. Boot your device and enjoy it

## List of Radxa Boards supported

### RK3528A

* ROCK 2A
* ROCK 2F
* Radxa E20C

### RK3576

* ROCK 4D

### RK3588(S)

* ROCK 5A
* ROCK 5B
* ROCK 5B+
* ROCK 5C
* ROCK 5T
* ROCK 5 ITX
* Radxa CM5 IO
* Radxa CM5 + RPI CM4 IO
* Radxa NX5 IO
* Radxa E52C
* Radxa E54C

## Example: Build ROCK 5B Machine

### Get source code

```
$ mkdir ~/yocto-rockchip-sdk && cd ~/yocto-rockchip-sdk
$ repo init -u https://github.com/radxa/yocto-manifests.git -b scarthgap
$ repo sync
```

Link the local.conf to the target board configuration file.
Here we aim to build ROCK 5B machine, so the local.conf is linked to rockchip-rk3588-rock-5b.conf.
You should change the link when you build the other machine.

```
$ cd ~/yocto-rockchip-sdk/build/conf
$ ln -sf rockchip-rk3588-rock-5b.conf local.conf
$ ls -al local.conf
lrwxrwxrwx 1 radxa radxa 28 Nov 21 14:44 local.conf -> rockchip-rk3588-rock-5b.conf
```

### Start build

```
$ cd ~/yocto-rockchip-sdk
$ source ./oe-init-build-env
$ bitbake core-image-minimal
```

And you will get the target system image under `build/tmp/deploy/images/rockchip-rk3588-rock-5b/`.

There are two formats of system images. One is wic, `core-image-minimal-rockchip-rk3588-rock-5b.rootfs.wic`.
And the othe one is rkupdate, `core-image-minimal-rockchip-rk3588-rock-5b.rootfs.update.img`.

### Write the image

#### For eMMC

Choose image `core-image-minimal-rockchip-rk3588-rock-5b.rootfs.wic`.
Choose one of the following flash ways:
* [Install the system on the EMMC Module](https://docs.radxa.com/en/rock5/rock5b/getting-started/install-os/boot_from_emmc)
* [RKDevTool](https://docs.radxa.com/en/template/module/radxa-os/low-level-dev/rkdevtool)
* [rkdeveloptool](https://docs.radxa.com/en/template/module/radxa-os/low-level-dev/rkdeveloptool)

#### For MicroSD Card

Choose image `core-image-minimal-rockchip-rk3588-rock-5b.rootfs.update.img`.
You can refer to this guide, [Write the image to MicroSD Card with SDDiskTool](https://docs.radxa.com/en/rock5/rock5c/other-os/buildroot#write-the-image-to-microsd-card).

## Maintainers

* Jeffy Chen `<jeffy.chen@rock-chips.com>`
* Stephen Chen `<stephen@radxa.com>`
