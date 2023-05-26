> 参考链接： [git rebase](https://blog.csdn.net/weixin_42310154/article/details/119004977) 
> 好文章一看就懂 [https://zhuanlan.zhihu.com/p/68834307](git rebase 好文章)

例如，当我们在dev分支上的工作开发完成后，直接commit，然后切换回主分支继续开发。经过一段时间的开发，我们需要合并dev分支上的代码，
这个时候我们需要先将分支切换到dev分支，使用`git merge master`拉取主分支的最新代码，解决冲突后,`git add .`,`git commit`。然后切换回主分支，拉取合并最新的分支代码，这个时候`git lg`可能会发现树歪掉了，这个时候需要用到`git rebase`，用完会出现冲突的文件，解决冲突后，`git add .`，再执行`git rebase --continue`，这个时候会进入到vim编辑器中，按下i,我们可以去修改之前的commit记录，修改完按esc，再按:wq!,表示强制退出并保存，最后再push上去就好了。

当代码执行commit后，有时会出现文档树歪斜的情况，这个时候就需要执行rebase将文档树调整回来，具体操作看下面的链接：
