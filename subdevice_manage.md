# 子设备管理

## 基本步骤

网关设备对子设备进行管理，一般需要如下几个步骤：

一、子设备添加流程

    1. 开启子设备扫描，网关开始搜索附近子设备
    2. 循环获取搜索到的子设备列表，选择需要到子设备
    3. 关闭子设备扫描
    4. 将第2步获取到到子设备添加到网关设备中
    5. 查询子设备添加到结果

二、网关内已添加子设备列表获取

三、删除网关添加到子设备

## 参数定义

**subDevInfo**

```json
{
    "did":"xxxx",       //子设备唯一id
    "pid":"xxxx",       //子设备产品id
    "name":"xxxx",      //子设备名称
    "flag":0            //子设备是否被添加标记位
}
```

**subDevCloudInfo**

```json
{
    "did":"xxxx",       //子设备唯一id
    "pid":"xxxx",       //子设备产品id
    "name":"xxxx",      //子设备名称
    "flag":0,           //子设备是否被添加标记位
    "cookie":"xxxxxxxx" //子设备所属网关信息
}
```

## 操作流程

使用SDK对网关设备进行子设备管理，是基于二进制命令透传实现的，具体操作请配合Demo进行。
相关的命令类型：

```java
    private short BL_START_SCAN_SUBDEV_REQ = 0x0b04;
    private short BL_STOP_SCAN_SUBDEV_REQ = 0x0b06;
    private short BL_SCAN_SUBDEV_LIST_REQ = 0x0b08;
    private short BL_ADD_SUBDEV_REQ = 0x0b0a;
    private short BL_DEL_SUBDEV_REQ = 0x0b0c;
    private short BL_SUBDEV_LIST_REQ = 0x0b0e;
    private short BL_SUBDEV_INFO_EDIT_REQ = 0x0b14;
    private short BL_SUBDEV_ADD_RESULT_REQ = 0x0b16;
```

Demo相关接口介绍：

**开启子设备扫描**

```java
    /**
     * 开启子设备扫描
     * @param devicePairInfo 网关设备信息
     * @param subPid 扫描子设备的PID
     * @return 是否开启扫描
     */
    public Boolean startSubDevScan(DevicePairInfo devicePairInfo, String subPid);
```

**关闭子设备扫描**

```java
    /**
     * 关闭子设备扫描
     * @param devicePairInfo 网关设备信息
     * @return 是否开启扫描
     */
    public Boolean stopSubDevScan(DevicePairInfo devicePairInfo);
```
**获取扫描到的子设备列表**

```java
    /**
     * 网关设备获取扫描到的子设备列表
     * 该列表支持翻页查询，单次查询个数不得超过 5
     *
     * @param devicePairInfo 网关设备信息
     * @param index 查询页index，初始值 0
     * @param count 查询个数，最大值 5
     * @param subPid 扫描子设备产品类型
     * @return
     */
    public String querySubDevScanList(DevicePairInfo devicePairInfo, int index, int count, String subPid);
```
**添加子设备**

```java
    /**
     * 添加子设备到网关设备
     * @param devicePairInfo 网关设备信息
     * @param subDevInfo 子设备信息
     * @return
     */
    public String addSubDev(DevicePairInfo devicePairInfo, SubDevInfo subDevInfo);
```

**删除子设备**

```java
    /**
     *  从网关中删除指定did的子设备
     * @param devicePairInfo 网关设备信息
     * @param subDid 子设备DID
     * @return
     */
    public String delSubDev(DevicePairInfo devicePairInfo, String subDid);
```
**获取子设备列表**

```java
    /**
     * 网关设备已经添加的子设备列表
     * 该列表支持翻页查询，单次查询个数不得超过 5
     *
     * @param devicePairInfo 网关设备信息
     * @param index 查询页index，初始值 0
     * @param count 查询个数，最大值 5
     * @return
     */
    public String querySubDevListHaveBeenAdded(DevicePairInfo devicePairInfo, int index, int count);
```



