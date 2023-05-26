> 在日常工作中，我们经常会遇到有多个commit的情况 直接推送上去 代码结构不够清晰 同时多个commit 之间也会有冲突 。所以合并多个commit的方法就比较重要，这边也是来总结一下。
> ==参考连接：==
> 1. [三种合并多个commit方法](https://blog.csdn.net/qq_23274715/article/details/112911355)
> 2. [git rebase 合并多个commit](https://www.cnblogs.com/gradyblog/p/16057734.html)
## git reset 
1. `git reset` 合并多个commit 是最好理解的，因为git reset 会将多个commit 都中的代码都回退到工作区，这个时候只需要在工作区中解决冲突，然后再重新`git add`,`git commit`即可。
2. 或者使用`git reset --soft HEAD~xx` xx代表需要回退几个commit，这样指定的代码都会被回退到暂存区，如果回退的多个commit 有冲突就先解决冲突，再`git commit`即可。
## git rebase

## git commit --amend