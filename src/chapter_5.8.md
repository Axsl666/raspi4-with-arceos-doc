# 实验三：读取 USB 设备，并完成一个无线鼠标的设备驱动

1. **端口检测**：USB 3.0主机控制器会定期轮询每个端口，检测是否有设备连接。通过检查端口状态寄存器来完成，如果探测到了连接，控制器会进入设备探测阶段。

2. **设备探测**：一旦检测到连接，USB 3.0主机控制器会开始与设备进行通信，以确定其速度和协议。包括向设备发送探测信号，等待设备响应，并解析设备的描述符。

3. **设备速度确认**：在探测到设备后，USB 3.0主机控制器会与设备进行通信，确认其速度和所支持的USB规范版本（例如USB 2.0、USB 3.0等）。

4. **配置阶段**：一旦设备的速度和规范确认，USB 3.0主机控制器会向设备发送配置命令，并分配设备地址。包括配置端点和分配USB地址。

5. **设备驱动加载**：在设备被成功配置后，USB 3.0主机控制器会加载相应的设备驱动程序。

目前进展已经可以读取到插入的 USB 设备的各种描述符，包括设备描述符、配置描述符、接口描述符以及端点描述符，之后要进行的工作就是写四种通信通信协议，包括控制传输、批量传输、同步传输和中断传输。

尝试接入不同的 USB 设备，可以发现会读出不一样的厂商号和设备号，例如：

| USB设备     | vendor（厂商号） | product_id（设备号） |
| ----------- | ---------------- | -------------------- |
| U盘（aigo） | 2316             | 4096                 |
| 鼠标（罗技g502） | 1133             | 49291                 |
| 鼠标（罗技M650） | 1133             | 50504                 |
| 键盘（京东京造） | 1452             | 591                 |
| 无线手柄 | 121             | 294                 |
| 摄像头（U20-CAM-1080P） | 12943             | 115                 |

```shell
U盘（爱国者）：

[ 27.176312 0:2 driver_usb::host::structures::xhci_usb_device:163] dev descriptors: [Device(Device { len: 18, descriptor_type: 1, cd_usb: 512, class: 0, subclass: 0, protocol: 0, max_packet_size0: 64, vendor: 2316, product_id: 4096, device: 4352, manufacture: 1, product: 2, serial_number: 3, num_configurations: 1 })]

键盘（京东京造）:

[ 29.586200 0:2 driver_usb::host::structures::xhci_usb_device:163] dev descriptors: [Device(Device { len: 18, descriptor_type: 1, cd_usb: 512, class: 0, subclass: 0, protocol: 0, max_packet_size0: 64, vendor: 1452, product_id: 591, device: 259, manufacture: 1, product: 2, serial_number: 0, num_configurations: 1 })]

鼠标（罗技G502）：

[ 31.996362 0:2 driver_usb::host::structures::xhci_usb_device:163] dev descriptors: [Device(Device { len: 18, descriptor_type: 1, cd_usb: 512, class: 0, subclass: 0, protocol: 0, max_packet_size0: 64, vendor: 1133, product_id: 49291, device: 9987, manufacture: 1, product: 2, serial_number: 3, num_configurations: 1 })]

摄像头（U20-CAM-1080P）：

[ 34.983512 0:2 driver_usb::host::structures::xhci_usb_device:163] dev descriptors: [Device(Device { len: 18, descriptor_type: 1, cd_usb: 512, class: 239, subclass: 2, protocol: 1, max_packet_size0: 64, vendor: 12943, product_id: 115, device: 256, manufacture: 2, product: 1, serial_number: 3, num_configurations: 1 })]

无线手柄：

[ 29.809112 0:2 driver_usb::host::structures::xhci_usb_device:163] dev descriptors: [Device(Device { len: 18, descriptor_type: 1, cd_usb: 272, class: 0, subclass: 0, protocol: 0, max_packet_size0: 8, vendor: 121, product_id: 294, device: 4099, manufacture: 0, product: 2, serial_number: 0, num_configurations: 1 })]

无线鼠标（罗技M650）：

[ 31.094196 0:2 driver_usb::host::structures::xhci_usb_device:163] dev descriptors: [Device(Device { len: 18, descriptor_type: 1, cd_usb: 512, class: 0, subclass: 0, protocol: 0, max_packet_size0: 64, vendor: 1133, product_id: 50504, device: 1281, manufacture: 1, product: 2, serial_number: 0, num_configurations: 1 })]
```

