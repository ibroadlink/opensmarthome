智能家居接口V2.0-品类参考表
===========================

2017/10/27 增加浇花器品类。

品类参考表
----------

  品类         关键字 备注         
  ------------ ------------------- --
  灯           LIGHT               
  电视         TV                  
  插座         SMARTPLUG           
  开关         SWITCH              
  空调         AC                  
  机顶盒       STB                 
  传感器       SENSOR              
  窗帘         CURTAIN             
  热水器       WATER\_HEATER       
  风扇         FAN                 
  电水壶       KETTLE              
  路由器       ROUTER              
  饭煲         COOKER              
  加湿器       HUMIDIFIER          
  饮水机       WATER\_COOLER       
  鱼缸         AQUARIUM            
  摄像头       CAMERA              
  空气净化器   AIRPURIFIER         
  台灯         LIGHT               
  落地灯       LIGHT               
  加热器       HEATER              
  加热毯       ELECTRIC\_BLANKET   
  电蚊香       ZAPPER              
  除湿器       DEHUMIDIFIER        
  电蒸锅       STEAMER             
  电炖锅       STEWPOT             
  充电器       CHARGER             
  插排         POWER\_STRIP        
  浇花器       SPRINKLER           
  场景触发     SCENE\_TRIGGER      
  其他         OTHER               

推荐品类和接口对应表，但具体产品支持的功能，需要根据
**设备发现时的capabilities字段动态判断** 。

-   SMARTPLUG/SWITCH

电源控制

> namespace: DNA.PowerControl
>
> >   动作(name)         属性(payload) 取值   范围
> >   ------------------ -------------------- -----------
> >   ChangePowerState   powerState           "ON"|"OFF
> >
-   TV和STB

电源控制
:   namespace: DNA.PowerControl

    >   动作(name)         属性(payload) 取值   范围
    >   ------------------ -------------------- -----------
    >   ChangePowerState   powerState           "ON"|"OFF
    >
频道控制
:   namespace: DNA.ChannelControl

    >   动作(name)      属性(payload) 取值   范围
    >   --------------- -------------------- -----------------
    >   ChangeChannel   channelNumber        频道号/频道名称
    >   AdjustChannel   channelSteps         -1至1
    >
播放控制
:   namespace: DNA.PlaybackControl

    >   动作(name)   属性(payload) 取值   范围
    >   ------------ -------------------- ------
    >   Play         无                   
    >   Pause        无                   
    >   Previous     无                   
    >   Next         无                   
    >
音量控制

> namespace: DNA.VolumeControl
>
> >   动作(name)     属性(payload) 取值   范围
> >   -------------- -------------------- ------------
> >   AdjustVolume   volumeSteps          -5至5
> >   SetMute        mute                 true|false
> >   SetVolume      volume               0至100
> >
-   AC

电源控制
:   namespace: DNA.PowerControl
    :   
          动作(name)         属性(payload) 取值   范围
          ------------------ -------------------- -----------
          ChangePowerState   powerState           "ON"|"OFF

温度模式控制

> namespace: DNA.ThermostatControl
>
> >   动作(name)                属性(payload) 取值范围   
> >   ------------------------- ------------------------ ------------------------
> >   SetTargetTemperature      targetPoint              0至50
> >   SetMode                   mode                     "COOL", "HEAT", "AUTO"
> >   AdjustTargetTemperature   targetPointSteps         -1至1
> >
风速控制

> namespace: DNA.WindSpeedControl
>
> >   动作(name)        属性(payload) 取值   范围
> >   ----------------- -------------------- ------
> >   SetWindSpeed      windSpeed            
> >   AdjustWindSpeed   windSpeedSteps       
> >
-   SENSOR

    所有DNA.xxxSensor的接口都可以使用

-   LIGHT

亮度控制

> namespace: DNA.BrightnessControl
>
> >   动作(name)      属性(payload) 取值   范围
> >   --------------- -------------------- --------
> >   SetBrightness   brightness           0至100
> >
电源控制

> namespace: DNA.PowerControl
>
> >   动作(name)         属性(payload) 取值   范围
> >   ------------------ -------------------- -----------
> >   ChangePowerState   powerState           "ON"|"OFF
> >
颜色控制（按HSL）
:   namespace: DNA.ColorControl

    >   动作(name)   属性(payload) 取值   范围
    >   ------------ -------------------- ------
    >   SetColor     hsl                  
    >
颜色控制（按颜色名称）
:   namespace: DNA.ColorNameControl

    >   动作(name)     属性(payload) 取值   范围
    >   -------------- -------------------- ------
    >   SetColorName   colorName            
    >
-   FAN

电源控制

> namespace: DNA.PowerControl
>
> >   动作(name)         属性(payload) 取值   范围
> >   ------------------ -------------------- -----------
> >   ChangePowerState   powerState           "ON"|"OFF
> >
风速控制

> namespace: DNA.WindSpeedControl
>
> >   动作(name)        属性(payload) 取值   范围
> >   ----------------- -------------------- ------
> >   SetWindSpeed      windSpeed            
> >   AdjustWindSpeed   windSpeedSteps       
> >
风向控制

> namespace: DNA.AirFlowControl
>
> >   动作(name)       属性(payload) 取值   范围
> >   ---------------- -------------------- ------
> >   Start                                 
> >   Stop                                  
> >   HorizontalFlow                        
> >   VerticalFlow                          
> >
-   CURTAIN

电源控制

> namespace: DNA.PowerControl
>
> >   动作(name)         属性(payload) 取值   范围
> >   ------------------ -------------------- -----------
> >   ChangePowerState   powerState           "ON"|"OFF
> >
运动控制

> namespace: DNA.MotionControl
>
> >   动作(name)   属性(payload) 取值   范围
> >   ------------ -------------------- ------
> >   Pause        无                   
> >   Stop         无                   
> >   Start                             
> >
-   其他

目前只支持电源控制

> namespace: DNA.PowerControl
>
> >   动作(name)         属性(payload) 取值   范围
> >   ------------------ -------------------- -----------
> >   ChangePowerState   powerState           "ON"|"OFF
> >
详细参考表
----------

[智能家居消息参考表](message_table.html#section)

[智能家居接口属性参考表](attribute_table.html#section)

[接口错误消息参考表](error_table.html#section)

[接口参考表](smarthome_api.html#section)
