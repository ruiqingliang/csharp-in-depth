# 4. 基础类型

### 4.1 is、as
```c#
public class A{

}
public class B{

}
public static void Main()
{
    A a = new B(); // B is a A
    object o = a;
    if(a is A){     // 判断a是不是一个A类型对象，如果是强转成A。
        A a1 = (A)o;
    }
    // 上面的代码会校验两次类型，性能不好

    // 使用as代替上面的代码，只有一次类型检查。
    A a2 = o as A;
    if(a2 != null){
        ...
    }
}
```

### 4.2 using
```c#
using System;
using System.IO;
using System.Text;

public static void Main()
{
    // 编译器将按照using顺序拼接Console的完整路径
    Console.WriteLine("111");
    /**
        System.Console;
        System.IO.Console;
        System.Text.Console;
    */

    // 下面是假设的伪代码
    // 假设 System.IO 和 System.Text 都有一个View类。
    View v = new(); // 编译器会报错，提示有多个命名空间找到了类定义。

    //解决方案1：使用using 改名
    using IOView = System.IO.View;
    IOView iv = new();

    //解决方案2: 指定完整路径
    System.IO.View view = new();
}



```