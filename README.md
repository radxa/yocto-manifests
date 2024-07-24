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

## Example: Build ROCK 5B Machine

Get source code

```
$ mkdir ~/yocto-rockchip-sdk && cd ~/yocto-rockchip-sdk
$ repo init -u https://github.com/radxa/yocto-manifests.git -b master
$ repo sync
```

Link the local.conf to the target board configuration file.
Here we aim to build ROCK 5B machine, so the local.conf is linked to rockchip-rk3588-rock-5b.conf.
You should change the link when you build the other machine.

```
$ cd ~/yocto-rockchip-sdk/build/conf
$ ln -sf rockchip-rk3588-rock-5b.conf local.conf
$ ls -al local.conf
lrwxrwxrwx 1 radxa radxa 28 Jul 24 18:45 local.conf -> rockchip-rk3588-rock-5b.conf
```

Start build

```
$ cd ~/yocto-rockchip-sdk
$ source ./oe-init-build-env
$ bitbake core-image-minimal
```

## Maintainers

* Jeffy Chen `<jeffy.chen@rock-chips.com>`
* Stephen Chen `<stephen@radxa.com>`
