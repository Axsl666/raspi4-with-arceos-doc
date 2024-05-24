# 实验二：xhci 控制器初始化，接管控制权

## USB 初始化

通过Uboot启动ArceOS时，我们已经发现飞腾派的USB接口已经可以识别出我们插入的USB存储设备，并能从存储设备中读取下载ArceOS启动镜像。这是由于在Uboot引导阶段，关于USB主机控制器已经被初始化成功，并且会加载相应的一些驱动程序：USB 控制器驱动程序、USB 存储设备驱动程序等。所以关于主机控制器的初始化工作，我们可以暂时跳过，直接用Uboot已经初始化的控制器，只需在ArceOS中接管其控制权便可以管理USB了。

## 接管控制权

1. 加载ArceOS：通过SD卡等引导设备实现

2. ArceOS初始化：内核开始初始化硬件和各种子系统。在初始化过程中，会尝试检测和配置已经初始化的 USB 控制器。

   代码地址：<https://github.com/arceos-usb/arceos_experiment/tree/phytium_pi_port>

   从飞腾派软件编程手册V1.0中5.4.2关于USB寄存器基地址可知，USB基地址为：0x31A0_0000

   但是，注意 XHCI 协议规范定义寄存器基地址为USB3.0寄存器基地址+0x8000，所以最终基地址为0x31A0_8000

   因此，我们在尝试注册 xhci 控制器时，传入的地址为0x31A0_8000，



   ```rust
   fn test_xhci(_args: &str) {
       driver_usb::try_init(0x31a08000 as usize)
   }
   ```

   运行实例：

   ```shell
   arceos# test_xhci
   [ 31.922557 0:2 driver_usb::host::structures::registers:30] handleing!
   [ 31.927492 0:2 driver_usb::host::xhci:47] resetting xhci controller
   [ 31.934955 0:2 driver_usb::host::structures::registers:30] handleing!
   [ 31.942594 0:2 driver_usb::host::xhci:98] stop
   [ 31.948236 0:2 driver_usb::host::xhci:103] wait until halt
   [ 31.954920 0:2 driver_usb::host::xhci:105] halted
   [ 31.960822 0:2 driver_usb::host::xhci:107] HCRST!
   [ 31.966726 0:2 driver_usb::host::xhci:133] Reset xHCI Controller Globally
   [ 31.974710 0:2 driver_usb::host::structures::registers:30] handleing!
   [ 31.983446 0:2 driver_usb::host::structures::xhci_slot_manager:51] initialized!
   [ 31.990854 0:2 driver_usb::host::structures::xhci_event_manager:40] initilizating!
   [ 31.999621 0:2 driver_usb::host::structures::registers:30] handleing!
   [ 32.007293 0:2 driver_usb::host::structures::event_ring:33] created!
   [ 32.014812 0:2 driver_usb::host::structures::registers:30] handleing!
   [ 32.022450 0:2 driver_usb::host::structures::xhci_event_manager:53] test
   [ 32.030353 0:2 driver_usb::host::structures::xhci_event_manager:98] initialized!
   [ 32.038942 0:2 driver_usb::host::structures::registers:30] handleing!
   [ 32.046614 0:2 driver_usb::host::structures::registers:30] handleing!
   [ 32.054220 0:2 driver_usb::host::structures::xhci_command_manager:59] initialized!
   [ 32.062985 0:2 driver_usb::host::structures::registers:30] handleing!
   [ 32.070632 0:2 driver_usb::host::structures::scratchpad:54] initialized!
   [ 32.078523 0:2 driver_usb::host::structures::scratchpad:60] initialized!
   [ 32.086421 0:2 driver_usb::host::structures::registers:30] handleing!
   [ 32.094063 0:2 driver_usb::host::structures::roothub:84] initialized!
   [ 32.101698 0:2 driver_usb::host::structures::registers:30] handleing!
   [ 32.109337 0:2 driver_usb::host::structures::registers:30] handleing!
   [ 32.116975 0:2 driver_usb::host::xhci:65] init completed!, coltroller state:UsbStatusRegister { hc_halted: false, host_system_error: false, event_interrupt: 
   false, port_change_detect: true, save_state_status: false, restore_state_status: false, save_restore_error: false, controller_not_ready: false, 
   host_controller_error: false }
   ```




