---
id: dc-download-user-tag-users
sidebar_position: 9
---

# 客户数据平台-用户标签用户列表下载

## 接口说明

下载客户数据平台指定用户标签覆盖用户的用户特征

## 接口地址

```
http://{api-host}/v1/api/user_tags/{tag_key}/users/export_jobs
```

## 请求方式

POST

## 公共请求参数

[公共请求参数](../../open-api#公共请求参数)

## 请求参数

| 名称      | 类型   | 必填 | 描述                 | 示例值        |
| --------- | ------ | ---- | -------------------- | ------------- |
| tag_key | String | 是   | 用户标签标识符 | tag_rfm |

## 请求参数

| 名称      | 类型   | 必填 | 描述                 | 示例值        |
| --------- | ------ | ---- | -------------------- | ------------- |
| properties | List | 否 | 查询的用户身份、用户属性、用户标签<br></br>最大查询60个，超过上限后查询失败 | id_$basic_userId |

## 返回数据

文件名称：{标签名称}_{下载日期}_UserList

文件格式：csv

数据格式：

| 名称            | 类型      | 描述                             |
| --------------- | --------- | -------------------------------- |
| gio_id | Int | GrowingIO 系统生成的用户标示 |
| {properties} | String | 用户自定义查询的下载列 |

## 示例 1：下载用户标签覆盖用户列表，并输入用户身份、用户属性、用户标签

场景：下载 用户标签 **tag_rfm** 的用户ID、性别、RFM标签

### 提交下载请求

```bash
curl --location --request POST 'http://{api-host}/v1/api/user_tags/tag_rfm/export_jobs' \
--header 'Authorization: Bearer 4aaa22c7-679f-49be-b97d-073dad5dfc15' \
--header 'Content-Type: application/json' \
--data-raw '{
    "properties": [
        "ids_$basic_userId",
        "usr_gender",
        "tag_rfm"
    ]
}'
```
### 返回下载任务信息

```json
{
    "id": "kqQeWeGr",           // 下载任务ID
    "name": "DES-202205240136-5818534160000"
}
```

### 获取下载地址

```bash
curl --location --request GET 'http://{api-host}/v1/api/job/result/kqQeWeGr' \
--header 'Authorization: Bearer 4aaa22c7-679f-49be-b97d-073dad5dfc15'
```

### 返回下载地址

```json
{
    "stage": "FINISH",
    "uris": [
        "%2Fjobs%2Fresults%2FDES-202205240136-5818534160000%2Fzxm_%E7%94%A8%E6%88%B7_%E5%AD%97%E7%AC%A6%E4%B8%B2_%E5%8A%A0%E5%AF%86_2022-04-26_UserList.csv"   // 下载地址
    ]
}
```

### 下载文件

下载地址："http://{api-host}/download?file=" + {下载地址}

文件格式：

```csv
“gio_id","d_$basic_userId","usr_gender","tag_rfm"
"603542","C001","男”,
"605419","C004",,"低"
...
```

## 示例 2：下载条件未输入用户身份、用户属性、用户标签

场景：下载 用户标签 **tag_rfm**

### 提交下载请求

```bash
curl --location --request POST 'http://{api-host}/v1/api/user_tags/tag_rfm/export_jobs' \
--header 'Authorization: Bearer 4aaa22c7-679f-49be-b97d-073dad5dfc15' \
--header 'Content-Type: application/json' \
--data-raw '{
    "properties": []
}'
```
### 返回下载任务信息

```json
{
    "id": "kqQeWeGr",           // 下载任务ID
    "name": "DES-202205240136-5818534160000"
}
```

### 获取下载地址

```bash
curl --location --request GET 'http://{api-host}/v1/api/job/result/kqQeWeGr' \
--header 'Authorization: Bearer 4aaa22c7-679f-49be-b97d-073dad5dfc15'
```

### 返回下载地址

```json
{
    "stage": "FINISH",
    "uris": [
        "%2Fjobs%2Fresults%2FDES-202205240136-5818534160000%2Fzxm_%E7%94%A8%E6%88%B7_%E5%AD%97%E7%AC%A6%E4%B8%B2_%E5%8A%A0%E5%AF%86_2022-04-26_UserList.csv"   // 下载地址
    ]
}
```

### 下载文件

下载地址："http://{api-host}/download?file=" + {下载地址}

文件格式：

```csv
“gio_id"
"603542"
"605419"
...
```