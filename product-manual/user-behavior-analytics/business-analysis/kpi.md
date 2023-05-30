---
id: kpi
sidebar_position: 1
---

# KPI 分析

## 简介

KPI 分析可以帮助业务负责人在 GrowingIO 平台上监控 KPI 数据，判断 KPI 是否符合预期。若数据与预期不符，用户可以借助维度拆解和下钻，迅速找到影响 KPI 表现的原因。

功能包括：

- 趋势对比：指标趋势，以及时间范围内的同环比计算；
- 维度拆解：基于不同维度的拆解，如根据维度拆解变化量和变化率指标；
- 维度下钻：支持基于不同维度的下钻分析；
- 变化洞察：支持 KPI 波动主要影响因子的洞察分析。

## 名词解释

KPI（Key Performance Indicator）即关键绩效指标，是企业内关键业务表现的衡量方式。在 GrowingIO 增长平台内，常把 “用户量“，“销售额“ ，“购买转化率“ 等用户、业绩相关的核心指标应用在 KPI 分析中进行监控和分析。

## 功能边界和约束

支持埋点事件、虚拟事件、预定义指标、自定义指标的分析，不支持无埋点事件。

## 功能说明

### 创建 KPI 分析

1. 在导航栏选择“**分析模型 > KPI分析**"，进入 KPI 分析新建页面。

 ![图 1](/img/45e860e0d89083b7b470779e8b37a7e3ce37fd0f2d237fdb65743f7206c254fe.png)  


2. 在新建页面，您可以做如下配置：

![图 56](/img/9613fc4e2cba7c88017d46f3e635565d16def11a581bd9f790a2210036a0e109.png)  

| 参数               | 说明                                                                                                                                                                                                                                                                                                                                                    |
|--------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 1-KPI指标          | 选择KPI指标。提供2种选择方式：<br/>1. 选择事件：KPI 由事件、事件的度量方式（人、次、人均）和过滤条件构成，以下指标都可以是 KPI：购买人数、购买次数、平均购买次数、购买金额、手机购买量等。他可以借助事件 “购买“，“购买”事件的度量方式 人、次、人均，事件的变量：金额、品类等组合构成。<br/>2. 选择指标：直接选择已经定义好的预置指标或自定义指标作为KPI |
| 2-目标用户         | 设置目标人群，以便了解特殊人群的KPI表现，如重新购买、新注册等。                                                                                                                                                                                                                                                                                         |
| 3-期望达到的目标值 | 选填项，如果您希望监控KPI在固定时间范围下的目标完成情况，可以配置对应目标值。                                                                                                                                                                                                                                                                           |
| 4-时间范围         | 可选择今天、本周、本月等时间段来监控KPI指标。若您选择今天，可以看到今天的小时级别数据，如果您对某一个指标的关注度是每小时都会看一看，或者每半天都会看一下，建议选择今天。                                                                                                                                                                               |
| 5-时间粒度         | 可选择按小时、天、周或月来查看指标                                                                                                                                                                                                                                                                                                                      |

3. 填写完成后单击**保存**，完成一个 KPI 分析的创建。

4. 您可以把已保存的KPI 分析添加到看板，展示效果如下图：

![添加 KPI 分析图表到看板](/img/17c8ec9107ac3bdc98430d5add02eb45afeed1fa12d810cd8ce7ec83a219e6c1_pic_1639995351993_2021-12-20.png)

### 监控 KPI 表现

将 KPI 分析添加到看板后，可持续监控 KPI 指标的表现，监控内容包括：KPI 指标的数值、趋势、同环比变化率、目标完成率情况。

![图 57](/img/a856d81eb5e8b8cb7783b6bc289706c19447702a5d688c71ac8eec0321479ad0.png)  


一个 KPI 分析卡片包含以下6个元素：

| 元素       | 说明                                                                                                                                                               |
|------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 标题       | 我们默认用了事件名称来指代标题，您可以在 KPI 分析详情页修改标题。建议标题设置一定要简单明了，所有人看到标题后就能明白它的业务含义。                                |
| 时间范围   | 考察 KPI 的时间范围，一般情况下公司用今天、本周、本月来看 KPI 的表现。在详情页编辑时您可以更灵活地选择时间。                                                       |
| 同比       | 同比是一个业务概念，是基于业务周期的定义。对比规则：本周比上周、本月比上月、今年比去年。如果今天是周三，那么本周比上周就是本周一至周三的数据比上周一至周三的数据。 |
| 环比       | 定义为这个N天比上个N天。比如：今天比昨天，过去7天的数据比过去 8~14 天数据，环比更关注业务的连续性。                                                                |
| 目标       | 给予所选时间范围和粒度的目标。比如本周目标、本月目标等。对于所选时间范围和粒度的 KPI 您可以设定对应的目标。注：当所选时间范围发生变化时，目标需要重新填写。        |
| 目标完成率 | 实际 KPI 表现/目标值，您可以借助目标完成率来追踪进程是否符合预期。                                                                                                 |

### 分析 KPI 波动

当您发现 KPI 表现不符合预期时，点击 KPI 卡片进入 KPI 详情页，详情页将帮助您快速定位数据波动的原因。

![分析 KPI 波动](/img/5e58e6ddb0f8c8abc3b0bbffd3334996f8a50090b77fb8426b48c097f2a32be2_pic_1642497988812_2022-01-18.png)  

您可以做以下操作来定位波动原因：

| 项         | 说明                                                                                                         |
|------------|--------------------------------------------------------------------------------------------------------------|
| 1-趋势图   | 趋势线图，帮助您监测 KPI 趋势与波动状况。                                                                    |
| 2-洞察     | 基于您关注的业务维度，直接呈现 KPI 变化的主要影响因子。快速理解导致数据波动的核心原因。                      |
| 3-维度拆解 | 您可以按照业务维度对您的 KPI 进行拆解，找到 KPI 变化的影响因子。表格提供不同业务维度下的数据变化量与变化率。<br/>您可添加多个维度，并将常用的维度保存下来，便于后续分析使用。|
| 4-维度下钻 | 单击维度列单元格可以对维度进行下钻。可以根据您的业务思路，不断拆解下钻找到最小粒度的原因。                   |