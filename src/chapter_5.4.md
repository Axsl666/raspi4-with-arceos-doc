# 实验一：PCIe 初始化，接管 PCIe 控制器

PCIe控制器由Uboot初始化。

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

* ```1000000000-1fffffffff : pcie@40000000```表示 PCIe 设备在系统地址空间中的分配。`40000000` 是 PCIe 设备的基址

* `1000000000-10000fffff` 是一个PCI设备的地址范围。`0000:00:01.0` 是PCIe设备的标识符，具体来说，`0000:00:01.0` 表示PCIe设备的域号、总线号、设备号和功能号。

  ` 1000100000-10002fffff `是另一个PCI设备的地址范围，`PCI Bus` 表示这是一个PCI总线设备，`0000:01` 表示PCI设备所在的总线号




## 接管控制权

1. 加载ArceOS:通过SD卡等引导设备实现

2. ArceOS初始化：内核开始初始化硬件和各种子系统。在初始化过程中，会尝试检测和配置已经初始化的PCIe控制器。

3. PCIe子系统初始化：当识别到PCIe控制器后，PCIe子系统会被初始化。其中包括
   * 设备检测
   * 资源分配
   * 设备驱动程序加载
