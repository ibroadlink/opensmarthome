# RM产品简介
RM产品的基本功能是将接收到的红外码/遥控码通过红外发送出去，其本身因为存储空间的限制不具备保存红外码功能。所以，目前的RM产品都是将红外码保存在APP或者云端。

# RM使用和控制机制
用户通过APP首先查询RM支持的品类，比如空调，电视，机顶盒，灯，风扇等，然后选择品类下的
品牌列表，比如格力，Aux，TCL，这时候APP会获取到一个红外码型号列表，用户通过UI界面和自己
要控制的设备进行匹配，一旦测试验证通过，APP就将对应的红外码保存下来。控制时，将红外码发送给RM即可。

BroadLink经过多年的积累，已经构建了目前全球最大的各品类的红外码库，涵盖全球所有知名品牌。
同时每个品类的功能都已经标准化，方便UI的交互设计。

# 对接流程介绍
1. 获取品类列表
    
    通过云端接口获取当前支持的品类列表，也可以固化部分品类，比如空调，电视

2. 获取品类下的品牌列表
    
    通过云端接口获取品类下的当前支持的品牌列表

3. 获取品牌下的型号列表
    
    获取品牌下的红码列表，该列表是有优先级的，排在前面的适配的产品更多

4. 获取红外码编号，和对应的面板类型

5. 通过SDK发送红外码
    
    将红码按要求的格式通过SDK发送给RM后，用户可以观察自己的设备是否有响应，进而判断匹配是否成功， 若成功，则返回生成的面板信息。

6. 云端注册与控制
    
    通过调用云端的XX接口

# SDK具体接口参考
1. 发送红外码接口

```
public String deviceControl(String action, String params)

action: RM_Panel_Test
params:
            {
                    "devicePairedInfo": devicePairedInfo    // 配置成功上的设备信息
                    "data" : {                      //  云端返回信息
                        "pid":"",                   // 设备类型
                        "ircodeid":"",              // 红外码ID
                        "ircode": {
                            "function":"on",                                    //本条红外码功能
                            "name":"空调打开"，　　　　　　　　　　　　　　　　　　　　　//功能名称
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

# 云端具体接口参考
1. 获取品类列表

```
URL: https://xxxbizopenplatform.ibroadlink.com/ircode/info

header: 
body:
    {
        "directive": {
            "header": {
                "namespace": "DNA.IrcodeInfo",
                "name": "getdevtype",
                "messageId": "1bd5d003-31b9-476f-ad03-71d471922820",
                "interfaceVersion": "2"
            },
            "endpoint": {
                "scope": {
                    "type": "",
                    "token": "some-access-token"
                },
                "endpointId": "appliance-001",//暂时不需要
                "devicePairedInfo": devicePairedInfo,
                "cookie": {}
            }，
            "payload": {
            }
        }
    }
                    
return:
   {
      "context": {
      },
      "event": {
        "header": {
           "namespace": "DNA.IrcodeInfo",
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
            "devtype": [{"devtypeid":int,"devtypename":string}]
        }
      }
    }
```

2. 获取品牌列表

```
URL: https://xxxbizopenplatform.ibroadlink.com/ircode/info

header: 
body:
    {
        "directive": {
            "header": {
                "namespace": "DNA.IrcodeInfo",
                "name": "getbrand",
                "messageId": "1bd5d003-31b9-476f-ad03-71d471922820",
                "interfaceVersion": "2"
            },
            "endpoint": {
                "scope": {
                    "type": "",
                    "token": "some-access-token"
                },
                "endpointId": "appliance-001",//暂时不需要
                "devicePairedInfo": devicePairedInfo,
                "cookie": {}
            },
            "payload": {
                "devtypeid":0
            }
        }
    }
                    
return:
   {
      "context": {
      },
      "event": {
        "header": {
           "namespace": "DNA.IrcodeInfo",
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
            "brand": [{"brandid":int,"brand":string,"enbrand":string,"famousstatus":int}]
        }
      }
    }
```

3. 获取型号列表（目前只有云电机有型号）

```
URL: https://xxxbizopenplatform.ibroadlink.com/ircode/info

header: 
body:
    {
        "directive": {
            "header": {
                "namespace": "DNA.IrcodeInfo",
                "name": "getversion",
                "messageId": "1bd5d003-31b9-476f-ad03-71d471922820",
                "interfaceVersion": "2"
            },
            "endpoint": {
                "scope": {
                    "type": "",
                    "token": "some-access-token"
                },
                "endpointId": "appliance-001",//暂时不需要
                "devicePairedInfo": devicePairedInfo,
                "cookie": {}
            },
            "payload": {
                "devtypeid":0，
                "brandid":1
            }
        }
    }
                    
return:
   {
      "context": {
      },
      "event": {
        "header": {
           "namespace": "DNA.IrcodeInfo",
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
            "version": [{"versionid":0,"version":"","devtypeid":0,brandid:0}]
        }
      }
    }
```


4. 获取红码列表

```
URL: https://xxxbizopenplatform.ibroadlink.com/ircode/info

header: 
body:
    {
        "directive": {
            "header": {
                "namespace": "DNA.IrcodeInfo",
                "name": "getircode",
                "messageId": "1bd5d003-31b9-476f-ad03-71d471922820",
                "interfaceVersion": "2"
            },
            "endpoint": {
                "scope": {
                    "type": "",
                    "token": "some-access-token"
                },
                "endpointId": "appliance-001",//暂时不需要
                "devicePairedInfo": devicePairedInfo,
                "cookie": {}
            },
            "payload": {
                "devtypeid":0，
                "brandid":1,
                "versionid":0//(可选)
            }
        }
    }
                    
return:
   {
      "context": {
      },
      "event": {
        "header": {
           "namespace": "DNA.IrcodeInfo",
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
            "ircode":[ 
                "pid":"",                   // 设备类型
                "ircodeid":"",              // 红外码ID
                "ircode": {
                    "function":"on",                                    //本条红外码功能
                    "name":"空调打开"　　　　　　　　　　　　　　　　　　　　　　//功能名称
                    "desc":"空调打开，模式制热,23摄氏度，自动风",            //本条红外码描述信息
                    "code":"2600121343241325243521342342141"            //红外码值
                }
                ]
        }
      }
    }
```

# 品类以及对应功能参考表
0. JSON格式
1. 空调
2. 电视
3. 机顶盒
4. 风扇
5. 灯

具体参看：  Go to [品类参考表](category_table.md).
