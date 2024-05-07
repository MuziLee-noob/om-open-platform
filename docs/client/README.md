[TOC]
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
示例
```
om.getNetworkType({
    success:function(res) {}
})
```
返回参数
|字段 |类型 |说明 |
|----|----|----|
|type|String|当前的网络类型：<br>wifi<br>2G<br>3G<br>4G<br>no-无网络<br>unknown-未知网络类型|

### 定位
#### 获取地理位置信息
说明：获取地理位置信息
getLocation
> 支持客户端：iOS、Android
示例
```
om.getLocation({
    type: "wgs84",
    success: function (res) {},
    fail: function (err) {},
})
```
请求参数
|字段|类型|必填|说明|
|----|----|-----|----|
|type|String|否|默认为“wgs84”代表 gps 坐标，支持传入“gcj02”。|

返回参数
|字段 |类型 |说明 |
|----|----|----|
|latitude|number|维度|
|longitude|number|经度|
|speed|number|速度|
|accuracy|number|精确度|
|address|String|地址，如河北省石家庄市长安区|
|province|String|省份|
|city|String|市，直辖市会返回空|
|district|String|区|
|road|String|街道|
#### 使用内置地图选择地址
说明：打开地图选择位置
chooseLocation
> 支持客户端：iOS、Android
示例
```
om.chooseLocation({
    type: "wgs84",
    success: function (res) {},
    fail: function (err) {},
})
```
请求参数
|字段|类型|必填|说明|
|----|----|-----|----|
|type|String|否|默认为“wgs84”代表 gps 坐标，支持传入“gcj02”。|

返回参数
|字段 |类型 |说明 |
|----|----|----|
|latitude|number|维度|
|longitude|number|经度|
|address|String|地址，如河北省石家庄市长安区|
#### 使用内置地图打开地理位置
说明：打开地图选择位置
openLocation
> 支持客户端：iOS、Android
示例
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
|字段|类型|必填|说明|
|----|----|-----|----|
|type|String|否|默认为“wgs84”代表 gps 坐标，支持传入“gcj02”。|
|latitude|number|是|维度|
|longitude|number|是|经度|
|name|String|否|位置名|
|address|String|否|地址详细说明|

#### 开启持续定位
说明：开启持续定位，需要通过卡其持续定位、关闭持续定位、位置变更通知三个API实现
startLocation
> 支持客户端：iOS、Android
示例
```
om.startLocation({
    type: "wgs84",
    success:function(res){}
    fail:function(res){}
})
```
请求参数
|字段|类型|必填|说明|
|----|----|-----|----|
|type|String|否|默认为“wgs84”代表 gps 坐标，支持传入“gcj02”。|

#### 关闭持续定位
说明：打开地图选择位置
stopLocation
> 支持客户端：iOS、Android
示例
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
|字段 |类型 |说明 |
|----|----|----|
|latitude|number|维度|
|longitude|number|经度|
|speed|number|速度|
|accuracy|number|精确度|
|address|String|地址，如河北省石家庄市长安区|
|province|String|省份|
|city|String|市，直辖市会返回空|
|district|String|区|
|road|String|街道|
#### 获取
### 电话
#### 拨打电话
说明：拨打电话
makeCall
> 支持客户端：iOS、Android
示例
```
om.makeCall({
    phoneNo: "13011111111",
    success:function(){}
    fail:function(res){}
})
```
请求参数
|字段|类型|必填|说明|
|----|----|-----|----|
|phoneNo|String|是|电话号码|
### 扫一扫
#### 扫一扫
说明：唤起客户端扫码界面
scanQRCode
> 支持客户端：iOS、Android
示例
```
om.scanQRCode({
    success:function(res){}
    fail:function(err){}
})
```
返回参数参数
|字段|类型|说明|
|----|----|----|
|scanResult|String|扫码结果|
### 截屏
#### 监听截屏
说明：截屏监听
onScreenShoot
> 支持客户端：iOS、Android
示例
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
示例
```
om.chooseImage({
    sourceType: ["album", "camera"],
    count: 9,
    success:(res){
        /**
        {
            files:[{"base64":""}]
        }
        */
    }
})
```
返回参数参数
|字段|类型|说明|
|----|----|----|
|scanResult|String|扫码结果|
#### 保存到系统相册
### 视频
#### 选择视频
#### 预览视频
## 界面
### 导航栏
#### 设置导航栏标题
#### 设置导航栏菜单
#### 设置导航栏背景颜色
### 页面
#### 关闭当前窗口
#### 打开新视图窗口
### 屏幕
#### 设置屏幕方向
#### 旋转屏幕到横屏状态
#### 重置屏幕状态
#### 全屏显示
## 通讯录
### 选择人员
### 打开人员名片
### 添加联系人到通讯录
## 消息
### 创建对话
### 选择对话
### 打开对话
### 创建群聊对话
### 打开群聊对话
## 文件
### 选择本地文件
### 文件下载到本地
## 音视频会议
### 单聊通话
#### 发起通话
### 多人会议
#### 创建会议
#### 加入会议
