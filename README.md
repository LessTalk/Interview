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

短信权限判断方法 支持android2.3 -android6.0+ <br>
背景: 国内机型种类繁多 并且谷歌公司并未提供 获取短信读写权限的api,这套解决方案支持绝大多数机型<br>
从 6.0+ 开始 谷歌公司开始向开发者提供判断 有无读写权限的api 这里只讨论6.0 以下的方法<br>
1: 如果系统版本 大于2.3 小于4.0 这个时候 先插入一条隐藏短信, 然后在去系统读取 如果系统短信大于0 说明有读取权限.反之没有<br>
2: 如果系统在4.0 到4.3之间 部分机型 可以用反射强制设置权限<br>
3: 如果系统版本大于4.3 或者不支持强制设置权限的机型 可以用反射 获取系统权限 <br>
4: 如果系统版本在4.0 - 6.0之前 并且之前方法均不成功 使用方法1获取系统权限 <br>
