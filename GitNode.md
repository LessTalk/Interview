
Git Note <br>
01 git checkout -b “name” 创建一个新的分支 <br>
02 git branch --set-upstream-to=origin/master “branch” 本地分支与远程关联 <br>
03 (checkout master) (git merge xxx) xxx分支合并到master分支  <br>
04 (git rebase -i head~*)(press insert) (edit squash) (:wq) 合并两个提交  <br>
05 git branch -a 获取所有的分支 <br>
06 git remote add origin git@github... 本地项目与远程关联 <br>
07 git diff --name-status new_commit_id old_commit_id git diff --name-status fff783f81f7559cd14a42a2ef6992142c2cbd3d5 ba5e6566f2472
   5eff1cb35ae2f1c7c3355fb9146 >d:\change.log 获取两个tag 之间的diff <br> 
08 git open .git/info/exclude 目录 写上想忽略的路径 <br>
09 git update-index --assume-unchanged PATH 忽略已经提交到服务端的类 <br>
10 git stash list   git stash apply stash@{2}  找回stash的代码 <br>
11 (1)gitk 右键<br>
   (2)git push origin --tags <br> 
   (3)gitk 复制 SHA1 <br>
   (4)git diff --name-status new_commit_id old_commit_id<br>
   (5)$ git diff --name-status fff783f81f7559cd14a42a2ef6992142c2cbd3d5 ba5e6566f2472
      5eff1cb35ae2f1c7c3355fb9146 >d:\change.log <br>
12 git push origin 本地分支:远程分支  本地分支提交到另一个远程分支 <br>
13 git branch <新分支名称> git push origin <新分支名称>  git branch -av (查看远程分支) <br>
14 git checkout master git merge as_master  将as_master分支合并到主分支 <br>
