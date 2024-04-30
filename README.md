## Raspberry Pi Kernel Builder 

Building and installing scripts based on the Docker image created by Xose Pérez (https://github.com/xoseperez/pi-kernel), incorporating the excellent scripts created by RonR (https://forums.raspberrypi.com/memberlist.php?mode=viewprofile&u=186692) from the Raspberry Pi Forums message https://forums.raspberrypi.com/viewtopic.php?t=360054

This environment can be used to [cross-compile the Raspberry Pi OS kernel](https://www.raspberrypi.org/documentation/linux/kernel/building.md) from a Linux, Windows, or Mac workstation using Docker.

This image has been successfully run to build and install a custom Linux kernel + modules on an RPi5 device.

## Bringing up the build environment

  1. Make sure Docker is installed.
  1. Build and run the docker image we will use for compilation: `./builder`

You will be dropped into a shell inside the container's `/build` directory with only the `make` script.. From here you can work on compiling the kernel.

> After you `exit` out of that shell, the Docker container will stop, but will not be removed. If you want to jump back into it, you can run `docker start cross-compile` and `docker attach cross-compile`.

> Also, the output of the built process will be available under `.build` folder.

## Compiling the Kernel

1. Within the Docker shell, run the 'build-kernel' script:

```
./build-kernel
```

A series of questions will be asked, answer them as you need to.

## Installing the Kernel

1. The output .zip file from the build of the RPi kernel will be in /root/<kernel-version-postfix>.zip, copy this file and the 'install-kernel' file to your RPi board (hint: sshfs can be used), then as root run the install file:

```
./install-kernel <kernel-version-postfix>.zip
```

## Full instructions
Full instructions on using this Docker image can be found at:

http://wifidiving.substack.com/rpi5-redux

