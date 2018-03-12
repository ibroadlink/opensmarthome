
<span style="color:#ccc">3.1</span> 电源控制

控制设备的电源开关

接口名称: DNA.PowerControl

ChangePowerState请求

请求例子
<span style="color:#ccc">3.1</span> 电源控制

控制设备的电源开关

接口名称: DNA.PowerControl

ChangePowerState请求

请求例子
```
    {
      "directive": {
        "header": {
           "namespace": "DNA.PowerControl",
           "name": "ChangePowerState",
           "interfaceVersion": "2",
           "messageId": "1bd5d003-31b9-476f-ad03-71d471922820",
        },
        "endpoint": {
          "scope": {
             "type": "",
             "token": "some-access-token"
          },
          "endpointId": "appliance-001",
		  "devicePairedInfo":devicePairedInfo,
          "cookie": {}
        },
        "payload": {
            "powerState": "ON"
        }
      }
    }
```

响应例子
```
    {
      "context": {
        "properties": [ {
           "namespace": "DNA.PowerControl",
           "name": "powerState",
           "value": "ON",
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
            "type": "",
            "token": "some-access-token"
          },
          "endpointId": "appliance-001"
        },
        "payload": {
        }
      }
    }

```

<span style="color:#ccc">3.2</span> 频道控制

控制电视/机顶盒频道

接口名称: DNA.ChannelControl

* ChangeChannel请求

请求例子
```   
    {
      "directive": {
        "header": {
           "namespace": "DNA.ChannelControl",
           "name": "ChangeChannel",
           "interfaceVersion": "2",
           "messageId": "1bd5d003-31b9-476f-ad03-71d471922820",
        },
        "endpoint": {
          "scope": {
             "type": "",
             "token": "some-access-token"
          },
          "endpointId": "appliance-001",
		  "devicePairedInfo":devicePairedInfo,
          "cookie": {}
        },
        "payload": {
              "channelNumber":"1234"
        }
      }
    }
```

响应例子
```
    {
      "context": {
        "properties": [ {
           "namespace": "DNA.ChannelControl",
           "name": "channelNumber",
           "value":"123",
           "timeOfSample": "2017-02-03T16:20:50.52Z",
        } ]
      },
      "event": {
        "header": {
           "namespace": "DNA.ChannelControl",
           "name": "Response",
           "interfaceVersion": "2",
           "messageId": "5f8a426e-01e4-4cc9-8b79-65f8bd0fd8a4",
        },
        "endpoint": {
          "scope": {
            "type": "",
            "token": "some-access-token"
          },
          "endpointId": "appliance-001"
        },
        "payload": {
        }
      }
    }
```

* AdjustChannel请求

按步长调整频道

请求:
```
    {
      "directive": {
        "header": {
          "namespace": "DNA.ChannelControl",
          "name": "AdjustChannel",
          "messageId": "c8d53423-b49b-48ee-9181-f50acedf2870",
          "payloadVersion": "2"
        },
       "endpoint": {
          "scope": {
             "type": "",
             "token": "some-access-token"
          },
          "endpointId": "appliance-001",
		  "devicePairedInfo":devicePairedInfo,
          "cookie": {}
        },
        "payload": {
          "channelSteps" : 1
        }
      }
    }
```

响应：
```
    {
      "context": {
        "properties": [
            {
               "namespace": "DNA.ChannelControl",
               "name": "channelSteps",
               "value": 1
               "timeOfSample": "2017-02-03T16:20:50.52Z",
            }
        ]
      },
      "event": {
          "header": {
          "messageId": "30d2cd1a-ce4f-4542-aa5e-04bd0a6492d5",
          "name": "Response",
          "payloadVersion": "2"
        },
        "endpoint": {
          "scope": {
            "type": "",
            "token": "some-access-token"
          },
          "endpointId": "appliance-001"
        },
        "payload": {
        }
      }
    }
```

<span style="color:#ccc">3.3</span> 音量控制

控制设备的音量

接口名称: DNA.VolumeControl

* 步长调节请求
```
    {
      "directive": {
        "header": {
          "namespace": "DNA.VolumeControl",
          "name": "AdjustVolume",
          "messageId": "c8d53423-b49b-48ee-9181-f50acedf2870",
          "payloadVersion": "2"
        },
        "endpoint": {
          "scope": {
            "type": "",
            "token": "some-access-token"
          },
          "endpointId": "appliance-001",
		  "devicePairedInfo":devicePairedInfo,
          "cookie": {}
        },
        "payload": {
          "volumeSteps": 20
        }
      }
    }
```
响应
```
    {
      "context": {
        "properties": [
            {
               "namespace": "DNA.VolumeControl",
               "name": "volumeSteps",
               "value": 20
               "timeOfSample": "2017-02-03T16:20:50.52Z",
            }
        ]
      },
      "event": {
          "header": {
          "messageId": "30d2cd1a-ce4f-4542-aa5e-04bd0a6492d5",
          "name": "Response",
          "payloadVersion": "2"
        },
        "endpoint": {
          "scope": {
            "type": "",
            "token": "some-access-token"
          },
          "endpointId": "appliance-001"
        },
        "payload": {
        }
      }
    }
```

* 直接控制请求
```
   
    {
      "directive": {
        "header": {
          "namespace": "DNA.VolumeControl",
          "name": "SetVolume",
          "messageId": "5f8a426e-01e4-4cc9-8b79-65f8bd0fd8a4",
          "payloadVersion": "2"
        },
        "endpoint": {
          "scope": {
            "type": "",
            "token": "<some-access-token>"
          },
          "endpointId": "<appliance-001>",
          "cookie": {
             
          }
        },
        "payload": {
          "volume": 50
        }
      }
    }
```

响应
```
    {
      "context": {
        "properties": [
            {
               "namespace": "DNA.VolumeControl",
               "name": "volume",
               "value": 50
               "timeOfSample": "2017-02-03T16:20:50.52Z",
            }
        ]
      },
      "event": {
          "header": {
          "messageId": "30d2cd1a-ce4f-4542-aa5e-04bd0a6492d5",
          "name": "Response",
          "payloadVersion": "2"
        },
        "endpoint": {
          "scope": {
            "type": "",
            "token": "some-access-token"
          },
          "endpointId": "appliance-001"
        },
        "payload": {
        }
      }
    }
```
* 静音控制请求
```
    {
      "directive": {
        "header": {
          "namespace": "DNA.VolumeControl",
          "name": "SetMute",
          "messageId": "c8d53423-b49b-48ee-9181-f50acedf2870",
          "payloadVersion": "3"
        },
        "endpoint": {
          "scope": {
            "type": "",
            "token": "<some-access-token>"
          },
          "endpointId": "<appliance-001>",
          "cookie": {}
        },
        "payload": {
          "mute": true
        }
      }
    }
```
响应
```
    {
      "context": {
        "properties": [
            {
               "namespace": "DNA.VolumeControl",
               "name": "mute",
               "value": true
               "timeOfSample": "2017-02-03T16:20:50.52Z",
            }
        ]
      },
      "event": {
          "header": {
          "messageId": "30d2cd1a-ce4f-4542-aa5e-04bd0a6492d5",
          "name": "Response",
          "payloadVersion": "2"
        },
        "endpoint": {
          "scope": {
            "type": "",
            "token": "some-access-token"
          },
          "endpointId": "appliance-001"
        },
        "payload": {
        }
      }
    }
```

<span style="color:#ccc">3.4</span>播放控制

控制设备的播放/暂停等,由于播放控制不涉及状态，所有返回是统一的。

接口名称：DNA.PlaybackControl

* 播放请求
```
    {
      "directive": {
        "header": {
          "namespace": "DNA.PlaybackController",
          "name": "Play",
          "messageId": "5f8a426e-01e4-4cc9-8b79-65f8bd0fd8a4",
          "payloadVersion": "2"
        },
        "endpoint": {
          "scope": {
            "type": "",
            "token": "<OAuth2认证后得到的access_token>"
          },
          "endpointId": "<设备ID，发现时返回>",
		  "devicePairedInfo":devicePairedInfo,
          "cookie": {
          }
        },
        "payload": {
        }
      }
    }
```

* 暂停请求

   
```
    {
      "directive": {
        "header": {
          "namespace": "DNA.PlaybackController",
          "name": "Pause",
          "messageId": "5f8a426e-01e4-4cc9-8b79-65f8bd0fd8a4",
          "payloadVersion": "2"
        },
        "endpoint": {
          "scope": {
            "type": "",
            "token": "<OAuth2认证后得到的access_token>"
          },
          "endpointId": "<设备ID，发现时返回>",
		  "devicePairedInfo":devicePairedInfo,
          "cookie": {
          }
        },
        "payload": {
        }
      }
    }
```
* 继续请求
```
   

    {
      "directive": {
        "header": {
          "namespace": "DNA.PlaybackController",
          "name": "Resume",
          "messageId": "5f8a426e-01e4-4cc9-8b79-65f8bd0fd8a4",
          "payloadVersion": "2"
        },
        "endpoint": {
          "scope": {
            "type": "",
            "token": "<OAuth2认证后得到的access_token>"
          },
          "endpointId": "<设备ID，发现时返回>",
		  "devicePairedInfo":devicePairedInfo,
          "cookie": {
          }
        },
        "payload": {
        }
      }
    }
 ```   
* 下一首请求
```
   

    {
      "directive": {
        "header": {
          "namespace": "DNA.PlaybackController",
          "name": "Next",
          "messageId": "5f8a426e-01e4-4cc9-8b79-65f8bd0fd8a4",
          "payloadVersion": "2"
        },
        "endpoint": {
          "scope": {
            "type": "",
            "token": "<OAuth2认证后得到的access_token>"
          },
          "endpointId": "<设备ID，发现时返回>",
		  "devicePairedInfo":devicePairedInfo,
          "cookie": {
          }
        },
        "payload": {
        }
      }
    }
```
* 上一首请求
```
   

    {
      "directive": {
        "header": {
          "namespace": "DNA.PlaybackController",
          "name": "Previous",
          "messageId": "5f8a426e-01e4-4cc9-8b79-65f8bd0fd8a4",
          "payloadVersion": "2"
        },
        "endpoint": {
          "scope": {
            "type": "",
            "token": "<OAuth2认证后得到的access_token>"
          },
          "endpointId": "<设备ID，发现时返回>",
		  "devicePairedInfo":devicePairedInfo,
          "cookie": {
          }
        },
        "payload": {
        }
      }
    }
```    
* 快进请求
```
   

    {
      "directive": {
        "header": {
          "namespace": "DNA.PlaybackController",
          "name": "FastForward",
          "messageId": "5f8a426e-01e4-4cc9-8b79-65f8bd0fd8a4",
          "payloadVersion": "2"
        },
        "endpoint": {
          "scope": {
            "type": "",
            "token": "<OAuth2认证后得到的access_token>"
          },
          "endpointId": "<设备ID，发现时返回>",
		  "devicePairedInfo":devicePairedInfo,
          "cookie": {
          }
        },
        "payload": {
        }
      }
    }
```
* 回放请求
```
   

    {
      "directive": {
        "header": {
          "namespace": "DNA.PlaybackController",
          "name": "Rewind",
          "messageId": "5f8a426e-01e4-4cc9-8b79-65f8bd0fd8a4",
          "payloadVersion": "2"
        },
        "endpoint": {
          "scope": {
            "type": "",
            "token": "<OAuth2认证后得到的access_token>"
          },
          "endpointId": "<设备ID，发现时返回>",
		  "devicePairedInfo":devicePairedInfo,
          "cookie": {
          }
        },
        "payload": {
        }
      }
    }
```
* 响应
```
   

    {
      "context": {
        "properties": [
        ]
      },
      "event": {
          "header": {
          "messageId": "30d2cd1a-ce4f-4542-aa5e-04bd0a6492d5",
          "name": "Response",
          "payloadVersion": "2"
        },
        "endpoint": {
          "scope": {
            "type": "",
            "token": "some-access-token"
          },
          "endpointId": "appliance-001"
        },
        "payload": {
        }
      }
    }
```    
    
