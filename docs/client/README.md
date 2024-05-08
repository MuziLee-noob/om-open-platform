# 客户端开放平台接口

## 接口调用准备及说明

此文档主要面向开发者介绍如何使用平台JSAPI及相关注意事项。

H5微应用JSAPI为应用提供了调用原生控件的能力，帮助开发者高效使用媒体、定位等手机系统的能力；同时可以直接使用分享、扫一扫等客户端特有的能力，带给微应用接近原生代码的体验。

## 免登流程 (暂无)

### 获取免登授权码

## JSAPI鉴权（暂无）

### JSAPI鉴权

## 设备

### 网络

#### 获取网络类型

说明：获取设备当前网络类型
getNetworkType

> 支持客户端：iOS、Android
> 示例

```
om.getNetworkType({
    success:function(res) {}
})
```

返回参数

| 字段 | 类型   | 说明                                                         |
| ---- | ------ | ------------------------------------------------------------ |
| type | String | 当前的网络类型：<br>wifi<br>2G<br>3G<br>4G<br>no-无网络<br>unknown-未知网络类型 |

### 定位

#### 获取地理位置信息

说明：获取地理位置信息
getLocation

> 支持客户端：iOS、Android
> 示例

```
om.getLocation({
    type: "wgs84",
    success: function (res) {},
    fail: function (err) {},
})
```

请求参数

| 字段 | 类型   | 必填 | 说明                                          |
| ---- | ------ | ---- | --------------------------------------------- |
| type | String | 否   | 默认为“wgs84”代表 gps 坐标，支持传入“gcj02”。 |

返回参数

| 字段      | 类型   | 说明                         |
| --------- | ------ | ---------------------------- |
| latitude  | number | 维度                         |
| longitude | number | 经度                         |
| speed     | number | 速度                         |
| accuracy  | number | 精确度                       |
| address   | String | 地址，如河北省石家庄市长安区 |
| province  | String | 省份                         |
| city      | String | 市，直辖市会返回空           |
| district  | String | 区                           |
| road      | String | 街道                         |

#### 使用内置地图选择地址

说明：打开地图选择位置
chooseLocation

> 支持客户端：iOS、Android
> 示例

```
om.chooseLocation({
    type: "wgs84",
    success: function (res) {},
    fail: function (err) {},
})
```

请求参数

| 字段 | 类型   | 必填 | 说明                                          |
| ---- | ------ | ---- | --------------------------------------------- |
| type | String | 否   | 默认为“wgs84”代表 gps 坐标，支持传入“gcj02”。 |

返回参数

| 字段      | 类型   | 说明                         |
| --------- | ------ | ---------------------------- |
| latitude  | number | 维度                         |
| longitude | number | 经度                         |
| address   | String | 地址，如河北省石家庄市长安区 |

#### 使用内置地图打开地理位置

说明：打开地图选择位置
openLocation

> 支持客户端：iOS、Android
> 示例

```
om.openLocation({
    type: "wgs84",
    latitude:,
    longitude:,
    name:'',
    address:'',
})
```

请求参数

| 字段      | 类型   | 必填 | 说明                                          |
| --------- | ------ | ---- | --------------------------------------------- |
| type      | String | 否   | 默认为“wgs84”代表 gps 坐标，支持传入“gcj02”。 |
| latitude  | number | 是   | 维度                                          |
| longitude | number | 是   | 经度                                          |
| name      | String | 否   | 位置名                                        |
| address   | String | 否   | 地址详细说明                                  |

#### 开启持续定位

说明：开启持续定位，需要通过卡其持续定位、关闭持续定位、位置变更通知三个API实现
startLocation

> 支持客户端：iOS、Android
> 示例

```
om.startLocation({
    type: "wgs84",
    success:function(res){}
    fail:function(res){}
})
```

请求参数

| 字段 | 类型   | 必填 | 说明                                          |
| ---- | ------ | ---- | --------------------------------------------- |
| type | String | 否   | 默认为“wgs84”代表 gps 坐标，支持传入“gcj02”。 |

#### 关闭持续定位

说明：打开地图选择位置
stopLocation

> 支持客户端：iOS、Android
> 示例

