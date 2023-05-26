> 在我们的日常开发中，如果我们想要改变仓库的链接其实很简单。
> 参考链接：https://blog.csdn.net/qq_38709383/article/details/124432908

### 1.  首先，我们需要先删除之前关联的origin的远程库，代码如下：
```git
git remote rm origin 

```
### 2. 将本地的仓库关联到github上，代码如下：
```git
git remote add origin xxx

// 这个xxx为git的ssl链接或者https链接
```
### 3.最后再执行一下如下操作就能成功推送到自己的仓库：
```git
git push origin master
```