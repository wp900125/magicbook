# CGLIB
## concept
CGLIB是一个功能强大，高性能的代码生成包。它为没有实现接口的类提供代理，为JDK的动态代理提供了很好的补充。通常可以使用Java的动态代理创建代理，但当要代理的类没有实现接口或者为了更好的性能，CGLIB是一个好的选择。
## demo
```java
import net.sf.cglib.proxy.Callback;  
import net.sf.cglib.proxy.CallbackFilter;  
import net.sf.cglib.proxy.Enhancer;  
import net.sf.cglib.proxy.NoOp;  
  
public class TestCglib {  
    public static void main(String args[]) {  
        Enhancer enhancer =new Enhancer();  
        enhancer.setSuperclass(TargetObject.class);  
        enhancer.setCallback(new TargetInterceptor());  
        TargetObject targetObject2=(TargetObject)enhancer.create();  
        System.out.println(targetObject2);  
        System.out.println(targetObject2.method1("mmm1"));  
        System.out.println(targetObject2.method2(100));  
        System.out.println(targetObject2.method3(200));  
    }  
}  
```
## insight
动态生成一个要代理类的子类，子类重写要代理的类的所有不是final的方法。在子类中采用方法拦截的技术拦截所有父类方法的调用，顺势织入横切逻辑。它比使用java反射的JDK动态代理要快。

使用字节码处理框架ASM，来转换字节码并生成新的类。不鼓励直接使用ASM，因为它要求你必须对JVM内部结构包括class文件的格式和指令集都很熟悉。