```
om.stopLocation({
    success:function(res){}
    fail:function(res){}
})
```

#### 持续定位位置监听

说明：持续定位地理位置变化叫监听，持续定位开启后生效
onLocationChange

```
om.startLocation({
    type: "wgs84",
    success:function(res){}
    fail:function(res){}
})

om.onLocationChange((result) => {})
```

返回参数

| 字段      | 类型   | 说明                         |
| --------- | ------ | ---------------------------- |
| latitude  | number | 维度                         |
| longitude | number | 经度                         |
| speed     | number | 速度                         |
| accuracy  | number | 精确度                       |
| address   | String | 地址，如河北省石家庄市长安区 |
| province  | String | 省份                         |
| city      | String | 市，直辖市会返回空           |
| district  | String | 区                           |
| road      | String | 街道                         |

#### 获取

### 电话

#### 拨打电话

说明：拨打电话
makeCall

> 支持客户端：iOS、Android
> 示例

```
om.makeCall({
    phoneNo: "13011111111",
    success:function(){}
    fail:function(res){}
})
```

请求参数

| 字段    | 类型   | 必填 | 说明     |
| ------- | ------ | ---- | -------- |
| phoneNo | String | 是   | 电话号码 |

### 扫一扫

#### 扫一扫

说明：唤起客户端扫码界面
scanQRCode

> 支持客户端：iOS、Android
> 示例

```
om.scanQRCode({
    success:function(res){}
    fail:function(err){}
})
```

返回参数参数

| 字段       | 类型   | 说明     |
| ---------- | ------ | -------- |
| scanResult | String | 扫码结果 |

### 截屏

#### 监听截屏

说明：截屏监听
onScreenShoot

> 支持客户端：iOS、Android
> 示例

```
om.onScreenShoot(()=>{

})
```

## 媒体

### 图片

#### 选择图片

说明：唤起客户端选择图片界面
chooseImage

> 支持客户端：iOS、Android
> 示例

```
om.chooseImage({
    sourceType: ["album", "camera"],
    count: 9,
    success:function(res){
        /**
        {
            files:[{"base64":""}]
        }
        */
    },
    fail:function(err){}
})
```

请求参数

| 字段       | 类型   | 必填 | 说明                                                     |
| ---------- | ------ | ---- | -------------------------------------------------------- |
| sourceType | Array  | 否   | 相册：["album"]，相机：["camera"]，当为camera时count无效 |
| count      | Number | 否   | 图片数量                                                 |

返回参数

| 字段  | 类型  | 说明                                     |
| ----- | ----- | ---------------------------------------- |
| files | Array | 图片文件列表，列表内为base64为图片base64 |

#### 保存到系统相册

说明：根据图片或视频的url保存相册
saveToPhotosAlbum

> 支持客户端：iOS、Android
> 示例

```
om.saveToPhotoAlbum({
    url:"",
    success:function(){},
    fail:function(err){}
})
```

请求参数

| 字段 | 类型   | 必填 | 说明    |
| ---- | ------ | ---- | ------- |
| url  | String | 否   | 图片url |

## 界面

### 导航栏

#### 设置导航栏标题

说明：设置导航栏标题
setTitle

> 支持客户端：iOS、Android

示例

```
om.setTitle({
    title:"",
})
```

请求参数

| 字段  | 类型   | 必填 | 说明 |
| ----- | ------ | ---- | ---- |
| title | String | 否   | 标题 |

### 页面

#### 关闭当前窗口

说明：关闭窗口
closeWindow

> 支持客户端：iOS、Android

示例

```
om.closeWindow()
```

#### 打开新视图窗口

说明：打开窗口
openWindow

> 支持客户端：iOS、Android

示例

```
om.openWindow({
    url:"",
    title:"",
    hiddenBar:0,
    alias:""
})
```

请求参数

| 字段      | 类型   | 必填 | 说明                         |
| --------- | ------ | ---- | ---------------------------- |
| url       | String | 是   | 加载地址                     |
| title     | String | 否   | 标题                         |
| hiddenBar | Number | 否   | 0不隐藏标题栏，1为隐藏标题栏 |
| alias     | String | 否   | 别名                         |

### 屏幕