<span style="color:#ccc">3.5</span>风速控制

    控制风扇的速度
    
    接口名称：DNA.WindSpeedControl
    
* 设置风速请求
```
    {
      "directive": {
        "header": {
          "namespace": "DNA.WindSpeedControl",
          "name": "SetWindSpeed",
          "interfaceVersion": "2",
          "messageId": "1bd5d003-31b9-476f-ad03-71d471922820",
        },
        "endpoint": {
          "scope": {
            "type": "",
            "token": "some-access-token"
          },
          "endpointId": "appliance-001",
		  "devicePairedInfo":devicePairedInfo,
          "cookie": {}
        },
        "payload": {
          "windSpeed": "HIGH"
        }
      }
    }
```
响应:
```
   

    {
      "context": {
        "properties": [
            {
               "namespace": "DNA.PercentageControl",
               "name": "windSpeed",
               "value":"HIGH",
               "timeOfSample": "2017-02-03T16:20:50.52Z",
            }
        ]
      },
      "event": {
          "header": {
          "messageId": "30d2cd1a-ce4f-4542-aa5e-04bd0a6492d5",
          "name": "Response",
          "payloadVersion": "2"
        },
        "endpoint": {
          "scope": {
            "type": "",
            "token": "some-access-token"
          },
          "endpointId": "appliance-001"
        },
        "payload": {
        }
      }
    }
```
具体支持的列表，请参考`智能家居接口属性参考表 `

* 步长调整风速请求
```
   

    {
      "directive": {
        "header": {
          "namespace": "DNA.WindSpeedControl",
          "name": "AdjustWindSpeed",
          "interfaceVersion": "2",
          "messageId": "1bd5d003-31b9-476f-ad03-71d471922820",
        },
        "endpoint": {
          "scope": {
            "type": "",
            "token": "some-access-token"
          },
          "endpointId": "appliance-001",
		  "devicePairedInfo":devicePairedInfo,
          "cookie": {}
        },
        "payload": {
          "windSpeedSteps": 1
        }
      }
    }
```
响应:
```
   

    {
      "context": {
        "properties": [
            {
               "namespace": "DNA.PercentageControl",
               "name": "windSpeedSteps",
               "value":1,
               "timeOfSample": "2017-02-03T16:20:50.52Z",
            }
        ]
      },
      "event": {
          "header": {
          "messageId": "30d2cd1a-ce4f-4542-aa5e-04bd0a6492d5",
          "name": "Response",
          "payloadVersion": "2"
        },
        "endpoint": {
          "scope": {
            "type": "",
            "token": "some-access-token"
          },
          "endpointId": "appliance-001"
        },
        "payload": {
        }
      }
    }
```

<span style="color:#ccc">3.6</span>风向控制

控制设备的风向，控制不涉及状态，所有返回是统一的。

接口名称：DNA.AirFlowControl

* 开启摆风请求
```

   

    {
      "directive": {
        "header": {
          "namespace": "DNA.AirFlowControl",
          "name": "Start",
          "messageId": "5f8a426e-01e4-4cc9-8b79-65f8bd0fd8a4",
          "payloadVersion": "2"
        },
        "endpoint": {
          "scope": {
            "type": "",
            "token": "<OAuth2认证后得到的access_token>"
          },
          "endpointId": "<设备ID，发现时返回>",
		  "devicePairedInfo":devicePairedInfo,
          "cookie": {
          }
        },
        "payload": {
        }
      }
    }
```

* 停止摆风请求
```
   

    {
      "directive": {
        "header": {
          "namespace": "DNA.AirFlowControl",
          "name": "Stop",
          "messageId": "5f8a426e-01e4-4cc9-8b79-65f8bd0fd8a4",
          "payloadVersion": "2"
        },
        "endpoint": {
          "scope": {
            "type": "",
            "token": "<OAuth2认证后得到的access_token>"
          },
          "endpointId": "<设备ID，发现时返回>",
		  "devicePairedInfo":devicePairedInfo,
          "cookie": {
          }
        },
        "payload": {
        }
      }
    }
```
* 水平摆风请求
```
   

    {
      "directive": {
        "header": {
          "namespace": "DNA.AirFlowControl",
          "name": "HorizontalFlow",
          "messageId": "5f8a426e-01e4-4cc9-8b79-65f8bd0fd8a4",
          "payloadVersion": "2"
        },
        "endpoint": {
          "scope": {
            "type": "",
            "token": "<OAuth2认证后得到的access_token>"
          },
          "endpointId": "<设备ID，发现时返回>",
		  "devicePairedInfo":devicePairedInfo,
          "cookie": {
          }
        },
        "payload": {
        }
      }
    }
```   

* 垂直摆风请求
```
   

    {
      "directive": {
        "header": {
          "namespace": "DNA.AirFlowControl",
          "name": "VerticalFlow",
          "messageId": "5f8a426e-01e4-4cc9-8b79-65f8bd0fd8a4",
          "payloadVersion": "2"
        },
        "endpoint": {
          "scope": {
            "type": "",
            "token": "<OAuth2认证后得到的access_token>"
          },
          "endpointId": "<设备ID，发现时返回>",
		  "devicePairedInfo":devicePairedInfo,
          "cookie": {
          }
        },
        "payload": {
        }
      }
    }
```    

响应：
```
   

    {
      "context": {
        "properties": [
        ]
      },
      "event": {
          "header": {
          "messageId": "30d2cd1a-ce4f-4542-aa5e-04bd0a6492d5",
          "name": "Response",
          "payloadVersion": "2"
        },
        "endpoint": {
          "scope": {
            "type": "",
            "token": "some-access-token"
          },
          "endpointId": "appliance-001"
        },
        "payload": {
        }
      }
    }
```    

<span style="color:#ccc">3.7</span>颜色控制

控制设备的颜色

接口名称：DNA.ColorControl

* 请求
```
   

    {
        "directive": {
            "header": {
                "namespace": "DNA.ColorControl",
                "name": "SetColor",
                "interfaceVersion": "2",
                "messageId": "1bd5d003-31b9-476f-ad03-71d471922820",
            },
            "endpoint": {
                "scope": {
                    "type": "",
                    "token": "some-access-token"
                },
                "endpointId": "appliance-001",
		  "devicePairedInfo":devicePairedInfo,
                "cookie": {}
            },
            "payload": {
                "color": {
                    "hue": 350.5,
                    "saturation": 0.7138,
                    "brightness": 0.6524
                }
            }
        }
    }
```
* 响应
```

    {
      "context": {
        "properties": [
            {
               "namespace": "DNA.ColorControl",
               "name": "color",
               "value":{
                    "hue": 350.5,
                    "saturation": 0.7138,
                    "brightness": 0.6524
               },
               "timeOfSample": "2017-02-03T16:20:50.52Z",
            }
        ]
      },
      "event": {
          "header": {
          "messageId": "30d2cd1a-ce4f-4542-aa5e-04bd0a6492d5",
          "name": "Response",
          "payloadVersion": "2"
        },
        "endpoint": {
          "scope": {
            "type": "",
            "token": "some-access-token"
          },
          "endpointId": "appliance-001"
        },
        "payload": {
        }
      }
    }
```

<span style="color:#ccc">3.8</span>颜色名称控制

控制设备的颜色

接口名称：DNA.ColorNameControl

请求
```
   

    {
        "directive": {
            "header": {
                "namespace": "DNA.ColorNameControl",
                "name": "SetColorName",
                "interfaceVersion": "2",
                "messageId": "1bd5d003-31b9-476f-ad03-71d471922820",
            },
            "endpoint": {
                "scope": {
                    "type": "",
                    "token": "some-access-token"
                },
                "endpointId": "appliance-001",
		  "devicePairedInfo":devicePairedInfo,
                "cookie": {}
            },
            "payload": {
                "colorName": "RED"
            }
        }
    }
```
响应
```
   

    {
      "context": {
        "properties": [
            {
               "namespace": "DNA.ColorNameControl",
               "name": "colorName",
               "value":"RED",
               "timeOfSample": "2017-02-03T16:20:50.52Z",
            }
        ]
      },
      "event": {
          "header": {
          "messageId": "30d2cd1a-ce4f-4542-aa5e-04bd0a6492d5",
          "name": "Response",
          "payloadVersion": "2"
        },
        "endpoint": {
          "scope": {
            "type": "",
            "token": "some-access-token"
          },
          "endpointId": "appliance-001"
        },
        "payload": {
        }
      }
    }
```
<span style="color:#ccc">3.9</span>色温控制


    控制设备的色温
    
    接口名称：DNA.ColorTempControl

* 设置色温请求
```    
   

    {
      "directive": {
        "header": {
          "namespace": "DNA.ColorTempControl",
          "name": "SetColorTemp",
          "interfaceVersion": "2",
          "messageId": "1bd5d003-31b9-476f-ad03-71d471922820",
        },
        "endpoint": {
          "scope": {
            "type": "",
            "token": "some-access-token"
          },
          "endpointId": "appliance-001",
		  "devicePairedInfo":devicePairedInfo,
          "cookie": {}
        },
        "payload": {
          "colortemp": 3000
        }
      }
    }
```    

* 设置色温响应
```    
   

    {
      "context": {
        "properties": [
            {
               "namespace": "DNA.ColorTempControl",
               "name": "colortemp",
               "value":3000,
               "timeOfSample": "2017-02-03T16:20:50.52Z",
            }
        ]
      },
      "event": {
          "header": {
          "messageId": "30d2cd1a-ce4f-4542-aa5e-04bd0a6492d5",
          "name": "Response",
          "payloadVersion": "2"
        },
        "endpoint": {
          "scope": {
            "type": "",
            "token": "some-access-token"
          },
          "endpointId": "appliance-001"
        },
        "payload": {
        }
      }
    }
```
    
<span style="color:#ccc">3.10</span>亮度控制


    控制设备的亮度
    
    接口名称：DNA.BrightnessControl

* 设置亮度请求
```    
   

    {
      "directive": {
        "header": {
          "namespace": "DNA.BrightnessControl",
          "name": "SetBrightness",
          "interfaceVersion": "2",
          "messageId": "1bd5d003-31b9-476f-ad03-71d471922820",
        },
        "endpoint": {
          "scope": {
            "type": "",
            "token": "some-access-token"
          },
          "endpointId": "appliance-001",
		  "devicePairedInfo":devicePairedInfo,
          "cookie": {}
        },
        "payload": {
          "brightness": 42
        }
      }
    }
```    

* 设置亮度响应
```    
   

    {
      "context": {
        "properties": [
            {
               "namespace": "DNA.BrightnessControl",
               "name": "brightness",
               "value":42,
               "timeOfSample": "2017-02-03T16:20:50.52Z",
            }
        ]
      },
      "event": {
          "header": {
          "messageId": "30d2cd1a-ce4f-4542-aa5e-04bd0a6492d5",
          "name": "Response",
          "payloadVersion": "2"
        },
        "endpoint": {
          "scope": {
            "type": "",
            "token": "some-access-token"
          },
          "endpointId": "appliance-001"
        },
        "payload": {
        }
      }
    }
```
* 按步长设置亮度请求
    
    正数表示增加，负数表示减少.
