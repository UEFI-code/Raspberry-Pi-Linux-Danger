# Linux-Danger 6.6 for Raspberry-Pi

# Build

https://www.raspberrypi.com/documentation/computers/linux_kernel.html

```
cd linux
KERNEL=kernel8
make ARCH=arm64 CROSS_COMPILE=aarch64-linux-gnu- bcm2711_defconfig
```

```
cd linux
KERNEL=kernel_2712
make ARCH=arm64 CROSS_COMPILE=aarch64-linux-gnu- bcm2712_defconfig
```