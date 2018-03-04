
## SDK接口参考
<span style="color:#ccc">1.1</span> 对象定义

<span style="color:#ccc">1.2</span> SDK集成方法

<span style="color:#ccc">1.3</span> 支持的配置方式

<span style="color:#ccc">1.4</span> smarconfig配置API

```
void deviceConfig(String action, String params, DeviceConfigCallback callback)
action: EasyConfig
params:
            {
                    "ssid":"Broadlink",      // wifi ssid
                    "password":"12345678",   // wifi密码
                    "timeout": 60,           // 配置超时时间，单位秒
                    "pid" : "",              // 配置设备的产品信息，可以为空
                    "version": 2             // 配网版本
            }
    callback返回:
            {
                    "status":0,
                    "deviceInfo": deviceInfo //配置成功上的设备信息
            }

```

<span style="color:#ccc">1.5</span> soft-ap 模式API

<span style="color:#ccc">1.6</span> 设备发现API
```
void deviceProbe(String action, String params, DeviceProbeCallback callback)
action: DeviceProbe
params:
            {
                    "timeout": 60,           // 配置超时时间，单位秒
                    "pid" : "",              // 配置设备的产品信息，可以为空
                    "version": 2             // 配网版本
            }
    callback返回:
            {
                    "status":0,
                    "deviceInfo": deviceInfo //配置成功上的设备信息
            }

```

<span style="color:#ccc">1.7</span> 配对API
```
void devicePair(String action, String params, DevicePairCallback callback)
action: DevicePair
params:
            {
                    "deviceInfo": deviceInfo
                    "timeout": 60,           // 配置超时时间，单位秒
                    "version": 2             // 配网版本
            }
    callback返回:
            {
                    "status":0,
                    "devicePairedInfo": devicePairedInfo //配置成功上的设备信息
            }

```
