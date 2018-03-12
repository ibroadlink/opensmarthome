

接口属性参考表
--------------

### 电源状态

> 名称: powerState
>
> 有效值: "ON", "OFF"
>
> 对应的动作：ChangePowerState, StateReport
>
> 示例：
>
> > ON表示打开电源
> >
> > OFF表示关闭电源

### 频道号

> 名称: channelNumber
>
> 有效值: 频道描述对象
>
> 对应的动作：ChangeChannel
>
> 示例：
>
> > value表示频道号

### 频道名称

> 名称: channelName
>
> 有效值: 频道描述对象
>
> 对应的动作：ChangeChannel
>
> 示例：
>
> > value表示频道号

### 步长频道

> 名称: channelSteps
>
> 有效值: 频道描述对象
>
> 对应的动作：AjustChannel
>
> 示例：
>
> value表示调节步长，正数表示增加，负数表示减少。

### 步长音量

> 名称： volumeSteps
>
> 有效值： 0-100
>
> 对应的动作：AdjustVolume
>
> 示例：
>
> value表示调节步长，正数表示增加，负数表示减少。

### 音量

> 名称： volume
>
> 有效值： 0-100
>
> 对应的动作：SetVolume
>
> 示例：
>
> value表示音量值。

### 静音

> 名称： mute
>
> 有效值： true,false
>
> 对应的动作：SetMute
>
> 示例：
>
> value表示音量值。

### 亮度

> 名称： brightness
>
> 有效值： 0-100
>
> 示例：
>
### 百分比

> 名称： percentage
>
> 有效值： 0-100
>
> 示例：
>
### 颜色

> 名称： color
>
> 有效值： 颜色对象
>
> 示例：
>
### 颜色名称

> 名称： colorName
>
> 有效值： 颜色名称对象
>
> 示例：
>
有效值：
AQUA、BLACK、BLUE、FUCHSIA、GRAY、GREEN、LIME、MAROON、NAVY、OLIVE、PURPLE、RED、SILVER、TEAL、WHITE、YELLOW

### 温度

> 名称： temperature
>
> 对应动作： StateReport， 表示查询
>
> 示例：
>
> value表示温度值
>
> scale表示单位，CELSIUS表示摄氏度。

### 湿度

> 名称： humidity
>
> 对应动作： StateReport， 表示查询
>
> 示例：
>
> value表示相对湿度百分比

### PM2.5

> 名称： pm2\_5
>
> 对应动作： StateReport， 表示查询
>
> 示例：
>
> value表示PM2.5浓度

### 目标值

> 名称： targetPoint
>
> 对应动作： SetTargetTemperature
>
> 示例：
>
> value表示值
>
> scale表示单位，CELSIUS表示摄氏度。

### 固定温度值

> 名称： fixedTargetTemperature
>
> 对应动作： SetFixedTargetTemperature
>
> 示例：
>
> value表示摄氏温度值

### 步长固定温度值（不带单位）

> 名称： fixedTargetTemperatureSteps
>
> 对应动作： AdjustFixedTargetTemperature
>
> 示例：
>
> value表示摄氏温度值调整步长，有效值1,-1.

### 步长固定温度值（带单位）

> 名称： targetPointSteps
>
> 对应动作： AdjustTargetPoint
>
> 示例：
>
> value表示调整的值大小，正数增加，负数减少.
>
> scale表示单位，CELSIUS表示摄氏度。

### 模式

> 名称: mode
>
> 有效值: 模式列表
>
> 对应的动作：SetMode
>
> 示例：
>
mode目前支持： "COLD", "HEAT", "AUTO", "VENT", "DEHUMI"

COLD: 制冷

HEAT： 制热

AUTO： 自动

VENT： 通风

DEHUMI: 除湿

### 风速

> 名称: windSpeed
>
> 有效值: 模式列表
>
> 对应的动作：SetWindSpeed
>
> 示例：
>
windSpeed目前支持： "AUTO", "LOW", "HIGH", "MEDIUM"

### 步长风速

> 名称: windSpeedSteps
>
> 有效值: 模式列表
>
> 对应的动作：AdjustWindSpeed
>
> 示例：
>
windSpeedSteps目前支持：正数和负数，正整表示增加，负整数表示减少

### 设备在线状态

> 名称: connectivity
>
> 有效值: OK,UNREACHABLE
>
> 对应的动作：无
>
> 示例：
>



