---
title: Lambda 体系架构
date: 2019-12-23 10:16:27
categories: 
           - Bigdata
tags:
           - Lambda
---
使用 Lambda 体系结构可对大型数据集进行高效的数据处理。 Lambda 体系结构使用批处理、流式处理和服务层，将查询大数据时存在的延迟降到最低。

什么是 lambda 体系结构？
lambda 体系结构是一种通用、可缩放且容错的数据处理体系结构，可以解决批处理和速度延迟方案。
源： http://lambda-architecture.net/

![](http://ningyylin.top/image/bigdata/la-overview_small.png)


所有数据同时推送到批处理层和速度层。
1. 批处理层包含主数据集（不可变、仅限追加的原始数据集），并预先计算批处理视图。
2. 服务层包含快速查询的批处理视图。
3. 速度层补偿处理时间（针对服务层），只处理最新的数据。
4. 通过合并批处理视图和实时视图中的结果或者单独 ping 每个结果，可以应答所有查询。