# AndroidNode

01 : textview 设置距离顶部 5dp 那真实的字距离顶部的距离等于5dp吗 ？ （不等于 textview 有内边距） <br>
02 : 如果一个手机StatusBar 那么通过 DisplayMetrics 获取到的全屏高度 是否包含 StatusBar 的高度 （包含）<br>
03 :  如下 第一个 print 和第二个 的结果分别是什么 (test transform2 ) <br>

    public static void main(String[] args) {
        Test test = new Test();
        transform1(test.t1);
        System.out.println(test.t1);
        transform2(test);
        System.out.println(test.t1);
    }
    
    public static void transform1(String str) {
        str = "transform1";
    }

    public static void transform2(Test test) {
        test.t1 = "transform2";
    }

    public static class Test {

        public Test() {
        }

        String t1 = "test";
    }
    //基本类型作为参数传递时，是传递值的拷贝，无论你怎么改变这个拷贝，原值是不会改变的
    
    
04 : 位运算符的一些理解 

    public static final int STATUS = 1;

    public static final int RED = STATUS << 1;

    public static final int YELLOW = STATUS << 2;

    public static final int BLUE = STATUS << 3;

    public static void main(String[] args) {
        // TODO Auto-generated method stub
        int temp = 0;
        //write
        temp |= RED;
        temp |= YELLOW;
        temp |= BLUE;
        System.out.println(Integer.toBinaryString(temp));
        //contain
        System.out.println((temp & YELLOW) == YELLOW ? "contain" : "no");
        //remove
        temp &= ~YELLOW;
        System.out.println((temp & YELLOW) == YELLOW ? "contain" : "no");
    }

