> 熟悉git开发的人应该知道，git存在四个区域，工作区、暂存区、版本库、远程仓库，只有熟悉这个基本概念，才能更好的深入git的使用，而git reset 的三个关键词也涉及到了这四个区域。
> 参考连接：
>1.  [git四个区域](https://www.cnblogs.com/zwh-world/articles/15913088.html)
>2.   [Git reset 三种模式(hard,soft,mixed)](https://blog.csdn.net/zts_zts/article/details/115220786)

### git 四个区域
- 工作区（Workspace）
	- 存放代码的地方，每次修改的代码都会放入工作区
- 暂存区（Stage / Index）
	- `git add` 后会将工作区的代码放到暂存区
	- 存放临时的改动，git diff可以对比工作区和暂存区的区别
- 版本库 （Repository）
	- `git commit` 后会将暂存区的代码放入到版本库 （这个时候就会有提交记录）
- 远程仓库（Remote）
	- `git push`会将版本库中的代码推送到远程仓库

### git reset 与四个区域的关联
> [commit id] 表示git commit 提交的某一个版本id，版本号。
- git reset --mixed [commit id]（默认，mixed可省略）
	- 回退到指定的commit id版本，回退之后的所有内容全部放进工作区中
    - 案例
```git
# 回退到指定 commit id 并且将回退的代码全部放入到工作区中。
git reset --mixed c983d4f8da9ab3b8db3d84d2d53e14c56047abc7
git reset c983d4f8da9ab3b8db3d84d2d53e14c56047abc7

操作如下：
1. git reset --mixed (commit id) 撤回代码
2. git status 可查看回撤到工作区的代码

```

- git reset --soft [commit id]
	-  回退到指定的commit id版本，回退之后的所有内容都放到暂存区
	- 案例
```git
# 回退到指定 commit id 并且将回退的代码全部放入到暂存区中。
git reset --soft c983d4f8da9ab3b8db3d84d2d53e14c56047abc7

操作如下：
1. git reset --soft (commit id) 撤回代码
2. git status 可查看回撤到暂存区的代码
```
- git reset --hard [commit id]
	- 回退到指定的commit id版本， 回退并清空工作目录以及暂存区的所有修改 （谨慎使用，一旦退回某个版本，工作区和缓存区的改动代码都会清空）
	- 案例
```git
# 回退到指定 commit id 并且清空工作目录及暂存区所有修改。
git reset --hard c983d4f8da9ab3b8db3d84d2d53e14c56047abc7

操作如下：
1. git reset --hard (commit id) 撤回代码
2. git log 可查看是否回退到了指定的 commit id
3. git status 可查本地修改代码都清空了
```
	
