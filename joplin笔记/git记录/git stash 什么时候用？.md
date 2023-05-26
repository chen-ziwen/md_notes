当我们日常分支开发中，我们不要去改动主分支的代码，只需要通过创建分支以及合并就可以完成所有的操作，同样的，这样的操作不会导致主分支产生冲突。合并分支两种方式
- `git merge dev`  //将dev分支合并到主分支
- `git rebase master` // 将主分支作为基底，其他分支拼接到主分支上

==分支开发再理解：==
首先我们需要将分支切换到主分支`git checkout master`，然后拉取主分支的最新代码`git pull origin master`，拉取最新代码后，就不要去改动主分支的任何代码了。接下来创建一个开发分支`git checkout -b dev`，在开发分支上进行新任务的开发。当开发分支上的任务结束时，`git commit`一下。随后切换到主分支`git checkout master`，再执行`git pull origin master`拉取一下主分支的最新代码，这步操作结束后，将开发分支合并到主分支`git merge dev`，合并分支的过程中大概率会出现冲突，解决完冲突，`git add .` `git commit -m ''` `git push origin master`,到这里本次开发就算完成了。这个过程中完全不需要`git stash`,之前要用到stahs是因为总是在主分支上修改代码。

**当然git stash  是一个很好的指令，可以帮助解决git的很多问题**