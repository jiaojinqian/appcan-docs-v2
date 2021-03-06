﻿[TOC]

#1、简介[![](http://appcan-download.oss-cn-beijing.aliyuncs.com/%E5%85%AC%E6%B5%8B%2Fgf.png)]()
系统联系人插件
##1.1、说明
打开，添加，删除，查找，修改联系人等功能。
##1.2、UI展示
 ![](http://newdocx.appcan.cn/docximg/152401g2015a6l7b.jpg)
##1.3、开源源码
插件测试用例与源码下载：[点击](http://plugin.appcan.cn/details.html?id=161_index) 插件中心至插件详情页 （插件测试用例与插件源码已经提供）
#2、API概览
 ##2.1、方法
> ### open　打开联系人界面
`uexContact.open()`
**说明:**
打开联系人应用，将选中的联系人的姓名，电话，邮件通过cbOpen回调，每次只能选择一个联系人。回调方法[cbOpen](#cbOpen　打开联系人界面的回调方法)
**参数:**
无
**平台支持:**
Android2.2+
iOS6.0+
**版本支持:**
3.0.0+
**示例:**

```
uexContact.open();
```
> ### multiOpen　　打开联系人选择界面

`uexContact.multiOpen()`
**说明:**
打开联系人选择界面，该界面中的数据是当前设备上所有联系人的信息，支持多选。回调方法[cbMultiOpen](#cbMultiOpen　打开联系人选择界面的回调方法)
**参数:**
  无
**平台支持:**
Android2.2+
iOS6.0+
** 版本支持:**
3.0.0+
** 示例:**

```
uexContact.multiOpen();
```
> ### addItem　添加联系人

`uexContact.addItem(name,num,email)`
** 说明:**

添加联系人
**  参数:**

|  参数名称 | 参数类型  | 是否必选  |  说明 |
| ------------ | ------------ | ------------ | ------------ |
| name | String | 是 |  名称 |
| num| Number | 是 | 电话号码 |
| email | String | 是 | 邮件 |

**平台支持:**
Android2.2+
iOS6.0+
**版本支持:**
3.0.0+
**示例:**

```
uexContact.addItem("张三","13436827900","widgetone@3g2win.com");
```
> ### deleteItem　删除联系人

`uexContact.deleteItem(name)`
**说明:**
删除联系人 回调方法[cbDeleteItem](#cbDeleteItem　删除联系人的回调方法)
**参数:**

|  参数名称 | 参数类型  | 是否必选  |  说明 |
| ------------ | ------------ | ------------ | ------------ |
| name | String | 是 |  名称 |

**平台支持:**
Android2.2+
iOS6.0+
**版本支持:**
3.0.0+
**示例:**

```
uexContact.deleteItem(“张三“);
```
> ### searchItem　查询联系人

`uexContact.searchItem(nameKey)`
**说明:**
查询联系人 回调方法[cbSearchItem](#cbSearchItem　查询联系人的回调方法)
 ** 参数:**

|  参数名称 | 参数类型  | 是否必选  |  说明 |
| ------------ | ------------ | ------------ | ------------ |
| nameKey | String | 是 |  名称 |

**平台支持:**
Android2.2+
iOS6.0+
**版本支持:**
3.0.0+
**示例:**

```
uexContact.searchItem(“张三“);
```
> ### modifyItem　修改联系人

`uexContact.modifyItem(name,num,email)`
**说明:**

修改联系人 回调方法[cbModifyItem](#cbModifyItem　修改联系人的回调方法)
**参数:**

|  参数名称 | 参数类型  | 是否必选  |  说明 |
| ------------ | ------------ | ------------ | ------------ |
| name | String | 是 |  名称 |
| num| Number | 是 | 电话号码 |
| email | String | 是 | 邮件 |

**平台支持:**
Android2.2+
iOS6.0+
**版本支持:**
  3.0.0+
**示例:**

```
uexContact.modifyItem("张三","13436827900","widgetone@3g2win.com");
```
> ### addItemWithVCard　添加联系人

`uexContact.addItemWithVCard(data,type)`
**说明:**
添加联系人 回调方法[cbAddItem](#cbAddItem　添加联系人的回调方法)
**参数:**

|  参数名称 | 参数类型  | 是否必选  |  说明 |
| ------------ | ------------ | ------------ | ------------ |
| data | String | 是 |  联系人数据，数据格式如下：`BEGIN:VCARD\nVERSION:3.0\nN:韩;超\nTEL:22334752\nEMAIL:zhuliang@ceair.com\nADR:;;绥宁路628号;;上海;200335\nORG:中国东方航空股有限公司\nTITLE:项目经理\nURL:mp.ceair.com\nNOTE:名\347\211\214二维码\nEND:VCARD`    其中：N-姓名，TEL-电话，EMAIL-邮箱，ADR-地址，ORG-公司，TITLE-职位，URL-网址，NOTE-备注 |
| type| Number | 是 | 是否显示提示框，1-不显示，其余情况显示。 |

**平台支持:**
Android2.2+
iOS6.0+
**版本支持:**
3.0.0+
**示例:**

```
uexContact.addItemWithVCard(`BEGIN:VCARD\nVERSION:3.0\nN:韩;超\nTEL:22334752\nEMAIL:zhuliang@ceair.com
\nADR:;;绥宁路628号;;上海;200335\nORG:中国东方航空股有限公司\nTITLE:项目经理\nURL:mp.ceair.com\nNOTE:名\347\211\214二维码\nEND:VCARD`);
```
##2.2   回调方法
> ### cbOpen　打开联系人界面的回调方法

`uexContact.cbOpen(opId,dataType,data)`
**参数:**

|  参数名称 | 参数类型  | 是否必选  |  说明 |
| ------------ | ------------ | ------------ | ------------ |
| opId | Number | 是 |  操作ID，在此函数中不起作用，可忽略 |
| dataType| Number | 是 | 参数类型详见CONSTANT中Callback方法数据类型 |
| data | Number | 是 | Key值uex.jkName、uex.jkNum、uex.jkEmail，详见CONSTANT中CallbackJson类型keyname |

**版本支持:**
3.0.0+
**示例:**

```
window.uexOnload = function(){
    uexContact.cbOpen = function(opCode, dataType, data) {
        var obj = eval(`(` + data + `)`);
        alert(data);
   }
}
```
> ### cbMultiOpen　打开联系人选择界面的回调方法

`uexContact.cbMultiOpen(opId,dataType,data)`
**参数:**

|  参数名称 | 参数类型  | 是否必选  |  说明 |
| ------------ | ------------ | ------------ | ------------ |
| opId | Number | 是 |  操作ID，在此函数中不起作用，可忽略 |
| dataType| Number | 是 | 参数类型详见CONSTANT中Callback方法数据类型 |
| data | Number | 是 | Key值uex.jkName、uex.jkNum、uex.jkEmail，详见CONSTANT中CallbackJson类型keyname |

**版本支持:**
3.0.0+
**示例:**
```
window.uexOnload = function(){
    uexContact.cbMultiOpen = function(opCode, dataType, data){
        alert(data);
    }
}
```

> ### cbAddItem　添加联系人的回调方法

`uexContact.cbAddItem(opId,dataType,data)`
**参数:**

|  参数名称 | 参数类型  | 是否必选  |  说明 |
| ------------ | ------------ | ------------ | ------------ |
| opId | Number | 是 |  操作ID，在此函数中不起作用，可忽略 |
| dataType| Number | 是 | 参数类型详见CONSTANT中Callback方法数据类型 |
| data | Number | 是 | 返回uex.cSuccess或者uex.cFailed，详见CONSTANT中Callbackint类型数据 |

**版本支持:**
3.0.0+
**示例:**
```
window.uexOnload = function(){
    uexContact.cbAddItem = function(opCode, dataType, data){
        alert(data);
    }
}
```

> ### cbDeleteItem　删除联系人的回调方法

`uexContact.cbDeleteItem(opId,dataType,data)`
**参数:**

|  参数名称 | 参数类型  | 是否必选  |  说明 |
| ------------ | ------------ | ------------ | ------------ |
| opId | Number | 是 |  操作ID，在此函数中不起作用，可忽略 |
| dataType| Number | 是 | 参数类型详见CONSTANT中Callback方法数据类型 |
| data | Number | 是 | 返回uex.cSuccess或者uex.cFailed，详见CONSTANT中Callbackint类型数据 |

**版本支持:**
3.0.0+
**示例:**
```
window.uexOnload = function(){
    uexContact.cbDeleteItem = function(opCode, dataType, data){
        alert(data);
    }
}
```

> ### cbSearchItem　查询联系人的回调方法

`uexContact.cbSearchItem(opId,dataType,data)`
**参数:**

|  参数名称 | 参数类型  | 是否必选  |  说明 |
| ------------ | ------------ | ------------ | ------------ |
| opId | Number | 是 |  操作ID，在此函数中不起作用，可忽略 |
| dataType| Number | 是 | 参数类型详见CONSTANT中Callback方法数据类型 |
| data | String | 是 | 返回的数据。Key值uex.jkName、uex.jkNum、uex.jkEmail，详见CONSTANT中CallbackJson类型keyname |
 
**版本支持:**
3.0.0+
**示例:**
```
window.uexOnload = function(){
    uexContact.cbSearchItem = function(opCode, dataType, data){
        alert(data);
    }
}
```

> ### cbModifyItem　修改联系人的回调方法

`uexContact.cbModifyItem(opId,dataType,data)`
**参数:**

|  参数名称 | 参数类型  | 是否必选  |  说明 |
| ------------ | ------------ | ------------ | ------------ |
| opId | Number | 是 |  操作ID，在此函数中不起作用，可忽略 |
| dataType| Number | 是 | 参数类型详见CONSTANT中Callback方法数据类型 |
| data | Number | 是 | 返回uex.cSuccess或者uex.cFailed，详见CONSTANT中Callbackint类型数据 |

**版本支持:**
3.0.0+
**示例:**
```
window.uexOnload = function(){
    uexContact.cbModifyItem = function(opCode, dataType, data){
        alert(data);
    }
}
```

#3、更新历史
API 版本：uexContact-3.0.6(iOS) uexContact-3.0.0（Android）
最近更新时间：2015-06-19

|  历史发布版本 | iOS更新  | 安卓更新  |
| ------------ | ------------ | ------------ |
| 3.0.6  |修改配置文件，修改BUG   |   |
| 3.0.5  |修改BUG   |   |
| 3.0.4 | 修改打开联系人，多选信息电话号码不全的BUG  |   |
| 3.0.3  | 增加可以查询和，修改多个号码的联系人接口  |   |
| 3.0.2  |  修改增加联系人接口，一个联系人可以添加多个电话号码 |   |
| 3.0.1  | 修复uexContact在iOS8以上版本无法返回联系人信息的bug  | |
| 3.0.0  | 联系人功能插件  | 联系人功能插件|
