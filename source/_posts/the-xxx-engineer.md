---
title: The XXX Engineer
date: 2020-11-26 15:06:28
mathjax: true
tags:
- 读书笔记
- 杂谈
---

整个11月都尽量从现实中抽离，刻意避免较「硬」的阅读思考，于是读了两本「软」一些的书，The Pragmatic Programmer（TPP）和The Effective Engineer（TEE），个人评分在7分。恰逢年底有几件重要的事情，在记忆被覆盖前先dump一下。
标题没什么特别的意义，只是为了表现各种可能的形式词，毕竟玩《千面英雄》梗写出The Engineer with a Thousand Faces还是过于中二了。

<!-- more -->

## Foreword

剥去pragmatic/effective/productive/10X这些定语，两本书在回答同一个问题，怎样成为更好的软件工程师。「好」从抽象到具体大致三个层次，(1) 正确的态度mindset，(2) 解决问题的通用思想thought pattern，和 (3) 工程上的最佳实践practice。举个例子，采取growth mindset是态度，遇到问题时设法尽快简单地验证想法是thought pattern，而是否给代码库引入持续集成是practice。相对来说，mindset和thought pattern更稳定所以学习价值高一些，但TPP出版1999年，TEE出版于2015年，关注下这几年的业界发展就能理解无论哪本都得take with a grain of salt。

## TPP: get the job done and do it well

TPP开篇提出pragmatic philosophy，之后的篇幅从项目前期准备、项目过程、架构设计甚至具体编程的方方面面提出怎么样做到pragmatic。但什么是作者提倡的pragmatic呢？我读完感觉这就是个筐，一切有利于把工作做完做好的就是pragmatic，反之则不是——pragmatic这里是严重过载的；所以别太纠结定语，把pragmatic当成是内容的包装盒比较好。

对我个人来说，TPP的精华可以概括为三句话：

- **It's your life.** 对自己的人生负责，不要让「改变」止于想法。
- **Find the box.** 有时客户没想清需求，有时工程师会被自己的思维限制，解决问题是不断探索「盒子」，理解条件和规则的过程。
- **Easy to change.** TPP把工程的最高美德总结为ETC (easy to change)。在不确定变化的环境中，最好的策略是保持快速适应的能力。这点放在设计上是orthogonality / reversibility，放在程序上是decouple / reduce software entropy，放在职业发展上是knowledge portfolio。

读TPP的有趣之处是你能感受到上个世纪的气息，却又能从中收获超越时间的东西。举个不恰当的例子，就像搭着大爷的老式汽车上高速，边上骑着鬼火的后浪们唰唰唰过去，你担心越落越后过了几迈发现那群人用各种姿势摔在地上，这时大爷才一推太阳镜「你们啊naive」。

## TEE: focus on high-leverage activities

整本TEE始于亦终于杠杆理论，圆算是画得完整。所谓杠杆理论就是要考虑工作的ROI (return on investment)，集中精力在高ROI的事情——10X工程师大概率不是用了10X的时间工作，而是ROI是普通人的10X。

$leverage=impact\\_produced / time\\_invested$

在真正的hard constraint时间有限的情况下，提高总impact只有三个方法：

- **减少工作时间。**这点可以概括为善用工具（人）。对于确定流程是用包括编辑器配置、性能分析工具、CI/CD等等尽可能简化、自动化；对于开放问题是善用别人的经验，“如果你已经考虑了2小时，就应该问问别人”。
- **增加工作产出。**大部分情况下产出内容确定，所以这条是最难的。不过价值是相对的，换言之可以通过宣传、重用等方法提高产出的价值。
- **转做杠杆更高的工作。**合理地给工作排序，潜台词是有的事可能拖着拖着就不用做了。

后面解释杠杆理论各种应用的章节（比如作者用To Do List战胜拖延症）可以一读但要带着批判性思维。因为对普通人来说真正重要的是可支配金钱和时间，和impact只能说是有correlation。虽然作者极力推崇optimize for learning，即使不抬杠learning的范畴，去start-up和在大公司rest and vest哪个结果更好也是没人能预测的。

TEE读起来知乎感很强，作者讲自己经历和业界故事动辄大段描写（甚至还有Googleplex沙滩排球场的风景），后面我都是大段跳着读了。

## Summary

两本书都在教你成为一名「好」工程师，道理大家多少都懂，看人梳理一遍也不错，但豆瓣之类的地方也有~~过于~~详细的笔记，没必要非得读原书。我在读时多少是抱着「每天阅读6分钟能有效降低老年痴呆发病率」的心态。

要说缺点的话，两本书都更多强调个人和公司利益的一致，甚至激进的引用了"what they are actually doing is paying you to accept a much lower intellectual growth rate"的TEE也没有更进一步，提出对抗的手段（比如在项目中使用相对不稳定的新技术，可能对公司不利但对个人是学习的最优解）。另一方面，其实我还挺期待哪本书能提下bad actors——比如把别人快做完的项目抢过来launch，那是多少倍的杠杆啊，可能这些一亩三分地的日经还是不宜正式出版吧。

标题的XXX也是因为想不出词来概括对现在工程师的要求，不过需要努力思考和行动这点在哪个时代都是一样的。

> Le vent se lève, il faut tenter de vivre. 