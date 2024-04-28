# 飞腾派运行ArceOS

1. 硬件准备：
   * 飞腾派板子
   
     ![image-20240427150305459](C:\Users\张江鹏\AppData\Roaming\Typora\typora-user-images\image-20240427150305459.png)
   
   * 两张SD卡，一张烧录好Ubuntu系统，一张放ArceOS启动镜像（或U盘）
   
   * 读卡器（或U盘）
   
   * USB转TTL串口线
   
   * ArceOS代码地址：https://github.com/arceos-usb/arceos_experiment/tree/phytium_pi_port（注意分支）
   
2. 飞腾派上电启动，把有ArceOS启动镜像的读卡器或者U盘插到飞腾派上，用串口把飞腾派与电脑相连接，启动电脑上的远程连接软件，如Putty，波特率设置为115200

   串口接法：接8、10、12号引脚位置，如图所示（8号代表TX，接RX；10号代表RX，接TX；12号接地线）

   ![image-20240427150400839](C:\Users\张江鹏\AppData\Roaming\Typora\typora-user-images\image-20240427150400839.png)

3. 在uboot倒计时结束前按任意键进入手动引导
   * 输入`usb start` ,启用USB驱动来识别插入的USB设备（读卡器/U盘）
   
     ![image-20240427145830692](C:\Users\张江鹏\AppData\Roaming\Typora\typora-user-images\image-20240427145830692.png)
   
   * 输入`fatload usb 0 0x90100000 cli_aarch64-phytium-pi.bin`，从插入的USB设备（读卡器/U盘）上下载ArceOS镜像
   
     ![image-20240427145929621](C:\Users\张江鹏\AppData\Roaming\Typora\typora-user-images\image-20240427145929621.png)
   
   * 输入`go 0x90100000`加载ArceOS镜像
   
     ![image-20240427150034220](C:\Users\张江鹏\AppData\Roaming\Typora\typora-user-images\image-20240427150034220.png)
   
     （这里是没有开debug）
   
   * 便可以看到ArceOS启动成功，进入到了shell界面
   
     ![image-20240425174531177](C:\Users\张江鹏\AppData\Roaming\Typora\typora-user-images\image-20240425174531177.png)















