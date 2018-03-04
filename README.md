# 概述
APP中集成iot SDK，云端与开放设备控制接口对接。对接的流程框图如下所示：
![整体框图](img/arch.png "整体框图")

<span style="color:#ccc">0.1</span> 配置设备上网

这个步骤将Wi-Fi的SSID和密码通过APP传递给设备，配置完成后设备会自动连接路由器。

<span style="color:#ccc">0.2</span> 局域网设备发现

设备发现功能是APP通过在局域网（LAN）内广播UDP报文，设备收到报文后会进行响应。通过这个过程APP
可以获取局域网内的在线设备列表。

<span style="color:#ccc">0.3</span> 局域网设备配对

APP如果要控制设备，必须在局域网内与设备进行配对，或者控制设备的KEY。
每次设备复位后，这个KEY都会变化。

<span style="color:#ccc">0.4</span> 设备注册

APP通过局域网获取到设备的信息以及KEY后，必须通过云端进行注册，完成后会得到
设备相关的详细信息，比如品类，名称，型号，支持的功能列表等信息。

<span style="color:#ccc">0.5</span> 设备状态查询

云端有批量查询设备在线状态接口，可以查看设备是否连接在服务器上。

<span style="color:#ccc">0.6</span> 设备控制

设备控制都使用JSON格式的命令。

<span style="color:#ccc">0.7</span> 设备数据上报

对于支持设备上报的产品，当设备有状态变化时，可以通过云端接口推送出来。

<span style="color:#ccc">0.8</span> 安全和隐私
  * 报文加密

    报文使用AES 128位进行加密，密钥在设备配对时产生，每次复位都会变化

  * 接口安全

    云端接口使用HTTPS，TLS 1.2.

  * 数据隐私

    iot 云端不保存任何数据，所有控制以来的数据都来自于app。每次控制时，需要携带设备的控制key。

<span style="color:#ccc">0.9</span> 注意事项
  * 第三方云端需要保存devicePairedInfo
  * 第三方云端需要知道每个devicePairedInfo对应的endpoint列表以及每个endpoint支持的功能
  
  Go to [对象定义](object-definition.md).

  ## SDK接口参考
  Go to [集成SDK](sdk-integrations.md).

  ## 云端接口参考
  Go to [集成云端API](cloud-integrations.md).
