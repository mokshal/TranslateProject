那些数据对于云服务器来说风险很大
======
 ![](https://opensource.com/sites/default/files/styles/image-full-size/public/lead-images/rh_003499_01_cloud21x_cc.png?itok=5UwC92dO)
 
 在这系列文章中我们分四部分，我们一直在关注每个组织在做云迁移的时候应该避免的陷阱——特别是混合多云的情况下
 [在第一部分][1], 我们会介绍一些基本的定义以及我们对于混合云以及多云的看法，已确保显示两者的区别. [在第二部分][2], 我们会对三个陷阱进行讨论：第一个为什么成本并不是成为迁移云的核心明显在第一部分，我们会介绍一些基本的定义以及我们对于混合种类云以及多种类云的看法，已确保显示出两者的区别，
动力。 而且，[在第三部分][3], 我们将对所有工作向云进行迁移的可行性。在最后，第四部分中，我们将会对如何处理云的数据做研究以及您应该怎么把数据向云端迁移吗？迁移多少？什么数据在云端起作用，又是什么会造成移动风险很大？
 ### 数据...数据...数据..
 影响您对云端数据的所有决策的关键因素在于确定您的带宽以及存储需求。 Gartner预计 "2018年成为[$173亿美元]的业务[4]" 并且大部分资金是浪费在一些不必要的存储容量上："但是只需要优化一下工作量，全球的所有公司就可以节约620亿美元的不必要IT成本。根据Gartner的研究，非常令人惊讶的是，全球所有的公司为云服务器平均支付的费用比他们实际的费用多达36%
如果你已经阅读了本系列的前三个章节，南无你应该不会为此感到惊讶。然而令人更惊讶的是 Gartner的结论是 "如果全球的公司将他他们服务器数据直接迁移到云端上，仅仅只有25%的公司能够做到省钱。"
 等一下。。。。工作带来的负载是可以针对云进行优化的，但是可能只有一小部分公司会通过将数据向云端迁移来节省资金吗？这个又是什么意思？
 如果你去认为云服务商会根据带宽来收取云产生的费用。那么是将所有的公司内部部署的数据移至云端很快就会成为他们成本的负担。有以下三种情况。公司才可能会觉得值得把数据放在云端中:
  *具有存储和应用程序的单个云
  * 云中自带的应用程序以及内部存储
  * 云中的应用程序和缓存在云端的数据以及内部存储 
 在第一种情况下，通过将所有的内容都保留在单个云服务商哪里来节省带宽成本，但是这会产生一些锁定，这个通常与CIO的云战略或者风险防范计划所冲突
第二种方案是仅仅保留应用程序在云端所收集的数据，并且以最小值的方式传输到本地存储。这就需要仔细的考虑策略，其中只有最少使用数据的应用程序部署在云端
第三种情况就是将数据缓存在云端，应用程序和存储数据或者是在内部的“一个事实”，这也就意味着分析人工智能学习和机器学习可以在内部运行而无需把数据向云服务商上传，然后处理之后再返回。缓存数据仅仅基于应用程序对云的需求，甚至进行跨多云的部署缓存
 要想获得更多信息，请下载红帽[案例研究][5]，其中描述了跨混合多云环境下的阿姆斯特丹的史基浦机场的数据以及云和部署策略
 ###数据危险
大多数公司都认识到了他们的数据在市场中的专有优势以及智能能力。因此他们会非常仔细的考虑它在云存储的地点
 想象一下，这种情况：如果你是一个零售商，全球十大零售商之一。而且你已经计划了很长一段时间云存储战略，并且考虑使用亚马逊的云服务，但是突然间，亚马逊的 [Amazon buys Whole Foods][6]，并且准备进入你的市场。一夜之间，亚马逊已经增长了50%的零售规模，你是否还回去信任此零售数据云？如果您的数据已经就在亚马逊云中，你会打算怎么做？您是否会考虑使用退出策略来进行创建云计划？虽然亚马逊可能永远不会去利用您的数据潜在的见解——该公司可能甚至有针对此计划的协议 你能相信世界上任何人的话吗？
 ### 陷阱分享，避免遇到陷阱
分享我们在以前经验中看到的一些陷阱来帮助您的公司规划更安全，更持久的云端策略 [了解成本不是明显的动力来源，][2], [并非一切东西都在云端][3], 而是你必须在云端有效管理数据才是您成功的关键所在


 --------------------------------------------------------------------------------
 via: https://opensource.com/article/18/8/data-risky-cloud
 作者：[Eric D.Schabell][a]
选题：[lujun9972](https://github.com/lujun9972)
译者：[geekmar](https://github.com/geekmar)
校对：[校对者ID](https://github.com/校对者ID)
 本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出
 [a]:https://opensource.com/users/eschabell
[1]:https://opensource.com/article/18/4/pitfalls-hybrid-multi-cloud
[2]:https://opensource.com/article/18/6/reasons-move-to-cloud
[3]:https://opensource.com/article/18/7/why-you-cant-move-everything-cloud
[4]:http://www.businessinsider.com/companies-waste-62-billion-on-the-cloud-by-paying-for-storage-they-dont-need-according-to-a-report-2017-11
[5]:https://www.redhat.com/en/resources/amsterdam-airport-schiphol-case-study
[6]:https://www.forbes.com/sites/ciocentral/2017/06/23/amazon-buys-whole-foods-now-what-the-story-behind-the-story/#33e9cc6be898