```    
   

    {
      "directive": {
        "header": {
          "namespace": "DNA.BrightnessControl",
          "name": "AdjustBrightness",
          "interfaceVersion": "2",
          "messageId": "1bd5d003-31b9-476f-ad03-71d471922820",
        },
        "endpoint": {
          "scope": {
            "type": "",
            "token": "some-access-token"
          },
          "endpointId": "appliance-001",
		  "devicePairedInfo":devicePairedInfo,
          "cookie": {}
        },
        "payload": {
          "brightnessSteps": 42
        }
      }
    }
```

* 按步长设置亮度响应
```    
   

    {
      "context": {
        "properties": [
            {
               "namespace": "DNA.BrightnessControl",
               "name": "brightness",
               "value":42,
               "timeOfSample": "2017-02-03T16:20:50.52Z",
            }
        ]
      },
      "event": {
          "header": {
          "messageId": "30d2cd1a-ce4f-4542-aa5e-04bd0a6492d5",
          "name": "Response",
          "payloadVersion": "2"
        },
        "endpoint": {
          "scope": {
            "type": "",
            "token": "some-access-token"
          },
          "endpointId": "appliance-001"
        },
        "payload": {
        }
      }
    }
```

<span style="color:#ccc">3.11</span>百分比控制

    控制设备属性的百分比
    
    接口名称：DNA.PercentageControl
    
    请求：
```
   

    {
      "directive": {
        "header": {
          "namespace": "DNA.PercentageControl",
          "name": "SetPercentage",
          "interfaceVersion": "2",
          "messageId": "1bd5d003-31b9-476f-ad03-71d471922820",
        },
        "endpoint": {
          "scope": {
            "type": "",
            "token": "some-access-token"
          },
          "endpointId": "appliance-001",
		  "devicePairedInfo":devicePairedInfo,
          "cookie": {}
        },
        "payload": {
          "percentage": 74
        }
      }
    }
```
    响应：
```
   

    {
      "context": {
        "properties": [
            {
               "namespace": "DNA.PercentageControl",
               "name": "percentage",
               "value":42,
               "timeOfSample": "2017-02-03T16:20:50.52Z",
            }
        ]
      },
      "event": {
          "header": {
          "messageId": "30d2cd1a-ce4f-4542-aa5e-04bd0a6492d5",
          "name": "Response",
          "payloadVersion": "2"
        },
        "endpoint": {
          "scope": {
            "type": "",
            "token": "some-access-token"
          },
          "endpointId": "appliance-001"
        },
        "payload": {
        }
      }
    }
```
<span style="color:#ccc">3.12</span>温控器控制

    控制可以调节温度的设备
    
    接口名称：DNA.ThermostatControl
    
    * 目标温度控制
    
    请求：
```
   

    {
      "directive": {
        "header": {
          "namespace": "DNA.ThermostatControl",
          "name": "SetTargetTemperature",
          "interfaceVersion": "2",
          "messageId": "1bd5d003-31b9-476f-ad03-71d471922820",
        },
        "endpoint": {
          "scope": {
            "type": "",
            "token": "some-access-token"
          },
          "endpointId": "appliance-001",
		  "devicePairedInfo":devicePairedInfo,
          "cookie": {}
        },
        "payload": {
          "targetPoint": {
                "value":23.0,
                "scale":"CELSIUS"
            }
        }
      }
    }
```
    响应：
```
   

    {
      "context": {
        "properties": [
            {
               "namespace": "DNA.ThermostatControl",
               "name": "targetPoint",
               "value":{
                    "value":23.0,
                    "scale":"CELSIUS"
               },
               "timeOfSample": "2017-02-03T16:20:50.52Z",
            }
        ]
      },
      "event": {
          "header": {
          "messageId": "30d2cd1a-ce4f-4542-aa5e-04bd0a6492d5",
          "name": "Response",
          "payloadVersion": "2"
        },
        "endpoint": {
          "scope": {
            "type": "",
            "token": "some-access-token"
          },
          "endpointId": "appliance-001"
        },
        "payload": {
        }
      }
    }
```

* 步长温度控制
    
    请求：
```
   

    {
      "directive": {
        "header": {
          "namespace": "DNA.ThermostatControl",
          "name": "AdjustTargetTemperature",
          "interfaceVersion": "2",
          "messageId": "1bd5d003-31b9-476f-ad03-71d471922820",
        },
        "endpoint": {
          "scope": {
            "type": "",
            "token": "some-access-token"
          },
          "endpointId": "appliance-001",
		  "devicePairedInfo":devicePairedInfo,
          "cookie": {}
        },
        "payload": {
          "targetPointSteps": {
                "value":-2,
                "scale":"CELSIUS"
            }
        }
      }
    }
```
    响应：
```
   

    {
      "context": {
        "properties": [
            {
               "namespace": "DNA.ThermostatControl",
               "name": "targetPointSteps",
               "value":{
                    "value":-2,
                    "scale":"CELSIUS"
               },
               "timeOfSample": "2017-02-03T16:20:50.52Z",
            }
        ]
      },
      "event": {
          "header": {
          "messageId": "30d2cd1a-ce4f-4542-aa5e-04bd0a6492d5",
          "name": "Response",
          "payloadVersion": "2"
        },
        "endpoint": {
          "scope": {
            "type": "",
            "token": "some-access-token"
          },
          "endpointId": "appliance-001"
        },
        "payload": {
        }
      }
    }
```

 * 固定目标温度控制
    单位恒定为摄氏度。
    
    请求：
```
   

    {
      "directive": {
        "header": {
          "namespace": "DNA.ThermostatControl",
          "name": "SetFixedTargetTemperature",
          "interfaceVersion": "2",
          "messageId": "1bd5d003-31b9-476f-ad03-71d471922820",
        },
        "endpoint": {
          "scope": {
            "type": "",
            "token": "some-access-token"
          },
          "endpointId": "appliance-001",
		  "devicePairedInfo":devicePairedInfo,
          "cookie": {}
        },
        "payload": {
          "fixedTargetTemperature": 23
        }
      }
    }
```
    响应：
```
   

    {
      "context": {
        "properties": [
            {
               "namespace": "DNA.ThermostatControl",
               "name": "fixedTargetTemperature",
               "value":23,
               "timeOfSample": "2017-02-03T16:20:50.52Z",
            }
        ]
      },
      "event": {
          "header": {
          "messageId": "30d2cd1a-ce4f-4542-aa5e-04bd0a6492d5",
          "name": "Response",
          "payloadVersion": "2"
        },
        "endpoint": {
          "scope": {
            "type": "",
            "token": "some-access-token"
          },
          "endpointId": "appliance-001"
        },
        "payload": {
        }
      }
    }
```
* 固定步长温度控制
    
    请求：
```
   

    {
      "directive": {
        "header": {
          "namespace": "DNA.ThermostatControl",
          "name": "AdjustFixedTargetTemperature",
          "interfaceVersion": "2",
          "messageId": "1bd5d003-31b9-476f-ad03-71d471922820",
        },
        "endpoint": {
          "scope": {
            "type": "",
            "token": "some-access-token"
          },
          "endpointId": "appliance-001",
		  "devicePairedInfo":devicePairedInfo,
          "cookie": {}
        },
        "payload": {
          "fixedTargetTemperatureSteps": 1
        }
      }
    }
```
    响应：
```
   

    {
      "context": {
        "properties": [
            {
               "namespace": "DNA.ThermostatControl",
               "name": "fixedTargetTemperatureSteps",
               "value":1,
               "timeOfSample": "2017-02-03T16:20:50.52Z",
            }
        ]
      },
      "event": {
          "header": {
          "messageId": "30d2cd1a-ce4f-4542-aa5e-04bd0a6492d5",
          "name": "Response",
          "payloadVersion": "2"
        },
        "endpoint": {
          "scope": {
            "type": "",
            "token": "some-access-token"
          },
          "endpointId": "appliance-001"
        },
        "payload": {
        }
      }
    }
```
* 模式控制


    请求：
```
   

    {
      "directive": {
        "header": {
          "namespace": "DNA.ThermostatControl",
          "name": "SetMode",
          "interfaceVersion": "2",
          "messageId": "1bd5d003-31b9-476f-ad03-71d471922820",
        },
        "endpoint": {
          "scope": {
            "type": "",
            "token": "some-access-token"
          },
          "endpointId": "appliance-001",
		  "devicePairedInfo":devicePairedInfo,
          "cookie": {}
        },
        "payload": {
          "mode": "COLD"
        }
      }
    }
```
    响应：
```
   

    {
      "context": {
        "properties": [
            {
               "namespace": "DNA.ThermostatControl",
               "name": "mode",
               "value":"COLD",
               "timeOfSample": "2017-02-03T16:20:50.52Z",
            }
        ]
      },
      "event": {
          "header": {
          "messageId": "30d2cd1a-ce4f-4542-aa5e-04bd0a6492d5",
          "name": "Response",
          "payloadVersion": "2"
        },
        "endpoint": {
          "scope": {
            "type": "",
            "token": "some-access-token"
          },
          "endpointId": "appliance-001"
        },
        "payload": {
        }
      }
    }
```    
具体支持的模式列表，请参考`智能家居接口属性参考表`


<span style="color:#ccc">3.13</span>温度感知


    查询温度
    接口名称：DNA.TemperatureSensor

    请求
```    
   

    {
      "directive": {
        "header": {
          "namespace": "DNA.TemperatureSensor",
          "name": "ReportState",
          "interfaceVersion": "2",
          "messageId": "1bd5d003-31b9-476f-ad03-71d471922820",
        },
        "endpoint": {
          "scope": {
            "type": "",
            "token": "some-access-token"
          },
          "endpointId": "appliance-001",
		  "devicePairedInfo":devicePairedInfo,
          "cookie": {}
        },
        "payload": {}
      }
    }
```

    响应
```    
   

        {
          "context": {
            "properties": [
                {
                   "namespace": "DNA.TemperatureSensor",
                   "name": "temperature",
                   "value":{
                        "value":12,
                        "scale":"CELSIUS",
                        "attributeName":""
                        "scaleName":"",
                        "valueName":""
                   },
                   "timeOfSample": "2017-02-03T16:20:50.52Z",
                }
            ]
          },
          "event": {
              "header": {
              "messageId": "30d2cd1a-ce4f-4542-aa5e-04bd0a6492d5",
              "name": "StateReport",
              "payloadVersion": "2"
            },
            "endpoint": {
              "scope": {
                "type": "",
                "token": "some-access-token"
              },
              "endpointId": "appliance-001"
            },
            "payload": {
            }
          }
        }
```
<span style="color:#ccc">3.14</span>湿度感知


    查询湿度
    接口名称：DNA.HumiditySensor

    请求
```
    {
      "directive": {
        "header": {
          "namespace": "DNA.HumiditySensor",
          "name": "ReportState",
          "interfaceVersion": "2",
          "messageId": "1bd5d003-31b9-476f-ad03-71d471922820",
        },
        "endpoint": {
          "scope": {
            "type": "",
            "token": "some-access-token"
          },
          "endpointId": "appliance-001",
		  "devicePairedInfo":devicePairedInfo,
          "cookie": {}
        },
        "payload": {}
      }
    }
```

    响应
