# 在飞腾派上运行Dora-rs

参考：https://dora-rs.ai/zh-CN/

## 安装Dora-rs

1. 下载 Ubuntu 系统镜像并烧录到飞腾派上

   用户名和密码均为：root

2. 飞腾派启用网络

   * 串口连接

     配置网络：

     输入`sudo nmcli dev wifi`，扫描附近热点

     输入`sudo nmcli dev wifi connect "SSID" password "PASSWORD" ifname wlan0`，连接到指定热点，SSID和 PASSWORD 替换成实际的 WiFi名称和密码。

   * 连接显示屏

3. 下载安装Dora-rs

   ```shell
   export DORA_VERSION=v0.3.2 # Check for the latest release
   export ARCHITECTURE=$(uname -m)
   wget https://github.com/dora-rs/dora/releases/download/${DORA_VERSION}/dora-${DORA_VERSION}-${ARCHITECTURE}-Linux.zip
   unzip dora-${DORA_VERSION}-${ARCHITECTURE}-Linux.zip
   pip install dora-rs==${DORA_VERSION}
   PATH=$PATH:$(pwd)
   dora --help
   ```

## 尝试使用Dora-rs

### Python Conversation

https://dora-rs.ai/zh-CN/docs/guides/getting-started/conversation_py

结果：

```shell
root@Phytium-Pi:/home/user/conversation_py# dora logs conversation listener
I heard Hello World
```

