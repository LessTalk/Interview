# Note

Common Note <br>
01 : resume-http://deercv.com/ <br>

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
    
<br>
