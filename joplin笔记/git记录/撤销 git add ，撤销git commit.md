### 撤销git add
有时可能 git add .（空格 + 点）表示当前目录所有文件，不小心就会提交其他文件。git add 如果添加了错误的文件的话，撤销操作：

```
git status // 先看一下add 中的文件

git reset HEAD // 如果后面什么都不跟的话，
就是上一次 add 里面的内容全部撤销

git reset HEAD XXX/XXX/XXX.java // 就是对某个文件进行撤销
```

### 撤销上一次git commit
```
git reset --soft HEAD^
```