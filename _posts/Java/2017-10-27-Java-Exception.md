---
layout: post
title:  JAVA中的异常处理机制及异常分类
categories: Java
description: AVA中的异常处理机制
keywords: keyword1, keyword2
---


JAVA的异常处理机制：如果某个方法不能按照正常的途径完成任务，就可以通过另一种路径退出方法。在这种情况下会抛出一个封装了错误信息的对象。此时，这个方法会立刻退出同时不返回任何值。另外，调用这个方法的其他代码也无法继续执行，异常处理机制会将代码执行交给异常处理器。  
  

#### 1.异常分类如下：  
![](http://img.blog.csdn.net/20170401153009718?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvc2luYXRfMzY3MTMzMTk=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)  
  
–>Throwable是 Java 语言中所有错误或异常的超类。下一层分为Error和Exception  
–>Error类是指java运行时系统的内部错误和资源耗尽错误。应用程序不会抛出该类对象。如果出现了这样的错误，除了告知用户，剩下的就是尽力使程序安全的终止。  
–>Exception又有两个分支，一个是运行时异常RuntimeException，如：NullPointerException、ClassCastException；一个是检查异常CheckedException，如I/O错误导致的IOException、SQLException。  
–>RuntimeException是那些可能在 Java 虚拟机正常运行期间抛出的异常的超类。      RuntimeException的异常一般包含几个方面：  
1、错误的类型转换  
2、数组访问越界  
3、访问空指针  

如果出现RuntimeException，那么一定是程序员的错误  
–>检查异常CheckedException一般是外部错误，这种异常都发生在编译阶段，Java编译器会强制程序去捕获此类异常，即会出现要求你把这段可能出现异常的程序进行try catch，该类异常一般包括几个方面：  
1、试图在文件尾部读取数据  
2、试图打开一个错误格式的URL  
3、试图根据给定的字符串查找class对象，而这个字符串表示的类并不存在  
  
#### 2.异常的处理方式  
##### （1）遇到问题不进行具体处理，而是继续抛给调用者  
抛出异常有三种形式，一是throw,一个throws，还有一种系统自动抛异常。  
```java
//程序编写者知道某句代码一定发生异常，使用throw关键字抛出
public static void main(String[] args) { 
    String s = "abc"; 
    if(s.equals("abc")) { 
      throw new NumberFormatException(); 
    } else { 
      System.out.println(s); 
    } 
} 
int div(int a,int b) throws Exception{
return a/b;}
//系统自动抛出异常
public static void main(String[] args) { 
    int a = 5, b =0; 
    System.out.println(5/b); 
}
```  
  
**注意：**  
**Throw和throws的区别：**  
1. 位置不同：throws用在函数上，后面跟的是异常类，可以跟多个；而throw用在函数内，后面跟的是异常对象。  
2. 功能不同：throws用来声明异常，让调用者只知道该功能可能出现的问题，可以给出预先的处理方式；throw抛出具体的问题对象，执行到throw，功能就已经结束了，跳转到调用者，并将具体的问题对象抛给调用者。也就是说throw语句独立存在时，下面不要定义其他语句，因为执行不到。  
3. throws表示出现异常的一种可能性，并不一定会发生这些异常；throw则是抛出了异常，执行throw则一定抛出了某种异常对象。  
4. 两者都是消极处理异常的方式（这里的消极并不是说这种方式不好），只是抛出或者可能抛出异常，但是不会由函数去处理异常，真正的处理异常由函数的上层调用处理。  
  
##### 针对性处理方式：捕获异常  
```java
Try{
//有可能发生异常的代码
}
 Catch（异常类 变量）
{
// 处理异常的代码，捕获
}
finally{
//一定会被执行的代码
}
```  
   
#### 3.RuntimeException和CheckedException的区别  
RuntimeException：在定义方法时不需要声明会抛出RuntimeException， 在调用这个方法时不需要捕获这个RuntimeException；总之，未检查异常不需要try…catch…或throws 机制去处理 
CheckedException：定义方法时必须声明所有可能会抛出的exception； 在调用这个方法时，必须捕获它的checked exception，不然就得把它的exception传递下去。  

**总之，一个方法必须声明所有的可能抛出的已检查异常；未检查异常要么不可控制（Error），要么应该避免（RuntimeException）。如果方法没有声明所有的可能发生的已检查异常，编译器就会给出错误信息**  