```
   

        {
          "context": {
            "properties": [
                {
                   "namespace": "DNA.HumiditySensor",
                   "name": "humidity",
                   "value":{
                        "value":12,
                        "scale":"",
                        "attributeName":""
                        "scaleName":"",
                        "valueName":""
                   },
                   "timeOfSample": "2017-02-03T16:20:50.52Z",
                }
            ]
          },
          "event": {
              "header": {
              "messageId": "30d2cd1a-ce4f-4542-aa5e-04bd0a6492d5",
              "name": "StateReport",
              "payloadVersion": "2"
            },
            "endpoint": {
              "scope": {
                "type": "",
                "token": "some-access-token"
              },
              "endpointId": "appliance-001"
            },
            "payload": {
            }
          }
        }
```
<span style="color:#ccc">3.15</span>PM2.5感知


    查询PM2.5
    接口名称：DNA.PM2_5Sensor

    请求
```
   
   

    {
      "directive": {
        "header": {
          "namespace": "DNA.PM2_5Sensor",
          "name": "ReportState",
          "interfaceVersion": "2",
          "messageId": "1bd5d003-31b9-476f-ad03-71d471922820",
        },
        "endpoint": {
          "scope": {
            "type": "",
            "token": "some-access-token"
          },
          "endpointId": "appliance-001",
		  "devicePairedInfo":devicePairedInfo,
          "cookie": {}
        },
        "payload": {}
      }
    }
```

    响应
```
   

        {
          "context": {
            "properties": [
                {
                   "namespace": "DNA.PM2_5Sensor",
                   "name": "pm2_5",
                   "value":{
                        "value":20,
                        "scale":"",
                        "attributeName":""
                        "scaleName":"",
                        "valueName":""
                   },
                   "timeOfSample": "2017-02-03T16:20:50.52Z",
                }
            ]
          },
          "event": {
              "header": {
              "messageId": "30d2cd1a-ce4f-4542-aa5e-04bd0a6492d5",
              "name": "StateReport",
              "payloadVersion": "2"
            },
            "endpoint": {
              "scope": {
                "type": "",
                "token": "some-access-token"
              },
              "endpointId": "appliance-001"
            },
            "payload": {
            }
          }
        }
```
<span style="color:#ccc">3.16</span>状态查询

    请求
```
       

        {
          "directive": {
            "header": {
              "messageId": "abc-123-def-456",
              "namespace": "DNA.TemperatureSensor"|“DNA”,
              "name": "ReportState",
              "interfaceVersion": "2"
            },
            "endpoint": {
              "endpointId": "appliance-001",
		  "devicePairedInfo":devicePairedInfo,
              "cookie": {},
              "scope":{ 
                    "type":"",
                    "token":"some-access-token"
              }
            },
            "payload": {
            }
          }
        }
```
    响应:
```
   

        {
          "context": {
            "properties": [
                {
                   "namespace": "DNA.TemperatureSensor",
                   "name": "temperature",
                   "value":{
                        "value":12,
                        "scale":"",
                        "attributeName":""
                        "scaleName":"",
                        "valueName":""
                   },
                   "timeOfSample": "2017-02-03T16:20:50.52Z",
                }
            ]
          },
          "event": {
              "header": {
              "messageId": "30d2cd1a-ce4f-4542-aa5e-04bd0a6492d5",
              "name": "StateReport",
              "payloadVersion": "2"
            },
            "endpoint": {
              "scope": {
                "type": "",
                "token": "some-access-token"
              },
              "endpointId": "appliance-001"
            },
            "payload": {
            }
          }
        }
```     
        
状态查询响应时，每个属性都会携带如下字段：

=====================         ==================
scale                            单位
attributeName                    属性名称
scaleName                        单位名称
valueName                        值名称
=====================         ==================

如果是查询一个endpoint的全部状态, namespace需要填DNA.

如果是查询单个属性，则填如对应属性的接口名称。



<span style="color:#ccc">3.17</span>变化通知


变化通知有三种通知：

1. 设备属性变化，比如温度，开关状态

2. 设备附件状态变化，比如用户的设备名称变化，设备在线情况变化，用户新增加/删除设备

当一个设备多个属性变化时，放到payload中，一起上报.如果发现是设备列表发生变化，那么需要重新调用
设备发现。

    上报格式:
```
   

        {
          "context": {
            "properties": []
          },
          "event": {
              "header": {
              "namespace": "DNA",
              "messageId": "30d2cd1a-ce4f-4542-aa5e-04bd0a6492d5",
              "name": "ChangeReport",
              "payloadVersion": "2"
            },
            "endpoint": {
              "scope": {
                "type": "",
                "token": "some-access-token"
              },
              "endpointId": "appliance-001",
			  "devicePairedInfo":{"did":"","pid":""},
            },
            "payload": {
              "reportType":"STATE_CHANGE",
              "change": {
                "cause": {
                  "type": "PHYSICAL_INTERACTION"
                },
                "properties": [
                  {
                    "namespace": "DNA.PowerControl",
                    "name": "powerState",
                    "value": "ON",
                    "timeOfSample": "2017-02-03T16:20:50.52Z",
                    "uncertaintyInMilliseconds": 0
                  },
                  {
                    "namespace": "DNA.PercentageControl",
                    "name": "percentage",
                    "value": 40,
                    "timeOfSample": "2017-02-03T16:20:50.52Z",
                  }
                ]
              }
            }
          }
        }
```

====================             =================            =======
 reportType                         说明                      备注
====================             =================            =======
STATE_CHANGE                       设备状态变化
ENDPOINT_CHANGE                    设备列表变化

====================             =================            =======

cause字段用来描述设备状态变化的原因，如果是设备列表变化，可以忽略这个字段。

<span style="color:#ccc">3.18</span>错误响应


    查询湿度
    接口名称：DNA.ErrorResponse

    响应
  ```  
   

        {
          "context": {},
          "event": {
              "header": {
              "namespace": "DNA",
              "messageId": "30d2cd1a-ce4f-4542-aa5e-04bd0a6492d5",
              "name": "ErrorResponse",
              "payloadVersion": "2"
            },
            "endpoint": {
              "scope": {
                "type": "",
                "token": "some-access-token"
              },
              "endpointId": "appliance-001"
            },
            "payload": {
                "type": "ENDPOIONT_UNREACHABLE",
                "message":"设备离线"
            }
          }
        }
```
   
```
        {
          "context": {},
          "event": {
              "header": {
              "namespace": "DNA",
              "messageId": "30d2cd1a-ce4f-4542-aa5e-04bd0a6492d5",
              "name": "ErrorResponse",
              "payloadVersion": "2"
            },
            "endpoint": {
              "scope": {
                "type": "",
                "token": "some-access-token"
              },
              "endpointId": "appliance-001"
            },
            "payload": {
                "type": "VALUE_OUT_OF_RANGE",
                "message":"值越界",
                "validRange": {
                    "minimumValue":10,
                    "maximumValue":200
                }
            }
          }
```
<span style="color:#ccc">3.19</span>场景控制

控制场景

接口名称: DNA.SceneControl

* 执行场景请求

请求例子
```   

    {
      "directive": {
        "header": {
           "namespace": "DNA.SceneControl",
           "name": "Activate",
           "interfaceVersion": "2",
           "messageId": "1bd5d003-31b9-476f-ad03-71d471922820",
        },
        "endpoint": {
          "scope": {
             "type": "",
             "token": "some-access-token"
          },
          "endpointId": "appliance-001",
		  "devicePairedInfo":devicePairedInfo,
          "cookie": {}
        },
        "payload": {
        }
      }
    }

```
响应例子
```

   

    {
      "context": {
      },
      "event": {
        "header": {
           "namespace": "DNA.SceneControl",
           "name": "ActivationStarted",
           "interfaceVersion": "2",
           "messageId": "5f8a426e-01e4-4cc9-8b79-65f8bd0fd8a4",
        },
        "endpoint": {
          "scope": {
            "type": "",
            "token": "some-access-token"
          },
          "endpointId": "appliance-001"
        },
        "payload": {
        }
      }
    }
```
* 取消场景请求

请求例子
```   

    {
      "directive": {
        "header": {
           "namespace": "DNA.SceneControl",
           "name": "Deactivate",
           "interfaceVersion": "2",
           "messageId": "1bd5d003-31b9-476f-ad03-71d471922820",
        },
        "endpoint": {
          "scope": {
             "type": "",
             "token": "some-access-token"
          },
          "endpointId": "appliance-001",
		  "devicePairedInfo":devicePairedInfo,
          "cookie": {}
        },
        "payload": {
        }
      }
    }


```
响应例子
```

   

    {
      "context": {
      },
      "event": {
        "header": {
           "namespace": "DNA.SceneControl",
           "name": "DeactivationStarted",
           "interfaceVersion": "2",
           "messageId": "5f8a426e-01e4-4cc9-8b79-65f8bd0fd8a4",
        },
        "endpoint": {
          "scope": {
            "type": "",
            "token": "some-access-token"
          },
          "endpointId": "appliance-001"
        },
        "payload": {
        }
      }
    }
```

<span style="color:#ccc">3.20</span>运动控制

控制设备的动作，所有返回是统一的。

接口名称：DNA.MotionControl

* 开始请求


   
```
    {
      "directive": {
        "header": {
          "namespace": "DNA.MotionControl",
          "name": "Start",
          "messageId": "5f8a426e-01e4-4cc9-8b79-65f8bd0fd8a4",
          "payloadVersion": "2"
        },
        "endpoint": {
          "scope": {
            "type": "",
            "token": "<OAuth2认证后得到的access_token>"
          },
          "endpointId": "<设备ID，发现时返回>",
		  "devicePairedInfo":devicePairedInfo,
          "cookie": {
          }
        },
        "payload": {
        }
      }
    }
```

* 暂停请求

   
```
    {
      "directive": {
        "header": {
          "namespace": "DNA.MotionControl",
          "name": "Pause",
          "messageId": "5f8a426e-01e4-4cc9-8b79-65f8bd0fd8a4",
          "payloadVersion": "2"
        },
        "endpoint": {
          "scope": {
            "type": "",
            "token": "<OAuth2认证后得到的access_token>"
          },
          "endpointId": "<设备ID，发现时返回>",
		  "devicePairedInfo":devicePairedInfo,
          "cookie": {
          }
        },
        "payload": {
        }
      }
    }
```
* 停止请求
```
   

    {
      "directive": {
        "header": {
          "namespace": "DNA.MotionControl",
          "name": "Stop",
          "messageId": "5f8a426e-01e4-4cc9-8b79-65f8bd0fd8a4",
          "payloadVersion": "2"
        },
        "endpoint": {
          "scope": {
            "type": "",
            "token": "<OAuth2认证后得到的access_token>"
          },
          "endpointId": "<设备ID，发现时返回>",
		  "devicePairedInfo":devicePairedInfo,
          "cookie": {
          }
        },
        "payload": {
        }
      }
    }
```
响应
```

   

    {
      "context": {
        "properties": [
        ]
      },
      "event": {
          "header": {
          "messageId": "30d2cd1a-ce4f-4542-aa5e-04bd0a6492d5",
          "name": "Response",
          "payloadVersion": "2"
        },
        "endpoint": {
          "scope": {
            "type": "",
            "token": "some-access-token"
          },
          "endpointId": "appliance-001"
        },
        "payload": {
        }
      }
    }
```
<span style="color:#ccc">3.21</span>文本控制

