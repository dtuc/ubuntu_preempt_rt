# ubuntu_preempt_rt
> Enable real-time capabilities of the Linux kernel.

This repository includes shell scripts to

* configure,
* compile and
* install

a Linux kernel patched with PREEMPT_RT for running real-time applications under Ubuntu Linux.

# Howto

1. Open up a terminal (STRG + ALT + T) and clone this repository `git clone ...`.
2. Run `sh configure.sh`. This will download the linux kernel, apply the PREEMPT_RT patch and overwrite the kernel configuration file with the correct settings for a fully preemptible kernel (`CONFIG_PREEMPT_RT_FULL=y`).
3. Run the compilation shell script: `sh compile.sh`.
4. Install the Debian packages: `sh install.sh`.

> Optional: If you want to adjust the kernel configuration change into the directory of the linux kernel (e.g. `cd linux-3.18.11-rt7`). Type `make menuconfig` to start the kernel configuration menu.

> Optional:  You may want to use your own kernel configuration file. For this, you need to uncomment the following line in `configure.sh`:

```
cp /boot/config-$(uname -r) .config
```

Comment out the following line:

```shell
cp rt-kernelconfig ${KERNEL}-rt/.config
```

Restart the configuration script:

```shell
sh configure.sh
```
