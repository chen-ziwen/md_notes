> 在日常开发中拉去新项目时，偶尔会出现拉去下来的项目文件夹为空，那是因为.git目录下.git/refs/heads不存在HEAD指向的文件，这个时候可以用git show-ref命令查看，解决办法如下：
> 参考链接：https://blog.csdn.net/williamvon/article/details/71421810

### 执行命令
git branch //输入出空
git branch -a //输出 remotes/origin/==chiko==
git checkout remotes/origin/==chiko== // ① checkout的是git branch -a输出的内容
这样通过ll命令查看，Contacts代码下载到工作目录了
接着创建分支：
git checkout -b remotes/origin/==chiko== // ② 创建分支
git branch //可以看到输出*remotes/origin/==chiko==了，不再为空
git branch -m remotes/origin/==chiko== master // ③ 重命名分支叫master

完成！！