通过文本字符串控制设备或者场景

接口名称: DNA.TextControl

请求例子
```   

    {
      "directive": {
        "header": {
           "namespace": "DNA.TextControl",
           "name": "Request",
           "interfaceVersion": "2",
           "messageId": "1bd5d003-31b9-476f-ad03-71d471922820",
        },
        "endpoint": {
          "scope": {
             "type": "",
             "token": "some-access-token"
          },
          "cookie": {}
        },
        "payload": {
          "text":"",
          "additionals":{}
        }
      }
    }

```
响应例子
```

   

    {
      "context": {
      },
      "event": {
        "header": {
           "namespace": "DNA.TextControl",
           "name": "Response",
           "interfaceVersion": "2",
           "messageId": "5f8a426e-01e4-4cc9-8b79-65f8bd0fd8a4",
        },
        "endpoint": {
          "scope": {
            "type": "",
            "token": "some-access-token"
          },
        },
        "payload": {
            "answerText":"",
            "endpoints":[
                {
                    "endpointId":"",
                    "actions": [{
                        "namespace":"",
                        "name":"",
                        "value":{}
                    }
                    ]
                }
            ]
        }
      }
    }
```

<span style="color:#ccc">3.22</span>自定义面板控制

控制RM自定义面板,需要运维设置是否返回自定义面板

接口名称: DNA.CustomizedRemoteControl

请求例子
```   

    {
      "directive": {
        "header": {
           "namespace": "DNA.CustomizedRemoteControl",
           "name": "打开",
           "interfaceVersion": "2",
           "messageId": "1bd5d003-31b9-476f-ad03-71d471922820",
        },
        "endpoint": {
          "scope": {
             "type": "",
             "token": "some-access-token"
          },
          "cookie": {}
        },
        "payload": {
          "text":"",
          "additionals":{}
        }
      }
    }

```
响应例子
```

   

    {
      "context": {
        "properties": []
      },
      "event": {
          "header": {
          "messageId": "30d2cd1a-ce4f-4542-aa5e-04bd0a6492d5",
          "name": "Response",
          "payloadVersion": "2"
        },
        "endpoint": {
          "scope": {
            "type": "",
            "token": "some-access-token"
          },
          "endpointId": "appliance-001"
        },
        "payload": {
        }
      }
    }
```

说明:

1.发现设备时能力中会返回自定义面板所支持的动作。

2.可以通过displayCategories中CUSTOMIZED来区分是否为自定义面板。

3.actions中的能力对应面板中保存的按键。

举例如下:
   
```
      {
                "endpointId":"3008880577263935437",
                "friendlyName":"自定义空调",
                "description":"BroadLink 智能遥控",
                "manufacturerName":"BroadLink",
                "icon":"https://ihcv0.ibroadlink.com/ec4appsysinfo/category2/CUSTOMIZED.png",
                "brand":"BroadLink",
                "roomName":"客厅",
                "displayCategories":[
                    "CUSTOMIZED"
                ],
                "cookie":{
                    "did":"xx",
                    "pid":"10039",
                    "sdid":"",
                    "spid":"",
                    "userid":"xx",
                    "devtype":0,
                    "devname":"自定义空调",
                    "moduleid":"3008880577263935437",
                    "moduletype":"20",
                    "familyid":"004734ce018aba779d8961378fa720bb",
                    "familyname":"我的家庭"
                },
                "isReachable":true,
                "capabilities":[
                    {
                        "type":"DNAInterface",
                        "interface":"DNA.CustomizedRemoteControl",
                        "version":"2",
                        "properties":{
                            "supported":null,
                            "proactivelyReported":false,
                            "retrievable":false
                        },
                        "actions":{
                            "supported":[
                                {
                                    "name":"打开"
                                },
                                {
                                    "name":"关闭"
                                }
                            ]
                        }
                    }
                ],
                "additional":null
      }

```

```
    {
      "directive": {
        "header": {
           "namespace": "DNA.PowerControl",
           "name": "ChangePowerState",
           "interfaceVersion": "2",
           "messageId": "1bd5d003-31b9-476f-ad03-71d471922820",
        },
        "endpoint": {
          "scope": {
             "type": "BearerToken",
             "token": "some-access-token"
          },
          "endpointId": "appliance-001",
          "cookie": {}
        },
        "payload": {
            "powerState": "ON"
        }
      }
    }
```

响应例子
```
    {
      "context": {
        "properties": [ {
           "namespace": "DNA.PowerControl",
           "name": "powerState",
           "value": "ON",
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

<span style="color:#ccc">3.2</span> 频道控制

控制电视/机顶盒频道

接口名称: DNA.ChannelControl

* ChangeChannel请求

请求例子
```   
    {
      "directive": {
        "header": {
           "namespace": "DNA.ChannelControl",
           "name": "ChangeChannel",
           "interfaceVersion": "2",
           "messageId": "1bd5d003-31b9-476f-ad03-71d471922820",
        },
        "endpoint": {
          "scope": {
             "type": "BearerToken",
             "token": "some-access-token"
          },
          "endpointId": "appliance-001",
          "cookie": {}
        },
        "payload": {
              "channelNumber":"1234"
        }
      }
    }
