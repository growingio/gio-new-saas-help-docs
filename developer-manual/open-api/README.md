---
id: open-api-overview
sidebar_position: 1
---

# Open API 概述

## 公共请求参数

公共请求参数是指每个接口都需要使用到的请求参数。如下表所示的参数均放在HTTP请求的头部。
| 参数 | 类型 | 说明 |
| --- | --- | --- |
| Authorization | string | 接口请求所需的认证码，即Token，您可以在GrowingIO平台的[个人设置](../../../../product-manual/personal)中获取一个长期有效的Token。|
| language | string | 语言，默认CH。可选：CH - 中文，US - 英文。 |


## 企业功能接口
| OpenAPI名称 | 描述 | 操作 |
| --- | --- | --- |
| 平台成员列表 | 查询平台所有成员列表 | [查看文档](./enterprise-api/platform-users) |
| 平台成员详情 | 查询平台某成员详情信息 | [查看文档](./enterprise-api/platform-user) |
| 平台角色列表 | 查询平台所有角色列表 | [查看文档](./enterprise-api/platform-roles) |
| 平台部门列表 | 查询平台所有部门列表 | [查看文档](./enterprise-api/platform-departments) |
| 项目列表 | 查询平台所有项目列表 | [查看文档](./enterprise-api/projects) |
| 项目详情 | 查询某项目的详情信息 | [查看文档](./enterprise-api/project) |
| 项目角色列表 | 查询某项目的所有角色列表 | [查看文档](./enterprise-api/project-roles) |
| 项目角色详情 | 查询某项目角色的详情信息 | [查看文档](./enterprise-api/project-role) |
| 项目成员列表 | 查询某项目的所有成员列表 | [查看文档](./enterprise-api/project-users) |
| 项目成员详情 | 查询项目成员的详情信息 | [查看文档](./enterprise-api/project-user) |
| 添加项目成员 | 添加平台成员到某项目 | [查看文档](./enterprise-api/project-user-add) |
| 修改项目成员角色 | 修改项目某成员的角色信息 | [查看文档](./enterprise-api/project-user-role-upt) |
| 删除项目成员 | 删除项目中的某成员 | [查看文档](./enterprise-api/project-user-del) |