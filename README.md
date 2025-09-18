# Linux-Danger 6.6 for Raspberry-Pi

# Build

https://www.raspberrypi.com/documentation/computers/linux_kernel.html

```
KERNEL=kernel8
make ARCH=arm64 CROSS_COMPILE=aarch64-linux-gnu- bcm2711_defconfig
```

```
KERNEL=kernel_2712
make ARCH=arm64 CROSS_COMPILE=aarch64-linux-gnu- bcm2712_defconfig
```

```
qemu-system-aarch64 -machine raspi4b -cpu cortex-a72 -dtb bcm2711-rpi-4-b.dtb -kernel piImage -append "earlyprintk loglevel=8"
```