```

响应例子
```
    {
      "context": {
        "properties": [ {
           "namespace": "DNA.ChannelControl",
           "name": "channelNumber",
           "value":"123",
           "timeOfSample": "2017-02-03T16:20:50.52Z",
        } ]
      },
      "event": {
        "header": {
           "namespace": "DNA.ChannelControl",
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

* AdjustChannel请求

按步长调整频道

请求:
```
    {
      "directive": {
        "header": {
          "namespace": "DNA.ChannelControl",
          "name": "AdjustChannel",
          "messageId": "c8d53423-b49b-48ee-9181-f50acedf2870",
          "payloadVersion": "2"
        },
       "endpoint": {
          "scope": {
             "type": "BearerToken",
             "token": "some-access-token"
          },
          "endpointId": "appliance-001",
          "cookie": {}
        },
        "payload": {
          "channelSteps" : 1
        }
      }
    }
```

响应：
```
    {
      "context": {
        "properties": [
            {
               "namespace": "DNA.ChannelControl",
               "name": "channelSteps",
               "value": 1
               "timeOfSample": "2017-02-03T16:20:50.52Z",
            }
        ]
      },
      "event": {
          "header": {
          "messageId": "30d2cd1a-ce4f-4542-aa5e-04bd0a6492d5",
          "name": "Response",
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
        }
      }
    }
```

<span style="color:#ccc">3.3</span> 音量控制

控制设备的音量

接口名称: DNA.VolumeControl

* 步长调节请求
```
    {
      "directive": {
        "header": {
          "namespace": "DNA.VolumeControl",
          "name": "AdjustVolume",
          "messageId": "c8d53423-b49b-48ee-9181-f50acedf2870",
          "payloadVersion": "2"
        },
        "endpoint": {
          "scope": {
            "type": "BearerToken",
            "token": "some-access-token"
          },
          "endpointId": "appliance-001",
          "cookie": {}
        },
        "payload": {
          "volumeSteps": 20
        }
      }
    }
```
响应
```
    {
      "context": {
        "properties": [
            {
               "namespace": "DNA.VolumeControl",
               "name": "volumeSteps",
               "value": 20
               "timeOfSample": "2017-02-03T16:20:50.52Z",
            }
        ]
      },
      "event": {
          "header": {
          "messageId": "30d2cd1a-ce4f-4542-aa5e-04bd0a6492d5",
          "name": "Response",
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
        }
      }
    }
```

* 直接控制请求
```
   
    {
      "directive": {
        "header": {
          "namespace": "DNA.VolumeControl",
          "name": "SetVolume",
          "messageId": "5f8a426e-01e4-4cc9-8b79-65f8bd0fd8a4",
          "payloadVersion": "2"
        },
        "endpoint": {
          "scope": {
            "type": "BearerToken",
            "token": "<some-access-token>"
          },
          "endpointId": "<appliance-001>",
          "cookie": {
             
          }
        },
        "payload": {
          "volume": 50
        }
      }
    }
```

响应
```
    {
      "context": {
        "properties": [
            {
               "namespace": "DNA.VolumeControl",
               "name": "volume",
               "value": 50
               "timeOfSample": "2017-02-03T16:20:50.52Z",
            }
        ]
      },
      "event": {
          "header": {
          "messageId": "30d2cd1a-ce4f-4542-aa5e-04bd0a6492d5",
          "name": "Response",
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
        }
      }
    }
```
* 静音控制请求
```
    {
      "directive": {
        "header": {
          "namespace": "DNA.VolumeControl",
          "name": "SetMute",
          "messageId": "c8d53423-b49b-48ee-9181-f50acedf2870",
          "payloadVersion": "3"
        },
        "endpoint": {
          "scope": {
            "type": "BearerToken",
            "token": "<some-access-token>"
          },
          "endpointId": "<appliance-001>",
          "cookie": {}
        },
        "payload": {
          "mute": true
        }
      }
    }
```
响应
```
    {
      "context": {
        "properties": [
            {
               "namespace": "DNA.VolumeControl",
               "name": "mute",
               "value": true
               "timeOfSample": "2017-02-03T16:20:50.52Z",
            }
        ]
      },
      "event": {
          "header": {
          "messageId": "30d2cd1a-ce4f-4542-aa5e-04bd0a6492d5",
          "name": "Response",
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
        }
      }
    }
```

<span style="color:#ccc">3.4</span>播放控制

控制设备的播放/暂停等,由于播放控制不涉及状态，所有返回是统一的。

接口名称：DNA.PlaybackControl

* 播放请求
```
    {
      "directive": {
        "header": {
          "namespace": "DNA.PlaybackController",
          "name": "Play",
          "messageId": "5f8a426e-01e4-4cc9-8b79-65f8bd0fd8a4",
          "payloadVersion": "2"
        },
        "endpoint": {
          "scope": {
            "type": "BearerToken",
            "token": "<OAuth2认证后得到的access_token>"
          },
          "endpointId": "<设备ID，发现时返回>",
		  "devicePairedInfo":devicePairedInfo,
          "cookie": {
          }
        },
        "payload": {
        }
      }
    }
```

* 暂停请求

   
```
    {
      "directive": {
        "header": {
          "namespace": "DNA.PlaybackController",
          "name": "Pause",
          "messageId": "5f8a426e-01e4-4cc9-8b79-65f8bd0fd8a4",
          "payloadVersion": "2"
        },
        "endpoint": {
          "scope": {
            "type": "BearerToken",
            "token": "<OAuth2认证后得到的access_token>"
          },
          "endpointId": "<设备ID，发现时返回>",
		  "devicePairedInfo":devicePairedInfo,
          "cookie": {
          }
        },
        "payload": {
        }
      }
    }
```
* 继续请求
```
   

    {
      "directive": {
        "header": {
          "namespace": "DNA.PlaybackController",
          "name": "Resume",
          "messageId": "5f8a426e-01e4-4cc9-8b79-65f8bd0fd8a4",
          "payloadVersion": "2"
        },
        "endpoint": {
          "scope": {
            "type": "BearerToken",
            "token": "<OAuth2认证后得到的access_token>"
          },
          "endpointId": "<设备ID，发现时返回>",
		  "devicePairedInfo":devicePairedInfo,
          "cookie": {
          }
        },
        "payload": {
        }
      }
    }
 ```   
* 下一首请求
```
   

    {
      "directive": {
        "header": {
          "namespace": "DNA.PlaybackController",
          "name": "Next",
          "messageId": "5f8a426e-01e4-4cc9-8b79-65f8bd0fd8a4",
          "payloadVersion": "2"
        },
        "endpoint": {
          "scope": {
            "type": "BearerToken",
            "token": "<OAuth2认证后得到的access_token>"
          },
          "endpointId": "<设备ID，发现时返回>",
		  "devicePairedInfo":devicePairedInfo,
          "cookie": {
          }
        },
        "payload": {
        }
      }
    }
```
* 上一首请求
```
   

    {
      "directive": {
        "header": {
          "namespace": "DNA.PlaybackController",
          "name": "Previous",
          "messageId": "5f8a426e-01e4-4cc9-8b79-65f8bd0fd8a4",
          "payloadVersion": "2"
        },
        "endpoint": {
          "scope": {
            "type": "BearerToken",
            "token": "<OAuth2认证后得到的access_token>"
          },
          "endpointId": "<设备ID，发现时返回>",
		  "devicePairedInfo":devicePairedInfo,
          "cookie": {
          }
        },
        "payload": {
        }
      }
    }
```    
* 快进请求
```
   

    {
      "directive": {
        "header": {
          "namespace": "DNA.PlaybackController",
          "name": "FastForward",
          "messageId": "5f8a426e-01e4-4cc9-8b79-65f8bd0fd8a4",
          "payloadVersion": "2"
        },
        "endpoint": {
          "scope": {
            "type": "BearerToken",
            "token": "<OAuth2认证后得到的access_token>"
          },
          "endpointId": "<设备ID，发现时返回>",
		  "devicePairedInfo":devicePairedInfo,
          "cookie": {
          }
        },
        "payload": {
        }
      }
    }
```
* 回放请求
```
   

    {
      "directive": {
        "header": {
          "namespace": "DNA.PlaybackController",
          "name": "Rewind",
          "messageId": "5f8a426e-01e4-4cc9-8b79-65f8bd0fd8a4",
          "payloadVersion": "2"
        },
        "endpoint": {
          "scope": {
            "type": "BearerToken",
            "token": "<OAuth2认证后得到的access_token>"
          },
          "endpointId": "<设备ID，发现时返回>",
		  "devicePairedInfo":devicePairedInfo,
          "cookie": {
          }
        },
        "payload": {
        }
      }
    }
```
* 响应
```
   

    {
      "context": {
        "properties": [
        ]
      },
      "event": {
          "header": {
          "messageId": "30d2cd1a-ce4f-4542-aa5e-04bd0a6492d5",
          "name": "Response",
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
        }
      }
    }
```    
    
<span style="color:#ccc">3.5</span>风速控制

    控制风扇的速度
    
    接口名称：DNA.WindSpeedControl
    
* 设置风速请求
```
    {
      "directive": {
        "header": {
          "namespace": "DNA.WindSpeedControl",
          "name": "SetWindSpeed",
          "interfaceVersion": "2",
          "messageId": "1bd5d003-31b9-476f-ad03-71d471922820",
        },
        "endpoint": {
          "scope": {
            "type": "BearerToken",
            "token": "some-access-token"
          },
          "endpointId": "appliance-001",
          "cookie": {}
        },
        "payload": {
          "windSpeed": "HIGH"
        }
      }
    }
```
响应:
```
   

    {
      "context": {
        "properties": [
            {
               "namespace": "DNA.PercentageControl",
               "name": "windSpeed",
               "value":"HIGH",
               "timeOfSample": "2017-02-03T16:20:50.52Z",
            }
        ]
      },
      "event": {
          "header": {
          "messageId": "30d2cd1a-ce4f-4542-aa5e-04bd0a6492d5",
          "name": "Response",
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
        }
      }
    }
```
具体支持的列表，请参考`智能家居接口属性参考表 `

* 步长调整风速请求
```
   

    {
      "directive": {
        "header": {
          "namespace": "DNA.WindSpeedControl",
          "name": "AdjustWindSpeed",
          "interfaceVersion": "2",
          "messageId": "1bd5d003-31b9-476f-ad03-71d471922820",
        },
        "endpoint": {
          "scope": {
            "type": "BearerToken",
            "token": "some-access-token"
          },
          "endpointId": "appliance-001",
          "cookie": {}
        },
        "payload": {
          "windSpeedSteps": 1
        }
      }
    }
```
响应:
```
   

    {
      "context": {
        "properties": [
            {
               "namespace": "DNA.PercentageControl",
               "name": "windSpeedSteps",
               "value":1,
               "timeOfSample": "2017-02-03T16:20:50.52Z",
            }
        ]
      },
      "event": {
          "header": {
          "messageId": "30d2cd1a-ce4f-4542-aa5e-04bd0a6492d5",
          "name": "Response",
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
        }
      }
    }
```

<span style="color:#ccc">3.6</span>风向控制

控制设备的风向，控制不涉及状态，所有返回是统一的。

接口名称：DNA.AirFlowControl

* 开启摆风请求
```

   

    {
      "directive": {
        "header": {
          "namespace": "DNA.AirFlowControl",
          "name": "Start",
          "messageId": "5f8a426e-01e4-4cc9-8b79-65f8bd0fd8a4",
          "payloadVersion": "2"
        },
        "endpoint": {
          "scope": {
            "type": "BearerToken",
            "token": "<OAuth2认证后得到的access_token>"
          },
          "endpointId": "<设备ID，发现时返回>",
		  "devicePairedInfo":devicePairedInfo,
          "cookie": {
          }
        },
        "payload": {
        }
      }
    }
```

* 停止摆风请求
```
   

    {
      "directive": {
        "header": {
          "namespace": "DNA.AirFlowControl",
          "name": "Stop",
          "messageId": "5f8a426e-01e4-4cc9-8b79-65f8bd0fd8a4",
          "payloadVersion": "2"
        },
        "endpoint": {
          "scope": {
            "type": "BearerToken",
            "token": "<OAuth2认证后得到的access_token>"
          },
          "endpointId": "<设备ID，发现时返回>",
		  "devicePairedInfo":devicePairedInfo,
          "cookie": {
          }
        },
        "payload": {
        }
      }
    }
```
* 水平摆风请求
```
   

    {
      "directive": {
        "header": {
          "namespace": "DNA.AirFlowControl",
          "name": "HorizontalFlow",
          "messageId": "5f8a426e-01e4-4cc9-8b79-65f8bd0fd8a4",
          "payloadVersion": "2"
        },
        "endpoint": {
          "scope": {
            "type": "BearerToken",
            "token": "<OAuth2认证后得到的access_token>"
          },
          "endpointId": "<设备ID，发现时返回>",
		  "devicePairedInfo":devicePairedInfo,
          "cookie": {
          }
        },
        "payload": {
        }
      }
    }
```   

* 垂直摆风请求
```
   

    {
      "directive": {
        "header": {
          "namespace": "DNA.AirFlowControl",
          "name": "VerticalFlow",
          "messageId": "5f8a426e-01e4-4cc9-8b79-65f8bd0fd8a4",
          "payloadVersion": "2"
        },
        "endpoint": {
          "scope": {
            "type": "BearerToken",
            "token": "<OAuth2认证后得到的access_token>"
          },
          "endpointId": "<设备ID，发现时返回>",
		  "devicePairedInfo":devicePairedInfo,
          "cookie": {
          }
        },
        "payload": {
        }
      }
    }
```    

响应：
```
   

    {
      "context": {
        "properties": [
        ]
      },
      "event": {
          "header": {
          "messageId": "30d2cd1a-ce4f-4542-aa5e-04bd0a6492d5",
          "name": "Response",
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
        }
      }
    }
```    

<span style="color:#ccc">3.7</span>颜色控制

控制设备的颜色

接口名称：DNA.ColorControl

* 请求
```
   

    {
        "directive": {
            "header": {
                "namespace": "DNA.ColorControl",
                "name": "SetColor",
                "interfaceVersion": "2",
                "messageId": "1bd5d003-31b9-476f-ad03-71d471922820",
            },
            "endpoint": {
                "scope": {
                    "type": "BearerToken",
                    "token": "some-access-token"
                },
                "endpointId": "appliance-001",
                "cookie": {}
            },
            "payload": {
                "color": {
                    "hue": 350.5,
                    "saturation": 0.7138,
                    "brightness": 0.6524
                }
            }
        }
    }
```
* 响应
```

    {
      "context": {
        "properties": [
            {
               "namespace": "DNA.ColorControl",
               "name": "color",
               "value":{
                    "hue": 350.5,
                    "saturation": 0.7138,
                    "brightness": 0.6524
               },
               "timeOfSample": "2017-02-03T16:20:50.52Z",
            }
        ]
      },
      "event": {
          "header": {
          "messageId": "30d2cd1a-ce4f-4542-aa5e-04bd0a6492d5",
          "name": "Response",
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
        }
      }
    }
```

<span style="color:#ccc">3.8</span>颜色名称控制

控制设备的颜色

接口名称：DNA.ColorNameControl

请求
```
   

    {
        "directive": {
            "header": {
                "namespace": "DNA.ColorNameControl",
                "name": "SetColorName",
                "interfaceVersion": "2",
                "messageId": "1bd5d003-31b9-476f-ad03-71d471922820",
            },
            "endpoint": {
                "scope": {
                    "type": "BearerToken",
                    "token": "some-access-token"
                },
                "endpointId": "appliance-001",
                "cookie": {}
            },
            "payload": {
                "colorName": "RED"
            }
        }
    }
```
响应
```
   

    {
      "context": {
        "properties": [
            {
               "namespace": "DNA.ColorNameControl",
               "name": "colorName",
               "value":"RED",
               "timeOfSample": "2017-02-03T16:20:50.52Z",
            }
        ]
      },
      "event": {
          "header": {
          "messageId": "30d2cd1a-ce4f-4542-aa5e-04bd0a6492d5",
          "name": "Response",
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
        }
      }
    }
```
<span style="color:#ccc">3.9</span>色温控制


    控制设备的色温
    
    接口名称：DNA.ColorTempControl

* 设置色温请求
```    
   

    {
      "directive": {
        "header": {
          "namespace": "DNA.ColorTempControl",
          "name": "SetColorTemp",
          "interfaceVersion": "2",
          "messageId": "1bd5d003-31b9-476f-ad03-71d471922820",
        },
        "endpoint": {
          "scope": {
            "type": "BearerToken",
            "token": "some-access-token"
          },
          "endpointId": "appliance-001",
          "cookie": {}
        },
        "payload": {
          "colortemp": 3000
        }
      }
    }
```    

* 设置色温响应
```    
   

    {
      "context": {
        "properties": [
            {
               "namespace": "DNA.ColorTempControl",
               "name": "colortemp",
               "value":3000,
               "timeOfSample": "2017-02-03T16:20:50.52Z",
            }
        ]
      },
      "event": {
          "header": {
          "messageId": "30d2cd1a-ce4f-4542-aa5e-04bd0a6492d5",
          "name": "Response",
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
        }
      }
    }
```
    
<span style="color:#ccc">3.10</span>亮度控制


    控制设备的亮度
    
    接口名称：DNA.BrightnessControl

* 设置亮度请求
```    
   

    {
      "directive": {
        "header": {
          "namespace": "DNA.BrightnessControl",
          "name": "SetBrightness",
          "interfaceVersion": "2",
          "messageId": "1bd5d003-31b9-476f-ad03-71d471922820",
        },
        "endpoint": {
          "scope": {
            "type": "BearerToken",
            "token": "some-access-token"
          },
          "endpointId": "appliance-001",
          "cookie": {}
        },
        "payload": {
          "brightness": 42
        }
      }
    }
```    

* 设置亮度响应
```    
   

    {
      "context": {
        "properties": [
            {
               "namespace": "DNA.BrightnessControl",
               "name": "brightness",
               "value":42,
               "timeOfSample": "2017-02-03T16:20:50.52Z",
            }
        ]
      },
      "event": {
          "header": {
          "messageId": "30d2cd1a-ce4f-4542-aa5e-04bd0a6492d5",
          "name": "Response",
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
        }
      }
    }
```
* 按步长设置亮度请求
    
    正数表示增加，负数表示减少.
```    
   

    {
      "directive": {
        "header": {
          "namespace": "DNA.BrightnessControl",
          "name": "AdjustBrightness",
          "interfaceVersion": "2",
          "messageId": "1bd5d003-31b9-476f-ad03-71d471922820",
        },
        "endpoint": {
          "scope": {
            "type": "BearerToken",
            "token": "some-access-token"
          },
          "endpointId": "appliance-001",
          "cookie": {}
        },
        "payload": {
          "brightnessSteps": 42
        }
      }
    }
```

* 按步长设置亮度响应
```    
   

    {
      "context": {
        "properties": [
            {
               "namespace": "DNA.BrightnessControl",
               "name": "brightness",
               "value":42,
               "timeOfSample": "2017-02-03T16:20:50.52Z",
            }
        ]
      },
      "event": {
          "header": {
          "messageId": "30d2cd1a-ce4f-4542-aa5e-04bd0a6492d5",
          "name": "Response",
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
        }
      }
    }
```

<span style="color:#ccc">3.11</span>百分比控制

    控制设备属性的百分比
    
    接口名称：DNA.PercentageControl
    
    请求：
```
   

    {
      "directive": {
        "header": {
          "namespace": "DNA.PercentageControl",
          "name": "SetPercentage",
          "interfaceVersion": "2",
          "messageId": "1bd5d003-31b9-476f-ad03-71d471922820",
        },
        "endpoint": {
          "scope": {
            "type": "BearerToken",
            "token": "some-access-token"
          },
          "endpointId": "appliance-001",
          "cookie": {}
        },
        "payload": {
          "percentage": 74
        }
      }
    }
```
    响应：
```
   

    {
      "context": {
        "properties": [
            {
               "namespace": "DNA.PercentageControl",
               "name": "percentage",
               "value":42,
               "timeOfSample": "2017-02-03T16:20:50.52Z",
            }
        ]
      },
      "event": {
          "header": {
          "messageId": "30d2cd1a-ce4f-4542-aa5e-04bd0a6492d5",
          "name": "Response",
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
        }
      }
    }
```
<span style="color:#ccc">3.12</span>温控器控制

    控制可以调节温度的设备
    
    接口名称：DNA.ThermostatControl
    
    * 目标温度控制
    
    请求：
```
   

    {
      "directive": {
        "header": {
          "namespace": "DNA.ThermostatControl",
          "name": "SetTargetTemperature",
          "interfaceVersion": "2",
          "messageId": "1bd5d003-31b9-476f-ad03-71d471922820",
        },
        "endpoint": {
          "scope": {
            "type": "BearerToken",
            "token": "some-access-token"
          },
          "endpointId": "appliance-001",
          "cookie": {}
        },
        "payload": {
          "targetPoint": {
                "value":23.0,
                "scale":"CELSIUS"
            }
        }
      }
    }
```
    响应：
```
   

    {
      "context": {
        "properties": [
            {
               "namespace": "DNA.ThermostatControl",
               "name": "targetPoint",
               "value":{
                    "value":23.0,
                    "scale":"CELSIUS"
               },
               "timeOfSample": "2017-02-03T16:20:50.52Z",
            }
        ]
      },
      "event": {
          "header": {
          "messageId": "30d2cd1a-ce4f-4542-aa5e-04bd0a6492d5",
          "name": "Response",
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
        }
      }
    }
```

* 步长温度控制
    
    请求：
```
   

    {
      "directive": {
        "header": {
          "namespace": "DNA.ThermostatControl",
          "name": "AdjustTargetTemperature",
          "interfaceVersion": "2",
          "messageId": "1bd5d003-31b9-476f-ad03-71d471922820",
        },
        "endpoint": {
          "scope": {
            "type": "BearerToken",
            "token": "some-access-token"
          },
          "endpointId": "appliance-001",
          "cookie": {}
        },
        "payload": {
          "targetPointSteps": {
                "value":-2,
                "scale":"CELSIUS"
            }
        }
      }
    }
```
    响应：
```
   

    {
      "context": {
        "properties": [
            {
               "namespace": "DNA.ThermostatControl",
               "name": "targetPointSteps",
               "value":{
                    "value":-2,
                    "scale":"CELSIUS"
               },
               "timeOfSample": "2017-02-03T16:20:50.52Z",
            }
        ]
      },
      "event": {
          "header": {
          "messageId": "30d2cd1a-ce4f-4542-aa5e-04bd0a6492d5",
          "name": "Response",
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
        }
      }
    }
```

 * 固定目标温度控制
    单位恒定为摄氏度。
    
    请求：
```
   

    {
      "directive": {
        "header": {
          "namespace": "DNA.ThermostatControl",
          "name": "SetFixedTargetTemperature",
          "interfaceVersion": "2",
          "messageId": "1bd5d003-31b9-476f-ad03-71d471922820",
        },
        "endpoint": {
          "scope": {
            "type": "BearerToken",
            "token": "some-access-token"
          },
          "endpointId": "appliance-001",
          "cookie": {}
        },
        "payload": {
          "fixedTargetTemperature": 23
        }
      }
    }
```
    响应：
```
   

    {
      "context": {
        "properties": [
            {
               "namespace": "DNA.ThermostatControl",
               "name": "fixedTargetTemperature",
               "value":23,
               "timeOfSample": "2017-02-03T16:20:50.52Z",
            }
        ]
      },
      "event": {
          "header": {
          "messageId": "30d2cd1a-ce4f-4542-aa5e-04bd0a6492d5",
          "name": "Response",
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
        }
      }
    }
```
* 固定步长温度控制
    
    请求：
```
   

    {
      "directive": {
        "header": {
          "namespace": "DNA.ThermostatControl",
          "name": "AdjustFixedTargetTemperature",
          "interfaceVersion": "2",
          "messageId": "1bd5d003-31b9-476f-ad03-71d471922820",
        },
        "endpoint": {
          "scope": {
            "type": "BearerToken",
            "token": "some-access-token"
          },
          "endpointId": "appliance-001",
          "cookie": {}
        },
        "payload": {
          "fixedTargetTemperatureSteps": 1
        }
      }
    }
```
    响应：
```
   

    {
      "context": {
        "properties": [
            {
               "namespace": "DNA.ThermostatControl",
               "name": "fixedTargetTemperatureSteps",
               "value":1,
               "timeOfSample": "2017-02-03T16:20:50.52Z",
            }
        ]
      },
      "event": {
          "header": {
          "messageId": "30d2cd1a-ce4f-4542-aa5e-04bd0a6492d5",
          "name": "Response",
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
        }
      }
    }
```
* 模式控制


    请求：
```
   

    {
      "directive": {
        "header": {
          "namespace": "DNA.ThermostatControl",
          "name": "SetMode",
          "interfaceVersion": "2",
          "messageId": "1bd5d003-31b9-476f-ad03-71d471922820",
        },
        "endpoint": {
          "scope": {
            "type": "BearerToken",
            "token": "some-access-token"
          },
          "endpointId": "appliance-001",
          "cookie": {}
        },
        "payload": {
          "mode": "COLD"
        }
      }
    }
```
    响应：
```
   

    {
      "context": {
        "properties": [
            {
               "namespace": "DNA.ThermostatControl",
               "name": "mode",
               "value":"COLD",
               "timeOfSample": "2017-02-03T16:20:50.52Z",
            }
        ]
      },
      "event": {
          "header": {
          "messageId": "30d2cd1a-ce4f-4542-aa5e-04bd0a6492d5",
          "name": "Response",
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
        }
      }
    }
```    
具体支持的模式列表，请参考`智能家居接口属性参考表`


<span style="color:#ccc">3.13</span>温度感知


    查询温度
    接口名称：DNA.TemperatureSensor

    请求
```    
   

    {
      "directive": {
        "header": {
          "namespace": "DNA.TemperatureSensor",
          "name": "ReportState",
          "interfaceVersion": "2",
          "messageId": "1bd5d003-31b9-476f-ad03-71d471922820",
        },
        "endpoint": {
          "scope": {
            "type": "BearerToken",
            "token": "some-access-token"
          },
          "endpointId": "appliance-001",
          "cookie": {}
        },
        "payload": {}
      }
    }
```

    响应
```    
   

        {
          "context": {
            "properties": [
                {
                   "namespace": "DNA.TemperatureSensor",
                   "name": "temperature",
                   "value":{
                        "value":12,
                        "scale":"CELSIUS",
                        "attributeName":""
                        "scaleName":"",
                        "valueName":""
                   },
                   "timeOfSample": "2017-02-03T16:20:50.52Z",
                }
            ]
          },
          "event": {
              "header": {
              "messageId": "30d2cd1a-ce4f-4542-aa5e-04bd0a6492d5",
              "name": "StateReport",
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
            }
          }
        }
```
<span style="color:#ccc">3.14</span>湿度感知


    查询湿度
    接口名称：DNA.HumiditySensor

    请求
    ```
   
   

    {
      "directive": {
        "header": {
          "namespace": "DNA.HumiditySensor",
          "name": "ReportState",
          "interfaceVersion": "2",
          "messageId": "1bd5d003-31b9-476f-ad03-71d471922820",
        },
        "endpoint": {
          "scope": {
            "type": "BearerToken",
            "token": "some-access-token"
          },
          "endpointId": "appliance-001",
          "cookie": {}
        },
        "payload": {}
      }
    }
    ```

    响应
    ```
   

        {
          "context": {
            "properties": [
                {
                   "namespace": "DNA.HumiditySensor",
                   "name": "humidity",
                   "value":{
                        "value":12,
                        "scale":"",
                        "attributeName":""
                        "scaleName":"",
                        "valueName":""
                   },
                   "timeOfSample": "2017-02-03T16:20:50.52Z",
                }
            ]
          },
          "event": {
              "header": {
              "messageId": "30d2cd1a-ce4f-4542-aa5e-04bd0a6492d5",
              "name": "StateReport",
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
            }
          }
        }
```
<span style="color:#ccc">3.15</span>PM2.5感知


    查询PM2.5
    接口名称：DNA.PM2_5Sensor

    请求
    ```
   
   

    {
      "directive": {
        "header": {
          "namespace": "DNA.PM2_5Sensor",
          "name": "ReportState",
          "interfaceVersion": "2",
          "messageId": "1bd5d003-31b9-476f-ad03-71d471922820",
        },
        "endpoint": {
          "scope": {
            "type": "BearerToken",
            "token": "some-access-token"
          },
          "endpointId": "appliance-001",
          "cookie": {}
        },
        "payload": {}
      }
    }
```

    响应
    ```
   

        {
          "context": {
            "properties": [
                {
                   "namespace": "DNA.PM2_5Sensor",
                   "name": "pm2_5",
                   "value":{
                        "value":20,
                        "scale":"",
                        "attributeName":""
                        "scaleName":"",
                        "valueName":""
                   },
                   "timeOfSample": "2017-02-03T16:20:50.52Z",
                }
            ]
          },
          "event": {
              "header": {
              "messageId": "30d2cd1a-ce4f-4542-aa5e-04bd0a6492d5",
              "name": "StateReport",
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
            }
          }
        }
```
<span style="color:#ccc">3.16</span>状态查询

    请求
```
       

        {
          "directive": {
            "header": {
              "messageId": "abc-123-def-456",
              "namespace": "DNA.TemperatureSensor"|“DNA”,
              "name": "ReportState",
              "interfaceVersion": "2"
            },
            "endpoint": {
              "endpointId": "appliance-001",
              "cookie": {},
              "scope":{ 
                    "type":"BearerToken",
                    "token":"some-access-token"
              }
            },
            "payload": {
            }
          }
        }
```
    响应:
```
   

        {
          "context": {
            "properties": [
                {
                   "namespace": "DNA.TemperatureSensor",
                   "name": "temperature",
                   "value":{
                        "value":12,
                        "scale":"",
                        "attributeName":""
                        "scaleName":"",
                        "valueName":""
                   },
                   "timeOfSample": "2017-02-03T16:20:50.52Z",
                }
            ]
          },
          "event": {
              "header": {
              "messageId": "30d2cd1a-ce4f-4542-aa5e-04bd0a6492d5",
              "name": "StateReport",
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
            }
          }
        }
   ```     
        
状态查询响应时，每个属性都会携带如下字段：

=====================         ==================
scale                            单位
attributeName                    属性名称
scaleName                        单位名称
valueName                        值名称
=====================         ==================

如果是查询一个endpoint的全部状态, namespace需要填DNA.

如果是查询单个属性，则填如对应属性的接口名称。

<span style="color:#ccc">3.17</span>变化通知


变化通知有三种通知：

1. 设备属性变化，比如温度，开关状态

2. 设备附件状态变化，比如用户的设备名称变化，设备在线情况变化，用户新增加/删除设备

当一个设备多个属性变化时，放到payload中，一起上报.如果发现是设备列表发生变化，那么需要重新调用
设备发现。

    上报格式:
```
   

        {
          "context": {
            "properties": []
          },
          "event": {
              "header": {
              "namespace": "DNA",
              "messageId": "30d2cd1a-ce4f-4542-aa5e-04bd0a6492d5",
              "name": "ChangeReport",
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
              "reportType":"STATE_CHANGE",
              "change": {
                "cause": {
                  "type": "PHYSICAL_INTERACTION"
                },
                "properties": [
                  {
                    "namespace": "DNA.PowerControl",
                    "name": "powerState",
                    "value": "ON",
                    "timeOfSample": "2017-02-03T16:20:50.52Z",
                    "uncertaintyInMilliseconds": 0
                  },
                  {
                    "namespace": "DNA.PercentageControl",
                    "name": "percentage",
                    "value": 40,
                    "timeOfSample": "2017-02-03T16:20:50.52Z",
                  }
                ]
              }
            }
          }
        }
```

====================             =================            =======
 reportType                         说明                      备注
====================             =================            =======
STATE_CHANGE                       设备状态变化
ENDPOINT_CHANGE                    设备列表变化

====================             =================            =======

cause字段用来描述设备状态变化的原因，如果是设备列表变化，可以忽略这个字段。

<span style="color:#ccc">3.18</span>错误响应


    查询湿度
    接口名称：DNA.ErrorResponse

    响应
  ```  
   

        {
          "context": {},
          "event": {
              "header": {
              "namespace": "DNA",
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
                "type": "ENDPOIONT_UNREACHABLE",
                "message":"设备离线"
            }
          }
        }
```
   
```
        {
          "context": {},
          "event": {
              "header": {
              "namespace": "DNA",
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
                "type": "VALUE_OUT_OF_RANGE",
                "message":"值越界",
                "validRange": {
                    "minimumValue":10,
                    "maximumValue":200
                }
            }
          }
```
<span style="color:#ccc">3.19</span>场景控制

控制场景

接口名称: DNA.SceneControl

* 执行场景请求

请求例子
```   

    {
      "directive": {
        "header": {
           "namespace": "DNA.SceneControl",
           "name": "Activate",
           "interfaceVersion": "2",
           "messageId": "1bd5d003-31b9-476f-ad03-71d471922820",
        },
        "endpoint": {
          "scope": {
             "type": "BearerToken",
             "token": "some-access-token"
          },
          "endpointId": "appliance-001",
          "cookie": {}
        },
        "payload": {
        }
      }
    }

```
响应例子
```

   

    {
      "context": {
      },
      "event": {
        "header": {
           "namespace": "DNA.SceneControl",
           "name": "ActivationStarted",
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
* 取消场景请求

请求例子
```   

    {
      "directive": {
        "header": {
           "namespace": "DNA.SceneControl",
           "name": "Deactivate",
           "interfaceVersion": "2",
           "messageId": "1bd5d003-31b9-476f-ad03-71d471922820",
        },
        "endpoint": {
          "scope": {
             "type": "BearerToken",
             "token": "some-access-token"
          },
          "endpointId": "appliance-001",
          "cookie": {}
        },
        "payload": {
        }
      }
    }


```
响应例子
```

   

    {
      "context": {
      },
      "event": {
        "header": {
           "namespace": "DNA.SceneControl",
           "name": "DeactivationStarted",
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

<span style="color:#ccc">3.20</span>运动控制

控制设备的动作，所有返回是统一的。

接口名称：DNA.MotionControl

* 开始请求


   
```
    {
      "directive": {
        "header": {
          "namespace": "DNA.MotionControl",
          "name": "Start",
          "messageId": "5f8a426e-01e4-4cc9-8b79-65f8bd0fd8a4",
          "payloadVersion": "2"
        },
        "endpoint": {
          "scope": {
            "type": "BearerToken",
            "token": "<OAuth2认证后得到的access_token>"
          },
          "endpointId": "<设备ID，发现时返回>",
		  "devicePairedInfo":devicePairedInfo,
          "cookie": {
          }
        },
        "payload": {
        }
      }
    }
```

* 暂停请求

   
```
    {
      "directive": {
        "header": {
          "namespace": "DNA.MotionControl",
          "name": "Pause",
          "messageId": "5f8a426e-01e4-4cc9-8b79-65f8bd0fd8a4",
          "payloadVersion": "2"
        },
        "endpoint": {
          "scope": {
            "type": "BearerToken",
            "token": "<OAuth2认证后得到的access_token>"
          },
          "endpointId": "<设备ID，发现时返回>",
		  "devicePairedInfo":devicePairedInfo,
          "cookie": {
          }
        },
        "payload": {
        }
      }
    }
```
* 停止请求
```
   

    {
      "directive": {
        "header": {
          "namespace": "DNA.MotionControl",
          "name": "Stop",
          "messageId": "5f8a426e-01e4-4cc9-8b79-65f8bd0fd8a4",
          "payloadVersion": "2"
        },
        "endpoint": {
          "scope": {
            "type": "BearerToken",
            "token": "<OAuth2认证后得到的access_token>"
          },
          "endpointId": "<设备ID，发现时返回>",
		  "devicePairedInfo":devicePairedInfo,
          "cookie": {
          }
        },
        "payload": {
        }
      }
    }
```
响应
```

   

    {
      "context": {
        "properties": [
        ]
      },
      "event": {
          "header": {
          "messageId": "30d2cd1a-ce4f-4542-aa5e-04bd0a6492d5",
          "name": "Response",
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
        }
      }
    }
```
<span style="color:#ccc">3.21</span>文本控制

通过文本字符串控制设备或者场景

接口名称: DNA.TextControl

请求例子
```   

    {
      "directive": {
        "header": {
           "namespace": "DNA.TextControl",
           "name": "Request",
           "interfaceVersion": "2",
           "messageId": "1bd5d003-31b9-476f-ad03-71d471922820",
        },
        "endpoint": {
          "scope": {
             "type": "BearerToken",
             "token": "some-access-token"
          },
          "cookie": {}
        },
        "payload": {
          "text":"",
          "additionals":{}
        }
      }
    }

```
响应例子
```

   

    {
      "context": {
      },
      "event": {
        "header": {
           "namespace": "DNA.TextControl",
           "name": "Response",
           "interfaceVersion": "2",
           "messageId": "5f8a426e-01e4-4cc9-8b79-65f8bd0fd8a4",
        },
        "endpoint": {
          "scope": {
            "type": "BearerToken",
            "token": "some-access-token"
          },
        },
        "payload": {
            "answerText":"",
            "endpoints":[
                {
                    "endpointId":"",
                    "actions": [{
                        "namespace":"",
                        "name":"",
                        "value":{}
                    }
                    ]
                }
            ]
        }
      }
    }
```

<span style="color:#ccc">3.22</span>自定义面板控制

控制RM自定义面板,需要运维设置是否返回自定义面板

接口名称: DNA.CustomizedRemoteControl

请求例子
```   

    {
      "directive": {
        "header": {
           "namespace": "DNA.CustomizedRemoteControl",
           "name": "打开",
           "interfaceVersion": "2",
           "messageId": "1bd5d003-31b9-476f-ad03-71d471922820",
        },
        "endpoint": {
          "scope": {
             "type": "BearerToken",
             "token": "some-access-token"
          },
		  "endpointId": "appliance-001",
		  "devicePairedInfo":devicePairedInfo,
          "cookie": {}
        },
        "payload": {
          "text":"",
          "additionals":{}
        }
      }
    }

```
响应例子
```

   

    {
      "context": {
        "properties": []
      },
      "event": {
          "header": {
          "messageId": "30d2cd1a-ce4f-4542-aa5e-04bd0a6492d5",
          "name": "Response",
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
        }
      }
    }
```

说明:

1.发现设备时能力中会返回自定义面板所支持的动作。

2.可以通过displayCategories中CUSTOMIZED来区分是否为自定义面板。

3.actions中的能力对应面板中保存的按键。

举例如下:
   
```
      {
                "endpointId":"3008880577263935437",
                "friendlyName":"自定义空调",
                "description":"BroadLink 智能遥控",
                "manufacturerName":"BroadLink",
                "icon":"https://ihcv0.ibroadlink.com/ec4appsysinfo/category2/CUSTOMIZED.png",
                "brand":"BroadLink",
                "roomName":"客厅",
                "displayCategories":[
                    "CUSTOMIZED"
                ],
                "cookie":{
                    "did":"xx",
                    "pid":"10039",
                    "sdid":"",
                    "spid":"",
                    "userid":"xx",
                    "devtype":0,
                    "devname":"自定义空调",
                    "moduleid":"3008880577263935437",
                    "moduletype":"20",
                    "familyid":"004734ce018aba779d8961378fa720bb",
                    "familyname":"我的家庭"
                },
                "isReachable":true,
                "capabilities":[
                    {
                        "type":"DNAInterface",
                        "interface":"DNA.CustomizedRemoteControl",
                        "version":"2",
                        "properties":{
                            "supported":null,
                            "proactivelyReported":false,
                            "retrievable":false
                        },
                        "actions":{
                            "supported":[
                                {
                                    "name":"打开"
                                },
                                {
                                    "name":"关闭"
                                }
                            ]
                        }
                    }
                ],
                "additional":null
      }

```
