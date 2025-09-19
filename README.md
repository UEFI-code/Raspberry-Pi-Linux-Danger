# Linux-Danger 6.6 for Raspberry Pi

See [Linux-Danger](https://github.com/UEFI-code/Linux-Danger) for details.

# ARM64 Hacking Status

I heard the fucking ARMv8 doesn't support EL1 syscall EL1 like x64...

And I'm lazy to hack libc

So I hacked the Page Table instead!

- Any page is RWX
- Usermode can touch physical-memory & MMIO directly
- `*sleep` syscall is `WFI` directly
- I deleted the fucking CFS-red-black-tree, cleaned bullshit with easy_sched

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

# Try this in your ELF

```c
#include <stdio.h>
#include <stdint.h>
uint8_t *phy_base = 0xffffff8000000000;
int main()
{
	printf("Read MMIO:0 @ %llx\n", phy_base);
	printf("0x%x\n", phy_base[0]);
}
```