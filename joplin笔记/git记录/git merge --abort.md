> 参考链接
> [git merge --abort](https://blog.csdn.net/ThisEqualThis/article/details/125553012)

开发中可能会遇到这么一个问题 就是让别人的改动比较大的时候，这个时候git pull 会产生冲突，而且冲突文件比较多，这个时候如果你放弃了git pull 拉取的文件，你再次pull的时候会报错，是因为合并状态还没有结束，git merge --abort 可以跳出合并