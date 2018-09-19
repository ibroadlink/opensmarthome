
## SDK接口参考
<span style="color:#ccc">1.1</span> 对象定义

Go to [对象定义](object-definition.md).

<span style="color:#ccc">1.2</span> 准备工作

#### 获取 kit 模块

如果你还没有 BroadLink DNA kit 模块，请联系我们咨询如何获取模块。

#### 建立产品测试与发布

如果你还没有建立一个产品，请登录我们的开发者平台注册账号，进行产品的建立，测试与发布。

#### 申请 License

为了设备的安全，所有使用 SDK 的用户必须向 `BroadLink Co., Ltd.` 申请 `License`，`License` 与应用的包名(`packageName`)相关联，不同的应用包名需要申请不同的 `License`。

1.  进入 `BroadLink DNA kit` 开发者平台。
2.  登录账号，没有账号请先注册。
3.  选择 `我的 SDK`。
4.  选择 `License 申请` -> `新建 License 申请`，按要求填写信息，若要控制第三方厂家设备，请在备注中说明厂家名称以及具体产品型号，提交审核。
5.  审核通过之后，可以在申请页面看见 `License`。

<span style="color:#ccc">1.3</span> SDK集成方法

#### Android 集成

将SDK压缩包内的JAR文件和so文件导入到工程中，SDK 支持 `Android2.3.1` 以后版本,支持 `armeabi/armeabi-v7a/arm64-v8a/mips/mips64/x86_64/x86` 指令集。

Android 平台使用 `NetworkAPI.getInstanceBLNetwork(Content content)` 进行 SDK 实例化，SDK 为单例模式。
在使用 SDK 时，应用需要如下权限:

```
<uses-permission android:name="android.permission.CHANGE_NETWORK_STATE" />
<uses-permission android:name="android.permission.CHANGE_WIFI_STATE" />
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
<uses-permission android:name="android.permission.ACCESS_WIFI_STATE" />
<uses-permission android:name="android.permission.INTERNET" />
<uses-permission android:name="android.permission.WAKE_LOCK" />
<uses-permission android:name="android.permission.CHANGE_WIFI_MULTICAST_STATE" />
```

#### iOS 集成

SDK 支持 `iOS6.0` 以后版本, 支持 `armv7/armv7s/arm64/i386/x86_64` 指令集。

iOS 平台使用 `[[BLSmartHomeAPI sharedDNASDK] sdkInit:[param toJSONString]]` 进行 SDK 实例化，SDK 为单例模式。

<span style="color:#ccc">1.4</span> SDK初始化

```

public String sdkInit(String params);

params: {
            "loglevel": 0,                                  // SDK日志打印级别
            "license": "xxxxxxxxxxxxx",                     // 申请的License
            "packageName": "cn.com.broadlink.SDKDemo"       // 申请License时的应用包名
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
                    "msg": "success", 
                    "devicePairedInfo": devicePairedInfo //配置成功上的设备信息
            }

```

```
public String devicePair(String action, String params)

action: CloudPair
params:
            {
                    "deviceInfo": deviceInfo    // Probe搜索到的设备信息
                    "timeout": 3000,            // 配对超时实际，默认3000ms
                    "version": 1                // 配对版本
            }

return:
            {
                    "status":0,
                    "msg": "success", 
                    "payload": {
                        "deviceToken":"xxxxxxx",
                        "deviceInfo":"xxxxxxx",
                        "deviceid":"xxxxxx"
                    }
            }

```

<span style="color:#ccc">1.9</span> 设备控制API
```
public String deviceControl(String action, String params)

action: RM_Panel_Test
params:
            {
                    "devicePairedInfo": devicePairedInfo    // 配置成功上的设备信息
                    "data" : {                      //  云端返回信息
                        "pid":"",                   // 设备类型
                        "ircodeid":"",              // 红外码ID
                        "timestamp":1514736000000,  // 云端返回测试时间戳
                        "ircode": {
                            "name": "打开空调",                                  //本条红外码功能名称
                            "function":"on",                                    //本条红外码功能
                            "desc":"xxx",                                       //本条红外码描述信息
                            "code":"2600121343241325243521342342141"            //红外码值
                        }
                    }
                    "version": 1                // 配对版本
            }

return:
            {
                    "status":0,
                    "msg": "success", 
                    "devicePairedInfo": devicePairedInfo    // 新返回创建的设备信息
            }

```

```
public String deviceControl(String action, String params)

action: dev_passthrough
params:
            {
                    "devicePairedInfo": devicePairedInfo    // 配置成功上的设备信息
                    "command": "xxxxxx"         // 透传指令，BASE64 EnCode
                    "version": 1                // 配对版本
            }

return:
            {
                    "status":0,
                    "msg": "success", 
                    "command": "xxxxxxxxx"    // 透传返回指令，BASE64 EnCode
            }

```
