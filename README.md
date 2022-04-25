
## MT7603 with USB interface

driver version from `include/os/rt_linux.h` is `JEDI.L0.MP1.mt7603u.v1.14`

this repo will deprecated while mt76 driver support mt7603 with usb interface.

If you got kernel panic when loading this driver, force-reboot and give more try can have a better luck.

Please note, this driver based on old ralink vendor driver, unstable.Void Warry. May cause kernel panic when loading is known issue.

If you have usb wifi based on mt7603u and interest on this , feel free to test this driver , and let mt76 driver support mt7603u ASAP.

branch `mt76-03-usb` is based on mt76 driver clone from OpenWRT. But this branch didn't complete. Only have driver compiled, need real hardware to debug and fix.

branch `mt7601u` is fork from khadas in github. version is `JEDI.MP1.mt7601u.v1.11`. Due to upstream has been supported MT7601U, this branch only for reference and test patch.

### How to use

install linux-header

more USB ID can be add to `common/rtusb_dev_id.c`

place `conf/MT7603USTA.dat` to `/lib/firmware/MT7603USTA.dat`

```
git clone https://gitlab.com/ChalesYu/buildroot_platform_hardware_wifi_mtk_drivers_mt7603.git
cd buildroot_platform_hardware_wifi_mtk_drivers_mt7603/
git checkout pub-test-v20220304
make KSRC=/lib/modules/$(uname -r)/build -j2
sudo cp os/linux/mt7603usta.ko /lib/modules/$(uname -r)/kernel/drivers/net/wireless/
sudo depmod -a
sudo modprobe mt7603usta
```

and , maybe also need

```
service  NetworkManager restart
```

### Build for OpenWRT

use Makefile.backports as Makefile

