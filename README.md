# Note

Common Note <br>
01 : resume-http://deercv.com/ <br>

Git Note <br>
01 git checkout -b “name” 创建一个新的分支 <br>
02 git branch --set-upstream-to=origin/master “branch” 本地分支与远程关联 <br>
03 (checkout master) (git merge xxx) xxx分支合并到master分支  <br>
04 (git rebase -i head~*)(press insert) (edit squash) (:wq) 合并两个提交  <br>
05 git branch -a 获取所有的分支 <br>
06 git remote add origin git@github... 本地项目与远程关联 <br>

RX Note <br>
01 Observable(被观察者) Observer(观察者) subscribe(订阅)<br>

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
