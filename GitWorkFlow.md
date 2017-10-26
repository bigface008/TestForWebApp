#  GitFlow
#### 导语
> Git是一种强大的版本控制工具。不同于svn，它更加强调一种适合团队工作、分布式管理的工作流程。不要被“团队工作”、“分布式管理”所吓倒。感谢Vincent Driessen和其他开源工作者的不懈努力与无私奉献，针对Git的工作流程——GitFlow不但功能强大而且简单易懂。

## 一、认识GitFlow

2010年1月5号，Vincent Driessen在个人博客网站上更新了一篇文章[A Successful Git Branching Model](http://nvie.com/posts/a-successful-git-branching-model/)，而这即是GitFlow的首次亮相。
其中，flow，工作流，即指工作流程。本文不会介绍工作流本身，理由如下。

>工作流（WorkFlow）本身不是一个初级主题，背后的本质问题其实是有效的项目流程管理和高效的开发协同约定，不仅是Git或SVN等VCS或SCM工具的使用。

上面一段话摘自[xirong在segmentationfault上整理的文章](https://segmentfault.com/a/1190000002918123)。可以看到，workflow已经超出了GitFlow的讨论范围。另外，GitFlow实际上是一种工作模式，并不是说基于Git只能进行GitFlow模式的工作。其他常见的软件开发模型，诸如瀑布模型、迭代开发模型、以及敏捷开发模型均可以使用Git进行工作。每种模型有各自的应用场景。而GitFlow重点解决的是源代码在开发过程中的各种冲突导致开发活动混乱的问题，在解决以上开发模型的冲突时大显身手。

### 工作方式

GitFlow工作流定义了一个围绕项目发布的严格分支模型：使用中央仓库为所有开发者的交互中心，开发者在本地工作并push分支到要中央仓库中。

#### 历史分支

GitFlow工作流使用2个分支来记录项目的历史：master分支存储正式发布的历史；develop分支作为功能的集成分支。

![](./images/pic1.png)

#### 功能分支

每个功能（Feature）拥有独立的分支。从develop分支上建立新分之后，在其基础上开发、完善功能，新功能完成之后合并回develop分支。当然，这些分支不一定根据功能来划分。不同的团队、开发者，均可以作为分支的依据。不过推荐使用功能作为分支依据。这（似乎）是程序员长期实践后得出的结论。

![](./images/pic2.png)

#### 发布分支

当需要发布或者开始准备发布工作时，应当从develop分支上新建一个发布分支。该分支仅用于发布，这意味着创建该分支后添加的所有功能不会加入发布分支。发布完成后，将发布分支合并到master分支上，分配版本号，打好Tag。另外，从建立发布分支以来做的修改要合并回develop分支。

![](./images/pic3.png)

#### 维护分支

维护分支用于快速修复发布版本（production release）的漏洞，是唯一从master分支中fork出来的分支。修复完成后，应马上合并回master分支、develop分支、当前发布分支。master分支应用新的版本号打好Tag。

![](./images/pic4.png)

至此，GitFlow的大致流程就介绍完了。

## 二、为何使用GitFlow

对于这个问题，我们需要追本溯源。来看看Vincent Driessen的原文中阐述选择Git而非SVN的理由。

>From the classic CVS/Subversion world I came from, merging/branching has always been considered a bit scary (“beware of merge conflicts, they bite you!”) and something you only do every once in a while.But with Git, these actions are extremely cheap and simple, and they are considered one of the core parts of your daily workflow, really.

这说明，在2010年时，已经有人将代码版本的管理视作开发工作中非常基础的需求。这实际上也是因为，2010年前后，正是互联网的又一次飞跃时期。云计算、分布式等概念的兴起与实施，需要我们方便快捷地管理代码、协作。

## 三、如何使用GitFlow

    