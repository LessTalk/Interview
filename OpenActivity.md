目前大耳朵 只支持三种类型跳转 <br>
第一种 显示启动  <br>
```java
{
    "parameter": "page^location^S",
    "type": "package",
    "flag": "",
    "name": "修改当前位置",
    "activity_name": "com.baofengtv.settings.MainActivity",
    "package_name": "com.baofengtv.settings"
}
```

其中parameter 代表参数

page     代表参数的 Key <br>
location 代表参数的 Value <br>
S        代表参数的类型  <br>

如果多个参数 用 | 区分 <br> 

例如 page^location^S|page^location^S <br>

flag 代表Intent需要添加的flag <br>

参数类型对照表如下 <br>
```java
B bundle.putBoolean(key, Boolean.parseBoolean(value)); <br>
S bundle.putString(key, Uri.decode(value)); <br>
b bundle.putByte(key, Byte.parseByte(value));<br>
c bundle.putChar(key, Uri.decode(value).charAt(0)); <br>
d bundle.putDouble(key, Double.parseDouble(value)); <br>
f bundle.putFloat(key, Float.parseFloat(value)); <br>
i bundle.putInt(key, Integer.parseInt(value));<br>
l bundle.putLong(key, Long.parseLong(value));<br>
s bundle.putShort(key, Short.parseShort(value));<br>

```
第二种 隐示启动  <br>
```java
{
    "name": "历史记录",
    "type": "action",
    "flag": "",
    "activity_name": "",
    "action_name": "com.bftv.fui.HistoryActivity"
}
```
第三种 发送广播启动 <br>
```java
{
    "parameter": "persion_type^login^S",
    "action_name": "com.baofengtv.voice.persion.action",
    "flag": "0X00008000",
    "type": "broadcast"
}
```
