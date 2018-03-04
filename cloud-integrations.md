## 云端接口参考
<span style="color:#ccc">2.1</span> 接口校验和安全方式方式

<span style="color:#ccc">2.2</span> 云端接口

<span style="color:#ccc">2.2.1</span> 设备注册接口
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
          "device": {
              "deviceInfo": deviceInfo,
          },
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
<span style="color:#ccc">2.2.2</span> 设备控制接口
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

<span style="color:#ccc">2.2.3</span> 设备在线状态查询接口

每次最多查询32个设备的在线状态
```
POST https://(OpenproxyURL)/openproxy/v2/querystate?license=(license)
请求：
{
  "directive": {
    "header": {
       "namespace": "DNA.QueryState",
       "name": "QueryState",
       "interfaceVersion": "2",
       "messageId": "1bd5d003-31b9-476f-ad03-71d471922820"
    },
    "endpoints": [{
      "scope": {
      },
      ”devicePairedInfo":devicePairedInfo,
      "endpointId": "Some-Device-ID",
      "cookie": {}
    }],
    "payload": {
    }
  }
}
响应：
{
  "context": {
    "properties": []
  },
  "event": {
    "header": {
       "namespace": "DNA.QueryState",
       "name": "Response",
       "interfaceVersion": "2",
       "messageId": "5f8a426e-01e4-4cc9-8b79-65f8bd0fd8a4",
    },
    "endpoints": [{
      "scope": {
      },
      "endpointId": "appliance-001",
      "state": "online"
    }],
    "payload": {
    }
  }
}
```

<span style="color:#ccc">2.2.4</span> 设备状态查询接口
```
POST https://(OpenproxyURL)/openproxy/v2/control?license=(license)
请求：
{
  "directive": {
    "header": {
       "namespace": "DNA",
       "name": "ReportState",
       "interfaceVersion": "2",
       "messageId": "1bd5d003-31b9-476f-ad03-71d471922820"
    },
    "endpoint": {
      "scope": {
      },
      ”devicePairedInfo":devicePairedInfo,
      "endpointId": "Some-Device-ID",
      "cookie": {}
    },
    "payload": {
    }
  }
}
响应：
{
  "context": {
"properties": [
        {
           "namespace": "DNA",
           "name": "powerState",
           "value":{
                "value":"ON",
                "scale":"",
                "attributeName":"开关"
                "scaleName":"",
                "valueName":"打开"
           },
           "timeOfSample": "2017-02-03T16:20:50.52Z",
        }
    ]

  },
  "event": {
    "header": {
       "namespace": "DNA.QueryState",
       "name": "Response",
       "interfaceVersion": "2",
       "messageId": "5f8a426e-01e4-4cc9-8b79-65f8bd0fd8a4",
    },
    "endpoint": {
      "scope": {
      },
      "endpointId": "appliance-001",
    },
    "payload": {
    }
  }
}
```

<span style="color:#ccc">2.2.5</span> 数据上报接口
```
POST https://(YOURSERVER)/eventchannel?PARAMS1=xx&PARAMS2=yy

```

<span style="color:#ccc">2.3</span> 接口错误响应

<span style="color:#ccc">2.3.1</span> 错误响应格式

```
返回消息中 
    event.name="ErrorResponse",
    payload中是具体错误类型和原因。
举例：
{
  "context": {},
  "event": {
      "header": {
      "namespace": "DNA.PowerControl",
      "messageId": "30d2cd1a-ce4f-4542-aa5e-04bd0a6492d5",
      "name": "ErrorResponse",
      "payloadVersion": "2"
    },
    "endpoint": {
      "scope": {
        "type": "BearerToken",
        "token": "some-access-token"
      },
      "endpointId": "appliance-001"
    },
    "payload": {
        "type": "ENDPOINT_UNREACHABLE",
        "message":"xxx",
    }
  }
```
<span style="color:#ccc">2.3.2</span> 错误码表

|字段 | 说明 | 备注|
|------------ | ------------- | -------------|
|ENDPOINT_UNREACHABLE | 设备离线 |	 
|NO_SUCH_ENDPOINT |设备不存在|	 
|INVALID_REQ	|请求格式不对|	 
|DEVICE_RESET|	设备已经复位	 |
|INVALID_DIRECTIVE|	指令错误	 |
|INVALID_ACCESSTOKEN|	token失效	| 
|INVALID_SIGNATURE	|签名非法|	 
|INTERNAL_ERROR	|其他错误	 |
|VALUE_OUT_OF_RANGE|	值越界	 |
|FUNCTION_NOT_SUPPORT|	功能不支持|	 
|UNDERSTAND_FAILURE	|无法理解	 |
|SERVICE_UNAVAILABLE	|服务器不可用	|当服务处理超时或者异常时返回|

