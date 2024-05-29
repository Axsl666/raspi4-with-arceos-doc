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

<https://dora-rs.ai/zh-CN/docs/guides/getting-started/conversation_py>

1. 创建一个新的数据流
   ```shell
   dora new conversation_py --lang python
   cd conversation_py
   ```
2. 添加一个新的节点
   ```shell
    dora new --kind custom-node talker
   ```
3. 在创建的新节点里创建并编辑talker.py

   加入以下内容：
   ```shell
   from dora import Node
   import pyarrow as pa

   node = Node()

   event = node.next()
   if event["type"] == "INPUT":
       print(
           f"""Node received:
       id: {event["id"]},
       value: {event["value"]},
       metadata: {event["metadata"]}"""
       )
   node.send_output("speech", pa.array(["Hello World"])) # add this line
   ```

4. 调整监听节点

   将node_1的名称更改为listener， 将node_1.py的名称更改为listener.py

   内容变为：

   ```shell
   from dora import Node
   import pyarrow as pa

   node = Node()

   event = node.next()
   if event["type"] == "INPUT":
       message = event["value"][0].as_py()
       print(
           f"""I heard {message}"""
       )
   ```
5. 修改dataflow.yml文件

   变为：
   ```shell
   nodes:
     - id: talker
       custom:
         source: talker/talker.py
         inputs:
           tick: dora/timer/secs/1
         outputs:
           - speech

     - id: listener
       custom:
         source: listener/listener.py
         inputs:
           speech: talker/speech
   ```
 
之后在终端运行：

```shell
dora up
dora start dataflow.yml --name conversation
dora logs conversation listener
```
结果：

```shell
root@Phytium-Pi:/home/user/conversation_py# dora logs conversation listener
I heard Hello World
```

