
# GIT 

#  git add 的作用 
```java
git 有一个缓存区 git add 就是将文件提交到缓存区 在这个缓存区 你可以随意的提交和修改 
确定好了之后一次性 commit 上去 而commit是原子性的 
```
1. git add .  当前目录下所有文件 <br>
2. git status 查看当前add的文件 <br>
3. git reset HEAD 上一次add的全部撤销 <br>
4. git reset HEAD path(路径) 撤销某一个路径 <br>

# 回滚 origin 

method1 但是这样会产生新的提交记录 <br>
```java
git revert Head 
git push origin master
```
method2 强制更新远程分支<br>
```java
git reset HEAD~1
git stash
git push -f origin master
```

# stash

```java
git stash #可用来暂存当前正在进行的工作
git stash pop #从Git栈中读取最近一次保存的内容
git stash list #显示Git栈内的所有备份
git stash clear #清空Git栈
git stash apply stash@{1} #可以将你指定版本号为stash@{1}的工作取出来
```

# config

```java
git config --global user.name "test"
git config --global user.email test@gmail.com
```
