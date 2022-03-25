
## MT7603 with USB interface

this repo will deprecated while mt76 driver support mt7603 with usb interface.

### How to use

install linux-header

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

