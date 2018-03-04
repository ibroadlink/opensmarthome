## 云端接口参考
<span style="color:#ccc">2.1</span> 接口校验和安全方式方式

<span style="color:#ccc">2.1</span> 设备注册接口
```
POST https://(OpenproxyURL)/openproxy/v2/register?license=(license)

请求：
{
    "directive": {
        "header": {
            "namespace": "DNA.Register",
            "name": "Register",
            "interfaceVersion": "2",
            "messageId": "1bd5d003-31b9-476f-ad03-71d471922820"
        },
        "payload": {
            "device": {
                "deviceInfo": deviceInfo,
            },
            "scope": {
                "type": "BearerToken",
                "token": "some-access-token"
            },
            "options": {
            }
        }
    }
}

响应：
{
    "context": {},
    "event": {
        "header": {
            "namespace": "DNA.Register",
            "name": "Response",
            "interfaceVersion": "2",
            "messageId": "5f8a426e-01e4-4cc9-8b79-65f8bd0fd8a4"
        },
        "payload": {
        },
        "endpoints": [
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
                ]
            }
        ]
    }
}

```
<span style="color:#ccc">2.1</span> 设备控制接口
```
POST https://(OpenproxyURL)/openproxy/v2/control?license=(license)
请求：
{
  "directive": {
    "header": {
       "namespace": "DNA.PowerControl",
       "name": "ChangePowerState",
       "interfaceVersion": "2",
       "messageId": "1bd5d003-31b9-476f-ad03-71d471922820"
    },
    "endpoint": {
      "scope": {
         "type": "BearerToken",
         "token": "Yodst_WQRoS6LHyNyMLSZA"
      },
      ”devicePairedInfo":devicePairedInfo,
      "endpointId": "Some-Device-ID",
      "cookie": {}
    },
    "payload": {
        "powerState":"OFF"
    }
  }
}
响应：
{
  "context": {
    "properties": [ {
       "namespace": "DNA.PowerControl",
       "name": "powerState",
       "value": “ON”,
       "timeOfSample": "2017-02-03T16:20:50.52Z",
    } ]
  },
  "event": {
    "header": {
       "namespace": "DNA.PowerControl",
       "name": "Response",
       "interfaceVersion": "2",
       "messageId": "5f8a426e-01e4-4cc9-8b79-65f8bd0fd8a4",
    },
    "endpoint": {
      "scope": {
        "type": "BearerToken",
        "token": "some-access-token"
      },
      "endpointId": "appliance-001"
    },
    "payload": {
    }
  }
}
```

<span style="color:#ccc">2.1</span> 设备状态查询接口

<span style="color:#ccc">2.1</span> 数据上报接口
