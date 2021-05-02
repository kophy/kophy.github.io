---
title: 2021/01月记
date: 2021-01-03 21:08:35
mathjax: true
tags:
	- 杂谈
---

新年新气象，今年打算把过去也~~偶尔~~会写的每月记录写得正式一点。
本来打算把每个月里遇到的、有趣的关键词组合起来，变成中二的标题，但20后半的人还是不玩这套了。

<!-- more -->

主力项目黄了后，这个月主要是在调整和探索——转到组里别的项目，面试外面的公司检验水平，读书，打游戏，炒股，看房，和各种各样的人聊天——算是调整和探索中，目前看来还得持续一段时间。

## 面试

这个月实打实地面试了两家公司，Lyft和Pure Storage，算上前期联系/面试后续的话大约在跟6、7家公司打交道。有几家公司HR拖延我也没刻意去催，毕竟onsite一场4-5个小时是真的非常消耗体力的。

NDA的关系不便公开写面试题，不过想分享些不负责任的思考（请注意New Grad/社招标准不同，我面试时是逛街心态没有压力，而且样本太少）：
- 算法和设计题都比预想中简单。回想起来我做面试官，以及合作过的面试官都没有用过太难的题目（太难得花时间准备，而且easy的括号匹配都能筛掉一大批人），现在LeetCode的数量和难度陡增是不有点和真实的面试情况脱节？
- 就像算法题考察的不是candidate掌握了多高级的算法，而是通用的解决问题能力和编程思维（分析问题中模糊的部分，合理的抽象、代码风格、etc），系统设计考察得也是更基本的知识积累。
  - > 和面试官的精彩对话（context是我说可以用zookeeper实现service discovery）：
    > 面试官："我问得这么细，就是想确实你是真的理解，因为有的人只是背了几个名词。"
    > 我："我只知道zookeeper的原理，从来没实际用过。"
    > 面试官："其实我也没用过zookeeper。"
    > ......
    > ~~什么叫菜鸡互啄啊~~
- Amazon的BQ（behavior question）可以说是BQ界的顶点，准备的段子够应对14条军规的话，基本临场稍微改变就可以搞定别家问题了。
- 之前近一年没写算法题花了很长时间复建，所以平时还是保持刷题的状态比较好。
- 最后问面试官问题的环节，没有心理压力的话就能问得很放纵——甚至包括与竞争对手的对比。
  - 我几乎每个人都问了有没有对公司最喜欢和最讨厌的地方。算上被我套话套出的内容，员工最讨厌的地方各色各样（包括工作有很多失败的尝试，福利不好，与客户打交道，technical debt重，等等），但最喜欢的地方几乎都可以总结为公司文化。
  - 有些面试官自称为technical guy，认为当前职场环境最好的地方是能让自己专注技术。几年前我大约会认可，现在看反而是red flag。对技术的推崇不应该成为程序员的information cacoon。

后面有两尊boss想要挑战一下，之后就要专心做别的事情了。

## 论文

**Azure Data Lake Store**
算是Microsoft论文第一篇。ADLS是Microsoft为了兼容原本的Cosmos和Hadoop开发的新data lake。原文虽然称之为文件系统，但结合Snowflake的multi-cluster，shared-data architecture会比较容易理解所谓的集群local和remote storage，都是为了分离存储和计算从而scale independently（反例：Redshift的compute node要存储所有数据）。

文章最大的亮点是因为采用了microservice架构，为了方便开发者维护replicated services之间的consistent state，团队结合Paxos和Hekaton（Microsoft's in-memory database）实现了自己的RSL-HK框架，这样用SQL语言就能操作多机器间的consistent state了。当然缺点也很明显…毕竟scalability是SQL的原罪，只能拆成多个partition table存在不同的Paxos ring里（对比：Snowflake采用了一个global key-value database）。

**Delta Lake**

Delta Lake是Databricks开源的所谓"lakehouse"（standard DBMS functions usable directly against low-cost object stores，开发者真喜欢造词）。基本上cloud object storage都存在问题(1) eventual consistency和 (2) metadata操作非常昂贵（比如有大量的小文件，AWS一次`LIST`只能返回1000个的话，就得反复调用`LIST`）。Delta Lake就是通过自己的protocol，在cloud object storage上实现了一个ACID transaction层，解决eventual consistency和需要`LIST`大量文件的速度问题。

简单地讲，Delta Lake就是在cloud object storage里维护了一份伪WAL log并定期用checkpoint压缩；每个写操作生成有unique id的log entry。用户在读时通过合成checkpoint和之后的WAL log得到要操作的文件名和pruning所需的统计信息；写的时候通过乐观并发控制抢unique id。总之都是经典数据库技术。

