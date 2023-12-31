---
id: autotrackevent-management
sidebar_position: 1
---

# 无埋点事件

## 简介[](#jian-jie)

无埋点事件是对使用无埋点能力采集的用户行为的定义，包含名称、标识符、事件类型、事件属性、描述。无埋点事件需要关联圈选规则才能正常采集用户行为。

## 名词解释[](#ming-ci-jie-shi)

| 信息 | 说明 |
| --- | ---- |
| 名称 | 事件在使用过程中的显示名。 |
| 标识符 | 事件在系统内的唯一标识符。<br></br>注：仅允许大小写英文、数字、下划线，并且不能以数字开头， 最大长度支持 100 字符。 |
| 事件类型  | 页面浏览、元素点击、元素修改 |                                                                                     |
| 描述 | 事件的描述，可填写事件的触发时机和应用场景。                                                                        |
| 关联事件属性 | 该事件需要采集的具体信息。<br></br>注：所需属性需要先添加为预置事件$page中的事件属性，才能选择。                                   |

## 功能边界或约束[](#gong-neng-bian-jie-huo-yue-shu)

### 重复性约束[](#zhong-fu-xing-yue-shu)

* 事件的名称和标识符均不可重复，包含埋点事件、虚拟事件
* 某一事件类型的无埋点事件只能添加对应类型的圈选规则
* 可添加的事件属性，必须先关联至预置事件$page中

## 功能说明[](#gong-neng-shuo-ming)

### 新增

通过定义名称、标识符、事件类型、描述、关联事件属性来完成一条新的无埋点事件的定义。

:::caution

“关联事件属性”可选范围：$page关联的事件属性。

“关联事件属性”可回溯范围：除了受回溯天数的限制，同时受该事件属性何时关联至$page影响。

举例：

系统默认7天回溯事件。

用户操作如下：

1. 在2月10日官网集成无埋点sdk。
2. 在3月3日事件属性“productId”添加至$page
3. 在3月9日创建无埋点事件“浏览商品详情页”，并关联事件属性“productId”。
4. 在3月9日创建圈选规则“商品详情页_官网_v4.0”，并关联至无埋点事件“浏览商品详情页”

以上操作结果：
- 埋点事件“浏览商品详情页”在3月2日开始有统计数据。
- 使用“productId”拆解时，从3月3日开始有数据。

:::

![图 0](/img/chuangjian_autotrackevent-management.png)  

### 查看

* 已创建的事件默认按照创建时间逆序排列
* 支持翻页查看
* 支持通过名称或标识符检索来查找已定义的事件。
* 支持通过关联圈选规则的数据源查找已定义的事件。

![图 1](/img/shijianliebiao_autotrackevent-management.png)  

点击某事件行，可查看事件定义详情，包含基本信息、关联规则、其他信息。

![图 2](/img/xiangqing_autotrackevent-management.png)  

### 编辑[](#xiu-gai)

点击某事件行，在事件详情中，编辑事件信息后保存。标识符、事件类型不支持修改。

![图 3](/img/bianji_autotrackevent-management.png)  

### 删除[](#shan-chu)

点击某事件行的操作列的图标，可删除单个事件。也可以在列表中使用复选框选择多个事件，进行批量删除。

事件被删除后不可恢复，引用它的看板图表将受到影响，请谨慎操作。

### 无埋点事件关联圈选规则

![图 5](/img/guanlianguize_autotrackevent-management.png)  

#### 查看规则详情

规则详情包含规则定义、过去7天规则匹配事件的趋势图、圈选截图。

![图 4](/img/guizexiangqing_autotrackevent-management.png)  

#### 解除关联

解除后，该规则过去及未来数据，不计入该无埋点事件

#### 下线规则

下线规则是对圈选规则的管理。一般在产品迭代后，该规则失效时，可下线规则，规则下线后

* 历史数据不受影响，可继续使用
* 下线后，不再产生新数据
* 该规则关联的其他无埋点事件, 同时受到影响

#### 上线规则

上线规则是对圈选规则的管理。若由于错误操作规则下线，可以重新上线规则，使规则生效，继续生产匹配的用户行为数据，计入无埋点事件。

![图 7](/img/shangxianguize_autotrackevent-management.png)  


### 新建圈选规则

圈选规则是对无埋点事件所代表的用户行为何时发生的描述，包含名称、数据源、规则类型、规则定义要素、描述。维护关联圈选规则的正确性，才能确保无埋点事件数据的准确性。

圈选规则一共有三种类型的圈选规则，分别为页面浏览、元素点击、元素修改，分别与无埋点事件的事件类型对应。

目前仅支持Web可视化圈选规则。

![图 6](/img/kaishiquanxuan_autotrackevent-management.png)  




