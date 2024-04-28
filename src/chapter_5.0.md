# 飞腾派运行ArceOS

1. 硬件准备：
   * 飞腾派板子
   
     ![image-20240427150305459](https://github.com/chenlongos/raspi4-with-arceos-doc/blob/master/src/assert/%E9%A3%9E%E8%85%BE%E6%B4%BE%E5%9B%BE%E7%89%87.jpg)
   
   * 两张SD卡，一张烧录好Ubuntu系统，一张放ArceOS启动镜像（或U盘）
   
   * 读卡器（或U盘）
   
   * USB转TTL串口线
   
   * ArceOS代码地址：https://github.com/arceos-usb/arceos_experiment/tree/phytium_pi_port（注意分支）
   
2. 飞腾派上电启动，把有ArceOS启动镜像的读卡器或者U盘插到飞腾派上，用串口把飞腾派与电脑相连接，启动电脑上的远程连接软件，如Putty，波特率设置为115200

   串口接法：接8、10、12号引脚位置，如图所示（8号代表TX，接RX；10号代表RX，接TX；12号接地线）

   ![image-20240427150400839](https://github.com/apengaaa/raspi4-with-arceos-doc/blob/master/src/assert/%E9%A3%9E%E8%85%BE%E6%B4%BE%E4%B8%B2%E5%8F%A3%E8%BF%9E%E6%8E%A5%E7%A4%BA%E6%84%8F%E5%9B%BE.jpg)

3. 在uboot倒计时结束前按任意键进入手动引导
   * 输入`usb start` ,启用USB驱动来识别插入的USB设备（读卡器/U盘）
   
     ![image-20240427145830692](https://github.com/apengaaa/raspi4-with-arceos-doc/blob/master/src/assert/%E9%A3%9E%E8%85%BE%E6%B4%BE%E5%90%AF%E5%8A%A8ArceOS-1.png)
   
   * 输入`fatload usb 0 0x90100000 cli_aarch64-phytium-pi.bin`，从插入的USB设备（读卡器/U盘）上下载ArceOS镜像
   
     ![image-20240427145929621](https://github.com/apengaaa/raspi4-with-arceos-doc/blob/master/src/assert/%E9%A3%9E%E8%85%BE%E6%B4%BE%E5%90%AF%E5%8A%A8ArceOS-2.png)
   
   * 输入`go 0x90100000`加载ArceOS镜像
   
     ![image-20240427150034220](https://github.com/apengaaa/raspi4-with-arceos-doc/blob/master/src/assert/%E9%A3%9E%E8%85%BE%E6%B4%BE%E5%90%AF%E5%8A%A8ArceOS-3.png)
   
     （这里是没有开debug）
   
   * 便可以看到ArceOS启动成功，进入到了shell界面
   
     ![image-20240425174531177](https://github.com/apengaaa/raspi4-with-arceos-doc/blob/master/src/assert/%E9%A3%9E%E8%85%BE%E6%B4%BE%E5%90%AF%E5%8A%A8ArceOS-3.png)















