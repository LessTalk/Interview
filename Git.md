# Git

* 合并两个提交
```git
(git rebase -i head~*)(press insert) (edit squash) (:wq)
```
* 获取两个tag 之间的diff
```git
git diff --name-status new_commit_id old_commit_id git diff --name-status 
fff783f81f7559cd14a42a2ef6992142c2cbd3d5 ba5e6566f2472 5eff1cb35ae2f1c7c3355fb9146 >d:\change.log
```

* 忽略已经提交到远程的file
```git
git update-index --assume-unchanged PATH
```
