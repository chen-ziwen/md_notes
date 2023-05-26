## 单密钥

> 参考链接：https://www.runoob.com/git/git-remote-repo.html

- ### 单密钥创建
    打开Gift Bash终端，输入以下代码：
    `ssh-keygen -t rsa -C "youremail@example.com"`

后面的 your\_email@youremail.com 改为你在 Github 上注册的邮箱，之后会要求确认路径和输入密码，我们这使用默认的一路回车就行。成功的话会在 ~/ 下生成 .ssh 文件夹，进去，打开 id\_rsa.pub，复制里面的 key。将复制的key添加到github的ssl密钥中即可。

## 多密钥
> 参考链接1：https://p3terx.com/archives/github-multiaccount-ssh-key-settings.html
>参考链接2： https://gitee.com/help/articles/4229#article-header1
> 前言：当有多个 GitHub 账号时，可能需要用到多个密钥，生成多个不同的公私密钥对，用 SSH 配置文件 ( ~/.ssh/config ) 管理它们。

- ### 生成多个密钥
```
ssh-keygen -t rsa -C "name@email.com" -f ~/.ssh/xxx //xxx表示额外的秘钥名称
```
完成之后，我们可以看到 ~/.ssh 目录下多了两个文件，变成：
>id_rsa
id_ras.pub
id_rsa_chenziwen
id_rsa_chenziwen.pub
known_hosts

- ### 配置config文件
如果没有就新建:
```
cd ~/.ssh/
touch config
```
添加一个主机别名配置:
```
# github
Host github.com
HostName github.com
PreferredAuthentications publickey  
IdentityFile ~/.ssh/id_rsa_chenziwen

//IdentityFile ~/.ssh/xxx 这个xxx指的就是新建密钥的名称
```
添加完测试一下
`ssh -T git@github.com`
如果成功则提示如下：
==Hi chen-ziwen! You've successfully authenticated, but GitHub does not provide shell access.==
完成
