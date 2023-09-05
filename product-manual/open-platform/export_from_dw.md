---
id: export_from_dw
sidebar_position: 2
---

# 离线数据导出

## 简介

GrowingIO 为开放架构，采集上报的用户数据支持离线导出到客户的自建数仓或数据湖系统，以满足在客户在自身系统中做数据集成应用。

离线数据导出需要较充裕的磁盘空间，它是默认关闭的。
开启功能管理入口：【开放平台】 - 【离线数据导出】

![图 1](/img/export_from_dw_01.png)  


## 能力边界和约束

- 用户数据由系统定时生成为文件供下载使用，不支持直连数仓导出数据。
- 系统生成文件的启动时间为每日凌晨，生成完毕的时间跟数据量有关，建议观察稳定后再做下游的使用配置。
- 每天定时生成的文件，按种类分为 5 组压缩文件：事件明细、用户 ID、用户属性、用户标签和用户分群，每组文件在其文件夹中存储。
- 用户 ID/属性/标签解压后的文件均是以 gio_id（GrowingIO 生成的用户编号）为首列（主键）的两列数据，第二列是用户字段的值。比如用户属性为生日的文件，第二列即是用户的生日值。这样设计的优点是文件内容的结构稳定，更接近数据的本质，使用灵活；缺点是在用户宽表的使用场景中，需要将所需字段的文件按主键关联整合成宽表存储，有一定的 ETL 工作量。
- 事件明细的数据是 T+1 的增量数据，即今天凌晨生成的文件内容是昨日 0 点起至 23 点末的事件；用户 ID/属性/标签/分群则为全量用户数据。

## 标准操作流程
SaaS客户的用户导出离线数据的流程步骤

![图 1](/img/export_05.jpg)  

## 功能说明


### 开启离线数据导出 
![图 3](/img/export_from_dw_03.jpg) 

### 配置数据导出范围 

 5 类数据以及导出范围设置方式：

  - 埋点事件，支持按事件分类选择导出事件范围：
    - 全选
    - 自定义埋点事件
    - 预定义Visit,Page事件
    - 预定义元素级无埋点事件

  - 用户身份，可选范围：元数据管理-用户身份中，定义的全部身份

 - 用户属性，支持按照用户属性分类选择属性范围，分类标准-元数据管理-用户属性——一级目录分类
 - 用户标签，支持按照标签分类选择用户标签范围，分类标准-客户数据平台-用户标签一级目录分类
 - 用户分群，可选范围：当前项目-客户数据平台-群组管理（全部空间）的群组

![图 4](/img/export_data_04.jpg) 


### 获取离线数据文件列表 API 

#### 接口地址

```
http://{api-host}/v1/api/projects/{projectId}/data_export/{file_create_date}/{file_type}
```

#### 请求方式

    GET

#### 请求参数

| 名称 | 类型 | 必填 | 描述 | 示例值 |
| ---- | ---- | ---- | ---- | ------ |
| projectId | string | 是 | 项目ID | 可以在项目概览中查看项目ID，如：WlG**Daj |
| file_type | string | 是 | 文件类型 | 文件类型:event,user_id,user_props,user_segments,user_tags |
| file_create_date | string | 是 | 文件类型 | 文件生成日期：格式yyyy-MM-dd，如：2023-01-01|

> 提示：项目 ID 从项目概览中获取

#### 返回数据

| 名称 | 类型   | 描述     |
| ---- | ------ | -------- |
| path   | string |  文件路径  |
| fileList | Array | 文件清单，清单元素内容为文件名称 |

 #### 成功示例

curl请求

 ```
 curl -X 'GET' \
  'http://uat-uba.growingio.cn/v1/api/{projectID}/data_export/2023-08-20/user_id' \
  -H 'accept: application/json'
 ```
返回码： 200 

```
[
  {
    "path": "/id_$anonymous_user",
    "fileList": [
      "id_$anonymous_user.csv.gz"
    ]
  },
  {
    "path": "/id_$basic_userId",
    "fileList": [
      "id_$basic_userId.csv.gz"
    ]
  },
  {
    "path": "/id_loginUserKey",
    "fileList": [
      "id_loginUserKey.csv.gz"
    ]
  },
  {
    "path": "/id_sdfwefw",
    "fileList": [
      "id_sdfwefw.csv.gz"
    ]
  },
  {
    "path": "/id_test4",
    "fileList": [
      "id_test4.csv.gz"
    ]
  }
]
```

### 下载文件 API 

#### 接口地址

```
http://{api-host}/v1/api/projects/{projectId}/data_export/{file_create_date}/{file_type}/downloadFile
```

#### 请求方式

    GET

#### 请求参数

| 名称 | 类型 | 必填 | 描述 | 示例值 |
| ---- | ---- | ---- | ---- | ------ |
| projectId | string | 是 | 项目ID | 可以在项目概览中查看项目ID，如：WlG**Daj |
| file_type | string | 是 | 文件类型 | 文件类型:event,user_id,user_props,user_segments,user_tags |
| file_create_date | string | 是 | 文件类型 | 文件生成日期：格式yyyy-MM-dd，如：2023-01-01|
| file_name | string | 是 | 文件名称 | 从查询文件清单API 返回 fileList 内容中获取|
| file_path | string | 否 | 文件地址 | 从查询文件清单API 返回 path值 |

> 提示 项目 ID 从项目概览中获取

#### 返回数据

| 名称 | 类型   | 描述     |
| ---- | ------ | -------- |
| path   | string |  文件路径  |
| fileList | Array | 文件清单 |

 #### 成功示例

curl请求

```
 curl -X 'GET' \
  'http://uat-uba.growingio.cn/v1/api/projects/Wl**4Daj/data_export/2023-08-20/user_id/downloadFile?file_name=id_%24anonymous_user.csv.gz&file_path=%2Fid_%24anonymous_user' \
  -H 'accept: application/octet-stream'
```