#### 设置屏幕方向

说明：设置屏幕方向，退出后回到竖屏
setScreenDirection

> 支持客户端：iOS、Android

示例

```
om.setScreenDirection({
    direction: 0,
    success: function () {},
    fail: function (error) {},
})
```

请求参数

| 字段      | 类型   | 必填 | 说明          |
| --------- | ------ | ---- | ------------- |
| direction | Number | 是   | 1-竖屏 2-横屏 |

## 通讯录

### 选择人员

说明：唤起选择人员界面，可选择用户
chooseContact

> 支持客户端：iOS、Android

示例

```
om.chooseContact({
    chosenIds: ["1"], 
    disableChosenIds: ["1"],
    multiple:0,
    max:3;
    success:function(res){
        /**
            [{"name":"",userId:""}]
        */
    }
    fail:function(err){

    }
})
```

请求参数

| 字段             | 类型          | 必填 | 说明           |
| ---------------- | ------------- | ---- | -------------- |
| chosenIds        | Array<String> | 否   | 默认选中的人员 |
| disableChosenIds | Array<String> | 否   | 不可选中的人员 |
| multiple         | Number        | 否   | 0-单选 1-多选  |
| max              | Number        | 否   | 最大选择人数   |

返回参数

| 字段   | 类型   | 说明   |
| ------ | ------ | ------ |
| name   | String | 名称   |
| userId | String | 用户ID |

### 打开人员信息界面

说明：打开人员信息界面
openProfile

> 支持客户端：iOS、Android

示例

```
om.openProfile({
    profileId: ""
    success:function(){
    }
    fail:function(err){
    }
})
```

请求参数

| 字段      | 类型   | 必填 | 说明   |
| --------- | ------ | ---- | ------ |
| profileId | String | 是   | 人员ID |

## 聊天

### 打开单聊会话

说明：打开单聊会话界面
enterChat

> 支持客户端：iOS、Android

示例

```
om.enterChat({
    chatId: ""
    success:function(){
    }
    fail:function(err){
    }
})
```

请求参数

| 字段   | 类型   | 必填 | 说明   |
| ------ | ------ | ---- | ------ |
| chatId | String | 是   | 聊天ID |

### 打开群聊

说明：打开已有群聊界面
enterGroupChat

> 支持客户端：iOS、Android

示例

```
om.enterGroupChat({
    groupId: ""
    success:function(){
    }
    fail:function(err){
    }
})
```

请求参数

| 字段    | 类型   | 必填 | 说明   |
| ------- | ------ | ---- | ------ |
| groupId | String | 是   | 群组ID |

## 文件

### 选择本地文件

说明：选择本地文件
chosenFile

> 支持客户端：iOS、Android

示例

```
om.chosenFile({
    success:function(res){
        /**
        base64:""
        */
    }
    fail:function(err){
    }
})
```

返回参数

| 字段   | 类型   | 说明             |
| ------ | ------ | ---------------- |
| base64 | String | 文件的base64数据 |

### 文件下载到本地

说明：文件下载至本地
downLoadFile

> 支持客户端：iOS、Android

示例

```
om.downLoadFile({
    url: ""
    success:function(){
    }
    fail:function(err){
    }
})
```

请求参数

| 字段 | 类型   | 必填 | 说明     |
| ---- | ------ | ---- | -------- |
| url  | String | 是   | 文件地址 |

## 音视频会议

### 单聊通话

#### 发起通话

说明：单聊通话
makeCall

> 支持客户端：iOS、Android

示例

```
om.makeCall({
    userId: ""
    success:function(){
    }
    fail:function(err){
    }
})
```

请求参数

| 字段   | 类型   | 必填 | 说明   |
| ------ | ------ | ---- | ------ |
| userId | String | 是   | 对端ID |

### 多人会议

#### 加入会议

说明：加入会议
joinMeeting

> 支持客户端：iOS、Android

示例

```
om.joinMeeting({
    meetingCode: ""
    success:function(){
    }
    fail:function(err){
    }
})
```

请求参数

| 字段        | 类型   | 必填 | 说明   |
| ----------- | ------ | ---- | ------ |
| meetingCode | String | 是   | 会议号 |
