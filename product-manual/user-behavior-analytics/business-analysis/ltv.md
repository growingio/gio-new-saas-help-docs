---
id: ltv
sidebar_position: 2
---

# LTV 分析

## 简介[](#jian-jie)

LTV 作为一种通用模型，衡量的是特定时期的特定用户群体的生命周期价值，即：Life Time Value，是产品能否取得利润的重要参考指标，在日常运营、广告变现等场景中都会涉及。
现有的分析工具，例如留存分析，更多的是聚焦用户行为的分析，缺少用户对于实际营收贡献的分析，而 LTV 正是解决这类问题的分析工具。

## 名词解释[](#ming-ci-jie-shi)

LTV：在本分析工具中，指的是某日的人均 LTV。LTVn = 该日指定条件的新增用户在随后 n 天内花费的金额/该日指定条件的新增用户
初始事件：用来确定 LTV0 的人群和日期。
营收事件：包含数值型属性的事件，用来计算累计数值。

## 功能说明[](#gong-neng-shuo-ming)

### LTV 的计算示例

场景说明：

计算 1 月 1 日注册的新用户，在 30 天后的人均购物金额（LTV30）

计算方法：

- 计算基准计算基准时间、事件、人群:

  - 选择日期：1 月 1 日~1 月 31 日
  - 选择事件：注册事件
  - 新用户范围：1 月 1 日触发注册事件的新用户群 A

- 统计该用户群体从 1 月 1 日到 1 月 30 日的全部购物金额累计值 B
  - LTV30=B/A

### 选择起始事件

选择任意事件或者埋点事件，作为计算基准人群的标准。

![图 1](/img/d3c7ed16e0febe7a2d32920556b1897e9fc7e9594cbe143a4c58ed1e9f80bfe7_pic_1677208511101_2023-02-24.png)

### 选择营收事件

选择有数值类型属性的事件，用于计算累计营收贡献值，例如可以选择下单事件的下单金额属性。可以选择多个营收事件，计算时会合并计算。<br/>

![图 8](/img/4a9c46948c1885eed4b8532c58acb4fc8c946d6eef2a1cb0a200242de5178c4e.png)

### 选择目标用户、日期范围等

和其他分析工具类似，可以选择需要分析的用户群、过滤属性、选择分析事件范围

![图 9](/img/0fa0e1a3fb0e7385393c00499f93426f95c98210b5d6e670ba31730dc37191bc.png)

### 查看 LTV 折线图和表格

通过以上条件的选择，可以在折线图和表格里查看 LTV0~LTV7，LTV15，LTV30，LTV60，LTV90 的数据。

![图 1](/img/34efbbcbf2cde0c9c68311bc163c164aa40513fdd2c84439cde337e05b970294_pic_1685412671492_2023-05-30.png)  