**Differential Privacy: A Primer for a Non-technical Audience**

工作中遇到隐私相关问题，所以娱乐性质地读一读。这篇重在解释传统隐私保护技术（如k-anonymity）的缺点，以及新工业界标准differential privacy的核心思想——通过引入噪声等方法，使得数据集中任何一用户参与与否，对于分析结果的影响都非常小。虽然没有太硬核的技术，但结合例子清楚解释了privacy parameter $\epsilon$、差分隐私能做到与不能做到的、privacy as a budget等基本概念，值得一读。

---
月中机缘巧合和一个现在Google做BigQuery，之前在Microsoft做Azure Data Lake的前辈聊天，对方挺震惊于我的了解程度，读点别家公司的东西唬人真好用啊:D

## 读书

本月读完了三本书，《从0到1》，《鳗鱼的旅行》和《仿制药的真相》（被朋友吐槽为什么是豆瓣热门书，当然是因为Amazon上打折啊），进度中~~不确定会不会读完~~的书还有好几本。

**从0到1** 
Peter Thiel关于创新、关于技术、关于商业的启示录。事物的发展有两个维度，垂直（技术创新，从0到1）和水平（全球化，从1到N）。在2000年互联网泡沫后人们变「怂」了，更想在水平维度重复经验，而不愿在垂直维度的爆炸性技术投入资源。用Peter的话说就是：

> “We wanted flying cars, instead we got 140 characters.”

但重复经验是有极限的（比如以现在的资源使用方式无法让全世界人过上美国人的生活），未来注定与现在不同，或者说我们想进入未来，就必须思考和创造与现在不同的东西。最成功的、实质上形成了垄断的企业是基于「秘密」建立的；只要觉得世界上不是处处完美，那就说明还有秘密等待被发现。

**鳗鱼的旅行**
奇数章是对鳗鱼的科普夹杂从科学到文学的杂谈，偶数章是与父亲关于鳗鱼的回忆。虽然大部分人对鳗鱼的印象停留在鳗鱼饭，但了解其生命周期后一定会觉得这种生物很神奇。诞生于马尾藻海，随洋流几年后到达欧洲，在淡水系中生存数年到数十年不等的时间，某日响应上天号召般，游回诞生的马尾藻海繁殖后死去——整个欧洲的鳗鱼都汇集在马尾藻海的画面，想想都觉得震撼。时至今日，鳗鱼依然有许多未解之谜。

当然最富冲击力的冷知识是：
精神分析之父，西格蒙德·弗洛伊德，早年曾解剖了几百条鳗鱼试图寻找睾丸。~~（年轻人不要再吐槽自己的工作了）~~

**仿制药的真相**
原文标题是Bottle of Lies，印度最大仿制药厂兰伯西（Ranbaxy）骗局现形记，你能想象服下的药片里混有爆炸产生的玻璃碎片吗？

这本书非常适合拍成电影——而且是群相剧，整个记录涉及的势力，以兰伯西为代表的印度问题仿制药厂，以迈兰（Mylan）为代表的正规仿制药厂，辉瑞（Pfizer）等品牌药厂，美国药监局FDA，外交部，医院，没有一个是「白」的。各势力中一些有良心的个人揭露印度仿制药厂的造假，用十几年的时间推动着美国漏洞频出的监管和法律机构，终于在2013年使兰伯西认罪。但这不是happy ending——时至今日这些问题仿制药依然在生产。读完大概只能一声叹息，多注意自己和家人要吃的药吧。


## 其他

- 把默认PDF阅读器从Adobe Reader换成了Xodo，颜值高了一个档次。
- 打了一个DLsite上的超低价（$2）的斯拉夫神话主题同人游戏Wet Steps，在推特上发表感想被作者亲自感谢…其实相对价格剧情/CG完成度真的很高，创作不易。
- 用15磅哑铃时间久了发现有了点肱二头肌，心情非常微妙。
- 这个月大多投资操作都很平淡。最刺激的是自以为看见了黑天鹅，赌Palantir的Demo Day用了10+张期权的高风险策略，然而周三起的WallStreetBets vs对冲基金的神仙打架…果然看不见的才是黑天鹅。
- 一月的新番追了很多部，里世界郊游、怪物事变、悠哉日常大王、工作细胞…说不定去年不是我对动画失去兴趣，而是去年的番都太不能打了（暴言）。
- 湾区在不正常的高温后下了一整周的雨，这周在家都不用听Rainymood了。