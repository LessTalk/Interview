
step1  导入 record.aar <br>

step2 检查自己项目中 是否实现Thread.UncaughtExceptionHandler 如果有需要去掉

step3 在Application中 添加如下代码
```a
RecordManager.getInstance().init(this, "you_name", new ErrorDealHandler.OnDealExceptionHandlerListener() {
            @Override
            public void onError() {

            }
        });
```
