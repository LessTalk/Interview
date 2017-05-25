# 集成

step1  导入 record1.1.aar <br>

step2 检查自己项目中 是否实现Thread.UncaughtExceptionHandler 如果有需要去掉 <br>

step3 在Application中 添加如下代码 <br>
```java
RecordManager.getInstance().init(this,"your_name");
```
当前我们还提供了高级功能 (其中TestActivity 代表你的MainActivity) 

```java
RecordManager.getInstance().init(this, "your_name", new ErrorDealHandler.OnDealExceptionHandlerListener() {
            @Override
            public boolean isDealError(String s) {
                return false;
            }

            @Override
            public Class isNeedRestart() {
                return TestActivity.class;
            }

        });
```

# 测试

step1 在自己项目代码任意处 手动制造一个错误 <br>

step2 检查SD卡 bftv_record 目录下面是否有 error.txt 和 hash.txt 文件 <br> 

step3 安装 log_collect.apk <br>

step4 模拟发送广播 action = "com.bftv.fui.log.test" <br>

step5 检查SD卡 bftv_record 目录下 如果文件为空 代表上传成功 通知我 <br>

