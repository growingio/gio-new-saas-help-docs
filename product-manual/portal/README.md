---
id: enterprise-configuration
sidebar_position: 2
---

# 企业门户

## 简介[](#jian-jie)

企业门户核心能力是管理能力，管理者将资源合理的分配给部门/成员，每个成员基于职能，拥有相应权利、责任，成员之间协作达成业务目标。

分析云平台，从管理上划分了三个层级：企业-项目-空间。

## 什么是企业、项目、空间

### 在业务视角上

| 层级 | 含义 |
| ---- | -----  |
企业 | 可被理解为与GrowingIO直接对接的商务对象， 即为**合同签约主体**。所有商务上购买的产品，都以企业为单位提供产品与服务。如使用期限、项目数量、空间数量、产品系统等等。|
项目 | 可被理解为企业下多个独立运营的业务线，在管理上有一定的自主性。
空间 | 可以被理解为业务线的职能部门，成员在空间内完成具体的业务活动。

* 若GrowingIO可以做为企业， GrowingIO车险业务线若单独采购则亦可作为 “企业” 。
* 如大型集团，旗下有多个品牌需要独立运营，可以通过增购多个项目解决。

### 在数据视角上

项目层级是业务活动数据生产的单位，空间层级在授权范围内查询和使用数据。企业层级则拥有所有项目的数据。

举例：
集团有品牌A、品牌B，2个业务线独立运作

在分析云上的使用者有：

* 品牌A：小程序产品部门、APP产品部门

* 品牌B：官网产品部门、小程序产品部门、负责小程序、官网运营的运营部门

企业-项目-空间数据关系说明：

![图 4](/img/3cengjishujuguanxi_README.png)  

## 管理原则

1. 层级管理者可以进行本级成员的成员管理、资源分配。

2. 上级管理者可以进行下级负责人的任命。

3. 层级管理者在未授权情况下，不能跃级或者降级管理。

### 管理内容

| 层级 | 向下可分配的资源 | 可分配功能权限 |
| ---- | -----  |  ---- |
| 企业 | 企业总的空间配额、企业购买的产品系统 | 企业管理 |
| 项目 | 项目下的产品系统、项目数据 | 项目管理、数据中心、标签管理、获客分析、运营设置
| 空间 | - | 空间管理、增长分析、客户数据平台、智能运营 |

## 项目&空间应用场景介绍

### 从数据管理的角度看

项目是用来隔离业务使用，如：多品牌、多业态 。

* 不同的项目可以对接不同的数据源，每个项目可以独立管理元数据。

空间是用来限制数据使用范围。

* 不同的空间会被授权不同的数据，每个空间只能使用被当前空间授权的用户范围、数据源、事件、用户属性、用户标签、埋点事件、虚拟事件。
* 在不同空间中，创建的看板、分析单图、分群、运营活动，是无法被别的空间访问的。

### 从企业管理的角度看

项目是用来建立品牌、多业态业务隔离的。

* 是否需要分开多个项目，完全取决于企业的**业务形态**。
* ‌当我们有多品牌、业态相互独立经营时，我们可以考虑建立多个项目。

空间是用来建立组织间协作关系的。

* 是否需要分开多个空间，完全取决于企业的**组织管理方式**。
* 当我们多个团队间可访问的数据范围一致，且有需要有大量需要共同协作时，我们可以考虑在同一个空间中协作。

### 总结

是否需要建立多个项目/空间，或是在同一个项目中协作 ，完全取决于企业中团队与团队间的协作方式 。 有以下几个简单的判断原则：  
  
需要分开多个项目 ：

* 企业有多个独立运营的子品牌，品牌之间数据需要完全隔离。
* 企业有多个业态，业态数据差异化较大，无法统一分析。
  
需要分开多个空间 ：

* 团队间的KPI数据为高度敏感信息，不希望跨团队间分享。
* 团队业务活动非常独立，并没有协作的需求 。

在一个空间中：

* 团队间的协作紧密，需要一同协作 ，比如市场需要知道用户的画像，产品需要知道获客的情况。
