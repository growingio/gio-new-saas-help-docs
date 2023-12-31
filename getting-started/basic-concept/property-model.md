---
id: property-model
sidebar_position: 4
---

# 属性模型

事物的性质和人的特征

## 简介[](#jian-jie)

属性是用于描述一个事物与性质的关系。事物与属性是不可分的，事物都是有属性的事物，属性也都是事物的属性。脱离了事物谈属性，属性也失去了它应有的色彩和意义。

GrowingIO 系统中支持三种事物模型，分别为事件模型、用户模型和维度表模型（广义的事物，如商品、门店等），其对应的属性如下：

| 事物模型   | 属性类型             |
| ---------- | -------------------- |
| 事件模型   | 预定义属性、事件属性 |
| 维度表模型 | 维度表属性           |
| 用户模型   | 用户信息、用户属性   |

根据描述的事物不同，事物的属性也千差万别。我们拿以下场景举例：

在电商业务中，我们经常会关注订单支付成功这一行为。为了更清晰地描述这一行为，谁在什么时间做什么事情，我们会用以下几个属性描述订单支付成功事件。

| 属性           | 属性值            |
| -------------- | ----------------- |
| 时间           | 2015-05-01        |
| 用户 ID        | 3325103           |
| 订单 ID        | 62531631501961032 |
| 订单支付金额   | 2999.00           |
| 是否使用优惠券 | 是                |
| 优惠券名称     | 新人大礼包        |

为了满足不同事物的属性描述，我们支持四种属性类型，分别为字符串、整数、小数和日期。根据事物的差异，上述属性分别支持以下几种属性类型：

| 属性       | 字符串 | 整数 | 小数 | 日期 |
| ---------- | ------ | ---- | ---- | ---- |
| 预定义属性 | --     | --   | --   | --   |
| 事件属性   | ✔️     | ✔️   | ✔️   | ​    |
| 维度表属性 | ✔️     | ​    | ​    | ​    |
| 用户信息   | --     | --   | --   | --   |
| 用户属性   | ✔️     | ✔️   | ​    | ✔️   |

事件属性仅支持非负整数和非负小数

> 注意：创建属性时可选择属性类型，创建成功后属性类型不可更改

## 属性说明[](#shu-xing-shuo-ming)

| 属性名称   | 说明                                       |
| ---------- | ------------------------------------------ |
| 预定义属性 | 系统预置的事件属性，SDK 配置成功后自动采集 |
| 事件属性   | 自定义配置的事件属性                       |
| 维度表属性 | 自定义配置的维度表属性                     |
| 用户信息   | 系统预置的用户属性，需要主动上传数据       |
| 用户属性   | 自定义配置的用户属性                       |

## 属性管理[](#shu-xing-guan-li)

GrowingIO 系统支持对[事件属性](../../product-manual/data-center/event-management/event-property)、[维度表](../../product-manual/data-center/dimension-table-management)和[用户属性](../../product-manual/data-center/user-management/user-properties)的创建、编辑和查看功能，详情请点击对应文字链接。

​[预定义属性](../../product-manual/data-center/event-management/present-property)和[用户信息](../../product-manual/data-center/user-management/user-identifications)为系统预置信息，仅支持查看，详情请点击对应文字链接。

## 属性关联[](#shu-xing-guan-lian)

事件属性创建成功后，需要主动关联事件，关联成功后才能在事件中使用相应的事件属性。
维度表创建成功后，需要主动给关联事件属性，关联成功后才能在事件中使用相应的维度表属性。

> 注意：如果事件没有关联或取消关联事件属性，即使数据正常上传也无法解析，且不支持计算对应属性的统计数据

用户属性创建成功后无需额外配置即可在系统中使用。

配置方法：[事件属性](../../product-manual/data-center/event-management/event-property#创建事件属性)、[维度表](../../product-manual/data-center/dimension-table-management#创建维度表)​

## 数据格式[](#shu-ju-ge-shi)

GrowingIO 支持多种语言的 SDK，不同语言的 SDK 上报数据和导入数据都使用统一的数据格式。不同属性类型的数据格式说明如下：

| 属性类型 | 格式限制                                              | 示例                                    |
| -------- | ----------------------------------------------------- | --------------------------------------- |
| 字符串   | 非空字符串                                            | 'GrowingIO'                             |
| 整数     | 以字符格式传入                                        | '1234567'                               |
| 小数     | 以字符格式传入，<br></br>小数点后最多包含四位有效数字 | '3.1415'                                |
| 日期     | 以字符格式传入，<br></br>yyyy-mm-dd 或 时间戳(毫秒)   | '2040-05-01' 或<br></br>'2219414400000' |

如上传数据不符合上述格式要求，GrowingIO 系统会对部分数据类型上传的数据进行强制格式转换，具体说明如下：

| 属性类型 | 转化规则                                               | 示例                                      |
| -------- | ------------------------------------------------------ | ----------------------------------------- |
| 整数     | 上传数据为小数时，按高斯取整处理，仅保留整数部分       | 上传: 9.99<br></br>存储: 9                |
| 小数     | 上传数据为高精度小数(超四位)时，按四舍五入保留四位小数 | 上传: 3.1415926<br></br>存储: 3.1416      |
| 日期     | 上传数据为整数或小数时，按毫秒时间戳转成日期格式存储   | 上传: 1588262400<br></br>存储: 1970-01-19 |

> 注意：日期属性如按时间戳格式上传时，需使用毫秒级时间戳（13 位）；如上传秒级时间戳（10 位）时存储时间会发生错误
