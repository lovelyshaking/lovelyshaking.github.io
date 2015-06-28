---
layout: post
title: Tips for program design
---
  
some tips for java api design:

***today's specific design tips:  ***

在java中，可以使用GetInstance()使用单例模式创建类的实例。

当一个类定义成服务类的时候，需要使用单例模式使用这个类的实例。

*** some abstract tips：***

1. 方法优于字段： 不要把类中的字段直接对外公布，而是应该放置在内部，最好让外部用户只能通过相应的getter/setter方法访问字段。千万不要把字段直接公布出去；

2. 工厂方法优于构造函数：使用工厂方法而不是直接使用构造函数创建对象。工厂方法为开发人员带来了很高的灵活性。它通常是一个静态方法。这个工厂方法的参数与构造函数的参数相同，返回值与构造函数创建的对象也是一致的。使用工厂方法的第一个优点是工厂方法的返回值不一定是声明类型的实例，也可以是它的子类实例；第二，每次返回的对象也不一定是新创建的对象，完全可以将其缓存；第三，其优势在对同步的控制，在工厂方法中可以将创建对象前后的相应代码进行统一管理。

 工厂方法和工厂模式见：

 http://zhidao.baidu.com/link?url=_jKJOX1yUv5lZYunJq-AvsULBUrB9msFnnVXZ83I_v0ypWo63V4J6v1294ErCYaA9q9OKHx5MQVdzuGJSjflyK

 http://www.cnblogs.com/devinzhang/archive/2011/12/19/2293160.html ;

 http://www.blogjava.net/javagrass/archive/2011/04/21/348671.html ;
 
3. 让所有的内容都不可更改：通常情况下，设计一个类的时候，如果不考虑让其拥有子类，就应该让这个类不能被继承。最简单的方法就是让类变成final，更推荐使用工厂方法。

4. 避免滥用setter方法

5.  尽可能通过友元方式来公开功能。java中的友元方式就是默认的package级访问方式，即只允许同一个包内代码进行互访。不要在api中公布那些外部不应该调用的方法。

6.  赋予对象创建者更多权利。

7.  避免暴露深层次继承。
