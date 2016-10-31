# Note

Common Note <br>
01 : resume-http://deercv.com/ <br>

Python Note <br>

ProGuard Note <br>
01 代码混淆压缩比，在0~7之间，默认为5,一般不下需要修改 -optimizationpasses 5 <br>
02 Android不需要preverify，去掉这一步可以加快混淆速度 -dontpreverify <br>

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

Fiddler Note<br>
01 添加Server Ip  FiddlerObject.UI.lvSessions.AddBoundColumn("IP", 50, "x-hostip");  <br>

KeyStore <br>
01 cd C:\Program Files\Java\jdk1.7.0_01\bin <br>
02 keytool -genkey -alias android.keystore -keyalg RSA -validity 20000 -keystore android.keystore <br>

English Note <br>
01 Gradient 坡度 <br>
02 Tint 着色 <br>
03 Wrapper 包装 <br>
04 Apply 申请 应用 <br>
05 Layer 层 <br>
06 Indicates 指出 <br>

Mac KeyMap Note <br>
01  command + shift + g  打开指定目录<br>

Plugin Note <br>
01 JSONOnlineViewer View-JSONOnlineViewer 测试接口的插件<br>
02 ParcelableGenerator open bean 右键 generate -Parcelable 自动生成序列化 <br>
03 SelectorChapek 自动生成selector 图片 <br>
04 ButterKnife Zelezny 选中R.layout.xx 右键 自动生成代码 <br>
05 Android File Grouping 右键 layout 第一个Group Layout自动分组插件 <br>

Android Studio Note <br>
01 File - Setting - Appearance - System Setting - Http Proxy 设置代理 <br>
02 Android Studio之导出JavaDoc出现编码GBK的不可映射字符  在Other command line arguments 添加 -encoding utf-8 -charset utf-8 <br>
03 Error Loading Project: Cannot load 3 facets Details...  File -> Settings - > Plugins -> Enable "Android Support" Plugin. <br>
04 Duplicate files copied in APK META-INF/LICENSE.txt <br>
       
    android {  
    
    packagingOptions {  
        exclude 'META-INF/DEPENDENCIES.txt'  
        exclude 'META-INF/LICENSE.txt'  
        exclude 'META-INF/NOTICE.txt'  
        exclude 'META-INF/NOTICE'  
        exclude 'META-INF/LICENSE'  
        exclude 'META-INF/DEPENDENCIES'  
        exclude 'META-INF/notice.txt'  
        exclude 'META-INF/license.txt'  
        exclude 'META-INF/dependencies.txt'  
        exclude 'META-INF/LGPL2.1'  
    }  
05 ctrl F 批量替换 <br>

Keymap Note(为了保证统一 window mac 均采用eclipse命名方式)<br>
01 ctrl + shift + r 打开新的类 <br>
02 ctrl + h 搜索 <br>
03 ctrl + l 跳转到line <br>
04 ctrl + 0 打开outline <br>
05 alt + shift + r 重命名 <br>
06 ctrl + d 删除当前行 <br>
07 ctrl + g 项目中的引用 <br>
08 ctrl + shift + g 当前类中的引用 <br>
09 ctrl + alt + l 格式化 <br>
10 ctrl + alt + o 删除无效的包 <br>
11 shift + F9 <br>



