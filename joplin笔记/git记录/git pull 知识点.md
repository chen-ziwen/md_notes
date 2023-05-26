**git pull 相当于git fetch和git merge的简写**
使用`git pull`的时候会遇到三种情况
1. 当远程与本地没有冲突时，这个时候直接pull即可，系统会自动生成一条commit记录，`git lg`可查看，此时本地仓库中不会显示拉取到的代码。
2. 当远程与本地有冲突，且本地没有未提交的commit时，此时pull会失败，而且会提示是哪个文件导致的冲突，这个时候需要进入文件中修改冲突，然后再pull即可，还有解决办法就是将本地的代码stash保存起来。
3. 当远程与本地有冲突，且本地有提交的commit时，此时pull会将远程所拉取到的所有文件都展示在工作区，这个时候将冲突解决后，就必须再commit一次，也就是说需要一次性提交两个commit，后面的那次commit可以备注merge，如果不想有多个commit记录，可以选择git rebase 变基。

**当git pull 提示冲突时解决办法
1. git stash
2. git fetch + git merge 手动合并冲突
