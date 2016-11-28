
Fiddler Note
01 添加Server Ip FiddlerObject.UI.lvSessions.AddBoundColumn("IP", 50, "x-hostip"); 
02 Https 抓包 <br>
```
 (1)首先对Fiddler进行设置：打开工具栏->Tools->Fiddler Options->HTTPS
 (2)选中Capture HTTPS CONNECTs，因为我们要用Fiddler获取手机客户端发出的HTTPS请求，
 所以中间的下拉菜单中选中from remote clients only。选中下方Ignore server certificate errors.
 (3)打开手机浏览器，在浏览器地址输入代理服务器IP和端口，(您自己的ip地址 +8888)
```
