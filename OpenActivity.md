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

page     代表参数的 Key
location 代表参数的 Value
S        代表参数的类型

参数类型对照表如下
```java
private Bundle setExtras(String type, String key, String value, Bundle bundle) {
        byte var6 = -1;
        switch(type.hashCode()) {
        case 66:
            if(type.equals("B")) {
                var6 = 1;
            }
            break;
        case 83:
            if(type.equals("S")) {
                var6 = 0;
            }
            break;
        case 98:
            if(type.equals("b")) {
                var6 = 2;
            }
            break;
        case 99:
            if(type.equals("c")) {
                var6 = 3;
            }
            break;
        case 100:
            if(type.equals("d")) {
                var6 = 4;
            }
            break;
        case 102:
            if(type.equals("f")) {
                var6 = 5;
            }
            break;
        case 105:
            if(type.equals("i")) {
                var6 = 6;
            }
            break;
        case 108:
            if(type.equals("l")) {
                var6 = 7;
            }
            break;
        case 115:
            if(type.equals("s")) {
                var6 = 8;
            }
        }

        switch(var6) {
        case 0:
            bundle.putString(key, Uri.decode(value));
            break;
        case 1:
            bundle.putBoolean(key, Boolean.parseBoolean(value));
            break;
        case 2:
            bundle.putByte(key, Byte.parseByte(value));
            break;
        case 3:
            bundle.putChar(key, Uri.decode(value).charAt(0));
            break;
        case 4:
            bundle.putDouble(key, Double.parseDouble(value));
            break;
        case 5:
            bundle.putFloat(key, Float.parseFloat(value));
            break;
        case 6:
            bundle.putInt(key, Integer.parseInt(value));
            break;
        case 7:
            bundle.putLong(key, Long.parseLong(value));
            break;
        case 8:
            bundle.putShort(key, Short.parseShort(value));
        }

        return bundle;
    }
```
第二种 隐示启动  <br>
```java

```
第三种 发送广播启动 <br>
