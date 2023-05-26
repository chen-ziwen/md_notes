> 日常工作中，使用git分支功能是很常见的

## git 切换分支问题（切换时需要commit）

**问题**：在使用git的时候发现如下小问题：不知道刚开始使用git的你有没有跟我一样也遇到过这样的问题：
git创建分支修改内容后，主分支也跟着改变，说好的分支之间各不影响呢？

**原因**：git在切换分支之前要确保当前分支没有未提交的修改，将当前分支内容进行commit之后再切换到其他分支，就看不到当前分支修改过的内容了

**总结**：当我们使用git的分支功能时，如果dev副分支的内容没有commit 提交，那么这个时候切换回main的时候，会发现main分支的内容也发生了修改。这个问题的解决方案就是，在切换回main分支之前，需要将dev分支的内容`git commit` ， 这个时候再切换回main分支，就会发现这次main分支并没有再因为dev分支的改变而改变。这个时候如果想要将dev分支的修改合并到main分支，只需要先切换到main分支，执行`git merge dev`即可合并分支内容。

**28/10/2022 补充**
当我们不想主副分支相互影响的话，就必须在副分支中多次commit ，但是多次commit会使副分支的提交记录过多，导致结构不够清晰，这个时候就可以进行多个commit之间的合并，将多个commit合并为一个commit后再进行push操作，这样就只会有一个commit提交记录。具体操作参考[多个commit的合并提交](../git记录/多个git%20commit的合并提交.md)文章。
* * *

==04/08/2022 补充==

## 小总结：

git branch 创建分支 创建出来的分支必须git add . git commit 后 才会跟主分支有所不同 一般分支执行完任务后就要删除掉 等下一次需要分支的时候在创建一个即可

比如说创建了分支 hello 当分支的commit 提交任务后 只需要切换到主分支 然后将hello分支和 主分支合并 。git merge hello 这样就能将 hello 分支的修改同步到master分支 使用起来非常的方便。

* * *

==28/10/2022 补充==

## 本地分支与远程分支
- 分支开发存在本地分支和远程分支，远程分支的意思就是将本地分支推送到了远程仓库，使用`git brach -a` 可以查看本地分支和远程分支，前面带个 `remotes/origin`的便是远程仓库，远程仓库的作用有很多，一个是备份，一个是独立开发，完全不影响主分支，独立开发完成后，再去合并到主分支，合并主分支有两个办法，一个是`git merge`，一个是`git rebase`,两种方法各有各的优点，需要的时候再去查看。
- 远程分支可以实现`git pull`,`git push`可以长期持有，但本地分支则不行。

### 本地分支

- 创建本地分支

```git
git branch xxx // 创建分支
git checkout xxx // 切换到xxx分支
or
git checkout -b xxx  // 创建分支的同时 切换分支

```

- 删除本地分支

```git
git checkout main // 先切换到主分支
git branch -d/-D xxx  // 删除副分支,-D为强制删除
```

### 远程分支

- 创建远程分支

```git
git branch 本地分支名 // 创建本地分支
git push origin 本地分支名 // 提交本地分支到远程仓库
git branch --set-upstream 本地分支名 origin / 远程分支名
or
git checkout -b 本地分支名  // 创建并切换到xxx分支
git push origin --set-upstream 本地分支名 // 远程分支创建成功
```

- 删除远程分支

```git
git push origin --delete 远程分支名 // 删除远程分支
```