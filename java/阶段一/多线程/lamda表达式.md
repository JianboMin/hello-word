# lamda表达式

- lamda表达式是为了简化创建函数式接口实现类

- 理解Functional Interface（函数式接口）是学历Java8 lamda表达式的关键

- 函数式接口定义：

  - 任何接口，如果它只包含唯一一个抽象接口，那么它就是一个函数式接口

    ```java
    public interface Runnable{
        public abstract void run();
    }
    ```

  - 对于函数式接口，我们可以通过lamda表达式来创建该接口的对象

>实例1 接口方法不带参数

```java
package lamda;

/**
 * @description:不带参数的lamda表达式
 * @author: minjb
 * @date: 2021-07-14 07:49
 **/
public class LamdaTest1 {
    // 静态内部类
    static class Like1 implements ILike {
        @Override
        public void lamda() {
            System.out.println("I Love lamda1");
        }
    }

    public static void main(String[] args) {
        ILike like = new Like();
        like.lamda();

        // 静态内部类
        like = new Like1();
        like.lamda();

        // 局部类
        class Like2 implements ILike {
            @Override
            public void lamda() {
                System.out.println("I Love lamda2");
            }
        }
        like = new Like2();
        like.lamda();

        // 匿名内部类
        like = new ILike() {
            @Override
            public void lamda() {
                System.out.println("I Love lamda3");
            }
        };
        like.lamda();

        // lamda表达式
        like = () -> {
            System.out.println("I Love lamda4");
        };
        like.lamda();

        // 去掉花括号（只有一行代码时才能省略）
        like = () -> System.out.println("I Love lamda5");
        like.lamda();
    }

}


interface ILike {
    public abstract void lamda();
}

// 1.内部类
class Like implements ILike {

    @Override
    public void lamda() {
        System.out.println("I Love lamda");
    }
}
```

> 实例2 带多个参数的lamda表达式

```java
package lamda;

/**
 * @description:带多个参数的lamda表达式
 * @author: minjb
 * @date: 2021-07-14 07:49
 **/
public class LamdaTest2 {
    // 静态内部类
    static class Like1 implements ILike2 {
        @Override
        public void lamda(int a, int b) {
            System.out.println("静态内部类： "+"I Love lamda1 a" + a +" b" + b);
        }
    }

    public static void main(String[] args) {
        ILike2 like = new Like2();
        like.lamda(520,521);

        // 静态内部类
        like = new Like1();
        like.lamda(520,521);

        // 局部类
        class Like3 implements ILike2 {
            @Override
            public void lamda(int a, int b) {
                System.out.println("局部类： "+"I Love lamda3 a" + a +" b" + b);
            }
        }
        like = new Like3();
        like.lamda(520,521);

        // 匿名内部类
        like = new ILike2() {
            @Override
            public void lamda(int a, int b) {
                System.out.println("匿名内部类： "+"I Love lamda4 a" + a +" b" + b);
            }
        };
        like.lamda(520,521);

        // lamda表达式
        like = (int a, int b) -> {
            System.out.println("带参数类型的lamda表达式: "+"I Love lamda5 a" + a +" b" + b);
        };
        like.lamda(520,521);

        // 去掉花括号（只有一行代码时才能省略）
        like = (a,b) -> System.out.println("去掉参数类型的lamda表达式："+"I Love lamda6 a" + a +" b" + b);
        like.lamda(520,521);
    }

}


interface ILike2 {
    public abstract void lamda(int a,int b);
}

// 1.内部类
class Like2 implements ILike2 {
    @Override
    public void lamda(int a, int b) {
        System.out.println("I Love lamda a" + a +" b" + b);
    }
}
```





