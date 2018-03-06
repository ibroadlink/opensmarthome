
## SDK接口参考
<span style="color:#ccc">1.1</span> 对象定义

Go to [对象定义](object-definition.md).

<span style="color:#ccc">1.2</span> SDK集成方法

<span style="color:#ccc">1.3</span> 支持的配置方式

<span style="color:#ccc">1.4</span> SDK初始化

```

public String sdkInit(String params);

params: {
            "loglevel": 0,                  // SDK日志打印级别
            "license": "xxxxxxxxxxxxx",      // 申请的License
            "packageName": "cn.com.broadlink.SDKDemo"       //申请License时的应用包名
        }

return: {
            "status": 0,
            "msg": "init success"
        }
```

<span style="color:#ccc">1.5</span> EasyConfig配置API

```
设备开始配网

public String deviceEasyConfig(String action, String params)

action:     ConfigStart
params:
            {
                    "ssid":"Broadlink",      // wifi ssid
                    "password":"12345678",   // wifi密码
                    "timeout": 60,           // 配置超时时间，单位秒
                    "cfgversion": 2          // 配网版本
            }

return:
            {
                    "status":0,
                    "msg": "success",           //配网结果
                    "mac": "00:11:22:33:44:55"  //配网设备MAC
            }

```


```
设备取消配网

public String deviceEasyConfig(String action, String params)

action:     ConfigCancel
params:
            {
            }

return:
            {
                    "status":0,
                    "msg": "success",           //配网结果
            }

```


<span style="color:#ccc">1.6</span> soft-ap 模式API

```
获取设备支持的AP列表

public String deviceAPConfig(String action, String params)

action:     ScanAPList
params:
            {
                    "timeout": 7000,      // 扫描AP列表超时时间，推荐7000ms
            }

return:
            {
                    "status":0,
                    "msg": "success",           //扫描结果
                    "list": [
                        APInfo                  //AP信息
                    ]
            }

```


```
AP配网

public String deviceAPConfig(String action, String params)

action:     APConfig
params:
            {
                    "APInfo": APInfo
            }

return:
            {
                    "status":0,
                    "msg": "success",           //配置结果
            }

```

<span style="color:#ccc">1.7</span> 设备发现API
```
public String deviceProbe(String action, String params)

action:     DeviceProbe
params:
            {
                    "scantime": 3000,           // 搜索设备的超时时间，默认 3000ms
                    "version": 1,
                    "pids" : [
                                                // 搜索指定设备Pid列表，默认为空，不限制设备Pid
                        ],
            }

return:
            {
                    "status":0,
                    "msg": "success",           // 搜索结果
                    "list": [
                        deviceInfo              // 搜索到的设备列表
                    ]
            }
```

<span style="color:#ccc">1.8</span> 配对API
```
public String devicePair(String action, String params)

action: DevicePair
params:
            {
                    "deviceInfo": deviceInfo    // Probe搜索到的设备信息
                    "timeout": 3000,            // 配对超时实际，默认3000ms
                    "version": 1                // 配对版本
            }

return:
            {
                    "status":0,
                    "devicePairedInfo": devicePairedInfo //配置成功上的设备信息
            }

```
