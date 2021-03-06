﻿[TOC]
# 1、简介 [![](http://appcan-download.oss-cn-beijing.aliyuncs.com/%E5%85%AC%E6%B5%8B%2Fgf.png)]()
视频播放插件
## 1.1、说明
 封装视频播放和录制相关操作
## 1.2、UI展示
 ![](http://newdocx.appcan.cn/docximg/152402p2015k6n7f.jpg)
 ![](http://newdocx.appcan.cn/docximg/151401g2015e6r7v.jpg)
## 1.3、开源源码
插件测试用例与源码下载：[点击](http://plugin.appcan.cn/details.html?id=194_index) 插件中心至插件详情页 （插件测试用例与插件源码已经提供）

# 2、API概览

## 2.1、方法

> ### open 打开视频播放界面

`uexVideo.open(path,orientation)`
**说明:**
打开视频播放界面
**参数:**

|  参数名称 | 参数类型  | 是否必选  |  说明 |
| ------------ | ------------ | ------------ | ------------ |
| path | String | 是 | 视频文件路径，路径协议详见CONSTANT中PathTypes |
| orientation | Number | 否 | 1:强制横屏，仅iOS有效 |

**平台支持:**
Android2.2+
iOS6.0+
**版本支持:**
3.0.0+
**示例:**
```
uexVideo.open("res://1.mp4")
```
> ### record 打开视频录制界面
  
`uexVideo.record()`
**说明:**
  打开视频录制界面
  回调 [cbRecord](#cbRecord 录制完成的回调方法 "录制完成的回调方法")
**参数:**
  无
**平台支持:**
Android2.2+
iOS6.0+
**版本支持:**
3.0.0+
**示例:**

```
uexVideo.record();
```
## 2.2、回调方法
> ### cbRecord 录制完成的回调方法
  
`uexVideo.cbRecord(opId,dataTpye,data)`
**参数:**

|  参数名称 | 参数类型  | 是否必选  |  说明 |
| ------------ | ------------ | ------------ | ------------ |
| opId | Number | 是 |  操作ID，在此函数中不起作用，可忽略 |
| dataType| Number | 是 | 参数类型详见CONSTANT中Callback方法数据类型 |
| data | String | 是 | 视频路径 |

**版本支持:**
3.0.0+
**示例**
```
function cbRecord (opId,dataType,data){
    alert(data);
}
window.uexOnload = function(){
    uexVideo.cbRecord = cbRecord ;
}
```
# 3、更新历史
API 版本：uexVideo-3.0.3(iOS) uexVideo-3.0.2（Android）
最近更新时间：2015-06-19

|  历史发布版本 | iOS更新  | 安卓更新  |
| ------------ | ------------ | ------------ |
| 3.0.3  | 重新编译，支持arm64  |   |
| 3.0.2  |  支持arm64 | 修复录制视频时模糊问题  |
| 3.0.1  | 更换动画效果，修复在6.1.2上的显示问题  | 修复res路径解析出错问题 |
| 3.0.0  | 视频功能插件  | 视频功能插件|
