# 实验一：PCIe初始化

PCIe控制器由Uboot初始化，会用到pci-generic-ecam这个驱动，这个驱动会在启动的时候检查控制器是否被初始化来决定要不要进行操作。

## 飞腾派Linux中关于 PCIe 部分

在飞腾派Linux系统中，输入```cat /proc/iomem```，得到如下输出：

```shell
user@Phytium-Pi:~$ sudo cat /proc/iomem
28000000-28000fff : 28000000.mmc mmc@28000000
28001000-28001fff : 28001000.mmc mmc@28001000
28005000-28005fff : 28009000.i2s i2s@28009000
28009000-28009fff : 28009000.i2s i2s@28009000
2800a000-2800afff : 2800a000.can can@2800a000
2800b000-2800bfff : 2800b000.can can@2800b000
2800c000-2800cfff : uart@2800c000
  2800c000-2800cfff : 2800c000.uart uart@2800c000
2800d000-2800dfff : uart@2800d000
  2800d000-2800dfff : 2800d000.uart uart@2800d000
2800e000-2800efff : uart@2800e000
  2800e000-2800efff : 2800e000.uart uart@2800e000
2800f000-2800ffff : uart@2800f000
  2800f000-2800ffff : 2800f000.uart uart@2800f000
28016000-28016fff : 28016000.i2c i2c@28016000
28024000-28024fff : 28024000.i2c i2c@28024000
28026000-28026fff : 28026000.i2c i2c@28026000
28030000-28030fff : 28030000.i2c i2c@28030000
28034000-28034fff : 28034000.gpio gpio@28034000
28035000-28035fff : 28035000.gpio gpio@28035000
28036000-28036fff : 28036000.gpio gpio@28036000
28037000-28037fff : 28037000.gpio gpio@28037000
28038000-28038fff : 28038000.gpio gpio@28038000
28039000-28039fff : 28039000.gpio gpio@28039000
2803a000-2803afff : 2803a000.spi spi@2803a000
28040000-28040fff : 28041000.watchdog watchdog@28040000
28041000-28041fff : 28041000.watchdog watchdog@28040000
28042000-28042fff : 28043000.watchdog watchdog@28042000
28043000-28043fff : 28043000.watchdog watchdog@28042000
2804a000-2804afff : 2804a000.pwm pwm@2804a000
2804b000-2804bfff : 2804b000.pwm pwm@2804b000
30000000-30000dff : 30000000.iommu
30010000-30010dff : 30000000.iommu
31a08000-31a1ffff : 31a08000.usb3 usb3@31a08000
31a28000-31a3ffff : 31a28000.usb3 usb3@31a28000
32000000-32007fff : 32000000.dc dc@32000000
32008000-32008fff : 32009000.i2s_dp0 i2s_dp0@32009000
32009000-32009fff : 32009000.i2s_dp0 i2s_dp0@32009000
3200c000-3200dfff : 3200c000.ethernet ethernet@3200c000
3200e000-3200ffff : 3200e000.ethernet ethernet@3200e000
32a00000-32a00fff : 32a00000.mailbox mailbox@32a00000
32a10000-32a11fff : 32a10000.sram sram@32a10000
32a36000-32a36fff : 32a36000.rng rng@32a36000
40000000-4fffffff : PCI ECAM
58000000-7fffffff : pcie@40000000
  58000000-581fffff : PCI Bus 0000:01
80000000-fbffffff : System RAM
  80000000-8000ffff : reserved
  90200000-913bffff : Kernel code
  913c0000-9160ffff : reserved
  91610000-917bffff : Kernel data
  e5c00000-f9bfffff : reserved
  f9c32000-f9c38fff : reserved
1000000000-1fffffffff : pcie@40000000
  1000000000-10000fffff : 0000:00:01.0
  1000100000-10002fffff : PCI Bus 0000:01
2000000000-207fffffff : System RAM
  207b000000-207effffff : reserved
  207f138000-207f197fff : reserved
  207f198000-207f798fff : reserved
  207f799000-207f7f4fff : reserved
  207f7f7000-207f7f9fff : reserved
  207f7fa000-207f7fafff : reserved
  207f7fb000-207f7fefff : reserved
  207f7ff000-207f81cfff : reserved
  207f81d000-207fffffff : reserved
```

* 由此```1000000000-1fffffffff : pcie@40000000```可以知道，

  `40000000` 是 PCIe 控制器的基地址。这个地址范围包含了 PCIe 控制器的寄存器，用来配置和控制 PCIe 总线。

* 由此 可以知道，

  ```shell
  1000000000-10000fffff : 0000:00:01.0
  1000100000-10002fffff : PCI Bus 0000:01
  ```

  `1000000000` 是 PCIe 总线的基地址。这个地址范围包含了连接到 PCIe 总线上的所有设备的地址范围。

  * **` 1000100000-10002fffff : PCI Bus 0000:01`：**
    * 表示 PCI Express 总线上的一个具体的子总线（Bus 0000:01）。PCI Express 总线通常包含多个子总线，每个子总线可能连接一个或多个设备。
    * 子总线的地址范围是从 `1000100000` 到 `10002fffff`。


  

## 关于 PCIe 总线的初始化


### 相关寄存器介绍


### 具体实例（Linux系统）


```shell
[    0.819462] pci-host-generic 40000000.pcie: host bridge /soc/pcie@40000000 ranges:
[    0.827065] pci-host-generic 40000000.pcie:    IO 0x50000000..0x50efffff -> 0x00000000
[    0.834988] pci-host-generic 40000000.pcie:   MEM 0x58000000..0x7fffffff -> 0x58000000
[    0.842907] pci-host-generic 40000000.pcie:   MEM 0x1000000000..0x1fffffffff -> 0x1000000000
[    0.851382] pci-host-generic 40000000.pcie: ECAM at [mem 0x40000000-0x4fffffff] for [bus 00-ff]
[    0.860167] pci-host-generic 40000000.pcie: PCI host bridge to bus 0000:00
[    0.867040] pci_bus 0000:00: root bus resource [bus 00-ff]
[    0.872525] pci_bus 0000:00: root bus resource [io  0x0000-0xefffff]
[    0.878876] pci_bus 0000:00: root bus resource [mem 0x58000000-0x7fffffff]
[    0.885748] pci_bus 0000:00: root bus resource [mem 0x1000000000-0x1fffffffff]
```
