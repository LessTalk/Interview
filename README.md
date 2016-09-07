# Note

Common Note <br>
01 : resume-http://deercv.com/ <br>

Python Note <br>

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

Fiddler Note<br>

English Note <br>
01 Gradient 坡度 <br>
02 Tint 着色 <br>
03 Wrapper 包装 <br>
04 Apply 申请 应用 <br>
05 Layer 层 <br>

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

RX Note <br>
01 Observable(被观察者) Observer(观察者) subscribe(订阅)<br>
02 Observable.timer(time, TimeUnit.MILLISECONDS).subscribe(action1); 延迟 <br>

Android Note <br>
01 : textview 设置距离顶部 5dp 那真实的字距离顶部的距离等于5dp吗 ？ （不等于 textview 有内边距） <br>
02 : 如果一个手机StatusBar 那么通过 DisplayMetrics 获取到的全屏高度 是否包含 StatusBar 的高度 （包含）<br>
03 :  如下 第一个 print 和第二个 的结果分别是什么 (test transform2 ) 

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

    //%index$ index 代表第几个参数
    System.out.println(String.format("%1$,09d", -3123, 1234));
    System.out.println(String.format("%2$,09d", -3123, 1234));
    //09d 9 表示几位数
    System.out.println(String.format("%1$,09d", -3123, 1234));
    System.out.println(String.format("%1$,07d", -3123, 1234));
    //,表示 三位是否用,分割
    System.out.println(String.format("%1$,09d", -3123, 1234));
    System.out.println(String.format("%1$09d", -3123, 1234));

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
  



