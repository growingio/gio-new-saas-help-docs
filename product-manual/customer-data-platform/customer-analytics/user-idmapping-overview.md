---
id: user-idmapping-overview
sidebar_position: 1
---

# 融合分析

## 简介[](#jian-jie)

用户多身份融合结果的概览

![picture 1](/img/9559c1cc743d2fceff7fd16cf6746543673b78b0f709c079d6a33d36b0351f01_pic_1683741548876_2023-05-11.png)  


## 融合概览

融合概览中的指标定义

- 总用户量：融合后用户的总量，若用户A被合并到用户B，A用户失效后，A将不会被统计
- 强身份用户量：用户身份中被定义为“唯一身份ID”的身份下的用户量，若某弱身份用户未被强身份融合，则该弱身份用户不会被统计
- 合并用户量：发生用户身份融合的用户量，若用户A合并到用户B，用户B又进一步合并到用户C，此时A和B被计入合并用户量

## 图表看板

图表看板中预置的图表

- 按用户身份统计用户量：统计每个身份下的用户量
- 每日新增用户量：每日新增OneID的数量
- 每日合并用户量：按照用户发生融合的日期统计每日合并用户量