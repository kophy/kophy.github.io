---
title: 关于不用AWS的我去了考AWS证书这件事
date: 2020-07-18 17:23:55
mathjax: true
tags:
- 编程
- 架构
- AWS
---

时隔两周的生存确认，今日もかわいい。
这周五考了AWS最基本的证书Cloud Practitioner，这篇比起Kaggle那次正经的总结，倒不如说是色々な吐槽合集。

<!-- more -->

会去考这个证书除了新冠在家待到自闭之外，今年读了很多system design论文后想找方法实践学到的理念，但自己造轮子需要写很多代码的话很麻烦~~身为程序员的问题发言~~。考虑到业界很多公司会用云而不是自己的infrastructure，那学习怎么用各种cloud services作为积木，搭建要考虑availability/consistency/scalability/...种种需求的应用就是一举多得的练习。

AWS和GCP都有自己的证书系列，而GCP是我工作的技术栈之一，没选择GCP主要是因为AWS一项考试100刀，GCP一项考试200刀，所以花同样的钱可以考两张AWS证书~~（比起吐槽役已经是在装傻了）~~。最开始想考的是Solutions Architect Associate，顾名思义更像是云服务架构师，但是我过去基本没用过AWS，还是一步个一脚印先获得些正反馈毕竟好。

Cloud Practitioner虽然是最基本的证书，但也不是毫无准备就能通过的（官方推荐是6个月经验）。我是读了两遍AWS Certified Cloud Practitioner Study Guide，一遍粗读一遍结合练习题精读。备考的话还是推荐看些书，倒不是做题家思维，而是有些重要知识点作为开发者基本是不会碰到的。举个例子，dedicated host指的的是可以指定一台AWS物理服务器专门用来跑你的EC2，如果应用授权是per-server license的话，就必须用dedicated host。这个知识点当然很重要——实际用到的时不知道的话会很麻烦，但感觉相当多的个人/团队根本不会遇到（查了一下主要例子是Microsoft SQL Server系列）。另一方面，有些考点就是要背，比如某个support plan能做什么（仿佛是培养推销员）。

其实比较“硬”的技术知识我大多是靠GCP经验类比和之前读的理论知识，比如GCS对S3，比如Dynamo的数据模型，准备这个证书对我最大的收获是对AWS的整体认识和具体名词，现在看Solutions Architect Associate的场景就明白在说些什么了——之前的感想是“Glacier是什么？Storage Gateway又是什么？”。

需要承认的是AWS的storytelling能力是真的很强，[The 5 Pillars of the AWS Well-Architected Framework](https://aws.amazon.com/blogs/apn/the-5-pillars-of-the-aws-well-architected-framework/)里没有一条是传统意义上的技术问题：

- Operational Excellence
- Security
- Reliability
- Performance Efficiency
- Cost Optimization

毕业后不知不觉在在湾区工作了两年，就算跳槽也不算是new grad了。之前晚上失眠的时候发现自己难以回忆起2019年的很多细节，但更早的记忆倒很清楚。去年也不算在自暴自弃，只是规划和总结都做得太少了。要纠结自己有没有成为更好的人的话，还是需要经常记录「此刻」自己是个怎样的人。