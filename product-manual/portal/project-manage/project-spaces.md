---
id: project-spaces
sidebar_position: 2
---

# 项目空间

## 简介

项目空间管理的使用者一般为业务线的负责人或者辅助业务线负责人进行管理的人员，包含：

* 查看项目下所有空间信息，包含空间的成员、数据授权范围
* 任命空间的负责人
* 分配空间可用资源：产品系统、可使用的数据范围
* 新建/删除空间

![图 5](/img/xiangmukongjian_project-spaces.png)  

## 功能边界

* 项目空间下，无法进行空间内的管理。比如，管理空间成员。

## 功能说明

### 新建空间

* 项目的总空间数=企业分配给项目的空间数。
* **产品系统**指项目可用且在空间级使用的产品系统，如：增长分析、客户数据平台、智能运营

![图 6](/img/xinjiankongjian_project-spaces.png)  

### 查看空间详情

点击空间名称，进入空间详情页。

![图 7](/img/kongjianxiangqing_project-spaces.png)  

### 数据权限

通过授权配置，不同的空间可使用的项目数据范围不同。

> 授权模式：
>
> * 全部可用 ：可以使用全部，当有新的属性、标签、埋点事件时，自动授权项目使用。
>
> * 全部禁用：不可以使用任何用户属性、标签、埋点事件。
>
> * 自定义：可以自由定义使用用户属性、标签、埋点事件。

以下为【用户属性】授权的示例：

![图 3](/img/shujuquanxian_project-spaces.png)  

### 移交空间负责人

* 被任命的负责人，必须已经在空间中。
* 在移交之前，需要进行当前操作人员二次身份验证。

![图 4](/img/yijiaokongjianfuzeren_project-spaces.png)  
