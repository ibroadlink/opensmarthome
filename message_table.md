智能家居接口V2.0-控制接口参考表
===============================

更新时间
--------

2017/7/24 增加状态查询和变化通知消息,增加按步长调节频道

2017/8/3 增加设备发现响应说明
:   调整返回属性格式

2017/8/4 补充上一首消息

2017/8/18 增加风速和固定目标温度接口

2017/8/26 补充设备发现，模式，风速说明。

2017/8/26 增加动作控制。

2017/10/27 增加文本控制并增加设备发现标签。

2018/03/02 增加增加色温控制和自定义面板控制。

详细接口参考表
--------------

各消息的详细属性参数请参考
[智能家居接口属性参考表](attribute_table.html#section)

### 设备发现

接口名称: DNA.Discovery

-   发现请求

其中options字段，可以用来指示设备发现时对设备列表等做特别处理。enableIntent只有要使用DNA.TextControl接口时才需要设置为true。

additionals字段可以填入更多内容，对设备列表的返回进行过滤和限制，具体参考其他文档（由于这部分业务暂未上线，该字段填空即可）。

-   发现响应

isReachable 表示设备是否在线，在线为true，不在线为false。

capabilities字段中描述了对应设备的具体能力，包括版本，支持的属性，
是否支持主动上报，是否支持状态查询。其中interface字段是和接口名称一一对应的。

即使两个产品的品类（displayCategories）相同，具备的能力也可能不同，所以需要根据设备发现返回的

capabilities字段描述的功能动态判断,目前会返回properties和actions两个字段，推荐使用actions.

cookie字段是与一个endpoint运行时关联的字段，里面保存控制时的一些上下文信息，
服务器只要保存下来就可以了，不需要对字段里面的数据进行解析。

cookie里面的数量是不定的，可能没有，也可能有多个。

  name                  值
  --------------------- -----------------------
  proactivelyReported   true： 支持主动上报
                        false: 不支持主动上报
  retrievable           true: 支持状态查询
                        false: 不支持状态查询

设备发现返回的displayCategories可以参考
[品类参考表](category_table.html#section)。

### 电源控制

控制设备的电源开关

接口名称: DNA.PowerControl

-   ChangePowerState请求

请求例子

响应例子

### 频道控制

控制电视/机顶盒频道

接口名称: DNA.ChannelControl

-   ChangeChannel请求

请求例子

响应例子

-   AdjustChannel请求

按步长调整频道

请求:

响应：

### 音量控制

控制设备的音量

接口名称: DNA.VolumeControl

-   步长调节请求

响应

-   直接控制请求

响应

-   静音控制请求

响应

### 播放控制

控制设备的播放/暂停等,由于播放控制不涉及状态，所有返回是统一的。

接口名称：DNA.PlaybackControl

-   播放请求

-   暂停请求

-   继续请求

-   下一首请求

-   上一首请求

-   快进请求

-   回放请求

-   响应

### 风速控制

> 控制风扇的速度
>
> 接口名称：DNA.WindSpeedControl

-   设置风速请求

响应:

具体支持的风俗列表，请参考[智能家居接口属性参考表](attribute_table.html#section)

-   步长调整风速请求

响应:

### 风向控制

控制设备的风向，控制不涉及状态，所有返回是统一的。

接口名称：DNA.AirFlowControl

-   开启摆风请求

-   停止摆风请求

-   水平摆风请求

-   垂直摆风请求

响应：

### 颜色控制

控制设备的颜色

接口名称：DNA.ColorControl

-   请求

-   响应
    :   

### 颜色名称控制

控制设备的颜色

接口名称：DNA.ColorNameControl

-   请求

-   响应
    :   

### 色温控制

> 控制设备的色温
>
> 接口名称：DNA.ColorTempControl

-   设置色温请求

-   设置色温响应

### 亮度控制

> 控制设备的亮度
>
> 接口名称：DNA.BrightnessControl

-   设置亮度请求

-   设置亮度响应

-   按步长设置亮度请求

    > 正数表示增加，负数表示减少.

-   按步长设置亮度响应

### 百分比控制

> 控制设备属性的百分比
>
> 接口名称：DNA.PercentageControl
>
> 请求：

### 温控器控制

> 控制可以调节温度的设备
>
> 接口名称：DNA.ThermostatControl
>
> -   目标温度控制
>
> 请求：

-   步长温度控制

    > 请求：

> -   固定目标温度控制
>     :   单位恒定为摄氏度。
>
>         请求：
>
-   固定步长温度控制

    > 请求：

-   模式控制

    > 请求：

具体支持的模式列表，请参考[智能家居接口属性参考表](attribute_table.html#section)

### 温度感知

> 查询温度 接口名称：DNA.TemperatureSensor
>
> 请求

### 湿度感知

> 查询湿度 接口名称：DNA.HumiditySensor
>
> 请求

### PM2.5感知

> 查询PM2.5 接口名称：DNA.PM2\_5Sensor
>
> 请求

### 状态查询

> 请求
>
> 响应:

状态查询响应时，每个属性都会携带如下字段：

  --------------- ----------
  scale           单位
  attributeName   属性名称
  scaleName       单位名称
  valueName       值名称
  --------------- ----------

如果是查询一个endpoint的全部状态, namespace需要填DNA.

如果是查询单个属性，则填如对应属性的接口名称。

### 变化通知

变化通知有三种通知：

1.  设备属性变化，比如温度，开关状态
2.  设备附件状态变化，比如用户的设备名称变化，设备在线情况变化，用户新增加/删除设备

当一个设备多个属性变化时，放到payload中，一起上报.如果发现是设备列表发生变化，那么需要重新调用
设备发现。

> 上报格式:

  reportType                                                    说明 备注                                          
  ------------------------------------------------------------- -------------------------------------------------- ------------------------------------------------
  STATE\_CHANGE                                                 设备状态变化                                       
  ENDPOINT\_CHANGE                                              设备列表变化                                       
  ====================                                          =================                                  =======
  cause字段用来描述设备状态变化的原因，如果是设备列表变化，可   以忽略这个字段。                                   
  错误响应                                                                                                         
  \^\^\^\^\^\^\^\^\^                                                                                               
  查询湿度                                                                                                         
  接口名称：DNA.ErrorResponse                                                                                      
  响应                                                                                                             
  .. sourcecode:: javascript                                                                                       
  {                                                                                                                
  "context": {},                                                                                                   
  "event": {                                                                                                       
  "header": {                                                                                                      
  "namespace": "DNA",                                                                                              
  "messageId": "30d2c                                           d1a-ce4f-4542-aa5e-04bd0a6492                      d5",
  "name": "ErrorRespo                                           nse",                                              
  "payloadVersion": "                                           2"                                                 
  },                                                                                                               
  "endpoint": {                                                                                                    
  "scope": {                                                                                                       
  "type": "BearerTo                                             ken",                                              
  "token": "some-ac                                             cess-token"                                        
  },                                                                                                               
  "endpointId": "appl                                           iance-001"                                         
  },                                                                                                               
  "payload": {                                                                                                     
  "type": "ENDPOION                                             T\_UNREACHABLE",                                   
  "message":"设备离线"                                                                                             
  }                                                                                                                
  }                                                                                                                
  }                                                                                                                
  .. sourcecode:: javascript                                                                                       
  {                                                                                                                
  "context": {},                                                                                                   
  "event": {                                                                                                       
  "header": {                                                                                                      
  "namespace": "DNA",                                                                                              
  "messageId": "30d2c                                           d1a-ce4f-4542-aa5e-04bd0a6492                      d5",
  "name": "ErrorRespo                                           nse",                                              
  "payloadVersion": "                                           2"                                                 
  },                                                                                                               
  "endpoint": {                                                                                                    
  "scope": {                                                                                                       
  "type": "BearerTo                                             ken",                                              
  "token": "some-ac                                             cess-token"                                        
  },                                                                                                               
  "endpointId": "appl                                           iance-001"                                         
  },                                                                                                               
  "payload": {                                                                                                     
  "type": "VALUE\_OU                                            T\_OF\_RANGE",                                     
  "message":"值越界",                                                                                              
  "validRange": {                                                                                                  
  "minimumValue                                                 ":10,                                              
  "maximumValue                                                 ":200                                              
  }                                                                                                                
  }                                                                                                                
  }                                                                                                                
  场景控制                                                                                                         
  \^\^\^\^\^\^\^\^\^                                                                                               
  控制场景                                                                                                         
  接口名称: DNA.SceneControl                                                                                       
  \* 执行场景请求                                                                                                  
  请求例子                                                                                                         
  .. sourcecode:: javascript                                                                                       
  {                                                                                                                
  "directive": {                                                                                                   
  "header": {                                                                                                      
  "namespace": "DNA.Scen                                        eControl",                                         
  "name": "Activate",                                                                                              
  "interfaceVersion": "2                                        ",                                                 
  "messageId": "1bd5d003                                        -31b9-476f-ad03-71d471922820"                      ,
  },                                                                                                               
  "endpoint": {                                                                                                    
  "scope": {                                                                                                       
  "type": "BearerToken                                          ",                                                 
  "token": "some-acces                                          s-token"                                           
  },                                                                                                               
  "endpointId": "applianc                                       e-001",                                            
  "cookie": {}                                                                                                     
  },                                                                                                               
  "payload": {                                                                                                     
  }                                                                                                                
  }                                                                                                                
  }                                                                                                                
  响应例子                                                                                                         
  .. sourcecode:: javascript                                                                                       
  {                                                                                                                
  "context": {                                                                                                     
  },                                                                                                               
  "event": {                                                                                                       
  "header": {                                                                                                      
  "namespace": "DNA.Scen                                        eControl",                                         
  "name": "ActivationSta                                        rted",                                             
  "interfaceVersion": "2                                        ",                                                 
  "messageId": "5f8a426e                                        -01e4-4cc9-8b79-65f8bd0fd8a4"                      ,
  },                                                                                                               
  "endpoint": {                                                                                                    
  "scope": {                                                                                                       
  "type": "BearerToken"                                         ,                                                  
  "token": "some-access                                         -token"                                            
  },                                                                                                               
  "endpointId": "applianc                                       e-001"                                             
  },                                                                                                               
  "payload": {                                                                                                     
  }                                                                                                                
  }                                                                                                                
  }                                                                                                                
  \* 取消场景请求                                                                                                  
  请求例子                                                                                                         
  .. sourcecode:: javascript                                                                                       
  {                                                                                                                
  "directive": {                                                                                                   
  "header": {                                                                                                      
  "namespace": "DNA.Scen                                        eControl",                                         
  "name": "Deactivate",                                                                                            
  "interfaceVersion": "2                                        ",                                                 
  "messageId": "1bd5d003                                        -31b9-476f-ad03-71d471922820"                      ,
  },                                                                                                               
  "endpoint": {                                                                                                    
  "scope": {                                                                                                       
  "type": "BearerToken                                          ",                                                 
  "token": "some-acces                                          s-token"                                           
  },                                                                                                               
  "endpointId": "applianc                                       e-001",                                            
  "cookie": {}                                                                                                     
  },                                                                                                               
  "payload": {                                                                                                     
  }                                                                                                                
  }                                                                                                                
  }                                                                                                                
                                                                                                                   
  响应例子                                                                                                         
  .. sourcecode:: javascript                                                                                       
  {                                                                                                                
  "context": {                                                                                                     
  },                                                                                                               
  "event": {                                                                                                       
  "header": {                                                                                                      
  "namespace": "DNA.Scen                                        eControl",                                         
  "name": "DeactivationS                                        tarted",                                           
  "interfaceVersion": "2                                        ",                                                 
  "messageId": "5f8a426e                                        -01e4-4cc9-8b79-65f8bd0fd8a4"                      ,
  },                                                                                                               
  "endpoint": {                                                                                                    
  "scope": {                                                                                                       
  "type": "BearerToken"                                         ,                                                  
  "token": "some-access                                         -token"                                            
  },                                                                                                               
  "endpointId": "applianc                                       e-001"                                             
  },                                                                                                               
  "payload": {                                                                                                     
  }                                                                                                                
  }                                                                                                                
  }                                                                                                                
                                                                                                                   
  运动控制                                                                                                         
  \^\^\^\^\^\^\^\^\^                                                                                               
  控制设备的动作，所有返回是统一的。                                                                               
  接口名称：DNA.MotionControl                                                                                      
  \* 开始请求                                                                                                      
                                                                                                                   
  .. sourcecode:: javascript                                                                                       
  {                                                                                                                
  "directive": {                                                                                                   
  "header": {                                                                                                      
  "namespace": "DNA.Motio                                       nControl",                                         
  "name": "Start",                                                                                                 
  "messageId": "5f8a426e-                                       01e4-4cc9-8b79-65f8bd0fd8a4",                      
  "payloadVersion": "2"                                                                                            
  },                                                                                                               
  "endpoint": {                                                                                                    
  "scope": {                                                                                                       
  "type": "BearerToken"                                         ,                                                  
  "token": "\<OAuth2认证后得                                    到的access\_token\>"                               
  },                                                                                                               
  "endpointId": "\<设备ID，发现                                 时返回\>",                                         
  "cookie": {                                                                                                      
  }                                                                                                                
  },                                                                                                               
  "payload": {                                                                                                     
  }                                                                                                                
  }                                                                                                                
  }                                                                                                                
                                                                                                                   
  \* 暂停请求                                                                                                      
  .. sourcecode:: javascript                                                                                       
  {                                                                                                                
  "directive": {                                                                                                   
  "header": {                                                                                                      
  "namespace": "DNA.Motio                                       nControl",                                         
  "name": "Pause",                                                                                                 
  "messageId": "5f8a426e-                                       01e4-4cc9-8b79-65f8bd0fd8a4",                      
  "payloadVersion": "2"                                                                                            
  },                                                                                                               
  "endpoint": {                                                                                                    
  "scope": {                                                                                                       
  "type": "BearerToken"                                         ,                                                  
  "token": "\<OAuth2认证后得                                    到的access\_token\>"                               
  },                                                                                                               
  "endpointId": "\<设备ID，发现                                 时返回\>",                                         
  "cookie": {                                                                                                      
  }                                                                                                                
  },                                                                                                               
  "payload": {                                                                                                     
  }                                                                                                                
  }                                                                                                                
  }                                                                                                                
  \* 停止请求                                                                                                      
  .. sourcecode:: javascript                                                                                       
  {                                                                                                                
  "directive": {                                                                                                   
  "header": {                                                                                                      
  "namespace": "DNA.Motio                                       nControl",                                         
  "name": "Stop",                                                                                                  
  "messageId": "5f8a426e-                                       01e4-4cc9-8b79-65f8bd0fd8a4",                      
  "payloadVersion": "2"                                                                                            
  },                                                                                                               
  "endpoint": {                                                                                                    
  "scope": {                                                                                                       
  "type": "BearerToken"                                         ,                                                  
  "token": "\<OAuth2认证后得                                    到的access\_token\>"                               
  },                                                                                                               
  "endpointId": "\<设备ID，发现                                 时返回\>",                                         
  "cookie": {                                                                                                      
  }                                                                                                                
  },                                                                                                               
  "payload": {                                                                                                     
  }                                                                                                                
  }                                                                                                                
  }                                                                                                                
  \* 响应                                                                                                          
  .. sourcecode:: javascript                                                                                       
  {                                                                                                                
  "context": {                                                                                                     
  "properties": [                                                                                                  
  ]                                                                                                                
  },                                                                                                               
  "event": {                                                                                                       
  "header": {                                                                                                      
  "messageId": "30d2cd1a-                                       ce4f-4542-aa5e-04bd0a6492d5",                      
  "name": "Response",                                                                                              
  "payloadVersion": "2"                                                                                            
  },                                                                                                               
  "endpoint": {                                                                                                    
  "scope": {                                                                                                       
  "type": "BearerToken"                                         ,                                                  
  "token": "some-access                                         -token"                                            
  },                                                                                                               
  "endpointId": "applianc                                       e-001"                                             
  },                                                                                                               
  "payload": {                                                                                                     
  }                                                                                                                
  }                                                                                                                
  }                                                                                                                
  文本控制                                                                                                         
  \^\^\^\^\^\^\^\^\^                                                                                               
  通过文本字符串控制设备或者场景                                                                                   
  接口名称: DNA.TextControl                                                                                        
  请求例子                                                                                                         
  .. sourcecode:: javascript                                                                                       
  {                                                                                                                
  "directive": {                                                                                                   
  "header": {                                                                                                      
  "namespace": "DNA.Text                                        Control",                                          
  "name": "Request",                                                                                               
  "interfaceVersion": "2                                        ",                                                 
  "messageId": "1bd5d003                                        -31b9-476f-ad03-71d471922820"                      ,
  },                                                                                                               
  "endpoint": {                                                                                                    
  "scope": {                                                                                                       
  "type": "BearerToken                                          ",                                                 
  "token": "some-acces                                          s-token"                                           
  },                                                                                                               
  "cookie": {}                                                                                                     
  },                                                                                                               
  "payload": {                                                                                                     
  "text":"",                                                                                                       
  "additionals":{}                                                                                                 
  }                                                                                                                
  }                                                                                                                
  }                                                                                                                
  响应例子                                                                                                         
  .. sourcecode:: javascript                                                                                       
  {                                                                                                                
  "context": {                                                                                                     
  },                                                                                                               
  "event": {                                                                                                       
  "header": {                                                                                                      
  "namespace": "DNA.Text                                        Control",                                          
  "name": "Response",                                                                                              
  "interfaceVersion": "2                                        ",                                                 
  "messageId": "5f8a426e                                        -01e4-4cc9-8b79-65f8bd0fd8a4"                      ,
  },                                                                                                               
  "endpoint": {                                                                                                    
  "scope": {                                                                                                       
  "type": "BearerToken"                                         ,                                                  
  "token": "some-access                                         -token"                                            
  },                                                                                                               
  },                                                                                                               
  "payload": {                                                                                                     
  "answerText":"",                                                                                                 
  "endpoints":[                                                                                                    
  {                                                                                                                
  "endpointId":                                                 "",                                                
  "actions": [{                                                                                                    
  "namespac                                                     e":"",                                             
  "name":""                                                     ,                                                  
  "value":{                                                     }                                                  
  }                                                                                                                
  ]                                                                                                                
  }                                                                                                                
  ]                                                                                                                
  }                                                                                                                
  }                                                                                                                
  }                                                                                                                
                                                                                                                   
  自定义面板控制                                                                                                   
  \^\^\^\^\^\^\^\^\^                                                                                               
  控制RM自定义面板,需要运维设置是否返回自定义面板                                                                  
  接口名称: DNA.CustomizedRemoteContro                          l                                                  
  请求例子                                                                                                         
  .. sourcecode:: javascript                                                                                       
  {                                                                                                                
  "directive": {                                                                                                   
  "header": {                                                                                                      
  "namespace": "DNA.Cust                                        omizedRemoteControl",                              
  "name": "打开",                                                                                                  
  "interfaceVersion": "2                                        ",                                                 
  "messageId": "1bd5d003                                        -31b9-476f-ad03-71d471922820"                      ,
  },                                                                                                               
  "endpoint": {                                                                                                    
  "scope": {                                                                                                       
  "type": "BearerToken                                          ",                                                 
  "token": "some-acces                                          s-token"                                           
  },                                                                                                               
  "cookie": {}                                                                                                     
  },                                                                                                               
  "payload": {                                                                                                     
  "text":"",                                                                                                       
  "additionals":{}                                                                                                 
  }                                                                                                                
  }                                                                                                                
  }                                                                                                                
  响应例子                                                                                                         
  .. sourcecode:: javascript                                                                                       
  {                                                                                                                
  "context": {                                                                                                     
  "properties": []                                                                                                 
  },                                                                                                               
  "event": {                                                                                                       
  "header": {                                                                                                      
  "messageId": "30d2cd1a-                                       ce4f-4542-aa5e-04bd0a6492d5",                      
  "name": "Response",                                                                                              
  "payloadVersion": "2"                                                                                            
  },                                                                                                               
  "endpoint": {                                                                                                    
  "scope": {                                                                                                       
  "type": "BearerToken"                                         ,                                                  
  "token": "some-access                                         -token"                                            
  },                                                                                                               
  "endpointId": "applianc                                       e-001"                                             
  },                                                                                                               
  "payload": {                                                                                                     
  }                                                                                                                
  }                                                                                                                
  }                                                                                                                
                                                                                                                   
  说明:                                                                                                            
  1.发现设备时能力中会返回自定义面板所支持的动作。                                                                 
  2.可以通过displayCategories中CUSTOMIZ                         ED来区分是否为自定义面板。                         
  3.actions中的能力对应面板中保存的按键。                                                                          
  举例如下:                                                                                                        
  .. sourcecode:: javascript                                                                                       
  {                                                                                                                
  "endpointId":"300                                             8880577263935437",                                 
  "friendlyName":"自                                            定义空调",                                         
  "description":"Br                                             oadLink 智能遥控",                                 
  "manufacturerName                                             ":"BroadLink",                                     
  "icon":"<https://i>                                           hcv0.ibroadlink.com/ec4appsys                      info/category2/CUSTOMIZED.png",
  "brand":"BroadLin                                             k",                                                
  "roomName":"客厅",                                                                                               
  "displayCategorie                                             s":[                                               
  "CUSTOMIZED"                                                                                                     
  ],                                                                                                               
  "cookie":{                                                                                                       
  "did":"xx",                                                                                                      
  "pid":"10039"                                                 ,                                                  
  "sdid":"",                                                                                                       
  "spid":"",                                                                                                       
  "userid":"xx"                                                 ,                                                  
  "devtype":0,                                                                                                     
  "devname":"自定                                               义空调",                                           
  "moduleid":"3                                                 008880577263935437",                               
  "moduletype":                                                 "20",                                              
  "familyid":"0                                                 04734ce018aba779d8961378fa720                      bb",
  "familyname":                                                 "我的家庭"                                         
  },                                                                                                               
  "isReachable":tru                                             e,                                                 
  "capabilities":[                                                                                                 
  {                                                                                                                
  "type":"D                                                     NAInterface",                                      
  "interfac                                                     e":"DNA.CustomizedRemoteContr                      ol",
  "version"                                                     :"2",                                              
  "properti                                                     es":{                                              
  "supp                                                         orted":null,                                       
  "proa                                                         ctivelyReported":false,                            
  "retr                                                         ievable":false                                     
  },                                                                                                               
  "actions"                                                     :{                                                 
  "supp                                                         orted":[                                           
  {                                                                                                                
                                                                "name":"打开"                                      
  }                                                             ,                                                  
  {                                                                                                                
                                                                "name":"关闭"                                      
  }                                                                                                                
  ]                                                                                                                
  }                                                                                                                
  }                                                                                                                
  ],                                                                                                               
  "additional":null                                                                                                
  }                                                                                                                
                                                                                                                   
  帐号主动授权                                                                                                     
  \^\^\^\^\^\^\^\^\^\^\^\^\^                                                                                       
  第三方主动授权。                                                                                                 
  接口名称：DNA.Authorization                                                                                      
  \* 授权请求                                                                                                      
  .. sourcecode:: javascript                                                                                       
  {                                                                                                                
  "directive": {                                                                                                   
  "header": {                                                                                                      
  "namespace": "DNA.Autho                                       rization",                                         
  "name": "AcceptGrant",                                                                                           
  "messageId": "5f8a426e-                                       01e4-4cc9-8b79-65f8bd0fd8a4",                      
  "payloadVersion": "2"                                                                                            
  },                                                                                                               
  "payload": {                                                                                                     
  "grant": {                                                                                                       
  "type": "OAuth2.A                                             uthorizationCode",                                 
  "code": "some-oau                                             th-code"                                           
  },                                                                                                               
  "grantee": {                                                                                                     
  "type": "BearerTo                                             ken",                                              
  "token":"some-oau                                             th-token"                                          
  },                                                                                                               
  }                                                                                                                
  }                                                                                                                
  }                                                                                                                
  \* 响应                                                                                                          
  .. sourcecode:: javascript                                                                                       
  {                                                                                                                
  "event": {                                                                                                       
  "header": {                                                                                                      
  "messageId": "30d2cd1a-                                       ce4f-4542-aa5e-04bd0a6492d5",                      
  "namespace": "DNA.Autho                                       rization",                                         
  "name":"AcceptGrant.Res                                       ponse",                                            
  "payloadVersion": "2"                                                                                            
  },                                                                                                               
  "payload": {                                                                                                     
  "grantee": {                                                                                                     
  "type": "BearerTo                                             ken",                                              
  "token":"some-oau                                             th-token",                                         
  "refreshToken":"s                                             ome-oauth-token"                                   
  }                                                                                                                
  }                                                                                                                
  }                                                                                                                
  }                                                                                                                
  接收到主动授权消息后，BroadLink云端会调用OAuth2.              0协议调用第三方提供的OAuth2.0 token获取与刷        新接口以及获取用户信息接口，完成OAuth2.0流程。
  如果之前没有进行过授权，那么grantee中的token为空。这          一步授权完成后，通过设备发现消息，可以查询         
  到授权消息中携带的设备。                                                                                         
  设备授权                                                                                                         
  \^\^\^\^\^\^\^\^\^\^\^\^\^                                                                                       
  第三方设备授权。                                                                                                 
  接口名称：DNA.Authorization                                                                                      
  \* 授权请求                                                                                                      
  .. sourcecode:: javascript                                                                                       
  {                                                                                                                
  "directive": {                                                                                                   
  "header": {                                                                                                      
  "namespace": "DNA.Autho                                       rization",                                         
  "name": "DeviceGrant",                                                                                           
  "messageId": "5f8a426e-                                       01e4-4cc9-8b79-65f8bd0fd8a4",                      
  "payloadVersion": "2"                                                                                            
  },                                                                                                               
  "payload": {                                                                                                     
  "endpoints": [{                                                                                                  
  "endpointId": "so                                             me-info-from-sdk",                                 
  "cookie": {}                                                                                                     
  }],                                                                                                              
  "scope": {                                                                                                       
  "type": "BearerTo                                             ken",                                              
  "token":"some-oau                                             th-token"                                          
  },                                                                                                               
  }                                                                                                                
  }                                                                                                                
  }                                                                                                                
  \* 响应                                                                                                          
  .. sourcecode:: javascript                                                                                       
  {                                                                                                                
  "event": {                                                                                                       
  "header": {                                                                                                      
  "messageId": "30d2cd1a-                                       ce4f-4542-aa5e-04bd0a6492d5",                      
  "namespace": "DNA.Autho                                       rization",                                         
  "name":"DeviceGrant.Res                                       ponse",                                            
  "payloadVersion": "2"                                                                                            
  },                                                                                                               
  "payload": {                                                                                                     
  }                                                                                                                
  }                                                                                                                
  }                                                                                                                
  产品详情查询                                                                                                     
  \^\^\^\^\^\^\^\^\^\^\^\^\^                                                                                       
  设备产品详情查询。                                                                                               
  接口名称：DNA.ProductInfo                                                                                        
  \* 产品详情查询                                                                                                  
  .. sourcecode:: javascript                                                                                       
  {                                                                                                                
  "directive": {                                                                                                   
  "header": {                                                                                                      
  "namespace": "DNA.Produ                                       ctInfo",                                           
  "name": "ProductQuery",                                                                                          
  "messageId": "5f8a426e-                                       01e4-4cc9-8b79-65f8bd0fd8a4",                      
  "payloadVersion": "2"                                                                                            
  },                                                                                                               
  "endpoints": [{                                                                                                  
  "endpointId":"",                                                                                                 
  "cookie":{}                                                                                                      
  }],                                                                                                              
  "payload": {                                                                                                     
  "scope":{                                                                                                        
  }                                                                                                                
  }                                                                                                                
  }                                                                                                                
  }                                                                                                                
  endpointInfo 从本地局域网获取，第三方无需解析.                                                                   
  \* 响应                                                                                                          
  .. sourcecode:: javascript                                                                                       
  {                                                                                                                
  "event": {                                                                                                       
  "header": {                                                                                                      
  "messageId": "30d2cd1a-                                       ce4f-4542-aa5e-04bd0a6492d5",                      
  "namespace": "DNA.Produ                                       ctInfo",                                           
  "name":"ProductQuery.Re                                       sponse",                                           
  "payloadVersion": "2"                                                                                            
  },                                                                                                               
  "endpoints":[                                                                                                    
  {                                                                                                                
  "endpointId": "ap                                             pliance-001",                                      
  "friendlyName": "                                             卧室灯",                                           
  "isReachable":tru                                             e,                                                 
  "description": "由                                            BroadLink生产的灯",                                
  "manufacturerName                                             ": "Sample Manufacturer",                          
  "icon":"产品图片URL",                                                                                            
  "brand":"品牌",                                                                                                  
  "displayCategorie                                             s": [                                              
  "LIGHT"                                                                                                          
  ],                                                                                                               
  "familyName": "用户                                           设置的家庭名称",                                   
  "roomName": "用户设置                                         的房间名称",                                       
  "cookie": {                                                                                                      
  "extraDetail1                                                 ": "某些设备可能会用到这个cookie，需要在控制时原   样返回",
  "extraDetail2                                                 ": "某些设备可能会用到这个cookie，需要在控制时原   样返回",
  "extraDetail3                                                 ": "某些设备可能会用到这个cookie，需要在控制时原   样返回",
  "extraDetail4                                                 ": "某些设备可能会用到这个cookie，需要在控制时原   样返回"
  },                                                                                                               
  "capabilities": [                                                                                                
  {                                                                                                                
  "type": "                                                     DNAInterface",                                     
  "interfac                                                     e": "DNA.PowerControl",                            
  "version"                                                     : "2",                                             
  "properti                                                     es": {                                             
  "supp                                                         orted": [                                          
  {                                                                                                                
                                                                "name": "powerState"                               
  }                                                                                                                
  ],                                                                                                               
  "proa                                                         ctivelyReported": true,                            
  "retr                                                         ievable": true                                     
  },                                                                                                               
  "actions":                                                    {                                                  
  "suppo                                                        rted": [                                           
  {                                                                                                                
                                                                "name": "ChangePowerState"                         
  }                                                                                                                
  ]                                                                                                                
  }                                                                                                                
  }                                                                                                                
  ]                                                                                                                
  }                                                                                                                
  ],                                                                                                               
  "payload": {                                                                                                     
  }                                                                                                                
  }                                                                                                                
  }                                                                                                                
  其他参考表                                                                                                       

[智能家居接口属性参考表](attribute_table.html#section)

[接口错误消息参考表](error_table.html#section)

[品类参考表](category_table.html#section)

[智能接口参考表](smarthome_api.html#section)