05 : android:clipChildren(是否限制子View在其范围内) 默认为true <br> 
06 : 5.0 通知要求Product icons are 48dp, with 1dp edges System icons are 24dp 白色icon 透明背景 <br>
07 : java 动态代理研究

    public class AsyncProxy implements InvocationHandler {
    private Object mObject;
    private ExecutorService mThreadPool = Executors.newFixedThreadPool(4);

    public AsyncProxy(Object obj) {
        mObject = obj;
    }

    @Override
    public Object invoke(Object proxy, Method method, Object[] args) throws Throwable {
        if (method.getReturnType() == void.class) {
            mThreadPool.submit(new Runnable() {
                @Override
                public void run() {
                    try {
                        method.invoke(mObject, args);
                    } catch (IllegalAccessException e) {
                        e.printStackTrace();
                    } catch (IllegalArgumentException e) {
                        e.printStackTrace();
                    } catch (InvocationTargetException e) {
                        e.printStackTrace();
                    }
                }
            });
            return null;
        } else {
            throw new RuntimeException("The return type of proxy method must be void.");
        }
    }
    ========================================================================================================
    public interface CallBack {
        public void call(ITest test);
    }
    ========================================================================================================
    public interface ITest {

    public void test1();

    public void test2(CallBack callBack);
    }
    ========================================================================================================
    public class Test implements ITest {

    private ITest test;

    public Test() {
        test = (ITest) Proxy.newProxyInstance(ITest.class.getClassLoader(),
                new Class<?>[] {
                    ITest.class
                }, new AsyncProxy(this));
    }

    public ITest async() {
        return test;
    }

    @Override
    public void test1() {
        // TODO Auto-generated method stub
        System.out.println("test1()@ThreadId=" + Thread.currentThread().getId());
    }

    @Override
    public void test2(CallBack callBack) {
        // TODO Auto-generated method stub
        System.out.println("test2()@ThreadId=" + Thread.currentThread().getId());
        callBack.call(this);
    }
    }
    ========================================================================================================
    public class Main {

    public static void main(String[] args) {
        // TODO Auto-generated method stub
        Test test = new Test();
        test.test1();
        test.async().test1();
        test.async().test2(new CallBack() {

            @Override
            public void call(ITest test) {
                // TODO Auto-generated method stub
                test.test1();
            }
        });
    }
08 String.format 
```java
    //%index$ index 代表第几个参数
    System.out.println(String.format("%1$,09d", -3123, 1234));
    System.out.println(String.format("%2$,09d", -3123, 1234));
    //09d 9 表示几位数
    System.out.println(String.format("%1$,09d", -3123, 1234));
    System.out.println(String.format("%1$,07d", -3123, 1234));
    //,表示 三位是否用,分割
    System.out.println(String.format("%1$,09d", -3123, 1234));
    System.out.println(String.format("%1$09d", -3123, 1234));
    // %1$s 格式化String
```
09 ViewCompat.postInvalidateOnAnimation(this); 会在下一帧 进行一些初始化操作 <br>
10 TextView 宽度 textView.measure(0, 0); textView.getMeasuredWidth(); <br>
11 java反射机制 <br>

    public class Hi {
    private void hello() {
        System.out.println("hello");
    }
    public static void main(String[] args) {
        // TODO Auto-generated method stub
        try {
            Class cls = Class.forName("Hi");
            Method m = cls.getDeclaredMethod("hello", new Class[] {});
            m.setAccessible(true);
            m.invoke(cls.newInstance());
        } catch (ClassNotFoundException e) {
            // TODO Auto-generated catch block
            e.printStackTrace();
        } catch (NoSuchMethodException e) {
            // TODO Auto-generated catch block
            e.printStackTrace();
        } catch (SecurityException e) {
            // TODO Auto-generated catch block
            e.printStackTrace();
        } catch (IllegalAccessException e) {
            // TODO Auto-generated catch block
            e.printStackTrace();
        } catch (IllegalArgumentException e) {
            // TODO Auto-generated catch block
            e.printStackTrace();
        } catch (InvocationTargetException e) {
            // TODO Auto-generated catch block
            e.printStackTrace();
        } catch (InstantiationException e) {
            // TODO Auto-generated catch block
            e.printStackTrace();
        }
    }
    
   
12 sin 对边/斜边  cos 临边/斜边 <br>
13 view.getTranslationX计算的是该view的偏移量。初始值为0，向左偏移值为负，向右偏移值为正 <br>
14 view.getX相当于该view距离父容器左边缘的距离，等于getLeft+getTranslationX <br>
15 is not an enclosing class ? <br>

      public class A {  
       public class B {  
           
       }  
      };  
      A a = new A();  
      A.B ab = a.new B(); 
      
16 Run with --stacktrace option to get the stack trace. Run with --info or --debug option to get more log output. ? <br>
   File > Settings > Compiler (Gradle-based Android Project) --info <br>
17 android handler use <br>

      private static class CommonHandler extends Handler{

        private final WeakReference<LayerDrawable> mLayerDrawable;

        public CommonHandler(LayerDrawable layerDrawable){
            mLayerDrawable = new WeakReference<LayerDrawable>(layerDrawable);
        }

        @Override
        public void handleMessage(Message msg) {
            super.handleMessage(msg);
            LayerDrawable layerDrawable = mLayerDrawable.get();
            if (layerDrawable != null) {
                layerDrawable.setLevel(msg.what);
            }
        }
    }

18 overridePendingTransition(R.anim.in_from_right, R.anim.out_to_left); 在子线程不工作 <br>
19 apply vs commit 对提交结果不关心建议使用apply(原子操作 之后会异步提交) 必须是同步建议commit <br>
20 java 泛型类 <br>
   

    public abstract class NetHelper<T> {

    protected Retrofit mRetrofit;

    protected NetHelper(String basrUrl){
        OkHttpClient.Builder builder = new OkHttpClient.Builder();
        builder.connectTimeout(5, TimeUnit.SECONDS);
        mRetrofit = new Retrofit.Builder().client(builder.build()).addConverterFactory(GsonConverterFactory.create())
                .baseUrl(basrUrl).addCallAdapterFactory(RxJavaCallAdapterFactory.create()).build();
    }

    protected void send(Observable<T> observable, Observer<T> observer){
        observable.subscribeOn(Schedulers.io())
                .observeOn(AndroidSchedulers.mainThread()).subscribe(observer);
    }
    }
    
21 java HashMap 遍历 <br>

        HashMap<String, String> testMap = new HashMap<String, String>();
        long maxValue = 1234567;

        for (int i = 0; i < maxValue; i++) {
            testMap.put(String.valueOf(i), "hello:" + i);

        }
        new Thread(new Runnable() {

            @Override
            public void run() {
                // TODO Auto-generated method stub
                long l1 = System.currentTimeMillis();
                for (Map.Entry<String, String> entry : testMap.entrySet()) {
                    String value = entry.getValue();
                }
                System.out.println("time1:" + (System.currentTimeMillis() - l1));
            }
        }).start();

        new Thread(new Runnable() {

            @Override
            public void run() {
                // TODO Auto-generated method stub
                long l2 = System.currentTimeMillis();
                for (String key : testMap.keySet()) {
                    String value = testMap.get(key);
                }
                System.out.println("time2:" + (System.currentTimeMillis() - l2));
            }
        }).start();

22 java super 默认构造函数 不写super同样会执行默认构造函数 <br>
   
   
     public class SuperTest {
     
     public SuperTest(){
        System.out.print("SuperTest");
     }
    
     public static void main(String[] args) {
        // TODO Auto-generated method stub

     }
      
    public class ChildTest extends SuperTest{
    
    private ChildTest(){
        System.out.print("ChildTest");
    }
     
    public static void main(String[] args) {
        // TODO Auto-generated method stub
        new ChildTest();
    }
23 singleTask模式的Activity不管是位于栈顶还是栈底，再次运行这个Activity时，都会destory掉它上面的Activity来保证整个栈中只有一个自己 <br>
24 ArrayList和LinkedList的区别 <br>
   1 ArrayLis 是线性表,在内存中是一块连续的存储空间,所以在中间添加或者删除某一个元素,都要移动其他元素<br>
   2LinkedList 是链性表 分散式存储, 每个元素都会记录下一个元素的位置,查找的值需要挨个遍历<br>
25 Split <br> 
   1 关于点的问题是用string.split("[.]") 解决<br>
   2 关于竖线的问题用 string.split("\\|")解决 <br>
   3 关于星号的问题用 string.split("\\*")解决 <br>
   4 关于斜线的问题用 sring.split("\\\\")解决 <br>
   5 关于中括号的问题用 sring.split("\\[\\]")解决 <br>
   
26 Android Button 5.0 之后英文默认大写  需要添加 android:textAllCaps="false" <br>
27 Android View Lifecircle <br>
<img src="https://github.com/LessTalk/Note/blob/master/android_view.png" width="700" height="400" /> <br>
