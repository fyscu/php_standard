# git flow
- [简单介绍](#c1)
- [开始使用](#c2)
- [详细说明](#c3)



## <a id="c1">简单介绍</a>
### git-flow,是一个工具，是一种规范
		
> 	Git Flow是构建在Git之上的一个组织软件开发活动的模型，是在Git之上构建的一项软件开发最佳实践。Git Flow是一套使用Git进行源代码管理时的一套行为规范和简化部分Git操作的工具。

> （ http://www.ituring.com.cn/article/56870 ）

所以说，git-flow 是一个规则，一种约定，一种规范，并不是什么洪水猛兽，
是提高你使用git技术的一个进阶实践。


### git-flow 基于git本身的分支管理机制
所以，你必须先了解什么是git的分支(branch).请看图

![](https://raw.githubusercontent.com/quickhack/translations/master/git-workflows-and-tutorials/images/git-workflow-release-cycle-2feature.png)

因为时间关系，我们假设你已经知道什么是branch，
git-flow就是通过在一个项目里划分不同的分支，来实现功能开发、bug修复、版本发布，以及开发过程中的冲突处理等。

（如果觉得这个描述有点绕，那么暂时不用理解它。）

### git-flow把分支划分了几个类别
Master
	
	就是平时我们看到的master，项目的主要分支，对外的第一门面。
	所有外人浏览你的项目，使用你的项目，第一时间都是看到master。
	你可以把它理解成  稳定无bug发布版 。（任何时候都ready to deploy）
	所以，git-flow 要求我们不能在master下做开发。
	
Develop

	处于功能开发最前线的版本，查看develop分支就能知道下一个发布版有哪些功能了。
	develop一开始是从master里分出来的，并且定期会合并到master里，
	每一次合并到master，表示我们完成了一个阶段的开发，产生一个稳定版。
	同样的，develop下也不建议直接开发代码，develop代表的是已经开发好的功能
	的回归版本（为什么说回归？）
	
Feature

	带着develop处的疑问，我们在feature里为你解答。（有点长，别不看）
	feature的作用是为每一个新功能从develop里创建出来的一个分支。
	例如小明和小白分别做两个不相干的功能，就应该分别创建两个分支，
	各自开发完以后，先后合并到develop里，这就叫做回归。
	在这个过程里，小明小白不需要任何的沟通，分别并行地开发，
	git-flow能很好的处理好分支间并行开发的关系。
	
	而develop，则会在适当的时候，由合适的人，合并到master，作为下一个稳定版本。
	
Hotfix

	以上3种以外，还有一个很重要的类型，hotfix。
	它是用来修复紧急bug的，而bug通常是来自线上的，
	所以hotfix分支是从master里创建出来的，并且，在bug修改好以后，
	要同时合并到master和develop，这一点需要特别注意。
	
Release

	release更多倾向与版本发布，项目上线前的一些全面测试以及上线准备。
	同样也肩负着版本归档，回滚支持等。

## <a id="c2">开始使用</a>
上面说到了，git-flow本质只是一个约定，所以你完全可以在现行的git命令行里，
手动地完成全部git-flow操作，（手动创建、合并分支等），
重点是遵守git-flow规范，遵守命名约定和分支管理流程。

不过，git-flow早就有插件了。参看这个文章：
> http://blog.163.com/tod_zhang/blog/static/1025522142012913113957679/
> 
> 安装了这个插件，你的git就多了一系列方便的命令，比如：

> git flow init
> 
> git flow feature start
> 
> git flow feature finish  
> 
> 等等。


不过，我觉得这个插件还是不够方便，我墙裂推荐你们都用 SourceTree 。

![](https://www.sourcetreeapp.com/dam/jcr:4c4d9b59-1049-4abc-b773-cc052c17f73c/sourcetree_rgb_slate.png?cdnVersion=fi)

如果我要推荐一个git-flow客户端，我会推荐SourceTree。

如果我要推荐一个git客户端，那我还是推荐SourceTree。

没错，SourceTree是专门为git-flow开发的git客户端，它涵盖了所有git本身的功能，

所以即使你不flow，你也可以使用SourceTree来管理你的git项目。

官方网站：
> https://www.sourcetreeapp.com/

至于如何下载、安装、/* 破解 */ ，这些内容就交给各位自行baidu了。

## <a id="c3">详细说明</a>

那么下面我们来实际操作一次，看看SourceTree如何帮助我们使用git-flow

**1.小明创建了一个新项目，就做 Demo，并且用SourceTree来打开它。如果这一步都
不会，你还是别做开发了。**

（一个新的项目，就不发图了）

**2.小明为了使用git-flow，需要为git项目做一次初始化。**

![](http://lanhao.name/img/upload/1.png)

这些可以改动的地方，为了方便其他协作人员，还是用默认好了。


**3.初始化后，会自动切换到develop分支，接下来，小明要发一个新功能**

![](http://lanhao.name/img/upload/2.png)

注意那个 **Git Flow** 按钮，所有flow的功能都是从那里开始操作的。
在弹出的窗口里输入功能的名字即可，小明决定开发一个 test1 功能。

这时，左侧的菜单已经看到分支切换到test1了（有加粗效果）

![](http://lanhao.name/img/upload/3.png)

**4.然后小明开始了暗无天日的编码过程，千辛万苦后写了一行readme**

接下来我们演示一下如何提交修改

![](http://lanhao.name/img/upload/4.png)

这个界面十分清晰地告诉你本地没有commit的代码，

当然了，这仅仅是commit到本地，因为这始终是git，我们还需要push到远端。

![](http://lanhao.name/img/upload/5.png)

可以在左侧看到，我们暂存了多少个commit。
按照图上流程，选择你要push 的分支，你也可以一次选择多个，
在这里我们先push 功能分支test1 。



**5.提交过几次代码之后，小明认为功能已经开发完毕，可以回归到develop了**

注意，这个时候，只有test1的代码是改变了的，develop还是停留在小明创建feature时的状态。

为了安全起见，每次合并之前，最好pull一下develop，再次不表。（SourceTree拉取）

那么我们现在把开发好的test1合并到develop：

![](http://lanhao.name/img/upload/6.png)

整个界面很简单，就一个操作，实际上，它背后做了很多。   (@  -_-)

如无意外，test1里的改动会合并到develop里，并且会删除**本地**的test1，

然后把分支切换到develop，这时候我们应该能看到整个test1期间的变动数目：
![](http://lanhao.name/img/upload/7.png)

接下来你应该立即把develop的改动push到远端！

OK，这就是一个功能开发的完整流程，就算有多个功能在并行开发，

通过git-flow的协调，都能互不干扰地开发，最终全部作用到develop上。