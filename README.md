# Note

Common Note <br>
01 : resume-http://deercv.com/ <br>

Python Note <br>

ProGuard Note <br>
01 代码混淆压缩比，在0~7之间，默认为5,一般不下需要修改 -optimizationpasses 5 <br>
02 Android不需要preverify，去掉这一步可以加快混淆速度 -dontpreverify <br>

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



