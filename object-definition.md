# 对象定义
```
deviceInfo
{
     "did":"",      //设备的唯一ID
     "pid":"",      //设备产品类型ID
     "mac":"",      //设备MAC地址
     "name":"",     //设备名称
     "lanaddr":"",  //设备局域网IP地址
     "extend":""    //设备扩展信息
}
```


```
devicePairedInfo
{
     "did":"",      //设备的唯一ID
     "pid":"",      //设备产品类型ID
     "mac":"",      //设备MAC地址
     "cookie":""    //设备Pair获取Cookie
}
```


```

APInfo
{
    "ssid":"xxxx",              // 配置AP的SSID名称
    "password":"xxxxx",         // 配置AP的密码
    "type": 0/1/2/3             // 配置AP的加密方式 0:无加密 1:WEP 2:WPA1 3:WPA2
}

```


```
endpoint
{
    "endpointId": "appliance-001",
    "friendlyName": "卧室灯",
    "isReachable":true,
    "description": "由BroadLink生产的灯",
    "manufacturerName": "Sample Manufacturer",
    "icon":"产品图片URL",
    "brand":"品牌",
    "displayCategories": [
        "LIGHT"
    ],
    "cookie": {
        "extraDetail1": "某些设备可能会用到这个cookie，需要在控制时原样返回",
        "extraDetail2": "某些设备可能会用到这个cookie，需要在控制时原样返回",
        "extraDetail3": "某些设备可能会用到这个cookie，需要在控制时原样返回",
        "extraDetail4": "某些设备可能会用到这个cookie，需要在控制时原样返回"
    },
    "capabilities": [
        {
            "type": "DNAInterface",
            "interface": "DNA.PowerControl",
            "version": "2",
            "properties": {
                "supported": [
                    {
                        "name": "powerState"
                    }
                ],
                "proactivelyReported": true,
                "retrievable": true
            },
           "actions": {
               "supported": [
                {
                     "name": "ChangePowerState"
                }
               ]
           }
        }
```