返回 200 
```
Response body
 Download file
```


### 数据详情

下载后事件明细和用户属性的格式示例：

#### 示例 1：事件明细数据

下载文件成功并解压后：part-00000-0c57c7a1-4d4c-4b49-ba40-045b802dd6cb-c000.csv

![picture 1](/img/9a36043772d0349768c10f3dde4f715d4325f10146d26cb9fe40ea6365bc1ede_pic_1639970518912_2021-12-20.png)

数据字段的分隔符是\t，空字符串为英文双引号包裹。各字段的含义见附录。

#### 示例 2：用户属性数据

下载文件成功并解压后：part-00000-39d0854c-6e9b-42cc-a06a-a419975911f7-c000.csv

文件格式：

![picture 1](/img/ab0a84dc99045edaacf9d609f1051c695ba5757fa38e62386f2272be7dae55a9_pic_1639970681349_2021-12-20.png)

数据字段的分隔符是\t，空字符串为英文双引号包裹

## 常见问题

Q：事件明细是否有历史数据一次性导出的方案？
A：由于事件明细的每日例行定时导出任务是导出 T+1 的数据，因此在开启离线数据导出能力后，可以每日下载前一日的事件数据。若需要将历史数据一次性导出，请联系 GrowingIO 项目经理获得支持。
Q：下载压缩文件前，如何知道文件是完整的？
A：请求获取文件 API，返回结果不为空，说明文件已生成完整。
Q：不同类型的文件的切割规则（即 fileList字段文件数）是怎样的？
A：event类型：文件数=当日总事件量 / 500w ；其他类型：文件数固定为 1。

## 附录：事件明细文件的字段详情

| 序号 | 字段                | 含义                                               | 备注                                                                       |
| ---- | ------------------- | -------------------------------------------------- | -------------------------------------------------------------------------- |
| 1    | event_key           | 事件标识                                           | visit 事件$visit、访问事件$page、自定义事件如 paySuccess                   |
| 2    | event_time          | 事件接收时间                                       | 示例：2021-06-01 23:59:20.912                                              |
| 3    | event_id            | 事件 ID                                            | 事件内容 hash 后的长度为 32 位的字符串，也支持导入数据中自定义 event_id 值 |
| 4    | event_type          | 事件类型                                           | visit, page, custom_event 类型                                             |
| 5    | client_time         | 事件采集时间                                       | 示例：2021-06-01 23:59:20.912                                              |
| 6    | anonymous_user      | 访问用户 ID                                        |                                                                            |
| 7    | user                | 登录用户 ID                                        |                                                                            |
| 8    | user_key            | 用户身份                                           | 访问状态：$anonymous_user；登录状态：$basic_userId；自定义身份：自定义值   |
| 9    | gio_id              | 用户编号                                           | GrowingIO id-service 服务给用户生成的唯一编号                              |
| 10   | session             | 会话标识                                           |                                                                            |
| 11   | attributes          | 事件属性                                           | 事件属性的 KV 值                                                           |
| 12   | $package            | 包名                                               |                                                                            |
| 13   | $platform           | 平台标识                                           | Web                                                                        |
| 14   | $referrer_domain    | 来源域名或包名                                     |                                                                            |
| 15   | $utm_source         | 广告来源，标识投放的网站                           |                                                                            |
| 16   | $utm_medium         | 广告媒介或营销媒介                                 |                                                                            |
| 17   | $utm_campaign       | 广告名称，产品的具体广告系列名称、标语、促销代码等 |                                                                            |
| 18   | $utm_term           | 广告关键字，标识付费搜索关键字                     |                                                                            |
| 19   | $utm_content        | 广告内容，用于区分相似内容或同一广告内的链接。     |                                                                            |
| 20   | $ads_id             | 广告 ID                                            |                                                                            |
| 21   | $key_word           | 访问来源广告关键字（通用维度）                     |                                                                            |
| 22   | $country_code       | 国家码                                             | 示例：CN                                                                   |
| 23   | $country_name       | 国家名称                                           | 示例：中国                                                                 |
| 24   | $region             | 省份                                               | 示例：江苏                                                                 |
| 25   | $city               | 城市                                               | 示例：南京                                                                 |
| 26   | $browser            | 浏览器名称                                         |                                                                            |
| 27   | $browser_version    | 浏览器版本                                         |                                                                            |
| 28   | $os                 | 操作系统名称                                       |                                                                            |
| 29   | $os_version         | 操作系统版本                                       |                                                                            |
| 30   | $client_version     | 客户端版本，移动端存在                             |                                                                            |
| 31   | $channel            | 客户端渠道来源                                     |                                                                            |
| 32   | $device_brand       | 设备品牌名称                                       |                                                                            |
| 33   | $device_model       | 设备型号                                           |                                                                            |
| 34   | $device_type        | 设备类型                                           | 0：平板 1：手机                                                            |
| 35   | $device_orientation | 设备方向                                           |                                                                            |
| 36   | $resolution         | 屏幕尺寸                                           |                                                                            |
| 37   | $language           | 语言                                               | 示例：zh-cn                                                                |
| 38   | $referrer_type      | 来源类型                                           |                                                                            |
| 39   | account_id          | GrowingIO 的 AI 值                                 |                                                                            |
| 40   | $domain             | 域名或包名                                         |                                                                            |
| 41   | $ip                 | 客户端 IP 地址                                     |                                                                            |
| 42   | $user_agent         | 浏览器 agent 详细信息                              |                                                                            |
| 43   | $sdk_version        | SDK 版本号                                         |                                                                            |
| 44   | $data_source_id     | 数据源 ID                                          |                                                                            |
