# 实验一：飞腾派 Uboot 启动 USB

输入`usb start`后可以看到如下输出：

```shell
starting USB...
Bus usb3@31a00000: Register 2000110 NbrPorts 2
Starting the controller
USB XHCI 1.10
Bus usb3@31a20000: Register 2000110 NbrPorts 2
Starting the controller
USB XHCI 1.10
scanning bus usb3@31a00000 for devices... 1 USB Device(s) found
scanning bus usb3@31a20000 for devices... 1 USB Device(s) found
       scanning usb for storage devices... 0 Storage Device(s) found

```

发现共有两个USB设备被发现，为两个USB主机控制器

输入`usb tree`也可以看到：

```shell
Phytium-Pi#usb tree
USB device tree:
  1  Hub (5 Gb/s, 0mA)
     U-Boot XHCI Host Controller

  1  Hub (5 Gb/s, 0mA)
     U-Boot XHCI Host Controller
```

尝试插入USB设备如内存卡（注意Uboot只初始化了一个端口（上方的蓝色端口），其余端口无法通信），由于Uboot不支持动态加载，所以我们需要`usb reset`，重新启动USB，可以看到，可以检测出一个存储设备：

```shell
Phytium-Pi#usb reset
resetting USB...
Bus usb3@31a00000: Register 2000110 NbrPorts 2
Starting the controller
USB XHCI 1.10
Bus usb3@31a20000: Register 2000110 NbrPorts 2
Starting the controller
USB XHCI 1.10
scanning bus usb3@31a00000 for devices... 2 USB Device(s) found
scanning bus usb3@31a20000 for devices... 1 USB Device(s) found
       scanning usb for storage devices... 1 Storage Device(s) found

Phytium-Pi#usb tree
USB device tree:
  1  Hub (5 Gb/s, 0mA)
  |  U-Boot XHCI Host Controller
  |
  +-2  Mass Storage (5 Gb/s, 124mA)
       Prolific Technology Inc. USB SD Card Reader      ABCDEF0123456789AB

  1  Hub (5 Gb/s, 0mA)
     U-Boot XHCI Host Controller
```

再尝试插入其它的USB设备，同样可以检测到：

```shell
Phytium-Pi#usb reset
resetting USB...
Bus usb3@31a00000: Register 2000110 NbrPorts 2
Starting the controller
USB XHCI 1.10
Bus usb3@31a20000: Register 2000110 NbrPorts 2
Starting the controller
USB XHCI 1.10
scanning bus usb3@31a00000 for devices... 2 USB Device(s) found
scanning bus usb3@31a20000 for devices... 1 USB Device(s) found
       scanning usb for storage devices... 0 Storage Device(s) found
Phytium-Pi#usb tree
USB device tree:
  1  Hub (5 Gb/s, 0mA)
  |  U-Boot XHCI Host Controller
  |
  +-2  Human Interface (12 Mb/s, 100mA)
       Keychron Keychron C1   //  键盘

  1  Hub (5 Gb/s, 0mA)
     U-Boot XHCI Host Controller
```



```shell
Phytium-Pi#usb reset
resetting USB...
Bus usb3@31a00000: Register 2000110 NbrPorts 2
Starting the controller
USB XHCI 1.10
Bus usb3@31a20000: Register 2000110 NbrPorts 2
Starting the controller
USB XHCI 1.10
scanning bus usb3@31a00000 for devices... 2 USB Device(s) found
scanning bus usb3@31a20000 for devices... 1 USB Device(s) found
       scanning usb for storage devices... 0 Storage Device(s) found
Phytium-Pi#usb tree
USB device tree:
  1  Hub (5 Gb/s, 0mA)
  |  U-Boot XHCI Host Controller
  |
  +-2   (480 Mb/s, 500mA)
       EMEET HD Webcam eMeet C950 SN0001   //  摄像头

  1  Hub (5 Gb/s, 0mA)
     U-Boot XHCI Host Controller

```



